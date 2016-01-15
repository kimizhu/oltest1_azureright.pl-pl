---
description: na
keywords: na
title: RMS Protection with Windows Server File Classification Infrastructure (FCI)
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9aa693db-9727-4284-9f64-867681e114c9
---
# Ochrona RMS z infrastruktury klasyfikacji plik&#243;w systemu Windows Server (FCI)
W tym artykule, aby uzyskać instrukcje i skrypt umożliwia konfigurowanie Menedżera zasobów serwera plików i infrastruktury klasyfikacji pliku (FCI) za pomocą klienta zarządzania prawami (RMS) za pomocą narzędzia RMS ochrony.

To rozwiązanie umożliwia automatycznie chronić wszystkie pliki w folderze na serwerze plików z systemem Windows Server lub automatycznie ochronę plików spełniających określone kryteria. Na przykład pliki, które mają zostało zaklasyfikowane jako zawierający informacje poufne lub poufne. To rozwiązanie wymaga [Azure Rights Management](../Topic/Azure_Rights_Management.md) (Azure RMS), aby chronić pliki, więc musi zawierać tej technologii wdrożonych w organizacji.

> [!NOTE]
> Chociaż Azure RMS zawiera [Łącznik](https://technet.microsoft.com/library/dn375964.aspx) czy obsługuje plików klasyfikacji infrastruktury, że rozwiązanie obsługuje tylko macierzystego ochrony — na przykład pliki pakietu Office.
> 
> Aby obsługuje wszystkie typy plików z infrastrukturą klasyfikacji pliku, należy użyć programu Windows PowerShell **ochrony RMS** modułu, opisane w tym artykule. Aplety poleceń RMS ochrony, takich jak RMS sharing aplikacji, obsługuje ogólnego ochrony, a także ochrony macierzysty, co oznacza, że wszystkie pliki mogą być chronione. Aby uzyskać więcej informacji na temat tych różnych poziomów ochrony, zobacz [Poziom ochrony — macierzystego i ogólny](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_LevelsofProtection) w sekcji [Przewodnik administratora aplikacji udostępniania zarządzania prawami dostępu](../Topic/Rights_Management_sharing_application_administrator_guide.md).

Postępuj zgodnie z instrukcjami są dla systemu Windows Server 2012 R2 lub Windows Server 2012. Po uruchomieniu innych obsługiwanych wersji systemu Windows, może być konieczne do dostosowania niektórych z instrukcjami dla różnic między wersji systemu operacyjnego i co opisano w tym artykule.

## Konfigurowanie wymagań wstępnych dotyczących ochrony Azure RMS za FCI serwera systemu Windows
Wymagania wstępne dotyczące te instrukcje:

-   Na każdym serwerze pliku, gdzie zostanie uruchomiony Menedżera zasobów plików z infrastrukturą klasyfikacji pliku:

    -   Zainstalowano Menedżera zasobów serwera plików jako jeden z usługi roli dla roli usługi plików.

    -   Został zidentyfikowany w folderze lokalnym, który zawiera plików do ochrony za pomocą funkcji zarządzania prawami. Na przykład C:\FileShare.

    -   Zainstalowano narzędziu RMS ochrony, w tym wymagania wstępne narzędzia (na przykład klienta RMS) oraz Azure RMS (np. konta głównego usługi). Aby uzyskać więcej informacji, zobacz [polecenia cmdlet ochrony RMS](https://msdn.microsoft.com/library/azure/mt433195.aspx).

    -   Jeśli chcesz zmienić domyślny poziom ochrony RMS (macierzysty lub ogólny) dla rozszerzeń nazw plików określonych wprowadzeniu rejestru zgodnie z opisem w [interfejsu API pliku konfiguracji](https://msdn.microsoft.com/library/dn197834%28v=vs.85%29.aspx) strony.

    -   Masz połączenia internetowego z ustawieniami komputera skonfigurowanego w razie potrzeby dla serwera proxy. Na przykład: `netsh winhttp import proxy source=ie`

-   Skonfigurowano dodatkowych wymagań wstępnych dla danego wdrożenia Azure Rights Management, zgodnie z opisem w [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/mt433202.aspx). W szczególności należy nawiązać Azure RMS za pomocą wystawcy usługi następujące wartości:

    -   BposTenantId

    -   AppPrincipalId

    -   Klucz symetryczny

-   Lokalnych kont użytkowników usługi Active Directory zostały zsynchronizowane z usługi Azure Active Directory lub usługi Office 365, w tym ich adresów e-mail. Jest to wymagane dla wszystkich użytkowników, których może być wymagane dostęp do plików po są chronione przez FCI i Azure RMS. Po wykonaniu tego kroku (na przykład w środowisku testowym), użytkowników może być zablokowany dostęp do tych plików. Aby uzyskać więcej informacji na temat tej konfiguracji konta, zobacz [Trwa przygotowywanie do systemu Azure Rights Management](../Topic/Preparing_for_Azure_Rights_Management.md).

-   Możesz zidentyfikować Rights Management szablon używany, która będzie chronić pliki. Upewnij się, czy znasz identyfikator dla tego szablonu za pomocą [Get-RMSTemplate](https://msdn.microsoft.com/library/azure/mt433197.aspx) polecenia cmdlet.

## Instrukcje dotyczące konfigurowania FCI Menedżera zasobów serwera plików do ochrony Azure RMS
Wykonaj te instrukcje, aby automatycznie chronić wszystkie pliki w folderze, za pomocą skryptu programu Windows PowerShell jako zadanie niestandardowe. Wykonaj te procedury w następującej kolejności:

1.  Zapisz skrypt programu Windows PowerShell

2.  Tworzenie właściwości klasyfikacji dla zarządzania prawami (RMS)

3.  Utwórz regułę klasyfikacji (Klasyfikacja do usług RMS)

4.  Skonfiguruj harmonogram klasyfikacji

5.  Utwórz zadanie zarządzania niestandardowy plik (Chroń pliki z usług RMS)

6.  Testowanie konfiguracji, należy ręcznie uruchomić reguły i zadania

Na końcu te instrukcje wszystkie pliki w wybranym folderze zostanie sklasyfikowany z właściwości niestandardowej RMS, a te pliki będą następnie chronione przez Rights Management. Do konfigurowania bardziej złożonych selektywnego chroniącego niektóre pliki i innych nie możesz utworzyć lub inną klasyfikację właściwości i reguł, za pomocą zadania zarządzania plikami, który chroni tylko te pliki.

#### Zapisz skrypt programu Windows PowerShell

1.  Rozwiń [Skrypt PowerShell systemu Windows Azure RMS ochrony za pomocą FCI Menedżera zasobów serwera plików](#BKMK_RMSProtection_Script) sekcji w tym artykule, a następnie skopiować jego zawartość. Wklej zawartość skryptu i podaj nazwę pliku **RMS-Protect-FCI.ps1** na komputerze użytkownika.

2.  Przejrzyj skrypt i dokonać następujących zmian:

    -   Wyszukiwanie następujących parametrów i zastąpić własnym AppPrincipalId, które użytkownik korzysta z [RMSServerAuthentication zestaw](https://msdn.microsoft.com/library/mt433199.aspx) polecenia cmdlet, aby nawiązać połączenie Azure RMS:

        ```
        <enter your AppPrincipalId here>
        ```
        Na przykład skrypt może wyglądać następująco:

        `[Parameter(Mandatory = $false)]`

        `[Parameter(Mandatory = $false)] [string]$AppPrincipalId = "b5e3f76a-b5c2-4c96-a594-a0807f65bba4",`

    -   Wyszukiwanie następujących parametrów i zastąpić własnym klucza symetrycznego użytkownik korzysta z [RMSServerAuthentication zestaw](https://msdn.microsoft.com/library/mt433199.aspx) polecenia cmdlet, aby nawiązać połączenie Azure RMS:

        ```
        <enter your key here>
        ```
        Na przykład skrypt może wyglądać następująco:

        `[Parameter(Mandatory = $false)]`

        `[string]$SymmetricKey = "zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA="`

    -   Wyszukiwanie następujących parametrów i zastąpić własnym BposTenantId (identyfikator dzierżawcy) użytkownik korzysta z [RMSServerAuthentication zestaw](https://msdn.microsoft.com/library/mt433199.aspx) polecenia cmdlet, aby nawiązać połączenie Azure RMS:

        ```
        <enter your BposTenantId here>
        ```
        Na przykład skrypt może wyglądać następująco:

        `[Parameter(Mandatory = $false)]`

        `[string]$BposTenantId = "23976bc6-dcd4-4173-9d96-dad1f48efd42",`

    -   Jeśli serwer jest uruchomiony system Windows Server 2012, trzeba będzie ręcznie załadować modułu RMSProtection na początku skryptu. Dodaj następujące polecenie (lub odpowiednik, jeśli w folderze "Program Files" znajduje się na dysku innym niż dysk C::

        ```
        Import-Module "C:\Program Files\WindowsPowerShell\Modules\RMSProtection\RMSProtection.dll"
        ```

3.  Utwórz skrypt. Jeśli nie rejestrować skryptu (bardziej bezpieczny), należy skonfigurować środowiska Windows PowerShell na serwerach, które go uruchomić. Na przykład uruchomienia sesji środowiska Windows PowerShell z **Uruchom jako Administrator** i wprowadź: **Set-ExecutionPolicy Unrestricted**. Jednak ta konfiguracja umożliwia wszystkich niepodpisanych skrypty uruchamiania (mniej bezpieczne).

    Aby uzyskać więcej informacji na temat podpisywania skryptów programu Windows PowerShell, zobacz [about_Signing](https://technet.microsoft.com/library/hh847874.aspx) w bibliotece dokumentacji programu PowerShell.

4.  Zapisz plik lokalnie na każdym serwerze plików, które będą używane przez Menedżera zasobów plików z infrastrukturą klasyfikacji pliku. Na przykład, Zapisz plik w **C:\RMS-Protection**. Zabezpieczenia tego pliku za pomocą uprawnień NTFS, tak aby nieupoważnione nie można go modyfikować.

Teraz wszystko jest gotowe do uruchomienia Konfigurowanie Menedżera zasobów serwera plików.

#### Tworzenie właściwości klasyfikacji dla zarządzania prawami (RMS)

-   W Menedżera zasobów serwera plików, zarządzanie klasyfikacją, Utwórz nową właściwość lokalnego:

    -   **Name**: Typ **RMS**

    -   **Opis**:   Typ **Rights Management protection**

    -   **Typ właściwości**: Wybierz **tak/nie**

    -   **Value**: Wybierz **Tak**

Teraz możesz stworzyć regułę klasyfikacji, który korzysta z tej właściwości.

#### Utwórz regułę klasyfikacji (Klasyfikacja do usług RMS)

-   Utwórz nową regułę klasyfikacji:

    -   Na **Ogólne** karty:

        -   **Name**: Typ **Classify for RMS**

        -   **Włączone**: Zachowaj wartość domyślna, którą jest, że to pole wyboru jest zaznaczone.

        -   **Opis**: Typ **Classify all files in the &lt;folder name&gt; folder for Rights Management**.

            Zastąp *&lt; nazwa folderu &gt;* z wybrana nazwa folderu. Na przykład **klasyfikowania wszystkie pliki w folderze C:\FileShare Rights Management**

        -   **Scope**: Dodaj wybranego folderu. Na przykład **C:\FileShare**.

            Nie należy zaznaczać pól wyboru.

    -   Na **klasyfikacji** karty:

    -   **Metoda klasyfikacji**: Wybierz **klasyfikatora folderów**

    -   **Właściwości** Nazwa: Wybierz **RMS**

    -   Właściwość **wartość**: Wybierz **Tak**

Chociaż reguły klasyfikacji można uruchomić ręcznie, dla bieżących operacji, można tę regułę do uruchomienia zgodnie z harmonogramem, dzięki czemu będzie być sklasyfikowany nowych plików z właściwością RMS.

#### Skonfiguruj harmonogram klasyfikacji

-   Na **Automatyczna klasyfikacja** karty:

    -   **Włączyć harmonogram stałych**: Zaznaczenie tego pola wyboru.

    -   Skonfiguruj harmonogram dla wszystkich reguł klasyfikacji do uruchomienia, który obejmuje naszych nową regułę do klasyfikowania plików z właściwością RMS.

    -   **Zezwalaj ciągłego klasyfikacji dla nowych plików**: Zaznaczenie tego pola wyboru, aby nowe pliki będą niejawnych.

    -   Opcjonalne: Wprowadzone zmiany otwierane, takie jak Konfigurowanie opcji dla raportów i powiadomień.

Po zakończeniu konfiguracji klasyfikacji, wszystko jest gotowe do skonfigurowania zadanie zarządzania, aby zastosować ochrony RMS do plików.

#### Utwórz zadanie zarządzania niestandardowy plik (Chroń pliki z usług RMS)

-   W **zadania zarządzania plikami**, Utwórz nowe zadanie zarządzania plikami:

    -   Na **Ogólne** karty:

        -   **Nazwa zadania**: Typ **Protect files with RMS**

        -   Zachowaj **Włącz** pole wyboru jest zaznaczone.

        -   **Opis**: Typ **Protect files in &lt;folder name&gt; with Rights Management and a template by using a Windows PowerShell script.**

            Zastąp *&lt; nazwa folderu &gt;* z wybrana nazwa folderu. Na przykład **ochronę plików w C:\FileShare z Rights Management i szablon przy użyciu skryptu programu Windows PowerShell**

        -   **Scope**: Wybierz wybranego folderu. Na przykład **C:\FileShare**.

            Nie należy zaznaczać pól wyboru.

    -   Na **akcji** karty:

        -   **Type**: Wybierz **niestandardowy**

        -   **Pliku wykonywalnego**: Ustaw następujące opcje:

            ```
            C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
            ```
            Jeśli system Windows nie znajduje się na dysku C:, zmodyfikować tę ścieżkę lub przejdź do tego pliku.

        -   **Argumentu**: Określ poniżej, dostarczanie własne wartości dla &lt; ścieżka &gt; oraz &lt; identyfikator szablonu &gt;:

            ```
            -Noprofile -Command "<path>\RMS-Protect-FCI.ps1 -File '[Source File Path]' -TemplateID <template GUID> -OwnerMail [Source File Owner Email]"
            ```
            Na przykład jeśli skopiować skrypt do C:\RMS-Protection i e6ee2481-26b9-45e5-b34a-f744eacd53b0 jest identyfikator szablonu zidentyfikowanego z warunków wstępnych, określ poniżej:

            `-Noprofile -Command "C:\RMS-Protection\RMS-Protect-FCI.ps1 -File '[Source File Path]' -TemplateID e6ee2481-26b9-45e5-b34a-f744eacd53b0 -OwnerMail [Source File Owner Email]"`

            W tym poleceniu **[Source File Path]** i **[E-mail właściciela pliku źródłowego]** są oba specyficzny dla FCI zmienne, więc wpisz je dokładnie tak, jak pojawiają się w poleceniu powyżej. Pierwsza z nich jest używana przez FCI automatycznie określić zidentyfikowanego pliku w folderze, a drugą jest wartość dla FCI do automatycznego pobierania adres e-mail właściciela nazwanych zidentyfikowanego pliku. To polecenie jest powtarzany dla każdego pliku w folderze, który w naszym przykładzie każdy plik w folderze C:\FileShare Ponadto zawierającej RMS jako właściwość klasyfikacji pliku.

            > [!NOTE]
            > **-OwnerMail [Source File Owner Email]** Parametru i wartości zapewnia właściciela oryginalnego pliku otrzymuje właściciela Rights Management pliku po jest chroniony. Zapewnia to, że właściciela oryginalnego pliku ma wszystkie prawa Rights Management do własnych plików. Gdy pliki są tworzone przez użytkownika domeny, adres e-mail jest pobrana z usługi Active Directory przy użyciu nazwy konta użytkownika w pliku właściwość właściciela. W tym celu serwer plików musi być w tej samej domenie lub w zaufanej domenie jako użytkownik.
            > 
            > Jeśli to możliwe, przypisywać dokumentów chronionych, aby upewnić się, że ci użytkownicy nadal mają pełną kontrolę nad plikami, które one utworzone oryginalnego właścicieli. Jednak użycie zmiennej [E-mail właściciela pliku źródłowego] jak powyżej, a plik ma domeny zdefiniowanej przez użytkownika jako właściciela (na przykład lokalne konto użyte do utworzenia pliku, więc właściciela Wyświetla SYSTEM), skrypt zakończy się niepowodzeniem.
            > 
            > Dla plików, które nie mają domeny użytkownika jako właściciela możesz skopiować i zapisać te pliki się jako użytkownik domeny, co staje się właścicielem tylko tych plików. Lub, jeśli użytkownik ma uprawnienia, można ręcznie zmienić właściciela.  Lub, można podać adres e-mail określony (takie jak własne lub adres grupy dla działu IT) zamiast zmiennej [E-mail właściciela pliku źródłowego], co oznacza, że wszystkie pliki ochrony za pomocą tego skryptu zostanie ten adres e-mail do definiowania nowego właściciela.

    -   **Uruchom polecenie jako**: Wybierz **System lokalny**

    -   Na **warunku** karty:

        -   **Właściwości**: Wybierz **RMS**

        -   **Operator**: Wybierz **takie same**

        -   **Value**: Wybierz **Tak**

    -   Na **Harmonogram** karty:

        -   **Run at**: Skonfiguruj preferowaną harmonogramu.

            Zezwalaj na dużo czasu na wykonanie skryptu. Mimo to rozwiązanie zabezpiecza wszystkie pliki w folderze, skrypt jest uruchamiany raz dla każdego pliku za każdym razem. Mimo to trwa dłużej niż ochronę wszystkich plików w tym samym czasie, który obsługuje narzędzie RMS ochrony, ta konfiguracja przez plik FCI jest bardziej wydajny. Na przykład chronionych plików może mieć różne właścicieli (zachować pierwotny właściciel) po używana zmienna [E-mail właściciela pliku źródłowego] i ta akcja przez pliku będzie wymagane, jeśli później zmienić konfigurację selektywnego ochrony plików, a nie wszystkie pliki w folderze.

        -   **Uruchom w sposób ciągły na nowe pliki**: Zaznaczenie tego pola wyboru.

#### Testowanie konfiguracji, należy ręcznie uruchomić reguły i zadania

1.  Uruchom regułę klasyfikacji:

    1.  Kliknij przycisk **reguł klasyfikacji** &gt; **teraz uruchomić klasyfikacji z wszystkich reguł**

    2.  Kliknij przycisk **poczekaj klasyfikacji ukończyć**, a następnie kliknij przycisk **OK**.

2.  Poczekaj **systemem klasyfikacji** okno dialogowe można zamknąć, a następnie przeglądać wyniki w raporcie automatycznie wyświetlane. Powinien zostać wyświetlony **1** dla **właściwości** pola i liczby plików w folderze. Upewnij się, za pomocą Eksploratora plików i sprawdzając właściwości plików w wybranym folderze. Na **klasyfikacji** kartę, powinny być widoczne **RMS** jako nazwę właściwości i **Tak** dla jego **wartość**.

3.  Uruchom zadanie zarządzania plikami:

    1.  Kliknij przycisk **zadania zarządzania plikami** &gt; **ochronę plików z usług RMS** &gt; **Uruchom plik zarządzania zadanie teraz**

    2.  Kliknij przycisk **poczekaj na zakończenie zadania**, a następnie kliknij przycisk **OK**.

4.  Poczekaj **uruchomione zadanie zarządzania plikami** okno dialogowe można zamknąć, a następnie przeglądać wyniki w raporcie automatycznie wyświetlane. Liczba plików, które znajdują się w folderze wybranym w powinny być widoczne **pliki** pola. Upewnij się, że pliki w folderze wybranym są teraz chronionych usługami RMS. Na przykład, jeśli wybrany folder jest C:\FileShare, wpisz następujące polecenie w sesji środowiska Windows PowerShell i upewnij się, że żadne pliki mają stan **UnProtected**:

    ```
    foreach ($file in (Get-ChildItem -Path C:\FileShare -Force | where {!$_.PSIsContainer})) {Get-RMSFileStatus -f $file.PSPath}
    ```
    > [!TIP]
    > Wskazówki dotyczące rozwiązywania problemów:
    > 
    > -   Jeśli widzisz **0** w raporcie, a nie liczba plików w folderze, oznacza to, że skrypt nie zostało uruchomione. Najpierw należy sprawdzić samego skryptu ładując go w programie Windows PowerShell ISE do sprawdzania poprawności zawartości skrypt i uruchom, aby sprawdzić, czy są wyświetlane wszystkie błędy. Bez argumentów określony skrypt podejmie próbę nawiązania połączenia i uwierzytelnianie w ramach Azure RMS.
    > 
    >     -   Jeśli skrypt raportów nie może nawiązać połączenia z Azure RMS, sprawdź wartości wyświetlania dla konta głównego usługi, które określona w skrypcie.  Aby uzyskać więcej informacji dotyczących sposobu tworzenia tego podmiotu zabezpieczeń konta usługi, zobacz drugi wymagań wstępnych w [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/mt433202.aspx)
    >     -   Jeśli skrypt zgłasza, że można nawiązać Azure RMS i regionie systemu Azure znajduje się poza USA, sprawdź, czy wprowadzeniu rejestru poprawnie dla tej konfiguracji. Dobrej test dla tego jest uruchamiana Get-RMSTemplate bezpośrednio za pomocą programu Windows PowerShell na serwerze. Aby uzyskać więcej informacji na temat edycji rejestru, zobacz trzeci wymagań wstępnych w [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/mt433202.aspx).
    > -   Jeśli skrypt przez ten sam jest uruchamiany w systemie Windows PowerShell ISE bez błędów, spróbuj wykonać uruchomił ją w następujący sposób z sesję programu PowerShell, określając nazwę pliku, aby chronić i bez parametru - OwnerEmail:
    > 
    >     ```
    >     powershell.exe -Noprofile -Command "<path>\RMS-Protect-FCI.ps1 -File <full path and name of a file>' -TemplateID <template GUID>"
    >     ```
    >     -   Jeśli skrypt został uruchomiony pomyślnie w tej sesji środowiska Windows PowerShell, Sprawdź wpisy dla **Executive** i **argumentu** w akcji zadanie zarządzania pliku.  Jeśli określono **- OwnerEmail [E-mail właściciela pliku źródłowego]**, spróbuj usunąć ten parametr.
    > 
    >         Jeśli zadanie zarządzania plikami działa pomyślnie bez  **- OwnerEmail [E-mail właściciela pliku źródłowego]**, należy sprawdzić, czy pliki niechronione użytkownika domeny wymieniony jako właściciel pliku zamiast **systemu**.  W tym celu należy użyć **zabezpieczeń** kartę dla właściwości pliku, a następnie kliknij przycisk **Zaawansowane**.**Właściciela** bezpośrednio po pliku jest wyświetlana wartość **Nazwa**. Dodatkowo sprawdź, czy serwer plików jest w tej samej domenie lub w zaufanej domenie można znaleźć adres e-mail użytkownika z usług domenowych w usłudze Active Directory.
    > -   Jeśli widzisz poprawna liczba plików w raporcie, ale pliki te nie są chronione, spróbuj ręcznie chronione pliki przy użyciu [RMSFile Chroń](https://msdn.microsoft.com/library/azure/mt433201.aspx) polecenia cmdlet, aby sprawdzić, czy są wyświetlane wszystkie błędy.

W przypadku potwierdzenia faktu, że te zadania uruchomione pomyślnie, można zamknąć Menedżera zasobów plików. Nowe pliki będą automatycznie chronione i wszystkie pliki będą chronione ponownie po uruchomieniu harmonogramy. Ponownie chronione pliki zapewnia, że wszystkie zmiany w szablonie są stosowane do plików.

### <a name="BKMK_RMSProtection_Script"></a>Skrypt PowerShell systemu Windows Azure RMS ochrony za pomocą FCI Menedżera zasobów serwera plików
Ta sekcja zawiera przykładowy skrypt do kopiowania i edytować, zgodnie z opisem w poprzedniej sekcji.

*&#42;&#42;Wykluczenie&#42;&#42;: Ten przykładowy skrypt nie jest obsługiwany w dowolnym standardowym programem ani usługą Microsoft. Ten przykładowy skrypt jest dostarczane IS bez jakiejkolwiek gwarancji.*

```
<# .SYNOPSIS Helper script to protect all file types with Azure RMS and FCI. .DESCRIPTION Protect files with Azure RMS and Windows Server FCI, using an RMS template ID. #> param( [Parameter(Mandatory = $false)] [ValidateScript({ If($_ -eq "") {$true} else { if (Test-Path -Path $_ -PathType Leaf) {$true} else {throw "Can't find file specified"} } })] [string]$File, [Parameter(Mandatory = $false)] [string]$TemplateID, [Parameter(Mandatory = $false)] [string]$OwnerMail, [Parameter(Mandatory = $false)] [string]$AppPrincipalId = "<enter your AppPrincipalId here>", [Parameter(Mandatory = $false)] [string]$SymmetricKey = "<enter your key here>", [Parameter(Mandatory = $false)] [string]$BposTenantId = "<enter your BposTenantId here>" ) # script information [String] $Script:Version = 'version 1.0' [String] $Script:Name = "RMS-Protect-FCI.ps1" #global working variables [switch] $Script:isScriptProcess = $False # Controls the script process. If false, the script gracefully stops running. #**Functions (general helper)*************************************** function Get-ScriptName(){ return $MyInvocation.ScriptName.Substring($MyInvocation.ScriptName.LastIndexOf('\') + 1, $MyInvocation.ScriptName.LastIndexOf('.') - $MyInvocation.ScriptName.LastIndexOf('\') - 1) } #**Functions (script specific)************************************** function Check-Module{ param ([String]$Module = $(Throw "Module name not specified")) [bool]$isResult = $False #try to load the module if (get-module -list -name $Module) { import-module $Module if (get-module -name $Module ) { $isResult = $True } else { $isResult = $False } } else { $isResult = $False } return $isResult } function Protect-File ($ffile, $ftemplateId, $fownermail) { [bool] $returnValue = $false try { If ($OwnerMail -eq $null -or $OwnerMail -eq "") { $protectReturn = Protect-RMSFile -File $ffile -TemplateID $ftemplateId $returnValue = $true Write-Host ( "Information: " + "Protected File: $ffile with Template: $ftemplateId") } else { $protectReturn = Protect-RMSFile -File $ffile -TemplateID $ftemplateId -OwnerEmail $fownermail $returnValue = $true Write-Host ( "Information: " + "Protected File: $ffile with Template: $ftemplateId, set Owner: $fownermail") } } catch { Write-Host ( "ERROR" + "During protection of file: $ffile with Template: $ftemplateId") } return $returnValue } function Set-RMSConnection ($fappId, $fkey, $fbposId) { [bool] $returnValue = $false try { Set-RMSServerAuthentication -AppPrincipalId $fappId -Key $fkey -BposTenantId $fbposId Write-Host ("Information: " + "Connected to Azure RMS Service with BposTenantId: $fbposId using AppPrincipalId: $fappId") $returnValue = $true } catch { Write-Host ("ERROR" + "During connection to Azure RMS Service with BposTenantId: $fbposId using AppPrincipalId: $fappId") } return $returnValue } #**Main Script (Script)********************************************* Write-Host ("-== " + $Script:Name + " " + $Version + " ==-") $Script:isScriptProcess = $True # Validate Azure RMS connection by checking the module and then connection if ($Script:isScriptProcess) { if (Check-Module -Module RMSProtection){ $Script:isScriptProcess = $True } else { Write-Host ("The RMSProtection module is not loaded") -foregroundcolor "yellow" -backgroundcolor "black" $Script:isScriptProcess = $False } } if ($Script:isScriptProcess) { #Write-Host ("Try to connect to Azure RMS with AppId: $AppPrincipalId and BPOSID: $BposTenantId" ) if (Set-RMSConnection $AppPrincipalId $SymmetricKey $BposTenantId) { Write-Host ("Connected to Azure RMS") } else { Write-Host ("Couldn't connect to Azure RMS") -foregroundcolor "yellow" -backgroundcolor "black" $Script:isScriptProcess = $False } } #  Start working loop if ($Script:isScriptProcess) { if ( !(($File -eq $null) -or ($File -eq "")) ) { if (!(Protect-File -ffile $File -ftemplateId $TemplateID -fownermail $OwnerMail)) { $Script:isScriptProcess = $False } } } # Closing if (!$Script:isScriptProcess) { Write-Host "ERROR occurred during script process" -foregroundcolor "red" -backgroundcolor "black"} write-host ("-== " + $Script:Name + " " + $Version + "  ==-") if (!$Script:isScriptProcess) { exit(-1) } else {exit(0)}
```

## Modyfikowanie z instrukcjami, aby wybiórczo ochronę plików
Jeśli masz uprzednio wskazówek pracy, jest ona prosty sposób modyfikować do bardziej zaawansowanych konfiguracji. Na przykład chronić pliki przy użyciu tej samej skryptu, ale tylko w przypadku plików, które zawierają danych osobowych do zidentyfikowania i prawdopodobnie wybierz szablon, który ma bardziej restrykcyjnego prawa.

W tym celu należy użyć jednej z właściwości wbudowanych klasyfikacji (na przykład **informacje osobiste użytkownika**) lub tworzyć własne nową właściwość. Następnie utwórz nową regułę, która korzysta z tej właściwości. Na przykład można wybrać **klasyfikatora zawartości**, wybierz **informacje osobiste użytkownika** właściwości o wartości **Wysoki**, i skonfigurować wzorzec ciągu lub wyrażenie określające pliku do można skonfigurować dla tej właściwości (takie jak ciąg "**Data urodzenia**").

Teraz wszystko, co należy zrobić to utworzyć nowe zadanie zarządzania plikami, który korzysta z takie same ale prawdopodobnie skryptów z innego szablonu i konfigurowania warunku dla właściwości klasyfikacji, które zostały skonfigurowane. Na przykład, zamiast warunek, że możemy wcześniej skonfigurowane (**RMS** właściwości, **takie same**, **Tak**), wybierz opcję **informacje osobiste użytkownika** właściwości o **Operator** ustawioną wartość **takie same** i **wartość** z **Wysoki**.

