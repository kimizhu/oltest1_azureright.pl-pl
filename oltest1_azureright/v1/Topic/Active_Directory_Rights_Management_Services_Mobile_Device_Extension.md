---
description: na
keywords: na
title: Active Directory Rights Management Services Mobile Device Extension
search: na
ms.date: na
ms.tgt_pltfrm: na
ms.assetid: a69ead9d-7dd3-4b38-9830-4728e9757341
robots: noindex,nofollow
---
# Rozszerzenie usług Active Directory Rights Management (AD&#160;RMS) dla urządzeń przenośnych
Rozszerzenie usług Active Directory Rights Management (AD RMS) dla urządzeń przenośnych działa, korzystając z istniejącego wdrożenia usług AD RMS. Pozwala to użytkownikom korzystającym z urządzeń przenośnych zabezpieczać poufne dane i uzyskiwać do nich dostęp, jeśli ich urządzenie obsługuje najnowszego klienta usług RMS i korzysta z aplikacji obsługujących usługi RMS. Użytkownicy takich urządzeń mogą wykonywać na przykład następujące czynności:

-   Korzystać z aplikacji RMS sharing do uzyskiwania dostępu do poufnych plików w różnych formatach (w tym txt, csv i xml).

-   Korzystać z aplikacji RMS sharing do uzyskiwania dostępu do poufnych plików obrazów (w tym jpg, gif i tif).

-   Korzystać z aplikacji RMS sharing do otwierania zabezpieczonych plików (w formacie pfile).

-   Korzystać z aplikacji RMS sharing do ochrony plików obrazów na ich urządzeniach.

-   Korzystać z przeglądarki plików PDF z obsługą usług RMS dla urządzeń przenośnych do otwierania plików PDF chronionych za pomocą aplikacji RMS sharing dla systemu Windows lub innej aplikacji z obsługą usług RMS.

-   Korzystać z aplikacji z obsługą usług RMS innych dostawców, które obsługują typy plików obsługiwane przez usługi RMS.

-   Korzystać z wewnętrznie opracowanych aplikacji z obsługą usług RMS napisanych przy użyciu zestawu SDK usług RMS.

