---
description: na
keywords: na
title: View and use files that have been protected by Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e5fa4666-6906-405a-9e0c-2c52d4cd27c8
---
# Wyświetlanie i używanie plik&#243;w chronionych przez usługi Rights Management
Gdy [zarządzania prawami (RMS) aplikacji do udostępniania jest zainstalowany na tym komputerze](https://technet.microsoft.com/library/dn574734%28v=ws.10%29.aspx), wyświetlanie chronionego pliku po prostu kliknij go dwukrotnie. Plik może być załącznika w wiadomości e-mail lub może go Zobacz, korzystając z Eksploratora pliku.

> [!NOTE]
> Aby można było wyświetlić chronionego pliku, RMS należy najpierw upewnij się, że masz uprawnienia do wyświetlania pliku, który tak, sprawdzając swoją nazwę użytkownika i hasło. W niektórych przypadkach to może być zapisane w pamięci podręcznej i nie będzie wyświetlany monit o podanie poświadczeń. W innych przypadkach wyświetli monit o podanie poświadczeń.
> 
> Jeśli w organizacji nie są używane, Azure Rights Management (Azure RMS) lub usług AD RMS, można zastosować bezpłatne konta, które będą akceptowane swoje poświadczenia, aby otwierania plików, które są chronione przy użyciu usług RMS:
> 
> -   Aby zastosować dla tego konta, kliknij łącze, aby zgłosić do [RMS dla osób](http://go.microsoft.com/fwlink/?LinkId=309469).
> 
>     Po utworzeniu konta, należy użyć adres e-mail firmy, a nie jest adresem e-mail osobistych. Jeśli zapisujesz się, ponieważ zostały wysłane pocztą e-mail chronionych załącznika, używają tego samego adresu e-mail, użytej do wysyłania wiadomości e-mail.
> -   Aby uzyskać więcej informacji, zobacz [RMS dla osób i systemu Windows Azure Rights Management](http://technet.microsoft.com/library/dn592127.aspx).

## <a name="BKMK_ViewPFILE"></a>Aby wyświetlić chronionego pliku
Za pomocą Eksploratora pliku lub wiadomości e-mail, która zawiera załącznik, kliknij dwukrotnie plik chroniony, a następnie wprowadź swoje poświadczenia, jeśli zostanie wyświetlony monit, aby to zrobić.

Jeśli widzisz dwie wersje pliku, ale z różne rozszerzenia nazw plików, otwórz plik, który ma rozszerzenie .ppdf tylko wtedy, gdy nie można otworzyć inny plik. Jeśli nie można otworzyć wersję .ppdf albo, najpierw zainstaluj [RMS sharing aplikacji](http://technet.microsoft.com/library/dn574734.aspx), który zna sposób otwierania plików, które mają rozszerzenie nazwy pliku .ppdf.

> [!NOTE]
> Aby uzyskać więcej informacji, zobacz "[Co to jest plik .ppdf, który jest tworzony automatycznie?](../Topic/Dialog_box_options_for_the_Rights_Management_sharing_application.md#BKMK_PPDF)".

Jak otwiera plik zależy od tego, jak został zabezpieczony, którego można stwierdzić, sprawdzając rozszerzenia nazwy pliku. W każdym przypadku otwierania pliku mogą podlegać inspekcji i pozostawia inspekcji, jak długo jest chroniony. Ponadto jeśli plik został wysłany jako załącznik wiadomości e-mail, nadawca może otrzymywania powiadomień pocztą e-mail zawsze podczas otwierania pliku.

|Rozszerzenie nazwy pliku i ochrona danych|Więcej informacji|
|---------------------------------------------|---------------------|
|Plik zawiera **pfile** rozszerzenia nazwy pliku.<br /><br />Plik został ogólnego chroniony.|Podczas otwierania pliku, zobacz **plik chroniony** okno dialogowe z udostępniania aplikacji, która informuje o tym, kto chroniony plik i powinny przestrzegać uprawnień właściciela współpracy. Kliknij przycisk **Otwórz** do odczytu tego pliku.<br /><br />![](../Image/ADRMS_MSRMSApp_PfilePermission.png)|
|Plik zawiera **.ppdf** rozszerzenia nazwy pliku lub plik jest chroniony tekst lub obraz (takie jak **.ptxt** lub **.pjpg**).<br /><br />Plik jest chroniony macierzyście jako kopię tylko do odczytu.|Otwiera plik za pomocą podglądu, który instaluje z RMS sharing aplikacji. Ten plik jest tylko do odczytu, nawet jeśli zapisać go w innej lokalizacji lub zmienić jego nazwy.|
|Inne rozszerzenia nazwy pliku.<br /><br />Plik jest chroniony sposób macierzysty.|Otwiera plik za pomocą aplikacji, która jest skojarzona z oryginalnym rozszerzenia nazwy pliku i ograniczenia transparentu jest wyświetlane u góry pliku. Baner następuje wyświetlenie uprawnienia, które są stosowane do pliku lub określić łącze, aby je wyświetlić. Na przykład, może dojść następujących gdzie należy kliknąć przycisk **uprawnienie jest obecnie ograniczone** rzeczywiste uprawnienia, które są stosowane do pliku i osób, które można do niego dostęp:<br /><br />![](../Image/ADRMS_MSRMSApp_RestrictedAccess.png)|
Aby uzyskać pełną listę rozszerzeń nazw plików, które obsługuje Rights Management, zobacz [Obsługiwane typy plików i rozszerzeń nazw plików](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SupportFileTypes) sekcji w  [Przewodnik administratora aplikacji udostępniania zarządzania prawami dostępu](../Topic/Rights_Management_sharing_application_administrator_guide.md). Jeśli nie ma rozszerzenia nazwy pliku, należy użyć wyszukiwania w sieci web, aby zobaczyć, to rozszerzenie nazwy pliku, który jest obsługiwany przez inną aplikację.

> [!NOTE]
> Jeżeli, po potwierdzeniu, że plik jest chroniony przez Rights Management i nie można otworzyć pliku, pobranie i używanie [Narzędzie analizatora RMS](https://www.microsoft.com/en-us/download/details.aspx?id=46437). Postępuj zgodnie z instrukcjami w narzędziu do sprawdzania problemów występujących na komputerze, które mogą uniemożliwiać chroniony dokument otwierania.

## <a name="BKMK_UserDefined"></a>Aby użyć pliki są chronione (na przykład, edytowania i drukowania pliku)
Jeśli po otwarciu chronionego pliku ma więcej niż tylko odczytu (na przykład edytowania, kopiowania i Drukuj):

|Rozszerzenie nazwy pliku|Instrukcje|
|----------------------------|--------------|
|Plik zawiera **pfile** rozszerzenia nazwy pliku.|Zapisz plik otwarty i nadać mu nowe rozszerzenie nazwy pliku skojarzonego z aplikacji, która ma być używany.<br /><br />Na przykład jeśli plik został chronione przy użyciu document.vsdx.pfile nazwy pliku, Wyświetl plik i Eksplorator pliku, Zapisz plik jako document.vsdx.<br /><br />Nowy plik nie jest chroniony. Jeśli chcesz zabezpieczyć go, możesz to zrobić ręcznie. Aby uzyskać instrukcje, zobacz [Ochrona pliku na urządzeniu &#40;Włącz ochronę miejscową&#41; przy użyciu Rights Management udostępnianie aplikacji](../Topic/Protect_a_file_on_a_device__protect_in-place__by_using_the_Rights_Management_sharing_application.md).|
|Plik zawiera **.ppdf** rozszerzenia nazwy pliku lub plik jest chroniony tekst lub obraz (takie jak **.ptxt** lub **.pjpg**).|Możesz jedynie wyświetlać pliku i nazwy lub przenieść go, ochrony pozostają związane z plikiem.|
|Inne rozszerzenia nazwy pliku.|Urządzenie musi mieć aplikację, w której rozumie zarządzania praw do korzystania z tych plików. Te aplikacje są nazywane aplikacjami RMS enlightened. Aplikacje z pakietu Office 2016 roku, pakietu Office 2013 i Office 2010 (takich jak Word, Excel, PowerPoint i Outlook) to przykłady aplikacji, które są enlightened Rights Management. Jednak aplikacje, które nie pochodzą od firmy Microsoft, takich jak innych firm i własne--aplikacji biznesowych, może być również enlightened Rights Management.<br /><br />Aplikacje, które są enlightened dla Rights Management wiedzieć, jak do otwierania plików, które są chronione przez inne Rights Management enlightened aplikacji. Trwała one również ochrony stosowany do nich, nawet jeśli Przeprowadź edycję pliku lub zapisać je na inną nazwę pliku lub w innej lokalizacji. Aplikacje te pozwalają użytkowania pliku zgodnie z uprawnieniami, które aktualnie zastosowanych do pliku, jeśli użytkownik ma uprawnienia do używania pliku, możesz to zrobić. Na przykład można edytować plik, ale nie jego wydrukowanie.|

## Inne instrukcje i przykłady
Przykłady dla sposobu wykorzystania Rights Management udostępnianie aplikacji i instrukcje dotyczące wykonywania określonych zadań w następujących sekcjach z Podręcznik użytkownika aplikacji udostępniania Rights Management:

-   [Przykłady korzystania z aplikacji do udostępniania RMS](../Topic/Rights_Management_sharing_application_user_guide.md#BKMK_SharingExamples)

-   [Co chcesz zrobić?](../Topic/Rights_Management_sharing_application_user_guide.md#BKMK_SharingInstructions)

## Zobacz też
[Przewodnik użytkownika aplikacji udostępniania zarządzania prawami dostępu](../Topic/Rights_Management_sharing_application_user_guide.md)

