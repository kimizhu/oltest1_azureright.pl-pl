---
description: na
keywords: na
title: Quick Start Tutorial for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1db923bf-7d19-4fdd-a413-bfeb58af5e03
---
# Samouczek Szybki Start Azure Rights Management
Użyj tego samouczka do szybkiego wypróbowywania Microsoft Azure Rights Management (Azure RMS) dla organizacji za pomocą tylko 5 czynności, które należy wykonać mniej niż 15 minut. Będzie aktywować usługę, bezpiecznie wysyłać pocztą e-mail poufny dokument chroniony w innej organizacji i możliwe jest śledzenie po otwarciu dokumentu. Gdy poufnych dokumentów jest pocztą e-mail, są szyfrowane podczas pracy w trakcie ich przesyłania i mogą być odczytane tylko przez osobę, że jest wysyłany do, przy użyciu uprawnień, które są ustawiane przez nadawcę.

![](../Image/AzRMS_QuickStartStepsAll.PNG)

Ten samouczek ma na celu Administratorzy IT i doradcy, aby pomóc im Azure Rights Management są interpretowane jako rozwiązanie do ochrony informacji w organizacji. W środowisku produkcyjnym z instrukcjami, aby aktywować usługę będą wykonywane przez administratora i instrukcje, aby wysłać dokument będzie wykonywane przez użytkowników końcowych. Oba zestawy instrukcje znajdują się w tej instrukcji, aby zademonstrować scenariusz end-to-end bezpiecznie wysyłać poufny dokument chroniony w innej organizacji. Jeśli masz problemy z ten samouczek wysyłania wiadomości e-mail do [AskIPTeam](mailto:askipteam@microsoft.com?subject=Having%20problems%20with%20the%20Quick%20Start%20tutorial) i pomożemy Ci.

Aby użyć tego samouczka, będą potrzebne następujące czynności:

