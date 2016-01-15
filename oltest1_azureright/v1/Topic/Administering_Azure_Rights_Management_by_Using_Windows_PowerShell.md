---
description: na
keywords: na
title: Administering Azure Rights Management by Using Windows PowerShell
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a890e04a-4b70-41b5-8d5f-3c210a669faa
---
# Administrowanie Azure Rights Management przy użyciu programu Windows PowerShell
Mimo że można uaktywnić Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (usług Azure RMS) przy użyciu [!INCLUDE[o365_2](../Token/o365_2_md.md)] Centrum administracyjne lub klasycznego portalu Azure umożliwia także modułu programu Windows PowerShell dla [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (aplikacją AADRM), w tym celu.

Po uaktywnieniu [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], dalsze Administracja usługi nie może być wymagane. Jednak niektóre scenariusze konfiguracji zaawansowanej mogą wymagać użyć modułu programu Windows PowerShell [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]. Poniższa lista zawiera niektóre scenariusze zaawansowanej konfiguracji, które używają programu Windows PowerShell. Aby uzyskać pełną listę dostępnych poleceń cmdlet z dodatkowymi informacjami na temat każdego z nich, zobacz [poleceń cmdlet programu Azure Rights Management](http://msdn.microsoft.com/library/azure/dn629398.aspx).

> [!NOTE]
> Jeśli musisz zainstalować moduł Windows PowerShell dla [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], zobacz [Instalowanie programu Windows PowerShell Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

Jest również uzupełniające moduł programu Windows PowerShell, **RMSProtection**, który obsługuje zarówno usług Azure RMS i AD RMS. Ten moduł obsługuje ochrony i usuwanie ochrony z wielu plików, tak aby na przykład zbiorcze chronić wszystkie pliki w folderze. Aby uzyskać więcej informacji, zobacz [Opcje obsługi skryptów dla administratorów](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md#BKMK_RMSProtectionModule) w sekcji [Konfigurowanie administratorów systemu Azure Rights Management i odnajdywania usług lub odzyskiwania danych](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md) tematu.

|Jeśli chcesz...|.. Użyj następujących poleceń cmdlet|
|-------------------|----------------------------------------|
|Migrację z lokalnych Rights Management (AD RMS lub Windows RMS) do [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].|[Importuj AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx)|
|Łączenie i rozłączanie z [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] dla Twojej organizacji.|[Połącz AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx)<br /><br />[Odłącz AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx)|
|Generowanie i zarządzaj nimi własny klucz dzierżawcy — Przełącz scenariusza klucza (BYOK).|[Dodaj AadrmKey](http://msdn.microsoft.com/library/azure/dn629418.aspx)<br /><br />[Get-AadrmKeys](http://msdn.microsoft.com/library/azure/dn629420.aspx)|
|Uaktywnianie lub dezaktywowanie [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] dla Twojej organizacji.|[Aplikacją Aadrm Włącz](http://msdn.microsoft.com/library/azure/dn629412.aspx)<br /><br />[Disable-aplikacją Aadrm](http://msdn.microsoft.com/library/azure/dn629422.aspx)|
|Wyłączanie lub włączanie śledzenia lokacji Azure Rights Management dokumentów.|[Wyłącz AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548471.aspx)<br /><br />[Włącz AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548469.aspx)<br /><br />[Get-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548470.aspx)|
|Skonfiguruj sterowanie dołączania etapowego wdrażania Azure Rights Management.|[Get-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857522.aspx)<br /><br />[Zestaw AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx)|
|Tworzenie i zarządzanie szablonów zasad praw dla Twojej organizacji.|[Dodaj AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727075.aspx)<br /><br />[AadrmTemplate eksportu](http://msdn.microsoft.com/library/azure/dn727078.aspx)<br /><br />[Get-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727079.aspx)<br /><br />[Get-AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727081.aspx)<br /><br />[Importuj AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727077.aspx)<br /><br />[Nowy AadrmRightsDefinition](http://msdn.microsoft.com/library/azure/dn727080.aspx)<br /><br />[Usuń AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727082.aspx)<br /><br />[Zestaw AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727076.aspx)|
|Skonfiguruj maksymalną liczbę dni, w których zawartość, która chroni organizacji są dostępne bez połączenia z Internetem (Użyj okresu ważności licencji).|[Get-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932062.aspx)<br /><br />[Zestaw AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932063.aspx)|
|Zarządzanie funkcją administratorów z [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] dla Twojej organizacji.|[Włącz AadrmSuperUserFeature](http://msdn.microsoft.com/library/azure/dn629400.aspx)<br /><br />[Wyłącz AadrmSuperUserFeature](http://msdn.microsoft.com/library/azure/dn629428.aspx)<br /><br />[Dodaj AadrmSuperUser](http://msdn.microsoft.com/library/azure/dn629411.aspx)<br /><br />[Get-AadrmSuperUser](http://msdn.microsoft.com/library/azure/dn629408.aspx)<br /><br />[Usuń AadrmSuperUser](http://msdn.microsoft.com/library/azure/dn629405.aspx)|
|Zarządzaj użytkownikami i grupami, które mają uprawnienia do administrowania [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] dla Twojej organizacji.|[Dodaj AadrmRoleBasedAdministrator](http://msdn.microsoft.com/library/azure/dn629417.aspx)<br /><br />[Get-AadrmRoleBasedAdministrator](http://msdn.microsoft.com/library/azure/dn629407.aspx)<br /><br />[Usuń AadrmRoleBasedAdministrator](http://msdn.microsoft.com/library/azure/dn629424.aspx)|
|Pobierz dziennik [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] zadania administracyjne dla Twojej organizacji.|[Get-AadrmAdminLog](http://msdn.microsoft.com/library/azure/dn629430.aspx)|
|Zaloguj się i analizowanie użycia rejestrowanie dla [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].|[Włącz AadrmUsageLogFeature](http://msdn.microsoft.com/library/azure/dn629421.aspx)<br /><br />[Get-AadrmUsageLog](http://msdn.microsoft.com/library/azure/dn629401.aspx)<br /><br />[Get-AadrmUsageLogFeature](http://msdn.microsoft.com/library/azure/dn629425.aspx)<br /><br />[Get-AadrmUsageLogLastCounterValue](http://msdn.microsoft.com/library/azure/dn629423.aspx)<br /><br />[Get-AadrmUsageLogStorageAccount](http://msdn.microsoft.com/library/azure/dn629419.aspx)<br /><br />[Zestaw AadrmUsageLogStorageAccount](http://msdn.microsoft.com/library/azure/dn629426.aspx)<br /><br />[Wyłącz AadrmUsageLogFeature](http://msdn.microsoft.com/library/azure/dn629404.aspx)|
|Wyświetl bieżącą [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] konfiguracji usługi dla Twojej organizacji.|[Get-AadrmConfiguration](http://msdn.microsoft.com/library/azure/dn629410.aspx)|
|Migracja organizacji z [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] do lokalnego wdrożenia usług AD RMS.|[Zestaw AadrmMigrationUrl](http://msdn.microsoft.com/library/azure/dn629429.aspx)<br /><br />[Get-AadrmMigrationUrl](http://msdn.microsoft.com/library/azure/dn629403.aspx)|

## Zobacz też
[Azure Rights Management](../Topic/Azure_Rights_Management.md)

