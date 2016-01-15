---
description: na
keywords: na
title: Dialog box options for the Rights Management sharing application
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b91ab30-6363-4929-bcbd-4dfbd05f644a
---
# Opcje okna dialogowego Rights Management udostępnianie aplikacji
Te informacje służą do pomaga określić opcje RMS sharing aplikacji **Dodaj ochronę** okno dialogowe lub **Udostępnij chronione** okno dialogowe. Pojawi się w tym oknie dialogowym wpisz, gdy użytkownik [chronić pliku do udostępniania](http://technet.microsoft.com/library/dn574735.aspx) lub [ochronę plików w miejscu](http://technet.microsoft.com/library/dn574733.aspx) i wybierz uprawnienia niestandardowe.

> [!IMPORTANT]
> Jeśli opcje widoczne są inne niż zabezpieczenia opisanych tutaj, prawdopodobnie nie masz najnowszą wersję programu udostępniania zainstalowania aplikacji. Możesz pobrać najnowszą wersję z [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) strony.
> 
> Skąd możesz wiedzieć, jeśli jest zainstalowana najnowsza wersja? Poszukaj **Microsoft Rights Management aplikacji do udostępniania** się na liście programy i funkcje i zaznacz odpowiedni numer wersji. Aby sprawdzić, a następnie użyć opcji w tabeli, wersja powinien być uruchomiony co najmniej **1.0.1770.0**. Można sprawdzić najnowsze numer wersji na stronie pobierania.

Oprócz opcje, które można wybrać użytkownik może również być zastanawiasz się:

-   [Co to jest plik .ppdf, który jest tworzony automatycznie?](../Topic/Dialog_box_options_for_the_Rights_Management_sharing_application.md#BKMK_PPDF)

-   [Co to jest różnica między ogólnego ochrony i wbudowane ochrony (w trybie macierzystym)?](../Topic/Dialog_box_options_for_the_Rights_Management_sharing_application.md#BKMK_GenericNative)

|Opcja|Opis|
|---------|--------|
|**UŻYTKOWNICY**|Jeśli jeszcze nie zostało już określony adres e-mail z programu Outlook, wprowadź adresy e-mail osób, które chcesz, aby można było otworzyć pliku.<br /><br />Jeśli organizacja korzysta z wersją lokalnie Rights Management (AD RMS), adresy e-mail, które można określić jest ograniczony do użytkowników w ramach danej organizacji. Gdy ma to zastosowanie i spróbuj określić adres e-mail zewnętrznych, zostanie wyświetlony komunikat z informacją, że konfiguracja firmy pozwala na udostępnianie chronionej zawartości wyłącznie w obrębie firmy. Jednak używana Azure RMS w organizacji, te adresy e-mail może być dla osób w ramach danej organizacji lub dla osób w innej organizacji.<br /><br />Na przykład: janetm@contoso.com; p.dover@Fabrikam.com|
|**Ogólny ochrony**|Jeśli ta opcja jest zaznaczona, oznacza to, że wybranego pliku nie można chronić sposób macierzysty. Aby uzyskać więcej informacji zobacz. [Co to jest różnica między ogólnego ochrony i wbudowane ochrony (w trybie macierzystym)?](../Topic/Dialog_box_options_for_the_Rights_Management_sharing_application.md#BKMK_GenericNative) w tym temacie.|
|**Podgląd — tylko w widoku**<br /><br />**Osoba dokonująca przeglądu — umożliwia wyświetlanie i edytowanie**<br /><br />**Edycja Współautor — widok, kopiowania i drukowania**<br /><br />**Właściciel współpracy — wszystkie uprawnienia** **Note:** Te opcje pojawienie się ikony zwrotnego przed nazwą, które zawierają globalny. Ta ikona służy ponieważ zwykle wybraniu jednej z tych opcji wysyłania załącznika ktoś w innej organizacji.|Wybierz jedną z poniższych opcji, aby zdefiniować prawa ochrony dokumentu. Kliknij przycisk każdej opcji, aby wyświetlić opis.<br /><br />Po wybraniu jednej z poniższych opcji tylko osoby określonej w **użytkowników** mieć praw Określ a przy użyciu dokumentu. Na przykład jeśli ich przekazywać je do innej osobie, dokumentu nie otwiera.|
|Szablony zasad, które służy do konfigurowania administratora.<br /><br />Na przykład, jeśli nazwa firmy jest Contoso, Ltd.: **Contoso, Ltd. - tylko poufne widoku** **Note:** Te opcje pojawienie się ikony kwadratowy przed nazwą, które reprezentują statystycznej. Ta ikona jest używana, ponieważ zwykle można wybrać jedną z następujących opcji podczas wysyłania załącznika osób w Twojej organizacji.|Po udostępnieniu dokumentu z osób, które działają dla organizacji, możesz zobaczyć szablonów dostępnych zasad, które służy do konfigurowania administratorem. Dokument nie powinien być udostępniany spoza swojej organizacji, należy wybrać jedną z tych.<br /><br />Po wybraniu jednej z poniższych opcji, administrator definiuje praw do dokumentu i który go otworzyć.|
|**Wygasa te dokumenty**|Wybierz tę opcję tylko w przypadku plików zależne od czasu, które wybranych użytkowników nie może być otwarcie po Data, który określisz. Nadal będzie można otwierać oryginalny plik, ale po północ (strefę czasową), w dniu, który określisz innym osobom nie będzie można otworzyć pliku.<br /><br />Ta opcja jest niedostępna, w przypadku wybrania szablonu zasad, który konfiguruje się z administratorem.|
|**Wyślij wiadomość e-mail, gdy ktoś spróbuje otworzyć te dokumenty**|**Note:** Ta opcja jest obecnie w podglądzie.<br />Wybierz tę opcję, jeśli chcesz otrzymywać powiadomienia e-mail zawsze, gdy ktoś spróbuje otworzyć dokument, który jest ochronę. Wiadomości e-mail będzie napisane, który próbowano otworzyć, czy i kiedy one zostały pomyślnie.<br /><br />Ta opcja jest dostępna tylko wtedy, gdy Twoja organizacja korzysta Azure RMS. Twoja organizacja korzysta z wersją lokalnie Rights Management (AD RMS), będzie mógł przeglądać tę opcję.|
|**Nie zezwala na natychmiast odwołać dostęp do tych dokumentów**|Wybierz tę opcję, jeśli konieczne może być później odwołać dostęp do dokumentów przy użyciu śledzenia witryny dokumentów i odwołania wymaga od razu zaczęły obowiązywać. Ustawienie tej opcji oznacza, że podczas dokumentu nie został odwołany, użytkownicy zawsze muszą jednak połączenie internetowe do odczytu dokumentu, zawsze im dostęp. Może to być Niektóre scenariusze, w którym użytkownicy nie może połączyć swoje urządzenie z Internetem, a użytkownicy nie można odczytać dokumentu poprawnie.<br /><br />Jeśli ta opcja nie jest wybrana, które można odwołać dokumenty, za pomocą witryny śledzenia dokumentu. Jednak ponieważ użytkownicy nie zawsze muszą połączenie internetowe do odczytu dokumentu, nie wiedzą, od razu że dokument został odwołany i mogą w dalszym ciągu ją czytać, aż do następnego uwierzytelniania z Azure RMS. Domyślnie maksymalną liczbę dni, które ktoś może w dalszym ciągu odczytu chroniony dokument, który został odwołany to 30 dni, ale administrator może zmienić tę wartość z wynosić co najmniej mniej niż 30 dni.<br /><br />Ta opcja jest dostępna tylko wtedy, gdy Twoja organizacja korzysta Azure RMS. Twoja organizacja korzysta z wersją lokalnie Rights Management (AD RMS), będzie mógł przeglądać tę opcję.|

## <a name="BKMK_GenericNative"></a>Co to jest różnica między ogólnego ochrony i wbudowane ochrony (w trybie macierzystym)?

-   Gdy użytkownik **ogólnego chronić pliku**, osoby nieupoważnione nie można otworzyć pliku. Ale po autoryzowanych osób otwierania tego pliku, można następnie przesyła je bez ochrony dla innych osób lub zapisać go w lokalizacji, którą inni mogą uzyskać dostęp do. Jednak użytkownicy widzą komunikat, który informuje je o tym, jakie ich uprawnień do tego pliku, i zażądano przestrzegać tych, ale nie można wymusić tej ochrony. Ponadto jeśli ogólnego chroniony plik, nie mogą ograniczać uprawnienia więcej niż autoryzacji. Na przykład nie mogą ograniczać zawartości do tylko do odczytu lub nie są drukowane.:

    > [!NOTE]
    > Ogólnie chronionych plików zawsze ma rozszerzenie nazwy pliku z **pfile**.

-   W porównaniu, gdy użytkownik korzysta z **Wbudowana ochrona (w trybie macierzystym)** zarządzania prawami z aplikacji obsługujących tę (na przykład pliki pakietu Office), ochrona ma zastosowanie do pliku, nawet jeśli plik jest następnie wysyłane do osób trzecich lub zapisany w innej lokalizacji. Jeśli chroniony tych plików, można skorzystać ograniczone uprawnienia takie jak tylko do odczytu, lub uprawnień do edycji, ale nie wydrukować lub skopiować. Na przykład można wybrać **Viewer — widok tylko**, tak aby zawartość nie może być edytowany, wydrukowania lub skopiowania.

Aby uzyskać dodatkowe informacje techniczne, zobacz [Poziom ochrony — macierzystego i ogólny](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_LevelsofProtection) w sekcji [Przewodnik administratora aplikacji udostępniania zarządzania prawami dostępu](../Topic/Rights_Management_sharing_application_administrator_guide.md).

## <a name="BKMK_PPDF"></a>Co to jest plik .ppdf, który jest tworzony automatycznie?

-   Po udostępnieniu chronionego pliku za pomocą wiadomości e-mail (Udostępnij chronione), RMS sharing aplikacji automatycznie tworzy **.ppdf** wersji pliku Word, Excel, PowerPoint lub PDF. To jest tylko do odczytu wersja chronionego pliku, który można także otworzyć, tylko osoby uwierzytelnione i zapewnia adresatów zawsze odczytywane załącznik, nawet jeśli są one za pomocą urządzenia przenośnego, które nie ma aplikacja, która w sposób macierzysty obsługuje Rights Management. Warunkiem tych osób ma zainstalować aplikację RMS, będzie możliwe odczytanie załącznik.

    W tym scenariuszu, w przeciwieństwie do ogólnego chronionych plików jest wymuszany ograniczenia użycia. Odbiorca nie będzie można zapisać tę wersję pliku, a jeśli przesyłają załącznika do innej osobie oryginalnego ograniczenia znajdują się w dokumencie. Tylko osoby, które zostały upoważnione chronionego dokumentu będzie można go otworzyć.

    > [!NOTE]
    > Plik .ppdf jest tworzony automatycznie, gdy udostępnianie chronionej (udział pocztą e-mail), ale nie jest tworzone po ochrony w miejscu.

## Inne instrukcje i przykłady
Przykłady dla sposobu wykorzystania Rights Management udostępnianie aplikacji i instrukcje dotyczące wykonywania określonych zadań w następujących sekcjach z Podręcznik użytkownika aplikacji udostępniania Rights Management:

-   [Przykłady korzystania z aplikacji do udostępniania RMS](../Topic/Rights_Management_sharing_application_user_guide.md#BKMK_SharingExamples)

-   [Co chcesz zrobić?](../Topic/Rights_Management_sharing_application_user_guide.md#BKMK_SharingInstructions)

## Zobacz też
[Przewodnik użytkownika aplikacji udostępniania zarządzania prawami dostępu](../Topic/Rights_Management_sharing_application_user_guide.md)

