---
description: na
keywords: na
title: Logging and Analyzing Azure Rights Management Usage
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a735f3f7-6eb2-4901-9084-8c3cd3a9087e
---
# Rejestrowanie i analizy użycia zarządzania prawami Azure
Użyj informacje w tym temacie opisano sposób korzystania z użycia rejestrowania z Azure Rights Management (usług Azure RMS). Usługa Azure Rights Management może rejestrować wszystkie żądania fakt, że dla danej organizacji, która obejmuje żądania od użytkowników, akcje wykonywane przez administratorów Rights Management w Twojej organizacji i akcje wykonywane przez operatory Microsoft ułatwia wdrażanie Azure Rights Management.

Następnie można te dzienniki Azure Rights Management obsługuje następujące scenariusze:

-   Analizy biznesowej informacji szczegółowych.

    Azure Rights Management zapisują dzienniki w formacie dziennika rozszerzonego W3C na podane konto magazynu systemu Azure. Następnie można kierować te dzienniki do repozytorium wybranym (takie jak bazy danych, system przetwarzania analitycznego online (OLAP) lub mapy zmniejszyć system) do analizowania danych i tworzenia raportów. Na przykład można zidentyfikować uzyskuje dostęp do danych chronionych przez usługi RMS. Można określić, jakie osoby danych chronionych przez usługi RMS uzyskują dostęp do i z jakich urządzeń i z jakiej lokalizacji. Można ustalić czy osób pomyślnie odczytanie zawartości chronionej. Można również zidentyfikować osoby, które znasz ważnego dokumentu, który był chroniony.

-   Monitoruj nadużycie.

    Azure Rights Management rejestrowanie informacji jest dostępne w pobliżu rzeczywistego czasu, tak, aby stale można monitorować użycie firmy Rights Management. 99,9% dzienniki są dostępne w ciągu 15 minut działanie inicjowane przez usługi RMS.

    Na przykład można otrzymywać alerty w przypadku nagły wzrost osób odczytywanie danych chronionych przez usługi RMS poza standardowe godziny pracy, które mogą wskazywać, że złośliwy użytkownik jest zbieranie informacji o sprzedaży na tle konkurencji. Lub, jeśli ten sam użytkownik pozornie uzyskuje dostęp do danych z dwóch różnych adresów IP w krótkim terminie, który może wskazywać, że konto użytkownika został naruszony.

-   Wykonaj analizy śledczej.

    Jeśli masz przeciek informacji najprawdopodobniej będzie wyświetlony monit, który ostatnio używanych określonych dokumentów i jakie informacje podejrzanych osoby dostępu do ostatnio. Tego rodzaju pytania może odpowiedzieć, jeśli są używane Azure Rights Management i rejestrowanie, ponieważ osoby korzystające z zawartości chronionej zawsze należy uzyskać licencję Rights Management w celu otwarcia dokumenty i obrazy, które są chronione przez Azure Rights Management, nawet jeśli te pliki są przenoszone za pośrednictwem poczty e-mail lub kopiowane do dyski USB lub innych urządzeń pamięci masowej. Oznacza to, że użyciem dzienniki Azure Rights Management jako ostateczne źródła informacji dla analizy śledczej chronić dane przy użyciu Azure Rights Management.

> [!NOTE]
> Jeśli planuje tylko w przypadku rejestrowania zadań administracyjnych dla Azure Rights Management i czy nie mają być śledzone, jak użytkownicy korzystają z Rights Management, można użyć [Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx) polecenia cmdlet środowiska Windows PowerShell dla Azure Rights Management.
> 
> Można również użyć portalu Azure raportów użycia wysokiego poziomu, które obejmują **użycia usług RMS**, **najbardziej aktywnych użytkowników usług RMS**, **Użycie urządzenia RMS**, i **RMS włączone użycia aplikacji**. Aby uzyskać dostęp do tych raportów z portalu Azure, kliknij przycisk **usługi Active Directory**, wybierz i otwórz katalog, a następnie kliknij **Raporty**,

Aby uzyskać więcej informacji na temat rejestrowania użycia Azure Rights Management, użyj poniższe sekcje.

-   [Jak włączyć rejestrowanie użycia Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_EnableRMSLogging)

-   [Jak uzyskać dostępu do usługi Azure Rights Management dzienniki użycia](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_AccesAndUseLogs)

-   [Zarządzanie magazynem dziennika Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_ManageStorage)

-   [Sposobu delegowania dostęp do dzienników użycia Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Delegate)

-   [Interpretowanie dzienników użycia Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Interpret)

