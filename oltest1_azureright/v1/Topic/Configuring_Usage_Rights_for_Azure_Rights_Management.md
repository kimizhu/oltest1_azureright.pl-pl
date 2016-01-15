---
description: na
keywords: na
title: Configuring Usage Rights for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 97ddde38-b91b-42a5-8eb4-3ce6ce15393d
---
# Konfigurowanie praw użytkowania Azure Rights Management
Można ustawić ochrony plików lub wiadomości e-mail przy użyciu Azure Rights Management (usług Azure RMS) i nie używasz szablonu, należy skonfigurować praw użytkowania samodzielnie. Ponadto po skonfigurowaniu niestandardowe szablony dla usług Azure RMS wybierz praw użytkowania, które zostaną następnie automatycznie zastosowane, gdy szablon jest wybierany przez użytkowników, administratorów lub skonfigurowane usługi. Na przykład w portalu Azure można wybrać role, które skonfigurować logiczne grupowanie praw użytkowania, lub można skonfigurować indywidualnych uprawnień.

Użyj w tym temacie ułatwiają konfigurowanie praw użytkowania, dla aplikacji, którego używasz i zrozumieć, jak te uprawnienia są interpretowane przez aplikacje.

## Prawa do użytkowania i opisów
W poniższej tabeli wymieniono i opisano praw użytkowania, które obsługuje Rights Management i jak są używane i interpretowane. W tej tabeli **Nazwa pospolita** jest zwykle, jak można napotkać użycia prawo wyświetlana lub określany jako wersja bardziej przyjazne wartości pojedynczej word, który jest używany w kodzie ( **kodowania w zasadach** wartości).**API stała lub wartość** to nazwa zestawu SDK wywołanie interfejsu API MSIPC używane podczas pisania aplikacji obsługujących usługę RMS, która sprawdza, czy użycie prawo lub dodaje użycia prawo do zasad.

