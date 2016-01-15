---
description: na
keywords: na
title: How Applications Support Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2cdc7bde-4044-4021-b887-11476f99afd9
---
# Jak aplikacje obsługują Azure Rights Management
Użyj poniższych informacji, aby pomagają zrozumieć, jak aplikacje użytkownika końcowego (np. Office aplikacji, Word, Excel, PowerPoint i Outlook) i usługi (np. Exchange i programu SharePoint) używać programu Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] w celu ochrony danych w organizacji:

-   [RMS aplikacji dla systemów Windows i platform przenośnych do udostępniania](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_SharingAppIntro)

-   [Aplikacje pakietu Office: Word, Excel, PowerPoint, Outlook](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_OfficeAppsIntro)

    -   [Exchange Online i Exchange Server](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_ExchangeIntro)

    -   [SharePoint Online i programu SharePoint Server](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_SharePointIntro)

-   [Serwery plików, uruchom systemu Windows Server, a następnie użyć pliku klasyfikacji infrastruktury (FCI)](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_FCIIntro)

-   [Inne aplikacje obsługujące interfejsów API usług RMS](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_APIAppsIntro)

> [!NOTE]
> Aby sprawdzić aplikacji i wersji który [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] obsługuje (Azure RMS), zobacz [Wymagania dotyczące systemu Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

W niektórych przypadkach ochrony informacji jest automatycznie stosowane, zgodnie z zasadami, które można konfigurować. Na przykład dotyczy to z biblioteki programu SharePoint, niejawnych plików i reguły transportu Exchange. W innych przypadkach użytkownicy musi stosować ochrony informacji się z aplikacjami, wybierając szablon lub wybierając konkretne opcje. Na przykład dotyczy to w przypadku użytkowników Udostępnij plik pocztą e-mail lub ochronę plików w miejscu przez ograniczanie dostępu do lub użycia dla wybranych użytkowników lub dla użytkowników spoza organizacji.

Szablony ułatwiają dla użytkowników (i administratorów, którzy skonfigurować zasady) do zastosowania odpowiedni poziom ochrony i ograniczyć dostęp dla osób w Twojej organizacji. Chociaż [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] pochodzi z dwóch domyślnych szablonów, prawdopodobnie można utworzyć własny szablon, aby ograniczyć sytuacje, gdy mają one Określ opcje pojedynczych. Aby uzyskać więcej informacji, zobacz [Konfigurowanie niestandardowych szablonów Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

Dla przypadków, w którym użytkownicy muszą być stosowane ochrony informacji, się upewnić, że zapewnienie im uzyskać instrukcje i wskazówki dotyczące jak i kiedy w tym celu. Instrukcje powinny być specyficzne dla aplikacji i wersji, które korzystają z i jak używały, a wskazówki dotyczące po i w jaki sposób zastosować informacji ochrona powinna być właściwe dla firmy. Aby uzyskać więcej informacji, zobacz [Ułatwienie użytkownikom ochronę plików przy użyciu systemu Azure Rights Management](../Topic/Helping_Users_to_Protect_Files_by_Using_Azure_Rights_Management.md).

Aby uzyskać informacje o sposobie konfiguracji te aplikacje dla Azure RMS, zobacz [Konfigurowanie aplikacji Azure Rights Management](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

> [!TIP]
> Zrzuty ekranów aplikacji za pomocą Azure RMS i przykłady, w temacie [Azure RMS w akcji: Administratorzy i użytkownicy wyświetlanych](../Topic/What_is_Azure_Rights_Management_.md#BKMK_RMSpictures) sekcji z [Co to jest Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md) tematu.

## <a name="BKMK_SharingAppIntro"></a>RMS aplikacji dla systemów Windows i platform przenośnych do udostępniania
Aplikacja udostępniania RMS jest aplikacją bezpłatne, do pobrania, która jest wymagana do obsługi pakietu Office 2010, ale także zalecane w przypadku komputerów z systemem Windows, Mac komputerów i urządzeń przenośnych. Jeden z jego zalety znajduje się że można stosować ogólnego ochrony dla aplikacji i plików, które nie obsługują [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], co oznacza, że wszystkie pliki mogą być chronione. Aby uzyskać więcej informacji na temat różnych poziomów ochrony, zobacz [poziom ochrony — macierzystego i ogólny](http://technet.microsoft.com/library/dn339003.aspx) sekcji z [Podręcznik administratora aplikacji udostępniania Rights Management](http://technet.microsoft.com/library/dn339003.aspx).

Po użytkowników ochrony plików przy użyciu RMS udostępnianie aplikacji, mogą również śledzić dokumenty, które są chronione i w razie potrzeby odwołania do nich dostęp. Są to zrobić za pomocą [śledzenia witryny dokumentów](http://go.microsoft.com/fwlink/?LinkId=529562).

Dla komputerów z systemem Windows RMS sharing aplikacji go dyskretnie integruje się z programem i zwiększa aplikacji, które użytkownicy już używać:

-   Office dodatek programu Word, Excel, PowerPoint i Outlook jest zainstalowany. Umożliwia użytkownikom **Udostępnij chronione** przycisk na Wstążce, który wywołuje jest łatwy w użyciu okno dialogowe ustawień, które są najczęściej używane do ochrony plików do przesłane pocztą e-mail. Ten przycisk oferuje także możliwość szybkiego dostępu do witryny śledzenia dokumentu.

-   Nowa opcja kliknij prawym przyciskiem myszy plik Eksploratora. Umożliwia użytkownikom **ochrony w miejscu** opcji, która wywołuje jest łatwy w użyciu okno dialogowe ustawień, które są najczęściej używane do ochrony plików przechowywanych na dysku.

-   Podgląd do otwierania plików, które są chronione przez [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]. Ta przeglądarka automatycznie jest wywoływane, gdy nie ma innych zainstalowanej aplikacji, które można otworzyć pliku chronionego.

-   Konfiguracja wewnętrznej bazy danych dla pakietu Office 2010, który pozwala Word, Excel, PowerPoint i Outlook z tego zestawu bezproblemową pracę z [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

Chociaż RMS sharing aplikacji dla systemu Windows można pobrać i zainstalować dla pojedynczego komputera przy użyciu [strony Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970), program obsługuje wdrożenia enterprise dyskretnej instalacji i konfiguracji niestandardowej. Aby uzyskać więcej informacji zobacz następujące zasoby:

-   [Przewodnik administratora aplikacji udostępniania zarządzania prawami dostępu](http://technet.microsoft.com/library/dn339003.aspx)

-   [Przewodnik użytkownika aplikacji udostępniania zarządzania prawami dostępu](http://technet.microsoft.com/library/dn339006.aspx)

Najczęściej używane urządzeń przenośnych, takich jak iPad i iPhone, Android, Windows Phone i Windows RT. obsługuje RMS sharing aplikacji dla urządzeń przenośnych Użytkownicy mogą pobrać tej aplikacji z odpowiedniego magazynu i ma łączy do tych z [strony Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970).

## <a name="BKMK_OfficeAppsIntro"></a>Aplikacje pakietu Office: Word, Excel, PowerPoint, Outlook
Te aplikacje sposób macierzysty obsługuje Rights Management przy użyciu informacji prawa zarządzania prawami i umożliwienie użytkownikom dotyczą ochrony zapisany dokument lub wiadomość e-mail do wysłania. Użytkownicy mogą stosować szablony lub wybierz bardzo dostosowane ustawienia dla ograniczenia dostępu, prawa i użytkowania. Na przykład użytkownicy mogą skonfigurować plik, aby go można uzyskać dostęp tylko osobom w swojej organizacji lub formant czy pliku mogą być edytowane, ograniczone tylko do odczytu lub uniemożliwić drukowania. W przypadku plików zależne od czasu, można skonfigurować czas wygaśnięcia (bezpośrednio przez użytkowników lub przez zastosowanie szablonu) dla Jeśli plik nie będzie można uzyskać dostęp. Dla programu Outlook, użytkownicy mogą także określić **nie przesyłaj dalej** opcję, aby zapobiec wyciek danych.

### <a name="BKMK_ExchangeIntro"></a>Exchange Online i Exchange Server
Gdy użytkownik korzysta z programu Exchange Online lub Exchange Server, można użyć informacji prawa zarządzania prawami integracji, które znajdują się dodatkowe informacje rozwiązań ochrony:

-   **Exchange ActiveSync IRM** tak, aby urządzenia przenośne można chronić i zużywać chronić wiadomości e-mail.

-   Obsługa RMS **aplikacji sieci Web programu Outlook**, podobnie zaimplementowana na kliencie programu Outlook, użytkowników można chronić wiadomości e-mail, szablony lub podając poszczególne opcje, a użytkownicy mogą odczytywać i używać chronić wiadomości e-mail, które są wysyłane do nich.

-   **Zasad ochrony** klientów programu Outlook czy administrator skonfiguruje automatycznie zastosować szablonów usług RMS do wiadomości e-mail komunikatów dla określonego odbiorcy. Na przykład gdy wewnętrznych wiadomości e-mail są wysyłane do działu prawnych, ich mogą być odczytywane tylko przez członków działu prawnego i nie mogą być przekazywane. Użytkownicy widzą ochrony stosowane do wiadomości e-mail przed wysłaniem go, a domyślnie one go usunąć Jeśli zdecydują, że nie jest konieczne. Wiadomości e-mail są szyfrowane przed ich wysłaniem. Aby uzyskać więcej informacji, zobacz [zasad ochrony programu Outlook](http://technet.microsoft.com/library/dd638178%28v=exchg.150%29.aspx) i [utworzenia reguły ochrony programu Outlook](http://technet.microsoft.com/library/dd638196%28v=exchg.150%29.aspx) w bibliotece programu Exchange.

-   **Transportu reguły** czy administrator skonfiguruje automatycznie zastosować szablonów usług RMS do wiadomości e-mail wiadomości na podstawie właściwości, takie jak informacje o nadawcy, odbiorcy, temat wiadomości i zawartości. Te są podobne do zasad ochrony, ale nie zezwala użytkownikom usunięcia ochrony, można zastosować do programu Outlook Web Access i wiadomości e-mail wysyłanych przez urządzenia przenośne i nie szyfrowania wiadomości e-mail, zanim zostaną one wysyłane z klienta. Aby uzyskać więcej informacji, zobacz [Utwórz regułę ochrony transportu](http://technet.microsoft.com/library/dd302432.aspx) w bibliotece programu Exchange.

-   **Zasady zapobiegania (DLP) utraty danych** zawiera zestawów warunków do filtrowania wiadomości e-mail i podjąć działania pozwala uniknąć utraty danych poufnych lub poufnych zawartości (na przykład dane osobowe lub informacje o karcie kredytowej). Porady dotyczące zasad można użyć, gdy zostanie wykryty poufnych danych, informujące użytkowników, których potrzebują do zastosowania ochrony informacji, w oparciu o informacje zawarte w wiadomości e-mail. Aby uzyskać więcej informacji, zobacz [Zapobieganie utraty danych](http://technet.microsoft.com/library/jj150527%28v=exchg.150%29.aspx) w bibliotece programu Exchange.

-   **Szyfrowania wiadomości usługi office 365** że jest używana transportu reguły do wysyłania wiadomości e-mail zaszyfrowane osobom spoza swojej organizacji, a wiadomości e-mail jest do odczytu w przeglądarce z interfejsem podobne do aplikacji sieci Web programu Outlook. Można dostosować wykluczenie tekst i tekst nagłówka w wiadomości e-mail dotyczącej zaszyfrowane firmy użytkownika i nawet dodawać logo firmy. Aby uzyskać więcej informacji, zobacz [szyfrowania wiadomości usługi Office 365](http://office.microsoft.com/o365-message-encryption-FX104179182.aspx) w witrynie sieci Web pakietu Office.

Jeśli używasz programu Exchange Server, można użyć funkcji ochrony informacji o [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] wdrażając łącznika RMS, który działa jako przekazywania między serwerami lokalnych i usługi w chmurze RMS. Aby uzyskać więcej informacji, zobacz [Łącznik zarządzania Azure prawa wdrażania](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

### <a name="BKMK_SharePointIntro"></a>SharePoint Online i programu SharePoint Server
Gdy użytkownik korzysta z programu SharePoint Online lub serwer programu SharePoint, można użyć informacji o integracji zarządzania prawami prawa, którego umożliwia administratorom chronić list lub bibliotek, tak aby, gdy użytkownik sprawdzania i wyewidencjonowywanie dokumentu, plik jest chroniony, tak aby tylko autoryzowane osoby mogą przeglądać i stosować plik zgodnie z zasadami dotyczącymi ochrony informacji przez użytkownika. Na przykład plik może być tylko do odczytu, Wyłącz kopiowanie tekstu, zapobiec zapisywaniu kopii lokalnej i uniemożliwić drukowanie pliku.

List i bibliotek ochrony informacji jest wykonywana przez administratora, nie wolno użytkownika końcowego. I jest stosowana na poziomie listy lub biblioteki dla wszystkich dokumentów tego kontenera, a nie dla poszczególnych plików.  Jeśli używasz programu SharePoint Online, można także zastosować IRM do ich usługi OneDrive dla biblioteki biznesowych.

Najpierw należy włączyć usługę IRM dla programu SharePoint. Następnie należy określić zarządzania prawami do informacji w bibliotece. W przypadku programu SharePoint Online i usługi OneDrive dla firm użytkownicy mogą także określić zarządzania prawami dostępu do ich usługi OneDrive dla biblioteki biznesowych. SharePoint nie używa szablonów zasad praw, mimo że istnieją SharePoint ustawienia konfiguracji, które można wybrać zgodnych dostosowane ustawienia, które można określić w szablonach.

Jeśli używasz programu SharePoint Server, można użyć funkcji ochrony informacji o [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] wdrażając łącznika RMS, który działa jako przekazywania między serwerami lokalnych i usługi w chmurze RMS. Aby uzyskać więcej informacji, zobacz [Łącznik zarządzania Azure prawa wdrażania](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

> [!NOTE]
> Obecnie istnieją pewne ograniczenia podczas korzystać z tej funkcji z programem SharePoint:
> 
> -   Nie można użyć domyślnego lub niestandardowe szablony, którymi można zarządzać w portalu systemu Azure.
> -   Pliki, których. Rozszerzenie nazwy pliku PPDF dla chronionych plików PDF nie są obsługiwane. Pliki, które mają. Rozszerzenie nazwy pliku PDF oraz że macierzyście chronionych usługami RMS są obsługiwane, gdy użytkownik korzysta z czytnik PDF, który w sposób macierzysty obsługuje RMS.
> -   Ponieważ Office na urządzeniach przenośnych jeszcze nie obsługuje RMS, te urządzenia należy użyć przeglądarki, aby wyświetlić pliki chronione za pomocą usług RMS i pliki są tylko do odczytu.

Azure RMS stosuje ograniczenia użycia i szyfrowania danych w dokumentach pobieranego z programu SharePoint, a nie w przypadku, gdy dokument jest pierwszy utworzony w programie SharePoint lub przekazane do biblioteki. Informacje, jak dokumenty są chronione przed pobraniu, zobacz [szyfrowania danych w usługi OneDrive dla firm i SharePoint Online](https://technet.microsoft.com/library/dn905447.aspx) z dokumentacji programu SharePoint.

Aby uzyskać więcej informacji dotyczących używania usług RMS Azure z programem SharePoint zobacz następujące wpis w blogu Office: [Co nowego z zarządzania prawami dostępu w programie SharePoint i programu SharePoint Online](http://blogs.office.com/2012/11/09/whats-new-with-information-rights-management-in-sharepoint-and-sharepoint-online/)

## <a name="BKMK_FCIIntro"></a>Serwery plików, uruchom systemu Windows Server, a następnie użyć pliku klasyfikacji infrastruktury (FCI)
Po skonfigurowaniu systemu Windows Server do użycia pliku klasyfikacji infrastruktury, ta funkcja Menedżera zasobów serwera plików można skanowania plików lokalnych i określenia, czy zawierają one dane poufne. W przypadku plików spełniających kryteria tego one są oznakowane za pomocą właściwości klasyfikacji, które definiuje przez administratora. Infrastruktura klasyfikacji pliku można podjąć odpowiednie działania automatyczne, zgodnie z klasyfikacją. Obejmują jedną z następujących czynności, zastosowanie ochrony informacji przy użyciu [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] i wdrażanie łącznika Rights Management (znanego także jako łącznik RMS). Pliki pakietu Office są następnie automatycznie chronionych usługami Azure RMS.

Aby chronić wszystkich typów plików, można będzie używa łącznika RMS, ale zamiast tego uruchomić skrypt programu Windows PowerShell, za pomocą apletów poleceń z [Narzędzie ochrony RMS](https://www.microsoft.com/en-us/download/details.aspx?id=47256).

Zasady klasyfikacji są można dowolnie konfigurować, rozszerzalna co może uniemożliwić potencjalnych wyciek danych z nieautoryzowanych i autoryzowanych użytkowników. Nawet może pomóc zmniejszyć ryzyko wyciek danych przez administratorów sieci, ponieważ można skonfigurować zasady, które nie wymagają tych Administratorzy mogą mieć dostęp do plików.

Aby uzyskać instrukcje można wdrożyć i skonfigurować łącznik RMS plików pakietu Office, zobacz [Łącznik zarządzania Azure prawa wdrażania](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

Aby uzyskać instrukcje dotyczące użycia skrypt programu Windows PowerShell dla wszystkich typów plików, zobacz [Ochrona RMS z infrastruktury klasyfikacji plików systemu Windows Server &#40;FCI&#41;](../Topic/RMS_Protection_with_Windows_Server_File_Classification_Infrastructure__FCI_.md).

## <a name="BKMK_APIAppsIntro"></a>Inne aplikacje obsługujące interfejsów API usług RMS
Przy użyciu zestawu SDK usług RMS, wewnętrzny deweloperów może zapisywać-biznesowych aplikacji w sposób macierzysty obsługuje [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]. Jak ochrony informacji jest zintegrowany z tymi aplikacjami zależy od tego, jak są zapisywane. Na przykład integracji mogą być automatycznie stosowane z udziału minimalne użytkownika lub jakości bardziej dostosowane użytkowników może zostać wyświetlony monit można skonfigurować ustawienia, aby zastosować ochrony informacji w plikach. Aby uzyskać więcej informacji o zestawie SDK, zobacz [Microsoft Rights Management SDK](http://msdn.microsoft.com/library/hh552972%28v=vs.85%29.aspx).

Na tej samej zasadzie wielu dostawców oprogramowania zapewniają aplikacjom zawierają informacje rozwiązania ochrony, nazywany również enterprise rights management (ERM) produktów. Popularne przykład jest PDF, który obsługuje [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] dla określonych platform. Można użyć tabeli w [Możliwości urządzenia klienta](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_ClientCapabilities) sekcję [Wymagania dotyczące systemu Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tematu do identyfikacji aplikacji obsługujących RMS (aplikacje RMS enlightened), a następnie użyć wyszukiwania w sieci web do zakupu lub pobrać aplikacji.

> [!TIP]
> Nowo opublikowanej aplikacji można znaleźć RMS kanały społeczności, na liście [Informacje i pomoc techniczna dla usługi Azure Rights Management](../Topic/Information_and_Support_for_Azure_Rights_Management.md).

## Zobacz też
[Wprowadzenie do korzystania z systemu Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

