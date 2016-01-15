---
description: na
keywords: na
title: Installing Windows PowerShell for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0d665ed6-b1de-4d63-854a-bc57c1c49844
---
# Instalowanie programu Windows PowerShell Azure Rights Management
Użyj poniższych informacji ułatwiające instalacji programu Windows PowerShell dla programu Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS).

Ten moduł programu Windows PowerShell służy do administrowania [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] z wiersza polecenia za pomocą dowolnego komputera, który ma połączenie z Internetem i które spełnia wymagania wstępne wymienione w sekcji dalej. Windows PowerShell dla [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] obsługuje skryptów do automatyzacji lub mogą być niezbędne dla scenariuszy zaawansowanych konfiguracji. Aby uzyskać więcej informacji dotyczących zadań administracyjnych i konfiguracji, które obsługuje moduł, zobacz [Administrowanie Azure Rights Management przy użyciu programu Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md).

## Wymagania wstępne
Poniższa tabela zawiera listę wymagań wstępnych instalacji i używania programu Windows PowerShell dla [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

|Wymagania|Więcej informacji|
|-------------|---------------------|
|Wersja systemu Windows, która obsługuje [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] modułu administracji|Sprawdź listę obsługiwanych systemów operacyjnych w **wymagania systemowe** sekcję [strona pobierania dla narzędzia administracji Azure Rights Management](http://go.microsoft.com/fwlink/?LinkId=257721).|
|Minimalna wersja programu Windows PowerShell: 2.0|Obsługę [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] w programie Windows PowerShell 2.0 została wprowadzona w module Administracja.<br /><br />Domyślnie większość systemów operacyjnych Windows jest zainstalowanie z co najmniej w wersji 2.0 programu Windows PowerShell. Jeśli należy zainstalować program Windows PowerShell 2.0, zobacz [instalacji programu Windows PowerShell 2.0](http://msdn.microsoft.com/library/ff637750.aspx). **Tip:** Wersja programu Windows PowerShell, które są uruchomione, wpisując można potwierdzić **$PSVersionTable** w sesji środowiska Windows PowerShell.|
|Minimalna wersja programu Microsoft .NET Framework: 4.5 **Tip:** Ta wersja programu Microsoft .NET Framework jest zawarte w nowszych systemów operacyjnych, dlatego powinien tylko należy ręcznie zainstalować, jeśli system operacyjny klienta jest mniejsza niż Windows 8.0 lub systemu operacyjnego serwera jest mniejsza niż system Windows Server 2012.|Jeśli to nie jest już zainstalowany, możesz pobrać [programu Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).<br /><br />Ta wersja programu Microsoft .NET Framework jest wymagana dla niektórych klas który [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] korzysta z modułu Administracja.|
|Logowanie Assistant 7.0 usług Microsoft Online Services|Asystent pakietu Microsoft Online Services logowania jest wymagany do [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] uwierzytelniania.<br /><br />Aby uzyskać więcej informacji, zobacz [Centrum pobierania: Usług Microsoft Online Services Asystenta dla RTW specjalistów IT](http://www.microsoft.com/en-us/download/details.aspx?id=41950).|

## Jak zainstalować modułu Administracja Rights Management

1.  Przejdź do Center Download firmy Microsoft i [Pobierz narzędzia administracji Azure Rights Management](https://go.microsoft.com/fwlink/?LinkId=257721), w którym znajduje się [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] modułu Administracja środowiska Windows PowerShell.

2.  W folderze lokalnym, gdzie pobrać i zapisać [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] Instalatora plików, kliknij dwukrotnie plik wykonywalny, który został pobrany dla danej platformy (WindowsAzureADRightsManagementAdministration_x64 lub WindowsAzureADRightsManagementAdministration_x86.exe) można uruchomić Azure AD Rights Management Administracja Kreatora instalacji.

3.  Wypełnij pola kreatora.

Windows PowerShell dla [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] został zainstalowany.

## Następne kroki
Aby zobaczyć, które apletów poleceń dostępnych, uruchomić środowisko Windows PowerShell z **Uruchom jako administrator** opcję i wpisz następujące polecenie:

```
Get-Command -Module aadrm
```
Użyj `the Get-Help <cmdlet_name>` polecenie w celu wyświetlenia pomocy dla określonego polecenia cmdlet.

Aby uzyskać więcej informacji:

-   Pełną listę apletów poleceń dostępnych: [Aplety poleceń zarządzania prawami dostępu w Azure](https://msdn.microsoft.com/library/windowsazure/dn629398.aspx)

-   Lista scenariuszy głównego konfiguracji, które obsługuje środowiska Windows PowerShell: [Administrowanie Azure Rights Management przy użyciu programu Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md)

Aby można było uruchomić wszystkie polecenia konfigurujące [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] usługi, należy się połączyć się z usługą za pomocą [Connect AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629415.aspx) polecenia cmdlet. Po zakończeniu uruchamiania poleceń konfiguracji, które chcesz odłączyć od usługi przy użyciu [AadrmService Rozłącz](https://msdn.microsoft.com/library/windowsazure/dn629416.aspx) polecenia cmdlet.

> [!NOTE]
> Jeśli nie został jeszcze aktywowany [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], można to zrobić, po połączeniu z usługą, korzystając z [Aadrm Włącz](https://msdn.microsoft.com/library/windowsazure/dn629412.aspx) polecenia cmdlet.

## Zobacz też
[Administrowanie Azure Rights Management przy użyciu programu Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md)