-   [Odwołanie do środowiska Windows PowerShell](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_PowerShell)

## <a name="BKMK_EnableRMSLogging"></a>Jak włączyć rejestrowanie użycia Azure Rights Management
Rejestrowanie użycia usługi Azure Rights Management jest opcjonalne, więc jeśli chcesz korzystać z niego musi podjąć specjalne kroki. Użycie opcji rejestrowania użycia Azure Rights Management, nie nastąpiła żadna zmiana w sposób działania Rights Management i sam proces rejestrowania jest bezpłatna. Jednakże należy podać konto magazynu systemu Azure dzienników i zostanie naliczona dla tego magazynu.

Przed rozpoczęciem upewnij się, że spełniają następujące wymagania wstępne umożliwia rejestrowanie użycia Azure Rights Management:

|Wymaganie|Więcej informacji|
|-------------|---------------------|
|Zarządzanymi subskrypcji, która zawiera Azure Rights Management|Musisz mieć subskrypcję Microsoft Azure Rights Management, który jest zarządzany przez organizację. Organizacje, które używają usług RMS dla osób, nie można użyć rejestrowanie użycia Azure Rights Management.<br /><br />Jeśli Twoja organizacja ma użytkowników, którzy korzystają z usług RMS dla użytkowników indywidualnych, rejestrowanie użycia Azure Rights Management zapewnia bardzo istotny powód biznesowych, aby przekształcić RMS dla osób w subskrypcję Microsoft Azure Rights Management.<br /><br />Aby uzyskać więcej informacji na temat subskrypcji, które obejmują usług Azure RMS, zobacz [Subskrypcje chmury, które obsługują Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) w sekcji [Wymagania dotyczące systemu Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tematu.<br /><br />Aby uzyskać więcej informacji dotyczących usług RMS dla użytkowników indywidualnych zobacz [RMS dla osób i Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md)|
|Subskrypcja platformy Azure|Dla dzienników Azure Rights Management, musisz mieć subskrypcję do magazynu Azure i wystarczające na platformie Azure.|
|Windows PowerShell dla usługi Azure Rights Management|Jeśli jeszcze tego nie zrobiono, należy pobrać i zainstalować moduł Windows PowerShell dla Azure Rights Management. Polecenia cmdlet programu Windows PowerShell użyje do konfigurowania i zarządzania Dzienniki użycia Azure Rights Management.<br /><br />Aby uzyskać więcej informacji, zobacz [Instalowanie programu Windows PowerShell Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).|
Użyj poniższej procedury umożliwiające rejestrowanie użycia Azure Rights Management, który zawiera kroki, aby utworzyć konto magazynu systemu Azure, a następnie skonfiguruj Azure, aby używał tego konta magazynu dla dzienników Rights Management.

> [!NOTE]
> Procedura ta zakłada, że masz konto platformy Azure. Rejestrowanie użycia usługi Azure Rights Management obsługuje indywidualne konta, ale jako najlepsze rozwiązanie należy użyć służbowego kont. Ponadto zaleca się tworzenie konta dedykowane magazynu dla dzienników Rights Management. Należy udostępniać klucze dostępu do magazynu Azure Rights Management, a potencjalnie z innymi osobami, jeśli korzystają również pliki dziennika.
> 
> Aby uzyskać więcej informacji dotyczących magazynu systemu Azure, zobacz [Azure dokumentacji magazynu](http://azure.microsoft.com/documentation/services/storage/).

#### Jak utworzyć konta magazynu i włączyć rejestrowanie użycia Azure Rights Management

1.  Zaloguj się do [portalu Azure](https://manage.windowsazure.com/).

2.  Wybierz **magazynu**.

    > [!TIP]
    > Jeśli ta opcja nie jest dostępna, sprawdź, czy subskrypcji platformy Azure oprócz subskrypcji Rights Management.

3.  Kliknij przycisk **Utwórz konto MAGAZYNU** oraz **adres URL**, wprowadź unikatową nazwę konta magazynu, a w razie potrzeby zmień **grupy lokalizacji/KOLIGACJI** aby był zgodny z danego regionu.

4.  Kliknij przycisk **OK**, i poczekaj, aż zobaczysz nazwa magazynu wyświetlany stan **Online**.

5.  Kliknij przycisk **zarządzania kluczami dostępu**.

6.  Z **Zarządzanie klawiszy** powoduje wyświetlenie okna dialogowego klucze podstawowe i pomocnicze dostępu skopiuj podstawowy klucz dostępu do Schowka, a następnie zamknij okno dialogowe.

7.  Uruchom program Windows PowerShell z **Uruchom jako administrator** opcji. Uruchom [Connect AadrmService](https://msdn.microsoft.com/library/azure/dn629415.aspx) polecenie, aby połączyć się z usługą Azure Rights Management:

    ```
    Connect-AadrmService
    ```

8.  Użyj [Set AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629426.aspx) polecenie, aby określić, gdzie chcesz zachować dzienniki użycia Azure Rights Management, zastępując *&lt; Access_Key &gt;* z podstawowy klucz dostępu skopiowany w kroku 6 i *&lt; StorageAccount &gt;* o nazwie konto magazynu, który został utworzony w kroku 3:

    ```
    $accesskey = convertto-securestring -asplaintext -force –string <Access_Key> Set-AadrmUsageLogStorageAccount -AccessKey $accesskey -StorageAccount <StorageAccount>
    ```

9. Użyj [AadrmUsageLogFeature Włącz](https://msdn.microsoft.com/library/azure/dn629421.aspx) polecenie, aby włączyć rejestrowanie użycia Azure Rights Management:

    ```
    Enable-AadrmUsageLogFeature
    ```
    Powinien zostać wyświetlony komunikat: **Funkcja dziennika użycia jest włączona dla usługi zarządzania prawami.**

Teraz, gdy jest włączone rejestrowanie użycia, Azure Rights Management rozpoczyna się rejestrować wszystkie akcje dla Twojej organizacji i zapisuje te informacje na koncie magazynu. Rejestrowanie informacji nie jest dostępne przed tego punktu.

## <a name="BKMK_AccesAndUseLogs"></a>Jak uzyskać dostępu do usługi Azure Rights Management dzienniki użycia
Jako serię obiektów blob Azure Rights Management zapisuje dzienniki konta usługi Magazyn Azure. Każdy obiekt blob zawiera jeden lub więcej rekordów dziennika w formacie dziennika rozszerzonego W3C. Nazwy obiektów blob są liczbami, w kolejności, w której zostały utworzone.[Interpretowanie dzienników użycia Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Interpret) Sekcja w dalszej części tego dokumentu zawiera więcej informacji na temat zawartość dziennika i ich utworzenia.

Może upłynąć trochę czasu, dzienników pojawi się na Twoim koncie magazynu po akcji Azure Rights Management. Większość dzienniki są wyświetlane w ciągu 15 minut.

Konto magazynu utworzony dla dzienników użycia Azure Rights Management przypomina skrzynki pocztowej i obsługuje odczyt bezpośrednio z konta magazynu, ale nie jest przeznaczona do użycia w ten sposób. Aby uzyskać najlepszą wydajność i zmniejszyć koszty, zalecany Pobierz dzienniki do lokalnego magazynu, na przykład folder lokalny, bazie danych lub repozytorium zmniejszyć mapy.

Można pobrać dzienników użycia na dwa sposoby:

-   Należy użyć polecenia cmdlet programu Windows PowerShell [Get-AadrmUsageLog](https://msdn.microsoft.com/library/azure/dn629401.aspx).

    Jest to najprostszy sposób, aby uzyskać dostęp do dzienników użycia. To polecenie cmdlet pobiera dzienniki na komputer, pobieranie każdego obiektu blob jako plik w lokalizacji określonej przez użytkownika.

-   Użyj [zestawu SDK usługi Magazyn Azure](http://www.windowsazure.com/en-us/develop/net/) do pisania aplikacji niestandardowe do pobrania w dziennikach.

    Niestandardowej aplikacji zapewniają większą elastyczność niż polecenia cmdlet Get-AadrmUsageLogs. Na przykład można przekazać pobierania dzienników komuś lub proces, który nie mogą korzystać z poświadczeń administracyjnych Azure Rights Management. Lub może wystąpić potrzeba sondowania dzienniki w czasie rzeczywistym, ponieważ chcesz monitorować niewłaściwego użycia.

#### Aby pobrać dzienników użycia przy użyciu programu PowerShell

-   Uruchom program Windows PowerShell z **Uruchom jako administrator** a Uruchom **Get-AadrmUsageLog –Path &lt;location&gt;**. Na przykład po utworzeniu folderu o nazwie **logs** na dysku E:

    -   Aby pobrać wszystkie dzienniki dostępne w folderze E:\logs: `Get-AadrmUsageLog -Path "e:\logs"`

    -   Aby pobrać określony zakres obiektów blob: `Get-AadrmUsageLog –Path "e:\logs" –FromCounter 1024 –ToCounter 2047`

Po uruchomieniu tych poleceń cmdlet programu Windows PowerShell nazwa ostatniego obiektu blob, który został pobrany. Ta nazwa można przypisać do zmiennej, co umożliwia uruchamianie Get-AadrmUsageLog w pętli lub zadania harmonogramu, pobierania każdorazowo tylko przyrostowe dzienników.

Na przykład:

**PS C:\ &gt; $LastBlobName = Get-AadrmUsageLog – Path "e:\logs"**

**1527**

**PS C:\ &gt; $LastBlobName**

**1527**

> [!TIP]
> Wszystkie pobrane pliki dziennika w formacie CSV można zagregować za pomocą [Analizator dziennika firmy Microsoft](http://www.microsoft.com/download/details.aspx?id=24659), który jest narzędzie do konwersji między różnych formatach znanych dziennika. Można również to narzędzie do konwersji danych do formatu SYSLOG lub zaimportuj go do bazy danych. Po zainstalowaniu narzędzia Uruchom **LogParser.exe /?** Pomoc i informacje, aby używać tego narzędzia. Na przykład, może uruchomić następujące polecenie, aby zaimportować wszystkie informacje w formacie pliku log: **logparser –i:w3c –o:csv “SELECT &#42; INTO AllLogs.csv FROM &#42;.log”**.

Można wstrzymać i wznowić rejestrowanie użycia. Po wstrzymaniu rejestrowania Azure Rights Management zachowuje informacje o koncie magazynu, dzięki czemu można łatwo wznowić rejestrowanie ponownie.

#### Zawieszanie i wznawianie rejestrowania użycia

-   Wstrzymywanie rejestrowania, użyj następującego polecenia cmdlet: [Wyłącz AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629404.aspx)

-   Aby wznowić rejestrowanie, użyj następującego polecenia cmdlet: [Włącz AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629421.aspx)

-   Aby sprawdzić, czy rejestrowanie jest włączone, użyj następującego polecenia cmdlet: [Get-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629425.aspx)

    Wartość **True** oznacza, że wartość i Azure Rights Management jest włączone rejestrowanie użycia **False** oznacza, że rejestrowanie użycia jest wyłączone.

## <a name="BKMK_ManageStorage"></a>Zarządzanie magazynem dziennika Azure Rights Management
Są naliczane opłaty dla miejsca do magazynowania, który jest używany do przechowywania dzienników Azure Rights Management.

Azure Rights Management nie bez automatycznego zarządzania użycie plików dziennika. Jeśli użytkownik nie podejmuj żadnych działań, pozostaną w koncie magazynu. Jednak aby zaoszczędzić miejsce i zmniejszenia kosztów magazynowania, można je usunąć, po ich pobraniu. Lub możesz wybrać pliki do usunięcia. Z jednym wyjątkiem Azure Rights Management nie używa tych plików dziennika, więc nie ma żadnych ograniczeń dotyczących, gdy można je usunąć.

Nosi nazwę pliku, który nie musisz usunąć (lub zmodyfikować) **metadanych** w **metadanych rms** kontenera. Azure Rights Management używa tego obiektu blob, aby śledzić ostatni numer obiektu blob, jaka jest używana. Jeśli ten plik zostanie usunięty, Azure Rights Management uruchamia nowy kontener dzienników, z numerem obiektów blob, który rozpoczyna się od 1, a wszystkie przyszłe pobrane pliki, które należy użyć polecenia cmdlet Get-AadrmUsageLog pobrać pliki dziennika przy użyciu tego nowego kontenera. W efekcie wszystkie dzienniki w kontenerze oryginalnej są zachowywane, ale oddzielona. Jedynym sposobem, aby pobrać te dzienniki oddzielone jest użycie magazynu Azure SDK.

> [!TIP]
> Zamiast zarządzać magazynem dziennika Azure Rights Management samodzielnie, możesz delegować tę funkcję zarządzania do innej firmy udostępnianie Twojego konta magazynu dostępu i nazwa klucza. Aby uzyskać więcej informacji, zobacz [Sposobu delegowania dostęp do dzienników użycia Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Delegate) później w tym temacie.

W pewnych okolicznościach można ponownie wygenerować klucze dostępu do magazynu. Na przykład:

-   Możesz zmienić firmy, która zarządza dzienniki użycia Azure Rights Management.

-   W przypadku podejrzeń złamane klucz dostępu do magazynu.

W takim przypadku do Ciebie jest to w przypadku używania pomocniczy klucz dostępu (przy założeniu, że podstawowy klucz dostępu był używany wcześniej) w celu zapewnienia ciągłości usługi. Podczas ponownego generowania klucza dostępu, które nie zostały wcześniej używa, następnie skonfiguruj Azure Rights Management, aby używać nowego klucza. Użyj poniższej procedury należy ponownie wygenerować pomocniczy klucz dostępu i Azure Rights Management, aby używać go skonfigurować:

#### Aby ponownie wygenerować pomocniczy klucz dostępu

1.  Zaloguj się do [portalu Azure](https://manage.windowsazure.com/).

2.  Wybierz **magazynu**.

3.  Kliknij przycisk **zarządzania kluczami dostępu**.

4.  W **Zarządzanie klawiszy** okno dialogowe, kliknij przycisk **ponownie wygenerować** obok pomocniczy klucz dostępu, a następnie skopiuj nowy klucz pomocniczy dostęp do Schowka.

5.  Uruchom program Windows PowerShell z **Uruchom jako administrator** opcji i używać [Set AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629426.aspx) skonfigurować Azure Rights Management, aby użyć tego nowego klucza dostępu przy użyciu polecenia cmdlet zastępowanie *&lt; StorageAccount &gt;* z nazwą konta usługi Magazyn i *&lt; Access_Key &gt;* z wygenerowano ponownie pomocniczy klucz dostępu, który został skopiowany:

    ```
    Set-AadrmUsageLogStorageAccount -StorageAccount <StorageAccount>-AccessKey <Access_Key>
    ```
    > [!WARNING]
    > Mimo że można przełączyć się do innego konta magazynu podczas wykonywania tego polecenia, ta akcja orphans poprzednie dzienniki i nie będzie dostępny dla polecenia cmdlet Set-AadrmUsageLogStorageAccount lub podobne polecenia zarządzania i funkcje.

6.  W **Zarządzanie klawiszy** okna dialogowego należy ponownie wygenerować klucz podstawowy dostęp.

## <a name="BKMK_Delegate"></a>Sposobu delegowania dostęp do dzienników użycia Azure Rights Management
Możesz delegować dostęp do dzienników RMS udostępnianie Twojego konta magazynu dostępu i nazwa klucza. Można przekazać dostęp do innego użytkownika administracyjnego, Deweloper w organizacji lub niezależnego dostawcę oprogramowania (ISV). Ponieważ nie będzie mieć poświadczenia administratora usług RMS, ich nie można użyć polecenia cmdlet Get-AardrmUsageLog pobrać dzienników usług RMS. W takim należy użyć zestawu SDK usługi Magazyn systemu Windows do pobrania w dziennikach. One również tworzyć aplikacje do odczytu w dziennikach bezpośrednio z usługi Magazyn Azure.

Jest to bezpieczne udostępnianie Twojego konta magazynu dostępu i nazwa klucza w ten sposób, gdy konto magazynu jest przeznaczone do dzienników usług RMS. Mimo że inne osoby mają klucz dostępu, nie mogą używać to na dostęp do innych kont magazynu lub użyj konta dzierżawy RMS.

## <a name="BKMK_Interpret"></a>Interpretowanie dzienników użycia Azure Rights Management
Skorzystaj z poniższych informacji, pomagają interpretować dzienniki użycia Azure Rights Management.

### Układ konto magazynu
Przy pierwszym uruchomieniu Azure Rights Management zapisują dzienniki na koncie magazynu tworzy następujące dwa kontenery:

-   **Metadanych rms**: Ten kontener jest zarezerwowana dla Azure Rights Management. Nie modyfikować ani usuwać tego kontenera.

-   **Rms - dzienniki - &lt; guid &gt;**: Ten kontener jest gdzie Azure Rights Management tworzy i zapisuje dziennik. Jeśli nie są już potrzebne w nich informacje rejestrowania można bezpiecznie usunąć wszystkie pliki w tym kontenerze.

Wraz z upływem czasu, Azure Rights Management może utworzyć dodatkowe **Rms - dzienniki - &lt; guid &gt;** kontenery. Na przykład jeśli **metadanych Rms** kontenera ulegnie uszkodzeniu lub zostanie przypadkowo usunięty, Azure Rights Management resetuje jego zawartość i tworzy nowy **Rms - dzienniki - &lt; guid &gt;** kontener dla wszystkich przyszłych dzienników. Stare dzienniki w kontenerze stare nie są usuwane, ale są oddzielone.

### Sekwencja dziennika
Azure Rights Management zapisuje dzienniki jako serię obiektów blob. Każdy obiekt blob zawiera jeden lub więcej rekordów dziennika w rozszerzony format W3C dziennika.

Nazwa każdego obiektu blob jest liczbą. W ramach każdego kontenera dziennika pierwszego obiektu blob nosi nazwę 000000001. Każdy obiekt blob jest nazywane kolejno w kolejności, w której został utworzony. Każdy obiekt blob zawiera jeden lub więcej rekordów dziennika. Każdy rekord dziennika zawiera sygnaturę czasową UTC, która wskazuje, kiedy odpowiednie żądanie zostało obsłużone przez usługę Azure Rights Management.

> [!IMPORTANT]
> System Azure Rights Management rejestrowania jest zoptymalizowany do zaoferowania dzienniki szybko, a nie w kolejności sekwencyjnej strict. Kolejność obiektów blob, jak również kolejność rekordów dziennika w obiektu blob, może być poza kolejnością chronologicznym. Jest jedynym powodem obiektów blob są nazywane kolejno umożliwia wydajne je pobrać przyrostowo.
> 
> Dwa przykłady możliwych wyników sekwencji dziennika:
> 
> -   Rekordy dziennika w obiekcie blob 000000004 może nakładać się na porządku chronologicznym z rekordów dziennika w obiekcie blob 000000003. W skrajnych przypadkach wszystkie rekordy dziennika w obiekcie blob 000000004 może zostać wygenerowane przed wszystkie rekordy dziennika w obiekcie blob 000000003.
> -   Drugi rekord dziennika w obiekcie blob może zostać wygenerowane przed pierwszym rekordu dziennika, ale zostało zapisane w magazynie w odwrotnej kolejności.

Przed analizy dzienników użycia Azure Rights Management, zalecamy pobierania i importowania dziennika do repozytorium, w którym można sortować dzienników z ich sygnatury czasowej. Dodatkowe informacje o Pobierz dzienniki, można znaleźć w temacie [Jak uzyskać dostępu do usługi Azure Rights Management dzienniki użycia](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_AccesAndUseLogs) w tym temacie.

Dzienniki nie są zawsze chronologicznym, ale większość z nich są zapisywane w ciągu 15 minut żądania podczas określania dzienniki przy użyciu ich sygnatury czasowej, dodawać do 15 minut do czasu, który Cię interesuje. Następnie należy pobrać te dzienniki. Ta strategia powinna mieć pewność, że prawie wszystkie dzienniki.

Inne rzeczą do zapamiętania jest znacznik czasu każdego rekordu dziennika lokalnego czasu przetwarzania żądania usługi Azure Rights Management. Ponieważ Azure Rights Management działa na wielu serwerach w wielu centrum danych, czasami dzienniki może wydawać się poza kolejnością, nawet wtedy, gdy są one posortowane według ich sygnatury czasowej. Jednak poszczególne jest mały i zazwyczaj w ciągu minuty. W większości przypadków to nie jest problem, który będzie problem dotyczący analizy dziennika.

### Format obiektów blob
Każdy obiekt blob jest w formacie dziennika rozszerzonego W3C. Rozpoczyna się od następujące dwa wiersze:

**#Software: RMS**

**#Version: 1.1**

Pierwszy wiersz określa, że są one dzienniki Azure Rights Management. Drugi wiersz identyfikuje, że pozostałą część obiektu blob następuje Specyfikacja wersji 1.1. Zaleca się, że wszystkie aplikacje, które przeanalizować te dzienniki Sprawdź poniższe dwa wiersze przed kontynuowaniem przeanalizować pozostałą część obiektu blob.

Trzeci wiersz wylicza listę nazw pól, które są oddzielone karty:

**#Fields: daty i czasu identyfikator wiersza typ żądania identyfikator użytkownika wynik identyfikator korelacji identyfikator zawartości wiadomości e-mail właściciela wystawcy identyfikator szablonu nazwa pliku Data opublikowana c-info c-ip**

Każdy z kolejnych wierszy jest rekordu dziennika. Wartości pól w takiej samej kolejności jak w poprzednim wierszu i są oddzielone znakami tabulacji. Interpretowanie pola, skorzystaj z poniższej tabeli.

|Nazwa pola|Typ danych W3C|Opis|Przykład wartości|
|--------------|------------------|--------|---------------------|
|Data|Data|Jeśli żądanie zostało obsłużone Data w formacie UTC.<br /><br />Źródło jest zegar lokalnego na serwerze, który obsłużonych żądań.|2013-06-25|
|czas|Czas|Czas UTC w formacie 24-godzinnym, gdy żądanie zostało obsłużone.<br /><br />Źródło jest zegar lokalnego na serwerze, który obsłużonych żądań.|21:59:28|
|Identyfikator wiersza|Tekst|Unikatowy identyfikator GUID dla tego rekordu dziennika.<br /><br />Ta wartość jest przydatne, gdy Agreguj dzienniki lub kopiowania dzienników do innego formatu.|1c3fe7a9-d9e0-4654-97b7-14fafa72ea63|
|Typ żądania|Nazwa|Nazwa interfejsu API usług RMS, którego zażądano.|AcquireLicense|
|Identyfikator użytkownika|Ciąg|Użytkownik, który wysłał żądanie.<br /><br />Wartość jest ujęta w apostrofy. Niektóre typy żądania są anonimowe, w którym to przypadku jest wartość ".|"joe@contoso.com"|
|wynik|Ciąg|'Sukces', jeśli żądanie zostało obsłużone pomyślnie.<br /><br />Typ błędu w pojedynczym cudzysłowie, jeśli żądanie nie powiodło się.|'Sukces'|
|Identyfikator korelacji|Tekst|Identyfikator GUID jest wspólne dziennika klienta usług RMS i dziennik serwera dla danego żądania.<br /><br />Ta wartość może być przydatne do rozwiązywania problemów z klientem.|cab52088-8925-4371-be34-4b71a3112356|
|Identyfikator zawartości|Tekst|Identyfikator GUID, ujęte w nawiasy klamrowe, które identyfikuje chronionej zawartości (na przykład dokumentu).<br /><br />To pole ma wartość tylko wtedy, gdy typ żądania jest AcquireLicense i jest pusta dla innych typów żądań.|{bb4af47b-cfed-4719-831d-71b98191a4f2}|
|adres e-mail właściciela|Ciąg|Adres e-mail właściciela dokumentu.|alice@contoso.com|
|wystawcy|Ciąg|Adres e-mail wystawcy dokumentu.|alice@contoso.com (lub) FederatedEmail.4c1f4d-93bf-00a95fa1e042@contoso.onmicrosoft.com "|
|Identyfikator szablonu|Ciąg|Identyfikator szablonu do ochrony dokumentu.|{6d9371a6-4e2d-4e97-9a38-202233fed26e}|
|Nazwa pliku|Ciąg|Nazwa pliku dokumentu, który był chroniony.|TopSecretDocument.docx|
|Data opublikowana|Data|Data, gdy był chroniony dokument.|2015-10-15T21:37:00|
|c informacje|Ciąg|Informacje o platformie klienta, który wysłał żądanie.<br /><br />Określony ciąg różni się zależnie od aplikacji (na przykład systemu operacyjnego lub przeglądarki).|"MSIPC; wersja = 1.0.623.47; AppName = WINWORD. EXE; AppVersion = 15.0.4753.1000; AppArch = x 86; OSName = Windows; OSVersion = 6.1.7601; OSArch = amd64 "|
|c-ip|Adres|Adres IP klienta, który wysyła żądanie.|64.51.202.144|

#### Wyjątki w polu Identyfikator użytkownika
Mimo że pole identyfikatora użytkownika zwykle wskazuje użytkownika, który wysłał żądanie, istnieją dwa wyjątki której wartość nie jest zmapowana rzeczywistego użytkownika:

-   Wartość **"microsoftrmsonline @&lt; YourTenantID &gt;. &lt; region &gt; rms.. aadrm.com"**.

    Oznacza to, że usługi Office 365, takich jak Exchange Online lub usługi Sharepoint Online jest zgłaszającego żądanie. W ciągu *&lt; YourTenantID &gt;* jest identyfikator GUID dla dzierżawcy i *&lt; region &gt;* jest region, w którym dzierżawcy jest zarejestrowany. Na przykład **na** reprezentuje Ameryka Północna **UE** reprezentuje Europie, i **ap** reprezentuje Azji.

-   Jeśli używasz łącznika usług RMS.

    Żądania z tego łącznika są rejestrowane przy użyciu nazwy głównej usługi RMS generuje automatycznie po zainstalowaniu łącznika usług RMS.

#### Typy typowe żądania
Istnieje wiele typów żądania Azure Rights Management, ale w poniższej tabeli przedstawiono niektóre typy najczęściej używanych żądania.

|Typ żądania|Opis|
|---------------|--------|
|AcquireLicense|z komputera z systemem Windows żądanie licencji dla zawartości chronionej RMS.|
|AcquirePreLicense|w imieniu użytkownika, żądanie o licencję dla zawartości chronionej RMS.|
|AcquireTemplates|zadzwoniono uzyskuje szablony na podstawie szablonu identyfikatory|
|AcquireTemplateInformation|zadzwoniono pobrać identyfikatorów szablonu z usługi.|
|AddTemplate|jest nawiązane połączenie z portalu Azure dodać szablon.|
|BECreateEndUserLicenseV1|następuje wywołanie z urządzenia przenośnego do tworzenia Umowa licencyjna użytkownika.|
|BEGetAllTemplatesV1|jest nawiązane połączenie z urządzeniem przenośnym (zaplecza) Pobierz wszystkie szablony.|
|Podpisz|klienta jest poświadczania zawartości do ochrony.|
|Odszyfrować|Klient próbuje odszyfrować zawartość chronioną RMS.|
|DeleteTemplateById|następuje wywołanie z portalu Azure, aby usunąć identyfikatora szablonu przez szablon|
|ExportTemplateById|jest nawiązane połączenie z portalu Azure eksportowania szablonu na podstawie szablonu identyfikatora|
|FECreateEndUserLicenseV1|podobny do żądania AcquireLicense, ale z urządzeń przenośnych.|
|FECreatePublishingLicenseV1|taki sam, jak Zatwierdź i GetClientLicensorCert połączone z klientów mobilnych.|
|FEGetAllTemplates|zostanie nawiązane połączenie, z urządzenia przenośnego (frontonu) pobrać szablony.|
|GetAllTemplates|następuje wywołanie z portalu Azure, aby pobrać wszystkie szablony.|
|GetClientLicensorCert|Klient żąda certyfikatu publikowania (który jest później używany do ochrony zawartości) z komputera z systemem Windows.|
|Getconfiguration —|polecenia cmdlet środowiska PowerShell Azure jest wywoływana w celu pobrania konfiguracji dzierżawy usługi Azure RMS.|
|GetConnectorAuthorizations|następuje wywołanie z łączników RMS uzyskać ich konfiguracji z chmury.|
|GetTenantFunctionalState|portalu Azure sprawdza, czy jest aktywny usług Azure RMS.|
|GetTemplateById|jest nawiązane połączenie z portalu Azure Pobierz szablon, określając szablonu identyfikatora|
|ExportTemplateById|Wywołanie jest wprowadzanych z portalu Azure do eksportowania szablonu, określając szablon identyfikatora|
|FindServiceLocationsForUser|następuje wywołanie kwerendy dla adresu URL, który jest używany do wywoływania Zatwierdź lub AcquireLicense.|
|ImportTemplate|jest nawiązane połączenie z portalu Azure importowania szablonu.|
|ServerCertify|następuje wywołanie z obsługą usług RMS klienta (na przykład program SharePoint) aby przeprowadzić certyfikację serwera.|
|SetUsageLogFeatureState|Wywołanie włączyć rejestrowanie użycia.|
|SetUsageLogStorageAccount|wywołanie do określenia lokalizacji dzienników usług Azure RMS.|
|SignDigest|zostanie nawiązane połączenie, gdy klucz jest używany do podpisywania celów. Jest to zazwyczaj raz na AcquireLicence (lub FECreateEndUserLicenseV1), Zatwierdź i GetClientLicensorCert (lub FECreatePublishingLicenseV1).|
|UpdateTemplate|z portalu Azure zaktualizować istniejący szablon zostanie nawiązane połączenie.|

## <a name="BKMK_PowerShell"></a>Odwołanie do środowiska Windows PowerShell
Aby konfiguracji i użycia rejestrowanie użycia Azure Rights Management, użyj następujących poleceń cmdlet programu Windows PowerShell:

-   [Wyłącz AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629404.aspx)

-   [Włącz AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629421.aspx)

-   [Get-AadrmUsageLog](https://msdn.microsoft.com/library/azure/dn629401.aspx)

-   [Get-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629425.aspx)

-   [Get-AadrmUsageLogLastCounterValue](https://msdn.microsoft.com/library/azure/dn629423.aspx)

-   [Get-AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629419.aspx)

-   [Zestaw AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629426.aspx)

Aby uzyskać więcej informacji o Azure Rights Management za pomocą środowiska Windows PowerShell, zobacz [Administrowanie Azure Rights Management przy użyciu programu Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md).

## Zobacz też
[Za pomocą systemu Azure Rights Management](../Topic/Using_Azure_Rights_Management.md)