-   Subskrypcję, która obsługuje Azure Rights Management. Może to być subskrypcji wersji próbnej lub płatnej subskrypcji. Jeśli chcesz użyć śledzenia, dokumentów, które są wymagane do kroku 5, w tym samouczku, subskrypcji musi obsługiwać śledzenia dokumentu. Aby uzyskać więcej informacji na temat opcji subskrypcji oraz łącza do bezpłatne wersje próbne zobacz [Subskrypcje chmury, które obsługują Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) w sekcji [Wymagania dotyczące systemu Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tematu.

    Porada: Jeśli potrzebujesz subskrypcji, w tym z wyprzedzeniem, ponieważ czasami ten proces może potrwać do ukończenia.

-   Konta administratora, aby zarejestrować w Centrum administracyjnym usługi Office 365 lub portalu Azure, dzięki czemu można aktywować usługę Rights Management. To konto musi mieć również, adres e-mail i usługi roboczych poczty e-mail (na przykład usługi Exchange Online lub Exchange Server).

-   Komputer z systemem Windows (minimum Windows 7 z dodatkiem SP1) i którym zainstalowano Office 2016, Office 2013 lub Office 2010.

Zacznijmy od początku.

## Krok 1: Aktywuj usługę Rights Management
![](../Image/AzRMS_QuickStartSteps1.PNG)

Mimo że może mieć subskrypcję, która obsługuje Azure Rights Management, usługa jest domyślnie wyłączona. Aby go aktywować, można użyć w Centrum administracyjnym usługi Office 365 lub portalu Azure:

-   Jeśli masz subskrypcję usługi Office 365, który zawiera Azure Rights Management lub subskrypcję usługi Office 365 który wyklucza Azure Rights Management, ale masz subskrypcję dla autonomicznej usług Azure RMS: **Użyć w Centrum administracyjnym usługi Office 365**.

-   Jeśli nie masz subskrypcji usługi Office 365: **Za pomocą portalu Azure**.

![](../Image/AzRMS_Tutorial_1_Screenshots.png)

#### Aby aktywować usługę Rights Management z Centrum administracyjne usługi Office 365

1.  Przejdź do [portalu usługi Office 365](https://portal.office.com/) i zaloguj się przy użyciu konta służbowego.

2.  Jeżeli w Centrum administracyjnym usługi Office 365 nie wyświetla automatycznie, wybierz ikonę uruchamiania aplikacji w lewym górnym i wybierz polecenie **Admin**.**Administrator** kafelka pojawia się tylko dla administratorów usługi Office 365.

    > [!TIP]
    > Pomoc Centrum administracyjne, zobacz [Centrum administracyjne dotyczące usługi Office 365 - pomoc administrator](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547).

3.  W lewym okienku, rozwiń węzeł **Ustawienia usługi**.

4.  Kliknij przycisk **Rights Management**.

5.  Na **RIGHTS MANAGEMENT** kliknij przycisk **Zarządzaj**.

6.  Na **rights management** kliknij przycisk **aktywować**.

7.  Po wyświetleniu monitu **Czy chcesz aktywować usługę Rights Management?**, kliknij przycisk **aktywować**.

Powinien pojawić się **Rights management została aktywowana** i opcję, aby dezaktywować (może być konieczne ręczne Odśwież stronę)

W tej chwili nie klikaj **Zaawansowane funkcje**. Powoduje przejście do portalu Azure konfigurowania szablonów, które nie są potrzebne dla tego samouczka. Zamiast tego można zamknąć w Centrum administracyjnym usługi Office 365.

#### Aby aktywować usługę Rights Management z portalu Azure

1.  Przejdź do [portalu Azure](http://go.microsoft.com/fwlink/p/?LinkID=275081) i zaloguj się.

2.  W lewym okienku kliknij **usługi ACTIVE DIRECTORY**.

3.  Z **usługi active directory** kliknij przycisk **RIGHTS MANAGEMENT**.

4.  Wybierz katalog, w celu zarządzania [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], kliknij przycisk **AKTYWACJI**, a następnie potwierdzić tę czynność.

**Stan zarządzania prawami** teraz powinien być wyświetlany **Active** i **AKTYWACJI** opcja zostanie zastąpiony **DEZAKTYWUJ**.

Mimo że można skonfigurować inne opcje zarządzania prawami w portalu, te nie są wymagane dla tego samouczka, możesz zamknąć portalu Azure.

To wszystko, czego potrzebujesz robić w pierwszym kroku. Usługa jest aktywny, wszyscy użytkownicy w organizacji teraz może zacząć chronić ważne i poufnych dokumentów. W środowisku produkcyjnym można ograniczyć, który może zrobić to początkowo etapowe wdrażanie. Ale nie jest konieczne dla tej instrukcji.

Mimo że nie zawartych w tym miejscu dla wdrożenia produkcyjnego, prawdopodobnie będzie także prawdopodobnie chcesz skonfigurować niestandardowe szablony. Szablony ułatwiają użytkownikom szybko zastosować odpowiednie ustawienia, gdy są niezbędne do ochrony plików. Podczas aktywowania Rights Management, automatycznie pobrać 2 domyślnych szablonów i prawdopodobnie będzie dodatkowo szablonów niestandardowych w środowisku produkcyjnym. Jednak szablony nie są potrzebne dla tego samouczka, więc jest gotowy przejść do następnego kroku.

|Aby uzyskać więcej informacji|Dodatkowe informacje|
|---------------------------------|------------------------|
|Temat aktywowania usługi Rights Management i kontrolowanie, kto może chronić pliki i wiadomości e-mail, gdy usługa jest aktywowana →|[Aktywowanie Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md)|
|O domyślnych szablonach oraz sposobu tworzenia nowych, → szablonów niestandardowych|[Konfigurowanie niestandardowych szablonów Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md)|

## Krok 2: Zainstaluj tworzenia aplikacji Rights Management
![](../Image/AzRMS_QuickStartSteps2.PNG)

Rights Management sharing application (znanej także jako "aplikację RMS sharing") nie jest to wymagane dla Azure Rights Management, ale zalecamy na wszystkich komputerach i urządzeniach przenośnych, które obsługują Azure Rights Management. Aplikacja RMS sharing integruje się z pakietem Office aplikacji przez zainstalowanie pakietu Office dodatku, dzięki czemu użytkownicy mogą łatwo chronić pliki bezpośrednio ze Wstążki. On również umożliwia ochronę wszystkich typów plików, stosując ogólna ochrona plików, które nie są obsługiwane przez Azure Rights Management oraz dokumentu śledzenia lokacji dla użytkowników, śledzenie i odwoływanie plików, które zostały objęte ochroną. Firma Microsoft będzie używać śledzenia lokacji dalej w tym samouczku dokumentów.

Ta aplikacja może pobrać i oferuje przy użyciu skryptu instalacji w środowiskach produkcyjnych. Jednak dla tej instrukcji, firma Microsoft będzie go zainstalować lokalnie.

![](../Image/AzRMS_Tutorial_2_Screenshots.png)

#### Aby pobrać i zainstalować Rights Management udostępnianie aplikacji

1.  Przejdź do [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) strony w witrynie sieci Web firmy Microsoft.

2.  W **komputerów** kliknij ikonę **aplikacji RMS dla systemu Windows** i Zapisz **Setup.exe** plik w celu zainstalowania aplikacji do udostępniania Microsoft Rights Management.

3.  W przypadku instalacji lokalnej musi być kontem administratora uruchom pobrany plik Setup.exe. Jeśli zostanie wyświetlony monit, aby kontynuować, kliknij przycisk **Tak**.

4.  Na **Instalatora Microsoft RMS** kliknij przycisk **Dalej**, i poczekaj na zakończenie instalacji.

5.  Po zakończeniu instalacji, kliknij przycisk **Uruchom ponownie** Jeśli monit o ponowne uruchomienie komputera, lub kliknij przycisk  **Zamknij** do ukończenia instalacji.

Teraz możesz zacząć chronić pliki, które zawierają informacje, które chcesz udostępnić, ale tylko osobom, które określisz.

|Aby uzyskać więcej informacji|Dodatkowe informacje|
|---------------------------------|------------------------|
|O instalacji lokalnej tworzenia aplikacji dla systemu Windows i użytkowników → instrukcje Rights Management|[Przewodnik użytkownika aplikacji udostępniania zarządzania prawami dostępu](http://technet.microsoft.com/library/dn339006.aspx)|
|O instalacji inicjowanych przez skrypty tworzenia aplikacji dla systemów Windows i bardziej technicznych → informacji Rights Management|[Przewodnik administratora aplikacji udostępniania zarządzania prawami dostępu](http://technet.microsoft.com/library/dn339003.aspx)|
|Aby zrozumieć różnicę między macierzystym i ochrona ogólna →|[Jaka jest różnica między ogólną i ochroną ochrona wbudowana (natywna)?](https://technet.microsoft.com/library/dn574738.aspx)|

## Krok 3: Poczty e-mail w dokumencie, który ma być chroniony
![](../Image/AzRMS_QuickStartSteps3.PNG)

W tym kroku najpierw utworzyć i zapisać dokumentu za pomocą programu Word, który reprezentuje dokumentu, który chcesz chronić i nadaj mu nazwę **Confidential.docx**. Ten samouczek rzeczywiście zawiera tekst nie ma znaczenia, ale ma będzie zawierać tekst, aby łatwiej można potwierdzić autoryzowanym odbiorcom można odczytać jej. Na przykład należy wpisać: **Jeśli może czytać to załącznika wiadomości e-mail, nadawca pomyślnie udostępnił plik był chroniony za pomocą usługi Azure RMS.**

Następnie możesz bezpiecznie udostępniać tego dokumentu pocztą e-mail.

![](../Image/AzRMS_Tutorial_3_Screenshots.png)

#### Można bezpiecznie udostępniać dokumentu pocztą e-mail

1.  Za pomocą programu Outlook, Utwórz nową wiadomość i Dołącz plik, który został utworzony.

2.  W **do** wpisz jedną lub więcej służbowy adres e-mail dotyczy. Upewnij się, takich jak określić adres e-mail firmy, **janetm@contoso.com** lub **p.dover@fabrikam.com** ponieważ obecnie Azure Rights Management nie obsługuje adresy e-mail osobistych, których można użyć w domu od dostawcy sieci Internet. Nie martw się o tym, czy osoby, do której jest wysyłana do ma Azure Rights Management, czy nie.

3.  Wpisz temat, takie jak  **dokument poufny** a następnie wpisz krótki komunikat do obsługi poczty e-mail, takich jak **należy przeczytać ten dokument poufne i nie udostępniać innym osobom.**

4.  Następnie na **komunikat** kartę w **RMS** kliknij polecenie **Udostępnij chronione** a następnie kliknij przycisk **Udostępnij chronione** ponownie:

5.  W **Udostępnij chronione** okno dialogowe:

    1.  Wybierz **Viewer — widok tylko**.

        Oznacza to, że nasze odbiorców będą mogli wyświetlić dokument, ale nie edytować lub jego wydrukowanie.

    2.  Wybierz **E-mail mnie, gdy ktoś spróbuje otworzyć te dokumenty**.

        Otrzymasz wiadomość e-mail z powiadomieniem za każdym razem adresatów spróbuj otworzyć załącznik, a także jeśli ktoś spróbuje otworzyć go — na przykład odbiorca przesyła wiadomość e-mail do rozwiązanie. W tym scenariuszu ostatnich zobaczysz, że nastąpiła odmowa dostępu i z szczegóły użytkownika, można określić, czy zostać wysłana kopia dokumentu, które mogą otwierać tej osoby.

    3.  Wybierz **Wybiorę natychmiast odwołać dostęp do tych dokumentów**.

        Ta opcja wymaga odbiorcy mają być połączony z Internetem za każdym razem, otwierając załącznik, ale z korzyści czy jeśli później można odebrać dokumentu, przy następnym próby otwarcia, ich nie będzie mógł. Jeśli ta opcja nie jest zaznaczona, adresatów można go otworzyć, nawet bez połączenia z Internetem, ale z wadą, że jeśli później można odebrać dokumentu, może występować opóźnienie podczas która obowiązuje.

    4.  Kliknij przycisk **Wyślij teraz**.

        Wiadomość e-mail z załącznikiem są wysyłane na adresy e-mail, określone przez użytkownika. Oprócz wiadomości e-mail zobaczą instrukcje jak odczytywać załączony dokument, który jest chroniony przez Azure Rights Management.

Teraz została wysłana chroniony dokument, aby przystąpić do Zadaj adresatów czekać na jego odebraniem, a następnie otwórz go. Ale pozostaw Outlook, ponieważ użyjemy go ponownie w naszym ostatni krok do śledzenia załącznik.

|Aby uzyskać więcej informacji|Dodatkowe informacje|
|---------------------------------|------------------------|
|Pełne instrukcje i alternatywne metody ochrony pliki, które mają pocztą e-mail →|[Ochrona pliku Udostępnij pocztą e-mail przy użyciu Rights Management udostępnianie aplikacji](https://technet.microsoft.com/library/dn574735.aspx)|
|O opcjach w **Udostępnij chronione** okno dialogowe →|[Opcje okna dialogowego Rights Management udostępnianie aplikacji](https://technet.microsoft.com/library/dn574738.aspx)|

## Krok 4: Zapytaj Twoich odbiorców, aby otworzyć dokumentu e-mail
![](../Image/AzRMS_QuickStartSteps4.PNG)

Adresatów można używać wiele urządzeń do odczytu chroniony dokument, który można wysłać jako załącznik wiadomości e-mail. Urządzenia obejmują iPads, iPhones, Android tabletów i telefonów, komputerów Mac, a także komputery z systemem Windows.

Poproś go do wiadomości e-mail, który można wysłać do odczytu. Zobaczy wiadomości e-mail i przed nim następujący tekst:

**Nadawca ma chronione załączniki z Microsoft RMS. Należy** [Zaloguj się](http://aka.ms/rms) **do ich otwierania.**

Po kliknięciu łącza zajmuje je do instrukcji, aby zainstalować aplikację RMS i w razie potrzeby utwórz pod kątem bezpłatne konto. Bezpłatne konto udziela je subskrypcję do usług RMS dla osób, który zapewnia autoryzowani użytkownicy mogą zawsze odczytać chronionego dokumentu, nawet jeśli w organizacji nie ma Azure RMS. Następnie są one gotowe do odczytu załącznika chronionych za pomocą następujących instrukcji.

![](../Image/AzRMS_Tutorial_4_Screenshots.png)

#### Aby wyświetlić załącznik chronionego dokumentu

1.  Ponieważ Azure Rights Management chroniony dokumentu programu Word, dostępne są dwie załączników wiadomości e-mail. Są to faktycznie dwie wersje tego samego pliku, ale z różne rozszerzenia nazw plików. Otwórz wersji, który ma **.ppdf** rozszerzenia nazwy pliku (**Confidential.ppdf**).

    Jeśli masz wersję [Office na urządzeniu, która obsługuje Rights Management](https://technet.microsoft.com/library/dn655136.aspx), możesz otworzyć wersję pliku (**Confidential.docx**), tak aby zostanie otwarty w programie Word.

2.  Jeśli zostanie wyświetlony monit o nazwę użytkownika i hasło, wprowadź swoją nazwę użytkownika w formacie adres e-mail użytej do wysyłania wiadomości e-mail i załącznika. Na przykład **janetm@contoso.com** lub **p.dover@fabrikam.com**. O podanie hasła wpisz hasło, które podano po zarejestrowaniu do usług RMS dla osób. Lub, jeśli w organizacji jest Azure RMS, wprowadź hasło normalną pracę.

Otwiera dokument i teraz można odczytać zawartości. Na przykład może być powiedz **Jeśli to można odczytać z załącznika wiadomości e-mail, nadawca pomyślnie udostępnił plik, który jest chroniony Azure RMS** Ponieważ jest tylko do odczytu, nie można zmienić zawartości.

Jako opcjonalny etap może poprosić adresata do przesyłania dalej wiadomości e-mail do innych osób, które nie włączono swoje oryginalne wiadomości e-mail. Nawet jeśli te inne osoby pracy dla organizacji mającej Azure Rights Management lub odnoszą się one do własnych usług RMS dla osób subskrypcji, nie będzie można otwierać załącznik. Gdy są one promowane dla nazwy użytkownika, będzie otrzymywał odmowę dostępu do dokumentu.

Teraz, kiedy odbiorca ma otworzyć załącznik i opcjonalnie przekazała je do innej osobie, założyć wiadomość e-mail z powiadomieniem opisujący tego działania. Jednak wiadomości e-mail są łatwe do utraty wraz z upływem czasu, dlatego używać śledzenia witryny, która opisanych w punkcie końcowym dokumentu lepszy sposób do śledzenia, który uzyskał dostęp do dokumentu.

|Aby uzyskać więcej informacji|Dodatkowe informacje|
|---------------------------------|------------------------|
|Pełna zawiera instrukcje dotyczące wyświetlania plików, które są chronione → Azure Rights Management|[Wyświetlanie i używanie plików chronionych przez usługi Rights Management](https://technet.microsoft.com/library/dn574741.aspx)|
|Temat bezpłatnej subskrypcji, RMS dla osób →|[RMS dla osób i Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md)|
|O dwie wersje pliku możesz zobaczyć dołączone do wiadomości e-mail →|[Co to jest plik .ppdf, który jest tworzony automatycznie?](https://technet.microsoft.com/library/dn574738.aspx)|

## Krok 5: Śledzenie chronionego dokumentu
![](../Image/AzRMS_QuickStartSteps5.PNG)

> [!NOTE]
> Dla tego etapu musi mieć subskrypcji, która obsługuje śledzenia dokumentu. Aby sprawdzić, czy subskrypcja zawiera śledzenia dokumentów, zobacz [ofert porównanie z usług zarządzania prawami (RMS)](https://technet.microsoft.com/dn858608.aspx).

Ten krok jest opcjonalny, ale wiedzieć, jeśli załącznik, który będą wysyłane do osób zostało otwarte, kiedy, a nawet w przypadku, takich jak największej liczbie użytkowników. Na przykład:

-   Odpowiedź od osób jest oczekiwanie przez określony czas i możesz zobaczyć z witryny śledzenia dokumentu czy nie otworzył dokument mimo że serwisowe terminu. Wyślij jej uzupełniającego wiadomości e-mail lub jej telefonu odpowiednim dla przypomnienia.

-   Po ustalenia, czy ktoś otworzył ten dokument, możesz monitorowania poprosić swoje if użytkownik ma pytania lub wymaga dodatkowych informacji.

![](../Image/AzRMS_Tutorial_5_Screenshots.png)

#### Aby śledzić chronionego dokumentu

1.  Za pomocą programu Outlook, na **Strona główna** kartę w **RMS** kliknij polecenie **użycie ścieżki**.

2.  Jeśli widzisz **Chroń i Udostępnij na własnych warunkach** kliknij przycisk **Zaloguj się** i podać nazwę użytkownika i hasło ponownie.

3.  Na **dokumentów udostępnionych** strony, zobaczysz dokumentu dołączonego do wiadomości e-mail, **Confidential.docx**. W tym momencie jest tylko ten plik jest wyświetlany, ale zgodnie z udostępnieniem dodatkowych dokumentów chronionych robią listy.

    Na tej stronie zobaczysz, gdy udostępniony dokumentu (po wysłaniu wiadomości e-mail z załącznikiem chronionych), Data ostatniej aktywności i nazwy odbiorcy wysłania wiadomości e-mail do. Kliknij nazwę dokumentu, aby uzyskać więcej informacji.

4.  Na nową stronę, która zawiera nazwę pliku, które zostało kliknięte, zobaczysz informacje podsumowania dla tego dokumentu tylko i listę inne opcje, które są dostępne dla dokumentu (**listy**, **osi**, **mapy**, **Ustawienia**).

    Kliknij przycisk każdego opcję, aby poznać różne sposoby śledzenia chronionego dokumentu. Lub nadal na **Podsumowanie** kliknij przycisk **otwarty w programie Excel** do eksportowania informacji do arkusza kalkulacyjnego lub kliknij przycisk **odwołać dostęp** Aby zatrzymać udostępnianie dokumentu.

Powrót do tej witryny do śledzenia dalszych czynności chroniony dokument lub odwołać dostęp, jeśli to konieczne. Użytkownik może nawet dostępu do tej witryny z urządzenia przenośnego lub tablet, za pomocą przeglądarki z tego łącza: [śledzenia dokumentu](http://go.microsoft.com/fwlink/?LinkId=529562)

|Aby uzyskać więcej informacji|Dodatkowe informacje|
|---------------------------------|------------------------|
|Pełne instrukcje dotyczące śledzenia → swoje dokumenty|[Śledzenie i odwołać dokumentów, gdy użytkownik korzysta z RMS sharing aplikacji](https://technet.microsoft.com/library/dn986611.aspx)|
|Dwóch minutę wideo która wyjaśnia i pokazuje śledzenia → dokumentu|[Śledzenie Azure RMS dokumentu i odwołania](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation)|
|Do rozwiązywania problemów i klienta → pytania|[Często zadawane pytania dotyczące śledzenia dokumentu](https://technet.microsoft.com/dn947488)|

## Następne kroki
W tym samouczku zwiększyć za pośrednictwem jednego scenariusz jak Azure RMS może pomóc chronić dane. Aby wyświetlić inne typowe zastosowania, zobacz [Azure RMS w akcji](https://technet.microsoft.com/library/jj585026.aspx) sekcji z [Co to jest Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md) artykułu. Istnieją inne sekcje, w tym artykule, który może również być przydatne, takie jak jakie problemów biznesowych i jak działa Azure RMS można rozwiązać.

Jeśli jesteś gotowy do wdrażania Azure RMS, użyj [Mapa wdrożenia usługi zarządzania prawami systemu Azure](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) kroki wdrażania i łącza, aby uzyskać instrukcje dotyczące wykonywania określonych zadań.

## Zobacz też
[Wprowadzenie do korzystania z systemu Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

