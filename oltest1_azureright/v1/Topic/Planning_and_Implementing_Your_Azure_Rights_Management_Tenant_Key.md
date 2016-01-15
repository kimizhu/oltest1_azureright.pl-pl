---
description: na
keywords: na
title: Planning and Implementing Your Azure Rights Management Tenant Key
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14
---
# Planowanie i wdrażanie swoim kluczem dzierżawcy zarządzania prawami Azure
Na tej podstawie w tym temacie ułatwia planowanie i Zarządzanie kluczem dzierżawy Rights Management service (RMS) dla Azure RMS. Na przykład zamiast Microsoft zarządzania swoim kluczem dzierżawy (domyślnie), można zarządzać własnych dzierżawy klucza, aby zachować zgodność z przepisami określonych, mające zastosowanie do swojej organizacji.  Zarządzanie kluczem dzierżawy jest również określana jako udostępnić własne klucza, lub BYOK.

> [!NOTE]
> Klucz dzierżawy RMS jest nazywana klucza certyfikatu licencjodawcy serwera (SLC). Azure RMS podtrzymuje co najmniej jednego klucza dla każdego organizację, która subskrybuje Azure RMS. Zawsze, gdy klucza jest używana do usług RMS w organizacji (na przykład kluczy użytkowników, klucze komputera, klucze szyfrowania dokumentu), ich kryptograficznie łańcucha kluczowi dzierżawy RMS.

**Na pierwszy rzut:** Skorzystaj z poniższej tabeli jako szybki przewodnik do topologii klucza zalecaną dzierżawy. Następnie należy użyć dodatkowe sekcje, aby uzyskać więcej informacji.

Jeśli wdrożono Azure RMS za pomocą klucza dzierżawy, który jest zarządzany przez firmę Microsoft, możesz zmienić na BYOK później. Jednak obecnie nie można zmienić klucza dzierżawy systemu Azure RMS z BYOK do zarządzanych przez firmę Microsoft.

|Potrzeba biznesowa|Topologia klucza zalecaną dzierżawcy|
|----------------------|----------------------------------------|
|Wdrażanie Azure RMS szybko i bez konieczności specjalnego sprzętu|Zarządzany przez firmę Microsoft|
|Potrzebujesz pełną funkcjonalność IRM w Exchange Online z Azure RMS|Zarządzany przez firmę Microsoft|
|Klucze są utworzone przez użytkownika i chronione w sprzętu zabezpieczeń moduły|BYOK<br /><br />Obecnie ta konfiguracja spowoduje ograniczonej funkcjonalności IRM w programie Exchange Online. Aby uzyskać więcej informacji, zobacz [BYOK pricing and restrictions](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing) sekcji.|
Umożliwia następujące sekcje pomagają w określeniu który klucz dzierżawy topologii do użycia, zrozumieć klucza cyklem życia dzierżawy, jak wdrożyć wyświetlone własne klucza (BYOK) i jakie kroki zaczęły dalej:

-   [Choose your tenant key topology: Managed by Microsoft (the default) or managed by you (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ChooseTenantKey)

-   [BYOK pricing and restrictions](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing)

-   [Implementing bring your own key (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK)

-   [Next steps](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_NextSteps)

## <a name="BKMK_ChooseTenantKey"></a>Wybierz dzierżawą topologii klucza: Zarządzany przez firmę Microsoft (domyślnie) lub zarządzane przez użytkownika (BYOK)
Określa, które topologia klucza dzierżawy jest najlepsze dla organizacji. Domyślnie Azure RMS generuje klucz dzierżawy i zarządza większością aspektów cyklem życia klucza dzierżawy. Jest to najprostszy opcja z najniższym ogólne koszty administracyjne. W większości przypadków można nawet niepotrzebne wiedzieć, że klucz dzierżawy. Po prostu Zarejestruj się do usług RMS Azure i pozostałej części procesu zarządzania kluczami jest obsługiwane przez firmę Microsoft.

Użytkownik może też pełną kontrolę nad klucza dzierżawy obejmuje tworzenie swoim kluczem dzierżawy i przechowywanie kopii głównej swojego lokalnie. Ten scenariusz jest często określone wyświetlone własny klucz (BYOK). Po wybraniu tej opcji następujące konsekwencje:

1.  Klucz dzierżawy jest generowanie swoje lokalnie, zgodnie z zasadami dotyczącymi IT.

2.  Można bezpiecznie przekierować klucz dzierżawy z modułu zabezpieczeń sprzętu (HSM) w swojej posiadanie HSM, które są własnością i są zarządzane przez firmę Microsoft. Przez cały ten proces swoim kluczem dzierżawy nigdy nie pozostawia granic ochrony sprzętu.

3.  Podczas przesyłania swoim kluczem dzierżawy do firmy Microsoft, pozostaje chronionych przez firmy Thales HSM. Firma Microsoft współpracuje z firmy Thales, aby upewnić się, że klucz dzierżawy nie może zostać wyodrębniony z HSM firmy Microsoft.

Opcjonalne, ale będzie również prawdopodobnie chcesz użyć najbliższej w czasie rzeczywistym obciążenie dzienników z Azure RMS, aby zobaczyć dokładnie tak jak i kiedy jest on używany klucz dzierżawy.

> [!NOTE]
> Jako środek dodatkowej ochrony Azure RMS używa tych oddzielnych zabezpieczeń dla jego centrów danych w USA, EMEA (Europa, Bliski Wschód i Afryka) i Azji. Jeśli zarządzasz kluczem dzierżawy jest powiązane na świecie zabezpieczeń regionu, w którym jest zarejestrowany dzierżawą RMS. Na przykład klucz dzierżawy z Europejskiego klienta nie można używać w centrach danych w USA lub Azji.

## <a name="BKMK_OverviewLifecycle"></a>Cykl życia klucza dzierżawcy
Jeśli zdecydujesz się, że firma Microsoft powinna zarządzać swoim kluczem dzierżawy, firma Microsoft obsługuje większość operacji klucza cyklem życia. Jednakże w razie do zarządzania swoim kluczem dzierżawy, użytkownik jest odpowiedzialny za wielu operacji klucza cyklem życia i niektóre dodatkowe procedury.

Następujące diagramy Pokaż i porównuje te dwie opcje. Pierwszy diagram pokazuje, jak małe ogólnych administratora jest dla Ciebie w konfiguracji domyślnej po Microsoft zarządza klucz dzierżawy.

![](../Image/RMS_BYOK_cloud.png)

Drugi diagram zawiera dodatkowe kroki wymagane podczas zarządzania klucz dzierżawy.

![](../Image/RMS_BYOK_onprem.png)

Jeśli zdecydujesz się swoim kluczem dzierżawcy zarządzania firma Microsoft, nie jest wymagana do wygenerowania klucza nie dodatkowych czynności i możesz pominąć następujące sekcje i przejdź wprost do [Next steps](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_NextSteps).

Jeśli zdecydujesz się samodzielnie zarządzać swoim kluczem dzierżawy, przeczytaj następujące sekcje, aby uzyskać więcej informacji.

### Więcej informacji na temat firmy Thales HSM i firmy Microsoft
Azure RMS używa HSM firmy Thales do ochrony kluczy.

Firmy Thales e zabezpieczeń to wiodąca globalnego dostawcy szyfrowania danych i cyber rozwiązania zabezpieczeń usługi finansowe, wysokiej technologii, produkcji, Rząd i sektory technologii. Z roku 40 ścieżki rekordu chroni firmy i informacje Rząd rozwiązań firmy Thales są używane przez cztery pięciu największych energii i aerospace firm, 22 NATO krajach i zabezpieczyć więcej niż 80 procent transakcji płatniczych na całym świecie.

Firma Microsoft ma we współpracy z firmy Thales udoskonalania stan clipart dla HSM. Te ulepszenia umożliwiają typowe korzystania z zalet obsługiwane usługi bez zrzeczenia się kontroli nad kluczy. W szczególności te ulepszenia zdalne zarządzanie HSM tak, aby nie masz do firmy Microsoft. Jako usługi w chmurze Azure RMS skaluje w krótkim terminie, aby spełnić kołkami użycie w organizacji. W tym samym czasie klucz jest chroniony wewnątrz HSM firmy Microsoft: Można zachować kontrolę nad klucza cyklem życia, ponieważ generowanie klucza i przekierować je HSM firmy Microsoft.

Aby uzyskać więcej informacji, zobacz [HSM firmy Thales i Azure RMS](http://www.thales-esecurity.com/msrms/cloud) w witrynie sieci web firmy Thales.

## <a name="BKMK_Pricing"></a>Ceny BYOK i ograniczenia
Za pomocą BYOK organizację, która ma zarządzanymi subskrypcji systemu Azure i zalogować się jego użycie bez dodatkowych opłat. Organizacje dla osób korzystających z usług RMS nie można użyć BYOK i rejestrowania, ponieważ nie mają administrator dzierżawy, aby skonfigurować tych funkcji.

> [!NOTE]
> Aby uzyskać więcej informacji dotyczących usług RMS dla użytkowników, zobacz [RMS dla osób i Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md).

![](../Image/RMS_BYOK_noExchange.png)

Rejestrowanie i BYOK bezproblemową pracę z każdej aplikacji, która integruje się z Azure RMS. To obejmuje usługi w chmurze takich jak SharePoint Online, lokalnych serwerach z systemem Exchange i programu SharePoint, które działają z Azure RMS za pomocą łącznika RMS i aplikacje klienckie, takie jak Office 2013. Instalacja obejmuje programy dzienniki użycia klucza, niezależnie od tego, które aplikacji sprawia, że żądania z Azure RMS.

Istnieje jeden wyjątek: Obecnie **Azure RMS BYOK nie jest zgodny z Exchange Online**.  Jeśli chcesz użyć Exchange Online, zaleca się wdrożenie Azure RMS w domyślny tryb zarządzania kluczami teraz, gdzie Microsoft generuje i zarządza swoim kluczem. Istnieje możliwość przenosić do BYOK później, na przykład Exchange Online obsługuje Azure RMS BYOK. Jeśli użytkownik nie może oczekiwać, inna opcja jest jednak do wdrożenia usług Azure RMS za pomocą BYOK teraz, z ograniczoną funkcjonalnością RMS programu Exchange Online (niechronione wiadomości e-mail i załączniki niechronione pozostają w pełni funkcjonalną):

-   Nie można wyświetlić chronionej wiadomości e-mail lub chronionych załączniki programu Outlook Web Access.

-   Nie można wyświetlić chronionej wiadomości e-mail na urządzeniach przenośnych, które korzystać z tej funkcji programu Exchange ActiveSync.

-   Transport odszyfrowywania (na przykład do skanowania w poszukiwaniu złośliwego oprogramowania) i odszyfrowywania dziennika nie jest możliwe, w ten sposób chroniona wiadomości e-mail i załączniki chronionych zostanie pominięty.

-   Transport ochrony reguły i danych zapobieganie utracie (DLP), który wymuszanie stosowania zasad IRM nie jest możliwe, więc nie można zastosować RMS ochrony za pomocą tych metod.

-   Oparte na serwerze wyszukiwanie chronionej wiadomości e-mail, więc chronionej wiadomości e-mail zostanie pominięty.

Korzystając z Azure RMS BYOK z ograniczoną funkcjonalnością RMS programu Exchange Online, RMS będzie działał z klientów wiadomości e-mail w programie Outlook w systemach Windows i Mac, a w innych klientów poczty e-mail, które nie korzystać z tej funkcji programu Exchange ActiveSync.

Jeśli do Azure RMS są migrowane z usług AD RMS, mogły być importowane swoim kluczem jako zaufany publikacji domenę Exchange online (nazywane również BYOK w terminologii Exchange różni się od Azure RMS BYOK). W tym scenariuszu musisz usunąć publikacji z programu Exchange Online, aby uniknąć konfliktu szablony i zasadami. Aby uzyskać więcej informacji, zobacz [RMSTrustedPublishingDomain Usuń](https://technet.microsoft.com/library/jj200720%28v=exchg.150%29.aspx) z biblioteki poleceń cmdlet programu Exchange Online.

Czasami wyjątek Azure RMS BYOK Exchange Online nie jest problem w praktyce. Na przykład organizacji, które potrzebują BYOK i rejestrowanie uruchamiania ich danych aplikacji (Exchange, SharePoint, Office) lokalnie, a Azure RMS dla funkcji, która nie jest łatwo dostępne z lokalnego AD RMS (na przykład współpracy z innych firm i dostęp z klientów przenośnych). Zarówno BYOK, jak i rejestrowanie pracy oraz w tym scenariuszu i umożliwić organizacji, aby mają pełną kontrolę nad ich subskrypcji Azure RMS.

## <a name="BKMK_ImplementBYOK"></a>Wykonania Przesuń własny klucz (BYOK)
Użyj informacje i procedury w tej sekcji, w przypadku do generowania i Zarządzaj swoim kluczem dzierżawy; Udostępnij własnym scenariuszu klucza (BYOK):

-   [Prerequisites for BYOK](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Preqs)

-   [Generate and transfer your tenant key – over the Internet](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOK_Internet)

-   [Generate and transfer your tenant key – in person](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOK_InPerson)

> [!IMPORTANT]
> Jeśli zostało już rozpoczęte do użycia [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (aktywować usługi) i użytkownikami, którzy uruchamiania pakietu Office 2010, skontaktuj się z usług obsługi klienta firmy Microsoft (CSS), przed uruchomieniem tych procedur. W zależności od scenariusza i wymagania, nadal można korzystać z BYOK, ale niektóre ograniczenia lub dodatkowe kroki.
> 
> Jeśli w organizacji jest określone zasady do obsługi klucze także kontaktować z CSS.

### <a name="BKMK_Preqs"></a>Wymagania wstępne dotyczące BYOK
W poniższej zamieszczono listę wymagań wstępnych dla Przesuń własny klucz (BYOK).

|Wymagania|Więcej informacji|
|-------------|---------------------|
|Subskrypcji, która obsługuje Azure RMS|Aby uzyskać więcej informacji na temat dostępnych subskrypcji, zobacz [Subskrypcje chmury, które obsługują Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) w sekcji [Wymagania dotyczące systemu Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tematu.|
|Nie należy używać usług RMS dla osób lub Exchange Online. Lub, jeśli używasz programu Exchange Online, należy zapoznać się i zaakceptować ograniczenia BYOK przy użyciu tej konfiguracji.|Aby uzyskać więcej informacji dotyczących ograniczenia i bieżące dla BYOK, zobacz [BYOK pricing and restrictions](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing) w tym temacie. **Important:** Aktualnie BYOK nie jest zgodny z Exchange Online.|
|Firmy Thales HSM, karty inteligentne i oprogramowania do obsługi<br /><br />Jeśli użytkownik są migrowane z usług AD RMS do Azure RMS za pomocą klucza oprogramowania do klucza sprzętu, musi mieć minimalnej wersji 11.62 sterowników firmy Thales.|Musi mieć dostęp do firmy Thales sprzętowego modułu zabezpieczeń i działania wiedza na poziomie podstawowym z firmy Thales HSM. Zobacz [sprzętowego modułu zabezpieczeń firmy Thales](http://www.thales-esecurity.com/msrms/buy) listy modeli zgodne lub zakupu sprzętowych modułów zabezpieczeń, jeśli nie masz.|
|Jeśli chcesz przenieść dzierżawą klucza w Internecie, a nie fizycznie występować w Redmond, USA:<br /><br />1.  Offline x 64 stacji roboczej z minimalną system operacyjny Windows 7 systemu Windows i firmy Thales nShield oprogramowania do co najmniej w wersji 11.62.<br />    W przypadku tej stacji roboczej działa system Windows 7, należy [zainstalować program Microsoft .NET Framework 4.5](http://go.microsoft.com/fwlink/?LinkId=225702).<br />2.  Stacji roboczej, który jest połączony z Internetem i ma minimalny system operacyjny Windows systemu Windows 7.<br />3.  Na dysku USB lub innych urządzeń magazynu przenośnego, które ma co najmniej 16 MB wolnego miejsca.|Następujące składniki wymagane wstępnie nie są wymagane, jeśli podróż do Redmond i transfer swoim kluczem dzierżawy osobiście.<br /><br />Ze względów bezpieczeństwa zaleca się pierwszy stacji roboczej nie jest połączony z siecią. Jednakże to nie są programistycznie wymuszane. **Note:** W instrukcji, które należy wykonać tej stacji roboczej nosi nazwę stacji roboczej po rozłączeniu.<br />Ponadto w przypadku swojego klucza dzierżawy dla sieci produkcji, zaleca się stosowanie drugim, oddzielne stacji roboczej, aby pobrać zestaw narzędzi i przekazać klucz dzierżawy. Jednak do celów testowych, można użyć tej samej stacji roboczej jako pierwszy. **Note:** W instrukcji, które należy wykonać drugi stacji nosi nazwę stacji roboczej połączony z Internetem.|
|Opcjonalne: Subskrypcji systemu Azure|Jeśli chcesz rejestrować użycie klucza dzierżawy (i użycie Rights Management), musisz mieć subskrypcję do magazynu systemu Azure i wystarczające Azure do przechowywania dzienników.|
Procedury Generowanie i używanie własnych klucz dzierżawy zależą od tego, czy użytkownik chce to zrobić przez Internet lub osobiście:

-   **W Internecie:** Wymaga to niektóre czynności konfiguracyjne dodatkowe, takie jak pobieranie i przy użyciu zestawu narzędzi i poleceń cmdlet programu Windows PowerShell. Jednak nie muszą być fizycznie w miejscu firmy Microsoft do transferu swoim kluczem dzierżawy. Zabezpieczenia jest obsługiwany przez następujących metod:

    -   Klucz dzierżawy jest generowanie offline stacji roboczej, która ogranicza ataku.

    -   Klucz dzierżawy jest szyfrowana z kluczem wymiany klucza (KEK), który pozostaje zaszyfrowany, aż do przesłania do HSM RMS Azure. Zaszyfrowana wersja swoim kluczem dzierżawy pozostawia oryginalne stacji roboczej.

    -   Narzędzie ustawia właściwości na swoim kluczem dzierżawy wiążącą swoim kluczem dzierżawy na świecie zabezpieczeń Azure RMS. Dlatego po HSM RMS Azure odbierać i odszyfrować klucz dzierżawy, tylko te HSM jej użyć. Nie można wyeksportować klucza dzierżawy. To powiązanie są realizowane przez HSM firmy Thales.

    -   Klucz wymiany klucza (KEK) używany do szyfrowania klucza dzierżawy jest generowany w HSM RMS Azure i nie można wyeksportować. HSM wymuszać, że nie można nie ma zwykłego wersji KEK poza HSM. Ponadto zestaw narzędzi zawiera poświadczenie z firmy Thales czy KEK nie jest możliwy do eksportowania i został wygenerowany wewnątrz oryginalnego HSM, który został wytwarzane przez firmy Thales.

    -   Zestaw narzędzi zawiera poświadczenie z firmy Thales, że na świecie zabezpieczeń Azure RMS również został wygenerowany na oryginalny HSM, wytwarzane przez firmy Thales. Okaże się użytkownikowi czy firma Microsoft używa oryginalnego sprzętu.

    -   Firma Microsoft używa oddzielnych KEKs, a także Rozdziel rozwiązań zabezpieczeń w każdy region geograficzny, który zapewnia, że klucz dzierżawy mogą użyty tylko w centrach danych w regionie on zaszyfrowany. Na przykład klucz dzierżawy z Europejskiego klienta nie można używać w centrach danych w amerykańskie północ lub Azji.

    > [!NOTE]
    > Klucz dzierżawy bezpiecznie przechodzić niezaufanymi komputerów i sieci, ponieważ jest zaszyfrowany i zabezpieczone z poziomu uprawnień kontroli dostępu, dzięki czemu można używać tylko w ramach swojej HSM i HSM firmy Microsoft dla systemu Azure RMS. Za pomocą skryptów, które znajdują się w zestawu narzędzi w celu zweryfikowania środki bezpieczeństwa i Przeczytaj więcej informacji o tym, jak to działa z firmy Thales: [Zarządzania sprzętem klucza w chmurze RMS](https://www.thales-esecurity.com/knowledge-base/white-papers/hardware-key-management-in-the-rms-cloud).

-   **Osobiście:** Wymagane jest, skontaktuj się z Microsoft klienta obsługi usług (CSS) do zaplanowania terminem transferu klucza dla Azure RMS. Do pakietu Microsoft office musi przejść w Redmond, Washington, USA przekierować swoim kluczem dzierżawy na świecie zabezpieczeń Azure RMS.

### <a name="BKMK_BYOK_Internet"></a>Generowanie i przesyłania swoim kluczem dzierżawy — w Internecie
Użyj następujących procedur, aby transfer swoim kluczem dzierżawy w Internecie, a nie przesyłane do firmy Microsoft infrastruktury do transferu klucz dzierżawy osobiście:

-   [Prepare your Internet-connected workstation](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetPrepareWorkstation)

-   [Prepare your disconnected workstation](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_DisconnectedPrepareWorkstation)

-   [Generate your tenant key](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetGenerate)

-   [Prepare your tenant key for transfer](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetPrepareTransfer)

-   [Transfer your tenant key to Azure RMS](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetTransfer)

#### <a name="BKMK_InternetPrepareWorkstation"></a>Przygotowanie stacji roboczej połączony z Internetem
Aby przygotować stacji roboczej, który jest połączony z Internetem, wykonaj następujące kroki 3:

-   [Step 1: Install Windows PowerShell for Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_PrepareInternetConnectedWorkstation1)

-   [Step 2: Get your Azure Active Directory tenant ID](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_PrepareInternetConnectedWorkstation2)

-   [Step 3: Download the BYOK toolset](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_PrepareInternetConnectedWorkstation3)

##### <a name="BKMK_PrepareInternetConnectedWorkstation1"></a>Krok 1: Instalowanie programu Windows PowerShell Azure Rights Management
Połączony z Internetem stacji roboczej pobrać i zainstalować moduł programu Windows PowerShell Azure Rights Management.

> [!NOTE]
> Jeśli wcześniej pobrano ten moduł programu Windows PowerShell, uruchom następujące polecenie, aby sprawdzić, czy numer wersji jest co najmniej 2.1.0.0: `(Get-Module aadrm -ListAvailable).Version`

Aby uzyskać instrukcje instalacji, zobacz [Instalowanie programu Windows PowerShell Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

##### <a name="BKMK_PrepareInternetConnectedWorkstation2"></a>Krok 2: Pobierz identyfikator dzierżawcy Azure Active Directory
Uruchomić środowisko Windows PowerShell z **Uruchom jako administrator** opcji, a następnie uruchom następujące polecenia:

-   Użyj [Connect AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629415.aspx) polecenia cmdlet, aby połączyć się z usługą Azure RMS:

    ```
    Connect-AadrmService
    ```
    Po wyświetleniu monitu, wprowadź swoją [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] dzierżawa poświadczenia administratora (zwykle można będzie używać konta, które jest administratora globalnego dla usługi Azure Active Directory lub usługi Office 365).

-   Użyj [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) polecenia cmdlet, aby wyświetlić konfigurację dzierżawy:

    ```
    Get-AadrmConfiguration
    ```
    Z zestawu wyników należy zapisać identyfikatora GUID z pierwszego wiersza (BPOSId). Jest to identyfikator dzierżawcy Azure Active Directory, konieczne będzie później podczas przygotowywania swoim kluczem dzierżawy dla przekazywania.

-   Użyj [AadrmService Rozłącz](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) polecenia cmdlet rozłączenie z usługi Azure RMS, dopóki użytkownik jest gotowy do przekazania swoim kluczem:

    ```
    Disconnect-AadrmService
    ```

Nie zamykaj okna programu Windows PowerShell.

##### <a name="BKMK_PrepareInternetConnectedWorkstation3"></a>Krok 3: Pobierz zestaw narzędzi BYOK
Przejdź do witryny Microsoft Download Center i [pobrać zestaw narzędzi BYOK](http://go.microsoft.com/fwlink/?LinkId=335781) dla regionu:

|Region|Nazwa pakietu|
|----------|-----------------|
|Ameryka Północna|AzureRMS-BYOK-narzędzia Zjednoczone States.zip|
|Europa|AzureRMS-BYOK-narzędzia Europe.zip|
|Azja|AzureRMS-BYOK-narzędzia AsiaPacific.zip|
Zestaw narzędzi znajdują się następujące informacje:

-   Pakiet klucz wymiany klucza (KEK), który ma jest nazwy zaczynające się **BYOK-KEK-Fully Packaged -**.

-   Pakiet świecie zabezpieczeń, który ma jest nazwy zaczynające się **BYOK-SecurityWorld-Fully Packaged -**.

-   Skrypt języka python o nazwie **verifykeypackage.py**.

-   Plik wykonywalny wiersza polecenia o nazwie **KeyTransferRemote.exe**, plik metadanych o nazwie **KeyTransferRemote.exe.config**, i skojarzonych z nim biblioteki dll.

-   Pakiet Visual C++ Redistributable, o nazwie **vcredist_x64.exe**.

Skopiuj pakiet na dysku USB lub innych magazynu przenośnego.

#### <a name="BKMK_DisconnectedPrepareWorkstation"></a>Przygotowanie stacji roboczej po rozłączeniu
Aby przygotować stacji roboczej, który nie jest połączony z siecią (Internet lub sieci wewnętrznej), wykonaj następujące kroki 2:

-   [Step 1: Prepare the disconnected workstation with Thales HSM](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_PrepareDisconnectedWorkstation1)

-   [Step 2: Install the BYOK toolset on the disconnected workstation](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_PrepareDisconnectedWorkstation2)

##### <a name="BKMK_PrepareDisconnectedWorkstation1"></a>Krok 1: Przygotuj po rozłączeniu stacji roboczej z firmy Thales HSM
Na stacji roboczej po rozłączeniu należy zainstalować to oprogramowanie nCipher (firmy Thales) na komputerze z systemem Windows, a następnie dołącz HSM firmy Thales na tym komputerze.

Upewnij się, że narzędzia firmy Thales znajdują się w ścieżce **(%nfast_home%\bin** i **%nfast_home%\python\bin**). Na przykład wpisz następujące czynności:

```
set PATH=%PATH%;”%nfast_home%\bin”;”%nfast_home%\python\bin”
```
Aby uzyskać więcej informacji, zobacz Podręcznik użytkownika objęte HSM firmy Thales lub w witrynie firmy Thales dla Azure RMS w [http://www.thales-esecurity.com/msrms/cloud](http://www.thales-esecurity.com/msrms/cloud).

##### <a name="BKMK_PrepareDisconnectedWorkstation2"></a>Krok 2: Zainstaluj zestaw narzędzi BYOK na stacji roboczej po rozłączeniu
Skopiować pakiet zestawu narzędzi BYOK z dysku USB lub innych magazynu przenośnego, a następnie wykonaj następujące czynności:

1.  Wyodrębnij pliki z pakietu pobrane do dowolnego folderu.

2.  W tym folderze uruchom vcredist_x64.exe.

3.  Postępuj zgodnie z instrukcjami do instalacji składniki wykonawcze Visual C++ dla programu Visual Studio 2012.

#### <a name="BKMK_InternetGenerate"></a>Generowanie klucza dzierżawcy
Na stacji roboczej po rozłączeniu, wykonaj następujące kroki 3 można wygenerować klucz dzierżawy:

-   [Step 1: Create a security world](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetGenerate1)

-   [Step 2: Validate the downloaded package](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetGenerate2)

-   [Step 3: Create a new key](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetGenerate3)

##### <a name="BKMK_InternetGenerate1"></a>Krok 1: Utwórz świecie zabezpieczeń
Uruchom wiersz polecenia, a następnie uruchom program firmy Thales nowego świata.

```
new-world.exe --initialize --cipher-suite=DLf1024s160mRijndael --module=1 --acs-quorum=2/3
```
Ten program tworzy **świecie zabezpieczeń** pliku % NFAST_KMDATA%\local\world, odnoszącą się w folderze C:\ProgramData\nCipher\Key Settings\User zarządzania. Możesz użyć różnych wartości dla kworum, ale w naszym przykładzie zostanie wyświetlony monit o podanie trzy pustymi kartami i kodu PIN dla każdego z nich. Następnie wszelkie dwie karty muszą mieć dostęp administracyjny do świata zabezpieczeń (kworum określony).  Te karty stają się **ustawić karty Administrator** dla nowego świata zabezpieczeń. Na tym etapie możesz określić hasła lub numeru PIN dla każdego karta ACS lub później dodać za pomocą polecenia.

> [!TIP]
> Aby sprawdzić bieżący stan konfiguracji sieci HSM za pomocą `nkminfo` polecenia.

Następnie należy wykonać następujące czynności:

1.  Zainstalować Dostawcy CNG firmy Thales w sposób opisany w dokumentacji firmy Thales i skonfigurować je do użycia nowego świata zabezpieczeń.

2.  Utwórz kopię zapasową pliku świata w **%nfast_kmdata%\local**. Bezpieczny chronić pliku świecie, karty Administrator i ich numery PIN i upewnij się, że nie jedna osoba ma dostęp do więcej niż jedną kartę.

##### <a name="BKMK_InternetGenerate2"></a>Krok 2: Sprawdź poprawność pobrany pakiet
Ten krok jest opcjonalna, ale zaleca, aby weryfikować następujących czynności:

-   Klucz wymiany klucza, który znajduje się zestaw narzędzi został wygenerowany z oryginalnych HSM firmy Thales.

-   Skrót Azure RMS świata zabezpieczeń, w której znajduje się zestaw narzędzi został wygenerowany w oryginalnych HSM firmy Thales.

-   Nie można wyeksportować jest klucza wymiany klucza.

> [!NOTE]
> Potwierdzenie pobrany pakiet HSM muszą być połączone włączony, a musi mieć świecie zabezpieczeń w nim (np. ten, który został utworzony).

###### Aby sprawdzić pobrany pakiet

1.  Uruchom skrypt verifykeypackage.py przez wiązanie jedną z następujących czynności, zależnie od regionu:

    -   Dla Ameryka Północna:

        ```
        python verifykeypackage.py -k BYOK-KEK-pkg-NA-1 -w BYOK-SecurityWorld-pkg-NA-1
        ```

    -   Gospodarczej:

        ```
        python verifykeypackage.py -k BYOK-KEK-pkg-EU-1 -w BYOK-SecurityWorld-pkg-EU-1
        ```

    -   Dla Azji:

        ```
        python verifykeypackage.py -k BYOK-KEK-pkg-AP-1 -w BYOK-SecurityWorld-pkg-AP-1
        ```

    > [!TIP]
    > Oprogramowanie firmy Thales zawiera interpreterem Python pod adresem %NFAST_HOME%\python\bin

2.  Potwierdź, że widoczne następujące dane, które wskazuje powodzenia weryfikacji: **Wynik:  POWODZENIE**

Ten skrypt weryfikuje łańcuch podpisujący do firmy Thales klucz główny. Skrót ten klucz główny jest osadzony w skrypcie, a jego wartość powinna być **59178a47 de508c3f 291277ee 184f46c4 f1d9c639**. Można również potwierdzić tę wartość osobno na stronie [witryny sieci Web firmy Thales](http://www.thalesesec.com/).

Teraz wszystko jest gotowe utworzyć nowy klucz, który ma zostać swoim kluczem dzierżawy RMS.

##### <a name="BKMK_InternetGenerate3"></a>Krok 3: Utwórz nowy klucz
Generowanie klucza CNG przy użyciu firmy Thales **generatekey** i **cngimport** programy.

Uruchom następujące polecenie, aby wygenerować klucz:

```
generatekey --generate simple type=RSA size=2048 protect=module ident=contosokey plainname=contosokey nvram=no pubexp=
```
Podczas wykonywania tego polecenia, korzystając z tych instrukcji:

-   Rozmiar klucza firma Microsoft zaleca 2048, ale także dokonywanie kluczy RSA 1024-bitowych dla istniejących klientów usług AD RMS, którzy mają takie klucze i są migrację do Azure RMS.

-   Zamień wartość *contosokey* dla **ident** i **plainname** z dowolną wartością ciągu. Aby zminimalizować ogólne koszty administracyjne i zmniejszyć ryzyko błędów, zaleca się używać tej samej wartości dla obu i używać wszystkie znaki na małe litery.

-   Pubexp w tym przykładzie pozostanie puste (domyślnie), ale można określić określone wartości. Aby uzyskać więcej informacji zobacz dokumentację firmy Thales.

Następnie uruchom następujące polecenie, aby zaimportować klucz do CNG:

```
cngimport --import -M --key=contosokey --appname=simple contosokey
```
Podczas wykonywania tego polecenia, korzystając z tych instrukcji:

-   Zastąp *contosokey* o tej samej wartości określonej w parametrze [Step 1: Create a security world](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetGenerate1) z *wygenerować klucz dzierżawy* sekcji.

-   Użyj **- M** opcji, aby klucz jest odpowiednie dla tego scenariusza. Bez tego klucza wynikowy będzie specyficzne dla użytkownika klucz dla bieżącego użytkownika.

To polecenie tworzy plik klucza Stokenizowana w folderze %NFAST_KMDATA%\local o nazwie rozpoczynając od **key_caping_** następuje identyfikatora SID. Na przykład: **key_caping_machine--801c1a878c925fd9df4d62ba001b94701c039e2fb**. Ten plik zawiera zaszyfrowane kluczem.

> [!TIP]
> Możesz zobaczyć bieżący stan konfiguracji kluczy przy użyciu `nkminfo –k` polecenia.

Wykonaj kopię zapasową tego pliku klucza Stokenizowana w bezpiecznej lokalizacji.

> [!IMPORTANT]
> Podczas przesyłania dalej swoim kluczem do Azure RMS, firmy Microsoft nie można wyeksportować ten klucz powrót do, tak aby stał się bardzo ważna bezpiecznie kopii zapasowej Twój świat klucza i zabezpieczeń. Skontaktuj się z firmy Thales dla orientacji i najlepszych rozwiązań tworzenia kopii zapasowych kluczem.

Teraz można przystąpić do przekierować swoim kluczem dzierżawy Azure RMS.

#### <a name="BKMK_InternetPrepareTransfer"></a>Przygotuj swoim kluczem dzierżawy transferu
Na stacji roboczej po rozłączeniu, wykonaj następujące kroki 4 do przygotowania klucz dzierżawy:

-   [Step 1: Create a copy of your key with reduced permissions](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetPrepareTransfer1)

-   [Step 2: Inspect the new copy of the key](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetPrepareTransfer2)

-   [Step 3: Encrypt your key by using Microsoft’s Key Exchange Key](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetPrepareTransfer3)

-   [Step 4: Copy your key transfer package to the Internet-connected workstation](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetPrepareTransfer4)

##### <a name="BKMK_InternetPrepareTransfer1"></a>Krok 1: Utwórz kopię klucza z uprawnieniami zmniejszonej
Aby zmniejszyć uprawnień na swoim kluczem dzierżawy, wykonaj następujące czynności:

-   Wiersz polecenia Uruchom z jedną z następujących czynności, zależnie od regionu:

    -   Dla Ameryka Północna:

        ```
        KeyTransferRemote.exe -ModifyAcls -KeyAppName simple -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-NA-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-NA-1
        ```

    -   Gospodarczej:

        ```
        KeyTransferRemote.exe -ModifyAcls -KeyAppName simple -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-EU-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-EU-1
        ```

    -   Dla Azji:

        ```
        KeyTransferRemote.exe -ModifyAcls -KeyAppName simple -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-AP-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-AP-1
        ```

Podczas wykonywania tego polecenia, należy zastąpić *contosokey* o takiej samej wartości określone w [Step 1: Create a security world](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetGenerate1) z *wygenerować klucz dzierżawy* sekcji.

Użytkownik jest proszony o dodatku karty ACS świecie zabezpieczeń, a jeśli zostały określone, ich hasła lub numeru PIN...

Kiedy polecenie kończy, pojawi się **wynik: Powodzenie** i kopia klucza dzierżawy z uprawnieniami zmniejszonej będzie w pliku o nazwie key_xferacId_*&lt; contosokey &gt;*.

##### <a name="BKMK_InternetPrepareTransfer2"></a>Krok 2: Sprawdź nową kopię klucza
Opcjonalnie można uruchomić firmy Thales narzędzia, aby potwierdzić minimalne uprawnienia dla nowego klucza dzierżawy:

-   aclprint.py:

    ```
    "%nfast_home%\bin\preload.exe" -m 1 -A xferacld -K contosokey "%nfast_home%\python\bin\python" "%nfast_home%\python\examples\aclprint.py"
    ```

-   kmfile-dump.exe:

    ```
    "%nfast_home%\bin\kmfile-dump.exe" "%NFAST_KMDATA%\local\key_xferacld_contosokey"
    ```

Po uruchomieniu te polecenia, Zastąp *contosokey* o takiej samej wartości określone w [Step 1: Create a security world](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetGenerate1) z *wygenerować klucz dzierżawy* sekcji.

##### <a name="BKMK_InternetPrepareTransfer3"></a>Krok 3: Szyfruj klucz za pomocą klucza wymiany klucza firmy Microsoft
Uruchom jeden z następujących poleceń, zależnie od regionu:

-   Dla Ameryka Północna:

    ```
    KeyTransferRemote.exe -Package -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-NA-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-NA-1 -TenantBposId GUID -KeyFriendlyName ContosoFirstkey
    ```

-   Gospodarczej:

    ```
    KeyTransferRemote.exe -Package -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-EU-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-EU-1 -TenantBposId GUID -KeyFriendlyName ContosoFirstkey
    ```

-   Dla Azji:

    ```
    KeyTransferRemote.exe -Package -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-AP-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-AP-1 -TenantBposId GUID -KeyFriendlyName ContosoFirstkey
    ```

Podczas wykonywania tego polecenia, korzystając z tych instrukcji:

-   Zastąp *contosokey* z identyfikatora, który umożliwia generowanie klucza w [Step 1: Create a security world](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetGenerate1) z *wygenerować klucz dzierżawy* sekcji.

-   Zastąp *identyfikatora GUID* z usługą Active Directory systemu Azure dzierżawa identyfikator, który jest pobierana w [Step 2: Get your Azure Active Directory tenant ID](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_PrepareInternetConnectedWorkstation2) z *Przygotowanie stacji roboczej połączony z Internetem* sekcji.

-   Zastąp *ContosoFirstKey* z etykietą, który zostanie użyty dla nazwy pliku wyjściowego.

Po zakończeniu tego procesu pomyślnie go Wyświetla **wynik: Powodzenie** i będzie ona nowy plik w bieżącym folderze o nazwie następujące: TransferPackage -*ContosoFirstkey*.byok

##### <a name="BKMK_InternetPrepareTransfer4"></a>Krok 4: Kopiuj do pakietu klucza transferu połączony z Internetem na stacji roboczej
Użyj dysku USB lub innych magazynu przenośnego, aby skopiować plik wyjściowy z poprzedniego kroku (KeyTransferPackage -*ContosoFirstkey*.byok) tej stacji roboczej połączony z Internetem.

> [!NOTE]
> Użyj wskazówki dotyczące zabezpieczeń, aby chronić pliku, ponieważ zawiera on klucza prywatnego.

#### <a name="BKMK_InternetTransfer"></a>Przekierować swoim kluczem dzierżawy Azure RMS
Na stacji roboczej połączony z Internetem wykonaj następujące 3 kroki przekierować Twój nowy klucz dzierżawy Azure RMS:

-   [Step 1: Connect to Azure RMS](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetTransfer1)

-   [Step 2: Upload the key package](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetTransfer2)

-   [Step 3: Enumerate your tenant keys – as needed](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_InternetTransfer3)

##### <a name="BKMK_InternetTransfer1"></a>Krok 1: Nawiązać Azure RMS
Wróć do okna programu Windows PowerShell, a następnie wpisz następujące polecenie:

1.  Połącz się ponownie [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] usługi:

    ```
    Connect-AadrmService
    ```

2.  Użyj [Get-AadrmKeys](http://msdn.microsoft.com/library/windowsazure/dn629420.aspx) polecenia cmdlet, aby wyświetlić bieżącą konfigurację klucza dzierżawy:

    ```
    Get-AadrmKeys
    ```

##### <a name="BKMK_InternetTransfer2"></a>Krok 2: Przekaż pakiet z kluczem
Użyj [AadrmKey Dodaj](http://msdn.microsoft.com/library/windowsazure/dn629418.aspx) polecenia cmdlet można przekazać pakietu transferu klucza, który skopiowano z po rozłączeniu stacji roboczej:

```
Add-AadrmKey –KeyFile <PathToPackageFile> -Verbose
```
> [!WARNING]
> Zostanie wyświetlony monit o potwierdzenie tej akcji. Należy określić, że ta akcja nie będzie można cofnąć. Podczas ładowania klucza dzierżawy, staje się automatycznie klucz podstawowy dzierżawy organizacji i użytkowników rozpocznie się do użycia tego klucza dzierżawy po ich ochrony dokumentów i plików.

Jeśli przekazywanie zakończy się pomyślnie, zostanie wyświetlony następujący komunikat: **Usługi zarządzania prawami pomyślnie dodany klucz.**

Oczekiwany opóźnienia replikacji zmiana propagowane do wszystkich [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] centrów danych.

##### <a name="BKMK_InternetTransfer3"></a>Krok 3: Wyliczanie kluczy dzierżawy — w razie potrzeby
Ponownie użyć polecenia cmdlet Get-AadrmKeys, aby sprawdzić zmiany w swoim kluczem dzierżawy i zawsze, gdy chcesz wyświetlić listę kluczy dzierżawy. Klucz początkowego dzierżawy, generowany dla Ciebie firmy Microsoft i klucze dzierżawy, które zostały dodane, między innymi klucze dzierżawy wyświetlane:

```
Get-AadrmKeys
```
Klucz dzierżawy, który jest oznaczony jako **Active** jest aktualnie używany do ochrony dokumentów i plików organizacji.

Ukończono wszystkie czynności wymagane dla Przesuń własny klucz przez Internet, można przejść do [Next steps](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_NextSteps).

### <a name="BKMK_BYOK_InPerson"></a>Generowanie i przesyłania swoim kluczem dzierżawy — osobiście
Użyj następujących procedur, jeśli nie chcesz przenosić swoim kluczem dzierżawy przez Internet, ale zamiast tego transferu swoim kluczem dzierżawy osobiście.

-   [Generate your tenant key](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_GenerateKey)

-   [Transfer your tenant key to Azure RMS](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Transfer)

#### <a name="BKMK_GenerateKey"></a>Generowanie klucza dzierżawcy
Aby wygenerować klucz dzierżawy, wykonaj następujące kroki 3:

-   [Step 1: Prepare a workstation with Thales HSM](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_GenerateYourKey1)

-   [Step 2: Create a security world](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_GenerateYourKey2)

-   [Step 3: Create a new key](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_GenerateYourKey3)

##### <a name="BKMK_GenerateYourKey1"></a>Krok 1: Przygotowanie stacji roboczej z firmy Thales HSM
Zainstaluj to oprogramowanie nCipher (firmy Thales) na komputerze z systemem Windows. Dołącz HSM firmy Thales na tym komputerze. Upewnij się, że narzędzia firmy Thales znajdują się w ścieżce. Aby uzyskać więcej informacji, zobacz Podręcznik użytkownika objęte HSM firmy Thales lub w witrynie firmy Thales dla Azure RMS w [http://www.thales-esecurity.com/msrms/cloud](http://www.thales-esecurity.com/msrms/cloud).

##### <a name="BKMK_GenerateYourKey2"></a>Krok 2: Utwórz świecie zabezpieczeń
Uruchom wiersz polecenia, a następnie uruchom program firmy Thales nowego świata.

```
new-world.exe --initialize --cipher-suite=DLf1024s160mRijndael --module=1 --acs-quorum=2/3
```
Ten program tworzy **świecie zabezpieczeń** pliku % NFAST_KMDATA%\local\world, odnoszącą się w folderze C:\ProgramData\nCipher\Key Settings\User zarządzania. Możesz użyć różnych wartości dla kworum, ale w naszym przykładzie zostanie wyświetlony monit o podanie trzy pustymi kartami i kodu PIN dla każdego z nich. Następnie wszelkie dwie karty będzie uzyska pełny dostęp do świata zabezpieczeń.  Te karty stają się **ustawić karty Administrator** dla nowego świata zabezpieczeń.

Następnie należy wykonać następujące czynności:

1.  Zainstalować Dostawcy CNG firmy Thales w sposób opisany w dokumentacji firmy Thales i skonfigurować je do użycia nowego świata zabezpieczeń.

2.  Wykonaj kopię zapasową pliku świecie. Bezpieczny chronić pliku świecie, karty Administrator i ich numery PIN i upewnij się, że nie jedna osoba ma dostęp do więcej niż jedną kartę.

Teraz wszystko jest gotowe utworzyć nowy klucz, który ma zostać swoim kluczem dzierżawy RMS.

##### <a name="BKMK_GenerateYourKey3"></a>Krok 3: Utwórz nowy klucz
Generowanie klucza CNG przy użyciu firmy Thales **generatekey** i **cngimport** programy.

Uruchom następujące polecenie, aby wygenerować klucz:

```
generatekey --generate simple type=RSA size=2048 protect=module ident=contosokey plainname=contosokey nvram=no pubexp=
```
Podczas wykonywania tego polecenia, korzystając z tych instrukcji:

-   Rozmiar klucza firma Microsoft zaleca 2048, ale także dokonywanie kluczy RSA 1024-bitowych dla istniejących klientów usług AD RMS, którzy mają takie klucze i są migrację do Azure RMS.

-   Zamień wartość *contosokey* dla **ident** i **plainname** z dowolną wartością ciągu. Aby zminimalizować ogólne koszty administracyjne i zmniejszyć ryzyko błędów, zaleca się używać tej samej wartości dla obu i używać wszystkie znaki na małe litery.

-   Pubexp w tym przykładzie pozostanie puste (domyślnie), ale można określić określone wartości. Aby uzyskać więcej informacji zobacz dokumentację firmy Thales.

Następnie uruchom następujące polecenie, aby zaimportować klucz do CNG:

```
cngimport --import –M --key=contosokey --appname=simple contosokey
```
Podczas wykonywania tego polecenia, korzystając z tych instrukcji:

-   Zastąp *contosokey* z tą samą wartością określoną w kroku 1.

-   Użyj **- M** opcji, aby klucz jest odpowiednie dla tego scenariusza. Bez tego klucza wynikowy będzie specyficzne dla użytkownika klucz dla bieżącego użytkownika.

To polecenie tworzy plik klucza Stokenizowana w folderze %NFAST_KMDATA%\local o nazwie rozpoczynając od **key_caping_** następuje identyfikatora SID. Na przykład: **key_caping_machine--801c1a878c925fd9df4d62ba001b94701c039e2fb**. Ten plik zawiera zaszyfrowane kluczem.

Wykonaj kopię zapasową tego pliku klucza Stokenizowana w bezpiecznej lokalizacji.

> [!IMPORTANT]
> Później przekierować swoim kluczem Azure RMS, firma Microsoft ma nie będzie kopię klucza. Oznacza to, że nikt nie można pobrać klucz z HSM w firmie Microsoft. Umożliwia to zachować wyłącznego kontrolę nad swoim kluczem dzierżawy. Z tego powodu staje się bardzo ważna bezpiecznie kopii zapasowej Twój świat klucza i zabezpieczeń. Skontaktuj się z firmy Thales dla orientacji i najlepszych rozwiązań tworzenia kopii zapasowych kluczem.

Teraz można przystąpić do przekierować swoim kluczem dzierżawy Azure RMS.

#### <a name="BKMK_Transfer"></a>Przekierować swoim kluczem dzierżawy Azure RMS
Po wygenerowaniu własny klucz, użytkownik musi przesłać do Azure RMS przed jego użyciem. Ten transfer najwyższy poziom zabezpieczeń, jest to proces wymagający ręcznej wymagające podnoszenia Microsoft Office w Redmond, Washington, USA. Aby ukończyć ten proces, wykonaj następujące kroki 3:

-   [Step 1: Bring your key to Microsoft](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_TransferYourKey1)

-   [Step 2: Transfer your key to the Window Azure RMS security world](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_TransferYourKey2)

-   [Step 3: Closing procedures](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_TransferYourKey3)

###### Krok 1: Wykorzystaj klucz do firmy Microsoft

-   Skontaktuj się z pomocą Microsoft klienta obsługi usług (CSS) do zaplanowania klucz przenieść termin dla Azure RMS. Przesuń następujących do firmy Microsoft w Redmond:

    -   Kworum administracyjnej karty. Po wykonaniu poprzedniego instrukcje w [Step 2: Create a security world](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_GenerateYourKey2), są dwa trzy karty.

    -   Personel uprawniony do karty administracyjną i kodów PIN, zwykle dwie (jeden dla każdej karty).

    -   Świecie zabezpieczeń pliku (% NFAST_KMDATA%\local\world) na dysku USB.

    -   Stokenizowana klucza pliku na dysku USB.

###### Krok 2: Transfer klucz w świecie zabezpieczeń systemu Windows Azure RMS

1.  Gdy przychodzą w firmie Microsoft do transferu swoim kluczem następujące konsekwencje:

    -   Firma Microsoft zapewnia offline stacji roboczej, która ma HSM firmy Thales, dołączyć, zainstalowane oprogramowanie firmy Thales oraz wstępnie załadować pliku Azure RMS zabezpieczeń świecie do folderu C:\Temp\Destination.

    -   Na tej stacji roboczej ładowania plików świecie zabezpieczeń i Stokenizowana plik klucza z dysku USB do folderu C:\Temp\Source.

    -   Azure RMS operatorów bezpiecznego transferu klucz w świecie zabezpieczeń Azure RMS za pomocą narzędzi firmy Thales.

    Ten proces będzie wyglądać podobnie do następujących, gdzie ostatni parametr klucz xfer im w tym przykładzie zostanie zastąpiony przez nazwy pliku klucza Stokenizowana:

    **C:\ &gt; mk — reprogram.exe — c:\Temp\Destination właściciela Dodaj c:\Temp\Source**

    **C:\ &gt; klucz xfer-im.exe c:\Temp\Source c:\Temp\Destination — c:\Temp\Source\key_caping_machine--801c1a878c925fd9df4d62ba001b94701c039e2fb modułu**

2.  Przechowywany MK poprosi możesz i operatorów Azure RMS dodatku ich odpowiednich karty Administrator i kodu PIN. Te polecenia danych wyjściowych w pliku klucza Stokenizowana w C:\Temp\Destination zawierający klucz chronionych usługami Azure RMS świecie zabezpieczeń.

###### Krok 3: Zamykanie procedury

-   Twoja obecność operatorów Azure RMS wykonaj następujące czynności:

    -   Uruchom narzędzia, które firma Microsoft wprowadziła we współpracy z firmy Thales, który usuwa dwa uprawnień: Uprawnienie do odzyskania klucza, a uprawnienia do zmiany uprawnień. Po wykonaniu tej czynności, ta kopia klucza jest zablokowany w świecie zabezpieczeń Azure RMS. Firmy Thales HSM uniemożliwi operatorów Azure RMs z ich karty Administrator odzyskać kopii zwykły tekst klucza.

    -   Skopiuj plik klucza wynikowy na dysku USB można później przekazać do usługi Azure RMS.

    -   Fabryka resetowania HSM i wyczyść czystego stacji roboczej.

Ukończono wszystkie czynności wymagane dla doprowadzić własny klucz osobiście i wrócić do swojej organizacji dla następnych kroków.

## <a name="BKMK_NextSteps"></a>Następne kroki

1.  Uruchom użyć tego samego klucza dzierżawy:

    -   Jeśli nie zostało to jeszcze zrobione, należy teraz uaktywnić Rights Management tak, aby uruchomić organizacji używania usług RMS. Użytkownicy od razu przystąpić do użycia w swoim kluczem dzierżawy (zarządzanych przez firmę Microsoft lub zarządzane przez użytkownika).

        Aby uzyskać więcej informacji o aktywacji, zobacz [Aktywowanie Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md).

    -   Jeśli zostały już aktywowany Rights Management, a następnie decyzję o klucz dzierżawcy zarządzania, użytkownicy stopniowo przejście ze starego klucza dzierżawy do nowego klucza dzierżawy, a to rozłożona przejście może zająć kilka tygodni, aby zakończyć. Dokumenty i pliki, które są chronione przy użyciu starego klucza dzierżawy pozostaje dostępne dla autoryzowanych użytkowników.

2.  Należy rozważyć włączyć rejestrowanie użycia, które dzienniki każdej transakcji, który będzie wykonywać RMS.

    Jeśli chcesz zarządzać klucz dzierżawy, rejestrowanie zawiera informacje o korzystaniu z kluczem dzierżawy. W poniższym przykładzie plik dziennika w programie Excel Zobacz gdzie **odszyfrować** i **SignDigest** Pokaż typy żądań jest używany klucz dzierżawy.

    ![](../Image/RMS_Logging.gif)

    Aby uzyskać więcej informacji na temat rejestrowania użycia, zobacz [Rejestrowanie i analizy użycia zarządzania prawami Azure](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md).

3.  Obsługa swoim kluczem dzierżawy.

    Aby uzyskać więcej informacji, zobacz [Operacje dla klucza dzierżawcy zarządzania prawami systemu Azure](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md).

## Zobacz też
[Konfigurowanie Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