> [!NOTE]
> Możesz pobrać aplikację RMS sharing ze strony [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) w witrynie internetowej firmy Microsoft.
> 
> Aby uzyskać więcej informacji na temat różnych typów plików obsługiwanych przez usługi RMS, zobacz [Obsługiwane typy plików i rozszerzenia nazw plików](http://technet.microsoft.com/library/dn339003.aspx) w przewodniku administratora aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Rights Management.

Rozszerzenie dla urządzeń przenośnych nie jest potrzebne do otwierania i tworzenia chronionych wiadomości e-mail na urządzeniach, jeśli aplikacja do obsługi poczty obsługuje protokół Exchange ActiveSync IRM. Natywna obsługa usług RMS i urządzeń przenośnych została wprowadzona w programie Exchange 2010 z dodatkiem Service Pack 1.

Użyj następujących sekcji, aby wdrożyć rozszerzenie usług Active Directory Rights Management (AD RMS) dla urządzeń przenośnych:

-   [Prerequisites for the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_Preqs)

    -   [Configuring AD FS for the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_ADFS)

    -   [Configuring AD FS for the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_ADFS)

-   [Specifying the DNS SRV records for the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_SRV)

-   [Deploying the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_Deploy)

## <a name="BKMK_Preqs"></a>Wymagania wstępne rozszerzenia usług AD RMS dla urządzeń przenośnych
Przed zainstalowaniem rozszerzenia usług AD RMS dla urządzeń przenośnych upewnij się, że spełniono następujące wymagania.

|Wymaganie|Więcej informacji|
|-------------|---------------------|
|Istniejące wdrożenie usług AD RMS w systemie Windows Server 2012 R2 lub Windows Server 2012. **Note:** Usługi AD RMS muszą korzystać z pełnej bazy danych opartej na programie Microsoft SQL Server znajdującej się na osobnym serwerze, a nie wewnętrznej bazy systemu Windows na tym samym serwerze (ta druga konfiguracja jest często używana na potrzeby testowania).|Aby zapoznać się z dokumentacją dotyczącą usług AD RMS, zobacz [Usługi Active Directory Rights Management](http://technet.microsoft.com/library/hh831364.aspx) w bibliotece systemu Windows Server.|
|Usługi AD FS wdrożone w systemie Windows Server 2012 R2|Aby zapoznać się z dokumentacją dotyczącą usług AD FS, zobacz [Przewodnik wdrażania usług Windows Server 2012 R2 AD FS](http://technet.microsoft.com/library/dn486820.aspx) w bibliotece systemu Windows Server.<br /><br />Usługi AD FS muszą być skonfigurowane na potrzeby rozszerzenia dla urządzeń przenośnych. Aby uzyskać instrukcje, zobacz sekcję [Configuring AD FS for the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_ADFS) w tym temacie.|
|Rekordy SRV w systemie DNS|Utwórz co najmniej jeden rekord SRV w domenie lub domenach firmy:<br /><br />-   Jeden rekord dla każdego sufiksu domeny adresów e-mail, z którego będą korzystali użytkownicy<br />-   Jeden rekord dla każdej nazwy FQDN używanej przez klastry usług RMS na potrzeby ochrony zawartości<br /><br />Gdy użytkowcy podają swoje adresy e-mail na urządzeniach przenośnych, sufiks domeny określa, czy ma być używana infrastruktura usług AD RMS, czy usługa Azure RMS. Po znalezieniu rekordu SRV klienci są przekierowywani do serwera usług AD RMS odpowiadającemu danemu adresowi URL.<br /><br />Gdy użytkownicy uzyskują dostęp do chronionej zawartości za pomocą urządzeń przenośnych, aplikacja klienta sprawdza rekord DNS zgodny z nazwą FQDN w adresie URL klastra chroniącego zawartość. Urządzenie jest następnie przekierowywane do klastra usług AD RMS określonego w rekordzie DNS i pobiera licencję w celu otwarcia zawartości. W większości przypadków klaster usług RMS będzie tym samym klastrem usług RMS, który chroni zawartość.<br /><br />Aby uzyskać informacje na temat sposobu określania rekordów SRV, zobacz sekcję [Specifying the DNS SRV Records for the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_SRV) w tym temacie.|
|Aktualnie obsługiwani klienci:<br /><br />-   Urządzenia z systemem Android z najnowszą wersją aplikacji RMS sharing dla systemu Android|Minimalna wersja systemu Android to 4.0.3.<br /><br />Pobierz aplikację RMS sharing dla systemu Android z [witryny Microsoft Connect](https://connect.microsoft.com/site1170/Downloads) i pobierz ją lokalnie na urządzenie.|

### <a name="BKMK_ADFS"></a>Konfigurowanie usług AD FS na potrzeby rozszerzenia usług AD RMS dla urządzeń przenośnych
Skonfiguruj usługi AD FS, a następnie autoryzuj aplikację RMS sharing dla systemu Android.

##### Krok 1. Aby skonfigurować usługi AD FS

-   Możesz uruchomić skrypt środowiska Windows PowerShell w celu automatycznego skonfigurowania usług AD FS do obsługi rozszerzenia usług AD RMS dla urządzeń przenośnych lub ręcznie określić opcje i wartości konfiguracji:

    -   Aby automatycznie skonfigurować usługi AD FS, skopiuj i wklej następujący kod do skryptu środowiska Windows PowerShell, a następnie go uruchom:

        ```
        # This Script Configures the Microsoft Rights Management Mobile Device Extension and Claims used in the ADFS Server

        # Check if Microsoft Rights Management Mobile Device Extension is configured on the Server 
        $CheckifConfigured = Get-AdfsRelyingPartyTrust -Identifier "api.rms.rest.com"
        if ($CheckifConfigured)
        {
        Write-Host "api.rms.rest.com Identifer used for Microsoft Rights Management Mobile Device Extension is already configured on this Server"
        Write-Host $CheckifConfigured 
        }
        else
        {
        Write-Host "Configuring  Microsoft Rights Management Mobile Device Extension "

        # TransformaRules used by Microsoft Rights Management Mobile Device Extension
        # Claims: E-mail, UPN and ProxyAddresses
        $TransformRules = @"
        @RuleTemplate = "LdapClaims"
        @RuleName = "Jwt Token"
        c:[Type ==
        "http://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname",
        Issuer == "AD AUTHORITY"]
         => issue(store = "Active Directory", types =
        ("http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress",
        "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn",
        "http://schemas.xmlsoap.org/claims/ProxyAddresses"), query =
        ";mail,userPrincipalName,proxyAddresses;{0}", param = c.Value);

        @RuleTemplate = "PassThroughClaims"
        @RuleName = "JWT pass through"
        c:[Type == "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress"]
         => issue(claim = c);

        @RuleTemplate = "PassThroughClaims"
        @RuleName = "JWT pass through"
        c:[Type == "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"]
         => issue(claim = c);

        @RuleTemplate = "PassThroughClaims"
        @RuleName = "JWT pass through Proxy addresses"
        c:[Type == "http://schemas.xmlsoap.org/claims/ProxyAddresses"]
         => issue(claim = c);
        "@

        # AuthorizationRules used by Microsoft Rights Management Mobile Device Extension
        # Allow All users
        $AuthorizationRules = @"
        @RuleTemplate = "AllowAllAuthzRule"
         => issue(Type = "http://schemas.microsoft.com/authorization/claims/permit",
        Value = "true");
        "@

        # Add a Relying Part Truest with Name -"Microsoft Rights Management Mobile Device Extension" Identifier "api.rms.rest.com"
        Add-ADFSRelyingPartyTrust -Name "Microsoft Rights Management Mobile Device Extension" -Identifier "api.rms.rest.com" -IssuanceTransformRules $TransformRules -IssuanceAuthorizationRules  $AuthorizationRules

        Write-Host "Microsoft Rights Management Mobile Device Extension Configured"
        }
        ```

    -   Aby ręcznie skonfigurować usługi AD FS, użyj następujących ustawień:

        |Konfiguracja|Wartość|
        |----------------|-----------|
        |**Relacja zaufania jednostki uzależnionej**|api.rms.rest.com|
        |**Reguła oświadczenia**|**Magazyn atrybutów**:  Active Directory<br /><br />**E Mail-Addresses**:  E-Mail-Address<br /><br />**User-Principal-Name**:  UPN<br /><br />**Proxy-Address**:  https://schemas.xmlsoap.org/claims/ProxyAddresses|

##### Krok 2. Autoryzowanie aplikacji RMS sharing dla systemu Android

-   Uruchom następujące polecenie środowiska Windows PowerShell, aby dodać obsługę urządzeń z systemem Android:

    ```
    Add-AdfsClient -Name "RMSsharingAndroid" -ClientId "com.microsoft.ipviewer" -RedirectUri @("com.microsoft.ipviewer://authorize")
    ```

### <a name="BKMK_SRV"></a>Określanie rekordów DNS SRV na potrzeby rozszerzenia usług AD RMS dla urządzeń przenośnych
Musisz utworzyć rekordy DNS SRV dla każdej domeny poczty e-mail, z której korzystają użytkownicy. Jeśli wszyscy użytkownicy korzystają z domen podrzędnych pojedynczej domeny głównej i wszyscy z tej ciągłej przestrzeni nazw korzystają z tego samego klastra usług RMS, możesz dodać tylko jeden rekord SRV w domenie nadrzędnej, a usługi RMS znajdą odpowiednie rekordy DNS.

Rekordy SRV mają następujący format: _rmsdisco._http._tcp. *&lt;sufiks_e-mail&gt;**&lt;numer_portu&gt;**&lt;FQDN_klastra_RMS&gt;*

Na przykład jeśli w organizacji są używane następujące adresy e-mail:

-   użytkownik@contoso.com

-   użytkownik@sales.contoso.com

-   użytkownik@fabrikam.com

- i nie ma żadnych innych domen podrzędnych dla domeny contoso.com korzystających z klastra RMS innego niż ten o nazwie **rmsserver.contoso.com**, utwórz dwa rekordy DNS SRV o następujących wartościach:

-   _rmsdisco._http._tcp.contoso.com 443 rmsserver.contoso.com

-   _rmsdisco._http._tcp.fabrikam.com 443 rmsserver.contoso.com

Oprócz tych rekordów DNS SRV dla domen poczty e-mail utwórz rekord DNS SRV w domenach użytkowników. Rekord musi określać adresy URL klastra usług RMS chroniącego zawartość. Każdy plik chroniony za pomocą usług RMS zawiera adres URL klastra chroniącego ten plik. Urządzenia przenośne używają rekordu DNS SRV oraz nazwy FQDN adresu URL określonego w rekordzie do znalezienia odpowiedniego klastra usług RMS, który może obsługiwać urządzenia przenośne.

Jeśli na przykład klaster RMS to **rmsserver.contoso.com**, utwórz rekord DNS SRV o następujących wartościach: **_rmsdisco._http._tcp.rmsserver.contoso.com 443 rmsserver.contoso.com**

## <a name="BKMK_Deploy"></a>Wdrażanie rozszerzenia usług AD RMS dla urządzeń przenośnych
Przed zainstalowaniem rozszerzenia usług AD RMS dla urządzeń przenośnych upewnij się, że spełniono wymagania wstępne określone w poprzedniej sekcji oraz że znasz adres URL serwera usług AD FS. Następnie wykonaj następujące czynności:

1.  Pobierz rozszerzenie usług AD RMS dla urządzeń przenośnych z [witryny Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=397245).

2.  Uruchom program Setup.exe, aby uruchomić Kreatora instalacji rozszerzenia usług Active Directory Rights Management dla urządzeń przenośnych.

3.  Po wyświetleniu monitu wprowadź adres URL wcześniej skonfigurowanego serwera usług AD FS.

4.  Ukończ działanie kreatora.

Uruchom tego kreatora na wszystkich węzłach usług RMS w klastrze.