|Nazwa pospolita|Kodowanie w zasadach|Opis|Implementacja w prawa niestandardowego pakietu Office|Nazwa w portalu Azure|Nazwa w szablonach usług AD RMS|Interfejs API stała lub wartość|Dodatkowe informacje|
|-------------------|------------------------|--------|---------------------------------------------------------|-------------------------|-----------------------------------|-----------------------------------|------------------------|
|Edytuj zawartość, Edycja|DOCEDIT|Zezwala użytkownikowi na modyfikowanie, rozmieszczanie, formatowania lub filtrować zawartość wewnątrz aplikacji. Nie uzyskuje prawo do zapisywania edytowanym kopii.|W ramach **zmiany** i **Pełna kontrola** opcje.|**Edytowanie zawartości**|**Edytuj**|Nie dotyczy|W aplikacjach pakietu Office to uprawnienie umożliwia użytkownikowi zapisanie dokumentu.|
|Zapisz|EDYTUJ|Umożliwia użytkownikowi zapisanie dokumentu w jego bieżącej lokalizacji.|W ramach **zmiany** i **Pełna kontrola** opcje.|**Zapisz plik**|**Zapisz**|IPC_GENERIC_WRITEL "EDYTUJ"|W aplikacjach pakietu Office to prawo zezwala użytkownikowi na modyfikowanie dokumentu.|
|Komentarz|KOMENTARZ|Pozwala dodawać adnotacje i komentarze do zawartości.|Nie zaimplementowano.|Nie zaimplementowano.|Nie zaimplementowano.|IPC_GENERIC_COMMENTL "KOMENTARZ"|Te uprawnienia są dostępne w zestawie SDK, jest dostępna jako zasadach ad hoc w module ochrony usług RMS dla środowiska Windows PowerShell i została zaimplementowana w niektórych aplikacjach dostawcy oprogramowania. Jednak nie jest powszechnie używana i nie jest obecnie obsługiwany przez aplikacje pakietu Office.|
|Zapisz jako, eksportowanie|EKSPORTUJ|Włącza opcję zapisać zawartość na inną nazwę pliku (Zapisz jako). W zależności od aplikacji może zapisać pliku bez ochrony.|W ramach **zmiany** i **Pełna kontrola** opcje.|**Eksportowanie zawartości (Zapisz jako)**|**Eksportuj (Zapisz jako)**|IPC_GENERIC_EXPORTL "EKSPORT"|To uprawnienie umożliwia również użytkownika wykonywać inne opcje eksportu w aplikacjach, takie jak **Wyślij do programu OneNote**.|
|Do przodu|DO PRZODU|Włącza opcję do przekazywania wiadomości e-mail i, aby dodać adresatów do **do** i **DW** wierszy.|Odmowa dostępu przy użyciu **nie przekazuj** standardowych zasad.|**Do przodu**|**Do przodu**|IPC_EMAIL_FORWARDL "DO PRZODU"|Nie zezwala na usługi przesyłania dalej przyznać prawa do innych użytkowników w ramach akcji do przodu.|
|Pełna kontrola|WŁAŚCICIEL|Przyznaje wszystkie uprawnienia do dokumentu, a wszystkie dostępne działania mogą być wykonywane.|Jako **Pełna kontrola** opcji niestandardowej.|**Pełna kontrola**|**Pełna kontrola**|IPC_GENERIC_ALLL "WŁAŚCICIEL"|Obejmuje to możliwość usunięcia ochrony.|
|Drukuj|DRUKUJ|Włącza opcje drukować zawartość.|Jako **drukowania zawartości** opcją uprawnień niestandardowych. Nie jest ustawienie dla adresata.|**Drukuj**|**Drukuj**|IPC_GENERIC_PRINTL "DRUKUJ|Brak dodatkowych informacji|
|Odpowiedź|ODPOWIEDŹ|Włącza opcję odpowiedź w kliencie poczty e-mail bez możliwości zmiany w **do** lub **DW** wierszy.|Nie dotyczy|**Odpowiedź**|**Odpowiedź**|IPC_EMAIL_REPLY|Brak dodatkowych informacji|
|Odpowiedz wszystkim|REPLYALL|Umożliwia **Odpowiedz wszystkim** opcję w kliencie poczty e-mail, ale nie zezwala na użytkownika, aby dodać adresatów do **do** lub **DW** wierszy.|Nie dotyczy|**Odpowiedz wszystkim**|**Odpowiedz wszystkim**|IPC_EMAIL_REPLYALLL "REPLYALL"|Brak dodatkowych informacji|
|Widok, Otwórz, Odczyt|WIDOK|Umożliwia użytkownikom otworzyć dokument i sprawdź zawartość.|Jako **odczytu** niestandardowe zasady **widoku** opcji.|**Wyświetlanie zawartości**|**Widok**|IPC_GENERIC_READL "WIDOK"|Brak dodatkowych informacji|
|Kopiuj|WYODRĘBNIJ|Włącza opcje skopiować dane z dokumentu do tego samego lub innego dokumentu.|Jako **Użytkownicy z dostępem do odczytu na kopiowanie zawartości** opcja zasady niestandardowe.|**Kopiuj i Wyodrębnij zawartość**|**Wyodrębnij**|IPC_GENERIC_EXTRACTL "WYCIĄGU"|W niektórych aplikacjach pozwala są także zapisane w postaci niechronionych do całego dokumentu.|
|Wyświetl prawa|VIEWRIGHTSDATA|Zezwala użytkownikowi na Zobacz zasady, który jest stosowany do dokumentu.|Nie zaimplementowano.|**Widok przypisanych uprawnień**|**Wyświetl prawa**|IPC_READ_RIGHTSL "VIEWRIGHTSDATA"|Ignorowane przez niektóre aplikacje.|
|Zmienianie uprawnień|EDITRIGHTSDATA|Umożliwia użytkownikowi zmianę zasad, który jest stosowany do dokumentu. Obejmuje, w tym usunięcia ochrony.|Nie zaimplementowano.|**Zmienianie uprawnień**|**Edytowanie praw**|IPC_WRITE_RIGHTSL "EDITRIGHTSDATA"|Brak dodatkowych informacji|
|Zezwalaj na makra|OBJMODEL|Włącza opcję do makr lub wykonywania innych programowe albo zdalny dostęp do zawartości w dokumencie.|Jako **umożliwić programowy dostęp** opcja zasady niestandardowe. Nie jest ustawienie dla adresata.|**Zezwalaj na makra**|**Zezwalaj na makra**|Nie dotyczy|Brak dodatkowych informacji|

