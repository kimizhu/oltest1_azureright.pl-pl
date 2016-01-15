---
description: na
keywords: na
title: Rights Management sharing application: Version release history
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6751bd90-959f-4eba-91ed-6588ac983762
---
# Rights Management aplikacji do udostępniania: Historia wersji wersji
Zespół Rights Management regularnie aktualizuje Rights Management aplikacji dla poprawek i nowych funkcji do udostępniania. Użyj następujące informacje, aby zapoznać się z nowe lub zmodyfikowane w wersji. Aktualna wersja jest umieszczane na początku.

Wersje przed 1 stycznia 2015 nie są wyświetlane.

> [!NOTE]
> Jeśli masz opinii lub pytanie dotyczące RMS sharing aplikacji, wysyłania wiadomości e-mail do [AskIPTeam](mailto:AskIPTeam@microsoft.com?subject=RMS%20sharing%20app:%20Feedback%20or%20question).

## Wersja 1.0.1908.0

|||
|-|-|
|Wydana|9/16/2015|
|Poprawki|-   Obsługa uwierzytelniania wieloczynnikowego (MFA) dla Azure RMS, co również powoduje usunięcie zależność Asystenta logowania w usłudze Microsoft dla aplikacji, które używają uwierzytelniania nowoczesnych.<br />    Aby uzyskać więcej informacji, zobacz [Uwierzytelnianie wieloskładnikowe (MFA) i Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_MFA)   w sekcji  [Wymagania dotyczące systemu Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).|

## Wersja 1.0.1784.0

|||
|-|-|
|Wydana|7/30/2015|
|Poprawki|-   Domyślny interwał odświeżania dla prawa szablonów zasad jest zmniejszona z 7 dni na 1 dzień.<br />-   Niewielkiej liczby strat i pomocniczych usterek.|

## Wersja 1.0.1770.0

|||
|-|-|
|Wydana|4/25/2015|
|Poprawki|-   Teraz tylko właściciel i współpracy właścicieli można usunąć ochrony. Nie można współautorów.<br />-   Chronione mogą teraz pliki, które znajdują się w udziale sieciowym.|
|Nowe funkcje|<ul><li>Obsługa śledzenia dokumentów i odwołania. Aby uzyskać więcej informacji zobacz [Śledzenie i odwołać dokumentów, gdy użytkownik korzysta z RMS sharing aplikacji](../Topic/Track_and_revoke_your_documents_when_you_use_the_RMS_sharing_application.md)</li><li>Obsługa szablonu po wybraniu **Udostępnij chronione**:<br /><br /><ul><li>Można wybierać szablony.</li><li>Zamiast suwaka pojawi się pole listy, które zawiera szablony i uprawnienia niestandardowe.</li><li>Nie widzisz opcje **Zezwalaj na użycie na wszystkich urządzeniach** i **wymusić ograniczenia użycia**. Zamiast tego **ogólny ochrony** jest automatycznie wybierany, w zależności od typu pliku.</li></ul>    Aby uzyskać więcej informacji, zobacz [Opcje okna dialogowego Rights Management udostępnianie aplikacji](../Topic/Dialog_box_options_for_the_Rights_Management_sharing_application.md).</li></ul>|

## Wersja 1.0.1667.0

|||
|-|-|
|Wydana|1/19/2015|
|Poprawki|-   Obsługa języka chińskiego czcionek w RMS sharing podglądu PPDF aplikacji.<br />-   Ulepszona obsługa błędów i obsługi wiadomości.<br />-   Poprawka danego problemu z powiadomienie automatycznej aktualizacji, gdy jest nowsza wersja aplikacji jest dostępna do pobrania.|
|Nowe funkcje|-   **Obsługa wielu domen poczty e-mail w ramach danej organizacji**: Jeśli używasz usług AD RMS i użytkowników w Twojej organizacji ma wiele domen poczty e-mail, ta aktualizacja umożliwia użytkownikom korzystać z zawartości, która jest chroniony przez użytkowników w Twojej organizacji w innych domenach. Aby uzyskać więcej informacji, zobacz [Usług AD RMS tylko: Obsługa wielu domen poczty e-mail w ramach danej organizacji](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_FederatedDomains) w sekcji [Przewodnik administratora aplikacji udostępniania zarządzania prawami dostępu](../Topic/Rights_Management_sharing_application_administrator_guide.md).|
