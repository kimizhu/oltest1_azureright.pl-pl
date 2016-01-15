---
description: na
keywords: na
title: Activating Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f8707e01-b239-4d1a-a1ea-0d1cf9a8d214
---
# Aktywowanie Azure Rights Management
Po uaktywnieniu [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (usług Azure RMS), Twoja organizacja może zacząć chronić ważne dane przy użyciu aplikacji i usług obsługujących to rozwiązanie ochrony informacji. Administratorzy mogą również zarządzanie i monitorowanie chronionych plików i wiadomości e-mail, należące do organizacji. Należy włączyć [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] przed rozpoczęciem korzystania z funkcji zarządzania (IRM) prawa informacji w pakiecie Office, SharePoint i Exchange i włącz ochronę plików poufne.

Jeśli chcesz dowiedzieć się więcej na temat Azure Rights Management przed uaktywnieniem usługi — na przykład, jakie to rozwiąże problemy biznesowe, czasami typowym zastosowaniem i jak działa — można znaleźć w temacie [Co to jest Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md)

> [!IMPORTANT]
> Przed aktywowaniem [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], upewnij się, że Twoja organizacja ma planu usług, która zawiera [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] usług. Jeśli nie, nie można aktywować usług Azure RMS.
> 
> Aby uzyskać więcej informacji, zobacz [Subskrypcje chmury, które obsługują Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) w sekcji [Wymagania dotyczące systemu Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tematu.

Po uaktywnieniu usług Azure RMS, wszystkich użytkowników w organizacji można stosować ochrony informacji do swoich plików i wszyscy użytkownicy mogą otworzyć (Korzystanie z nich) pliki chronione za pomocą usług Azure RMS. Jednak jeśli wolisz, można ograniczyć kto zastosowania ochrony informacji za pomocą formantów dołączania etapowe wdrożenia. Aby uzyskać więcej informacji, zobacz [Konfigurowanie dołączania kontrolek etapowe wdrożenia](../Topic/Activating_Azure_Rights_Management.md#BKMK_OnboardingControls) w tym temacie.

## Aktywacja usługi Rights Management
Użyj jednej z następujących procedur do aktywacji [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].

> [!TIP]
> Można również użyć polecenia cmdlet programu Windows PowerShell, [aplikacją Aadrm Włącz](http://msdn.microsoft.com/library/windowsazure/dn629412.aspx), aby uaktywnić [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].

#### Aby aktywować usługę Rights Management z Centrum administracyjnym usługi Office 365

1.  Po zarejestrowaniu na plan usługi Office 365, który uwzględnia Rights Management [zalogować się do usługi Office 365 za pomocą konta służbowego](https://portal.office.com/) czyli administrator wdrożenia usługi Office 365.

2.  Jeżeli w Centrum administracyjnym usługi Office 365 nie wyświetla automatycznie, wybierz ikonę uruchamiania aplikacji w lewym górnym i wybierz polecenie **Admin**.**Admin** kafelka pojawia się tylko dla administratorów usługi Office 365.

    > [!TIP]
    > Administrator Centrum pomocy, zobacz [Centrum administracyjne dotyczące usługi Office 365 — pomoc administratora](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547).

3.  W lewym okienku rozwiń węzeł **Ustawienia usługi**.

4.  Kliknij przycisk **Rights Management**.

    > [!NOTE]
    > Jeśli ta opcja nie jest dostępna, być może usługa wersja planu lub produktu nie obsługują zarządzanie prawami lub go nie została jeszcze uaktualniona do obsługi zarządzania prawami.
    > 
    > Informacje zawarte w [Subskrypcje chmury, które obsługują Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) w sekcji [Wymagania dotyczące systemu Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tematu, aby potwierdzić pomocy technicznej. Jeśli wersja planu lub produktu usługa jest obsługiwana, ale opcja Rights Management nie jest dostępna, może to być, ponieważ usługa nie jest jeszcze uaktualniona. Aby uzyskać pomoc dotyczącą tego problemu, Wyślij wiadomość e-mail do [askipteam](mailto:askipteam@microsoft.com?subject=I%20cannot%20activate%20RMS).

5.  Na **RIGHTS MANAGEMENT** kliknij **Zarządzaj**.

6.  Na **zarządzania prawami dostępu** kliknij **aktywować**.

7.  Po wyświetleniu monitu **Czy chcesz aktywować usługę Rights Management?**, kliknij przycisk **aktywować**.

Powinien pojawić się **Rights management została aktywowana** i opcję, aby dezaktywować.

#### Aby aktywować usługę Rights Management z portalu Azure klasycznego

1.  Po zarejestrowaniu do konta systemu Azure [zalogować się do portalu Azure klasycznego](http://go.microsoft.com/fwlink/p/?LinkID=275081).

2.  W okienku po lewej stronie kliknij **usługi ACTIVE DIRECTORY**.

3.  Z **usługi active directory** kliknij **RIGHTS MANAGEMENT**.

4.  Wybierz katalog do zarządzania dla [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], kliknij przycisk **UAKTYWNIENIA**, a następnie potwierdź działanie.

    > [!NOTE]
    > Jeśli zostanie wyświetlony błąd aktywacji, może to być spowodowane nie obsługuje wersji planu lub produktu usługi [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].
    > 
    > Informacje zawarte w [Subskrypcje chmury, które obsługują Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) w sekcji [Wymagania dotyczące systemu Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) tematu, aby potwierdzić Obsługa usług RMS. Aby uzyskać pomoc dotyczącą tego problemu, Wyślij wiadomość e-mail do [askipteam](mailto:askipteam?subject=I%20cannot%20activate%20RMS).

**Stan zarządzania prawami** powinna być teraz wyświetlana **Active** i **UAKTYWNIENIA** opcja zostanie zastąpiony **DEZAKTYWUJ**.

### Wartości stanu zarządzania prawami i opisy w portalu Azure klasycznego
Oprócz **Active** stan, który wskazuje, że jest włączona usługa Rights Management i gotowe do użycia, mogą być również **nieaktywne**, **Unavailable**, lub **Brak autoryzacji**.

|Wartość stanu|Opis|
|-----------------|--------|
|**Aktywne**|[!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] jest włączony i gotowy do użycia.|
|**Nieaktywne**|[!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] jest wyłączone i musi być aktywowany zanim organizacji można chronić pliki.|
|**Niedostępny**|[!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] Usługa nie działa. Spróbuj ponownie później.|
|**Brak autoryzacji**|Nie masz uprawnień do wyświetlania stanu [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] usługi. Na przykład Twoje konto jest zablokowane lub nie jesteś administratorem globalnym dla wybranego dzierżawcy.|

## <a name="BKMK_OnboardingControls"></a>Konfigurowanie dołączania kontrolek etapowe wdrożenia
Jeśli nie chcesz, aby wszyscy użytkownicy mogli bezpośrednio chronić pliki za pomocą usług Azure RMS, formanty dołączania użytkownika można skonfigurować za pomocą [Set AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx) polecenia środowiska Windows PowerShell. To polecenie można uruchomić przed lub po aktywacji usług Azure RMS.

> [!IMPORTANT]
> Aby użyć tego polecenia, użytkownik musi mieć co najmniej wersji **2.1.0.0** z [modułu PowerShell platformy Windows Azure RMS](http://go.microsoft.com/fwlink/?LinkId=257721).
> 
> Sprawdzanie wersji zainstalowane, uruchom polecenie: **(Get-Module aadrm –ListAvailable).Version**

Na przykład chcąc początkowo tylko administratorzy w grupie "Działu IT" (który ma identyfikator obiektu fbb99ded-32a0-45f1-b038-38b519009503) można chronić zawartość do celów testowych, użyj następującego polecenia:

```
Set-AadrmOnboardingControlPolicy – SecurityGroupObjectId fbb99ded-32a0-45f1-b038-38b519009503
```
Należy zauważyć, że ta opcja konfiguracji, należy określić grupę; Nie można określić poszczególnych użytkowników.

Lub, jeśli chcesz upewnić się, że tylko użytkownicy, którzy są poprawnie licencji na używanie usług Azure RMS można chronić zawartość:

```
Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $true
```
Korzystając z tych dołączania formantów, wszyscy użytkownicy w organizacji mogą wykorzystywać zawsze chronionej zawartości, który jest chroniony przez podzbiór użytkowników, ale nie będzie można zastosować sami ochrony informacji z aplikacji klienta. Na przykład, ich nie będą widoczne w swoich klientów Office domyślnych szablonów, które są automatycznie publikowane po aktywowaniu usług Azure RMS lub szablonów niestandardowych, które można konfigurować.  Aplikacje serwerowe, takie jak Exchange, można zaimplementować własnych formantów użytkownika dla integracji usług RMS na ten sam efekt.

## Następne kroki
Teraz, kiedy już aktywowany [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] dla danej organizacji, należy użyć [Mapa wdrożenia usługi zarządzania prawami systemu Azure](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) do sprawdzania, czy istnieją inne czynności konfiguracyjne, które należy zrobić przed można wdrożyć [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] użytkownikom i administratorom. Na przykład można użyć [szablonów niestandardowych](http://technet.microsoft.com/library/dn642472.aspx) w celu ułatwienia użytkownikom na stosowanie ochrony informacji w plikach Podłącz serwery lokalnego do używania [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] instalując [łącznika usług RMS](http://technet.microsoft.com/library/dn375964.aspx), i wdrożyć [Rights Management sharing application](http://technet.microsoft.com/library/jj585031.aspx) obsługującej ochronę wszystkich typów plików na wszystkich urządzeniach. Aby móc używać ich funkcje zarządzania prawami do informacji (IRM), usług Office, takich jak Exchange Online i SharePoint Online wymagać dodatkowej konfiguracji. Jednak w przypadku konfiguracja nie kroków, które trzeba zobacz [Za pomocą systemu Azure Rights Management](../Topic/Using_Azure_Rights_Management.md) operational wskazówki do obsługi pomyślne wdrożenie dla Twojej organizacji.

Informacje o działaniu aplikacji za pomocą [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], zobacz [Jak aplikacje obsługują Azure Rights Management](../Topic/How_Applications_Support_Azure_Rights_Management.md).

## Zobacz też
[Konfigurowanie Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

