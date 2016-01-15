---
description: na
keywords: na
title: Requirements for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb
---
# Wymagania dotyczące systemu Azure Rights Management
Do wdrożenia systemu Microsoft Azure Rights Management (Azure RMS) w swojej organizacji, upewnij się, że następujące wymagania wstępne. Następnie można użyć [Mapa wdrożenia usługi zarządzania prawami systemu Azure](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) wdrożyć zarządzania prawami do swojej organizacji.

|Wymagania|Więcej informacji|
|-------------|---------------------|
|Chmura subskrypcję RMS|Organizacji musi mieć subskrypcji chmury, która obsługuje RMS.<br /><br />Aby uzyskać informacje dotyczące licencjonowania, zobacz [Subskrypcje chmury, które obsługują Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) w tym temacie.|
|Azure katalogu AD|Organizacji musi mieć katalog usługi Azure AD do obsługi uwierzytelniania użytkownika do usług RMS. Ponadto jeśli chcesz korzystać z kont użytkowników z katalogu lokalnego (AD DS), należy skonfigurować także Integracja katalogu.<br /><br />Uwierzytelnianie wieloskładnikowe (MFA) jest obsługiwana przez Azure RMS wymaganego oprogramowania klienckiego i poprawnie skonfigurowany infrastruktury obsługi MFA.<br /><br />Aby uzyskać więcej informacji, zobacz [Azure katalogu AD](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_AzureADTenant) w tym temacie.|
|Urządzenia klientów|Użytkownicy muszą mieć urządzeniach klienta (komputera lub urządzenia przenośnego) systemem operacyjnym, który obsługuje RMS.<br /><br />Aby uzyskać więcej informacji, zobacz [Urządzenia klientów, które obsługują Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedDevices) w tym temacie.|
|Aplikacje|Użytkownicy konieczne jest uruchomienie aplikacji obsługujących RMS.<br /><br />Aby uzyskać więcej informacji, zobacz [Aplikacje, które obsługują Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedApplications) w tym temacie.|
|Infrastrukturę, która obsługuje łączności z Internetem i usługi w chmurze zależne|Jeśli zapora lub podobnych uczestniczą urządzenia, które należy skonfigurować, aby zezwolić na określone połączenia, zobacz [adresów URL 356 pakietu Office i przedziały adresów IP](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).<br /><br />Lista adresów URL i adres IP adresów w **portalu 356 pakietu Office i tożsamości** sekcji stosuje się do portalu usługi Office 365, zasoby Azure Active Directory i Azure Rights Management. W tym artykule, wykonaj instrukcje do zachowania aktualności informacji o zmianach do tych informacji, subskrybując źródła danych RSS.<br /><br />Oprócz informacji w artykule Office, charakterystyczne dla Azure RMS:<br /><br />-   Kończy połączenie usługi klienta TLS (na przykład, czy inspekcja poziomie pakietu). Ten sposób dzieli certyfikatu przypinanie, że klienci usług RMS za pomocą CAs zarządzanych przez firmę Microsoft można zabezpieczyć ich komunikację z Azure RMS.<br />-   Nie należy używać konfiguracji serwera proxy sieci web, który jest uwierzytelniany w imieniu użytkownika.|

Jeśli chcesz Azure RMS za pomocą serwerów lokalnych są obsługiwane następujących produktów:

-   Exchange Server

-   Serwer programu SharePoint

-   Serwery plików systemu Windows Server obsługujące pliku klasyfikacji infrastruktury

Informacje dodatkowe wymagania Azure RMS w tym scenariuszu, zobacz [Lokalnych serwerach obsługujących Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedServers) w tym temacie.

