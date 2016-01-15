---
description: na
keywords: na
title: Operations for Your Azure Rights Management Tenant Key
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1284d0ee-0a72-45ba-a64c-3dcb25846c3d
---
# Operacje dla klucza dzierżawcy zarządzania prawami systemu Azure
W zależności od dzierżawy klucza topologii (zarządzanych przez firmę Microsoft lub zarządzane przez klienta) masz różne poziomy kontrolę i odpowiedzialność za klucza dzierżawy systemu Microsoft Azure Rights Management (Azure RMS) po jego implementacji.

Gdy zarządzasz kluczem dzierżawy to często jest określana jako Przesuń własny klucz (BYOK). Aby uzyskać więcej informacji dotyczących tego scenariusza i na dokonanie wyboru między topologii klucza dwóch dzierżawy, zobacz [Planowanie i wdrażanie swoim kluczem dzierżawcy zarządzania prawami Azure](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

W poniższej tabeli przedstawiono operacje, które można wykonać, w zależności od topologii wybrane dla klucza dzierżawy Azure RMS.

|Operacja cyklu życia|Zarządzany przez firmę Microsoft (domyślnie)|Zarządzane przez klienta (BYOK)|
|------------------------|------------------------------------------------|-----------------------------------|
|Unieważnij swoim kluczem dzierżawcy|(Automatycznie)|(Automatycznie)|
|Ponownie klucz swoim kluczem dzierżawcy|Tak|Tak|
|Wykonywanie kopii zapasowych i odzyskiwanie swojego klucza dzierżawcy|Nr|Tak|
|Eksportuj klucz dzierżawcy|Tak|Nr|
|Odpowiadanie na naruszenia|Tak|Tak|
Po zidentyfikowaniu topologii, który został zaimplementowany, należy użyć jednej z następujących sekcjach uzyskać więcej informacji na temat tych operacji dla klucza dzierżawy Azure RMS.

## <a name="BKMK_MSManagedOperations"></a>Zarządzany przez firmę Microsoft: Operacje klucza cyklem życia dzierżawcy
Jeśli firma Microsoft zarządza swoim kluczem dzierżawy Azure Rights Management (domyślnie), aby uzyskać więcej informacji na temat operacji cyklem życia, które odnoszą się do tego topologii należy użyć następujące sekcje:

-   [Unieważnij swoim kluczem dzierżawcy](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSRevoke)

-   [Ponownie klucz swoim kluczem dzierżawcy](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSRekey)

-   [Wykonywanie kopii zapasowych i odzyskiwanie swojego klucza dzierżawcy](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSBackup)

-   [Eksportuj klucz dzierżawcy](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSExport)

-   [Odpowiadanie na naruszenia](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSBreach)

### <a name="BKMK_MSRevoke"></a>Unieważnij swoim kluczem dzierżawcy
Możesz zrezygnować z otrzymywania Azure RMS, Azure RMS zatrzyma się przy użyciu swojego klucza dzierżawy i żadna akcja jest niezbędne od Ciebie.

### <a name="BKMK_MSRekey"></a>Ponownie klucz swoim kluczem dzierżawcy
Kluczy ponownych jest również znane jako klucz do poprzedniej. Nie ponownie kluczy swoim kluczem dzierżawy, chyba że jest naprawdę konieczne. Starsze klientów, takich jak Office 2010 nie są przeznaczone do obsługi protokołu zmian klucza. W tym scenariuszu można wyczyścić stanu usług RMS w komputerach z systemem za pomocą zasad grupy lub mechanizm równorzędne. Istnieją pewne wiarygodnego zdarzenia, które mogą wymagać ponownie klucz swoim kluczem dzierżawy. Na przykład:

-   Firmy został podzielony na dwie lub więcej firm. Jeśli klucz zostanie ponownie klucz dzierżawy, nowe firmy nie mają dostęp do nowej zawartości, która publikowania pracowników. Jeśli mają one kopię starego klucza dzierżawy mogą uzyskać dostęp stary zawartości.

-   Masz pewność, że główną kopię swoim kluczem dzierżawy (kopia w swojej posiadania) została naruszona.

Klucz dzierżawy można ponownie kluczy przez wywołanie usługi obsługi klienta firmy Microsoft (CSS) i potwierdzania administrator dzierżawy.

Jeśli klucz zostanie ponownie klucz dzierżawy, Nowa zawartość jest chroniony za pomocą nowego klucza dzierżawy. Miało to miejsce w sposób stopniowy, więc w danym okresie czasu niektóre nową zawartość będzie w dalszym ciągu być chronione przy użyciu starego klucza dzierżawy. Wcześniej chronionej zawartości pozostaje chronionej do Twojego starego klucza dzierżawy. Obsługa tego scenariusza, Azure RMS zachowuje Twojego starego klucza dzierżawy, aby go wystawić licencji dla starego zawartości.

### <a name="BKMK_MSBackup"></a>Wykonywanie kopii zapasowych i odzyskiwanie swojego klucza dzierżawcy
Firma Microsoft jest odpowiedzialny za wykonywanie kopii zapasowych kluczem dzierżawy i nie są wymagane przez nie akcje.

### <a name="BKMK_MSExport"></a>Eksportuj klucz dzierżawcy
Postępując zgodnie z instrukcjami w tych trzech krokach można wyeksportować swój Konfiguracja usług RMS Azure i klucz dzierżawy:

##### Krok 1: Inicjowanie eksportu

-   W tym celu należy skontaktować się z pomocy technicznej usługi klienta firmy Microsoft (CSS). Należy potwierdzić, że jesteś administratorem dla dzierżawy Azure RMS.

##### Krok 2: Poczekaj na potrzeby weryfikacji

-   Firma Microsoft sprawdza, czy żądanie zwolnienia swoim kluczem dzierżawy RMS wiarygodnego. Ten proces może potrwać do 3 tygodnie.

##### Krok 3: Otrzymasz instrukcje klucza z CSS

-   Usługi obsługi klienta firmy Microsoft (CSS) otrzymają Państwo swój Konfiguracja usług RMS Azure i klucz dzierżawy jako zaszyfrowane w chronionej hasłem pliku, który ma rozszerzenie nazwy pliku .tpd. W tym celu CSS najpierw wysyła do użytkownika (jako osoba zainicjowane eksportowanie) to narzędzie pocztą e-mail. To narzędzie musi być uruchamiany z wiersza polecenia w następujący sposób:

    ```
    AadrmTpd.exe -createkey
    ```
    Generuje parę kluczy RSA i zapisuje połowy publiczny i prywatny, gdy pliki w bieżącym folderze. Na przykład: **PublicKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt** i **PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt**.

    Odpowiedz na wiadomość e-mail od CSS, dołączyć plik, który zawiera nazwę, która rozpoczyna się od **PublicKey**. CSS obok otrzymają Państwo pliku publikacji jako plik XML, który jest szyfrowana za pomocą klucza RSA. Skopiować ten plik do tego samego folderu, ponieważ pierwotnie uruchomił narzędzie AadrmTpd i uruchomić narzędzie ponownie, używając pliku, który rozpoczyna się od **PrivateKey** i pliku z CSS. Na przykład:

    ```
    AadrmTpd.exe -key PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt -target TPD-77172C7B-8E21-48B7-9854-7A4CEAC474D0.xml
    ```
    Dane wyjściowe tego polecenia powinny być dwa pliki: Jedno zawiera hasła w postaci zwykłego tekstu dla publikacji chronionej hasłem, a drugi jest chroniony hasłem publikacji automatycznie. Dla odwołania krzyżowe celów, zarówno powinien być ten sam identyfikator GUID publiczny i prywatny klucza plików z kiedy uruchomiono polecenie - createkey AadrmTpd.exe:

    -   Password-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt

    -   ExportedTPD-FA29D0FE-5049-4C8E-931B-96C6152B0441.xml

    Te pliki kopii zapasowych i przechowują je bezpiecznie, aby upewnić się, można nadal odszyfrować zawartości, które są chronione przy użyciu tego klucza dzierżawy. Ponadto, jeśli są migrowane do usług AD RMS, można zaimportować ten plik publikacji (plik, który rozpoczyna się od **ExportedTDP**) z serwerem usług AD RMS.

##### Krok 4: Bieżące: Chroń swój klucz dzierżawcy

-   Po otrzymaniu swoim kluczem dzierżawy zachować dobrze zabezpieczona, ponieważ jeśli ktoś uzyskuje dostęp do niego, ich odszyfrować wszystkie dokumenty, które są chronione przy użyciu tego klucza.

    Jeśli przyczyną dla eksportowanie klucza dzierżawy jest już nie chcesz użyć Azure RMS najlepszym rozwiązaniem, teraz dezaktywować dzierżawą RMS. Nie opóźnienie po otrzymaniu swoim kluczem dzierżawy, ponieważ w ten sposób może pomóc w celu zminimalizowania konsekwencje, jeśli klucz dzierżawy jest dostępna przez osób, które nie powinny mieć w ten sposób. Aby uzyskać instrukcje, zobacz [Likwidowanie i dezaktywowanie Azure Rights Management](../Topic/Decommissioning_and_Deactivating_Azure_Rights_Management.md).

### <a name="BKMK_MSBreach"></a>Odpowiadanie na naruszenia
Brak systemu zabezpieczeń, niezależnie od tego, jak silne, zostanie zakończona bez naruszenia proces odpowiedzi. Klucz dzierżawy mogą ujawnienia lub kradzieży. Nawet wtedy, gdy jest dobrze chroniony poprawnie, luk w zabezpieczeniach można znaleźć w bieżącej generacji HSM technologii lub bieżącego długość klucza i algorytmów.

Firma Microsoft ma dedykowanego zespołu reagowania na zagrożenia bezpieczeństwa w swoich produktów i usług. Jak jest wiarygodne raportu incydentu, ten zespół uczestniczy do sprawdzania, czy zakres, przyczynę i czynniki. Jeśli ten incydent ma wpływ na Twoje zasoby, następnie Microsoft powiadomi użytkownika Administratorzy dzierżawy Azure RMS pocztą e-mail przy użyciu podanej podczas subskrybowanego przez Ciebie adres.

Jeśli masz naruszenia najlepszych akcję, która zostanie lub firma Microsoft może zająć zależy od zakresu naruszenia; Firma Microsoft będzie współpracować z Tobą za pośrednictwem tego procesu. W poniższej tabeli przedstawiono niektóre typowe sytuacje i prawdopodobnie odpowiedzi, mimo że dokładne odpowiedzi będzie zależało od wszystkie informacje, które jest ujawniła podczas analizy.

|Opis zdarzenia|Prawdopodobnie odpowiedzi|
|------------------|-----------------------------|
|Klucz dzierżawy jest przecieku.|Ponownie kluczy swoim kluczem dzierżawy. Zobacz [Ponownie klucz swoim kluczem dzierżawcy](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSRekey) w tym temacie.|
|Nieautoryzowana lub złośliwe oprogramowanie, które otrzymały praw do korzystania z kluczem dzierżawy, ale nie pamięci klucza jest.|Klucz dzierżawy kluczy ponownych nie pomaga w tym miejscu i wymaga analizy przyczyn. Usterkę procesu lub oprogramowania jest odpowiedzialny za nieautoryzowana uzyskać dostęp, takiej sytuacji muszą być rozwiązane.|
|Usterki wykryte algorytm RSA długość klucza lub atakom metodą siłową stają się w praktyce jest to możliwe.|Firma Microsoft musi zaktualizować Azure RMS do obsługi nowych algorytmów i długimi kluczy, które są elastyczne i wydać polecenie wszystkich klientów do klucze dzierżawy.|

## <a name="BKMK_BYOKManagedOperations"></a>Zarządzane klienta: Operacje klucza cyklem życia dzierżawcy
Można zarządzać swoim kluczem dzierżawy Azure Rights Management (Udostępnij swój własny klucz lub BYOK, scenariusz), użyj następujących sekcjach uzyskać więcej informacji na temat operacji cyklem życia, które odnoszą się do tego topologii:

-   [Unieważnij swoim kluczem dzierżawcy](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKRevoke)

-   [Ponownie klucz swoim kluczem dzierżawcy](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKRekey)

-   [Wykonywanie kopii zapasowych i odzyskiwanie swojego klucza dzierżawcy](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKBackup)

-   [Eksportuj klucz dzierżawcy](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKExport)

-   [Odpowiadanie na naruszenia](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKBreach)

### <a name="BKMK_BYOKRevoke"></a>Unieważnij swoim kluczem dzierżawcy
Możesz zrezygnować z otrzymywania Azure RMS, Azure RMS zatrzyma się przy użyciu swojego klucza dzierżawy i żadna akcja jest niezbędne od Ciebie.

### <a name="BKMK_BYOKRekey"></a>Ponownie klucz swoim kluczem dzierżawcy
Kluczy ponownych jest również znane jako klucz do poprzedniej. Nie ponownie kluczy swoim kluczem dzierżawy, chyba że jest naprawdę konieczne. Starsze klientów, takich jak Office 2010 nie są przeznaczone do obsługi protokołu zmian klucza. W tym scenariuszu można wyczyścić stanu usług RMS w komputerach z systemem za pomocą zasad grupy lub mechanizm równorzędne. Istnieją pewne wiarygodnego zdarzenia, które mogą wymagać ponownie klucz swoim kluczem dzierżawy. Na przykład:

-   Firmy został podzielony na dwie lub więcej firm. Jeśli klucz zostanie ponownie klucz dzierżawy, nowe firmy nie mają dostęp do nowej zawartości, która publikowania pracowników. Jeśli mają one kopię starego klucza dzierżawy mogą uzyskać dostęp stary zawartości.

-   Masz pewność, że główną kopię swoim kluczem dzierżawy (kopia w swojej posiadania) została naruszona.

Jeśli klucz zostanie ponownie klucz dzierżawy, Nowa zawartość jest chroniony za pomocą nowego klucza dzierżawy. Miało to miejsce w sposób stopniowy, więc w danym okresie czasu niektóre nową zawartość będzie w dalszym ciągu być chronione przy użyciu starego klucza dzierżawy. Wcześniej chronionej zawartości pozostaje chronionej do Twojego starego klucza dzierżawy. Obsługa tego scenariusza, Azure RMS zachowuje Twojego starego klucza dzierżawy, aby go wystawić licencji dla starego zawartości.

Aby ponownie klucz swoim kluczem dzierżawy, generowanie i utworzony nowy klucz przez Internet lub osobiście, korzystając z procedur w [Implementing bring your own key (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) sekcji z [Planowanie i wdrażanie swoim kluczem dzierżawcy zarządzania prawami Azure](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) tematu.

### <a name="BKMK_BYOKBackup"></a>Wykonywanie kopii zapasowych i odzyskiwanie swojego klucza dzierżawcy
Użytkownik jest odpowiedzialny za wykonywanie kopii zapasowych kluczem dzierżawy. Klucz dzierżawy jest generowana w HSM firmy Thales, do wykonania kopii zapasowej klucza, po prostu wykonać kopię zapasową pliku klucza Stokenizowana, plik światowej i Administrator kart.

Jeśli klucz jest przekazywane wykonując procedury w [Implementing bring your own key (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) sekcji z [Planowanie i wdrażanie swoim kluczem dzierżawcy zarządzania prawami Azure](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) tematu, Azure RMS będzie trwała Stokenizowana klucza pliku w celu ochrony przed awarii wszystkie węzły Azure RMS. Jednak nie należy wziąć pod uwagę to być pełna kopia zapasowa. Na przykład kiedykolwiek kopię klucza, aby używać poza HSM firmy Thales zwykłego tekstu, należy Azure RMS nie będzie można do pobrania dla Ciebie, ponieważ zawiera on tylko kopia nie będzie.

### <a name="BKMK_BYOKExport"></a>Eksportuj klucz dzierżawcy
Jeśli używasz BYOK, nie można wyeksportować klucza dzierżawy z Azure RMS. Nie będzie to kopią w Azure RMS. Jeśli chcesz usunąć ten klucz, więc nie można go używać, skontaktuj się z Obsługa usługi klienta firmy Microsoft (CSS).

### <a name="BKMK_BYOKBreach"></a>Odpowiadanie na naruszenia
Brak systemu zabezpieczeń, niezależnie od tego, jak silne, zostanie zakończona bez naruszenia proces odpowiedzi. Klucz dzierżawy mogą ujawnienia lub kradzieży. Nawet wtedy, gdy jest dobrze chroniony poprawnie, luk w zabezpieczeniach można znaleźć w bieżącej generacji HSM technologii lub bieżącego długość klucza i algorytmów.

Firma Microsoft ma dedykowanego zespołu reagowania na zagrożenia bezpieczeństwa w swoich produktów i usług. Jak jest wiarygodne raportu incydentu, ten zespół uczestniczy do sprawdzania, czy zakres, przyczynę i czynniki. Jeśli ten incydent ma wpływ na Twoje zasoby, następnie Microsoft powiadomi użytkownika Administratorzy dzierżawy Azure RMS pocztą e-mail przy użyciu podanej podczas subskrybowanego przez Ciebie adres.

Jeśli masz naruszenia najlepszych akcję, która zostanie lub firma Microsoft może zająć zależy od zakresu naruszenia; Firma Microsoft będzie współpracować z Tobą za pośrednictwem tego procesu. W poniższej tabeli przedstawiono niektóre typowe sytuacje i prawdopodobnie odpowiedzi, mimo że dokładne odpowiedzi będzie zależało od wszystkie informacje, które jest ujawniła podczas analizy.

|Opis zdarzenia|Prawdopodobnie odpowiedzi|
|------------------|-----------------------------|
|Klucz dzierżawy jest przecieku.|Ponownie kluczy swoim kluczem dzierżawy. Zobacz [Ponownie klucz swoim kluczem dzierżawcy](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKRekey) w tym temacie.|
|Nieautoryzowana lub złośliwe oprogramowanie, które otrzymały praw do korzystania z kluczem dzierżawy, ale nie pamięci klucza jest.|Klucz dzierżawy kluczy ponownych nie pomaga w tym miejscu i wymaga analizy przyczyn. Usterkę procesu lub oprogramowania jest odpowiedzialny za nieautoryzowana uzyskać dostęp, takiej sytuacji muszą być rozwiązane.|
|Usterka znalezionych w zakresie technologii HSM bieżącej generacji.|Microsoft, musisz zaktualizować HSM. W przypadku powód, aby przypuszczać, że luki narażony kluczy, firma Microsoft będzie poinstruowanie wszystkich klientów do klucze dzierżawy.|
|Usterki wykryte algorytm RSA długość klucza lub atakom metodą siłową stają się w praktyce jest to możliwe.|Firma Microsoft musi zaktualizować Azure RMS do obsługi nowych algorytmów i długimi kluczy, które są elastyczne i wydać polecenie wszystkich klientów do klucze dzierżawy.|

## Zobacz też
[Za pomocą systemu Azure Rights Management](../Topic/Using_Azure_Rights_Management.md)

