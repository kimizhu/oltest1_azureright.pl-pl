---
description: na
keywords: na
title: Microsoft Rights Management sharing application user guide - original publication
search: na
ms.date: na
ms.tgt_pltfrm: na
ms.assetid: 350b6869-084d-4e8a-a4d3-df44a40fa13b
robots: noindex,nofollow
---
# Przewodnik użytkownika aplikacji do tworzenia i przetwarzania dokument&#243;w chronionych usługami Microsoft Rights Management — publikacja oryginalna
Ten przewodnik użytkownika aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management dla systemu Windows zawiera następujące sekcje:

-   [Evaluating and Installing Microsoft Rights Management sharing application](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_Eval)

-   [Using Microsoft Rights Management sharing application](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_UsingMSRMSApp)

-   [Using User-Authored Permissions and Sharing Protected Content](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_Custom)

-   [Using the Office Toolbar Add-in](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_OfficeToolbar)

-   [Administrator’s guidance for Microsoft Rights Management sharing application](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_AdminGuide)

Aby poznać często zadawane pytania oraz informacje dotyczące rozwiązywania problemów, zobacz [Często zadawane pytania dotyczące aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management dla systemu Windows](http://go.microsoft.com/fwlink/?LinkId=303971).

## <a name="BKMK_Eval"></a>Ocena i instalacja aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management
W tej sekcji wyjaśniono, czym jest aplikacja do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management oraz w jaki sposób można ją zainstalować:

-   [What is the Microsoft Rights Management sharing application?](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_WhatIs)

-   [Requirements for Microsoft Rights Management sharing application](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_Reqs)

-   [Installing the Microsoft Rights Management sharing application](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_Install)

### <a name="BKMK_WhatIs"></a>Co to jest aplikacja do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management?
Aplikacja do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management to opcjonalna aplikacja do pobrania dla systemu Microsoft Windows, która zapewnia następujące korzyści:

-   Rozszerza Eksploratora plików (znanego również jako Eksplorator Windows w systemie Windows 7 i wcześniejszych wersjach) o możliwość ochrony pojedynczego pliku lub masowej ochrony wielu plików, a także wszystkich plików w wybranym folderze.

-   Dodaje obsługę ochrony dowolnego typu pliku oraz wbudowanej przeglądarki dla często używanych typów plików tekstowych i obrazów.

-   Dodaje nowe przyciski do paska narzędzi pakietu Microsoft Office dla programów Word, PowerPoint i Excel.

### <a name="BKMK_Reqs"></a>Wymagania dotyczące aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management
Aby można było używać aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management, na komputerze musi działać system operacyjny Windows 8.1, Windows 8 lub Windows 7.

Aplikacja do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management wymaga programu AD RMS Client 2.1, który jest instalowany w ramach pakietu instalacyjnego. Aplikacja do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management będzie działać tylko z tą wersją klienta usług AD RMS.

### <a name="BKMK_Install"></a>Instalowanie aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management
Aby zainstalować aplikację do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management, wykonaj następujące czynności:

1.  Przejdź do strony [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) w witrynie internetowej firmy Microsoft.

2.  W sekcji **Komputery** kliknij ikonę **aplikacji RMS dla systemu Windows** i zapisz pakiet instalacyjny aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management na swoim komputerze.

3.  Kliknij dwukrotnie pobrany skompresowany plik, a następnie kliknij dwukrotnie plik **setup.exe**. Jeśli zostanie wyświetlony monit o kontynuowanie, kliknij pozycję **Tak**.

4.  Na stronie **Instalowanie usług Microsoft RMS** kliknij przycisk **Dalej** i poczekaj na zakończenie instalacji.

5.  Po zakończeniu instalacji kliknij pozycję **Uruchom ponownie**, aby ponownie uruchomić komputer i ukończyć instalację. Możesz również kliknąć pozycję **Zamknij** i uruchomić komputer ponownie później, aby ukończyć instalację.

## <a name="BKMK_UsingMSRMSApp"></a>Używanie aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management
W tej sekcji opisano różne sposoby stosowania aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management:

-   [Creating a protected text (.ptxt) file](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_CreatePTXT)

-   [Viewing a protected text (.ptxt) or a protected image file](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_ViewPTXT)

-   [Creating a generic protected (.pfile) file](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_CreatePFILE)

-   [Viewing a generic protected (.pfile) file](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_ViewPFILE)

-   [Removing protection from a file](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_Unprotect)

### <a name="BKMK_CreatePTXT"></a>Tworzenie chronionego pliku tekstowego (ptxt)
Za pomocą aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management można przekonwertować zwykły plik tekstowy (txt) na plik chroniony (ptxt).

##### Aby utworzyć chroniony plik tekstowy (ptxt)

1.  W Eksploratorze plików kliknij prawym przyciskiem myszy wewnątrz folderu, wskaż pozycję **Nowy**, a następnie kliknij pozycję **Dokument tekstowy**.

2.  Zmień nazwę pliku (np.: Przykład.txt).

3.  Kliknij dwukrotnie plik, aby otworzyć go w Notatniku.

4.  W programie Notatnik dodaj kilka wierszy tekstu do pliku, na przykład takich jak poniższe, a następnie zapisz ten plik:

    ```
    This is a sample text file.
    This is a sample text file.
    This is a sample text file.
    This is a sample text file. 
    This is a sample text file.
    This is a sample text file.
    ```

5.  Kliknij plik prawym przyciskiem myszy, wskaż pozycję **Włącz ochronę miejscową**, a następnie wybierz szablon z listy. (Pamiętaj, że jeśli używasz narzędzia po raz pierwszy, musisz wybrać pozycję **Firma — Ochrona**, aby zainicjować pobieranie szablonów dla swojej organizacji).

6.  Na ekranie **Aplikacja do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management** potwierdź zasady, które chcesz zastosować, a następnie kliknij pozycję **Zastosuj**, a po włączeniu ochrony pliku kliknij pozycję **Zamknij**.

### <a name="BKMK_ViewPTXT"></a>Wyświetlanie chronionego pliku tekstowego (ptxt) lub chronionego pliku obrazu
Aby wyświetlić chroniony plik tekstowy (ptxt), kliknij dwukrotnie ten plik (np. Przykład.ptxt) w Eksploratorze plików. Może zostać wyświetlony monit o autoryzację aplikacji do uzyskiwania praw. Zasady ochrony zostaną wyświetlone u góry pliku.

Chronione obrazy mogą być otwierane i wyświetlane w podobny sposób.

### <a name="BKMK_CreatePFILE"></a>Tworzenie pliku chronionego ogólnie (pfile)
Format pliku chronionego ogólnie (pfile) może być stosowany w celu zapewniania ogólnego poziomu ochrony dla plików o typach, które nie są bezpośrednio obsługiwane przez aplikację do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management lub inne aplikacje dostarczające wbudowaną ochronę typu RMS.

Przykładowo: format pliku chronionego ogólnie może być stosowany do ochrony plików vsd utworzonych w programie Microsoft Visio (który obecnie nie obsługuje wbudowanej ochrony).

> [!NOTE]
> Pliki używające ogólnej ochrony są zabezpieczane wyłącznie na potrzeby uwierzytelniania. Użytkownik autoryzowany do używania pliku chronionego (pfile) będzie uwierzytelniony, a jego prawa i uprawnienia zostaną wyświetlone, ale nie będzie można ich wymusić po otwarciu pliku w jego oryginalnym formacie (na przykład po otwarciu pliku vsd w programie Visio). Użytkownik, który nie jest autoryzowany lub nie może zostać uwierzytelniony, nie będzie mógł otworzyć pliku chronionego.

##### Aby utworzyć plik chroniony ogólnie (pfile) z pliku rysunku programu Visio (vsd)

1.  W Eksploratorze plików kliknij prawym przyciskiem myszy wewnątrz folderu, wskaż pozycję **Nowy**, a następnie kliknij pozycję **Nowy dokument programu Visio**.

2.  Zmień nazwę pliku (np. Przykład.vsd).

3.  Kliknij dwukrotnie plik, aby otworzyć go w programie Visio.

4.  W programie Visio dodaj elementy do rysunku, a następnie zapisz i zamknij plik.

5.  Kliknij plik prawym przyciskiem myszy, wskaż pozycję **Włącz ochronę miejscową**, a następnie wybierz szablon zasad z listy. (Pamiętaj, że jeśli używasz narzędzia po raz pierwszy, musisz wybrać pozycję **Firma — Ochrona**, aby zainicjować pobieranie szablonów dla swojej organizacji).

6.  Na ekranie **Aplikacja do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management** wybierz zasadę, którą chcesz zastosować, a następnie kliknij pozycję **Zastosuj**.

7.  Zostanie wyświetlony komunikat z informacją, że plik chroniony został zapisany jako plik Przykład.vsd.pfile (oryginalny plik zostanie usunięty).

### <a name="BKMK_ViewPFILE"></a>Wyświetlanie pliku chronionego ogólnie (pfile)
Aby wyświetlić plik chroniony ogólnie (pfile), kliknij dwukrotnie ten plik (np. plik Przykład.vsd.pfile) w Eksploratorze plików, a następnie kliknij pozycję **Otwórz**.

### <a name="BKMK_Unprotect"></a>Usuwanie ochrony z pliku
Aplikacja do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management umożliwia korzystanie z opcji usuwania ochrony z plików, które były wcześniej chronione.

Aby usunąć ochronę (tj. wyłączyć ochronę) w przypadku pliku, który był wcześniej chroniony, zastosuj opcję **Usuń ochronę** w następujący sposób:

1.  Kliknij prawym przyciskiem myszy plik **Sample.ptxt**, wskaż pozycję **Włącz ochronę miejscową**, a następnie kliknij pozycję **Usuń ochronę**. Może zostać wyświetlony monit o autoryzację aplikacji do uzyskiwania praw.

2.  Plik Przykład.ptxt zostanie usunięty i zamieniony na plik Przykład.txt.

## <a name="BKMK_Custom"></a>Korzystanie z uprawnień utworzonych przez użytkownika i udostępnianie chronionej zawartości
W tej sekcji omówiono ochronę i używanie pliku korzystającego z uprawnień utworzonych przez użytkownika, udostępnianie chronionej zawartości oraz ochronę wielu plików:

-   [Protecting a file with user-authored permissions](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_ProtectCustom)

-   [Consuming files that have user-authored protection](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_UserDefined)

-   [Sharing protected content](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_ShareProtected)

-   [Using keyboard shortcuts](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_AccessKeys)

-   [Applying protection to multiple files and folders](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_Multiple)

### <a name="BKMK_ProtectCustom"></a>Ochrona pliku z uprawnieniami utworzonymi przez użytkownika
Ochrona utworzona przez użytkownika może być stosowana:

-   Aby ograniczać dostęp do plików tylko do określonej listy poszczególnych użytkowników identyfikowanych na podstawie ich adresów e-mail.

-   Aby ograniczać używanie pliku tylko do określonych praw, takich jak prawo tylko do odczytu do dokumentu.

Aby chronić plik z uprawnieniami utworzonymi przez użytkownika, kliknij plik prawym przyciskiem myszy, kliknij pozycję **Włącz ochronę miejscową** i kliknij przycisk **Uprawnienia niestandardowe**. Zostanie wyświetlony poniższy ekran:

![](../Image/ADRMS_MSRMSApp_ProtectCustom.gif)

Wprowadź adresy e-mail użytkowników z listy, wybierz uprawnienia do pliku za pomocą suwaka, a następnie kliknij przycisk **Zastosuj**.

### <a name="BKMK_UserDefined"></a>Używanie plików korzystających z uprawnień utworzonych przez użytkownika
Większość chronionych plików obsługiwanych przez aplikację do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management będzie chroniona przez stosowanie poziomów ochrony opartych na szablonach. Aplikacja do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management może jednak również obsługiwać pliki, którym przyznano poziom ochrony utworzony przez użytkownika.

Ochrona tworzona przez użytkownika może być stosowana do uzyskiwania następujących typów ochrony pliku:

-   Do ograniczenia dostępu do plików tylko do bardzo szczegółowej listy poszczególnych użytkowników identyfikowanych na podstawie ich adresów e-mail.

-   Do ograniczenia używania pliku tylko do określonego prawa, takiego jak prawo tylko do wydruku do dokumentu.

W przypadku formatów plików obrazów i plików tekstowych ten poziom ochrony wymaga, aby wszelkie aplikacje używane do edycji, zapisywania i ograniczania plików tekstowych oraz plików obrazów zostały zaprojektowane z myślą o obsłudze ochrony usług RMS oraz miały zaimplementowane interfejsy API ochrony udostępnione w zestawie SDK usług AD RMS.

Podczas wyświetlania chronionego pliku tekstowego, względem którego zastosowano ochronę użytkownika, będzie zauważalna niewielka różnica w sposobie wyświetlania uprawnień dla pliku, co pokazano w poniższym przykładzie.

W przypadku plików chronionych przy użyciu formatu pliku ochrony ogólnej (pfile) określone prawa lub uprawnienia przyznane przez użytkownika zostaną wyświetlone na ekranie potwierdzenia zamiast nazwy szablonu użytego do ochrony pliku, co zostało pokazane na poniższej ilustracji.

![](../Image/ADRMS_MSRMSApp_SP_ConsumePfile.gif)

### <a name="BKMK_ShareProtected"></a>Udostępnianie chronionej zawartości
Aby chronić i udostępniać zawartość, kliknij prawym przyciskiem myszy plik, a następnie kliknij pozycję **Udostępnij chronione**. Zostanie wyświetlony poniższy ekran:

![](../Image/ADRMS_MSRMSAPP_SP_ShareProtected.gif)

Wprowadź adresy e-mail użytkowników z listy, wybierz uprawnienia do pliku za pomocą suwaka, a następnie kliknij przycisk **Wyślij**. Aplikacja uruchomi program Outlook przy użyciu wstępnego adresu e-mail, z załączonym chronionym plikiem. Oryginalny plik nie będzie chroniony.

Aby umożliwić użytkownikom wyświetlanie chronionych plików na urządzeniach z systemem innym niż Windows, kliknij pozycję **Zezwalaj na użycie na wszystkich urządzeniach**. Użytkownicy będą musieli [pobrać aplikację do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) na swoje urządzenia.

### <a name="BKMK_AccessKeys"></a>Korzystanie ze skrótów klawiaturowych
Naciśnij klawisz **Alt**, aby wyświetlić dostępne klawisze dostępu. Naciśnij klawisze **Alt**+ odpowiedni klawisz dostępu, aby wybrać określoną opcję. Na przykład w oknie dialogowym **Udostępnianie chronionej zawartości** naciśnij klawisz **Alt** w celu wyświetlenia klawiszy dostępu, a następnie naciśnij klawisze **Alt+u** w celu wybrania opcji **Użytkownicy będą musieli się zalogować przy każdym otwarciu tego pliku**.

![](../Image/ADRMS_MSRMSApp_AccessKeys.png)

### <a name="BKMK_Multiple"></a>Stosowanie ochrony do wielu plików i folderów
Aplikacja do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management może być również używana do stosowania ochrony do więcej niż jednego pliku, na przykład dzięki możliwości wybierania wielu plików lub folderu zawierającego niechronione pliki w Eksploratorze plików.

##### Aby chronić kilka plików lub wszystkie pliki w wybranym folderze

1.  W Eksploratorze plików wybierz wiele plików lub wybierz folder zawierający wiele plików, które mają być chronione.

2.  Kliknij wybrany folder lub wybrane pliki prawym przyciskiem myszy, wskaż pozycję **Włącz ochronę miejscową**, a następnie wybierz szablon z listy. (Pamiętaj, że jeśli używasz narzędzia po raz pierwszy, musisz wybrać pozycję **Firma — Ochrona**, aby zainicjować pobieranie szablonów dla swojej organizacji).

3.  Na ekranie **Aplikacja do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management** sprawdź, czy pliki zostały poddane ochronie.

W przypadku błędów zobacz [Często zadawane pytania dotyczące aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management dla systemu Windows](http://go.microsoft.com/fwlink/?LinkId=303971).

## <a name="BKMK_OfficeToolbar"></a>Używanie dodatku dla paska narzędzi pakietu Office
Możesz chronić i udostępniać pliki programu Word, PowerPoint i Excel bezpośrednio z pakietu Microsoft Office, używając dodatku aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management dla Wstążki pakietu Office. Kliknij pozycję **Udostępnij chronione** na wstążce, aby uruchomić aplikację do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management.

![](../Image/ADRMS_MSRMSApp_SP_OfficeToolbar.png)

## <a name="BKMK_AdminGuide"></a>Wskazówki dla administratora dotyczące aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management
Przewodnik administratora aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management zawiera następujące sekcje:

-   [Microsoft Rights Management sharing application Technical Overview](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_AdminOverview)

-   [Supported File Types](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_SupportFileTypes)

-   [Automatic deployment for the Microsoft Rights Management sharing application](../Topic/Microsoft_Rights_Management_sharing_application_user_guide_-_original_publication.md#BKMK_ScriptedInstall)

### <a name="BKMK_AdminOverview"></a>Omówienie techniczne aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management
Aplikacja do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management to opcjonalna aplikacja do pobrania dla systemu Microsoft Windows i innych platform, która zapewnia następujące korzyści:

-   Ochrona pojedynczego pliku lub masowa ochrona wielu plików, a także wszystkich plików w wybranym folderze.

-   Pełna obsługa ochrony dowolnego typu pliku oraz wbudowana przeglądarka dla często używanych typów plików tekstowych i obrazów.

-   Ogólna ochrona plików, które nie obsługują ochrony usługami RMS.

-   Pełne współdziałanie z plikami chronionymi za pomocą usługi Zarządzanie prawami do informacji (IRM) pakietu Office

-   Pełne współdziałanie z plikami PDF chronionymi przy użyciu programu SharePoint, infrastruktury FCI i obsługiwanych narzędzi do tworzenia plików PDF

Aplikacja do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management używa nowego [środowiska uruchomieniowego programu AD RMS Client 2.1](http://www.microsoft.com/download/details.aspx?id=38396). Oferuje ono użytkownikom możliwość ochrony zawartości przy użyciu wstępnie zdefiniowanych lub zdefiniowanych przez użytkownika szablonów, które można dostosowywać i wdrażać dla organizacji. Korzystając z funkcji usług AD RMS 2.1, aplikacja do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management oferuje użytkownikom końcowym proste środowisko ochrony i środowisko użytkowe.

Od wersji usług AD RMS systemu Windows Azure z października 2013 r. możesz chronić dokumenty w sposób natywny za pomocą pakietu Office 2010 i wysyłać je do osób w innej firmie, które będą mogły ich używać za pomocą usług AD RMS systemu Windows Azure. Ponadto w tej wersji, jeśli używasz trybu kryptograficznego 2 usług AD RMS, możesz korzystać z usług RMS dla użytkowników indywidualnych i używać zawartości od osób z innej firmy, w której są używane usługi AD RMS systemu Windows Azure. Aby uzyskać więcej informacji o trybie kryptograficznym 2, zobacz [Tryby kryptograficzne usług AD RMS](http://technet.microsoft.com/library/hh867439%28v=ws.10%29.aspx).

Aby pobrać aplikację do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management, wykonaj następujące czynności:

1.  Zaloguj się w witrynie [Microsoft Connect](http://connect.microsoft.com/) za pomocą swojego konta Microsoft (znanego wcześniej jako identyfikator Live ID).

2.  Na stronie **stronie głównej** wyszukaj produkt **Rights Management Services** i dołącz do tej grupy.

3.  Kliknij pozycję **Pliki do pobrania**, a następnie kliknij pozycję **Aplikacja do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management**.

4.  Na stronie **Szczegóły pobierania** wybierz plik **Microsoft Rights Management sharing application.zip** i kliknij przycisk **Pobierz**.

5.  W razie potrzeby zainstaluj program Microsoft File Transfer Manager i wykonaj czynności potrzebne do pobrania aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management.

#### Poziomy ochrony obsługiwane przez aplikację do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management
Aplikacja do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management obsługuje ochronę na dwóch różnych poziomach, co opisano w poniższej tabeli.

||||
|-|-|-|
|Typ ochrony|Natywna|Ogólna|
|Opis|W przypadku plików tekstowych, obrazów, plików pakietu Microsoft Office (Word, Excel, PowerPoint), plików pdf oraz innych typów plików aplikacji obsługujących usługi AD RMS ochrona natywna zapewnia silny poziom ochrony obejmujący szyfrowanie i wymuszanie praw (uprawnień).|W przypadku pozostałych aplikacji i typów plików ochrona ogólna zapewnia poziom ochrony obejmujący hermetyzację plików z wykorzystaniem typu pliku pfile oraz uwierzytelnianie umożliwiające weryfikację, czy użytkownik jest autoryzowany do otwierania pliku.|
|Ochrona|Pliki są w pełni szyfrowane, a ochrona jest wymuszana w następujący sposób:<br /><br />-   Przed wyświetleniem chronionej zawartości musi nastąpić pomyślne uwierzytelnienie użytkowników odbierających plik pocztą e-mail lub mających dostęp do niego za pośrednictwem uprawnień do pliku lub uprawnień udziału.<br />-   Ponadto wymuszane są prawa użytkowania i zasady ustawiane przez właściciela zawartości, gdy zawartość jest wyświetlana w aplikacji IP Viewer (dla chronionych plików tekstowych i obrazów) lub w skojarzonej aplikacji (dla pozostałych obsługiwanych typów plików).|Ochrona plików jest wymuszana w następujący sposób:<br /><br />-   Przed wyświetleniem chronionej zawartości musi nastąpić pomyślne uwierzytelnienie użytkowników autoryzowanych do otwierania pliku i mających do niego dostęp. W przypadku niepowodzenia autoryzacji plik nie jest otwierany.<br />-   Prawa do użytkowania i zasady ustawiane przez właściciela zawartości są wyświetlane, aby informować autoryzowanych użytkowników o przewidywanych zasadach użytkowania.<br />-   Rejestrowanie inspekcji autoryzowanych użytkowników otwierających pliki i uzyskujących do nich dostęp jest przeprowadzane, jednak żadne prawa do użytkowania nie są wymuszane przez aplikacje, które tego nie obsługują.|
|Domyślny dla typów plików|Jest to domyślny poziom ochrony dla następujących typów plików:<br /><br />-   Pliki tekstowe i pliki obrazów<br />-   Pliki pakietu Microsoft Office (Word, Excel, PowerPoint)<br />-   Portable Document Format (pdf)<br /><br />Aby uzyskać więcej informacji, zobacz „Obsługiwane typy plików”.|Jest to domyślna ochrona dla wszystkich pozostałych typów plików (takich jak vsdx, rtf itd.), które nie są obsługiwane w ramach pełnej ochrony.|

### <a name="BKMK_SupportFileTypes"></a>Obsługiwane typy plików
Poniższa tabela zawiera listę typów plików, które są obsługiwane przez aplikację do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management.

|Rozszerzenie pliku|Opis|Oryginalne rozszerzenie pliku|
|----------------------|--------|---------------------------------|
|ptxt|Chroniony plik tekstowy|txt|
|pxml|Chroniony plik XML|xml|
|pjpg|Chroniony plik obrazu JPG|jpg|
|pjpeg|Chroniony plik obrazu JPEG|jpeg|
|ppng|Chroniony plik obrazu PNG|png|
|ptiff|Chroniony plik obrazu TIFF|tiff|
|pbmp|Chroniony plik mapy bitowej systemu Windows|bmp|
|pgif|Chroniony plik obrazu GIF|gif|
|pgiff|Chroniony plik obrazu GIFF|giff|
|pjpe|Chroniony plik obrazu JPE|jpe|
|pjfif|Chroniony plik obrazu JFIF|jfif|
|pjif|Chroniony plik obrazu JIF|jif|
Poniższa tabela zawiera listę typów plików, które są obsługiwane przez pakiety Microsoft Office 2013, Office 2010 i Office 2007. Istnieją dwa typy funkcji ochrony: MsoIrmProtector i OpcIrmProtector. Aby uzyskać więcej informacji o tych typach funkcji ochrony, zobacz [Funkcje ochrony formatów plików pakietu Microsoft Office](http://archive.msdn.microsoft.com/OfficeProtectors).

|||
|-|-|
|Funkcja MsoIrmProtector obsługuje następujące typy plików:<br /><br />-   doc<br />-   dot<br />-   xla<br />-   xls<br />-   xlt<br />-   pps<br />-   ppt|Funkcja OpcIrmProtector obsługuje następujące typy plików:<br /><br />-   docm<br />-   docx<br />-   dotm<br />-   dotx<br />-   xlam<br />-   xlsb<br />-   xlsm<br />-   xlsx<br />-   xltm<br />-   xltx<br />-   xps<br />-   potm<br />-   potx<br />-   ppsx<br />-   ppsm<br />-   pptm<br />-   pptx<br />-   thmx|

### <a name="BKMK_ScriptedInstall"></a>Automatyczne wdrażanie aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management
Wersja aplikacji RMS sharing obsługuje instalację skryptową, dzięki czemu ta aplikacja nadaje się do wdrożeń w przedsiębiorstwie.

##### Aby pobrać aplikację RMS sharing do automatycznego wdrożenia

1.  Przejdź do strony [Aplikacja do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management dla systemu Windows](http://www.microsoft.com/en-us/download/details.aspx?id=40857) w Centrum pobierania Microsoft, a następnie kliknij przycisk **Pobierz**.

2.  Wybierz i pobierz potrzebne pliki. Istnieją dwa pakiety instalacyjne klienta: jeden dla 64-bitowej wersji systemu Windows (Microsoft Rights Management sharing application x64.zip) i drugi dla 32-bitowej wersji systemu Windows (Microsoft Rights Management sharing application x86.zip).

3.  Wypakuj pliki ze skompresowanych pakietów instalacyjnych, na przykład klikając je dwukrotnie. Następnie skopiuj wypakowane pliki do lokalizacji sieciowej, która jest dostępna dla komputerów klienckich.

Pakiety instalacyjne aplikacji RMS sharing obsługują różne scenariusze wdrażania i zawierają następujące składniki:

|Opis|Scenariusz wdrażania|
|--------|------------------------|
|Asystent logowania usługi online firmy Microsoft|Wymagany dla następującego oprogramowania:<br /><br />-   Pakiet Office 2010 i usługi Windows Azure RMS|
|Poprawka dla pakietu Office (KB 2596501)|Wymagany dla następującego oprogramowania:<br /><br />-   Pakiet Office 2010 i usługi Windows Azure RMS|
|Poprawka dla trybu kryptograficznego 2 (KB 2627273)|Wymagany dla następującego oprogramowania:<br /><br />-   Pakiet Office 2010 i usługi Windows Azure RMS|
|Klient usług AD RMS i aplikacja RMS sharing|Wymagany dla następującego oprogramowania:<br /><br />-   Pakiet Office 2013 i usługi Windows Azure RMS<br />-   Pakiet Office 2010 i usługi Windows Azure RMS<br />-   Pakiet Office 2013 i usługi Active Directory RMS<br />-   Pakiet Office 2010 i usługi Active Directory RMS<br />-   Uaktualnianie aplikacji RMS sharing|
|Dodatek dla wstążki pakietu Office|Wymagany dla następującego oprogramowania:<br /><br />-   Pakiet Office 2013 i usługi Windows Azure RMS<br />-   Pakiet Office 2013 i usługi Active Directory RMS<br />-   Pakiet Office 2010 i usługi Active Directory RMS<br />-   Uaktualnianie aplikacji RMS sharing|
|Narzędzie przygotowywania usługi Windows Active Directory Rights Management|Wymagany dla następującego oprogramowania:<br /><br />-   Pakiet Office 2010 i usługi Windows Azure RMS|
> [!NOTE]
> W przypadku scenariusza **Pakiet Office 2010 i usługi Windows Azure RMS** możesz już używać usług Windows Azure RMS lub Active Directory RMS, ale może dojść do sytuacji, w której zechcesz bezpiecznie wysyłać dokumenty do osób z innych firm, które używają usług Windows Azure RMS.
> 
> Po zainstalowaniu i uruchomieniu narzędzia przygotowywania usługi Windows Active Directory Rights Management do obsługi pakietu Office 2010 to narzędzie wykonuje dwie czynności:
> 
> -   Edytuje rejestr w celu obsługi aplikacji RMS sharing.
> -   „Uruchamia” użytkownika, co oznacza, że komputer kontaktuje się z serwerem usług AD RMS lub usługami Windows Azure RMS i uzyskuje certyfikaty potrzebne dla komputera i użytkownika do korzystania z usług RMS.

Poniższe procedury umożliwiają zidentyfikowanie poleceń wymaganych do wdrożenia aplikacji RMS sharing dotyczących następujących scenariuszy wdrażania:

-   Pakiet Office 2013 i usługi Windows Azure RMS

-   Pakiet Office 2010 i usługi Windows Azure RMS

-   Pakiet Office 2013 lub Office 2010 i usługi Active Directory RMS

-   Uaktualnianie aplikacji RMS sharing

Na potrzeby przykładów w poleceniach przyjęto założenie, że pobrane i wypakowane pliki zostały skopiowane do udziału sieciowego dostępnego dla komputerów klienckich za pośrednictwem ścieżki **\\server5\apps\rms** oraz że na komputerach klienckich istnieje już folder o nazwie **C:\Log files**, w którym są przechowywane pliki dzienników instalacji. Dla każdej instalacji należy wybrać nazwę pliku dziennika instalacji, który musi mieć rozszerzenie log.

> [!IMPORTANT]
> Przed wdrożeniem aplikacji RMS sharing należy spakować wymagane polecenia w tych procedurach, tak aby mogły one zostać użyte do instalacji w kontekście komputera dla wszystkich użytkowników i z zastosowaniem uprawnień administratora lokalnego. Pakiet będzie mógł następnie zostać wdrożony na komputerach za pomocą standardowego mechanizmu wdrażania aplikacji, takiego jak zasady grupy lub program System Center Configuration Manager.
> 
> Wyjątek stanowi narzędzie przygotowywania usługi Windows Azure Active Directory Rights Management: Musi ono zostać uruchomione jednokrotnie dla każdego użytkownika na komputerze, a jego uruchomienie musi zostać przeprowadzone z podniesionymi uprawnieniami w celu pomyślnej edycji rejestru. Można to osiągnąć różnymi metodami, w tym prosząc użytkowników o uruchomienie polecenia (na przykład przez kliknięcie linku w wiadomości e-mail lub w portalu pomocy technicznej) lub dodając polecenie do skryptu logowania każdego użytkownika. Jeśli nie można użyć polecenia „uruchom jako” (runas), ponieważ użytkownicy nie mają konta administratora lokalnego, istnieją narzędzia wdrażania, które mogą automatycznie podnieść poziom uprawnień dla polecenia zgodnie z określonymi zasadami.

##### Aby wdrożyć aplikację RMS sharing dla pakietu Office 2013 i usług Windows Azure RMS

1.  Zainstaluj klienta usług AD RMS oraz aplikację RMS sharing przy użyciu następujących poleceń:

    -   W przypadku 64-bitowego systemu Windows: x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "&lt;ścieżka i nazwa pliku dziennika&gt;"

        ```
        x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    -   W przypadku 32-bitowego systemu Windows:

        ```
        X86\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    Przykład: `\\server5\apps\rms\x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "C:\Log files\ipviewerinstall.log"`

2.  Zainstaluj dodatek dla pakietu Office przy użyciu następujących poleceń:

    -   W przypadku 64-bitowej wersji pakietu Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "<log file path and name>"
        ```

    -   W przypadku 32-bitowej wersji pakietu Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x86\Setup.msi" /L*v "<log file path and name>"
        ```

    > [!NOTE]
    > Aby ukończyć instalację, należy ponownie uruchomić komputer. Możesz zainicjować automatyczne ponowne uruchomienie przy użyciu polecenia takiego jak shutdown /i.

    Przykład: `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "C:\Log files\rmsoffice.log"`

##### Aby wdrożyć aplikację RMS sharing dla pakietu Office 2010 i usług Windows Azure RMS

1.  Zainstaluj asystenta logowania usługi online firmy Microsoft przy użyciu następujących poleceń:

    -   W przypadku 64-bitowego systemu Windows:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\msoidcli_64bit.msi" /L*v "<log file path and name >"
        ```

    -   W przypadku 32-bitowego systemu Windows:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\msoidcli_64bit.msi" /L*v "<log file path and name>"
        ```

    Przykład: `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\msoidcli_64bit.msi" /L*v "C:\Log files\assistant.log"`

2.  Zainstaluj poprawkę dla pakietu Office przy użyciu następujących poleceń:

    -   W przypadku 64-bitowej wersji pakietu Office:

        ```
        x64\office2010-kb2596501-fullfile-x64-glb.exe /norestart /quiet /log:"<log file path and name >"
        ```

    -   W przypadku 32-bitowej wersji pakietu Office:

        ```
        x86\office2010-kb2596501-fullfile-x86-glb.exe /norestart /quiet /log:"<log file path and name>"
        ```

    Przykład: `\\server5\apps\rms\x64\office2010-kb2596501-fullfile-x64-glb.exe /norestart /quiet /log:"C:\Log files\kb2596501install.log"`

3.  Zainstaluj poprawkę trybu kryptograficznego 2 przy użyciu następujących poleceń:

    -   W przypadku 64-bitowego systemu Windows:

        ```
        wusa.exe /norestart /quiet "x64\Windows6.1-KB2627273-v4-x64.msu" /log:"<log file path and name >"
        ```

    -   W przypadku 32-bitowego systemu Windows:

        ```
        wusa.exe /norestart /quiet "x86\Windows6.1-KB2627273-v4-x86.msu" /log:"<log file path and name>"
        ```

    Przykład: `\\server5\apps\rms\wusa.exe /norestart /quiet "x64\Windows6.1-KB2627273-v4-x64.msu" /log:"C:\Log files\kb267273.log"`

4.  Zainstaluj klienta usług AD RMS oraz aplikację RMS sharing przy użyciu następującego polecenia:

    -   W przypadku 64-bitowego systemu Windows:

        ```
        x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name >"
        ```

    -   W przypadku 32-bitowego systemu Windows:

        ```
        X86\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    Przykład: `\\server5\apps\rms\x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "C:\Log files\ipviewerinstall.log"`

5.  Zainstaluj dodatek dla pakietu Office przy użyciu następujących poleceń:

    -   W przypadku 64-bitowej wersji pakietu Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "<log file path and name>"
        ```

    -   W przypadku 32-bitowej wersji pakietu Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x86\Setup.msi" /L*v "<log file path and name>"
        ```

    > [!NOTE]
    > Aby ukończyć instalację, należy ponownie uruchomić komputer. Możesz zainicjować automatyczne ponowne uruchomienie przy użyciu polecenia takiego jak shutdown /i.

    Przykład: `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "C:\Log files\rmsoffice.log"`

6.  Zainstaluj narzędzie przygotowywania usługi Windows Active Directory Rights Management, dodając następujące polecenie do skryptów logowania:

    > [!IMPORTANT]
    > Aby uruchomić to polecenie pomyślnie, użytkownicy muszą mieć uprawnienia administratora lokalnego.

    -   W przypadku 64-bitowego systemu Windows 8:

        ```
        x64\aadrmprep.exe /initiateMe /logfile "<log file path and name>"
        ```

    -   W przypadku 32-bitowego systemu Windows 8:

        ```
        X86\aadrmprep.exe /initiateMe /logfile "<log file path and name>"
        ```

    -   W przypadku 64-bitowego systemu Windows 7:

        ```
        x64\win7\aadrmprep.exe /initiateMe /logfile "<log file path and name>"
        ```

    -   W przypadku 32-bitowego systemu Windows 7:

        ```
        X86\win7\aadrmprep.exe /initiateMe /logfile "<log file path and name>"
        ```

    > [!NOTE]
    > To polecenie może monitować użytkownika o wprowadzenie jego poświadczeń systemu Windows Azure. Jeśli komputer nie będzie przyłączony do domeny, użytkownik będzie monitowany. Jeśli komputer będzie przyłączony do domeny, narzędzie może użyć buforowanych poświadczeń.

    Przykład: `\\server5\apps\rms\x64\aadrmprep.exe /initiateMe /logfile "C:\Log files\aadrmprepinstall.log"`

##### Aby wdrożyć aplikację RMS sharing dla pakietu Office 2013 lub Office 2010 i usług Active Directory RMS

1.  Zainstaluj klienta usług AD RMS oraz aplikację RMS sharing przy użyciu następujących poleceń:

    -   W przypadku 64-bitowego systemu Windows:

        ```
        x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    -   W przypadku 32-bitowego systemu Windows:

        ```
        X86\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    Przykład: `\\server5\apps\rms\x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "C:\Log files\ipviewerinstall.log"`

2.  Zainstaluj dodatek dla pakietu Office przy użyciu następujących poleceń:

    -   W przypadku 64-bitowej wersji pakietu Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "<log file path and name>"
        ```

    -   W przypadku 32-bitowej wersji pakietu Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x86\Setup.msi" /L*v "<log file path and name>"
        ```

    > [!NOTE]
    > Aby ukończyć instalację, należy ponownie uruchomić komputer. Możesz zainicjować automatyczne ponowne uruchomienie przy użyciu polecenia takiego jak shutdown /i.

    Przykład: `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "C:\Log files\rmsofficeinstall.log"`

##### Aby uaktualnić aplikację RMS sharing

1.  Zainstaluj klienta usług AD RMS oraz aplikację RMS sharing przy użyciu następującego polecenia:

    -   W przypadku 64-bitowego systemu Windows:

        ```
        x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    -   W przypadku 32-bitowego systemu Windows:

        ```
        X86\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    Przykład: `\\server5\apps\rms\x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "C:\Log files\ipviewerinstall.log"`

2.  Zainstaluj dodatek dla pakietu Office przy użyciu następujących poleceń:

    -   W przypadku 64-bitowej wersji pakietu Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "<log file path and name>"
        ```

    -   W przypadku 32-bitowej wersji pakietu Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x86\Setup.msi" /L*v "<log file path and name>"
        ```

    > [!NOTE]
    > Aby ukończyć instalację, należy ponownie uruchomić komputer. Możesz zainicjować automatyczne ponowne uruchomienie przy użyciu polecenia takiego jak shutdown /i.

    Przykład: `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "C:\Log files\rmsofficeinstall.log"`

#### <a name="BKMK_verifyscripted"></a>Sprawdzanie, czy instalacja przebiegła pomyślnie
Korzystając z plików dzienników instalacji, możesz sprawdzić, czy instalacja przebiegła pomyślnie.

###### Aby zweryfikować powodzenie instalacji asystenta logowania usługi online firmy Microsoft

-   Aby zweryfikować powodzenie, wyszukaj następujący tekst w pliku dziennika instalacji: **Stan powodzenia lub błędu instalacji: 0**

    Przykładowe wiersze z pomyślnej instalacji:

    **MSI (s) (9C:88) [18:49:04:007]: Produkt: Microsoft RMS Office Addins — Instalacja została ukończona pomyślnie.**

    **MSI (s) (9C:88) [18:49:04:007]: Instalator Windows zainstalował produkt. Nazwa produktu: Microsoft RMS Office Addins. Wersja produktu: 1.0.7. Język produktu: 1045. Producent: Microsoft. Stan powodzenia lub błędu instalacji: 0.**

###### Aby zweryfikować powodzenie instalacji poprawki dla pakietu Office

-   Aby zweryfikować powodzenie, wyszukaj jeden z poniższych ciągów tekstowych w pliku dziennika instalacji:

    -   W przypadku 64-bitowej wersji pakietu Office:

        -   **office2010-kb2596501-fullfile-x64-glb.exe exited with status SUCCESS (program office2010-kb2596501-fullfile-x64-glb.exe zakończył działanie ze stanem POWODZENIE)**

        -   **office2010-kb2596501-fullfile-x64-glb.exe exited with status NOTAPPLICABLE (program office2010-kb2596501-fullfile-x64-glb.exe zakończył działanie ze stanem NIE DOTYCZY)**

    -   W przypadku 32-bitowej wersji pakietu Office:

        -   **office2010-kb2596501-fullfile-x86-glb.exe exited with status SUCCESS (program office2010-kb2596501-fullfile-x86-glb.exe zakończył działanie ze stanem POWODZENIE)**

        -   **office2010-kb2596501-fullfile-x86-glb.exe exited with status NOTAPPLICABLE (program office2010-kb2596501-fullfile-x86-glb.exe zakończył działanie ze stanem NIE DOTYCZY)**

###### Aby zweryfikować powodzenie instalacji poprawki dla trybu kryptograficznego 2

-   Aby zweryfikować powodzenie, wyszukaj jeden z poniższych ciągów tekstowych w pliku dziennika instalacji:

    -   W przypadku 64-bitowego systemu Windows:

        -   **Windows6.1-KB2627273-v4-x64.msu exited with status SUCCESS (program Windows6.1-KB2627273-v4-x64.msu zakończył działanie ze stanem POWODZENIE)**

        -   **Windows6.1-KB2627273-v4-x64.msu exited with status NOTAPPLICABLE (program Windows6.1-KB2627273-v4-x64.msu zakończył działanie ze stanem NIE DOTYCZY)**

    -   W przypadku 32-bitowego systemu Windows:

        -   **Windows6.1-KB2627273-v4-x86.msu exited with status SUCCESS (program Windows6.1-KB2627273-v4-x86.msu zakończył działanie ze stanem POWODZENIE)**

        -   **Windows6.1-KB2627273-v4-x86.msu exited with status NOTAPPLICABLE (program Windows6.1-KB2627273-v4-x86.msu zakończył działanie ze stanem NIE DOTYCZY)**

###### Aby zweryfikować powodzenie instalacji klienta usług AD RMS i aplikacji RMS sharing

-   Aby zweryfikować powodzenie, wyszukaj następujący tekst w pliku dziennika instalacji: **Stan powodzenia lub błędu instalacji: 0**

    Przykładowe wiersze z pomyślnej instalacji:

    **MSI (s) (F0:B8) [14:19:57:854]: Produkt: Active Directory Rights Management Services Client 2.1 — Instalacja została ukończona pomyślnie.**

    **MSI (s) (F0:B8) [14:19:57:854]: Instalator Windows zainstalował produkt. Nazwa produktu: Active Directory Rights Management Services Client 2.1. Wersja produktu: 1.0.1179.1. Język produktu: 1045. Producent: Microsoft Corporation. Stan powodzenia lub błędu instalacji: 0.**

###### Aby zweryfikować powodzenie instalacji dodatku dla pakietu Office

-   Aby zweryfikować powodzenie, wyszukaj następujący tekst w pliku dziennika instalacji: **Stan powodzenia lub błędu instalacji: 0**

    Przykładowe wiersze z pomyślnej instalacji:

    **MSI (s) (9C:88) [18:49:04:007]: Produkt: Microsoft RMS Office Addins — Instalacja została ukończona pomyślnie.**

    **MSI (s) (9C:88) [18:49:04:007]: Instalator Windows zainstalował produkt. Nazwa produktu: Microsoft RMS Office Addins. Wersja produktu: 1.0.7. Język produktu: 1045. Producent: Microsoft. Stan powodzenia lub błędu instalacji: 0.**

###### Aby zweryfikować powodzenie instalacji narzędzia przygotowywania usługi Windows Azure Active Directory Rights Management

-   Aby zweryfikować powodzenie, wyszukaj następujący tekst w pliku dziennika instalacji: **aadrmprep.exe exited with status SUCCESS (program aadrmprep.exe zakończył działanie ze stanem POWODZENIE)**

    > [!NOTE]
    > Czasami ta instalacja może zostać uruchomiona dwukrotnie — pierwsze wystąpienie nie powiedzie się, natomiast drugie zakończy się pomyślnie.

Zmiany w rejestrze wprowadzone przez to narzędzie, które można sprawdzić ręcznie, są następujące:

-   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\Federation]

    "FederationHomeRealm"="urn:HostedRmsOnlineService:Certification"

-   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\Federation]

    "FederationHomeRealm"="urn:HostedRmsOnlineService:Certification"

-   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation]

    @="&lt;adres URL certyfikacji&gt;"

-   [HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\14.0\Common\DRM]

    DefaultUser="&lt;użytkownik_domyślny&gt;"

#### <a name="BKMK_uninstallscripted"></a>Polecenia dezinstalacji
Nie wszystkie polecenia instalacji wymagane przez te wdrożenia obsługują polecenie dezinstalacji. Możliwa jest dezinstalacja klienta usług AD RMS, aplikacji do udostępniania i dodatku dla pakietu Office. Te elementy można odinstalować za pomocą poniższych poleceń.

###### Aby odinstalować klienta usług AD RMS i aplikację RMS sharing

-   Użyj następujących poleceń:

    -   W przypadku 64-bitowego systemu Windows:

        ```
        x64\setup_ipviewer.exe /uninstall /quiet
        ```

    -   W przypadku 32-bitowego systemu Windows:

        ```
        x86\setup_ipviewer.exe /uninstall /quiet
        ```

###### Aby odinstalować dodatek dla pakietu Office

-   Użyj następujących poleceń:

    -   W przypadku 64-bitowej wersji pakietu Office:

        ```
        msiexec /x \x64\Setup[64].msi /quiet
        ```

    -   W przypadku 32-bitowej wersji pakietu Office:

        ```
        msiexec /x \x86\Setup.msi /quiet
        ```

## Zobacz też
[Pobieranie aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management (http://go.microsoft.com/fwlink/?LinkId=303970)](http://go.microsoft.com/fwlink/?LinkId=303970)
 [Często zadawane pytania dotyczące aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management dla systemu Windows](http://go.microsoft.com/fwlink/?LinkId=303971)