> [!IMPORTANT]
> Następujący scenariusz wdrażania nie jest obsługiwany:
> 
> -   Uruchamianie usług AD RMS i Azure RMS side-by-side w tej samej organizacji, z wyjątkiem podczas migracji, zgodnie z opisem w [Migrowanie z usług AD RMS do usługi Azure Rights Management](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md).
> 
> Jest ścieżką obsługiwanych migracji [z usług AD RMS do Azure RMS](http://technet.microsoft.com/library/Dn858447.aspx), a z [Azure RMS do usług AD RMS](http://msdn.microsoft.com/library/azure/dn629429.aspx). Jeśli wdrażanie Azure RMS i zdecydować, już nie chcesz używać tej usługi w chmurze, zobacz [Likwidowanie i dezaktywowanie Azure Rights Management](../Topic/Decommissioning_and_Deactivating_Azure_Rights_Management.md).

Użyj następujące sekcje, aby dowiedzieć się więcej na temat wymagań Azure RMS.

## <a name="BKMK_SupportedSubscriptions"></a>Subskrypcje chmury, które obsługują Azure RMS
Aby korzystać z usług RMS Azure, organizacji musi mieć co najmniej jeden z następujących subskrypcji z wystarczającą liczbę licencji użytkowników i usług, które będą chronić pliki i wiadomości e-mail. Jeśli masz to usługa, która będzie stosowana ochrony dla użytkowników (właścicieli plików lub wiadomości e-mail), ci użytkownicy wymagają jednej z tych licencji. Użytkownicy, którzy zajmie tylko (na przykład do odczytu i edycji) to zabezpieczone dane nie ma potrzeby licencji.

-   Usługi Office 365

-   Azure Rights Management Premium (dawniej Azure RMS samodzielny)

-   Enterprise Suite mobilność

-   RMS dla osób

Użyj następujące sekcje, aby uzyskać więcej informacji, a następnie zaloguj się opcje.

Porównanie licencjonowania możliwości Azure RMS płatnej subskrypcji, zobacz [ofert porównanie z usług zarządzania prawami (RMS)](http://technet.microsoft.com/dn858608).

### Subskrypcja usługi Office 365
[Bezpłatna 30-dniowa wersja próbna: Enterprise E3](http://go.microsoft.com/fwlink/p/?LinkID=403802)

Ta subskrypcja jest przeznaczona dla organizacji, którzy chcą korzystać z usług online pakietu Office i używać ich funkcji zarządzania prawami do informacji, która używa Azure RMS. Nie wszystkie subskrypcje usługi Office 365 obejmują jednak Azure RMS.

|Opcja licencjonowania|Essentials biznesowych usługi Office 365|Premium biznesowych usługi Office 365|E1 Enterprise usługi Office 365<br /><br />A1 edukacyjna usługi Office 365|E3 Enterprise usługi Office 365<br /><br />A3 edukacyjna usługi Office 365<br /><br />G3 Rząd usługi Office 365|E4 Enterprise usługi Office 365<br /><br />A4 edukacyjna usługi Office 365<br /><br />G4 Rząd usługi Office 365|K1 Enterprise usługi Office 365|SharePoint Plan 1<br />programu SharePoint 2|Exchange Online planu 1<br />Exchange Online Plan 2|
|-------------------------|--------------------------------------------|-----------------------------------------|----------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|-----------------------------------|--------------------------------------------|---------------------------------------------------|
|Ochrona praw informacji (IRM)|Nr|Nr|Nr|Tak|Tak|Nr|Nr|Nr|

### Subskrypcji Rights Management Premium systemu Azure
[Bezpłatna 30-dniowa wersja próbna](https://portal.microsoftonline.com/Signup/MainSignUp15.aspx?&amp;OfferId=A43415D3-404C-4df3-B31B-AAD28118A778&amp;dl=RIGHTSMANAGEMENT&amp;ali=1)

Ta subskrypcja wcześniej Azure RMS autonomiczny i jest przeznaczony dla organizacji, które mają być używane Azure RMS, ale nie masz subskrypcji, zawierającej Azure RMS. Na przykład, jeśli masz subskrypcję dla Office 365 Business Essentials lub Office 365 Enterprise E1 te subskrypcje nie uwzględniają Azure RMS (zobacz tabelę w poprzedniej sekcji). Aby korzystać z usług RMS Azure, możesz można zakup subskrypcji systemu Azure Rights Management Premium (lub zakupu innej subskrypcji, takich jak Office 365 Enterprise E4, które obejmują Azure RMS).

Aby uzyskać więcej informacji, zobacz [Microsoft Azure Rights Management](http://products.office.com/business/microsoft-azure-rights-management).

Ta subskrypcja oferuje także okres próbny na wypróbowanie Azure RMS 25 użytkowników, bez dodatkowych kosztów. Jeśli subskrypcja wygaśnie przed Kup subskrypcję zastępczy, zobacz sekcji poniżej "co się stanie po wygaśnięciu subskrypcji wersji próbnej?"

|Opcja licencjonowania|Essentials biznesowych usługi Office 365|Premium biznesowych usługi Office 365|E1 Enterprise usługi Office 365<br /><br />A1 edukacyjna usługi Office 365|E3 Enterprise usługi Office 365<br /><br />A3 edukacyjna usługi Office 365<br /><br />G3 Rząd usługi Office 365|E4 Enterprise usługi Office 365<br /><br />A4 edukacyjna usługi Office 365<br /><br />G4 Rząd usługi Office 365|K1 Enterprise usługi Office 365|SharePoint Plan 1<br />programu SharePoint 2|Exchange Online planu 1<br />Exchange Online Plan 2|
|-------------------------|--------------------------------------------|-----------------------------------------|----------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|-----------------------------------|--------------------------------------------|---------------------------------------------------|
|Ochrona praw informacji (IRM)|Tak|Yes <sup>1</sup>|Tak|Tak|Tak|Tak|Tak|Tak|
<sup>1</sup> dla Business Premium istnieją pewne ograniczenia klienta: Możesz chronić zawartość i korzystać z chronionej zawartości z usług RMS za pomocą aplikacji sieci Web programu Outlook i aplikację RMS. Zawartość chroniona mogą wykorzystywać przy użyciu wszystkie inne aplikacje pakietu Office, co obejmuje Office Online i aplikacje klienckie dla Office 365 Business Premium.

#### <a name="BKMK_TrialExpiryBehavior"></a>Co się stanie, gdy wygaśnięcia subskrypcji wersji próbnej?
Jeśli Twoja subskrypcja wersji próbnej wygaśnie, utraci dostęp do zawartości, która była chroniona przy użyciu subskrypcji wersji próbnej dla Azure RMS. Jednakże w przypadku następnie zakupu subskrypcji, która obsługuje Azure RMS, dostępu automatycznie po przywróceniu.

Wyjątek do utraty dostępu po upływie jest czy organizacji używane Azure RMS z RMS dla osób subskrypcji przed uzyskany subskrypcji wersji próbnej. Następnie dostęp do chronionych wcześniej zawartość pozostaje, nawet po subskrypcji wersji próbnej.

### Subskrypcja pakietu mobilność Enterprise
[Bezpłatna 30-dniowa wersja próbna](http://go.microsoft.com/fwlink/?LinkId=615385)

Ta subskrypcja jest przeznaczona dla organizacji, którzy chcą korzystać z kombinacją Azure Active Directory — wersja Premium, usługa Windows Intune i Azure Rights Management. Aby uzyskać więcej informacji, zobacz [Microsoft Enterprise mobilność omówienie](http://go.microsoft.com/fwlink/?LinkId=615386).

|Opcja licencjonowania|Essentials biznesowych usługi Office 365|Premium biznesowych usługi Office 365|E1 Enterprise usługi Office 365<br /><br />A1 edukacyjna usługi Office 365|E3 Enterprise usługi Office 365<br /><br />A3 edukacyjna usługi Office 365<br /><br />G3 Rząd usługi Office 365|E4 Enterprise usługi Office 365<br /><br />A4 edukacyjna usługi Office 365<br /><br />G4 Rząd usługi Office 365|K1 Enterprise usługi Office 365|SharePoint Plan 1<br />programu SharePoint 2|Exchange Online planu 1<br />Exchange Online Plan 2|
|-------------------------|--------------------------------------------|-----------------------------------------|----------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|-----------------------------------|--------------------------------------------|---------------------------------------------------|
|Ochrona praw informacji (IRM)|Tak|Yes <sup>1</sup>|Tak|Tak|Tak|Tak|Tak|Tak|
<sup>1</sup> dla Business Premium istnieją pewne ograniczenia klienta: Możesz chronić zawartość i korzystać z chronionej zawartości z usług RMS za pomocą aplikacji sieci Web programu Outlook i aplikację RMS. Zawartość chroniona mogą wykorzystywać przy użyciu wszystkie inne aplikacje pakietu Office, co obejmuje Office Online i aplikacje klienckie dla Office 365 Business Premium.

### RMS dla osób subskrypcji
Ta subskrypcja jest przeznaczona dla użytkowników w organizacji nie wdrożono Azure RMS lub usług AD RMS. Umożliwia on te osoby do odczytu zawartość, która jest chroniony przez organizację, która używa Azure RMS, a ponadto można zabezpieczyć własną zawartość.

Aby uzyskać więcej informacji, zobacz [RMS dla osób i Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md).

## <a name="BKMK_AzureADTenant"></a>Azure katalogu AD
Musi mieć katalogu usługi Azure AD Azure RMS. Możesz używać konta organizacji dla tego katalogu do logowania do portalu zarządzania systemu Azure, gdzie, na przykład można skonfigurować i zarządzać szablony Rights Management.

Jeśli nie już masz subskrypcji systemu Azure w organizacji, możesz pobrać go za subskrybowania bezpłatnej wersji próbnej.: Przejdź do [Azure Pobierz rozpoczęto](https://account.windowsazure.com/organization) strona, a następnie postępuj zgodnie z instrukcjami.

Aby uzyskać więcej informacji zobacz następujące zasoby w dokumentacji Azure Active Directory:

-   [Co to jest katalogu Azure AD?](http://msdn.microsoft.com/en-us/library/185da266-58a9-43e6-9c66-2c8f702545c6)

-   [Jak Azure subskrypcji są skojarzone z usługą Azure AD](http://msdn.microsoft.com/en-us/library/edf05c2e-944a-4da5-a330-dc9dc479f127)

Jeśli chcesz Integracja katalogu Azure AD z użytkownika lokalnego lasów usługi AD, zobacz [Integracja katalogu](http://msdn.microsoft.com/en-us/library/bf82bdff-2467-403b-8c1a-0e9eebcf31e8).

> [!NOTE]
> Jeśli masz urządzeń przenośnych lub komputerów Mac uwierzytelnienia lokalnie przy użyciu programu AD FS lub dostawcę uwierzytelniania równoważne:
> 
> -   Należy użyć programu AD FS na minimalna wersja na **Windows Server 2012 R2**, lub dostawcy uwierzytelniania alternatywnych, który obsługuje protokołu OAuth 2.0.

### <a name="BKMK_MFA"></a>Uwierzytelnianie wieloskładnikowe (MFA) i Azure RMS
Do użycia usługi Multi-Factor authentication (MFA) z Azure RMS zgodnie z wymaganiami co najmniej jedną z następujących czynności:

-   Office 2013 (wersja minimalna):

    -   Jeśli masz pakietu Office 2013, należy także zainstalować [9 czerwca 2015 aktualizacji dla pakietu Office 2013 (KB3054853)](https://support.microsoft.com/kb/3054853). Aby uzyskać więcej informacji na temat tej aktualizacji i nowoczesnych uwierzytelniania dostarcza na podstawie Active Directory uwierzytelniania biblioteki ADAL logowania do pakietu Office 2013, zobacz [prapremiery publicznej nowoczesnych uwierzytelniania pakietu Office 2013 anonsów o](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/)  w blogu pakietu Office.

-   Rights Management udostępnianie aplikacji dla systemu Windows:

    -   Należy zainstalować minimalna wersja 1.0.1908.0, który można zatwierdzić za pomocą Panelu sterowania, programy i funkcje. Aby uzyskać więcej informacji na temat udostępniania aplikacji, zobacz  [Rights Management udostępnianie aplikacji dla systemu Windows](../Topic/Rights_Management_Sharing_Application_for_Windows.md).

-   Rights Management udostępnianie aplikacji dla urządzeń przenośnych i komputerów Mac:

    -   Upewnij się, że w najnowszej wersji. Obsługa MFA przeszła do wydania września 2015 aplikację RMS.

Następnie należy skonfigurować rozwiązanie MFA:

-   Dla dzierżawców zarządzanych przez firmę Microsoft (masz Azure Active Directory lub usługi Office 365):

    -   Skonfiguruj MFA Azure, aby wymusić MFA dla użytkowników. Aby uzyskać instrukcje, zobacz [Wprowadzenie do korzystania z uwierzytelniania wieloskładnikowego Azure w chmurze](https://azure.microsoft.com/documentation/articles/multi-factor-authentication-get-started-cloud/) z dokumentacji systemu Azure.

        Aby uzyskać więcej informacji na temat Azure MFA, zobacz [Co to jest uwierzytelnianie wieloczynnikowe Azure?](https://azure.microsoft.com/documentation/articles/multi-factor-authentication/)

-   Dla dzierżawców federacyjnych (prowadzisz Federacji serwerów lokalnych):

    -   Skonfigurować serwery Federacji Azure Active Directory lub usługi Office 365. Na przykład, jeśli używasz programu AD FS, zobacz [skonfigurować dodatkowe metody uwierzytelniania usług AD FS](https://technet.microsoft.com/library/dn758113.aspx) w witrynie TechNet.

        Aby uzyskać więcej informacji na temat tego scenariusza, zobacz  [Works za pośrednictwem usługi Office 365 — program tożsamości teraz usprawniane](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/) w blogu pakietu Office.

## <a name="BKMK_SupportedDevices"></a>Urządzenia klientów, które obsługują Azure RMS
Poniższe sekcje służą do identyfikacji urządzenia, które obsługuje Azure zarządzania prawami (RMS), i możliwości usług RMS, które obsługują:

-   [Komputery](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_RMSSupportedComputers)

-   [Urządzenia przenośne](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_RMSSupportedMobileDevices)

-   [Możliwości urządzenia klienta](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_ClientCapabilities)

### <a name="BKMK_RMSSupportedComputers"></a>Komputery
Następujące systemy operacyjne komputer obsługuje Azure Rights Management:

-   **Windows 7** (x 86, x 64)

-   **Systemu Windows 8** (x 86, x 64)

-   **Windows 8.1** (x 86, x 64)

-   **Windows 10** (x 86, x 64)

-   **Systemu Mac OS X**: Minimalna wersja systemu Mac OS X 10.8 (górski dużą)

### <a name="BKMK_RMSSupportedMobileDevices"></a>Urządzenia przenośne
Następujące systemy operacyjne urządzenia przenośnego obsługuje Azure Rights Management:

-   **Systemu Windows Phone**: Systemu Windows Phone 8.1

-   **Android telefonów i tabletów**: Minimalna wersja Android 4.0.3

-   **iPhone i iPad**: Minimalna wersja iOS 7.0

-   **Tabletów Windows RT**: RT systemu Windows 8, Windows 8.1 RT

### <a name="BKMK_ClientCapabilities"></a>Możliwości urządzenia klienta
Nie wszystkie urządzenia klienta obsługiwanych obsługują obecnie wszystkie możliwości usług RMS. Skorzystaj z poniższej tabeli, aby zidentyfikować aplikacji, które obsługuje możliwości usług RMS i wyjątków.

O ile nie zaznaczono inaczej, obsługiwane możliwości dotyczą zarówno Azure RMS i AD RMS. Ponadto wymaga usług AD RMS pomoc dotyczącą systemu iOS, Android, OS X i Windows Phone 8.1 [Active Directory prawa zarządzania usługi Mobile urządzenia rozszerzenia](http://technet.microsoft.com/library/a69ead9d-7dd3-4b38-9830-4728e9757341).

Informacje na temat kolumn tabeli.

-   **Chronione pliki PDF**: Pliki, w tym rozszerzenie nazwy pliku .ppdf, które są tworzone automatycznie podczas korzystania z RMS sharing aplikacji do udostępniania plików pakietu Office i pliki PDF pocztą e-mail. Aplikacja udostępniania RMS zawiera czytnik dla chronionych plików PDF. Wcześniej utworzono pliki PDF, które są chronione przy użyciu Azure RMS lub usług AD RMS, można odczytać przy użyciu czytnika Foxit i Nitro Pro tych plików w systemie Windows, iOS i Android.

-   **Adres e-mail:** Klienci poczty e-mail na liście możesz chronić wiadomości e-mail, który będzie automatycznie chronić wszystkie załączone pliki. W tym scenariuszu funkcji Podgląd klienta można wyświetlić chronionej zawartości (wiadomości i załączników) do autoryzowanych adresatów. Jednak jeśli samej wiadomości e-mail nie jest chroniony, ale jest chroniony załącznik, funkcji Podgląd klienta nie można wyświetlić chronionych załącznika do autoryzowanych adresatów.

-   **Innych typów plików**: Tekst i pliki obrazów obejmują pliki, których rozszerzenie nazwy pliku, takich jak txt, XML, jpg, jpeg .i. Te pliki po macierzyste są chronione przy RMS zmienić ich rozszerzenie nazwy pliku i stają się tylko do odczytu. Pliki, które nie mogą być chronione w sposób macierzysty ma rozszerzenie nazwy pliku pfile po ogólnego są chronione przy RMS. Aby uzyskać więcej informacji, zobacz [poziomy ochrony — macierzystego i ogólny](https://technet.microsoft.com/library/dn339003.aspx) i [obsługiwanych typów plików i rozszerzeń nazw plików](https://technet.microsoft.com/library/dn339003.aspx) sekcje z [Podręcznik administratora aplikacji udostępniania Rights Management](http://technet.microsoft.com/library/dn339003%28v=ws.10%29.aspx).

|**System operacyjny urządzenia**|Word, Excel, PowerPoint|Chroniony plik PDF.|Adres e-mail|Inne typy plików|
|------------------------------------|---------------------------|-----------------------|----------------|--------------------|
|**Systemu Windows**|Pakiet Office 2010<br /><br />Office 2013<br /><br />Aplikacje mobilne pakietu Office (tylko Azure RMS)<sup>1</sup><br /><br />Witryna Office Online<sup>2</sup>|Dokumenty Gaaiho<br /><br />Klient PDF GigaTrust Desktop Adobe<br /><br />Czytnik Foxit<br /><br />Nitro plików PDF<br /><br />Udostępnianie aplikacji RMS|Outlook 2010<br /><br />Outlook 2013<br /><br />Aplikacja sieci Web programu Outlook (OWA)<br /><br />Windows Mail<sup>3</sup>|RMS sharing aplikacji dla systemu Windows: Tekst, obrazy, pfile<br /><br />Siemens JT2Go: Pliki JT (tylko Windows 10)|
|**iOS**|Urząd iPad i iPhone<sup>4</sup><br /><br />Witryna Office Online<sup>2</sup><br /><br />Dokumentacja TITUS|Czytnik Foxit<br /><br />Aplikacji RMS sharing<sup>1</sup><br /><br />Dokumentacja TITUS|NitroDesk<br /><br />Program Outlook dla urządzenia iPad i iPhone<sup>3</sup><br /><br />OWA dla systemu iOS<br /><br />Wyspy IQProtector Secure<sup>1</sup><br /><br />TITUS poczty|Aplikacji RMS sharing<sup>1</sup>: Tekst, obrazy, pfile<br /><br />Dokumentacja TITUS: Pfile|
|**Android**|GigaTrust aplikacji dla systemu Android<br /><br />Witryna Office Online<sup>2</sup>|GigaTrust aplikacji dla systemu Android<br /><br />Czytnik Foxit<br /><br />Aplikacji RMS sharing<sup>1</sup>|9Folders<br /><br />GigaTrust aplikacji dla systemu Android<br /><br />NitroDesk<br /><br />OWA dla systemu Android<sup>5</sup><br /><br />Adres E-mail Samsung (S3 i nowsze)<br /><br />Wyspy IQProtector Secure<sup>1</sup><br /><br />Klasyfikacja TITUS dla urządzeń przenośnych|Aplikacji RMS sharing<sup>1</sup>: Tekst, obrazy, pfile|
|**OS X**|Office 2011 (tylko usług AD RMS)<br /><br />2016 roku Office dla komputerów Macintosh<br /><br />Witryna Office Online<sup>2</sup>|Czytnik Foxit<br /><br />Aplikacji RMS sharing<sup>1</sup>|Outlook 2011 (tylko usług AD RMS)<br /><br />2016 Outlook roku dla komputerów Macintosh<br /><br />Program Outlook dla komputerów Macintosh|Aplikacji RMS sharing<sup>1</sup>: Tekst, obrazy, pfile|
|**Systemy Windows RT**|Office 2013 RT<br /><br />Witryna Office Online<sup>2</sup>|Nie jest obsługiwany|Program Outlook 2013 RT<br /><br />Poczta aplikacji dla systemu Windows<br /><br />Windows Mail<sup>3</sup>|Siemens JT2Go: Pliki JT|
|**Systemu Windows Phone 8.1**|Office Mobile (tylko usług AD RMS)|Aplikacji RMS sharing<sup>1</sup>|Program Outlook Mobile|Aplikacji RMS sharing<sup>1</sup>: Tekst, obrazy, pfile|
|**10 urządzeń Blackberry**|Nie jest obsługiwany|Nie jest obsługiwany|Wiadomości e-mail z urządzeń Blackberry<sup>3</sup>|Nie jest obsługiwany|
<sup>1</sup> obsługuje przeglądania chronionej zawartości.

<sup>2</sup> obsługuje przeglądanie chronionej zawartości w trybie Online programu SharePoint, usługi OneDrive dla firm i Outlook Web Access.

<sup>3</sup> korzysta z programu Exchange ActiveSync IRM, który musi zostać włączone przez administratora programu Exchange. Użytkownicy mogą przeglądać, odpowiedzi i odpowiedzi, że wszystkie dla wiadomości e-mail chronionych, ale użytkownicy nie można włączyć ochrony nowych wiadomości e-mail, sami.

<sup>4</sup> dokumentów chronionych obsługuje przeglądania i edycji. Aby uzyskać więcej informacji zobacz następujące wpis w blogu Office: [Azure obsługi Rights Management jest dostarczana do pakietu Office dla urządzenia iPad i iPhone](https://blogs.office.com/2015/07/22/azure-rights-management-support-comes-to-office-for-ipad-and-iphone-2/)

<sup>5</sup> uzyskać więcej informacji, zobacz następujące wpis w blogu Office: [OWA dla systemu Android jest teraz dostępny na urządzeniach select](http://blogs.office.com/2014/06/11/owa-for-android-now-available-on-select-devices/)

> [!TIP]
> Aby uzyskać więcej informacji na temat nadchodzących obsługi usług RMS w pakiecie Office na różne platformy zobacz następujące wpis w blogu Office: [Office szeroko dostępne, szeroko dostępne szyfrowania](http://blogs.office.com/2015/02/18/office-everywhere-encryption-everywhere/)

## <a name="BKMK_SupportedApplications"></a>Aplikacje, które obsługują Azure RMS
Poniższe aplikacje obsługują Azure RMS, co oznacza, że RMS jest ściśle zintegrowany z tych aplikacji za pomocą interfejsów API usług RMS do obsługi ograniczenia użycia. Te aplikacje są również znane jako enlightened RMS:

-   **Aplikacje Microsoft Office** (Word, Excel, PowerPoint i Outlook) z następujących pakietów można chronić zawartości przy użyciu Azure RMS:

    -   Usługi Office 365 ProPlus

    -   E3 Enterprise usługi Office 365

    -   E4 Enterprise usługi Office 365

    -   Office Professional Plus 2016 roku

    -   Office Professional Plus 2013

    -   Office Professional Plus 2010

    Inne wersje pakietu Office (z wyjątkiem Office 2007) mogą wykorzystywać chronionej zawartości.

    > [!NOTE]
    > Usług Azure RMS za pomocą pakietu Office Professional Plus 2010 lub Professional pakietu Office 2010:
    > 
    > -   Wymaga Rights Management udostępnianie aplikacji dla systemu Windows
    > -   Nie jest obsługiwany w systemie Windows 10

-   **Rights Management udostępnianie aplikacji dla systemu Windows**

    Aby uzyskać więcej informacji na temat Rights Management udostępniania aplikacji dla systemu Windows zobacz następujące zasoby:

    -   [Przewodnik administratora aplikacji udostępniania zarządzania prawami dostępu](http://technet.microsoft.com/library/dn339003.aspx)

    -   [Przewodnik użytkownika aplikacji udostępniania zarządzania prawami dostępu](http://technet.microsoft.com/library/dn339006.aspx)

-   **Rights Management udostępnianie aplikacji mobilnej platformy**

    Aby uzyskać więcej informacji na temat Rights Management udostępniania aplikacji mobilnej platformy zobacz następujące zasoby:

    -   Pobierz odpowiednich aplikacji za pomocą łącza na [strony Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970)

    -   Aby zarządzać urządzeniami przenośnymi za pomocą programu Microsoft Intune, można wdrożyć i skonfigurować aplikację na [iOS i Android urządzeń jako zasadę zarządzanych aplikacji](https://technet.microsoft.com/library/dn878026.aspx).

    -   [Często zadawane pytania dotyczące Microsoft Rights Management udostępnianie aplikacji mobilnej platformy](http://technet.microsoft.com/dn451248)

-   **Inne aplikacje, które obsługują interfejsy API usług RMS**:

    -   Biznesowych aplikacji, które są zapisywane we własnym zakresie przy użyciu zestawu SDK usług RMS

    -   Aplikacje z dostawcami oprogramowania, opracowane przy użyciu zestawu SDK usług RMS

    Aby uzyskać więcej informacji o zestawie SDK, zobacz [Microsoft Rights Management SDK](http://msdn.microsoft.com/library/hh552972%28v=vs.85%29.aspx).

> [!IMPORTANT]
> Poniższe aplikacje nie są obecnie obsługiwane przez Azure RMS:
> 
> -   Microsoft Office 2011 dla komputerów Mac.
> -   Usługi OneDrive firmy Microsoft dla firm dla programu SharePoint Server 2013
> -   Przeglądarka plików XPS
> 
> Ponadto RMS sharing aplikacji ma następujące ograniczenia:
> 
> -   Komputery z systemem Windows: Wymaga minimalnej wersji systemu Windows 7 z dodatkiem SP1

Aby uzyskać więcej informacji na temat jak te aplikacje obsługują Azure RMS, zobacz [Jak aplikacje obsługują Azure Rights Management](../Topic/How_Applications_Support_Azure_Rights_Management.md).

Aby uzyskać informacje o konfigurowaniu ich, zobacz [Konfigurowanie aplikacji Azure Rights Management](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

## <a name="BKMK_SupportedServers"></a>Lokalnych serwerach obsługujących Azure RMS
Korzystając z łącznika Azure RMS, która działa jako interfejs (przekazywania) komunikacji między serwerami lokalnych i Azure RMS następujących produktów lokalnego serwera są obsługiwane Azure RMS. Ponadto ta konfiguracja wymaga skonfigurowania synchronizacji katalogu między lasów usługi Active Directory i usługi Azure Active Directory.

-   **Exchange Server**:

    -   Exchange Server 2013

    -   Exchange Server 2010

-   **Oprogramowania office SharePoint Server**:

    -   Program Office SharePoint Server 2013

    -   Program Office SharePoint Server 2010

-   **Serwery uruchamiania systemu Windows Server, a następnie użyć pliku klasyfikacji infrastruktury (FCI) plików**:

    -   Windows Server 2012 R2

    -   Windows Server 2012

    > [!NOTE]
    > Ponieważ serwery plików, z systemem Windows Server 2008 R2 nie ma Akcja zadanie zarządzania wbudowane pliku do zastosowania RMS ochrony, łącznik RMS nie można użyć dla tego scenariusza. Jednak służy plik klasyfikacji infrastruktury i Azure RMS na te systemy operacyjne w przypadku konfigurowania zadanie zarządzania niestandardowy plik, aby uruchomić plik wykonywalny lub skrypt, który można chronić pliki przy użyciu Azure RMS. Na przykład skrypt programu Windows PowerShell, który używa [polecenia cmdlet ochrony RMS](https://msdn.microsoft.com/library/azure/mt433195.aspx).
    > 
    > Można także użyć tych apletów poleceń z serwerów działających w nowszych wersjach systemu Windows Server z korzyści czy te aplety poleceń można chronić wszystkie typy plików. Łącznik RMS chroni tylko pliki pakietu Office. Aby uzyskać instrukcje dotyczące wykonywania określonych zadań, zobacz [Ochrona RMS z infrastruktury klasyfikacji plików systemu Windows Server &#40;FCI&#41;](../Topic/RMS_Protection_with_Windows_Server_File_Classification_Infrastructure__FCI_.md).

Łącznik RMS jest obsługiwana w Windows Server 2012 R2, Windows Server 2012 i Windows Server 2008 R2.

Aby uzyskać więcej informacji o sposobie konfiguracji łącznika RMS tych serwerów lokalnych, zobacz [Łącznik zarządzania Azure prawa wdrażania](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

## Zobacz też
[Wprowadzenie do korzystania z systemu Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

