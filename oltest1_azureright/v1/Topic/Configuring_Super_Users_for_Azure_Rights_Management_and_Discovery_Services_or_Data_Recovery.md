---
description: na
keywords: na
title: Configuring Super Users for Azure Rights Management and Discovery Services or Data Recovery
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: acb4c00b-d3a9-4d74-94fe-91eeb481f7e3
---
# Konfigurowanie administrator&#243;w systemu Azure Rights Management i odnajdywania usług lub odzyskiwania danych
Funkcja administratorów firmy Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS) zapewnia, że autoryzowane osoby i usługi można zawsze odczytać i sprawdzić dane, które chroni Azure RMS w organizacji. I w razie potrzeby usunąć ochronę lub zmienić ustawienia ochrony, który wcześniej został zastosowany. Jesteś administratorem ma zawsze pełne prawa właściciela dla wszystkich licencji użytkowania, które zostało przyznane przez dzierżawy usług RMS w organizacji. Ta możliwość jest nazywane "uzasadnienie nad danymi" i jest czynnikiem w odpowiedniej kontroli danych w organizacji. Na przykład należy użyć tej funkcji dla każdego z następujących sytuacji:

-   Pracownik pozostawia organizacji i potrzebne do odczytu plików, które są chronione.

-   IT administrator musi usunąć bieżące zasady ochrony skonfigurowanego dla plików i zastosować nowe zasady ochrony.

-   Exchange Server musi skrzynki pocztowe indeks dla operacji wyszukiwania.

-   Masz istniejące usługi IT rozwiązań zapobiegania (DLP) utraty danych, szyfrowania zawartości bramy (CEG) i produktów narzędzia chroniące przed złośliwym oprogramowaniem, które należy sprawdzić pliki, które są już zabezpieczone.

-   Musisz zbiorczo odszyfrowywania plików dla inspekcji, prawnych lub innych przyczyn zgodności.

Domyślnie nie jest włączona funkcja administratorów, a żaden użytkownik nie jest przypisany do tej roli. Jest włączona dla Ciebie automatycznie Jeśli skonfigurować łącznik Rights Management for Exchange i nie jest wymagane dla usługi standardowe, które Uruchom Exchange Online, SharePoint Online lub SharePoint Server.

Jeśli musisz ręcznie włączyć funkcję administratorów, należy użyć polecenia cmdlet programu Windows PowerShell [AadrmSuperUserFeature Włącz](https://msdn.microsoft.com/library/azure/dn629400.aspx), a następnie przypisanie użytkowników (lub konta usługi), zgodnie z potrzebami przy użyciu [AadrmSuperUser Dodaj](https://msdn.microsoft.com/library/azure/dn629411.aspx) polecenia cmdlet. Masz jednego lub wielu administratorów dla organizacji, ale należy dodać poszczególnych użytkowników. grupy nie są obsługiwane.

> [!NOTE]
> Jeśli nie został jeszcze zainstalowany moduł programu Windows PowerShell dla [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], zobacz [Instalowanie programu Windows PowerShell Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

Najważniejsze wskazówki dotyczące zabezpieczeń dla funkcji administratorów:

-   Ograniczenia i Monitoruj administratorów, którzy są przypisane administratora globalnego dla dzierżawy usługi Office 365 lub Azure RMS lub który przypisano rolę GlobalAdministrator przy użyciu [AadrmRoleBasedAdministrator Dodaj](https://msdn.microsoft.com/library/azure/dn629417.aspx) polecenia cmdlet. Ci użytkownicy mogą włączyć funkcję administratorów przypisywania użytkowników (i sami) jako administratorów i potencjalnie odszyfrować wszystkie pliki, które chroni swojej organizacji.

-   Aby zobaczyć, którzy użytkownicy i kont usługi są przypisywane jako administratorów, użyj [polecenie cmdlet Get-AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629408.aspx).  Podobnie jak wszystkie akcje Administracja, włączenie lub wyłączenie funkcji super i dodawanie lub usuwanie administratorów są rejestrowane i mogą podlegać inspekcji przy użyciu [Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx) polecenia. W przypadku administratorów odszyfrować pliki, ta akcja jest rejestrowane i mogą podlegać inspekcji z [Rejestrowanie użycia](https://technet.microsoft.com/library/dn529121.aspx).

-   Jeśli funkcja administratorów nie ma potrzeby codzienne usług, należy włączyć funkcję tylko wtedy, gdy jest potrzebna i wyłącz ją ponownie za pomocą [Disable AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629428.aspx) polecenia cmdlet.

Następujące wyodrębniania dzienników przedstawia niektóre wpisy przykład z za pomocą polecenia cmdlet Get-AadrmAdminLog. W tym przykładzie administrator Contoso Ltd potwierdza, że funkcja administratorów jest wyłączona, dodaje Richard Simone jako administratorów, sprawdza, czy Richard tylko administratorów skonfigurowany dla Azure RMS i następnie włączy tę funkcję administratorów, tak aby Richard teraz może odszyfrować pliki, które zostały objęte ochroną przez pracownika, który ma teraz pozostanie firmy.

`2015-08-01T18:58:20	admin@contoso.com	GetSuperUserFeatureState	Passed	Disabled`
`2015-08-01T18:59:44	admin@contoso.com	AddSuperUser -id rsimone@contoso.com	Passed	True`
`2015-08-01T19:00:51	admin@contoso.com	GetSuperUser	Passed	rsimone@contoso.com`
`2015-08-01T19:01:45	admin@contoso.com	SetSuperUserFeatureState -state Enabled	Passed	True`

## <a name="BKMK_RMSProtectionModule"></a>Opcje obsługi skryptów dla administratorów
Często ktoś, któremu przypisano administratorów dla [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] należy usunąć ochrony z wielu plików w wielu lokalizacjach. Mimo że jest to możliwe, w tym celu ręcznie, jest bardziej wydajne (i często niezawodny) to skryptu. Aby to zrobić, [ponownie pobrać RMS ochrony](http://www.microsoft.com/en-us/download/details.aspx?id=47256). Następnie za pomocą  [RMSFile nie Chroń](https://msdn.microsoft.com/library/azure/mt433200.aspx) polecenia cmdlet, i [RMSFile Chroń](https://msdn.microsoft.com/library/azure/mt433201.aspx)   polecenia cmdlet zgodnie z wymaganiami.

> [!IMPORTANT]
> Mimo to narzędzie ochrony RMS jest przeznaczony dla administratorów zbiorczym nie Chroń pliki na potrzeby odzyskiwania, bieżącej wersji narzędzia nie obsługuje uwierzytelniania użytkowników dla Azure RMS. Do momentu rozwiązania tego ograniczenia, trzeba użyć konta głównego usługi uwierzytelnić się Azure RMS przed usunięciem ochrony z plików.  Aby uzyskać więcej informacji oraz instrukcje, zobacz [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/azure/mt433202.aspx).

Aby uzyskać więcej informacji na temat tych apletów poleceń, zobacz [polecenia cmdlet ochrony RMS](https://msdn.microsoft.com/library/azure/mt433195.aspx).

> [!NOTE]
> Moduł RMSProtection Windows PowerShell, dostarczanego wraz z narzędziem ochrony RMS różni się od oraz uzupełnia głównym [programu Windows PowerShell w module Azure Rights Management](https://technet.microsoft.com/library/jj585027.aspx). Program obsługuje zarówno Azure RMS i AD RMS.

## Zobacz też
[Konfigurowanie Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

