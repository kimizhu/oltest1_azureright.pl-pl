---
description: na
keywords: na
title: Preparing for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: afbca2d6-32a7-4bda-8aaf-9f93f5da5abc
---
# Trwa przygotowywanie do systemu Azure Rights Management
Po przystąpił do subskrypcji chmury i ustanowić organizacji za pomocą konta dla [!INCLUDE[o365_1](../Token/o365_1_md.md)] lub Azure Active Directory, aby przystąpić do włączenia [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] usługi.

Jednak przed zrobić, upewnij się, że następujące znajdują się:

-   Konta użytkowników i grupy w chmurze, który można utworzyć ręcznie lub które są automatycznie tworzone i zsynchronizowane z usług domenowych w usłudze Active Directory (AD DS).

    Podczas synchronizowania kont lokalnych i grup, nie wszystkie atrybuty muszą zostać zsynchronizowane. Lista atrybutów, które należy zsynchronizować dla Azure RMS, zobacz [sekcji Azure RMS](https://azure.microsoft.com/documentation/articles/active-directory-aadconnectsync-attributes-synchronized/) z dokumentacji Azure Active Directory. W celu ułatwienia wdrażania, zalecamy użycie [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) do nawiązania połączenia z lokalnym katalogów w usłudze Azure Active Directory, ale można użyć dowolnej metody synchronizacji katalogu, który daje taki sam efekt.

-   Grupy komputerów z obsługą poczty w chmurze, która będzie używana z Rights Management. Te mogą być wbudowane grupy lub grupy zawierające użytkowników korzystających z Rights Management utworzone ręcznie.

    Jeśli masz Exchange Online, można tworzyć i używać grupy z włączoną obsługą poczty za pomocą Centrum administracyjne usługi Exchange. Jeśli masz usług AD DS i synchronizują do usługi Azure AD, można tworzyć i używać grup włączoną obsługą poczty, będące grup zabezpieczeń lub grup dystrybucji.

## Włącz Rights Management
Domyślnie [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] jest wyłączona, gdy logujesz się z [!INCLUDE[o365_2](../Token/o365_2_md.md)] lub konta usługi Azure AD. Aby włączyć [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] dla organizacji, należy aktywować usługę. Aby uzyskać więcej informacji, zobacz [Aktywowanie Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md).

## Zobacz też
[Konfigurowanie Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

