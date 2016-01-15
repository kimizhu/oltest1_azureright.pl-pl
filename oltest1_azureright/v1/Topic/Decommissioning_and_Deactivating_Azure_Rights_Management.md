---
description: na
keywords: na
title: Decommissioning and Deactivating Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0b1c2064-0d01-45ae-a541-cebd7fd762ad
---
# Likwidowanie i dezaktywowanie Azure Rights Management
Użytkownik ma zawsze kontrolę nad czy organizacji chroni zawartość za pomocą [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (usług Azure RMS), a jeśli okażą się już nie chcę używać tego rozwiązania ochrony informacji, konieczne jest zapewnienie, że nie można zablokować poza zawartość, która była wcześniej chroniona. Jeśli nie ma potrzeby ciągłego dostępu do zawartości chronionej wcześniej, po prostu dezaktywować usługę i pozwolić subskrypcji Azure Rights Management wygaśnie. Na przykład, powinien to być odpowiednie dla po zakończeniu testowania [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] przed wdrożeniem w środowisku produkcyjnym.

Jednakże jeśli wdrożono [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] w środowisku produkcyjnym, upewnij się, że mieć kopię klucza dzierżawy Azure Rights Management, aby dezaktywować usługę i to zrobić przed wygaśnięciem subskrypcji, ponieważ daje to pewność, że mogą zachować dostęp do zawartości, która była chroniona przez Azure Rights Management po usługa jest wyłączona. Jeśli używasz Przełącz własnego klucza rozwiązania (BYOK) gdzie Generowanie i zarządzanie klucz w sprzętowych modułów zabezpieczeń, trzeba będzie już klucz dzierżawy usługi Azure Rights Management. Ale jeśli został on zarządzany przez firmę Microsoft (ustawienie domyślne), zobacz instrukcje dotyczące eksportowanie klucza dzierżawy w [Operacje dla klucza dzierżawcy zarządzania prawami systemu Azure](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md) tematu.

> [!TIP]
> Nawet po wygaśnięciu subskrypcji dzierżawcy Azure Rights Management pozostaje dostępna umożliwiającego korzystanie z zawartości przez dłuższy czas. Jednak nie można wyeksportować klucz dzierżawcy.

Jeśli masz klucz dzierżawy usługi Azure Rights Management, można wdrożyć Rights Management (AD RMS) lokalnie i zaimportować klucz dzierżawcy jako zaufaną domenę publikacji (zaufaną domenę publikacji). Można wybrać następujące opcje likwidacji wdrożenia Azure Rights Management:

|Dotyczy to dla Ciebie...|… wykonaj następujące czynności:|
|----------------------------|------------------------------------|
|Wszyscy użytkownicy mają nadal używać Rights Management, ale używać rozwiązania lokalnego, a nie za pomocą usług Azure RMS →|Użyj [Set AadrmMigrationUrl](https://msdn.microsoft.com/library/azure/dn629429.aspx) bezpośrednie istniejących użytkowników do wdrożenia lokalnego, podczas gdy używają zawartości chronionej po tej zmianie przy użyciu polecenia cmdlet. Aby korzystać z zawartości chronionej użytkowników będzie automatycznie używać instalacji usług AD RMS.<br /><br />Aby użytkownicy mogli korzystać z zawartości, która była chroniona przed wprowadzeniem tej zmiany, przekierowanie klientów do lokalnego wdrożenia przy użyciu **LicensingRedirection** klucza rejestru dla pakietu Office 2016 lub Office 2013, zgodnie z opisem w [usługi odnajdowania sekcji](https://technet.microsoft.com/library/jj159267%28v=ws.10%29.aspx) w uwagi dotyczące wdrażania klienta usług RMS i **LicenseServerRedirection** klucza rejestru dla pakietu Office 2010, zgodnie z opisem w [ustawień rejestru Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
|Aby zatrzymać przy użyciu technologii Rights Management całkowicie →|Przyznaj określonego administratora [super prawa użytkownika](https://technet.microsoft.com/library/mt147272.aspx) i przypisz do tej osoby [Narzędzie ochrony usług RMS](http://www.microsoft.com/en-us/download/details.aspx?id=47256).<br /><br />Administrator może następnie narzędzie do zbiorczego odszyfrowywania plików w folderach, które były chronione przez usługę Azure Rights Management, aby powrócić do usunięcia ochrony plików i w związku z tym można czytać bez technologii zarządzania prawami dostępu, takich jak usług Azure RMS lub AD RMS. To narzędzie może służyć z usług Azure RMS i AD RMS, więc musisz wybrać odszyfrowywania plików przed lub Po dezaktywowaniu usług Azure RMS lub w połączeniu.|
|Nie jest możliwe zidentyfikować wszystkie pliki chronione za pomocą usług Azure RMS lub wszyscy użytkownicy, aby można było automatycznie odczytać chronionych plików, które zostały pominięte →|Wdrażanie ustawienie rejestru na wszystkich komputerach klienckich za pomocą **LicensingRedirection** klucza rejestru dla pakietu Office 2016 i pakietu Office 2013, zgodnie z opisem w [usługi odnajdowania sekcji](https://technet.microsoft.com/library/jj159267%28v=ws.10%29.aspx) w uwagi dotyczące wdrażania klienta usług RMS i **LicenseServerRedirection** klucza rejestru dla pakietu Office 2010, zgodnie z opisem w [ustawień rejestru urzędu](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).<br /><br />Również wdrożyć innego ustawienie rejestru, aby uniemożliwić użytkownikom ochrony nowych plików przez ustawienie **DisableCreation** do **1**, w sposób opisany w [ustawień rejestru Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
|Usługa odzyskiwania kontrolowanych, ręczne, dla wszystkich plików, które zostały pominięte →|Udzielanie wyznaczonym użytkownikom w grupie odzyskiwania danych [super prawa użytkownika](https://technet.microsoft.com/library/mt147272.aspx) i nadaj im [Narzędzie ochrony usług RMS](http://www.microsoft.com/en-us/download/details.aspx?id=47256) tak, aby mógł wyłączyć ochronę plików użytkownicy standardowi na żądanie.<br /><br />Na wszystkich komputerach, należy wdrożyć ustawienie, aby uniemożliwić użytkownikom ochrony nowych plików przez ustawienie rejestru **DisableCreation** do **1**, w sposób opisany w [ustawień rejestru Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
Aby uzyskać więcej informacji o procedurach w tej tabeli zobacz następujące zasoby:

-   Informacje dotyczące usługi AD RMS i odwołuje się do wdrożenia, zobacz [Omówienie usług zarządzania prawami dostępu Active Directory](https://technet.microsoft.com/library/hh831364.aspx).

-   Aby uzyskać instrukcje dotyczące importowania klucz dzierżawy usługi Azure RMS jako plik zaufaną domenę publikacji, zobacz [Dodawanie zaufanej domeny publikacji](https://technet.microsoft.com/library/cc771460.aspx).

-   Aby zainstalować moduł Windows PowerShell dla usług Azure RMS, aby ustawić adres URL migracji, zobacz [Instalowanie programu Windows PowerShell Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

Gdy wszystko będzie gotowe zdezaktywować service usług Azure RMS w organizacji, wykonaj następujące instrukcje.

## Dezaktywowania usługi Rights Management
Należy użyć jednej z poniższych procedur można wyłączyć opcję [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

> [!TIP]
> Można również użyć polecenia cmdlet programu Windows PowerShell, [aplikacją Aadrm Wyłącz](http://msdn.microsoft.com/library/windowsazure/dn629422.aspx), aby go dezaktywować [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].

#### Aby dezaktywować usługę Rights Management z Centrum administracyjnym usługi Office 365

1.  [Zalogować się do usługi Office 365 za pomocą konta służbowego](https://portal.office.com/) czyli administrator wdrożenia usługi Office 365.

2.  Jeżeli w Centrum administracyjnym usługi Office 365 nie wyświetla automatycznie, wybierz ikonę uruchamiania aplikacji w lewym górnym i wybierz polecenie **Admin**.**Admin** kafelka pojawia się tylko dla administratorów usługi Office 365.

    > [!TIP]
    > Administrator Centrum pomocy, zobacz [Centrum administracyjne dotyczące usługi Office 365 — pomoc administratora](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547).

3.  W lewym okienku rozwiń węzeł **Ustawienia usługi**.

4.  Kliknij przycisk **Rights Management**.

5.  Na **RIGHTS MANAGEMENT** kliknij **Zarządzaj**.

6.  Na **zarządzania prawami dostępu** kliknij **dezaktywować**.

7.  Po wyświetleniu monitu **Czy chcesz dezaktywować usługę Rights Management?**, kliknij przycisk **dezaktywować**.

Powinien pojawić się **Rights Management nie jest uaktywniona** i opcję aktywacji.

#### Aby dezaktywować z portalu Azure Rights Management

1.  Zaloguj się do [portalu Azure klasycznego](http://go.microsoft.com/fwlink/p/?LinkID=275081).

2.  W okienku po lewej stronie kliknij **usługi ACTIVE DIRECTORY**.

3.  Z **usługi active directory** kliknij **RIGHTS MANAGEMENT**.

4.  Wybierz katalog do zarządzania dla [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], kliknij przycisk **DEZAKTYWUJ**, a następnie potwierdź działanie.

**Stan zarządzania prawami** powinna być teraz wyświetlana **nieaktywne** i **DEZAKTYWUJ** opcja zostanie zastąpiony **UAKTYWNIENIA**.

## Zobacz też
[Konfigurowanie Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

