---
description: na
keywords: na
title: Rights Management sharing application administrator guide
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d9992e30-f3d1-48d5-aedc-4e721f7d7c25
---
# Przewodnik administratora aplikacji udostępniania zarządzania prawami dostępu
Użyj poniższych informacji, czy użytkownik jest odpowiedzialny za Microsoft Rights Management, udostępnianie aplikacji w sieci przedsiębiorstwa, czy ma więcej informacji technicznych nie znajduje się w [Przewodnik użytkownika aplikacji udostępniania zarządzania prawami dostępu](../Topic/Rights_Management_sharing_application_user_guide.md) lub [często zadawane pytania dotyczące Microsoft prawa udostępniania aplikacji dla systemu Windows do zarządzania](http://go.microsoft.com/fwlink/?LinkId=303971):

-   [Automatyczne wdrażanie firmy Microsoft Rights Management, udostępnianie aplikacji](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_ScriptedInstall)

    -   [Trwa weryfikowanie powodzenia instalacji](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted)

    -   [Odinstaluj polecenia](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_uninstallscripted)

    -   [Pomijanie aktualizacje automatyczne](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SuppressAutomaticUpdates)

    -   [Tylko Azure RMS: Konfigurowanie śledzenia dokumentu](#BKMK_DocumentTracking)

    -   [Usług AD RMS tylko: Obsługa wielu domen poczty e-mail w ramach danej organizacji](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_FederatedDomains)

-   [Opis techniczny oprogramowania Microsoft Rights Management, udostępnianie aplikacji](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_AdminOverview)

    -   [Poziom ochrony — macierzystego i ogólny](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_LevelsofProtection)

    -   [Obsługiwane typy plików i rozszerzeń nazw plików](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SupportFileTypes)

    -   [Zmiana domyślny poziom ochrony plików](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_ChangeDefaultProtection)

> [!TIP]
> Jeśli korzystasz z aplikacji udostępniania RMS lub wyszukiwania, aby uzyskać więcej informacji, zobacz [jak RMS chroni wszystkie typy plików — za pomocą aplikacji RMS sharing](https://curah.microsoft.com/191031/how-rms-protects-all-file-types-by-using-the-rms-sharing-app).

RMS sharing aplikacji jest dostosowane do pracy z Azure RMS, ponieważ ta konfiguracja wdrożenia obsługuje wysyłania chronionych załączniki do użytkowników w innej organizacji i opcje, takie jak powiadomienia e-mail i śledzenia z odwołania dokumentu.  Jednak z pewnymi ograniczeniami działa w wersji lokalnych usług AD RMS. Kompleksowe porównanie funkcji, które są obsługiwane przez Azure RMS i AD RMS, zobacz [Porównanie Azure Rights Management i usług AD RMS](https://technet.microsoft.com/library/jj739831.aspx). Jeśli masz usług AD RMS i chcesz dokonać migracji do usług RMS Azure, zobacz [migracji z usług AD RMS do Azure Rights Management](https://technet.microsoft.com/library/dn858447.aspx).

## <a name="BKMK_ScriptedInstall"></a>Automatyczne wdrażanie firmy Microsoft Rights Management, udostępnianie aplikacji
Wersja systemu Windows udostępniania aplikacji RMS obsługuje przy użyciu skryptu instalacji, co pozwala na odpowiedni w przypadku wdrożeń.

Tylko wymagania wstępne dotyczące instalacji są, czy komputery Uruchom minimalnej wersji systemu Windows 7 z dodatkiem SP1 i że Framework firmy Microsoft, minimalnej wersji 4.0 jest zainstalowany. Jeśli należy zainstalować program Microsoft .NET Framework 4.0, możesz [pobrać instalacja z witryny Microsoft Center Download](http://www.microsoft.com/download/details.aspx?id=17718).

#### Aby pobrać RMS sharing aplikacji do automatycznego wdrażania

1.  Przejdź do [Microsoft Rights Management aplikacji dla systemu Windows do udostępniania](http://www.microsoft.com/download/details.aspx?id=40857) strony Center Download firmy Microsoft, a następnie kliknij przycisk **Pobierz**.

2.  Wybierz i pobierania plików, które są potrzebne. Istnieją dwie pakietów instalacyjnych klienta: jeden dla Windows 64-bit (Microsoft Rights Management udostępniania x64.zip aplikacji), a druga dla systemu Windows 32-bitowe (Microsoft Rights Management udostępnianie x86.zip aplikacji).

3.  Wyodrębnij pliki z pakiety skompresowane instalacji, na przykład dwukrotne kliknięcie. Następnie skopiuj wyodrębnione pliki do lokalizacji sieciowej, która może uzyskać dostęp do komputerów klienckich.

Pakiety instalacyjne dla aplikacji do udostępniania RMS obsługuje różnych scenariuszy wdrażania i znajdują się następujące informacje:

|Opis|Scenariusz wdrażania|
|--------|------------------------|
|Microsoft Online Asystenta logowania|Wymagana dla następujących czynności:<br /><br />-   Pakiet Office 2010 i Azure RMS<br />-   Office 2013 i Azure RMS, jeśli nie jest zainstalowany [9 czerwca 2015 aktualizacji dla pakietu Office 2013](https://support.microsoft.com/kb/3054853) (KB3054853)|
|Poprawka dla pakietu Office (KB 2596501)|Wymagana dla następujących czynności:<br /><br />-   Pakiet Office 2010 i Azure RMS<br />-   RMS pakietu Office 2010 i usługi Active Directory|
|Poprawka, aby włączyć klienta AD RMS 1.0 do pracy z Azure RMS (KB 2843630)|Wymagana dla następujących czynności:<br /><br />-   Pakiet Office 2010 i Azure RMS<br />-   RMS pakietu Office 2010 i usługi Active Directory|
|Klienta AD RMS i RMS sharing aplikacji|Wymagana dla następujących czynności:<br /><br />-   2016 Office roku lub pakietu Office 2013 i Azure RMS lub RMS usługi Active Directory<br />-   Pakiet Office 2010 i Azure RMS<br />-   RMS pakietu Office 2010 i usługi Active Directory<br />-   Udostępnianie aplikacji i pakietu Office dodatku tylko RMS|
|Dodatek Office dla wstążki|Wymagana dla następujących czynności:<br /><br />-   2016 Office roku lub pakietu Office 2013 i Azure RMS lub RMS usługi Active Directory<br />-   Pakiet Office 2010 i Azure RMS<br />-   RMS pakietu Office 2010 i usługi Active Directory<br />-   Udostępnianie aplikacji i pakietu Office dodatku tylko RMS|
|Narzędzie do przygotowywania Azure zarządzania prawami dostępu w usłudze Active Directory|Wymagana dla następujących czynności:<br /><br />-   Pakiet Office 2010 i Azure RMS|
Użyj następujących procedur, aby zidentyfikować polecenia wymagane do wdrożenia RMS sharing aplikacji dla tych scenariuszy wdrażania:

-   **2016 Office roku lub pakietu Office 2013 i Azure RMS lub RMS usługi Active Directory**

    Użytkownicy są uruchomione 2016 Office roku lub Office 2013, Twoja organizacja korzysta Azure RMS lub RMS usługi Active Directory, a użytkownicy współpracować z innymi organizacjami korzystający z Azure RMS lub RMS usługi Active Directory.

-   **Pakiet Office 2010 i Azure RMS**

    Użytkownicy są uruchomione pakietu Office 2010, używana Azure RMS w organizacji, a użytkownicy współpracować z innymi organizacjami korzystający z Azure RMS lub RMS usługi Active Directory.

-   **RMS pakietu Office 2010 i usługi Active Directory**

    Użytkownicy są uruchomione pakietu Office 2010, Twoja organizacja korzysta z usług AD RMS, a użytkownicy współpracować z innymi organizacjami korzystający z Azure RMS.

-   **Udostępnianie aplikacji i pakietu Office dodatku tylko RMS**

    Użytkownicy w systemie Office 2016 roku, pakietu Office 2013 lub pakietu Office 2010, Twoja organizacja korzysta z usług AD RMS i użytkowników nie ma potrzeby współpracować z innymi organizacjami korzystający z Azure RMS. Ta instalacja pozwala zainstalować tylko na udostępnianie aplikacji i dodatek do pakietu Office.

> [!NOTE]
> W tych scenariuszach organizacji działa usług AD RMS, użytkownicy mogą otrzymywać chronionej zawartości z innymi organizacji korzystający z Azure RMS, ale użytkownicy nie może wysyłać chronionej zawartości użytkownikom w organizacji używająca Azure RMS. Jednak jeśli w organizacji jest uruchomiona Azure RMS, użytkownicy mogą wysyłanie i odbieranie chronionej zawartości z innymi organizacji.

Aby ukończyć instalację, dla każdej procedury, należy ponownie uruchomić komputer. Można to zrobić automatyczne ponowne uruchomienie za pomocą polecenia takie jak zamknięcie /i.

#### Aby wdrożyć RMS sharing aplikacji Office 2016 roku lub Office 2013 i Azure RMS RMS usługi Active Directory

-   Na każdym komputerze, na którym chcesz zainstalować RMS aplikacji i składników pokrewnych uruchom następujące polecenie z podniesionymi uprawnieniami:

    ```
    setup.exe /s
    ```

Aby sprawdzić sukces, zobacz [Trwa weryfikowanie powodzenia instalacji](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) w tym temacie.

#### Aby wdrożyć RMS sharing aplikacji dla pakietu Office 2010 i Azure RMS

1.  Musi być administratora globalnego dla dzierżawy usługi Office 365 lub Azure Active Directory, tak aby mogli uzyskać adres URL usługi certyfikacji w organizacji, należy uruchomić narzędzie przygotowywania Azure Active Directory Rights Management. To narzędzie należy uruchomić tylko raz na jednym komputerze. Adres URL usługi certyfikacji ma być używany podczas zainstalować RMS aplikacji na każdym komputerze:

    1.  Zaloguj się do komputera przy użyciu konta administratora lokalnego.

    2.  Na tym komputerze [pobierze i zainstaluje Online Asystent logowania w witrynie Microsoft](http://www.microsoft.com/download/details.aspx?id=28177).

    3.  Uruchom następujące polecenie, aby wyświetlić wyświetlanego na ekranie URL usługi certyfikacji, który można kopiować i Zapisz się do kolejnego kroku:

        -   Dla Windows 8.1 i Windows 8, 64-bitowy:

            ```
            x64\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   Dla systemu Windows 8.1 i Windows 8, 32-bitowy:

            ```
            X86\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   Dla systemu Windows 7, 64-bitowy:

            ```
            x64\win7\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        > [!NOTE]
        > To polecenie mogą wyświetlić monit o wprowadzenie poświadczeń dla systemu Azure. Jeśli komputer nie jest przyłączony do domeny, zostanie wyświetlony monit. Jeśli komputer jest przyłączony do domeny, narzędzie może mieć możliwość korzystania poświadczenia z pamięci podręcznej.

2.  Na każdym komputerze, na którym zostanie zainstalowany RMS sharing aplikacji uruchom następujące polecenie z podniesionymi uprawnieniami:

    ```
    setup.exe /s /configureO2010Admin /certificationUrl <certification_url>
    ```

3.  Na każdym komputerze, na którym zostanie zainstalowany RMS sharing aplikacji, użytkownicy muszą uruchom następujące polecenie (nie jest konieczne podwyższonych uprawnień). Istnieją różne sposoby, można to osiągnąć, łącznie z zapytaniem użytkownikom Uruchom polecenie (na przykład łącze w wiadomości e-mail lub łącze w portalu pomocy technicznej) lub można go dodać do ich skryptu logowania:

    ```
    bin\RMSSetup.exe /configureO2010Only
    ```

Aby sprawdzić sukces, zobacz [Trwa weryfikowanie powodzenia instalacji](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) w tym temacie.

#### Aby wdrożyć RMS sharing aplikacji dla pakietu Office 2010 i RMS usługi Active Directory

1.  Na każdym komputerze, na którym zostanie zainstalowany RMS sharing aplikacji uruchom następujące polecenie z podniesionymi uprawnieniami:

    ```
    setup.exe /s /configureO2010Admin
    ```

2.  Na każdym komputerze, na którym zostanie zainstalowany RMS sharing aplikacji, użytkownicy muszą uruchom następujące polecenie (nie jest konieczne podwyższonych uprawnień). Istnieją różne sposoby, można to osiągnąć, łącznie z zapytaniem użytkownikom Uruchom polecenie (na przykład łącze w wiadomości e-mail lub łącze w portalu pomocy technicznej) lub można go dodać do ich skryptu logowania:

    -   Windows 10, Windows 8.1 i Windows 8, 64-bitowy:

        ```
        x64\aadrmprep.exe /configureO2010
        ```

    -   10 systemu Windows, Windows 8.1 i Windows 8, 32-bitowy:

        ```
        X86\aadrmprep.exe /configureO2010
        ```

    -   Dla systemu Windows 7, 64-bitowy:

        ```
        x64\win7\aadrmpep.exe /configureO2010
        ```

Aby sprawdzić sukces, zobacz [Trwa weryfikowanie powodzenia instalacji](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) w tym temacie.

#### Aby zainstalować i aplikacji Office dodatku tylko RMS

1.  Instalowanie klienta AD RMS i RMS sharing aplikacji przy użyciu następującego polecenia:

    -   64-bitowym systemie operacyjnym Windows:

        ```
        x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    -   Dla 32-bitowego systemu Windows:

        ```
        X86\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    Na przykład: `\\server5\apps\rms\x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "C:\Log files\ipviewerinstall.log"`

2.  Zainstaluj dodatek pakietu Office, korzystając z następujących poleceń:

    -   64-bitowej wersji pakietu Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "<log file path and name>"
        ```

    -   32-bitowej wersji pakietu Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x86\Setup.msi" /L*v "<log file path and name>"
        ```

    Na przykład: `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "C:\Log files\rmsofficeinstall.log"`

Aby sprawdzić sukces, zobacz [Trwa weryfikowanie powodzenia instalacji](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) w tym temacie.

### <a name="BKMK_verifyscripted"></a>Trwa weryfikowanie powodzenia instalacji
Pliki dziennika instalacji umożliwia Sprawdź instalacja przebiegła pomyślnie.

##### Aby sprawdzić powodzenia instalacji dla RMS sharing aplikacji Office 2016 roku lub Office 2013 i Azure RMS RMS usługi Active Directory

-   Można zweryfikować sukces polecenia Setup.exe, na każdym komputerze wyszukać plik dziennika instalacji **RMInstaller.log** w *%temp%\RMS_installer_ &lt; guid &gt;* folderu, a następnie zidentyfikować kod wyjścia.

    Instalacja przebiegła pomyślnie ma kod zakończenia 0 oraz dowolną inną liczbę wskazuje niepowodzenia instalacji.

    Nazwa pliku dziennika w przykładzie: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0\RMInstaller.log**

##### Aby sprawdzić powodzenia instalacji dla RMS sharing aplikacji dla pakietu Office 2010 i Azure RMS

1.  Można zweryfikować sukces polecenia Setup.exe, na każdym komputerze wyszukać plik dziennika instalacji **RMInstaller.log** w *%temp%\RMS_installer_ &lt; guid &gt;* folderu, a następnie zidentyfikować kod wyjścia.

    Instalacja przebiegła pomyślnie ma kod zakończenia 0 oraz dowolną inną liczbę wskazuje niepowodzenia instalacji.

    Nazwa pliku dziennika w przykładzie: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  Aby sprawdzić sukces polecenia RMSSetup.exe, użytkownik musi mieć następujące pliki utworzone w ich *%localappdata%\microsoft\drm* folder:

    -   CERTYFIKAT Machine-2048.drm

    -   Machine.drm certyfikatu

    -   CLC &#42;.drm

    -   WKL &#42;.drm

    Przykład pliku CLC &#42;.drm:

    **.Drm CLC-alice@isvtenant999.onmicrosoft.com-{1b9cfccf k5b11; k4a10; kac15; k29b2b6980f4c}**

##### Aby sprawdzić powodzenia instalacji dla RMS sharing aplikacji dla pakietu Office 2010 i RMS usługi Active Directory

1.  Aby sprawdzić sukces polecenia Setup.exe, na każdym komputerze wyszukiwania w pliku dziennika instalacji *%temp%\RMS_installer_ &lt; guid &gt;* folderu i identyfikację kod zakończenia.

    Instalacja przebiegła pomyślnie ma kod zakończenia 0 oraz dowolną inną liczbę wskazuje niepowodzenia instalacji.

    Nazwa pliku dziennika w przykładzie: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  Aby sprawdzić sukces polecenia aadrmprep.exe, na każdym komputerze Wyszukaj następujący tekst w pliku dziennika instalacji: **aadrmprep.exe został zakończony z stan powodzenia**

    > [!NOTE]
    > Czasami tej instalacji można uruchomić dwukrotnie; pierwsze wystąpienie nie powiedzie się, a drugą zakończy się pomyślnie.

    Jeśli chcesz ręcznie sprawdzić zmian w rejestrze, które narzędzie to sprawia, że są one w następujący sposób:

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\Federation]

        "FederationHomeRealm"="urn: HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\Federation]

        "FederationHomeRealm"="urn: HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation]

        @= "&lt; adres url certyfikacji &gt;"

    -   [HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\14.0\Common\DRM]

        Domyślny = "&lt; default_user &gt;"

##### Aby sprawdzić powodzenia instalacji dla RMS sharing i aplikacji Office dodatku tylko

1.  Aby sprawdzić sukces polecenia Setup_ipviewer.exe, Wyszukaj następujący tekst w pliku dziennika instalacji: **Stan powodzenia lub błędu instalacji: 0**

    Przykład wiersze z powodzenia instalacji:

    **MSI (s) (F0:B8) [14:19:57:854]: Produkt: Active Directory Rights Management Services Client 2.1 — Instalacja została ukończona pomyślnie.**

    **MSI (s) (F0:B8) [14:19:57:854]: Instalator Windows zainstalował produkt. Nazwa produktu: Usługa Active Directory Rights Management Services Client 2.1. Wersja produktu: 1.0.1179.1. Język produktu: 1033. Producent: Firma Microsoft Corporation. Stan powodzenia lub błędu instalacji: 0.**

2.  Wyszukaj następujący tekst w pliku dziennika instalacji można zweryfikować powodzenia Office dodatku, na każdym komputerze: **Stan powodzenia lub błędu instalacji: 0**

    Przykład wiersze z powodzenia instalacji:

    **MSI (s) (9C: 88) [18:49:04:007]: Produkt: Dodatki Microsoft RMS Office — Instalacja została ukończona pomyślnie.**

    **MSI (s) (9C: 88) [18:49:04:007]: Instalator Windows zainstalował produkt. Nazwa produktu: Dodatki pakietu Office RMS firmy Microsoft. Wersja produktu: 1.0.7. Język produktu: 1033. Producent: Firmy Microsoft. Stan powodzenia lub błędu instalacji: 0.**

### <a name="BKMK_uninstallscripted"></a>Odinstaluj polecenia
Nie wszystkie wymagane do wdrożenia tych poleceń instalacji obsługują polecenie dezinstalacji. Można odinstalować klienta usług AD RMS i udostępniania aplikacji i można odinstalować dodatek pakietu Office. Za pomocą następujących poleceń odinstalować tych elementów.

##### Aby odinstalować klienta AD RMS i RMS sharing aplikacji

-   Użyj następujących poleceń:

    -   64-bitowym systemie operacyjnym Windows:

        ```
        x64\setup_ipviewer.exe /uninstall /quiet
        ```

    -   Dla 32-bitowego systemu Windows:

        ```
        x86\setup_ipviewer.exe /uninstall /quiet
        ```

##### Aby odinstalować dodatek pakietu Office

-   Użyj następujących poleceń:

    -   64-bitowej wersji pakietu Office:

        ```
        msiexec /x \x64\Setup[64].msi /quiet
        ```

    -   32-bitowej wersji pakietu Office:

        ```
        msiexec /x \x86\Setup.msi /quiet
        ```

### <a name="BKMK_SuppressAutomaticUpdates"></a>Pomijanie aktualizacje automatyczne
Domyślnie użytkownicy są powiadomienie, jeśli istnieje nowsza wersja aplikacji RMS udostępniania i pojawi się monit, aby ją pobrać. Można pominąć tego powiadomienia o następującą wartość rejestru edytować:

1.  Przejdź do **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC** i jeśli nie już istnieje, Utwórz nowy klucz o nazwie **RmsSharingApp**.

2.  Wybierz **RmsSharingApp**, Utwórz nową wartość DWORD **AllowUpdatePrompt**, a wartość **0**.

Udostępniania aplikacji RMS nie jest obsługiwane przez program WSUS, można użyć następujących techniki do przetestowania wszystkich nowych wersji RMS sharing aplikacji przed wdrożeniem go do wszystkich użytkowników:

1.  Komputery, na wszystkich użytkowników należy uruchomić skrypt, aby pominąć aktualizacje automatyczne. Komputery, na które Administratorzy używać do testowania nowych wersji które nie działają ten skrypt.

2.  Jeśli dostępna jest nowa wersja, Administratorzy pobrać i należy przeprowadzić test.

3.  Po zakończeniu testowania i wszelkie problemy rozwiązane, wdrożyć najnowszą wersję wszystkim użytkownikom za pomocą instrukcji automatycznego wdrażania tego podręcznika.

### <a name="BKMK_DocumentTracking"></a>Tylko Azure RMS: Konfigurowanie śledzenia dokumentu
Jeśli masz [subskrypcji obsługującego śledzenia dokumentu](https://technet.microsoft.com/en-us/dn858608), śledzenia dokumentów witryny jest włączona domyślnie dla wszystkich użytkowników w Twojej organizacji.  Śledzenia dokumentu zawiera informacje, takie jak adresy e-mail osób, które próbowano uzyskać dostęp do chronionych dokumentów użytkowników udostępniony, podczas próby dostępu oraz ich lokalizacji tych osób. Jeśli te informacje są wyświetlane jest zabroniona w organizacji z powodu wymagania ochrony prywatności, można wyłączyć dostęp do dokumentu śledzenia witryny za pomocą  [Disable AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623032) polecenia cmdlet. W dowolnej chwili można ponownie włączyć dostęp do witryny, za pomocą [AadrmDocumentTrackingFeature Włącz](http://go.microsoft.com/fwlink/?LinkId=623037), i można sprawdzić, czy dostęp jest aktualnie włączone lub wyłączone przy użyciu [Get-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623037).

 Aby uruchomić te aplety poleceń, użytkownik musi mieć przynajmniej wersja **2.3.0.0** modułu Azure RMS środowiska Windows PowerShell.  Instrukcje instalacji, zobacz [instalowania programu Windows PowerShell Azure Rights Management](https://technet.microsoft.com/library/jj585012.aspx).

> [!TIP]
> Jeśli wcześniej zostały pobrane i zainstalowane moduł, sprawdź numer wersji, uruchamiając: `(Get-Module aadrm –ListAvailable).Version`

Następujące adresy URL są używane do śledzenia dokumentów i prawem (na przykład, dodaj je do magazynu zaufanych witryn w przypadku korzystania z programu Internet Explorer z ze zwiększonymi zabezpieczeniami):

-   https://&#42;.azurerms.com

-   https://ecn.dev.virtualearth.net

    > [!NOTE]
    > ten adres URL jest zestaw Bing maps.

-   https://&#42;.microsoftonline.com

-   https://&#42;.microsoftonline-p.com

### <a name="BKMK_FederatedDomains"></a>Usług AD RMS tylko: Obsługa wielu domen poczty e-mail w ramach danej organizacji
Jeśli używasz usług AD RMS i użytkowników w Twojej organizacji ma wiele domen poczty e-mail, co w wyniku połączenia lub przejęcia, należy wykonać następującą wartość rejestru edytować:

1.  Przejdź do **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC** i jeśli nie już istnieje, Utwórz nowy klucz o nazwie **RmsSharingApp**.

2.  Wybierz **RmsSharingApp**, Utwórz nową wartość ciągu wielokrotnego o nazwie **FederatedDomains**, a następnie dodaj domeny i wszystkich poddomen używanymi w organizacji. Symbole wieloznaczne nie są obsługiwane.

    Na przykład: Firmy winnic Hurtownia &amp; Winery ma domenę standardowych wiadomości e-mail z **cohovineyardandwinery.com**, ale w wyniku łączenia, domen poczty e-mail również użyć **cohowinery.com**, **eastcoast.cohowinery.com**, i **cohovineyard**. Dla **FederatedDomains** wartości danych, administrator wprowadza: **cohowinery.com; eastcoast.cohowinery.com; cohovineyard**

Jeśli nie dokonasz tej zmiany rejestru, użytkowników może nie móc korzystać z zawartości, która jest chroniony przez innych użytkowników w organizacji. Ta edycja rejestru nie jest wymagana, jeśli używasz Azure RMS.

## <a name="BKMK_AdminOverview"></a>Opis techniczny oprogramowania Microsoft Rights Management, udostępnianie aplikacji
Microsoft Rights Management, udostępnianie aplikacji jest opcjonalne do pobrania aplikacji systemu Microsoft Windows oraz innych platform, która zapewnia następujące możliwości:

-   Ochrona danych jednego pliku lub zbiorczego ochrony wielu plików także jako wszystkie pliki w ramach wybranego folderu.

-   Pełna obsługa ochrony dowolnego typu pliku i wbudowane podglądu często używanych typów plików tekstowych i graficznych.

-   Ogólny ochronę plików, które nie obsługują ochrony RMS.

-   Pełne współdziałanie z plików chronionych za pomocą pakietu Office informacji zarządzania prawami dostępu.

-   Pełne współdziałanie z chronione przy użyciu programu SharePoint, FCI i PDF obsługiwane narzędzia do tworzenia plików PDF.

Microsoft Rights Management aplikacji do udostępniania korzysta z nowego [środowiska wykonawczego klienta usług AD RMS 2.1](http://www.microsoft.com/download/details.aspx?id=38396). Za pomocą funkcji usług AD RMS 2.1, Microsoft Rights Management aplikacji do udostępniania oferuje użytkownikom końcowym prosty interfejs ochrony i zużycie.

Wraz z wydaniem październik 2013 RMS można sposób macierzysty chronić dokumenty za pomocą pakietu Office 2010 i wysyłać je do osób w innej firmy, który następnie mogą wykorzystywać przy użyciu Azure RMS. Ponadto w tej wersji, korzystając z usług AD RMS w kryptograficznego trybu 2, może być używany RMS dla osób i korzystać z zawartości od osób w innej firmy, która używa Azure RMS. Więcej informacji na temat kryptograficznych 2 tryb w temacie [AD RMS kryptograficznych tryby](http://technet.microsoft.com/library/hh867439%28v=ws.10%29.aspx).

### <a name="BKMK_LevelsofProtection"></a>Poziom ochrony — macierzystego i ogólny
Microsoft Rights Management aplikacji do udostępniania obsługuje funkcję ochrony na dwóch różnych poziomach, zgodnie z opisem w poniższej tabeli.

|Typ ochrony|Macierzysty|Ogólne|
|---------------|---------------|----------|
|Opis|Tekst, obraz, Microsoft Office (Word, Excel, PowerPoint) pliki, pliki PDF i innych typów plików aplikacji obsługujących usług AD RMS ochrony macierzystego zapewnia wysoki poziom ochrony, który obejmuje zarówno szyfrowania i stosowania praw (uprawnienia).|Wszystkie inne aplikacje i typów plików ogólny ochrony zapewnia poziom ochrony, który obejmuje zarówno hermetyzacji pliku za pomocą pfile typu pliku i uwierzytelniania, aby sprawdzić, czy użytkownik jest autoryzowany do otwierania tego pliku.|
|Ochrony|Pliki w pełni są szyfrowane i ochrony jest wymuszany w następujący sposób:<br /><br />-   Przed renderowaniem jest chronionej zawartości, pomyślnym uwierzytelnieniu musi przypadać dla osób, które zostało odebrane pliku za pośrednictwem poczty e-mail lub są podane do niego dostępu za pomocą uprawnień plików lub udział.<br />-   Ponadto prawa użytkowania i zasad ustawionych przez właściciela zawartości, gdy pliki są chronione w pełni są wymuszane podczas odtwarzania zawartości w trybie podglądu IP (dla chronionych plików tekstowych i graficznych) lub skojarzonej aplikacji (dla wszystkich innych obsługiwanych typów plików).|Ochrona plików jest wymuszany w następujący sposób:<br /><br />-   Przed renderowaniem jest chronionej zawartości, pomyślnym uwierzytelnieniu musi przypadać dla tych, którzy mają autoryzację do otwierania tego pliku i biorąc pod uwagę dostęp do niego. Jeśli autoryzacja nie powiedzie się, kończy się niepowodzeniem.<br />-   Informowanie autoryzowanych użytkowników zasady przeznaczenia są wyświetlane praw użytkowania i zasad ustawionych przez właściciela zawartości.<br />-   Występuje, rejestrowanie inspekcji autoryzowanych użytkowników, otwierając okno i dostęp do plików, jednak nie praw użytkowania są wymuszane przez — Obsługa aplikacji.|
|Domyślny dla typów plików|Jest to domyślny poziom ochrony dla następujących typów plików:<br /><br />-   Tekst i pliki obrazów<br />-   Pliki programu Microsoft Office (Word, Excel, PowerPoint)<br />-   Format dokumentów przenośnych (PDF)<br /><br />Aby uzyskać więcej informacji, zobacz sekcji poniżej [Obsługiwane typy plików i rozszerzeń nazw plików](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SupportFileTypes).|Jest to domyślną ochronę dla wszystkich pozostałych typów plików (takich jak .vsdx, RTF itd.) nie są obsługiwane za pośrednictwem pełnej ochrony.|
Można zmienić domyślny poziom ochrony stosowanym udostępniania aplikacji RMS. Można zmienić domyślny poziom natywne ogólny, z ogólnymi dla macierzystego, a nawet uniemożliwiają RMS sharing aplikacji ze stosowania ochrony. Aby uzyskać więcej informacji, zobacz [Zmiana domyślny poziom ochrony plików](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_ChangeDefaultProtection) w tym temacie.

### <a name="BKMK_SupportFileTypes"></a>Obsługiwane typy plików i rozszerzeń nazw plików
Poniższa tabela zawiera listę typów plików, które są obsługiwane przez aplikację udostępniania Microsoft Rights Management. Dla tych typów plików oryginalne rozszerzenie nazwy pliku jest zmieniany, gdy stosowany jest chroniona w trybie macierzystym, a te pliki stają się tylko do odczytu.

Ponadto RMS sharing aplikacji w sposób macierzysty chroni użytkowników chronić udostępniania pliku Word, Excel lub PowerPoint, ta akcja automatycznie tworzy drugi plik, który jest kopią oryginalnego o takiej samej nazwie pliku, ale z **.ppdf** ¹. rozszerzenie nazwy pliku. Tę wersję pliku powoduje, że adresatów, do których zainstalować aplikację RMS zawsze można otworzyć plik, który ma macierzystego ochrony stosowane.

W przypadku plików chronionych ogólnego oryginalne rozszerzenia nazwy pliku zawsze jest zmieniana na pfile.

> [!WARNING]
> Jeśli użytkownik ma zapory, serwery proxy sieci web lub zabezpieczeń oprogramowania Zbadaj i podjąć działania zgodnie z rozszerzeń nazw plików, konieczne może być ponownie skonfigurować je do obsługi tych nowych rozszerzeń nazw plików.

|Oryginalne rozszerzenia nazwy pliku|Rozszerzenie nazwy pliku chronionego RMS|
|---------------------------------------|--------------------------------------------|
|.txt|.ptxt|
|XML|.pxml|
|jpg|.pjpg|
|JPEG|.ppng|
|PDF|.ppdf|
|.PNG|.ppng|
|TIFF|.ptiff|
|.bmp|.pbmp|
|.GIF|.pgif|
|.giff|.pgiff|
|.jpe|.pjpe|
|.jfif|.pjfif|
|.jif|.pjif|
|.JT|.pjt|
¹ renderowanie plików PDF obsługiwane przez technologię Foxit. Copyright © 2003-2014 Foxit Corporation.

Poniższa tabela zawiera listę typów plików, które aplikacji Microsoft Rights Management udostępniania w sposób macierzysty obsługuje w 2016 roku pakietu Microsoft Office, Office 2013 i Office 2010. W przypadku tych plików rozszerzenia nazwy pliku nie zmienia się po plik jest chroniony przez RMS.

|Typy plików obsługiwanych przez pakiet Office|Typy plików obsługiwanych przez pakiet Office|
|-------------------------------------------------|-------------------------------------------------|
|doc<br /><br />docm<br /><br />.docx<br /><br />dot<br /><br />dotm<br /><br />dotx<br /><br />.potm<br /><br />.potx<br /><br />.pps<br /><br />.ppsm<br /><br />ppsx<br /><br />ppt<br /><br />.pptm|pptx<br /><br />.thmx<br /><br />.xla<br /><br />.xlam<br /><br />xls<br /><br />xlsb<br /><br />.xlt<br /><br />xlsm<br /><br />xlsx<br /><br />xltm<br /><br />xltx<br /><br />XPS|

### <a name="BKMK_ChangeDefaultProtection"></a>Zmiana domyślny poziom ochrony plików
Możesz zmienić sposób RMS sharing aplikacji chroni pliki, edytując rejestr. Na przykład można wymusić plików, które obsługują macierzystego ochrony ogólnego chronionych przez aplikację RMS udostępniania.

Przyczyny, dlaczego warto to zrobić:

-   Aby upewnić się, że wszyscy użytkownicy można otworzyć pliku z urządzeniami przenośnymi.

-   Aby upewnić się, wszyscy użytkownicy umożliwiającej otwarcie tego pliku, jeśli nie mają aplikacji, która obsługuje macierzystego ochrony.

-   Aby uwzględnić systemów zabezpieczeń, które zająć się plików przez ich rozszerzenia nazwy pliku i zostać skonfigurowane ponownie, aby uwzględnić rozszerzenie nazwy pliku pfile, ale nie może zostać skonfigurowane ponownie, aby obsłużyć wiele rozszerzeń nazw plików do ochrony macierzystego.

Podobnie można wymusić RMS sharing aplikacji do zastosowania ochrony macierzystego do plików, które domyślnie miałoby ogólnego ochrony zastosowane. Może to być odpowiednie, jeśli masz aplikacji, która obsługuje RMS interfejsów API — na przykład,-biznesowych zapisywanych przez deweloperów wewnętrzny lub aplikacja nabywane w niezależny producent oprogramowania (ISV).

Można także wymusić RMS sharing aplikacji, aby zablokować ochrony plików (dotyczy ochrony macierzystego lub ochrony ogólny). Na przykład może to być wymagane w przypadku automatyczne aplikacji lub usługi, która musi być w stanie można otworzyć określonego pliku do przetwarzania jego zawartość. Blokowanie ochrony dla typu pliku, użytkownicy nie mogą używać RMS sharing aplikacji do ochrony pliku z danym typem pliku. Podczas prób, użytkownicy widzą komunikat, że administrator zablokował ochrony i anulować ich działania w celu ochrony pliku.

Aby skonfigurować RMS sharing aplikacji do zastosowania do wszystkich plików, które domyślnie będą miały macierzystego ochrony stosowane ogólnego ochrony, powodują, że następujące edycji rejestru:

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection**: Utwórz nowy klucz o nazwie **&#42;**.

    To ustawienie oznacza pliki z rozszerzenie nazwy pliku.

2.  Nowo dodanego klucza w **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\ &#42;**, Utwórz nową wartość ciągu (REG_SZ) o nazwie **szyfrowania** ma wartość danych równą **Pfile**.

    To ustawienie powoduje RMS sharing ochrona ogólnego zastosowania aplikacji.

Te dwie wartości spowodować RMS sharing aplikacji ochrony ogólnego zastosowania do wszystkich plików, które mają rozszerzenie nazwy pliku. Jeśli to jest zadaniem gracza, konfiguracja nie dalszych jest wymagany. Jednak można zdefiniować wyjątki dla określonych typów plików, tak aby nadal w sposób macierzysty są chronione. W tym celu należy wykonać trzy edycji rejestru dodatkowe w przypadku każdego typu pliku:

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection**: Dodaj nowy klucz o nazwie rozszerzenie nazwy pliku (bez poprzedniego okresu).

    Na przykład w przypadku plików, które mają .docx, rozszerzenia nazwy pliku, Utwórz klucz o nazwie **DOCX**.

2.  Klucz typu nowo dodanego pliku (na przykład **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\DOCX**), Utwórz nową wartość DWORD o nazwie **AllowPFILEEncryption** który ma wartość **0**.

3.  Klucz typu nowo dodanego pliku (na przykład **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\DOCX**), Utwórz nową wartość ciągu o nazwie **szyfrowania** który ma wartość **macierzystego**.

W wyniku tych ustawień wszystkie pliki ogólnego są chronione oprócz plików, które mają rozszerzenie nazwy pliku .docx macierzyście chronionych przez aplikację udostępniania RMS.

Powtórz te trzy kroki dla innych typów plików, które chcesz zdefiniować jako wyjątki, ponieważ obsługiwane macierzystego ochrony i chcesz, aby chronić ogólnego przez aplikację RMS udostępniania.

Możesz wykonać podobne edycję rejestru dla innych scenariuszach zmieniając wartość **szyfrowania** ciąg, który obsługuje następujące wartości:

-   **Pfile**: Ogólny ochrony

-   **Macierzystego**: Macierzysty ochrony

-   **Off**: Ochrona bloku

## Zobacz też
[Przewodnik użytkownika aplikacji udostępniania zarządzania prawami dostępu](../Topic/Rights_Management_sharing_application_user_guide.md)

