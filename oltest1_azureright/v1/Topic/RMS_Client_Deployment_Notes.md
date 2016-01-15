---
description: na
keywords: na
title: RMS Client Deployment Notes
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 03cc8c6f-3b63-4794-8d92-a5df4cdf598f
---
# Uwagi dotyczące wdrażania klienta RMS
Usługi zarządzania prawami klienta (klienta RMS) w wersji 2 jest nazywana MSIPC klienta. Jest oprogramowania na komputerach z systemem Windows, które komunikują się z usługami Microsoft Rights Management usługi lokalnie lub w chmurze, aby pomóc chronić dostęp do i użycie informacji, zgodnie z jej przepływu przez aplikacji i urządzeń, w granicach swojej organizacji, jak i poza te zarządzane granice. Oprócz wysyłki z [Rights Management udostępnianie aplikacji dla systemu Windows](https://technet.microsoft.com/library/dn919648.aspx), Klient RMS jest dostępny [jako opcjonalną pobierania](http://www.microsoft.com/download/details.aspx?id=38396) który można o potwierdzenie akceptacji umowy licencyjnej, rozpowszechniać oprogramowanie innych firm, aby klienci mogli chronić i korzystać z zawartości, która jest chroniony przez usługi Rights Management.

Ten temat zawiera następujące sekcje:

-   [Redystrybuowanie klienta RMS](#BKMK_RedistributeInstaller)

-   [Instalowanie klienta RMS](#BKMK_InstallClient)

-   [Pytania i odpowiedzi dotyczące klienta RMS](#BKMK_QA)

-   [Ustawienia klienta RMS](#BKMK_Settings)

-   [Usług AD RMS tylko: Ograniczenia klienta RMS do używania Zaufane serwery AD RMS](#BKMK_UsingTrustedServers)

-   [Odnajdywanie usługi RMS](#BKMK_ServiceDiscovery)

## <a name="BKMK_RedistributeInstaller"></a>Redystrybuowanie klienta RMS
Klienta RMS można bezpłatnie rozpowszechniać i używać w połączeniu z innymi aplikacjami i rozwiązania IT. Jeśli Deweloper aplikacji i rozwiązań dostawcy jest rozpowszechniać klienta RMS, masz dwie opcje:

-   Zalecane: Osadzanie Instalatora klienta usług RMS w instalacji aplikacji i uruchom go w trybie dyskretnym ( **/quiet** przełącznika, szczegółowo w następnej sekcji).

-   Należy do wymagań wstępnych dla aplikacji klienta RMS. Po wybraniu tej opcji może być konieczne do zapewnienia użytkownikom dodatkowe instrukcje dotyczące ich do uzyskania, instalowania i aktualizowania swoich komputerach przy użyciu klienta, zanim będzie można korzystać z aplikacji.

## <a name="BKMK_InstallClient"></a>Instalowanie klienta RMS
Klient RMS znajduje się w pliku wykonywalnego Instalatora o nazwie **setup_msipc_***&lt; arch &gt;***.exe**, gdzie *&lt; arch &gt;* jest **x86** (dla komputerów klienckich 32-bitowy) lub **x64** (dla komputerów klienckich 64-bitowy). Pakiet Instalatora 64-bitowe (x 64) instaluje zarówno środowiska wykonawczego 32-bitowego pliku wykonywalnego dla zgodności z 32-bitowych aplikacji, które działają na instalację 64-bitowym systemie operacyjnym, a także środowiska wykonawczego 64-bitowych wykonywalnego do obsługi aplikacji natywnych 64-bitowych. Instalator 32-bitowe (x 86) nie będzie działać w 64-bitowej instalacji systemu Windows.

> [!NOTE]
> Należy z podwyższonym poziomem uprawnień, aby zainstalować klienta RMS, takie jak należących do grupy Administratorzy na komputerze lokalnym.

Klienta RMS można zainstalować przy użyciu jednej z następujących metod instalacji:

-   **Trybie dyskretnym.** Przy użyciu **/quiet** Przełącz w ramach opcji wiersza polecenia, użytkownik może instalacji dyskretnej klienta RMS na komputerach. W poniższym przykładzie pokazano w trybie dyskretnym instalacji klienta RMS na komputerze klienckim 64-bitowe:

    ```
    setup_msipc_x64.exe /quiet
    ```

-   **Tryb interakcyjny.** Alternatywnie można zainstalować klienta RMS za pomocą programu instalacyjnego na podstawie GUI, dostarczanego przez Kreatora instalacji klienta RMS. W tym celu kliknij dwukrotnie pakiet Instalatora klienta RMS (**setup_msipc_***&lt; arch &gt;***.exe**) w folderze, do którego zostało skopiowane lub pobrane na komputerze lokalnym.

## <a name="BKMK_QA"></a>Pytania i odpowiedzi dotyczące klienta RMS
Poniższa sekcja zawiera często zadawane pytania dotyczące klienta RMS i odpowiedzi do nich.

### Systemy operacyjne, które obsługuje klienta RMS?
Klienta RMS jest obsługiwane w następujących systemach operacyjnych:

|System operacyjny Windows Server|Kliencki System operacyjny Windows|
|------------------------------------|--------------------------------------|
|Windows Server 2012 R2|Windows 8.1|
|Windows Server 2012|System Windows 8|
|Windows Server 2008 R2|Windows 7 z co najmniej z dodatkiem SP1|
|Windows Server 2008 (tylko usług AD RMS)|Windows Vista z dodatkiem SP2 co najmniej (tylko usług AD RMS)|

### Które procesorów lub platformy obsługi klienta RMS?
Klient RMS jest obsługiwana w x 86 i x 64 platform komputerowych.

### Którym zainstalowano klienta usług RMS?
Domyślnie klienta RMS jest zainstalowany w %ProgramFiles%\Active katalogu Rights Management usługi klienta 2. &lt; podrzędny numer wersji &gt;.

### Jakie pliki są skojarzone z oprogramowania klienckiego usług RMS?
Następujące pliki są instalowane jako część oprogramowania klienckiego RMS:

-   Msipc.dll

-   Ipcsecproc.dll

-   Ipcsecproc_ssp.dll

-   MSIPCEvents.man

Oprócz tych plików klienta RMS także instaluje pliki obsługi interfejsu (użytkownika MUI) wielojęzyczny użytkownika w językach 44. Aby sprawdzić, czy obsługiwane języki, uruchom instalację klienta RMS i po zakończeniu instalacji przejrzyj zawartość folderów obsługi wielu języków, ścieżka domyślna.

### Jest klienta RMS dołączone domyślnie w przypadku zainstalować nieobsługiwany system operacyjny?
Nie. Ta wersja klienta RMS dostarczany jako opcjonalny pobierania, która może być zainstalowana osobno na komputerach z systemem obsługiwanych wersji systemu operacyjnego Microsoft Windows.

### Klient RMS automatycznie zaktualizowaniu usługi Microsoft Update?
Jeśli zainstalowano klienta usług RMS za pomocą opcji instalacji dyskretnej, klienta RMS dziedziczy bieżące ustawienia Microsoft Update. Jeśli zainstalowano klienta usług RMS za pomocą programu instalacyjnego na podstawie GUI, pojawi się monit Kreatora instalacji klienta RMS umożliwiające Microsoft Update.

## <a name="BKMK_Settings"></a>Ustawienia klienta RMS
Poniższa sekcja zawiera ustawienia informacje dotyczące klienta RMS. Te informacje mogą być przydatne, jeśli masz problemy z aplikacjami lub usługi, które korzystają z klienta RMS.

> [!NOTE]
> Niektóre ustawienia są zależne od tego, czy działa aplikacja RMS enlightened jako aplikacji tryb klienta (np. program Microsoft Word i Outlook lub udostępnianie aplikacji RMS) lub aplikacji trybu serwera (takie jak SharePoint i Exchange).  W następujących tabel, te ustawienia są oznaczone jako **tryb klienta** i **tryb serwera**, odpowiednio.

### Gdzie sklepów klienta RMS licencje na komputerach klienckich
Klient RMS licencje są przechowywane na lokalnym dysku i buforuje także niektóre informacje zawarte w rejestrze systemu Windows.

|Opis|Ścieżki tryb klienta|Serwer tryb ścieżki|
|--------|------------------------|-----------------------|
|Lokalizacja magazynu licencji|%localappdata%\Microsoft\MSIPC|%ALLUSERSPROFILE%\Microsoft\MSIPC\Server\*&lt; identyfikator SID &gt;*\|
|Lokalizacja przechowywania szablonu|%localappdata%\Microsoft\MSIPC\Templates|%ALLUSERSPROFILE%\Microsoft\MSIPC\Server\Templates\*&lt; identyfikator SID &gt;*\|
|Lokalizacji w rejestrze|HKEY_CURRENT_USER<br /> \Software<br /> \Classes<br /> ustawienia \Local<br /> \Software<br /> \Microsoft<br /> \MSIPC|HKEY_CURRENT_USER<br /> \Software<br /> \Microsoft<br /> \MSIPC<br /> \Server<br /> \*&lt; identyfikator SID &gt;*|
> [!NOTE]
> *&lt; identyfikator SID &gt;* jest identyfikator zabezpieczeń (SID) dla konta, na którym uruchomiono aplikację serwera. Na przykład, jeśli aplikacja jest uruchomiona na koncie usługi sieciowej wbudowane, Zastąp *&lt; identyfikator SID &gt;* z wartością dobrze znany identyfikator SID dla tego konta (S-1-5-20).

### Ustawienia rejestru systemu Windows dla klienta RMS
Klucze rejestru systemu Windows można użyć do ustawiania lub modyfikowania niektórych konfiguracji klienta RMS. Na przykład jako administrator RMS enlightened aplikacje, które komunikują się z serwerami usług AD RMS, należy zaktualizować lokalizację usługi enterprise (zastąpienie AD RMS serwery, które jest aktualnie wybrane do publikacji) w zależności od bieżącej lokalizacji komputera klienta w topologii usługi Active Directory. Można też włączyć śledzenie RMS na komputerze klienckim, w celu ułatwienia rozwiązywania problemów z aplikacją RMS enlightened. Skorzystaj z poniższej tabeli, aby zidentyfikować ustawienia rejestru, które można zmienić dla klienta RMS.

|Zadanie|Ustawienia|
|-----------|--------------|
|Usług AD RMS tylko: Aby zaktualizować lokalizację usługi enterprise na komputerze klienckim|Aktualizacja następujących kluczy rejestru:<br /><br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterpriseCertification<br />    REG_SZ: domyślny<br />    **Wartość:**&lt; http lub https &gt; :// *RMS_Cluster_Name*/_wmcs/certyfikacji<br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterprisePublishing<br />    REG_SZ: domyślny<br />    **Wartość:** &lt; http lub https &gt; :// *RMS_Cluster_Name*/_wmcs/Licensing|
|Aby włączyć lub wyłączyć śledzenie|Aktualizacja następującego klucza rejestru:<br /><br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC<br />    REG_DWORD: Śledzenie<br />    **Wartość:** 1-Włącz śledzenie, 0, aby wyłączyć śledzenie (domyślnie)|
|Aby zmienić częstotliwość w dniach, aby odświeżyć szablony|Określić następujące wartości rejestru, jak często szablony będą odświeżane na komputerze użytkownika, jeśli nie ustawiono wartość TemplateUpdateFrequencyInSeconds.  Jeśli żadna z tych wartości, domyślny interwał odświeżania dla aplikacji za pomocą klienta RMS (wersja 1.0.1784.0), aby pobrać szablony to 1 dzień. Wersje przed to mieć wartość domyślną, co 7 dni.<br /><br />**Tryb klienta:**<br /><br />-   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />    REG_DWORD: TemplateUpdateFrequency<br />    **Wartość:** Liczba całkowita określająca liczbę dni (co najmniej 1) między — pliki do pobrania.<br /><br />**Tryb serwera:**<br /><br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\Server\*&lt; identyfikator SID &gt;*<br />    REG_DWORD: TemplateUpdateFrequency<br />    **Wartość:** Liczba całkowita określająca liczbę dni (co najmniej 1) między — pliki do pobrania.|
|Aby zmienić częstotliwość w sekundach, aby odświeżyć szablony **Important:** Jeśli to nie zostanie określona, wartość odświeżanie szablonów w dniach jest ignorowana. Określ jeden lub drugi, nie oba jednocześnie.|Określić następujące wartości rejestru, jak często szablony będą odświeżane na komputerze użytkownika. Jeśli ta wartość lub wartości, aby zmienić częstotliwość w dniach (TemplateUpdateFrequency) nie jest ustawiony, domyślny interwał odświeżania dla aplikacji za pomocą klienta RMS (wersja 1.0.1784.0), aby pobrać szablony to 1 dzień. Wersje przed to mieć wartość domyślną, co 7 dni.<br /><br />**Tryb klienta:**<br /><br />-   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />    REG_DWORD: TemplateUpdateFrequencyInSeconds<br />    **Wartość:** Liczba całkowita określająca liczbę sekund (co najmniej 1) między — pliki do pobrania.<br /><br />**Tryb serwera:**<br /><br />-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\Server\*&lt; identyfikator SID &gt;*<br />    REG_DWORD: TemplateUpdateFrequencyInSeconds<br />    **Wartość:** Liczba całkowita określająca liczbę sekund (co najmniej 1) między — pliki do pobrania.|
|Usług AD RMS tylko: Aby pobrać szablony natychmiast przy następnym żądaniu publikacji|Podczas testowania i oceny można klienta RMS jak najszybciej pobierania szablonów. W tym celu należy usunąć następującego klucza rejestru i klienta RMS będą pobierać szablony natychmiast przy następnym żądaniu publikacji zamiast czekać w czasie określonym przez ustawienie rejestru TemplateUpdateFrequency:<br /><br />-   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\ &lt; nazwa serwera &gt; \Template **Note:** &lt; nazwa serwera &gt; może mieć zewnętrznego (corprights.contoso.com) i adresy URL wewnętrzny (corprights) i z tego powodu dwóch różnych wpisów.|
|Usług AD RMS tylko: Aby włączyć obsługę uwierzytelniania federacyjnego|Jeśli komputer klienta RMS łączy się klastra AD RMS za pomocą zaufania federacyjnego, należy skonfigurować obszar macierzysty federacji.<br /><br />-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\Federation<br />    REG_SZ: FederationHomeRealm<br />    **Wartość:** Wartość tego wpisu rejestru jest identyfikator (URI) dla usługi federacyjnej (na przykład "https://fs-01.contoso.com").|
|Usług AD RMS tylko: Do obsługi partnera serwerów federacyjnych, które wymagają uwierzytelniania opartego na formularzach na dane wejściowe użytkownika|Domyślnie klienta RMS działa w trybie dyskretnym, a dane wejściowe użytkownika nie jest wymagane. Partner serwerów federacyjnych, jednak może pozwalać na wymagać dane wejściowe użytkownika takich jak w szczególności uwierzytelniania opartego na formularzach. W takim przypadku należy skonfigurować klienta RMS Ignoruj trybie dyskretnym, tak aby formularz uwierzytelniania federacyjnego pojawia się w oknie przeglądarki i użytkownik będzie przeniesiony do uwierzytelniania.<br /><br />-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\Federation<br />    REG_DWORD: EnableBrowser **Note:** Jeśli serwer federacyjny jest skonfigurowany na korzystanie z uwierzytelniania opartego na formularzach, ten klucz jest wymagany. Jeśli serwer federacyjny jest skonfigurowany do używania zintegrowanego uwierzytelniania systemu Windows, ten klucz nie jest wymagana.|
|Usług AD RMS tylko: Aby zablokować zużycie usługi ILS|Domyślnie klienta RMS umożliwia wykorzystujących zawartość chroniona przez usługę ILS, ale można skonfigurować klienta tak, aby zablokować tej usługi, ustawiając następującego klucza rejestru. Jeśli ten klucz rejestru jest ustawiony do blokowania usługę ILS, wszelkie próby otwarcia i korzystać z zawartości chronionej przez usluge ILS zwróci następujący błąd:<br />HRESULT_FROM_WIN32(ERROR_ACCESS_DISABLED_BY_POLICY)<br /><br />-   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />    REG_DWORD: **DisablePassportCertification**<br />    **Wartość:** 1, aby zablokować zużycie ILS, 0, aby umożliwić ILS zużycie (domyślnie)|

### Zarządzanie dystrybucją szablonów dla klienta RMS
Szablony ułatwiają tworzenie aplikacji dla użytkowników i administratorów, aby szybko zastosować ochrony Rights Management i klienta RMS automatycznie pliki do pobrania szablony z jego serwerów usług RMS lub usługi umieszczenie w następującej lokalizacji folderu Szablony, klienta RMS nie pobierze wszystkie szablony z jego domyślnej lokalizacji i zamiast tego Pobierz szablony, które zostało umieszczone w tym folderze. Klienta RMS mogą w dalszym ciągu pobrać szablony z innych dostępnych serwerów usług RMS.

**Tryb klienta:** %localappdata%\Microsoft\MSIPC\UnmanagedTemplates

**Tryb serwera:** %allusersprofile%\Microsoft\MSIPC\Server\UnmanagedTemplates\*&lt; identyfikator SID &gt;*

Gdy użytkownik korzysta z tego folderu, nie ma żadnych specjalnych konwencją nazewnictwa wymagane z tą różnicą, że szablony powinien być wystawiony przez serwer usług RMS lub usługi i ich musi mieć rozszerzenie nazwy pliku XML. Na przykład Contoso Confidential.xml lub Contoso ReadOnly.xml są prawidłowe nazwy.

## <a name="BKMK_UsingTrustedServers"></a>Usług AD RMS tylko: Ograniczenia klienta RMS do używania Zaufane serwery AD RMS
Klient RMS może być ograniczone do przy użyciu tylko określonych zaufanych usług AD RMS serwerów o następujących zmian w rejestrze systemu Windows na komputerach lokalnych.

**Aby włączyć ograniczenia RMS klienta do używania tylko zaufanych serwerów usług AD RMS**

-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\TrustedServers\
    REG_DWORD: AllowTrustedServersOnly

    **Wartość:** Jeśli określono wartość inną niż zero, klienta RMS będzie zaufania tylko określonych serwerów skonfigurowanych do listy TrustedServers i usługi Azure Rights Management.

**Aby dodać członków do listy zaufanych serwerów usług AD RMS**

-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\TrustedServers\
    REG_SZ: *&lt; URL_or_HostName &gt;*

    **Wartość:** Wartości ciągu dodanych w tej lokalizacji klucza rejestru mogą być albo formacie nazwa domeny DNS (na przykład **adrms.contoso.com**) lub pełne adresy URL do zaufanych serwerów usług AD RMS (na przykład **https://adrms.contoso.com**). Jeśli określony adres URL, który rozpoczyna się od **https://**,  klienta RMS użyje SSL lub TLS skontaktować się z określonym serwerem usług AD RMS.

## <a name="BKMK_ServiceDiscovery"></a>Odnajdywanie usługi RMS
Odnajdywanie usługi RMS umożliwia klienta RMS Sprawdź serwer usług RMS lub komunikowanie się z przed ochroną zawartości. Odnajdywanie usługi może również być spowodowane klienta RMS wykorzystuje chronionej zawartości, ale jest mniej prawdopodobne, ponieważ zasady dołączone do zawartości zawiera preferowanego serwera usług RMS lub usługi i tylko wtedy, gdy nie powiedzie się który klient następnie uruchamia odnajdywania usług.

Odnajdywanie usługi najpierw sprawdza wersję lokalnie Rights Management (AD RMS). Jeśli to się niepowodzeniem, odnajdowanie usługi automatycznie szuka wersja chmury Rights Management (Azure RMS).

Aby przeprowadzić odnajdywanie usługi do użycia we wdrożeniach lokalnie, klienta RMS sprawdza, czy następujące:

1.  W rejestrze systemu Windows na komputerze lokalnym: Jeśli ustawienia odnajdowania usługi są skonfigurowane w rejestrze, te ustawienia są używane w pierwszej kolejności.  Domyślnie te ustawienia nie są skonfigurowane w rejestrze.

2.  Usług domenowych w usłudze Active Directory: Komputer przyłączony do domeny kwerendę usługi Active Directory dla punktu połączenia usługi (SCP). Jeśli zarejestrowano SCP, zwracana jest adres URL serwera usług RMS do klienta RMS do użycia.

### Usług AD RMS tylko: Włączanie odnajdowania usługi po stronie serwera przy użyciu usługi Active Directory
Jeśli konto ma wystarczające uprawnienia ("Administratorzy przedsiębiorstwa" i administratora lokalnego na serwerze usług AD RMS), możesz automatycznie zarejestrować punkt połączenia usługi (SCP) podczas instalowania usług AD RMS głównego klastra serwera. Jeśli punkt SCP już istnieje w lesie, musisz najpierw usunąć istniejący punkt SCP przed zarejestrowaniem nową.

Można zarejestrować i Usuń punkt SCP po zainstalowaniu usług AD RMS za pomocą następującej procedury. Przed rozpoczęciem, upewnij się, że Twoje konto ma wymagane uprawnienia ("Administratorzy przedsiębiorstwa" i administratora lokalnego na serwerze usług AD RMS).

##### Aby włączyć odnajdywania usług AD RMS rejestrując punkt połączenia usługi w usłudze Active Directory

1.  Otwórz konsolę usługi zarządzania w usłudze Active Directory na serwerze usług AD RMS:

    -   Jeśli używasz systemu Windows Server 2008 R2 lub Windows Server 2008, kliknij przycisk **Start**, kliknij przycisk **Narzędzia administracyjne**, a następnie kliknij przycisk **usługi zarządzania prawami dostępu w usłudze Active Directory**.

    -   Jeśli używasz systemu Windows Server 2012 R2 lub Windows Server 2012, w Menedżerze serwera, kliknij przycisk **narzędzia**, a następnie kliknij przycisk **usługi zarządzania prawami dostępu w usłudze Active Directory**.

2.  W konsoli usług AD RMS kliknij prawym przyciskiem myszy klaster AD RMS, a następnie kliknij przycisk **właściwości**.

3.  Kliknij przycisk **SCP** karty.

4.  Wybierz **SCP zmiany** pole wyboru.

5.  Wybierz **Ustaw punkt połączenia usługi na bieżący klaster certyfikacji** opcji, a następnie kliknij przycisk **OK**.

### Włączanie odnajdowania usługi po stronie klienta przy użyciu w rejestrze systemu Windows
Alternatywnie za pośrednictwem połączenia usługi lub gdy punkt połączenia usługi nie istnieje można skonfigurować rejestr na komputerze klienckim tak, aby klienta RMS można zlokalizować jej serwera usług AD RMS.

##### Aby włączyć odnajdywania usług AD RMS po stronie klienta przy użyciu w rejestrze systemu Windows

1.  Otwórz Edytor rejestru systemu Windows, Regedit.exe:

    -   Na komputerze klienckim, w oknie Uruchom wpisz **regedit**, a następnie naciśnij klawisz ENTER, aby otworzyć Edytor rejestru.

2.  W Edytorze rejestru przejdź do **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC**.

    > [!IMPORTANT]
    > Jeśli aplikacją 32-bitową są uruchomione na komputerze z 64-bitowych, ścieżka jest następująca: 
    > **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC**

3.  Można utworzyć podklucz ServiceLocation, kliknij prawym przyciskiem myszy **MSIPC**, wskaż polecenie **Nowy**, kliknij przycisk **klucz**, a następnie wpisz **ServiceLocation**.

4.  Można utworzyć podklucz EnterpriseCertification, kliknij prawym przyciskiem myszy **ServiceLocation**, wskaż polecenie **Nowy**, kliknij przycisk **klucz**, a następnie wpisz **EnterpriseCertification**.

5.  Aby ustawić adres URL certyfikacji przedsiębiorstwa, kliknij dwukrotnie **(domyślne)** wartości, w obszarze **EnterpriseCertification** podklucz i kiedy **Edytowanie ciągu** pojawi się okno dialogowe dla **Dane wartości**, typ &lt;http or https&gt;://*AD RMS_cluster_name*/_wmcs/Certification, a następnie kliknij przycisk **OK**.

6.  Można utworzyć podklucz EnterprisePublishing, kliknij prawym przyciskiem myszy **ServiceLocation**, wskaż polecenie **Nowy**, kliknij przycisk **klucz**, a następnie wpisz EnterprisePublishing.

7.  Aby ustawić enterprise adres URL, kliknij dwukrotnie **(domyślne)** , w obszarze **EnterprisePublishing** podklucz i kiedy **Edytowanie ciągu** pojawi się okno dialogowe, wpisz **Dane wartości** następujące &lt;http or https&gt;://*AD RMS_cluster_name*/_wmcs/Licensing, a następnie kliknij przycisk **OK**.

8.  Zamknij Edytor rejestru.

Jeśli nie jest określona w rejestrze klienta RMS nie można odnaleźć SCP przy użyciu usługi Active Directory, wywołań odnajdowania usługi dla usług AD RMS nie powiedzie się.

### Przekierowywanie licencjonowania ruchu związanego z serwera
W niektórych przypadkach konieczne może być przekierowanie ruchu podczas odnajdywania usług, na przykład podczas dwóch organizacje są scalane i wycofywania starego serwera licencji w jednej organizacji i klientów należy przekierować do nowego serwera licencji. Lub migracji z usług AD RMS do Azure RMS. Aby włączyć przekierowanie licencjonowania, należy użyć następującej procedury.

##### Aby włączyć RMS licencjonowania przekierowanie przy użyciu w rejestrze systemu Windows

1.  Otwórz Edytor rejestru systemu Windows, Regedit.exe:

    -   Na komputerze klienckim, w oknie Uruchom wpisz **regedit**, a następnie naciśnij klawisz ENTER, aby otworzyć Edytor rejestru.

2.  W Edytorze rejestru przejdź do jednej z następujących czynności:

    -   Dla 64-bitowej wersji pakietu Office x 64 platformy: HKLM\SOFTWARE\Microsoft\MSIPC\Servicelocation

    -   Do 32-bitowej wersji pakietu Office x 64 platformy: HKLM\SOFTWARE\Wow6432Node\Microsoft\MSIPC\Servicelocation

3.  Utwórz podklucz LicensingRedirection, klikając prawym przyciskiem myszy **Servicelocation**, wskaż polecenie **Nowy**, kliknij przycisk **klucz**, a następnie wpisz **LicensingRedirection**.

4.  Aby ustawić przekierowanie licencjonowania, kliknij prawym przyciskiem myszy **LicensingRedirection** podklucza, wybierz opcję **Nowy**, a następnie wybierz **wartość ciągu**.  Dla **Nazwa**, określ poprzedniego serwera licencji adresu URL i **wartość** określ nowy serwer licencjonowania adresu URL.

    Ma nastąpić przekierowanie na jeden na Fabrikam.com Licencjonowanie z serwera w Contoso.com, możesz na przykład wprowadź następujące wartości:

    **Nazwa:** `https://contoso.com/_wmcs/licensing`

    **Wartość:** `https://fabrikam.com/_wmcs/licensing`

    > [!NOTE]
    > Jeśli ma starego serwera licencjonowania intranetowe i adresy URL w ekstranecie określony, nową nazwę i zawiera mapowanie wartości do ustawienia dla obu tych adresów URL w kluczu LicensingRedirection.

5.  Powtórz poprzedni krok dla wszystkich serwerów, które należy przekierować.

6.  Zamknij Edytor rejestru.

