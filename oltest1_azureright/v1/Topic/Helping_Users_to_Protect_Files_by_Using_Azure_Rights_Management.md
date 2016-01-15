---
description: na
keywords: na
title: Helping Users to Protect Files by Using Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 58f9a6ff-4121-4c8c-9865-1bb290604ad2
---
# Ułatwienie użytkownikom ochronę plik&#243;w przy użyciu systemu Azure Rights Management
Po wdrożeniu i skonfigurowana Azure Rights Management (Azure RMS) w organizacji, należy uzyskać pomoc i wskazówki dla użytkowników, Administratorzy i pomoc techniczna:

-   **Informacje dla użytkowników końcowych:**

    Powiadomić użytkowników, jak i kiedy do ochrony dokumentów i wiadomości e-mail, które zawierają poufne informacje. Zawsze, gdy jest to możliwe, należy podać te informacje dotyczące przepływów pracy, aby zawierają dodatkowe kroki procesu już znane, a nie wprowadzenie całkowicie nowe procesy. Należy upewnić się, że Poinformuj korzyści (i ryzyko), które są specyficzne dla firmy, a także podaje wskazówki dotyczące kiedy należy chronić pliki i wiadomości e-mail. Jeśli skonfigurowano [Szablony niestandardowe](http://technet.microsoft.com/library/dn642472.aspx), udostępnić informacje o nich, zaznacz, jeśli nie jest wystarczające wybrać właściwą nazwę i opis szablonu.

    > [!TIP]
    > Przykład filmy wideo dla użytkowników końcowych:
    > 
    > -   [Interfejs użytkownika usługi Azure RMS](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-user-experience)
    > -   [Śledzenie Azure RMS dokumentu i odwołania](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation)

-   **Informacje dla administratorów:**

    Niektóre aplikacje automatycznie zastosować ochrony informacji przy użyciu zasady i ustawienia konfigurujące Administratorzy. W przypadku tych aplikacji może być konieczne w celu przekazania instrukcji dotyczących innych administratorów, którzy zarządzają te aplikacje i usługi. Aby uzyskać więcej informacji, zobacz [Jak aplikacje obsługują Azure Rights Management](../Topic/How_Applications_Support_Azure_Rights_Management.md) i [Konfigurowanie aplikacji Azure Rights Management](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

-   **Informacje o pomocy technicznej:**

    Jedną z najbardziej przydatnych narzędzi dla pomocy technicznej jest [analizatora RMS](https://www.microsoft.com/en-us/download/details.aspx?id=46437).   Pomocy technicznej operatorów ją uruchomić z opcją administratora Azure RMS, a ich poprosić użytkowników do uruchomienia go z opcją Azure RMS użytkownika. Tego narzędzia można nie tylko identyfikowania problemów, ale także rozwiązać problemy znalezione, i jeśli nadal nie rozwiązaniu dzienniki śledzenia rekordu.

    W przypadku żądań wiarygodnego pełne prawa dostępu do chronionej dokumenty, na przykład żądania przez dział prawny lub Menedżera po pracownika pozostały organizacji, upewnij się, pomocy technicznej ma procesy na to żądanie przy użyciu Azure RMS [Funkcja administratorów](https://technet.microsoft.com/en-us/library/mt147272.aspx).

    Ponadto to niektóre typowych problemów, które może zgłosić użytkowników:

    -   **Zaloguj się pomocy:**

        Użytkowników może zostać wyświetlony monit o poświadczenia, gdy Azure RMS wymaga uwierzytelnienia użytkownika i nie można użyć poświadczenia z pamięci podręcznej. Będzie to jego pracy lub szkolnego konta i hasła, skojarzony z dzierżawcy usługi Office 365 lub dzierżawy usługi Azure Active Directory. Nie będzie konto Microsoft (dawniej Microsoft Live ID) lub ich osobiste konto e-mail, ponieważ te nie są obecnie obsługiwane przez Azure RMS. Instrukcje dotyczące konta, które można użyć, gdy użytkownicy są monitowani o poświadczenia, jeśli korzystają z tych aplikacji z Azure RMS zapewnienia użytkownicy i pomoc techniczna.

    -   **Problemy z ochronę lub kliencie zawartości:**

        Upewnij się, że użytkownicy mają odpowiednie instrukcje dla aplikacji, ich używać i korzysta z aplikacji i urządzeń, które są obsługiwane przez Azure RMS. Aby uzyskać więcej informacji o obsługiwanych aplikacji i urządzeń, zobacz [Wymagania dotyczące systemu Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

        Jeśli użytkownicy widzą wystąpił błąd podczas próby ochrony lub korzystać z zawartości, poproś o Uruchom [analizatora RMS](https://www.microsoft.com/en-us/download/details.aspx?id=46437) jako użytkownik Azure RMS.

        Jeśli użytkownicy raport, aby otworzyć chronionej zawartości, ale nie mają praw, które są im niezbędne, poproś o Uruchom [analizatora RMS](https://www.microsoft.com/en-us/download/details.aspx?id=46437) jako użytkownik Azure RMS i pobrać i wyświetlić szablony. To potwierdzi, że ich został pomyślnie pobrany szablony i szablony co praw świadczenia. Może to oznaczać że użytkownik nie jest poprawną grupę, która jest skonfigurowany dla szablonu lub że szablon wymaga ponownej konfiguracji dla użytkownika.

Użyj w następujących sekcjach informacje specyficzne dla aplikacji, aby pomóc chronić ważne dokumenty i wiadomości e-mail użytkowników.

## Używanie ochrony informacji z aplikacją udostępniania Rights Management
Zarządzania prawami (RMS) aplikacji do udostępniania jest wymagana dla użytkowników do ochrony i korzystać z zawartości chronionej użycie pakietu Office 2010, ale także zalecane w przypadku wszystkich komputerów i urządzeń przenośnych, które obsługują Azure RMS.

Oprócz ułatwienie użytkownikom ochrony ważnych dokumentów RMS sharing aplikacji umożliwia użytkownikom śledzenie dokumentów, które mają one chronione, a w razie potrzeby odwołania do nich dostęp.

Aby uzyskać instrukcje dotyczące korzystania z tej aplikacji dla komputerów z systemem Windows, zobacz [Podręcznik użytkownika aplikacji udostępniania Rights Management](http://technet.microsoft.com/library/dn339006.aspx).

Dla urządzeń przenośnych, zobacz [często zadawane pytania dotyczące Microsoft prawa udostępniania aplikacji do zarządzania dla platformy Mobile](http://technet.microsoft.com/dn451248).

> [!TIP]
> Przykład wysokiego poziomu scenariusza z zrzuty ekranu, zobacz [Użytkownicy bezpiecznie udostępniać załączniki użytkowników mobilnych](../Topic/What_is_Azure_Rights_Management_.md#BKMK_Example_SharingApp) w sekcji [Co to jest Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md) tematu.

## Używanie ochrony informacji z usługi Office 365, pakietu Office 2016 roku lub Office 2013
Jeśli używasz Azure RMS i nie jest zainstalowany Rights Management udostępnianie aplikacji, użytkownicy nie będą widoczne **Udostępnij chronione** przycisk na Wstążce lub **ochrony w miejscu** z Eksploratora plik, który ułatwia ich do ochrony plików. Dla tych użytkowników muszą się stosować podobne do następujących instrukcji.

> [!TIP]
> Aby znaleźć pomoc określonych aplikacji i instrukcje dotyczące korzystania z tymi aplikacjami ochrony informacji, wyszukiwanie **IRM** i nazwa i wersja aplikacji.

#### Aby chronić dokumentu programu Word 2013

1.  W ramach programu Microsoft Word należy utworzyć nowy dokument.

2.  Z **pliku** menu, kliknij przycisk **informacje o**, kliknij przycisk **Chroń dokument**, kliknij przycisk **ograniczania dostępu**, a następnie wybierz szablon, aby szybko zastosować praw użytkowania odpowiednie, lub wybierz **ograniczania dostępu do** i wybrać siebie praw użytkowania.

    > [!NOTE]
    > Jeśli to jest użycie Rights Management po raz pierwszy, skontaktujemy [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] usługi i zostanie wyświetlony monit o poświadczenia, aby skonfigurować klienta IRM pakietu Office.

3.  Zapisz dokument.

Podczas otwierania dokumentu, najpierw potwierdzone. Jeśli nie masz uprawnień do otwierania tego dokumentu, nie powoduje otwarcia dokumentu. Jeśli są one zatwierdzone do otwierania tego dokumentu, zostanie otwarte z praw użytkowania ograniczona, które zostały określone dla tego użytkownika. Na przykład użycie prawej strony tylko do odczytu nie zezwala użytkownikowi edytowanie lub Zapisz dokument, nawet wtedy, gdy jest ona kopiowana najpierw ją w innej lokalizacji. Prawa użytkowania są wyświetlane u góry okna dokumentu za pomocą ograniczenia transparentu. Baner następuje wyświetlenie uprawnienia, które są stosowane do dokumentu lub określić łącze, aby je wyświetlić.

#### Aby chronić wiadomości e-mail przy użyciu programu Outlook 2013 i Exchange Online

1.  W programie Outlook utwórz nową wiadomość e-mail skierowane do odbiorcy w ramach danej organizacji.

2.  Z **Opcje** kliknij **uprawnienia**, a następnie wybierz opcję. Na przykład: **Nie są przekazywane przez**, **&lt; nazwa firmy - &gt; poufne** lub **&lt; nazwa firmy - &gt; poufne widoku tylko**.

3.  Wyślij wiadomość.

Podobnie do przeglądania chroniony dokument, gdy adresatów otrzymywać wiadomości e-mail, ich najpierw uwierzytelniania. Jeśli ich uprawnienia do wiadomości e-mail, zostanie otwarte z praw użytkowania ograniczona, które zostały określone dla tego użytkownika. Na przykład w przypadku wybrania **nie przesyłaj dalej**, przycisk Prześlij dalej na wstążce jest niedostępny.

#### Aby chronić wiadomości e-mail za pomocą aplikacji sieci Web programu Outlook

1.  W aplikacji sieci Web programu Outlook utwórz nową wiadomość e-mail skierowane do odbiorcy w ramach danej organizacji.

2.  Kliknij przycisk  **...**,  kliknij przycisk **Ustaw uprawnienia**, a następnie wybierz opcję. Na przykład: **Nie są przekazywane przez**, **nie Odpowiedz wszystkim**, **&lt; nazwa firmy - &gt; poufne** lub **&lt; nazwa firmy - &gt; poufne widoku tylko**.

3.  Wyślij wiadomość.

Podobnie do przeglądania chroniony dokument, gdy adresatów otrzymywać wiadomości e-mail, ich najpierw uwierzytelniania. Jeśli ich uprawnienia do wiadomości e-mail, zostanie otwarte z praw użytkowania ograniczona, które zostały określone dla tego użytkownika. Na przykład w przypadku wybrania **czy nie Odpowiedz wszystkim**,  **ODPOWIEDZ wszystkim** opcję w oknie komunikatu jest niedostępny.

## Zobacz też
[Za pomocą systemu Azure Rights Management](../Topic/Using_Azure_Rights_Management.md)

