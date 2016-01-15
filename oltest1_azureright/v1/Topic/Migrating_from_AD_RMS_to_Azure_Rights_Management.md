---
description: na
keywords: na
title: Migrating from AD RMS to Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 828cf1f7-d0e7-4edf-8525-91896dbe3172
---
# Migrowanie z usług AD RMS do usługi Azure Rights Management
Następujący zestaw instrukcji umożliwia migrację wdrożenia prawa usługi zarządzania Active Directory (AD RMS) do Azure Rights Management (usług Azure RMS). Po migracji użytkownicy nadal będą mieli dostęp do dokumentów i wiadomości e-mail organizacji chroniony za pomocą usług AD RMS oraz nowo zawartości chronionej używa usług Azure RMS.

Nie masz pewności, czy tej migracji usług AD RMS jest odpowiednie dla Twojej organizacji?

-   Wprowadzenie do usług Azure RMS, problemów biznesowych, które można rozwiązać, co prawdopodobnie administratorom i użytkownikom i jak działa zobacz [Co to jest Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md)

-   Porównanie usług Azure RMS za pomocą usług AD RMS, zobacz [Porównanie Azure Rights Management i usług AD RMS](../Topic/Comparing_Azure_Rights_Management_and_AD_RMS.md).

## Wymagania wstępne dotyczące migracji usług AD RMS do usług Azure RMS
Przed rozpoczęciem migracji do usługi Azure RMS, upewnij się, że zostały spełnione następujące wymagania wstępne i zapoznaj się ze wszelkich ograniczeń.