## Prawa zawarte w poziomy uprawnień
Niektóre aplikacje zgrupować praw użytkowania na poziomy uprawnień, aby ułatwić wybierz opcję praw użytkowania, które zazwyczaj są używane razem. Te poziomy permisisons pomagają abstrakcyjnej poziom złożoności od użytkowników, więc mogą wybrać opcje, które są oparte na rolach.  Na przykład **Weryfikacja** i **Współautor**. Mimo że te opcje często Pokaż podsumowanie praw użytkowników, może nie zawierają co prawo, który znajduje się w poprzedniej tabeli.

Aby uzyskać listę tych poziomów uprawnień i pełną listę praw, które zawierają, skorzystaj z poniższej tabeli.

|Poziom uprawnień|Aplikacje|Prawa zawarte (nazwa pospolita)|
|--------------------|-------------|-----------------------------------|
|Podgląd|Portalu Azure<br /><br />Do tworzenia aplikacji dla systemu Windows Rights Management|Widok, Otwórz, Odczyt<br /><br />Odpowiedź<br /><br />Odpowiedz wszystkim|
|Osoba dokonująca przeglądu|Portalu Azure<br /><br />Do tworzenia aplikacji dla systemu Windows Rights Management|Widok, Otwórz, Odczyt<br /><br />Zapisz<br /><br />Edytuj zawartość, Edycja<br /><br />Reply<sup>*</sup><br /><br />Odpowiedz wszystkim<sup>*</sup><br /><br />Do przodu<sup>*</sup>|
|Współautor|Portalu Azure<br /><br />Do tworzenia aplikacji dla systemu Windows Rights Management|Widok, Otwórz, Odczyt<br /><br />Zapisz<br /><br />Edytuj zawartość, Edycja<br /><br />Kopiuj<br /><br />Wyświetl prawa<br /><br />Zmienianie uprawnień<br /><br />Zezwalaj na makra<br /><br />Zapisz jako, eksportowanie<br /><br />Drukuj<br /><br />Reply<sup>*</sup><br /><br />Odpowiedz wszystkim<sup>*</sup><br /><br />Do przodu<sup>*</sup>|
|Współwłaściciel|Portalu Azure<br /><br />Do tworzenia aplikacji dla systemu Windows Rights Management|Widok, Otwórz, Odczyt<br /><br />Zapisz<br /><br />Edytuj zawartość, Edycja<br /><br />Kopiuj<br /><br />Wyświetl prawa<br /><br />Zmienianie uprawnień<br /><br />Zezwalaj na makra<br /><br />Zapisz jako, eksportowanie<br /><br />Drukuj<br /><br />Reply<sup>*</sup><br /><br />Odpowiedz wszystkim<sup>*</sup><br /><br />Do przodu<sup>*</sup><br /><br />Pełna kontrola|
<sup>*</sup> Nie ma zastosowania do tworzenia aplikacji dla systemu Windows Rights Management

## Prawa zawarte w domyślnych szablonach
Prawa, które są dołączone do domyślnych szablonów są następujące:

|Nazwa wyświetlana|Prawa zawarte (nazwa pospolita)|
|---------------------|-----------------------------------|
|&lt; nazwa organizacji &gt; - tylko widok poufne|Widok, Otwórz, Odczyt|
|&lt; nazwa organizacji &gt; - poufne|Widok, Otwórz, Odczyt<br /><br />Zapisz<br /><br />Edytuj zawartość, Edycja<br /><br />Wyświetl prawa<br /><br />Zezwalaj na makra<br /><br />Do przodu<br /><br />Odpowiedź<br /><br />Odpowiedz wszystkim|

## Zobacz też
[Konfigurowanie Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

