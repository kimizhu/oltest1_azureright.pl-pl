---
description: na
keywords: na
title: Frequently Asked Questions for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 71ce491f-41c1-4d15-9646-455a6eaa157d
---
# Często zadawane pytania dotyczące usługi Azure Rights Management
Niektóre często zadawane pytania dotyczące Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], znanego również jako usług Azure RMS:

## Co jest potrzebne do wdrożenia usług Azure RMS i jak I zacząć?
Po pierwsze, [Wymagania dotyczące systemu Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md), która zawiera informacje o opcjach subskrypcji chmury, korzystania z serwerów lokalnych z usług Azure RMS, które scenariusze wdrażania obecnie nie są obsługiwane, urządzeń i obsługi aplikacji usług Azure RMS, a także łącze w razie potrzeby listę adresów IP i nazw domen dla zapory lub serwery proxy. Można także sprawdzić w innych tematach [Wprowadzenie do korzystania z systemu Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md) sekcji, aby uzyskać podstawową wiedzą dotyczącą sposobu [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] pomaga chronić dane organizacji jak działa z aplikacjami, w jaki sposób porównuje z lokalną wersją zarządzania prawami dostępu w usłudze Active Directory i zapoznać się z warunkami i skróty, które są specyficzne dla [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

Następnie, gdy będzie gotowe do testów usług Azure RMS dla siebie, albo wdrożyć go dla Twojej organizacji, użyj [Mapa wdrożenia usługi zarządzania prawami systemu Azure](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) listę czynności wraz z łączami, aby uzyskać dalsze informacje i instrukcje instrukcje.

Aby uzyskać dodatkowe informacje, zasoby i opcje pomocy technicznej, zobacz [Informacje i pomoc techniczna dla usługi Azure Rights Management](../Topic/Information_and_Support_for_Azure_Rights_Management.md).

## Czy można zintegrować z serwerów lokalnych usług Azure RMS?
Tak. Azure RMS można zintegrować z serwerów lokalnych, takich jak serwery plików programu Exchange Server, SharePoint i Windows. Aby to zrobić, należy użyć [łącznika Rights Management](https://technet.microsoft.com/library/dn375964.aspx). Jeśli interesują tylko przy użyciu pliku klasyfikacji infrastruktury (FC) w systemie Windows Server, można użyć [poleceń cmdlet ochrony usług RMS](https://technet.microsoft.com/library/mt601315%28v=ws.10%29.aspx). Można także zsynchronizować i Federację z kontrolerami domeny usługi Active Directory z usługą Azure AD, aby usprawnić środowisko uwierzytelniania dla użytkowników, na przykład za pomocą [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/).

Azure RMS automatycznie generuje i zarządza certyfikaty XrML zgodnie z potrzebami, więc nie używa PKI lokalnie. Aby uzyskać więcej informacji o używaniu certyfikatów usług Azure RMS, zobacz [Wskazówki działania usług Azure RMS: Najpierw użyj, zawartości ochrony zawartości zużycie](../Topic/What_is_Azure_Rights_Management_.md#BKMK_Walthrough) w sekcji [Co to jest Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md) tematu.

## Masz wdrożenia hybrydowego programu Exchange z niektórych użytkowników usługi Exchange Online, a w innych na serwerze Exchange — jest to obsługiwane przez usług Azure RMS?
Absolutnie i nieuprzywilejowany operacją jest, użytkownicy będą mogli bezproblemowo chronić i korzystanie z chronionej wiadomości e-mail i załączniki przez dwa wdrożenia programu Exchange. W przypadku tej konfiguracji [usług Azure RMS Aktywuj](https://technet.microsoft.com/library/jj658941.aspx) i [Włączenie usługi IRM dla usługi Exchange Online](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx), następnie [Wdrażanie i Konfigurowanie łącznika usług RMS](https://technet.microsoft.com/library/dn375964.aspx) dla programu Exchange Server.

## Jeśli usług Azure RMS można wdrożyć w środowisku produkcyjnym, jest Moja firma zablokowane do rozwiązania lub ryzyko utraty dostępu do zawartości, którą możemy chronione za pomocą usług Azure RMS?
Nie, należy zawsze pozostają w formancie danych i może nadal dostępu do niego, nawet jeśli zdecydujesz się już używać usług Azure RMS. Aby uzyskać więcej informacji, zobacz [Likwidowanie i dezaktywowanie Azure Rights Management](../Topic/Decommissioning_and_Deactivating_Azure_Rights_Management.md).

Jednak przed zlikwidować wdrożenia usług Azure RMS, chcielibyśmy usłyszeć i zrozumieć, dlaczego wprowadzone tej decyzji. Jeśli usług Azure RMS nie spełnia wymagań biznesowych, skonsultuj się z nami w przypadku, gdy zaplanowano nowe funkcje w przyszłości, lub jeśli występują alternatywy. Wyślij wiadomość e-mail do [AskIPTeam@Microsoft.com](mailto:askipteam@microsoft.com?subject=Planning%20to%20decommission%20Azure%20RMS) i będziemy chętnie omówiono wymagania techniczne i biznesowe.

## Można kontrolować z użytkowników do ochrony zawartości można używać usług Azure RMS?
Tak, usług Azure RMS zawiera formanty dołączania użytkownika, w tym scenariuszu. Aby uzyskać więcej informacji, zobacz [Konfigurowanie dołączania kontrolek etapowe wdrożenia](../Topic/Activating_Azure_Rights_Management.md#BKMK_OnboardingControls) w sekcji [Aktywowanie Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md) tematu.

## Można uniemożliwić użytkownikom udostępnianie chronione dokumenty z określonych organizacji?
Jedną z największych korzyści wynikające z usług Azure RMS jest obsługuje firma firma współpracy, bez konieczności konfigurowania jawne zaufania dla każdej organizacji partnera, ponieważ Azure AD zajmie się kompilowaniem uwierzytelniania dla Ciebie.

Nie ma żadnej opcji Administracja uniemożliwi użytkownikom bezpieczne udostępnianie dokumentów z określonej organizacji. Na przykład chcesz zablokować organizacja, która nie ufasz lub zawiera konkurencyjnych biznesowych. Uniemożliwia wysyłanie chronione dokumenty do użytkowników w tych usług Azure RMS organizacji nie ma sensu, ponieważ użytkownicy będą następnie udostępnić swoje dokumenty bez ochrony, który prawdopodobnie jest ostatnim operacją, której ma się stać w tym scenariuszu! Na przykład nie można zidentyfikować, który jest udostępnianie dokumentów poufnych danych firmy za pomocą których użytkownicy w tych organizacji, które można zrobić w przypadku dokumentu (lub adres e-mail) jest chroniony przez usług Azure RMS.

## Gdy chroniony dokument I udostępnić komuś spoza firmy, jak ten użytkownik uwierzytelniane?
Azure RMS zawsze używa konta usługi Azure Active Directory i adres e-mail skojarzony do uwierzytelniania użytkownika, dzięki czemu firma firma współpracy bezproblemowe dla administratorów. Jeśli inna organizacja używa usług Azure, użytkownicy już mają konta w usłudze Azure Active Directory, nawet jeśli te konta są tworzone i zarządzana lokalnie, a następnie synchronizowane Azure.  Jeśli organizacja ma Office 365, pod maską, ta usługa używa również Azure Active Directory dla kont użytkowników.  Jeśli organizacja użytkownika nie ma konta zarządzane w systemie Azure, użytkownicy mogą się logować się w celu [usług RMS dla osób](https://technet.microsoft.com/library/dn592127.aspx), które tworzą niezarządzane dzierżawą platformy Azure i katalog dla organizacji przy użyciu konta użytkownika, tak, aby ten użytkownik może zostać uwierzytelniony następnie usług Azure RMS.

Metodę uwierzytelniania dla tych kont może się różnić w zależności od tego, jak administrator w innej organizacji skonfigurował kont usługi Azure Active Directory. Na przykład można używać hasła, które zostały utworzone dla tych kont, uwierzytelnianie wieloskładnikowe (MFA), Federacji lub hasła, które zostały utworzone w usługach domenowych w usłudze Active Directory i następnie synchronizowane z usługi Azure Active Directory.

## Czy mogę dodać użytkowników z spoza firmy do szablonów niestandardowych
Tak.  Tworzenie szablonów niestandardowych, które użytkownicy końcowi (i Administratorzy) można wybrać z aplikacji ułatwia szybkie i łatwe stosowane ochrony informacji za pomocą wstępnie zdefiniowane zasady, które określisz. Jest jedno z ustawień w szablonie, który jest w stanie uzyskać dostęp do zawartości i można określić użytkowników i grupy z w ramach organizacji, a użytkownicy z spoza organizacji.

Aby określić użytkowników z spoza organizacji, użyj [Moduł Windows PowerShell dla Azure Rights Management](https://technet.microsoft.com/library/jj585012.aspx). Można użyć jednej z następujących opcji:

-   **Eksportu, edycji i importowanie zaktualizowany szablon**:  Jeśli chcesz dodać do istniejącego szablonu, który zawiera inne grupy tych użytkowników zewnętrznych jest najłatwiejsza metoda. Użyj [AadrmTemplate eksportu](https://msdn.microsoft.com/library/azure/dn727078.aspx) Eksportuj szablon do przy użyciu polecenia cmdlet. Plik CSV, który można edytować, aby dodać adresy e-mail zewnętrznych tych użytkowników i ich praw do istniejących grup i uprawnień. Następnie użyj [AadrmTemplate importowania](https://msdn.microsoft.com/library/azure/dn727077.aspx) polecenia cmdlet do importowania tej zmiany z powrotem do usług Azure RMS.

-   **Używać obiektu definicji prawa do utworzenia lub zaktualizowania szablonu**:    Określ adresy e-mail zewnętrznych i ich praw w obiekcie definicji prawa, który następnie umożliwia tworzenie lub aktualizowanie szablonu. Określ prawa definicji obiektu za pomocą [AadrmRightsDefinition nowy](https://msdn.microsoft.com/library/azure/dn727080.aspx) polecenia cmdlet, aby utworzyć zmienną, a następnie podaj tę zmienną z parametrem - RightsDefinition z [AadrmTemplate Dodaj](https://msdn.microsoft.com/library/azure/dn727075.aspx) polecenia cmdlet (dla nowego szablonu) lub [Set AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx) polecenia cmdlet (Jeśli w przypadku modyfikowania istniejącego szablonu). Jednak w przypadku dodawania tych użytkowników do istniejącego szablonu, należy zdefiniować obiekty definicji prawa do istniejących grup w szablonach i nie tylko użytkowników zewnętrznych.

Aby uzyskać więcej informacji o niestandardowych szablonów, zobacz [Konfigurowanie niestandardowych szablonów Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

## Jakich urządzeń i typy plików obsługiwanych przez usług Azure RMS?
Aby uzyskać listę obsługiwanych urządzeń, zobacz [Urządzenia klientów, które obsługują Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedDevices) w sekcji [Wymagania dotyczące systemu Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tematu. Ponieważ nie wszystkie obsługiwane urządzenia obecnie obsługuje wszystkie funkcje usług RMS, należy również sprawdzić, czy [Możliwości urządzenia klienta](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_ClientCapabilities) tabeli w tym samym tematem.

Azure RMS może obsługiwać wszystkie typy plików. Tekst, obraz, Microsoft Office (Word, Excel, PowerPoint) plików, plików PDF i niektórych innych typów plików aplikacji usług Azure RMS zapewnia natywnego ochrony, obejmujący szyfrowanie i wymuszanie praw (uprawnień). Dla wszystkich innych aplikacji i typów plików ochrona ogólna zapewnia hermetyzację plików i uwierzytelniania, aby sprawdzić, czy użytkownik jest autoryzowany do otwierania tego pliku.

Aby uzyskać listę rozszerzeń nazw plików, które są obsługiwane przez usługi Azure RMS, zobacz [obsługiwane typy plików i rozszerzenia nazw plików](http://technet.microsoft.com/library/dn339003.aspx) części [Rights Management sharing Przewodnik administratora aplikacji](http://technet.microsoft.com/library/dn339003.aspx). Nie na liście rozszerzeń nazw plików są obsługiwane za pomocą usług RMS, udostępnianie aplikacji, która automatycznie stosuje ochronę ogólną do tych plików.

## Podczas migracji z usług AD RMS będzie obsługiwać?
Początkowo usług Azure RMS nie obsługuje migracji z systemów lokalnych Rights Management, takich jak usługi AD RMS. Jednak jest obecnie obsługiwane.

Aby uzyskać więcej informacji, zobacz [Migrowanie z usług AD RMS do usługi Azure Rights Management](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md).

## Firma Microsoft naprawdę chcesz BYOK za pomocą usług Azure RMS, ale pokazaliśmy, że nie jest zgodny z usługą Exchange Online — co firma?
Nie przegap tego ograniczenia bieżącego opóźnienia wdrożenia usług Azure RMS. Jeśli masz program Exchange Online i chcesz Użyj przełączyć własny klucz (BYOK), zaleca się wdrożenie usług Azure RMS w domyślnym trybie zarządzania kluczami, gdzie Microsoft generuje i zarządza klucz. W ten sposób możesz korzystać ze wszystkich zalet ochrony ważnych plików i wiadomości e-mail, z opcją przenieść BYOK później (na przykład, gdy usługi Exchange Online obsługuje BYOK).

Jednak jeśli zasadami obowiązującymi w organizacji wymagają użycia sprzętu zabezpieczeń moduły, w przeciwnym razie będzie to blokowanie wdrożenia usług Azure RMS innej opcji jest teraz wdrożenie usług Azure RMS za pomocą BYOK z ograniczoną funkcjonalnością usług RMS dla programu Exchange. Aby uzyskać więcej informacji, zobacz [BYOK pricing and restrictions](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing) w sekcji [Planowanie i wdrażanie swoim kluczem dzierżawcy zarządzania prawami Azure](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) tematu.

## Funkcja szukam prawdopodobnie nie do pracy z programem SharePoint chronione bibliotek — Obsługa Moje funkcji planowane jest?
Obecnie programu SharePoint obsługuje RMS chronione dokumenty przy użyciu usługi IRM chronione bibliotek, które nie obsługują niestandardowe szablony i niektóre inne możliwości śledzenia dokumentów.  Aby uzyskać więcej informacji, należy rozwinąć   [SharePoint Online i usługi OneDrive dla firm: Konfiguracja usługi IRM](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharePointOnline) w sekcji [Jak aplikacje obsługują Azure Rights Management](../Topic/How_Applications_Support_Azure_Rights_Management.md) tematu.

Jeśli jesteś zainteresowany określonych możliwości, który nie jest jeszcze obsługiwany, pamiętaj śledzą na anonsów [blog zespołu RMS](http://blogs.technet.com/b/rms/).

## Jak skonfigurować jeden dysk w przedsiębiorstwie w usłudze SharePoint Online, dzięki czemu użytkownicy mogą bezpiecznie udostępniać swoje pliki osobom i spoza firmy?
Domyślnie jako administrator usługi Office 365, nie zostanie skonfigurowany. czy użytkownicy.

Tak samo, jak administrator witryny SharePoint włącza i konfiguruje prawami do biblioteki programu SharePoint, który jest właścicielem, OneDrive dla firm jest przeznaczony dla użytkowników włączyć i skonfigurować IRM dla własnych OneDrive biblioteki biznesowych.  Jednak przy użyciu programu PowerShell, można to zrobić dla nich. Aby uzyskać instrukcje, rozwiń [SharePoint Online i usługi OneDrive dla firm: Konfiguracja usługi IRM](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharePointOnline)  w sekcji [Konfigurowanie aplikacji Azure Rights Management](../Topic/Configuring_Applications_for_Azure_Rights_Management.md) artykułu.

## Czy masz wskazówki ani wskazówki pomyślne wdrożenie usług RMS?
Po nadzorowanie wielu wdrożeń i słuchanie naszych klientów, partnerzy, wystąpić doradcy i pracowników działu pomocy technicznej — jedną z największych porady, które firma Microsoft może przekazać między: **Projektowania i wdrażania zasad prawa proste**.

Ponieważ usług Azure RMS obsługuje bezpieczne udostępnianie osobom, można przyznać można ambitny z zasięg ochrony informacji. Ale konserwatywnego z zasadami dotyczącymi praw. Wiele organizacji, aby uzyskać największy wpływ na prowadzoną działalność pochodzi z uniemożliwia wycieku danych przez zastosowanie szablonu zasad praw domyślnej, która ogranicza dostęp do osób w Twojej organizacji. Oczywiście, można uzyskać bardziej szczegółowe niż która w razie potrzeby — zapobieżenie drukowania, edycji itp. Ale zachować bardziej szczegółowym ograniczenia jako wyjątek dla dokumentów, które wymagają wysokiego poziomu zabezpieczeń i nie implementują te zasady bardziej restrykcyjne na jeden dzień, ale plan bardziej etapowe.

## Jakie funkcje może lub nie można używać z innej subskrypcji dla usług Azure RMS?
W przypadku płatnej subskrypcji, obsługujące usług Azure RMS (Office 365, Azure RMS Premium i Enterprise Mobility Suite) istnieją pewne różnice w funkcjach RMS, które są obsługiwane. Lista tych, zobacz [ofert porównania z usług zarządzania prawami (RMS)](http://technet.microsoft.com/dn858608).

Bezpłatna subskrypcja, obsługujący usług Azure RMS (RMS dla użytkowników indywidualnych) obsługuje wykorzystujących zawartości chronionej przez usług Azure RMS. Aby uzyskać więcej informacji, zobacz [RMS dla osób i Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md).

## Gdzie można uzyskać informacje techniczne na temat bezpłatnej subskrypcji usług Azure RMS (RMS dla użytkowników indywidualnych) — na przykład, jak naprawdę działa jak kontrolować kont i nie można używać domen?
Znajdziesz odpowiedzi na te pytania w [RMS dla osób i Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md) tematu.

## Jak odzyskać dostęp do plików, które były chronione przez pracownika, który teraz opuszczenie organizacji?
Funkcja administratorów usług Azure RMS, która pozwala autoryzowani użytkownicy mają pełne prawa właściciela dla wszystkich licencji użytkowania, które zostały przyznane przez dzierżawcę RMS w organizacji. Tej samej funkcji pozwala indeksu autoryzowanych usług i przeglądanie plików, w razie potrzeby.

Aby uzyskać więcej informacji, zobacz [Konfigurowanie administratorów systemu Azure Rights Management i odnajdywania usług lub odzyskiwania danych](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md).

## Rights Management może uniemożliwić przechwytywania ekranu?
Zarządzanie prawami Zablokuj Przechwytywanie ekranu od większości narzędzi przechwytywania ekranu często używane, co pomaga uniknąć zaniedbania lub przypadkowego ujawnienia informacji poufnych lub wrażliwych. Istnieje jednak wiele sposobów, że użytkownik może udostępnić dane wyświetlane na ekranie i biorąc zrzut ekranu jest tylko jedna metoda. Na przykład konwersji na udostępnianie informacji wyświetlanych użytkownikowi może obrazu przy użyciu telefonu z aparatem, wpisywania danych lub po prostu ustnie przekazywania chroniony.

Jak pokazują powyższe przykłady, technologii samodzielnie nie zawsze uniemożliwić użytkownikom udostępnianie danych, które nie powinny. Gdy Rights Management może pomóc w ochronie ważnych danych za pomocą zasad użytkowania i autoryzacji, to rozwiązanie do zarządzania przedsiębiorstwem prawa powinien być używany z innymi formantami. Na przykład implementować zabezpieczenia fizyczne, dokładnie ekranu i monitorowanie osób, które mają autoryzację dostępu do danych w organizacji i inwestycji w Edukacja użytkowników, więc użytkownicy rozumieją, jakie dane nie powinien być współużytkowany.

## Gdzie można znaleźć informacji dodatkowych usług Azure RMS — takie jak prawne, zgodności i umowy SLA?
Również zależy od innych usług Azure RMS i obsługuje innych usług. Jeśli szukasz informacji związanych z usług Azure RMS, ale nie na temat sposobu korzystania z usług Azure RMS, sprawdź następujące zasoby:

**Prawne i ochrona prywatności:**

-   Dla informacji o umowach Microsoft Azure: [Umowy Microsoft Azure](http://azure.microsoft.com/support/legal/subscription-agreement/)

-   Informacje o ochronie prywatności Microsoft Azure: [Zasady zachowania poufności informacji w systemie Microsoft Azure](http://azure.microsoft.com/support/legal/privacy-statement/)

**Zabezpieczenia, zgodności i inspekcji:**

Zobacz [Wymagania dotyczące przepisami, zgodności i zabezpieczeń](../Topic/What_is_Azure_Rights_Management_.md#BKMK_RMScompliance) w sekcji [Co to jest Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md) tematu. Ponadto:

-   Dla zewnętrznych certyfikaty dla usług Azure RMS: [Centrum zaufania usługi Microsoft Azure](http://azure.microsoft.com/support/trust-center/)

-   FIPS 140 informacji: [FIPS 140 sprawdzania poprawności](https://technet.microsoft.com/library/security/cc750357.aspx)

**Umowy dotyczące poziomu usług:**

-   Umowy dotyczącej poziomu usług Azure RMS przez wybranego kraju: [Umowa dotycząca poziomu usług](http://microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&amp;DocumentTypeId=37)

-   Umowy dotyczącej poziomu usług Azure Active Directory: [Umowy dotyczące poziomu usług](http://azure.microsoft.com/support/legal/sla/)

**Dokumentacja:**

-   Witryna dokumentacji usługi Active Directory systemu Azure: [Azure Active Directory](http://azure.microsoft.com/documentation/services/active-directory/)

-   Biblioteka usługi Azure Active Directory: [Azure Active Directory](http://msdn.microsoft.com/library/azure/jj673460.aspx)

-   Biblioteka usługi Office 365: [Usługi Office 365](http://technet.microsoft.com/library/dn127064%28v=office.14%29.aspx)

## Co należy zrobić, jeśli w tym miejscu nie jest moje pytanie?
Użyj łączy i zasobów wymienionych w [Informacje i pomoc techniczna dla usługi Azure Rights Management](../Topic/Information_and_Support_for_Azure_Rights_Management.md).

Ponadto są przeznaczone dla użytkowników końcowych — często zadawane pytania:

-   [Często zadawane pytania dotyczące tworzenia aplikacji dla systemu Windows Rights Management](https://technet.microsoft.com/dn467883)

-   [Często zadawane pytania dotyczące tworzenia aplikacji dla platform mobilnych i Mac Rights Management](https://technet.microsoft.com/dn451248)

-   [Często zadawane pytania dotyczące śledzenia dokumentu](http://go.microsoft.com/fwlink/?LinkId=523977)

Ta strona często zadawane pytania jest aktualizowany regularnie, o nowych dodatków wymienionych w miesięcznych aktualizacjach dokumentacji na [zespołu Microsoft Rights Management (RMS)](http://blogs.technet.com/b/rms/) blogu.

> [!TIP]
> Można użyć [tag dokumenty](http://blogs.technet.com/b/rms/archive/tags/docs/) w blogu, bardziej łatwo znaleźć anonse te dokumentacji.

## Zobacz też
[Wprowadzenie do korzystania z systemu Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

