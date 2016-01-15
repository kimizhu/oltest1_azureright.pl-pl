---
description: na
keywords: na
title: Configuring Custom Templates for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1775d8d0-9a59-42c8-914f-ce285b71ac1c
---
# Konfigurowanie niestandardowych szablon&#243;w Azure Rights Management
Po uaktywnieniu Azure Rights Management (usług Azure RMS), użytkownicy mogą automatycznie użyć dwóch szablonów domyślnych, które ułatwiają je, aby zastosować zasady do poufnych plików, które ograniczają dostęp do autoryzowanych użytkowników w organizacji. Te dwa szablony ma następujące ograniczenia zasad prawa:

-   Wyświetlanie tylko do odczytu do chronionej zawartości

    -   Nazwa wyświetlana: **&lt; nazwa organizacji &gt; - tylko poufne widok**

    -   Określone uprawnienia: Wyświetlanie zawartości

-   Odczytywać lub modyfikować uprawnienia do chronionej zawartości

    -   Nazwa wyświetlana: **&lt; nazwa organizacji &gt; - poufne**

    -   Określone uprawnienia: Wyświetlanie zawartości, Zapisz plik, edytować zawartość, wyświetlić przypisane prawa, Zezwalaj na makra, do przodu, odpowiedź, Odpowiedz wszystkim

