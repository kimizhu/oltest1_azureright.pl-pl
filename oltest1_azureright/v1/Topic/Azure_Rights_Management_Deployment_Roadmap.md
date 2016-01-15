---
description: na
keywords: na
title: Azure Rights Management Deployment Roadmap
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 086600c2-c5d8-47ec-a4c0-c782e1797486
---
# Mapa wdrożenia usługi zarządzania prawami systemu Azure
Przygotowanie do, wdrożenia i zarządzania Azure Rights Management (Azure RMS) dla organizacji, wykonaj następujące kroki.

Jednak, jeśli chcesz szybko spróbować Azure RMS na własne potrzeby, raczej niż limit uruchomieniem w środowisku produkcyjnym, zobacz [Samouczek Szybki Start Azure Rights Management](../Topic/Quick_Start_Tutorial_for_Azure_Rights_Management.md).

> [!IMPORTANT]
> Przed wykonaniem poniższych kroków upewnij się, że w przypadku stwierdzenia [Wymagania dotyczące systemu Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

## Krok 1: Sprawdź, czy masz subskrypcję, które obejmują Azure Rights Management
Istnieje więcej niż jeden typ subskrypcji, zawierającej [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]. Zobacz [Subskrypcje chmury, które obsługują Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) w sekcji [Wymagania dotyczące systemu Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tematu, a następnie sprawdź, czy Twoja subskrypcja zawiera funkcję, która ma być używany w Twojej organizacji przez odwołuje się do tabeli w [ofert porównanie z usług zarządzania prawami (RMS)](https://technet.microsoft.com/dn858608).

## Krok 2: Przygotuj konta dzierżawy, aby użyć Rights Management
Przed rozpoczęciem korzystania z [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], wykonaj następujące przygotowania:

1.  Upewnij się, że dzierżawą Azure lub usługi Office 365 zawiera konta użytkowników i grup, które będą używane przez Azure RMS do uwierzytelniania użytkowników w Twojej organizacji. W razie potrzeby należy utworzyć te konta i grupy lub synchronizować je z katalogu lokalnego. Aby uzyskać więcej informacji, zobacz [Trwa przygotowywanie do systemu Azure Rights Management](../Topic/Preparing_for_Azure_Rights_Management.md).

2.  Określa, czy użytkownik chce firmy Microsoft do zarządzania swoim kluczem dzierżawy (domyślnie), lub wygenerować oraz zarządzania swoim kluczem dzierżawy, samodzielnie (znaną jako własny klucz lub BYOK). Należy zauważyć, że obecnie nie można użyć BYOK korzystając z programu Exchange Online. Aby uzyskać więcej informacji, zobacz [Planowanie i wdrażanie swoim kluczem dzierżawcy zarządzania prawami Azure](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

3.  Zainstaluj moduł programu Windows PowerShell dla [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] na co najmniej jeden komputer, który ma dostęp do Internetu. Można wykonać ten krok teraz lub później. Aby uzyskać więcej informacji, zobacz [Instalowanie programu Windows PowerShell Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

4.  Jeśli używasz obecnie usługi Rights Management lokalnie: Przeprowadzić migracji można przenieść kluczy, szablonów i adresów URL w chmurze. Aby uzyskać więcej informacji, zobacz [Migrowanie z usług AD RMS do usługi Azure Rights Management](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md).

5.  Aktywować usługę Rights Management, tak aby mogli rozpocząć do korzystania z usługi. Jeśli stopniowy wdrożenia jest wymagany, należy skonfigurować formantów przysposobienie użytkownika ograniczenia użycia do konkretnych użytkowników. Aby uzyskać więcej informacji, zobacz [Aktywowanie Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md).

Opcjonalnie należy wziąć pod uwagę konfigurowania następujących czynności:

-   Szablony niestandardowe, jeśli wartość domyślna szablonów zasad praw są niewystarczające do swojej organizacji. Można wykonać ten krok teraz lub później. Aby uzyskać więcej informacji, zobacz [Konfigurowanie niestandardowych szablonów Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

-   Użycie logowania, które można monitorować, jak organizacja używa Rights Management. Można wykonać ten krok teraz lub później. Aby uzyskać więcej informacji, zobacz [Rejestrowanie i analizy użycia zarządzania prawami Azure](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md).

## Krok 3: Skonfiguruj aplikacje i usługi Rights Management
Konfigurowanie aplikacji mogą obejmować instalowanie Rights Management aplikacji do udostępniania i włączyć obsługę funkcji zarządzania prawami prawa informacji w usłudze SharePoint Online lub Exchange Online. Aby uzyskać więcej informacji, zobacz [Konfigurowanie aplikacji Azure Rights Management](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

Jeśli masz istniejące usługi IT, które należy sprawdzić pliki chroniących Azure RMS — takich jak przeciek zapobiegania (DLP) rozwiązania do obsługi danych, zawartości szyfrowania bram (CEG) i produktów programów chroniących przed złośliwym — Konfigurowanie kont usług jako administratorów dla Azure RMS. Aby uzyskać więcej informacji, zobacz [Konfigurowanie administratorów systemu Azure Rights Management i odnajdywania usług lub odzyskiwania danych](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md).

Jeśli masz lokalnych usług, które ma być używany z Azure Rights Management, zainstaluj i skonfiguruj łącznik Rights Management. Aby uzyskać więcej informacji, zobacz [Łącznik zarządzania Azure prawa wdrażania](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

## Krok 4: Publikowanie i korzystać z zawartości chronionej prawami
Teraz wszystko jest gotowe do publikowania i korzystać z zawartości chronionej, a następnie zaloguj się, jak firma używa Rights Management. Aby uzyskać więcej informacji, zobacz [Za pomocą systemu Azure Rights Management](../Topic/Using_Azure_Rights_Management.md).

## Krok 5: Administrowanie Rights Management dla swojego konta dzierżawy w razie potrzeby
Po rozpoczęciu do użycia [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], może się okazać [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] modułu przydatne ułatwia tworzenie skryptów lub zautomatyzować zmiany administracyjne środowiska Windows PowerShell. Aby uzyskać więcej informacji, zobacz [Administrowanie Azure Rights Management przy użyciu programu Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md).

## Zobacz też
[Konfigurowanie Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