|Wymaganie|Więcej informacji|
|-------------|---------------------|
|Obsługiwane wdrażanie usług RMS|Wszystkie wersje usług AD RMS systemu Windows Server 2008 za pośrednictwem systemu Windows Server 2012 R2 obsługuje migrację do usług Azure RMS:<br /><br />-   Windows Server 2008 (x 86 lub x 64)<br />-   Windows Server 2008 R2 (x 64)<br />-   Windows Server 2012 (x 64)<br />-   Windows Server 2012 R2 (x 64) **Note:** Jeśli używasz usług RMS systemu Windows w systemie Windows Server 2003, ta wersja systemu operacyjnego będzie obsługiwany podczas 2015. Ta wersja usług RMS można migrować do usług Azure RMS, ale proces ten jest obsługiwany tylko wtedy, gdy nadal jest obsługiwany system operacyjny. Obejść ten problem można importować z zaufanej domeny publikacji (zaufaną domenę publikacji) do wersji usług AD RMS, który jest obsługiwany, a następnie zaimportuj ponownie zaufaną domenę publikacji bez opcji zgodności RMS 1.0. Aby uzyskać więcej informacji na temat zaufanych domen publikacji, zobacz [zaufanej domeny publikacji](http://technet.microsoft.com/library/dd996639%28v=ws.10%29.aspx)<br />Obsługiwane są wszystkie prawidłowe topologii usług AD RMS:<br /><br />-   Pojedynczy las, pojedynczy klaster RMS<br />-   Pojedynczy las wielu klastrów RMS przeznaczonego tylko do licencjonowania<br />-   Wiele lasów, wielu klastrów RMS **Note:** Domyślnie wielu klastrów RMS migracji do pojedynczego dzierżawy usługi Azure RMS. Różne dzierżawcy RMS, należy należy je traktować jako różnych migracji. Nie można zaimportować klucza z jednego klastra usług RMS do więcej niż jeden dzierżawy usługi Azure RMS.|
|Wszystkie wymagania do uruchamiania usług Azure RMS, w tym dzierżawy usługi Azure RMS (nieaktywna)|Zobacz [Wymagania dotyczące systemu Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).<br /><br />Mimo że dzierżawy usługi Azure RMS musi mieć, aby można migrować z usług AD RMS, zaleca się nie zostanie aktywowany usługi zarządzania prawami dostępu przed migracją. Proces migracji zawiera ten krok po wyeksportować kluczy i szablony z usług AD RMS i zaimportować je do usług Azure RMS. Jednak jeśli usług Azure RMS został już aktywowany, można nadal migracji z usług AD RMS.|
|Przygotowanie do usług Azure RMS:<br /><br />-   Synchronizacja katalogu z katalogu lokalnego i Azure Active Directory<br />-   Obsługujące pocztę grup w usłudze Azure Active Directory|Zobacz [Trwa przygotowywanie do systemu Azure Rights Management](../Topic/Preparing_for_Azure_Rights_Management.md).|
|W przypadku użycia funkcji zarządzania prawami do informacji (IRM) programu Exchange Server (na przykład reguł transportu i Outlook Web Access) lub serwer programu SharePoint za pomocą usług AD RMS:<br /><br />-   Planowanie krótkim czasie, kiedy IRM nie będą dostępne na tych serwerach|Możesz korzystać z tej funkcji na tych serwerach z usług Azure RMS po migracji. Jednak jeden z kroków migracji jest tymczasowo wyłączyć usługę IRM, zainstalować i skonfigurować łącznik, ponownie skonfigurować serwery i ponownie włączyć IRM.<br /><br />Jest to tylko czas przestoju do usługi podczas procesu migracji.|
Ograniczenia:

-   Proces migracji obsługuje migrację serwera licencjonowania usług Azure RMS klucza certyfikatu (certyfikat licencjodawcy serwera) do sprzętowego modułu zabezpieczeń (HSM), usługi Exchange Online nie obsługuje obecnie tej konfiguracji. Chcąc pełną funkcjonalność IRM z usługą Exchange Online po migracji do usługi Azure RMS, klucz dzierżawy usługi Azure RMS musi być [zarządzane przez firmę Microsoft](http://technet.microsoft.com/library/dn440580.aspx). Alternatywnie można uruchomić IRM z ograniczoną funkcjonalnością w usłudze Exchange Online, gdy dzierżawcy usług Azure RMS jest zarządzane przez użytkownika (BYOK). Aby uzyskać więcej informacji o używaniu programu Exchange Online z usług Azure RMS, zobacz [Step 6. Configure IRM integration for Exchange Online](#BKMK_Step6Migration) w tych instrukcji.

-   Jeśli masz oprogramowania i klientów, które nie są obsługiwane za pomocą usług Azure RMS, nie będą w stanie ochrony lub korzystać z zawartości chronionej przez usług Azure RMS. Należy sprawdzić obsługiwane aplikacje i klientów w sekcji [Wymagania dotyczące systemu Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tematu.

-   W przypadku zaimportowania do usług Azure RMS jako klucz lokalnie zarchiwizowane (nie ustawiono zaufaną domenę publikacji być aktywne podczas procesu importowania.) i migracji użytkowników do migracji stopniowej, zawartości chronionej nowo zmigrowanych użytkownicy nie będą dostępne dla użytkowników, którzy chcą korzystać z usług AD RMS. W tym scenariuszu jeśli to możliwe, zachować krótki czas migracji i migracji użytkowników logicznej taki sposób, że jeśli współpracują ze sobą, są one migracji ze sobą.

    To ograniczenie nie dotyczy po ustawieniu zaufaną domenę publikacji na aktywny podczas procesu importowania, ponieważ wszyscy użytkownicy będą ochrony zawartości przy użyciu tego samego klucza. Zaleca się tej konfiguracji, ponieważ umożliwia migrację wszystkich użytkowników, niezależnie od siebie i we własnym tempie.

-   Jeśli współpracę z partnerami zewnętrznymi (na przykład przy użyciu zaufanych domen użytkowników lub federation) migrowania musi do usług Azure RMS albo w tym samym czasie jako migracji lub jak najszybciej go później. Aby kontynuować, dostęp do zawartości, że organizacji wcześniej chronione za pomocą usług AD RMS, muszą mieć klienta zmian konfiguracji, które są podobne do tych, które należy wybrać i uwzględnione w tym dokumencie.

    Z powodu zmian możliwych konfiguracji, które mogą mieć partnerów dokładne instrukcje dotyczące proces ponownej konfiguracji są poza zakres tego dokumentu. Aby uzyskać pomoc skontaktuj się z usług pomocy technicznej firmy Microsoft (CSS).

## Kroki dotyczące migracji usług AD RMS do usług Azure RMS

|Krok migracji|Więcej informacji|
|-----------------|---------------------|
|**1. Pobierz narzędzia administracyjne zarządzania usług Azure RMS**|Aby uzyskać instrukcje, zobacz [Step 1: Download the Azure Rights Management Administration Tool](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step1Migration).|
|**2. Eksportowanie danych konfiguracji z usług AD RMS i zaimportuj go do usług Azure RMS**|Eksportowanie danych konfiguracji (klucze, szablony, adresy URL) z usług AD RMS do pliku XML, a następnie przekaż ten plik do usług Azure RMS za pomocą polecenia cmdlet Import-AadrmTpd środowiska Windows PowerShell. Mogą być potrzebne dodatkowe kroki w zależności na klucza konfiguracji usług AD RMS:<br /><br />-   Oprogramowanie chronione klucz oprogramowanie chronione klucza migracji: Centralnie zarządzane, na podstawie hasła kluczy w usługach AD RMS do klucza dzierżawy zarządzany przez firmę Microsoft Azure RMS. Jest to najprostsza ścieżka migracji i nie dodatkowe czynności nie są wymagane.<br />-   Chronione HSM klucz chronione HSM klucza migracji: Klucze, które są przechowywane przez sprzętowych modułów zabezpieczeń dla usług AD RMS kluczowi zarządzane przez klienta usług Azure RMS dzierżawy ("wprowadzić własny klucz" lub scenariusza BYOK). Wymaga to dodatkowe czynności, aby przenieść klucz z sieci lokalnej firmy Thales HSM do Azure RMS HSM.<br />-   Oprogramowanie chronione klucz chronione HSM klucza migracji: Zarządzane centralnie, na podstawie hasła kluczy w usługach AD RMS kluczowi zarządzane przez klienta usług Azure RMS dzierżawy ("wprowadzić własny klucz" lub scenariusza BYOK). Wymaga to większość konfiguracji, ponieważ należy najpierw wyodrębnić klucz oprogramowania i zaimportować go do sprzętowych modułów zabezpieczeń lokalnych, a następnie wykonaj dodatkowe czynności, aby przenieść klucz z sieci lokalnej firmy Thales HSM do Azure RMS HSM.<br /><br />Aby uzyskać instrukcje, zobacz [Step 2. Export configuration data from AD RMS and import it to Azure RMS](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step2Migration).|
|**3. Aktywuj dzierżawcy RMS**|Jeśli to możliwe wykonaj ten krok po zakończeniu procesu importowania i przed nie.<br /><br />Aby uzyskać więcej informacji oraz instrukcje, zobacz [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).|
|**4. Konfigurowanie importowanych szablonów**|Podczas importowania szablonów zasad praw, ich stan zostaną zarchiwizowane. Jeśli chcesz, aby użytkownicy mogli zobaczyć i użyć je, należy zmienić stan szablonu, aby opublikowane w portalu Azure klasycznego.<br /><br />Aby uzyskać instrukcje, zobacz [Step 4. Configure imported templates](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step4Migration).|
|**5. Ponownie skonfigurować klientów do używania usług Azure RMS**|Aby korzystać z usługi Azure RMS zamiast usług AD RMS, należy zmienić konfigurację istniejących komputerów z systemem Windows. Ten krok w przypadku komputerów w organizacji i na komputerach w organizacji partnera ma we współpracy z nich podczas podczas uruchamiania usług AD RMS.<br /><br />Ponadto, jeśli wdrożono [rozszerzenia urządzenia przenośnego](http://technet.microsoft.com/library/dn673574.aspx) do obsługi urządzeń przenośnych, takich jak telefony iOS i Ipad, telefony z systemem Android i tablety, Windows phone i komputerów Mac, należy usunąć rekordy SRV w systemie DNS, który przekierowanie do używania usług AD RMS.<br /><br />Aby uzyskać instrukcje, zobacz [Step 5. Reconfigure clients to use Azure RMS](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step5Migration).|
|**6. Konfigurowanie prawami do integracji z usługą Exchange Online**|Ten krok jest wymagany, jeśli chcesz użyć usługi Exchange Online z usług Azure RMS.<br /><br />Aby uzyskać instrukcje, zobacz [Step 6. Configure IRM integration for Exchange Online](#BKMK_Step6Migration).|
|**7. Wdrażanie łącznika usług RMS**|Ten krok jest wymagany, jeśli chcesz użyć dowolnego z następujących usług lokalnych z usług Azure RMS:<br /><br />-   Exchange Server (na przykład reguł transportu i Outlook Web Access)<br />-   Serwer programu SharePoint<br />-   Windows Server, który jest uruchamiany plik klasyfikacji infrastruktury<br /><br />Aby uzyskać instrukcje, zobacz [Step 7. Deploy the RMS connector](#BKMK_Step7Migration).|
|**8. Likwidowanie usług AD RMS**|Po potwierdzeniu, że wszyscy klienci używają usług Azure RMS i nie jest już dostęp do serwerów usług AD RMS, można zlikwidować wdrożenie usług AD RMS.<br /><br />Aby uzyskać instrukcje, zobacz [Step 8. Decommission AD RMS](#BKMK_Step8Migration).|
|**9. Ponownie klucz klucz dzierżawy usługi Azure RMS**|Ten krok jest wymagany, jeśli nie zostały uruchomione trybu kryptograficznego 2 przed migracją i opcjonalne, ale zalecane w przypadku wszystkich migracji, które pomagają w ochronie zabezpieczeń klucza dzierżawy usługi Azure RMS.<br /><br />Aby uzyskać instrukcje, zobacz [Step 9. Re-key your Azure RMS tenant key](#BKMK_Step9Migration).|

### <a name="BKMK_Step1Migration"></a>Krok 1: Pobierz narzędzie administracyjne usługi Azure Rights Management
Przejdź do witryny Microsoft Download Center i pobrać [Narzędzie administracyjne Azure Rights Management](http://go.microsoft.com/fwlink/?LinkId=257721), który zawiera modułu Administracja usług Azure RMS dla środowiska Windows PowerShell.

### <a name="BKMK_Step2Migration"></a>Krok 2. Eksportowanie danych konfiguracji z usług AD RMS i zaimportuj go do usług Azure RMS
Ten krok jest procesem dwóch części:

1.  Eksportuj dane konfiguracji z usług AD RMS, eksportując zaufanych domen publikacji (zaufanych domen publikacji) do pliku .xml. Ten proces jest taka sama dla wszystkich migracji.

2.  Importowanie danych konfiguracji z usług Azure RMS. Istnieją różne procesy tego kroku, w zależności od bieżącej konfiguracji wdrożenia usług AD RMS i topologii preferowanych dla klucza dzierżawy usługi Azure RMS.

#### Eksportowanie danych konfiguracji z usług AD RMS
Wykonanie poniższej procedury na wszystkich klastrach usług AD RMS dla wszystkich zaufanych domen publikacji chronionych zawartości dla Twojej organizacji. Nie trzeba uruchamiać w klastrach tylko do licencjonowania.

> [!NOTE]
> Jeśli używasz systemu Windows Server 2003 Rights Management, zamiast tych instrukcji, postępuj zgodnie z procedurą [wyeksportować certyfikat licencjodawcy serwera, zaufanej domeny użytkownika, zaufaną domenę publikacji i RMS klucza prywatnego](http://technet.microsoft.com/library/jj835767%28v=ws.10%29.aspx) z [migracji z usług RMS systemu Windows do usług AD RMS w różnych infrastruktury](http://technet.microsoft.com/library/jj835767%28v=ws.10%29.aspx) tematu.

###### Aby wyeksportować dane konfiguracyjne (zaufanej domeny informacje dotyczące publikowania)

1.  Zaloguj się na klaster AD RMS jako użytkownik z usługi AD RMS uprawnienia administratora.

2.  Z konsoli zarządzania usług AD RMS (**usługi zarządzania prawami dostępu w usłudze Active Directory**) rozwiń nazwę klastra usług AD RMS, rozwiń węzeł **Zasady zaufania**, a następnie kliknij przycisk **zaufanych domen publikacji**.

3.  W okienku wyników wybierz zaufanej domeny publikacji, a następnie w okienku Akcje kliknij polecenie **Eksportuj zaufaną domenę publikacji**.

4.  W **Eksportuj zaufaną domenę publikacji** okno dialogowe:

    -   Kliknij przycisk **Zapisz jako** i Zapisz ścieżkę i nazwę pliku. Upewnij się określić **.xml** jako rozszerzenie nazwy pliku (to nie jest dołączany automatycznie).

    -   Określ i Potwierdź silne hasło. Pamiętaj to hasło, ponieważ będą potrzebne później, podczas importowania danych konfiguracji z usług Azure RMS.

    -   Nie należy zaznaczać pole wyboru, aby zapisać plik zaufanej domeny RMS w wersji 1.0.

Po wyeksportowaniu zaufanych domen publikacji, możesz uruchomić procedurę do importowania danych do usług Azure RMS.

#### Importowanie danych konfiguracji z usług Azure RMS
Dokładne procedury dla tego kroku zależą od bieżącej konfiguracji wdrożenia usług AD RMS i topologii preferowanych dla klucza dzierżawy usługi Azure RMS.

Bieżące wdrożenia usług AD RMS będzie używany jeden z następujących konfiguracji dla klucza (certyfikat licencjodawcy serwera) certyfikatu licencjodawcy serwera:

-   Ochrona za pomocą hasła w bazie danych usług AD RMS. Jest to konfiguracja domyślna.

-   Ochrona HSM za pomocą firmy Thales sprzętu zabezpieczeń moduły.

-   Ochrona HSM przy użyciu sprzętu zabezpieczeń moduły od dostawcy innego niż firmy Thales.

-   Hasło jest chroniony za pomocą zewnętrznego dostawcy usług kryptograficznych.

> [!NOTE]
> Aby uzyskać więcej informacji o używaniu modułów zabezpieczeń sprzętu z usług AD RMS, zobacz [usług AD RMS korzystanie z modułów zabezpieczeń sprzętu](http://technet.microsoft.com/library/jj651024.aspx).

Są dwie opcje klucza topologii dzierżawy usługi Azure RMS: Firma Microsoft sama zarządza klucz dzierżawcy (**zarządzany przez firmę Microsoft**) lub zarządzać klucz dzierżawcy (**zarządzane przez klienta**). Podczas zarządzania własny klucz dzierżawy usługi Azure RMS go jest czasami określane jako "Przynieś własne klucza" (BYOK) i wymaga sprzętu zabezpieczeń moduły z firmy Thales. Aby uzyskać więcej informacji, zobacz [Choose your tenant key topology: Managed by Microsoft (the default) or managed by you (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ChooseTenantKey) w sekcji [Planowanie i wdrażanie swoim kluczem dzierżawcy zarządzania prawami Azure](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) tematu.

> [!IMPORTANT]
> Usługa Exchange Online nie jest obecnie zgodny z Azure RMS BYOK.  Jeśli chcesz użyć BYOK po migracji i planowane jest używanie usługi Exchange Online, upewnij się, zrozumieć, jak ta konfiguracja ogranicza funkcjonalność prawami do programu Exchange Online. Zapoznaj się z informacjami w [BYOK pricing and restrictions](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing) w sekcji  [Planowanie i wdrażanie swoim kluczem dzierżawcy zarządzania prawami Azure](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) temacie pomogą określić najlepszą usług Azure RMS dzierżawy topologii klucza do migracji.

Skorzystaj z poniższej tabeli, aby zidentyfikować procedurę do migracji. Nie są obsługiwane kombinacje, które nie są wyświetlane.

|Bieżące wdrożenia usług AD RMS|Topologia klucza dzierżawy wybrane usług Azure RMS|Instrukcje dotyczące migracji|
|----------------------------------|------------------------------------------------------|---------------------------------|
|Ochrona za pomocą hasła w bazie danych usług AD RMS|Zarządzany przez firmę Microsoft|Zobacz **oprogramowanie chronione klucz do migracji klucza oprogramowanie chronione** procedury po tej tabeli.<br /><br />Jest to najprostsza ścieżka migracji i wymaga jedynie w przypadku transferu danych konfiguracyjnych do usług Azure RMS.|
|HSM ochrony za pomocą firmy Thales nShield sprzętu zabezpieczeń moduły|Zarządzane przez klienta (BYOK)|Zobacz **chronione HSM klucz chronione HSM migracji klucza** procedury po tej tabeli.<br /><br />Wymaga to zestaw narzędzi BYOK i zestaw dwa kroki, aby przenieść klucz z sieci lokalnej HSM do HSM RMS Azure i następnie przenieść danych konfiguracji usług Azure RMS.|
|Ochrona za pomocą hasła w bazie danych usług AD RMS|Zarządzane przez klienta (BYOK)|Zobacz **oprogramowanie chronione klawisz, aby chronić HSM migracji kluczy** procedury po tej tabeli.<br /><br />Wymaga to zestaw narzędzi BYOK i zestawy trzy kroki, aby pierwszym wyodrębnianie z klucza oprogramowania i importowania do sprzętowych modułów zabezpieczeń lokalnych, następnie przenieść klucz z sieci lokalnej HSM HSM RMS Azure i wreszcie transferu danych konfiguracji z usług Azure RMS.|
|HSM ochrony przy użyciu sprzętu zabezpieczeń moduły od dostawcy innego niż firmy Thales|Zarządzane przez klienta (BYOK)|Skontaktuj się z dostawcą dla Ciebie HSM instrukcje można przetransferować klucz z tego HSM do firmy Thales nShield sprzętowego modułu zabezpieczeń (HSM). Następnie postępuj zgodnie z instrukcjami dotyczącymi **chronione HSM klucz chronione HSM migracji klucza** procedury po tej tabeli.|
|Hasło chronione przy użyciu zewnętrznego dostawcy usług kryptograficznych|Zarządzane przez klienta (BYOK)|Skontaktuj się z dostawcą usług kryptograficznych dostawcy instrukcje można przetransferować klucz do firmy Thales nShield sprzętu zabezpieczeń moduły. Następnie postępuj zgodnie z instrukcjami dotyczącymi **chronione HSM klucz chronione HSM migracji klucza** procedury po tej tabeli.|
Przed rozpoczęciem tych procedur upewnij się, że można uzyskać dostęp do plików .xml, utworzone wcześniej podczas eksportowania zaufanych domen publikacji. Na przykład te może zostać zapisane pamięć USB w przypadku przełączenia z serwera usług AD RMS do stacji roboczej połączonych z Internetem.

> [!NOTE]
> Jednak te pliki były przechowywane, użyj zabezpieczeń najlepszych rozwiązań, aby je chronić, ponieważ te dane obejmują swoim kluczem prywatnym.

##### Oprogramowanie chronione klucz do migracji klucza oprogramowanie chronione
Użyj tej procedury do importowania konfiguracji usług AD RMS do usług Azure RMS, aby spowodować klucz dzierżawcy usług Azure RMS, który jest zarządzany przez firmę Microsoft.

###### Aby zaimportować dane konfiguracyjne do usług Azure RMS

1.  Na połączonych z Internetem stacji roboczej należy pobrać i zainstalować moduł Windows PowerShell dla usług Azure RMS (minimalna wersja 2.1.0.0), który zawiera [AadrmTpd importowania](http://msdn.microsoft.com/library/azure/dn857523.aspx) polecenia cmdlet.

    > [!TIP]
    > Jeśli zostały wcześniej pobrane i zainstalowane moduł, sprawdź numer wersji, uruchamiając: `(Get-Module aadrm -ListAvailable).Version`

    Aby uzyskać instrukcje instalacji, zobacz [Instalowanie programu Windows PowerShell Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

2.  Uruchom program Windows PowerShell z **Uruchom jako administrator** opcji i używać [Connect AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx) polecenia cmdlet, aby połączyć się z usługą Azure RMS:

    ```
    Connect-AadrmService
    ```
    Po wyświetleniu monitu wprowadź swoje [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] poświadczenia administratora dzierżawy (zazwyczaj będzie się używać konta, które jest administratorem globalnym usługi Azure Active Directory lub usługi Office 365).

3.  Użyj [AadrmTpd importowania](http://msdn.microsoft.com/library/azure/dn857523.aspx) polecenia cmdlet, aby przekazać pierwszy wyeksportowane pliku zaufanej domeny (XML) publikacji. Jeśli masz więcej niż jeden plik .xml, ponieważ miał wiele zaufanych domen publikacji, wybierz plik zawierający wyeksportowany zaufanej domeny publikacji, których chcesz użyć w usług Azure RMS do ochrony zawartości po migracji. Za pomocą następującego polecenia:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword -Active $True -Verbose
    ```
    Na przykład: **Import-AadrmTpd -TpdFile E:\contosokey1.xml -ProtectionPassword -Active $true -Verbose**

    Po wyświetleniu monitu wprowadź hasło, które określony wcześniej i potwierdzenie do wykonania tej akcji.

4.  Po zakończeniu działania polecenia, powtórz krok 3 dla każdego pozostałe plik XML, który został utworzony przez wyeksportowanie zaufanej domeny publikacji. Ale tych plików, należy ustawić **-Active** do **false** po uruchomieniu polecenia importu. Na przykład: **Import-AadrmTpd -TpdFile E:\contosokey2.xml -ProtectionPassword -Active $false -Verbose**

5.  Użyj [AadrmService rozłączenia](http://msdn.microsoft.com/library/azure/dn629416.aspx) rozłączyć się z usługą Azure RMS przy użyciu polecenia cmdlet:

    ```
    Disconnect-AadrmService
    ```

Teraz możesz przejść do [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).

##### Chronione HSM klucz chronione HSM klucza migracji
Jest to procedura dwuczęściowej importować klucz HSM i konfiguracji usług AD RMS do usług Azure RMS, aby spowodować klucz dzierżawcy usług Azure RMS, który jest zarządzany przez użytkownika (BYOK).

Należy najpierw pakiet klucz HSM, więc jest gotowe do przeniesienia do usług Azure RMS, a następnie zaimportować go z danymi konfiguracji.

###### Część 1: Pakiet klucz HSM, więc jest gotowe do przesłania do usług Azure RMS

1.  Postępuj zgodnie z instrukcjami [Implementing bring your own key (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) części [Planowanie i wdrażanie swoim kluczem dzierżawcy zarządzania prawami Azure](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md), korzystając z procedury **Generuj i transfer klucza dzierżawcy — w Internecie** z następującymi wyjątkami:

    -   Nie należy wykonać kroki **wygenerować klucz dzierżawcy**, ponieważ istnieje już równoważne z wdrożeniem usług AD RMS. Należy zidentyfikować klucz używanym przez serwer usług AD RMS z instalacji firmy Thales i jest on używany podczas migracji. Zaszyfrowane pliki klucza są zwykle nazwę firmy Thales **key_(keyAppName)_(keyIdentifier)** lokalnie na serwerze.

    -   Nie należy wykonać kroki **transferu klucz dzierżawcy do usług Azure RMS**, który używa polecenia Dodaj AadrmKey.  Zamiast tego po przekazać swoje wyeksportowany zaufanej domeny publikacji, przy użyciu polecenia Import AadrmTpd będzie transferu klucz HSM przygotowany.

2.  Na stacji roboczej połączonych z Internetem w sesji środowiska Windows PowerShell, ponownie nawiązać połączenie z usług Azure RMS.

Teraz, gdy klucz HSM zostały przygotowane do usług Azure RMS, możesz zaimportować plik klucza HSM i danych konfiguracji usług AD RMS.

###### Część 2: Importuj HSM klucza konfiguracji danych i usług Azure RMS

1.  Nadal na stacji roboczej połączenia z Internetem i w sesji środowiska Windows PowerShell należy przekazać pierwszy wyeksportowanego pliku zaufanej domeny publikacji (XML). Jeśli masz więcej niż jeden plik .xml, ponieważ miał wiele zaufanych domen publikacji, wybierz plik zawierający wyeksportowany zaufanej domeny publikacji, która odpowiada kluczowi HSM, którego chcesz użyć w usług Azure RMS na potrzeby ochrony zawartości po migracji. Za pomocą następującego polecenia:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToBYOKPackage> -Active $True -Verbose
    ```
    Na przykład: **Import -TpdFile E:\no_key_tpd_contosokey1.xml  -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $true -Verbose**

    Po wyświetleniu monitu wprowadź hasło, które określony wcześniej i potwierdzenie do wykonania tej akcji.

2.  Po zakończeniu działania polecenia, powtórz krok 1 dla każdego pozostałe plik XML, który został utworzony przez wyeksportowanie zaufanej domeny publikacji. Ale tych plików, należy ustawić **-Active** do **false** po uruchomieniu polecenia importu.  Na przykład: **Import -TpdFile E:\contosokey2.xml -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $false -Verbose**

3.  Użyj [AadrmService rozłączenia](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) rozłączyć się z usługą Azure RMS przy użyciu polecenia cmdlet:

    ```
    Disconnect-AadrmService
    ```

Teraz możesz przejść do [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).

##### Oprogramowanie chronione klawisz, aby chronić HSM migracji kluczy
Jest to procedura trzyczęściowej do importowania konfiguracji usług AD RMS do usług Azure RMS, aby spowodować klucz dzierżawcy usług Azure RMS, który jest zarządzany przez użytkownika (BYOK).

Należy najpierw wyodrębniania klucz (certyfikat licencjodawcy serwera) certyfikatu licencjodawcy serwera z danych konfiguracji i przenieść klucz do firmy Thales lokalnych sprzętowych modułów zabezpieczeń, a następnie pakietu i przenieść klucz HSM do usług Azure RMS i następnie zaimportować dane konfiguracyjne.

###### Część 1: Wyodrębnienie swoje certyfikat licencjodawcy serwera z danych konfiguracji i zaimportować klucz do HSM sieci lokalnej

1.  Użyj następujących kroków w [Implementing bring your own key (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) części [Planowanie i wdrażanie swoim kluczem dzierżawcy zarządzania prawami Azure](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) tematu:

    -   **Generuj i transfer klucza dzierżawcy — w Internecie**: **Przygotowanie stacji roboczej połączonych z Internetem**

    -   **Generuj i transfer klucza dzierżawcy — w Internecie**: **Przygotowanie stacji roboczej odłączonego**

    Nie podlegają kroki, aby wygenerować klucz dzierżawy, ponieważ istnieje już odpowiednik w pliku konfiguracyjnym wyeksportowanych danych (XML). Zamiast tego zostanie Uruchom polecenie, aby wyodrębnić ten klucz z pliku i zaimportuj go w sieci lokalnej HSM.

2.  Na stacji roboczej odłączony uruchom następujące polecenie:

    ```
    KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath <TPD> -ProtectionPassword -KeyIdentifier <KeyID> -ExchangeKeyPackage <BYOK-KEK-pka-Region> -NewSecurityWorldPackage <BYOK-SecurityWorld-pkg-Region>
    ```
    Na przykład dla Ameryki Północnej: **KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath E:\contosokey1.xml -ProtectionPassword -KeyIdentifier contosorms1key –- -ExchangeKeyPackage &lt;BYOK-KEK-pka-NA-1&gt; -NewSecurityWorldPackage &lt;BYOK-SecurityWorld-pkg-NA-1&gt;**

    Informacje dodatkowe:

    -   Parametr ImportRmsCentrallyManagedKey oznacza operację zaimportować klucza certyfikat licencjodawcy serwera.

    -   Jeśli hasło nie zostanie określony w poleceniu, pojawi się monit go określić.

    -   Parametr KeyIdentifier jest dla klucza przyjaznej nazwy, która tworzy nazwę pliku klucza. Musi zawierać tylko małe znaki ASCII.

    -   Parametr ExchangeKeyPackage określa pakietem (KEK) klucza wymiany kluczy określonego regionu nazwisko zaczynające BYOK-KEK - Fully Packaged-.

    -   Parametr NewSecurityWorldPackage określa pakietem world zabezpieczeń określonego regionu nazwisko zaczynające BYOK-SecurityWorld - Fully Packaged-.

    To polecenie powoduje następujące czynności:

    -   Plik klucza HSM: %NFAST_KMDATA%\local\key_mscapi_ &lt; identyfikator klucza &gt;

    -   Plik danych konfiguracji usług RMS z certyfikat licencjodawcy serwera usunięte: %NFAST_KMDATA%\local\no_key_tpd_ &lt; identyfikator klucza &gt; .xml

3.  Jeśli masz więcej niż jeden pliki danych konfiguracji usług RMS w pozostałej części te pliki należy powtórzyć krok 2.

Teraz, dzięki czemu klucza na podstawie HSM wyodrębnieniu swoje certyfikat licencjodawcy serwera, możesz przystąpić do pakietu i przenieść ją do usług Azure RMS.

###### Część 2: Pakiet i przenieść klucz HSM do usług Azure RMS

1.  Wykonaj poniższe kroki z [Implementing bring your own key (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) części [Planowanie i wdrażanie swoim kluczem dzierżawcy zarządzania prawami Azure](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md):

    -   **Generuj i transfer klucza dzierżawcy — w Internecie**: **Przygotowanie klucz dzierżawcy w celu przeniesienia**

    -   **Generuj i transfer klucza dzierżawcy — w Internecie**: **Przenieś klucz dzierżawcy do usług Azure RMS**

Teraz, gdy klucz HSM zostały przeniesione do usług Azure RMS, możesz zaimportować danych konfiguracji usług AD RMS, które zawiera tylko wskaźnik do klucza nowo transferowane dzierżawy.

###### Część 3: Importowanie danych konfiguracji z usług Azure RMS

1.  Nadal na stacji roboczej połączonych z Internetem i w sesji środowiska Windows PowerShell kopiować pliki konfiguracji usług RMS z certyfikat licencjodawcy serwera usunięte (z odłączonym workstation %NFAST_KMDATA%\local\no_key_tpd_ &lt; identyfikator klucza &gt; .xml)

2.  Przekaż plik. Jeśli masz więcej niż jeden plik .xml, ponieważ miał wiele zaufanych domen publikacji, wybierz plik zawierający wyeksportowany zaufanej domeny publikacji, która odpowiada kluczowi HSM, którego chcesz użyć w usług Azure RMS na potrzeby ochrony zawartości po migracji. Za pomocą następującego polecenia:

    ```
    Import-AadrmTpd -TpdFile <PathToNoKeyTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToKeyTransferPackage> -Active $true -Verbose
    ```
    Na przykład: **Import -TpdFile E:\no_key_tpd_contosorms1key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $true -Verbose**

    Po wyświetleniu monitu wprowadź hasło, które określony wcześniej i potwierdzenie do wykonania tej akcji.

3.  Po zakończeniu działania polecenia, powtórz krok 2 dla każdego pozostałe plik XML, który został utworzony przez wyeksportowanie zaufanej domeny publikacji. Ale tych plików, należy ustawić **-Active** do **false** po uruchomieniu polecenia importu. Na przykład: **Import -TpdFile E:\no_key_tpd_contosorms2key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $false -Verbose**

4.  Użyj [AadrmService rozłączenia](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) rozłączyć się z usługą Azure RMS przy użyciu polecenia cmdlet:

    ```
    Disconnect-AadrmService
    ```

Teraz możesz przejść do [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).

### <a name="BKMK_Step3Migration"></a>Krok 3. Aktywuj dzierżawcy RMS
Instrukcje dla tego kroku są w pełni objęte [Aktywowanie Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md) tematu.

> [!TIP]
> Jeśli masz subskrypcję usługi Office 365, można aktywować usług Azure RMS z Centrum administracyjnym usługi Office 365 lub klasycznego portalu Azure. Zaleca się używanie klasycznego portalu Azure, ponieważ ten portal zarządzania będą używane do zakończenia następnego kroku.

**Co zrobić, jeśli dzierżawcy usług Azure RMS został już aktywowany?** Jeśli usługa Azure RMS został już aktywowany dla Twojej organizacji, użytkownicy już zajęte usług Azure RMS na potrzeby ochrony zawartości z kluczem automatycznie generowanych dzierżawy (i domyślnych szablonów) zamiast istniejące klucze (i szablony) z usług AD RMS. Jest to prawdopodobne na komputerach, które są dobrze zarządzanej w sieci intranet, ponieważ to zostaną automatycznie skonfigurowane w infrastrukturze usług AD RMS. Jednak może się zdarzyć, na komputerach grupy roboczej lub komputerów, które rzadko łączą się z siecią intranet. Niestety jest również trudne do identyfikowania tych komputerów tworzonym zaleca się, że nie aktywować usługę przed importowaniem danych konfiguracji z usług AD RMS.

Jeśli dzierżawcy usług Azure RMS został już aktywowany, można zidentyfikować te komputery upewnij się, uruchom skrypt CleanUpRMS_RUN_Elevated.cmd na tych komputerach, zgodnie z opisem w kroku 5. Uruchomienie tego skryptu wymusza, aby ponownie zainicjować środowiska użytkownika tak, aby ich pobrać klucz dzierżawcy zaktualizowanej i importowanych szablonów.

### <a name="BKMK_Step4Migration"></a>Krok 4. Konfigurowanie importowanych szablonów
Ponieważ szablonów, które zostały zaimportowane ma domyślny stan **archiwizacji**, należy zmienić ten stan się **opublikowaną** Jeśli chcesz, aby użytkownicy mogli używać tych szablonów z usług Azure RMS.

Ponadto, jeśli używane szablony w usługach AD RMS **ANYONE** grupa ta grupa zostanie automatycznie usunięta po zaimportowaniu szablony do usług Azure RMS, należy ręcznie dodać równoważne grup i użytkowników oraz te same prawa do importowanych szablonów. Równoważne grupy dla usług Azure RMS nosi nazwę **AllStaff-&lt;tenant_GUID&gt;@&lt;tenant_name&gt;.onmicrosoft.com**. Na przykład, ta grupa może wyglądać podobnie do poniższego "contoso": **AllStaff-9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a@contoso.onmicrosoft.com**.

Jeśli nie masz pewności, czy dołączyć grupy Każdy szablonów usług AD RMS, rozwiń  [PowerShell script to identify AD RMS templates that include the ANYONE group](#BKMK_ScriptForANYONE) części ten krok, aby kopiować i używać przykładowy skrypt programu PowerShell, aby zidentyfikować te szablony. Aby uzyskać więcej informacji o używaniu środowiska Windows PowerShell z usługami AD RMS, zobacz  [przy użyciu programu Windows PowerShell do administrowania usługami AD RMS](https://technet.microsoft.com/library/ee221079%28v=ws.10%29.aspx).

Zobaczysz organizacji użytkownika utworzony automatycznie grupy skopiować jedną z domyślnych szablonów zasad praw w klasycznym portalu Azure, a następnie Zidentyfikuj **Nazwa użytkownika** na **prawa** strony. Jednak nie można użyć klasycznego portalu do dodania tej grupy do szablonu, który został utworzony ręcznie lub zaimportować i zamiast tego należy użyć jednej z następujących opcji Azure RMS PowerShell:

-   Użyj [AadrmRightsDefinition nowy](https://msdn.microsoft.com/library/azure/dn727080.aspx) polecenia cmdlet środowiska PowerShell do definiowania grupy "AllStaff" i prawa jako obiekt definicji prawa i uruchom ponownie to polecenie dla każdej grupy lub użytkownicy już prawa w oryginalnym szablonie oprócz grupy ANYONE. Następnie dodaj wszystkie te obiekty definicji prawa do szablonów przy użyciu  [Set AadrmTemplateProperty](https://msdn.microsoft.com/en-us/library/azure/dn727076.aspx) polecenia cmdlet.

-   Użyj [AadrmTemplate eksportu](https://msdn.microsoft.com/library/azure/dn727078.aspx) Eksportuj szablon do przy użyciu polecenia cmdlet. Plik XML, który można edytować, aby dodać grupy "AllStaff" i prawa do istniejących grup i uprawnień, a następnie użyj [AadrmTemplate importowania](https://msdn.microsoft.com/library/azure/dn727077.aspx) polecenia cmdlet do importowania tej zmiany z powrotem do usług Azure RMS.

> [!NOTE]
> Ta grupa równoważne "AllStaff" nie jest dokładnie taki sam, jak grupy usług AD RMS w ANYONE:  "AllStaff" grupy należą wszyscy użytkownicy w tej dzierżawie Azure grupy każdy obejmuje wszystkie uwierzytelnionym użytkownikom, którzy mogą być spoza organizacji.
> 
> Ta różnica między dwiema grupami może być konieczne również dodać użytkowników zewnętrznych oprócz grupy "AllStaff". Adresy e-mail zewnętrzne dla grup nie są obecnie obsługiwane.

Szablony, które można zaimportować z usług AD RMS wyglądają i zachowują się tak samo jak niestandardowe szablony utworzone w portalu Azure klasycznego. Aby zmienić importowanych szablonów do opublikowania, dzięki czemu użytkownicy mogą je widzieć i zaznacz je z aplikacji lub do wprowadzania zmian do szablonów, zobacz [Konfigurowanie niestandardowych szablonów Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

> [!TIP]
> Bardziej spójne środowisko dla użytkowników podczas procesu migracji nie należy wprowadzać zmian do importowanych szablonów innych niż te dwie zmiany. nie Publikuj dwa domyślne szablony dostarczane z usług Azure RMS i tworzyć nowe szablony w tej chwili. Zamiast tego poczekaj na zakończeniu procesu migracji i mieć zlikwidowana serwerów usług AD RMS.

#### <a name="BKMK_ScriptForANYONE"></a>Przykładowy skrypt programu Windows PowerShell, aby zidentyfikować szablony usług AD RMS, które zawierają grupy ANYONE
Ta sekcja zawiera przykładowy skrypt, aby pomóc w zidentyfikowaniu szablonów usług AD RMS, które mają grupy ANYONE zdefiniowane, zgodnie z opisem w poprzedniej sekcji.

*&#42;&#42;Zastrzeżenie:&#42;&#42; Ten przykładowy skrypt nie jest obsługiwana w ramach Microsoft standardowym programem ani usługi. Ten przykładowy skrypt jest dostarczany jako IS bez jakiejkolwiek gwarancji.*

```
import-module adrmsadmin New-PSDrive -Name MyRmsAdmin -PsProvider AdRmsAdmin -Root https://localhost -Force $ListofTemplates=dir MyRmsAdmin:\RightsPolicyTemplate foreach($Template in $ListofTemplates) { $templateID=$Template.id $rights = dir MyRmsAdmin:\RightsPolicyTemplate\$Templateid\userright $templateName=$Template.DefaultDisplayName if ($rights.usergroupname -eq "anyone") { $templateName = $Template.defaultdisplayname write-host "Template " -NoNewline write-host -NoNewline $templateName -ForegroundColor Red write-host " contains rights for " -NoNewline write-host ANYONE  -ForegroundColor Red } } Remove-PSDrive MyRmsAdmin -force
```

### <a name="BKMK_Step5Migration"></a>Krok 5. Ponownie skonfigurować klientów do używania usług Azure RMS
Dla klientów systemu Windows:

1.  [Pobierz skrypty migracji](http://go.microsoft.com/fwlink/?LinkId=524619):

    -   CleanUpRMS_RUN_Elevated.cmd

    -   Redirect_OnPrem.cmd

    Skrypty te Zresetuj konfigurację na komputerach z systemem Windows, dzięki czemu będą korzystali z usług Azure RMS, a nie usług AD RMS.

2.  Postępuj zgodnie z instrukcjami w skrypcie przekierowania (Redirect_OnPrem.cmd), aby zmodyfikować skrypt, aby wskazywały nowy dzierżawcy usług Azure RMS.

3.  Na komputerach z systemem Windows uruchamiać te skrypty z podwyższonym poziomem uprawnień w kontekście użytkownika.

Dla klientów urządzeń przenośnych i komputerów Mac:

-   Usuwanie rekordów DNS SRV, które zostały utworzone podczas wdrażania [rozszerzenia usług AD RMS dla urządzeń przenośnych](http://technet.microsoft.com/library/dn673574.aspx).

#### Zmiany wprowadzone przez skrypty migracji
W tej sekcji omówiono zmian skryptów migracji. Te informacje można użyć tylko w celach informacyjnych, lub w celu rozwiązania problemu lub jeśli wolisz te zmiany samodzielnie.

CleanUpRMS_RUN_Elevated.cmd:

-   Usuń zawartość folderów %userprofile%\AppData\Local\Microsoft\DRM i %userprofile%\AppData\Local\Microsoft\MSIPC, w tym wszystkie podfoldery i pliki o długich nazw plików.

-   Usuń zawartość następujących kluczy rejestru:

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation

    -   HKEY_LOCAL_MACHINE\SOFTWARE\WoW6432Node\Microsoft\MSIPC\ServiceLocation

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation

-   Usuń następujące wartości rejestru:

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServerURL

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServer

Redirect_OnPrem.cmd:

-   Utwórz następujące wartości rejestru dla każdego adresu URL dostarczany jako parametr w każdym z następujących lokalizacji:

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\ (11.0|12.0|14.0) \Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\LicensingRedirection

    Każdy wpis ma wartość REG_SZ **https://OldRMSserverURL/_wmcs/licensing** z danymi w następującym formacie: **https://&lt;YourTenantURL&gt;/_wmcs/licensing**.

    > [!NOTE]
    > *&lt; YourTenantURL &gt;* ma następujący format: **{identyfikator GUID} .rms. [Region].aadrm.com**.
    > 
    > Na przykład:  5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com
    > 
    > Tę wartość można znaleźć, określając **RightsManagementServiceId** wartość po uruchomieniu [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) polecenia cmdlet dla usług Azure RMS.

### <a name="BKMK_Step6Migration"></a>Krok 6. Konfigurowanie integracji prawami do programu Exchange Online
Jeśli wcześniej zaimportowano TDP użytkownika z usług AD RMS do usługi Exchange Online, należy usunąć ten TDP, aby uniknąć szablony powodujące konflikt i zasad po wykonaniu migracji do usługi Azure RMS. Aby to zrobić, użyj [RMSTrustedPublishingDomain Usuń](https://technet.microsoft.com/en-us/library/jj200720%28v=exchg.150%29.aspx) polecenia cmdlet z usługą Exchange Online.

W przypadku wybrania usług Azure RMS dzierżawy klucza topologii **Microsoft zarządzane**:

-   Zobacz [Exchange Online: Konfiguracja usługi IRM](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_ExchangeOnline) w sekcji [Konfigurowanie aplikacji Azure Rights Management](../Topic/Configuring_Applications_for_Azure_Rights_Management.md) tematu. Ta sekcja zawiera typowe polecenie do uruchomienia, które łączy się z usługą Exchange Online, importuje klucz dzierżawcy z usług Azure RMS i włącza funkcję prawami do programu Exchange Online. Po wykonaniu tych kroków należy pełną funkcjonalność usług RMS z usługą Exchange Online.

W przypadku wybrania usług Azure RMS dzierżawy klucza topologii **klientów zarządzanych (BYOK)**:

-   Możesz mieć zmniejszy funkcjonalność usług RMS z usługą Exchange Online zgodnie z opisem w [BYOK pricing and restrictions](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing) w sekcji [Planowanie i wdrażanie swoim kluczem dzierżawcy zarządzania prawami Azure](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) tematu.

### <a name="BKMK_Step7Migration"></a>Krok 7. Wdrażanie łącznika usług RMS
W przypadku użycia funkcji zarządzania prawami do informacji (IRM) programu Exchange Server lub serwer programu SharePoint za pomocą usług AD RMS, możesz wyłączyć IRM na tych serwerach i usunięcia konfiguracji usług AD RMS. Następnie można wdrożyć łącznik Rights Management (RMS), który działa jako interfejs komunikacji (przekazywanie) między na serwerach lokalnych i usług Azure RMS.

Na koniec tego kroku, jeśli wiele zaufanych domen publikacji zostały zaimportowane do usług Azure RMS, które zostały użyte do ochrony wiadomości e-mail, można ręcznie zmodyfikować rejestru na komputerach serwera Exchange, aby przekierować wszystkie adresy URL zaufanych domen publikacji z łącznikiem usług RMS.

> [!NOTE]
> Przed rozpoczęciem Sprawdź obsługiwane wersje serwerów lokalnych, które obsługuje łącznika usług RMS w "lokalnych serwerów obsługujących usług Azure RMS" w [Aplikacje, które obsługują Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedApplications) części [Wymagania dotyczące systemu Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tematu.

##### Wyłącz IRM na serwerach programu Exchange i Usuń konfiguracji usług AD RMS

1.  Na każdym serwerze Exchange zlokalizuj następujący folder i Usuń wszystkie wpisy w tym folderze: \ProgramData\Microsoft\DRM\Server\S-1-5-18

2.  Jeden z serwerów programu Exchange, należy użyć programu Exchange [Set_IRMConfiguration](http://technet.microsoft.com/library/dd979792.aspx) najpierw wyłączyć IRM przy użyciu polecenia cmdlet funkcji dla komunikatów wysyłanych do adresatów wewnętrznych:

    ```
    Set-IRMConfiguration -InternalLicensingEnabled $false
    ```

3.  Następnie użyć tych samych poleceń cmdlet, aby wyłączyć funkcje IRM dla komunikatów wysyłanych do adresatów zewnętrznych:

    ```
    Set-IRMConfiguration -ExternalLicensingEnabled $false
    ```

4.  Następnie można użyć tych samych poleceń cmdlet, aby wyłączyć IRM w aplikacji sieci Web programu Microsoft Office Outlook i Microsoft Exchange ActiveSync:

    ```
    Set-IRMConfiguration -ClientAccessServerEnabled $false
    ```

5.  Wreszcie należy użyć polecenia cmdlet tej samej wyczyścić wszystkie certyfikaty przechowywane w buforze:

    ```
    Set-IRMConfiguration -RefreshServerCertificates
    ```

6.  Na każdym serwerze Exchange teraz zresetować usługi IIS, na przykład uruchomiony z wiersza polecenia jako administrator, a następnie wpisując **iisreset**.

##### Wyłącz IRM na serwerach programu SharePoint i Usuń konfiguracji usług AD RMS

1.  Upewnij się, że nie ma żadnych dokumentów wyewidencjonowany z bibliotek chronionego przez usługi RMS. Jeśli istnieją, staną się one być niedostępne na końcu tej procedury.

2.  W programie SharePoint sieci Web administracji centralnej lokacji w **Szybkie uruchamianie** kliknij przycisk **zabezpieczeń**.

3.  Na **zabezpieczeń** strony w **zasad informacji** kliknij przycisk **skonfigurować zarządzanie prawami do informacji**.

4.  Na **Zarządzanie prawami do informacji** strony w **Zarządzanie prawami do informacji** zaznacz **nie korzystać z tej funkcji na tym serwerze**, następnie kliknij przycisk **OK**.

5.  Na każdym komputerze serwera programu SharePoint, usuń zawartość tego folderu \ProgramData\Microsoft\MSIPC\Server\*&lt; identyfikator SID konta z programem SharePoint Server &gt;*.

##### Instalowanie i Konfigurowanie łącznika usług RMS

-   Postępuj zgodnie z instrukcjami w [Łącznik zarządzania Azure prawa wdrażania](../Topic/Deploying_the_Azure_Rights_Management_Connector.md) tematu.

##### Tylko wymiany i wiele zaufanych domen publikacji: Dokonaj edycji rejestru

-   Na każdym serwerze Exchange należy ręcznie dodać następujące klucze rejestru, dla każdego dodatkowego zaufaną domenę publikacji zaimportowanego, przekierowywanie adresów URL zaufaną domenę publikacji z łącznikiem usług RMS. Te wpisy rejestru są specyficzne dla migracji i nie są dodawane przez narzędzie do konfiguracji serwera Microsoft RMS łącznika.

    Po wprowadzeniu tych zmian rejestru, wykonaj następujące instrukcje:

    -   Zastąp *ConnectorFQDN* o nazwie zdefiniowanego w systemie DNS dla łącznika. Na przykład **rmsconnector.contoso.com**.

    -   Użyj prefiksu protokołu HTTP lub HTTPS dla adresu URL łącznika, w zależności od tego, czy skonfigurowano łącznik do używania protokołu HTTP lub HTTPS do komunikacji z serwerów lokalnych.

    **Dla programu Exchange 2013:**

    |Ścieżki rejestru|Typ|Wartość|Danych|
    |--------------------|-------|-----------|----------|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;AD URL licencjonowania Intranet RMS &gt;/_wmcs/licensing|Jeden z następujących elementów, w zależności od tego, czy używasz protokołu HTTP lub HTTPS z serwerem Exchange z łącznikiem usług RMS:<br /><br />-   http://&lt;connectorFQDN&gt;/_wmcs/licensing<br />-   https://&lt;connectorName&gt;/_wmcs/licensing|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;AD ekstranetu URL licencjonowania usług RMS &gt;/_wmcs/licensing|Jeden z następujących elementów, w zależności od tego, czy używasz protokołu HTTP lub HTTPS z serwerem Exchange z łącznikiem usług RMS:<br /><br />-   http://&lt;connectorFQDN&gt;/_wmcs/licensing<br />-   https://&lt;connectorFQDN&gt;/_wmcs/licensing|
    **Exchange Server 2010:**

    |Ścieżki rejestru|Typ|Wartość|Danych|
    |--------------------|-------|-----------|----------|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;AD URL licencjonowania Intranet RMS &gt;/_wmcs/licensing|Jeden z następujących elementów, w zależności od tego, czy używasz protokołu HTTP lub HTTPS z serwerem Exchange z łącznikiem usług RMS:<br /><br />-   http://&lt;connectorName&gt;/_wmcs/licensing<br />-   https://&lt;connectorName&gt;/_wmcs/licensing|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;AD ekstranetu URL licencjonowania usług RMS &gt;/_wmcs/licensing|Jeden z następujących elementów, w zależności od tego, czy używasz protokołu HTTP lub HTTPS z serwerem Exchange z łącznikiem usług RMS:<br /><br />-   http://&lt;connectorName&gt;/_wmcs/licensing<br />-   https://&lt;connectorName&gt;/_wmcs/licensing|

Po wykonaniu tych procedur należy przeczytać **Następne kroki** w sekcji [Łącznik zarządzania Azure prawa wdrażania](../Topic/Deploying_the_Azure_Rights_Management_Connector.md) tematu.

### <a name="BKMK_Step8Migration"></a>Krok 8. Likwidowanie usług AD RMS
Opcjonalne: Usuń punkt połączenia usługi (SCP) z usługi Active Directory, aby uniemożliwić komputerom odnajdywanie infrastruktury lokalnej Rights Management. Jest to opcjonalne z powodu przekierowania, który został skonfigurowany w rejestrze (na przykład przez uruchomienie skryptu migracji). Aby usunąć punkt połączenia usługi, użyj narzędzia zarejestrować punkt połączenia usługi AD z [Toolkit administracji usług zarządzania prawami](http://www.microsoft.com/download/details.aspx?id=1479).

Monitorowanie serwerów usług AD RMS dla działania, na przykład, sprawdzając [żądań raportu o kondycji systemu](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx),  [żądania obsługi tabeli](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx) lub [inspekcji dostępu użytkownika do chronionej zawartości](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx). Po potwierdzeniu, że klienci usług RMS nie jest już komunikację z te serwery i klienci pomyślnie używa usług Azure RMS, możesz usunąć rolę serwera AD RMS z tych serwera. Jeśli używasz dedykowanych serwerach, można wybrać ostrzegawcze kroku pierwszy zamykanie serwery w danym okresie czasu, aby upewnić się, że nie ma żadnych zgłoszonych problemów, które mogą wymagać ponownego uruchamiania tych serwerów w celu zapewnienia ciągłości usługi podczas badania, dlaczego klienci nie korzystają z usług Azure RMS.

Po likwidacji serwerów usług AD RMS, można podjąć możliwość Przejrzyj szablony w portalu Azure klasycznego i konsolidować je, aby użytkownicy mieli mniej, aby wybrać, lub skonfigurować je ponownie lub nawet dodawać nowych szablonów. Będzie to również odpowiedni moment, aby opublikować domyślnych szablonów. Aby uzyskać więcej informacji, zobacz [Konfigurowanie niestandardowych szablonów Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

### <a name="BKMK_Step9Migration"></a>Krok 9. Ponownie klucz klucz dzierżawy usługi Azure RMS
Ten krok jest wymagany, po zakończeniu migracji wdrożenia usług AD RMS został używania usług RMS kryptograficznych tryb 1, ponieważ kluczy ponownych tworzy nowy klucz dzierżawy, który korzysta z usług RMS trybu kryptograficznego 2. Za pomocą usług Azure RMS z 1 trybu kryptograficznego jest obsługiwana tylko podczas procesu migracji.

Ta czynność jest opcjonalna, ale zalecana po zakończeniu migracji, nawet jeśli były uruchomione RMS trybu kryptograficznego 2, ponieważ ułatwia zabezpieczenie usług Azure RMS klucz dzierżawcy z potencjalnych naruszeń zabezpieczeń do klucza usług AD RMS. Gdy ponownie klawisz klucz dzierżawy usługi Azure RMS (znanej także jako "stopniowe klucz"), tworzony jest nowy klucz i oryginalny klucz zostaną zarchiwizowane. Jednak ponieważ przechodzenia z jednego klucza do innego niezbyt natychmiast, ale przez kilka tygodni nie czekać należy podejrzewać naruszenie do oryginalnego klucza, ale zaraz po zakończeniu migracji kluczy ponownych klucz dzierżawcy usługi RMS.

Aby ponownie klucz klucz dzierżawy usługi Azure RMS:

-   Jeśli klucz dzierżawcy usługi RMS jest zarządzany przez firmę Microsoft: Wywołania usług pomocy technicznej firmy Microsoft (CSS) i potwierdzić, że jesteś administratorem dzierżawy usługi RMS.

-   Jeśli klucz dzierżawcy usługi RMS jest zarządzany przez użytkownika (BYOK): Powtórz procedurę BYOK do generowania i Utwórz nowy klucz w Internecie lub w osoby.

Aby uzyskać więcej informacji o zarządzaniu klucz dzierżawcy usługi RMS, zobacz [Operacje dla klucza dzierżawcy zarządzania prawami systemu Azure](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md).

## Zobacz też
[Konfigurowanie Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