Ponadto [aplikacji RMS sharing](http://technet.microsoft.com/library/dn339006.aspx) pozwala użytkownikom na definiowanie własnych zestaw uprawnień. I dla klienta programu Outlook i Outlook Web Access, użytkownicy mogą wybrać **nie przekazuj** opcja dla wiadomości e-mail.

W wielu organizacjach domyślne szablony mogą być wystarczające. Ale jeśli chcesz utworzyć własne niestandardowe uprawnienia szablonów zasad, możesz to zrobić. Poniżej przedstawiono przyczyny tworzenia niestandardowego szablonu:

-   Chcesz szablonu przyznać prawa do podzbioru użytkowników w organizacji, a nie wszystkich użytkowników.

-   Mają tylko podzbiór użytkowników, aby można było wyświetlić i wybrać szablon (działów szablonu) z aplikacji, a nie dla wszystkich użytkowników w organizacji można znaleźć i wybrać szablon.

-   Chcesz zdefiniować niestandardowy prawa do szablonu, takich jak wyświetlanie i edytowanie, ale nie kopiowanie i drukowanie.

-   Użytkownik chce skonfigurować dodatkowe opcje w szablonie zawierają datę wygaśnięcia i tego, czy zawartość jest możliwy bez połączenia z Internetem.

Dla użytkowników można było wybrać niestandardowy szablon, który zawiera ustawienia, takie jak te należy najpierw utworzyć niestandardowy szablon, jest skonfigurowana i następnie opublikuj go.

Użyj poniższych sekcjach ułatwiają konfigurowanie i używanie szablonów niestandardowych:

-   [Sposób tworzenia, konfigurowania i publikowanie szablonu niestandardowego](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToConfigureCustomTemplates)

-   [Jak skopiować szablonu](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToCopyTemplates)

-   [Jak usunąć szablony (archiwum)](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToArchiveTemplates)

-   [Odświeżanie szablonów dla użytkowników](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_RefreshingTemplates)

-   [Odwołanie do środowiska Windows PowerShell](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_PowerShellTemplates)

## <a name="BKMK_HowToConfigureCustomTemplates"></a>Sposób tworzenia, konfigurowania i publikowanie szablonu niestandardowego
Można tworzyć i zarządzać szablonami niestandardowe w portalu zarządzania Azure. Można to zrobić bezpośrednio w portalu zarządzania Azure, lub zaloguj się w Centrum administracyjnym usługi Office 365 i wybierz polecenie **Zaawansowane funkcje** Rights Management, który następnie przekieruje użytkownika do portalu zarządzania Azure.

Poniższe procedury umożliwiają tworzenie, konfigurowanie i publikowanie szablonów niestandardowych Rights Management.

#### Aby utworzyć niestandardowy szablon

1.  W zależności od tego, czy logujesz się do Centrum administracyjnego usługi Office 365 lub portalu Azure wykonaj jedną z następujących czynności:

    -   Z [Centrum administracyjnym usługi Office 365](https://portal.office.com/):

        1.  W okienku po lewej stronie kliknij **Ustawienia usługi**.

        2.  Z **Ustawienia usługi** kliknij **zarządzania prawami dostępu**.

        3.  W **ochronie informacji użytkownika** kliknij przycisk **Zarządzaj**.

        4.  W **zarządzania prawami dostępu** kliknij przycisk **Zaawansowane funkcje**.

            > [!NOTE]
            > Jeśli Rights Management nie został jeszcze aktywowany, najpierw kliknij **aktywować** i potwierdzenie tej operacji. Aby uzyskać więcej informacji, zobacz [Aktywowanie Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md).
            > 
            > Jeśli jeszcze nie zostało kliknięte **Zaawansowane funkcje** przed, po uaktywnieniu Rights Management, postępuj zgodnie z wyświetlanymi instrukcje w celu uzyskania bezpłatnej subskrypcji Azure, który ma uzyskać dostęp do portalu Azure.

            Kliknięcie **Zaawansowane funkcje** ładuje portalu Azure, w którym można zarządzać **RIGHTS MANAGEMENT** dla organizacji w usłudze Azure Active Directory.

    -   Z [portalu Azure](http://go.microsoft.com/fwlink/p/?LinkID=275081):

        1.  W okienku po lewej stronie kliknij **usługi ACTIVE DIRECTORY**.

        2.  Z **usługi active directory** kliknij **RIGHTS MANAGEMENT**.

        3.  Wybierz katalog, w celu zarządzania Rights Management.

        4.  Jeśli Rights Management nie został jeszcze aktywowany, kliknij przycisk **UAKTYWNIENIA** i potwierdzenie tej operacji.

            > [!NOTE]
            > Aby uzyskać więcej informacji, zobacz [Aktywowanie Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md).

2.  Tworzenie nowego szablonu:

    -   W portalu Azure z **wprowadzenie Rights Management** szybki start strony, kliknij przycisk **Tworzenie nowego szablonu zasad praw**.

        Ta strona nie jest od razu ma po wykonaniu instrukcji dla Office 365, użyj instrukcji nawigacji powyżej, dla portalu Azure.

3.  Na **dodać nowego szablonu zasad praw** wybierz język, w którym będzie wpisz nazwę i opis szablonu, który użytkownicy będą widzieć (można dodać więcej języków później). Następnie wpisz unikatową nazwę i opis i kliknij przycisk ukończone.

Z **wprowadzenie Rights Management** szybki start strony, kliknij przycisk **zarządzania szablonami zasad praw**. Wyświetlony zostanie dodany do listy szablonów ze stanem nowo utworzony szablon **archiwizacji**. Na tym etapie, szablon zostanie utworzony, ale nie jest skonfigurowane i nie jest widoczny dla użytkowników.

#### Aby skonfigurować i publikowanie szablonu niestandardowego

1.  Wybierz nowo utworzony szablon z **Szablony** strony w portalu zarządzania Azure.

2.  Z **został dodany do szablonu** szybki start strony, kliknij przycisk **rozpocząć** w kroku 1, **konfigurowania uprawnień dla użytkowników i grup,** przycisk **Zacznij już teraz** lub **dodać**, a następnie wybierz użytkowników i grupy, którzy będą mieć praw do korzystania z zawartości chronionej przez nowy szablon.

    > [!NOTE]
    > Użytkownicy lub grupy, które można wybrać musi mieć adres e-mail. W środowisku produkcyjnym prawie zawsze będzie wielkość liter, ale w środowisku testowym proste, należy dodać adresy e-mail do kont użytkowników lub grup.

    Najlepszym rozwiązaniem przy użyciu grup zamiast użytkowników, co ułatwia zarządzanie szablonów. Jeśli masz lokalnej usługi Active Directory i synchronizacji do usługi Azure AD, można użyć grup obsługą wiadomości, które są grupy dystrybucji lub grupy zabezpieczeń. Jednak jeśli chcesz przyznać prawa do wszystkich użytkowników w organizacji będzie bardziej efektywne skopiować jednego z szablonów domyślnych, a nie określić wiele grup. Aby uzyskać więcej informacji, zobacz [Jak skopiować szablonu](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToCopyTemplates) w tym temacie.

    > [!TIP]
    > Można później dodać użytkowników z spoza organizacji do szablonu, za pomocą [Moduł Windows PowerShell dla Azure Rights Management](https://technet.microsoft.com/library/jj585012.aspx) i przy użyciu jednej z następujących metod:
    > 
    > -   **Eksportu, edycji i importowanie zaktualizowany szablon**:  To jest najłatwiejsza metoda dodawania użytkowników zewnętrznych do istniejącego szablonu, który zawiera inne grupy. Użyj [AadrmTemplate eksportu](https://msdn.microsoft.com/library/azure/dn727078.aspx) Eksportuj szablon do przy użyciu polecenia cmdlet. Plik CSV, który można edytować, aby dodać adresy e-mail zewnętrznych tych użytkowników i ich praw do istniejących grup i uprawnień. Następnie użyj [AadrmTemplate importowania](https://msdn.microsoft.com/library/azure/dn727077.aspx) polecenia cmdlet do importowania tej zmiany z powrotem do usług Azure RMS.
    > -   **Używać obiektu definicji praw, aby zaktualizować szablon**:    Określ adresy e-mail zewnętrznych i ich praw w obiekcie definicji prawa, który następnie służy do aktualizowania szablonu. Określ prawa definicji obiektu za pomocą [AadrmRightsDefinition nowy](https://msdn.microsoft.com/library/azure/dn727080.aspx) polecenia cmdlet, aby utworzyć zmienną, a następnie podaj tę zmienną z parametrem - RightsDefinition z [Set AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx) polecenia cmdlet, aby zmodyfikować istniejący szablon. Jednak w przypadku dodawania tych użytkowników do istniejącego szablonu, również należy do definiowania obiektów definicji prawa do istniejących grup w szablonach i nie tylko zewnętrznego, nowych użytkowników.

3.  Kliknij przycisk Dalej, a następnie przypisać jeden z wymienionych prawa do wybranych użytkowników i grup.

    Więcej informacji na temat każdego prawa (i niestandardowe uprawnienia), należy skorzystać z opisu wyświetlanych. Bardziej szczegółowe informacje są także dostępne w [Konfigurowanie praw użytkowania Azure Rights Management](../Topic/Configuring_Usage_Rights_for_Azure_Rights_Management.md). Jednak aplikacje obsługujące RMS może się różnić w sposób wykonania tych praw. Zobacz ich dokumentację i własne testowanie z aplikacji, które użytkownicy używają sprawdzać zachowanie przed wdrożeniem szablonu dla użytkowników. Aby wyświetlić ten szablon tylko Administratorzy dla tego badania, należy ten szablon działów szablonu (krok 6).

4.  W przypadku wybrania **niestandardowy**, kliknij przycisk Dalej, a następnie wybierz prawa niestandardowe.

    Mimo że można użyć dowolnej kombinacji indywidualnych uprawnień dostępne w niektórych aplikacjach, niektóre prawa może być zależny od inne prawa poszczególnych. W przypadku prawa zależne zostaną zaznaczone automatycznie za Ciebie.

    > [!TIP]
    > Należy rozważyć dodanie **kopiowania i Wyodrębnij zawartość** prawym przyciskiem myszy, a następnie przydzielić to do wybranych administratorów lub pracowników w innych ról, które się do odzyskiwania informacji. Udzielanie prawo to umożliwi Usuń ochronę w razie potrzeby z plików i wiadomości e-mail, które będą chronione za pomocą tego szablonu. Ta możliwość usunięcia ochrony na poziomie szablonu zawiera większa kontrola niż przy użyciu funkcji użytkownika nadrzędnego.

5.  Kliknij przycisk ukończone.

6.  Jeśli szablon ma być widoczne tylko podzbiór użytkowników, gdy zostaje wyświetlona lista szablonów w aplikacjach: Kliknij przycisk **zakres** do skonfigurowania tego jako szablon działów, a następnie kliknij przycisk **Zacznij już teraz**. W przeciwnym razie przejdź do kroku 9.

    Więcej informacji o szablonach działów: Domyślnie wszyscy użytkownicy w katalogu Azure Zobacz wszystkie szablony opublikowane i mogą następnie wybrać je z aplikacji podczas ochrony zawartości. Chcąc określonych użytkowników tylko do niektórych opublikowanych szablonów, użytkownik musi określić zakres szablony dla tych użytkowników. Następnie tylko ci użytkownicy będą mogli wybrać te szablony. Innych użytkowników, którzy nie określisz nie zobaczą szablony i dlatego nie można ich wybrać. Ta technika wykonywać, wybór prawidłowy szablon łatwiejsze dla użytkowników, zwłaszcza gdy tworzyć szablony, które są przeznaczone do określonych grup lub działów. Następnie użytkownicy widzą tylko szablonów, które są przeznaczone do nich.

    Na przykład utworzono szablon dla działu zasobów ludzkich, które dotyczą elementów członkowskich w dziale finansowym uprawnienia tylko do odczytu. Tak, aby tylko członkowie działu kadr można zastosować ten szablon, używając Rights Management sharing application, zakres szablon do grupy komputerów z obsługą wiadomości e-mail o nazwie kadry. Następnie należy tylko członkowie tej grupy Zobacz i będzie można zastosować ten szablon.

7.  Na **widoczność szablonu** Wybierz użytkowników i grupy, którzy będą mogli wyświetlić, a następnie wybierz szablon z obsługą usług RMS aplikacji. Jak wcześniej, najlepszym rozwiązaniem użycia grupy zamiast użytkowników i grup lub użytkowników musi mieć adres e-mail.

8.  Kliknij przycisk Dalej i zdecyduj, czy należy skonfigurować zgodności aplikacji działów szablonu. Jeśli klikniesz **zgodności aplikacji**, zaznacz pole wyboru i kliknij przycisk **zakończone**.

    Dlaczego może być konieczne skonfigurowanie zgodności aplikacji? Nie wszystkie aplikacje mogą obsługiwać działów szablonów. Aby to zrobić, aplikacja najpierw musi uwierzytelniać za pomocą usługi RMS przed pobraniem szablonów. Jeśli proces uwierzytelniania nie występuje, domyślnie żadna z działów szablony zostaną pobrane. Zachowanie to można zastąpić, określając, że wszystkie szablony działów należy pobrać, konfigurowanie zgodności aplikacji i wybierając **Pokaż ten szablon do wszystkich użytkowników, gdy aplikacje nie obsługują tożsamość użytkownika** pole wyboru.

    Na przykład jeśli zgodność aplikacji dla działów szablonu w naszym przykładzie zasobów ludzkich nie zostanie skonfigurowane, tylko użytkownicy w dziale zasobów ludzkich Zobacz działów szablonu korzystają z aplikacji RMS sharing, kiedy żaden użytkownik nie można znaleźć w temacie działów szablonu przy korzystaniu z programu Outlook Web Access (OWA) z programu Exchange Server 2013 ponieważ OWA programu Exchange i programu Exchange ActiveSync aktualnie nie obsługują działów szablony. Jeśli to domyślne zachowanie można zastąpić przez skonfigurowanie zgodności aplikacji, tylko użytkownicy w dziale zasobów ludzkich Zobacz działów szablonu korzystają z aplikacji RMS sharing, ale wszyscy użytkownicy widzą działów szablonu, jeśli korzystają z programu Outlook Web Access (OWA). Jeśli użytkowników za pomocą programu OWA lub protokołu Exchange ActiveSync z usługi Exchange Online, wszyscy użytkownicy widzą szablony działów lub użytkownicy nie zobaczą szablony działu, na podstawie stanu szablonu (archiwizacji lub opublikowanych) w usłudze Exchange Online.

    > [!NOTE]
    > Jeśli masz aplikacje, które jeszcze nie obsługują działów szablonów, można użyć [niestandardowego skryptu pobierania szablonu RMS](http://go.microsoft.com/fwlink/?LinkId=524506) lub innych narzędzi, aby wdrożyć te szablony do folderu lokalnego klienta usług RMS. Następnie te aplikacje poprawnie wyświetli działów szablonów dla użytkowników i grup, które wybrano w zakresie szablonu:
    > 
    > -   Dla pakietu Office 2010, folder klienta jest **%localappdata%\Microsoft\DRM\Templates**.
    > -   Z komputera klienckiego pobranie wszystkich szablonów można skopiować, a następnie wklej pliki szablonów do innych komputerów.
    > 
    > Office 2016 natywnie obsługuje działów szablony, a co powoduje pakietu Office 2013 przy użyciu najnowszych aktualizacji pakietu Office ([KB 3054853](https://support.microsoft.com/kb/3054853)).

9. Kliknij przycisk **Konfiguruj** i dodawanie dodatkowych języków używanych przez użytkowników, oraz nazwę i opis tego szablonu w tym języku. Gdy użytkownicy wiele języków, jest ważne, aby dodać każdego z języków mogą korzystać, a następnie podaj nazwę i opis, w tym języku. Użytkownicy widzą nazwę i opis szablonu w tym samym języku co ich system operacyjny klienta, który gwarantuje, że rozumieją zasady stosowane do wiadomości e-mail lub dokumentu. Jeśli nie zostanie odnaleziony odpowiednik z ich kliencki system operacyjny, nazwa i opis, które będą widoczne powraca do języka i opis zdefiniowany przez użytkownika podczas tworzenia szablonu.

    Następnie sprawdź, czy chcesz wprowadzić zmiany w następujących ustawień:

    |Ustawienie|Więcej informacji|
    |--------------|---------------------|
    |**wygaśnięcia zawartości**|Należy zdefiniować datę lub liczbę dni, dla tego szablonu, kiedy nie należy otwierać pliki chronione za pomocą szablonu. Można określić datę lub określ liczbę dni, rozpoczynając od godziny ochrony stosowany do pliku.<br /><br />Po określeniu daty jest efektywne północy w bieżącej strefy czasowej.|
    |**dostęp w trybie offline**|To ustawienie umożliwia zrównoważenia wszelkie wymagania dotyczące zabezpieczeń, czy wprowadzona przed wymaganie, że użytkownicy muszą być w stanie otworzyć ochrona plików podczas ich nie masz połączenia internetowego.<br /><br />Jeśli określisz, że zawartość nie jest dostępna bez połączenia z Internetem lub zawartość jest dostępna tylko dla określonej liczby dni, po osiągnięciu tego progu, użytkownicy muszą być ponownie uwierzytelniony, a ich dostęp jest zalogowany. Kiedy tak się stanie, jeśli nie są buforowane swoje poświadczenia, użytkownicy są monitowani do logowania się przed otwarciem pliku.<br /><br />Oprócz ponowne uwierzytelnianie jest ponownie oceniane zasady i członkostwo w grupie użytkowników. Oznacza to, czy użytkownicy mogą wystąpić dostęp różne wyniki dla tego samego pliku wprowadzeniu zmian w członkostwie grupy lub zasad z podczas ich ostatniego dostępu do pliku.|

10. Po upewnieniu się, że szablon jest odpowiednio skonfigurowane dla użytkowników, kliknij przycisk **publikowania** widoczności szablonu dla użytkowników, a następnie kliknij przycisk **ZAPISAĆ**.

11. Kliknij przycisk Wstecz, aby powrócić do portalu zarządzania **Szablony** strony, gdzie szablon ma teraz zaktualizowany stan **opublikowaną**.

Aby wprowadzić zmiany w szablonie, zaznacz go i ponownie użyć kroki szybki start. Lub wybierz jedną z następujących opcji:

-   Dodanie większej liczby użytkowników i grup i zdefiniować uprawnienia dla tych użytkowników i grup: Kliknij przycisk **prawa**, następnie kliknij przycisk **dodać**.

-   Aby usunąć użytkowników lub grupy, które wcześniej wybrano: Kliknij przycisk **prawa**, wybierz użytkownika lub grupę z listy, a następnie kliknij przycisk **usunąć**.

-   Aby zmienić, które użytkownicy mogą zobaczyć szablonów, aby wybrać je z aplikacji: Kliknij przycisk **zakres**, następnie kliknij przycisk **dodać** lub **usunąć**, lub **zgodności aplikacji**.

-   Aby szablon był już widoczne dla wszystkich użytkowników: Kliknij przycisk **Konfiguruj**, kliknij przycisk **ARCHIWUM**, a następnie kliknij przycisk **ZAPISAĆ**.

-   Do wprowadzania zmian konfiguracji: Kliknij przycisk **Konfiguruj**, wprowadzić zmiany, a następnie kliknij przycisk **ZAPISAĆ**.

> [!WARNING]
> Po wprowadzeniu zmian do szablonu, który został wcześniej zapisany, klienci nie będą widzieć te zmiany w szablonie do momentu szablony są odświeżane na swoich komputerach. Aby uzyskać więcej informacji, zobacz [Odświeżanie szablonów dla użytkowników](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_RefreshingTemplates) w tym temacie.

## <a name="BKMK_HowToCopyTemplates"></a>Jak skopiować szablonu
Jeśli chcesz utworzyć nowy szablon, który zawiera ustawienia bardzo podobny do istniejącego szablonu, wybierz szablon oryginalnego na **Szablony** kliknij przycisk **KOPIĘ**, określ unikatową nazwę i wprowadzić zmiany, które są potrzebne.

> [!IMPORTANT]
> Podczas kopiowania szablonu, **opublikowaną** lub **archiwizacji** stanu jest również kopiowany. Zatem jeśli kopiujesz publikowanych szablonu jego stan natychmiastowe będą publikowane, chyba że zostanie zmienione.

Można skopiować szablony niestandardowe i domyślnych szablonów. Najlepszym rozwiązaniem skopiuj jedną z domyślnych szablonów zamiast tworzyć nowy szablon niestandardowy, jeśli szablon ma prawa do wszystkich użytkowników w organizacji. Tej metody oznacza, że nie trzeba tworzyć lub Wybierz wiele grup w celu określenia wszystkich użytkowników. W tym scenariuszu jednak pamiętaj określić nową nazwę i opis szablonu skopiowanych dodatkowych języków.

## <a name="BKMK_HowToArchiveTemplates"></a>Jak usunąć szablony (archiwum)
Nie można usuwać domyślnych szablonów, ale można je archiwizować tak, aby użytkownicy nie widzą je.

Podobnie, opublikowaniu szablonu niestandardowego, nie są już potrzebne użytkowników, aby można było go obejrzeć można edytować szablon i wybierz **ARCHIWUM** i **ZAPISAĆ** z **Konfiguruj** strony. Lub możesz wybrać je z **Szablony** strony i wybierz **ARCHIWUM**.

Ponieważ nie można edytować domyślne szablony do archiwizacji tych szablonów, należy użyć **ARCHIWUM** opcję **Szablony** strony. Nie można zarchiwizować Outlook **nie przekazuj** opcji.

#### Aby usunąć szablon domyślny

-   Z **Szablony** strony, wybierz szablon domyślny i kliknij przycisk **ARCHIWUM**.

Stan zmieni się z **opublikowaną** do **archiwizacji**. Jeśli zmienisz zdanie, wybierz szablon i kliknij przycisk **publikowania**.

## <a name="BKMK_RefreshingTemplates"></a>Odświeżanie szablonów dla użytkowników
Korzystając z usług Azure RMS, szablony są automatycznie pobierane na komputerach klienckich, dzięki czemu użytkownicy mogą wybrać je z ich aplikacji. Jednak może być konieczne wprowadzenie zmian do szablonów należy wykonać dodatkowe czynności:

|Aplikacji lub usługi|Jak szablony są odświeżane po wprowadzeniu zmian|
|------------------------|----------------------------------------------------|
|Usługi Exchange Online|Konfiguracja ręczna, wymagane, aby odświeżyć szablony.<br /><br />Kroki konfiguracyjne rozwiń sekcji poniżej [Exchange Online tylko: Konfigurowanie programu Exchange, aby pobrać zmieniony szablonów niestandardowych](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_ExchangeOnlineTemplatesUpdate).|
|Usługi Office 365|Automatyczne odświeżanie — nie dodatkowych kroków wymaganych.|
|2016 pakietu Office i pakietu Office 2013<br /><br />Aplikację RMS sharing dla systemu Windows|Automatycznie odświeżane — według harmonogramu:<br /><br />-   Dla tych nowszej wersji pakietu Office: Domyślny interwał odświeżania to co 7 dni.<br />-   Dla aplikacji RMS sharing dla systemu Windows: Począwszy od wersji 1.0.1784.0, domyślny interwał odświeżania jest codziennie. Wcześniejsze wersje ma domyślny interwał co 7 dni odświeżania.<br /><br />Aby wymusić odświeżenie wcześniej niż ten harmonogram, a następnie rozwiń sekcji poniżej [Office 2016, Office 2013 i aplikację RMS sharing dla systemu Windows: Jak wymusić odświeżenie zmienionych szablonu niestandardowego](#BKMK_Office2013ForceUpdate).|
|Pakiet Office 2010|Odświeżanie podczas logowania się użytkowników.<br /><br />Aby wymusić odświeżenie, poproś lub wymusza na użytkownikach wylogować i zalogować ponownie. Lub, zobacz następującą sekcję [Tylko pakietu Office 2010: Jak wymusić odświeżenie zmienionych szablonu niestandardowego](#BKMK_Office2010ForceUpdate).|
Dla urządzeń przenośnych, które korzystają z aplikacji RMS sharing, szablony są automatycznie pobrać (i odświeżane w razie potrzeby) bez konieczności dodatkowej konfiguracji.

### <a name="BKMK_ExchangeOnlineTemplatesUpdate"></a>Exchange Online tylko: Konfigurowanie programu Exchange, aby pobrać zmieniony szablonów niestandardowych
Jeśli została już skonfigurowana zarządzania prawami do informacji (IRM) dla usługi Exchange Online, dopóki nie zostaną wprowadzone następujące zmiany za pomocą środowiska Windows PowerShell w programie Exchange Online szablonów niestandardowych nie pobierze dla użytkowników.

> [!NOTE]
> Aby uzyskać więcej informacji na temat używania środowiska Windows PowerShell w usłudze Exchange Online, zobacz [przy użyciu programu PowerShell z usługą Exchange Online](https://technet.microsoft.com/library/jj200677%28v=exchg.160%29.aspx).

Tę procedurę należy wykonać w każdej zmianie szablonu.

##### Aby zaktualizować szablonów dla usługi Exchange Online

1.  Za pomocą środowiska Windows PowerShell w programie Exchange Online, połącz się z usługą:

    1.  Podaj usługi Office 365, nazwę użytkownika i hasło:

        ```
        $Cred = Get-Credential
        ```

    2.  Połącz się z usługą Exchange Online, uruchamiając następujące dwa polecenia:

        ```
        $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell/ -Credential $Cred -Authentication Basic –AllowRedirection
        ```

        ```
        Import-PSSession $Session
        ```

2.  Użyj [RMSTrustedPublishingDomain importowania](http://technet.microsoft.com/library/jj200724%28v=exchg.160%29.aspx) zaimportuj ponownie z zaufanej domeny publikacji (zaufaną domenę publikacji) z usług Azure RMS przy użyciu polecenia cmdlet:

    ```
    Import-RMSTrustedPublishingDomain -Name "<TPD name>" -RefreshTemplates -RMSOnline
    ```
    Na przykład, jeśli nazwą zaufaną domenę publikacji jest **RMS Online - 1** (typowa nazwa dla wielu organizacji), wprowadź: **Import-RMSTrustedPublishingDomain -Name "RMS Online - 1" -RefreshTemplates -RMSOnline**

    > [!NOTE]
    > Aby sprawdzić nazwę zaufaną domenę publikacji, można użyć [Get-RMSTrustedPublishingDomain](http://technet.microsoft.com/library/jj200707%28v=exchg.160%29.aspx) polecenia cmdlet.

3.  Aby potwierdzić, że szablony zostały pomyślnie zaimportowane, zaczekaj kilka minut, a następnie uruchomić [Get-RMSTemplate](http://technet.microsoft.com/library/dd297960%28v=exchg.160%29.aspx) polecenia cmdlet i ustawić typ do wszystkich. Na przykład:

    ```
    Get-RMSTemplate -TrustedPublishingDomain "RMS Online - 1" -Type All
    ```
    > [!TIP]
    > Jest przydatne do przechowywania kopii danych wyjściowych, dzięki czemu można łatwo kopiować szablonu nazwy lub identyfikatory GUID później archiwizowania szablonu.

4.  W przypadku każdego importowany szablon, które mają być dostępne w programie Outlook Web App, należy użyć [RMSTemplate zestaw](http://technet.microsoft.com/library/hh529923%28v=exchg.160%29.aspx) polecenia cmdlet i ustawić typ rozproszonych:

    ```
    Set-RMSTemplate -Identity "<name  or GUID of the template>" -Type Distributed
    ```
    Ponieważ program Outlook Web Access buforuje interfejsu użytkownika przez 24 godziny, użytkownicy nie mogą widzieć nowego szablonu dla maksymalnie dziennie.

Ponadto, jeśli Archiwizowanie szablonu (niestandardowe lub domyślny) i używanie usługi Exchange Online z usługi Office 365 użytkowników będzie wyświetlana zarchiwizowane szablony korzystające z programu Outlook Web App lub urządzeń przenośnych, które używają protokołu Exchange ActiveSync.

Tak, aby użytkownicy nie są już wyświetlane tych szablonów, należy połączyć się z usługą za pomocą środowiska Windows PowerShell w programie Exchange Online, a następnie użyć [Set RMSTemplate](http://technet.microsoft.com/library/hh529923%28v=exchg.160%29.aspx) polecenia cmdlet, uruchamiając następujące polecenie:

```
Set-RMSTemplate -Identity "<name or GUID of the template>" -Type Archived
```

### <a name="BKMK_Office2013ForceUpdate"></a>Office 2016, Office 2013 i aplikację RMS sharing dla systemu Windows: Jak wymusić odświeżenie zmienionych szablonu niestandardowego
Edytując rejestr na komputerach z programem Office 2016, pakietu Office 2013 lub Rights Management (RMS) udostępniania aplikacji dla systemu Windows, można zmienić harmonogramu automatycznego tak, że zmienione szablony zostaną odświeżone częściej niż wartość domyślna na komputerach. Możesz też wymusić natychmiastowe odświeżanie przez usunięcie istniejących danych w wartości rejestru.

> [!WARNING]
> Używanie Edytora rejestru w niewłaściwy sposób może spowodować poważne problemy, które mogą wymagać ponownego zainstalowania systemu operacyjnego. Firma Microsoft nie gwarantuje, że można rozwiązać problemy wynikające z niewłaściwego używania Edytora rejestru. Użyj Edytora rejestru na własne ryzyko.

##### Zmiana harmonogramu automatycznego

1.  Za pomocą Edytora rejestru utworzyć i ustawić jedną z następujących wartości rejestru:

    -   Aby ustawić częstotliwość aktualizacji w dniach (co najmniej 1 dzień):  Utwórz wartość rejestru o nazwie **TemplateUpdateFrequency** i zdefiniuj wartość całkowitą dla danych, który określa częstotliwość w dniach, aby pobrać wszystkie zmiany do pobranego szablonu. Skorzystaj z poniższej tabeli, aby zlokalizować ścieżki rejestru do utworzenia tej nowej wartości rejestru.

        |Ścieżki rejestru|Typ|Wartość|
        |--------------------|-------|-----------|
        |HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC|REG_DWORD|TemplateUpdateFrequency|

    -   Aby ustawić częstotliwość aktualizacji w sekundach (co najmniej 1 sekundę):  Utwórz wartość rejestru o nazwie **TemplateUpdateFrequencyInSeconds** i zdefiniuj wartość całkowitą dla danych, który określa częstotliwość w sekundach, aby pobrać wszystkie zmiany do pobranego szablonu. Skorzystaj z poniższej tabeli, aby zlokalizować ścieżki rejestru do utworzenia tej nowej wartości rejestru.

        |Ścieżki rejestru|Typ|Wartość|
        |--------------------|-------|-----------|
        |HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC|REG_DWORD|TemplateUpdateFrequencyInSeconds|

    Upewnij się, utworzenie i ustawić jedną z następujących wartości rejestru nie oba jednocześnie. Jeśli obecne są oba **TemplateUpdateFrequency** jest ignorowana.

2.  Jeśli chcesz wymusić natychmiastowe odświeżanie szablonów, przejdź do następnej procedury. W przeciwnym razie teraz ponownie uruchomić aplikacje pakietu Office i wystąpienia Eksploratora plików.

##### Aby wymusić natychmiastowe odświeżanie

1.  Za pomocą Edytora rejestru, usunąć dane **LastUpdatedTime** wartości. Na przykład może wyświetlać dane **2015-04-20T15:52**; usunąć 2015-04-20T15:52 tak, aby dane nie są wyświetlane. Skorzystaj z poniższej tabeli, aby zlokalizować ścieżki rejestru, aby usunąć ten danych wartości rejestru.

    |Ścieżki rejestru|Typ|Wartość|
    |--------------------|-------|-----------|
    |HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\ &lt; MicrosoftRMS_FQDN &gt; \Template|REG_SZ|LastUpdatedTime|
    > [!TIP]
    > W ścieżce rejestru *&lt; MicrosoftRMS_FQDN &gt;* odwołuje się do usług Microsoft RMS nazwy FQDN. Jeśli chcesz sprawdzić tę wartość:
    > 
    > 1.  Uruchom [Get-AadrmConfiguration](https://msdn.microsoft.com/library/windowsazure/dn629410.aspx) polecenia cmdlet dla usług Azure RMS. Jeśli nie został już zainstalowany moduł programu Windows PowerShell usług Azure RMS, zobacz [Instalowanie programu Windows PowerShell Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).
    > 2.  Z danych wyjściowych, należy zidentyfikować **LicensingIntranetDistributionPointUrl** wartości.
    > 
    >     Na przykład: **LicensingIntranetDistributionPointUrl: https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**
    > 3.  Od wartości, Usuń **https://** i **/_wmcs/licensing** z tych parametrów. Pozostała wartość jest usługi Microsoft RMS nazwy FQDN. W naszym przykładzie nazwy FQDN usługi Microsoft RMS będzie następującą wartość:
    > 
    >     **5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

2.  Usuń następujący folder i wszystkie pliki, które zawiera: **%localappdata%\Microsoft\MSIPC\Templates**

3.  Ponownie uruchom aplikacje pakietu Office i wystąpienia Eksploratora plików.

### <a name="BKMK_Office2010ForceUpdate"></a>Tylko pakietu Office 2010: Jak wymusić odświeżenie zmienionych szablonu niestandardowego
Tak, że zmienione szablony zostaną odświeżone na komputerach bez oczekiwania na użytkownikom Wyloguj się i na powrót, edytując rejestr na komputerach z programem Office 2010, można ustawić wartość. Możesz też wymusić natychmiastowe odświeżanie przez usunięcie istniejących danych w wartości rejestru.

> [!WARNING]
> Używanie Edytora rejestru w niewłaściwy sposób może spowodować poważne problemy, które mogą wymagać ponownego zainstalowania systemu operacyjnego. Firma Microsoft nie gwarantuje, że można rozwiązać problemy wynikające z niewłaściwego używania Edytora rejestru. Użyj Edytora rejestru na własne ryzyko.

##### Aby zmienić częstotliwość aktualizacji

1.  Za pomocą Edytora rejestru, utwórz wartość rejestru o nazwie **UpdateFrequency** i zdefiniuj wartość całkowitą dla danych, który określa częstotliwość w dniach, aby pobrać wszystkie zmiany do pobranego szablonu. Skorzystaj z poniższej tabeli, aby zlokalizować ścieżki rejestru do utworzenia tej nowej wartości rejestru.

    |Ścieżki rejestru|Typ|Wartość|
    |--------------------|-------|-----------|
    |HKEY_CURRENT_USER\Software\Microsoft\MSDRM\TemplateManagement|REG_DWORD|UpdateFrequency|

2.  Jeśli chcesz wymusić natychmiastowe odświeżanie szablonów, przejdź do następnej procedury. W przeciwnym razie teraz ponownie uruchomić aplikacji pakietu Office.

##### Aby wymusić natychmiastowe odświeżanie

1.  Za pomocą Edytora rejestru, usunąć dane **LastUpdatedTime** wartości. Na przykład może wyświetlać dane **2015-04-20T15:52**; usunąć 2015-04-20T15:52 tak, aby dane nie są wyświetlane. Skorzystaj z poniższej tabeli, aby zlokalizować ścieżki rejestru, aby usunąć ten danych wartości rejestru.

    |Ścieżki rejestru|Typ|Wartość|
    |--------------------|-------|-----------|
    |HKEY_CURRENT_USER\Software\Microsoft\MSDRM\TemplateManagement|REG_SZ|lastUpdatedTime|

2.  Usuń następujący folder i wszystkie pliki, które zawiera: **%localappdata%\Microsoft\MSIPC\Templates**

3.  Ponowne uruchomienie aplikacji pakietu Office.

## <a name="BKMK_PowerShellTemplates"></a>Odwołanie do środowiska Windows PowerShell
Wszystko, co można zrobić w portalu zarządzania Azure, aby utworzyć i zarządzać szablonami możesz wykonać z wiersza polecenia przy użyciu programu Windows PowerShell. Ponadto można eksportować i importować szablony, dzięki czemu możesz skopiować szablony między dzierżawcy lub dokonać edycji zbiorczej ze złożonych właściwości w szablonach, takie jak wielojęzyczny nazwy i opisy.

Można również użyć eksportowania i importowania kopii zapasowej i przywracanie szablonów niestandardowych, najlepszym rozwiązaniem, regularnie tworzyć kopie zapasowe szablonów niestandardowych, dzięki czemu po wprowadzeniu zmiany, która nie jest przeznaczony łatwo można przywrócić do poprzedniej wersji.

> [!IMPORTANT]
> Aby użyć środowiska Windows PowerShell do tworzenia i zarządzania szablonami zasad praw usług Azure RMS, użytkownik musi mieć co najmniej wersji 2.0.0.0 [Moduł Windows PowerShell dla usług Azure RMS](http://go.microsoft.com/fwlink/?LinkId=257721).
> 
> Jeśli wcześniej zainstalowano ten moduł programu Windows PowerShell, uruchom następujące polecenie w oknie programu PowerShell, aby sprawdzić numer wersji: `(Get-Module aadrm -ListAvailable).Version`

Aby uzyskać instrukcje instalacji, zobacz [Instalowanie programu Windows PowerShell Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

Polecenia cmdlet używane do obsługi tworzenia i zarządzania szablonami:

-   [Dodaj AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727075.aspx)

-   [AadrmTemplate eksportu](https://msdn.microsoft.com/library/azure/dn727078.aspx)

-   [Get-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727079.aspx)

-   [Get-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727081.aspx)

-   [Importuj AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx)

-   [Nowy AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx)

-   [Usuń AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727082.aspx)

-   [Zestaw AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx)

## Następne kroki
Po skonfigurowaniu szablonów niestandardowych Azure Rights Management, użyj [Mapa wdrożenia usługi zarządzania prawami systemu Azure](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) do sprawdzania, czy istnieją inne czynności konfiguracyjne, które należy wykonać przed można wdrożyć [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] użytkownikom i administratorom. Jeśli nie ma żadnych innych czynności konfiguracyjnych potrzebnych zobacz [Za pomocą systemu Azure Rights Management](../Topic/Using_Azure_Rights_Management.md) operational wskazówki do obsługi pomyślne wdrożenie dla Twojej organizacji.

## Zobacz też
[Konfigurowanie Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

