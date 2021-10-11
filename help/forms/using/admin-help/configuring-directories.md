---
title: Ordner konfigurieren
seo-title: Configuring directories
description: Erfahren Sie, wie Sie Ordner hinzufügen, bearbeiten und löschen und User Management für die virtuelle Listenansicht konfigurieren.
seo-description: Learn how to add, edit and delete directories and configure user management to use virtual list view.
uuid: 0bf1a8a7-c917-4248-9937-d24e31c5ba17
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 1f15f028-aa81-478e-97eb-f83a4dc0418c
exl-id: 30edcef2-e8fa-403a-9850-b8dfeeb9ac65
source-git-commit: 1cdd15800548362ccdd9e70847d9df8ce93ee06e
workflow-type: tm+mt
source-wordcount: '3227'
ht-degree: 78%

---

# Ordner konfigurieren {#configuring-directories}

Für jede Unternehmensdomäne, die Sie konfigurieren, geben Sie die Ordner an, aus denen der Authentifizierungsanbieter Benutzerdaten abfragt. Sie können mehrere Ordner für eine Domäne konfigurieren.

## Ordner oder benutzerdefinierte SPIs hinzufügen {#adding-directories-or-custom-spis}

Für jede Unternehmensdomäne, die Sie konfigurieren, geben Sie die Ordner an, aus denen der Authentifizierungsanbieter Benutzerdaten abfragt. Sie können einen Ordner zu einer bestehenden Unternehmensdomäne hinzufügen oder zu einer neuen Unternehmensdomäne, die Sie gerade hinzufügen. Sie können mehrere Ordner für eine Domäne konfigurieren. Sie können eine Domäne auch für die Verwendung einer benutzerdefinierten SPI (Service Provider Interface) zur Synchronisierung konfigurieren.

### Ordner hinzufügen {#add-a-directory}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domänenverwaltung“.
1. Klicken Sie auf „Neue Unternehmensdomäne“ oder wählen Sie eine bestehende Unternehmensdomäne aus.
1. Klicken Sie auf Verzeichnis hinzufügen.
1. Geben Sie im Feld „Profilname“ einen Namen ein, um diesen Ordner von anderen zu unterscheiden, und klicken Sie dann auf „Weiter“.
1. Konfigurieren Sie die Ordnerservereinstellungen. (Siehe [Ordnereinstellungen](configuring-directories.md#directory-settings).)
1. Klicken Sie auf „Testen“, um zu überprüfen, ob eine Verbindung mit dem LDAP-Server hergestellt werden kann. Um die Fehlerursache zu bestimmen, überprüfen Sie die Ausnahme in der Protokolldatei des Anwendungsservers. Klicken Sie auf „Schließen“ und dann auf „Weiter“.
1. Wählen Sie „Benutzereinstellungen“ aus und konfigurieren Sie die Einstellungen den Anforderungen entsprechend. (Siehe [Ordnereinstellungen](configuring-directories.md#directory-settings).)
1. Klicken Sie auf „Testen“, um zu prüfen, ob der Basis-DN und andere konfigurierte Attribute den richtigen Benutzerstapel abrufen. LDAP versucht, die ersten 200 Einträge unter Verwendung der angegebenen Einstellungen (wie Basis-DN, Suchfilter und allen Attributen) abzurufen.

   Wenn Benutzer zurückgegeben werden, zeigen die Ergebnisse die Werte, die jedem Feld gemäß der Attributfestlegung zugewiesen werden. Schlägt der Test fehl (wegen eines nicht existierenden Servernamens, falscher Autorisierungsinformationen oder falscher Attribute), wird die folgende Fehlermeldung angezeigt: „Die angegebenen Suchkriterien haben kein Ergebnis zurückgegeben.“ Um die Fehlerursache zu bestimmen, überprüfen Sie die Ausnahme in der Protokolldatei des Anwendungsservers. Klicken Sie auf „Schließen“ und dann auf „Weiter“.

1. Wählen Sie „Gruppeneinstellungen“ aus und konfigurieren Sie die Einstellungen den Anforderungen entsprechend. (Siehe [Ordnereinstellungen](configuring-directories.md#directory-settings).)
1. Klicken Sie auf „Testen“, um zu überprüfen, ob der Basis-DN und andere konfigurierte Attribute den richtigen Gruppenstapel abrufen. Wenn Gruppen zurückgegeben werden, zeigen die Ergebnisse die Werte, die jedem Feld gemäß der Attributfestlegung zugewiesen werden. Klicken Sie auf Schließen.

### Eine benutzerdefinierte SPI hinzufügen {#add-a-custom-spi}

Informationen zum Erstellen einer benutzerdefinierten SPI finden Sie unter „Entwickeln von SPIs für AEM Forms“ in [Programmieren mit AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63). Starten Sie den Server neu, damit eine neu bereitgestellte benutzerdefinierte SPI für die Verknüpfung mit der Domäne verfügbar wird.

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domänenverwaltung“.
1. Klicken Sie auf „Neue Unternehmensdomäne“ oder wählen Sie eine bestehende Unternehmensdomäne aus.
1. Klicken Sie auf Verzeichnis hinzufügen.
1. Geben Sie in das Feld „Profilname“ einen Namen ein oder wählen Sie die Option „Benutzerdefinierter SPI-Anbieter“ aus und klicken Sie auf „Weiter“.
1. Wählen Sie einen benutzerdefinierten Benutzeranbieter in der Liste aus und klicken Sie auf „Weiter“.
1. Wählen Sie einen benutzerdefinierten Gruppenanbieter in der Liste aus und klicken Sie auf „Fertig stellen“.

## Ordner bearbeiten {#edit-a-directory}

Sie können die Details eines bereits konfigurierten Ordners bearbeiten.

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domänenverwaltung“.
1. Klicken Sie in der Liste auf die gewünschte Domäne und wählen Sie auf der eingeblendeten Seite in der Liste den gewünschten Ordner aus.
1. Konfigurieren Sie die Ordner-, Benutzer- und Gruppeneinstellungen den Anforderungen entsprechend. (Siehe [Ordnereinstellungen](configuring-directories.md#directory-settings).)
1. Klicken Sie auf OK.

## Ordner löschen {#delete-a-directory}

Wenn Sie Ihre Domänen nach dem Löschen eines Ordners synchronisieren, werden alle Benutzer und Gruppen in der Datenbank als veraltet markiert. Sie werden bei keiner Suche von Administration Console zurückgegeben.

>[!NOTE]
>
>Unternehmensdomänen erfordern mindestens einen Authentifizierungs- und einen Ordneranbieter.

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domänenverwaltung“.
1. Wählen Sie die gewünschte Domäne in der Liste aus.
1. Aktivieren Sie das Kontrollkästchen neben dem gewünschten Ordner und klicken Sie auf „Löschen“.
1. Klicken Sie zuerst auf der angezeigten Bestätigungsseite auf „OK“ und dann erneut auf „OK“.

## Ordnereinstellungen {#directory-settings}

Wenn Sie einer Domäne einen Ordner hinzufügen, geben Sie die folgenden Ordnereinstellungen an.

**Server:**  (Obligatorisch) Vollqualifizierter Domänenname (FQDN) des Ordnerservers. Beispielsweise lautet der FQDN für einen Computer mit dem Namen x im Netzwerk adobe.com x.adobe.com. Anstelle des vollständig qualifizierten Servernamens kann auch eine IP-Adresse verwendet werden.

**Port:**  (Obligatorisch) Der Port, den der Ordnerserver verwendet. Dies ist in der Regel Anschluss 389 bzw. 636, falls das SSL-Protokoll (Secure Sockets Layer) zum Senden der Authentifizierungsinformationen über das Netzwerk verwendet wird.

**SSL:**  (Obligatorisch) Gibt an, ob der Ordnerserver SSL beim Senden von Daten über das Netzwerk verwendet. Die Standardeinstellung ist „Nein“. Wenn Sie „Ja“ wählen, muss das entsprechende LDAP-Serverzertifikat von der Java™-Umgebung (Java Runtime Environment) des Anwendungsservers als vertrauenswürdig betrachtet werden.

**Bindung**  (Obligatorisch) Gibt an, wie auf den Ordner zugegriffen wird.

**Anonym:** Es ist kein Benutzername oder Kennwort erforderlich. Anonyme Benutzer können nur eine begrenzte Datenmenge abrufen. Diese Option kann beim ersten Testing sinnvoll sein.

**Benutzer:** Authentifizierung ist erforderlich. Geben Sie im Feld „Name“ den Namen des Benutzereintrags an, der auf den Ordner zugreifen darf. Am besten geben Sie den vollständigen definierten  Namen (DN) des Benutzerkontos ein, z. B. cn=Jane Doe, ou=user, dc=can, dc=com. Geben Sie im Feld „Kennwort“ das zugehörige Kennwort an. Wenn Sie „Benutzer“ als Bindungsoption auswählen, sind diese Einstellungen obligatorisch.

**Name:** Name, der verwendet werden kann, um eine Verbindung zur LDAP-Datenbank herzustellen, wenn der anonyme Zugriff nicht aktiviert ist. Geben Sie für Active Directory 2003 `[domain name]\[userid]` an. Geben Sie für Sun™ One, eDirectory oder IBM Tivoli Directory Server den vollständig qualifizierten Benutzernamen, z. B. uid=lcuser,ou=it,o=company.com an.

**Kennwort:** Kennwort, das dem von Ihnen angegebenen Namen für die Verbindung mit der LDAP-Datenbank entspricht, wenn der anonyme Zugriff nicht aktiviert ist.

**Seite füllen mit:** Wenn diese Option aktiviert ist, werden Attribute auf den Seiten &quot;Benutzer- und Gruppeneinstellungen&quot;mit entsprechenden LDAP-Standardwerten gefüllt.

**Basis-DNs abrufen:** Ruft die Basis-DNs ab und zeigt sie in der Dropdownliste an. Diese Einstellung ist sinnvoll, wenn mehrere Basis-DNs vorhanden sind und Sie einen Wert auswählen müssen.

**Verweise aktivieren:** Diese Einstellung ist verfügbar, wenn Ihr Unternehmen mehrere in einer hierarchischen Struktur organisierte Active Directory-Domänen verwendet und Sie nur die Ordnereinstellungen für die übergeordnete Domäne angegeben haben. In diesem Fall kann User Management bei Aktivierung dieser Option auf Benutzer- und Gruppendetails in den untergeordneten Domänen zugreifen.

>[!NOTE]
>
>Klicken Sie auf „Testen“, um zu prüfen, ob eine Verbindung zum LDAP-Server hergestellt werden kann. Um die Fehlerursache zu bestimmen, überprüfen Sie die Ausnahme in der Protokolldatei des Anwendungsservers.

### Benutzereinstellungen {#user-settings}

**Eindeutige Kennung:**  (Obligatorisch) Ein eindeutiges und konstantes Attribut, das zur Identifizierung von Benutzern verwendet wird. Verwenden Sie als eindeutigen Bezeichner ein Nicht-DN-Attribut, da sich der definierte Name (DN) eines Benutzers ändern kann, wenn er in einen anderen Unternehmensbereich wechselt. Diese Einstellung hängt vom Ordnerserver ab. Der Wert ist objectGUID für Active Directory 2003, nsuniqueID für Sun™ One und guid für eDirectory.

>[!NOTE]
>
>Stellen Sie sicher, dass ein Attribut eingegeben wird, das in Ihrer Organisation garantiert eindeutig ist. Die Eingabe eines falschen Wertes kann zu schwerwiegenden Systemproblemen führen.

**Basis-DN:** Als Ausgangspunkt für die Synchronisierung von Benutzern und Gruppen aus der LDAP-Hierarchie festlegen. Es empfiehlt sich, einen Basis-DN auf der niedrigsten Hierarchieebene anzugeben, die sämtliche Benutzer und Gruppen enthält, die für Dienste synchronisiert werden müssen.

Wenn Sie in den Ordnereinstellungen „Verweise aktivieren“ ausgewählt haben, legen Sie die Option „Basis-DN“ auf den *dc*-Teil des definierten Namens (DN) fest. Damit der Verweis funktioniert, muss der Suchbereich sowohl über- als auch untergeordnete Domänen umfassen.

>[!NOTE]
>
>Diese Einstellung enthält nicht den definierten Namen (DN) des Benutzers. Um einen bestimmten Benutzer zu synchronisieren, wählen Sie die Einstellung „Suchfilter“.

Obwohl „Basis-DN“ eine obligatorische Einstellung in Administration Console ist, erfordern möglicherweise einige Ordnerserver, z. B. IBM Domino Enterprise Server, einen leeren Basis-DN. Um einen leeren Basis-DN anzugeben, exportieren Sie die Datei „config.xml“, bearbeiten Sie die Einstellung in dieser Datei und importieren Sie sie dann erneut. (Siehe [Konfigurationsdatei importieren und exportieren](/help/forms/using/admin-help/importing-exporting-configuration-file.md#importing-and-exporting-the-configuration-file).)

**Suchfilter:**  (Obligatorisch) Der Suchfilter, der verwendet werden soll, um den Datensatz zu finden, der dem Benutzer zugeordnet ist. Sie können eine Suche auf einer Ebene oder auf Unterebenen durchführen. (Siehe Syntax für Suchfilter oder RFC 2254.) Weitere Informationen für das Microsoft AD-Schema finden Sie unter Active Directory-Schema.

**Beschreibung:** Das Schemaattribut für die Beschreibung des Benutzers

**Vollständiger Name:**  (Obligatorisch) Das Schemaattribut für den vollständigen Namen des Benutzers

**Anmelde-ID:**  (Obligatorisch) Das Schemaattribut für die Anmelde-ID des Benutzers.

**Nachname:**  (Obligatorisch) Das Schemaattribut für den Nachnamen des Benutzers.

**Vorname:**  (Obligatorisch) Das Schemaattribut für den Vornamen des Benutzers

**Initialen:** Schemaattribut für die Initialen des Benutzers

**Geschäftskalender:** Ermöglicht die Zuordnung eines Geschäftskalenders zu einem Benutzer basierend auf dem Wert für diese Einstellung (Geschäftskalenderschlüssel). Im Geschäftskalender werden Arbeits- und freie Tage definiert. AEM Forms kann Geschäftskalender zum Berechnen künftiger Termine und Zeiten für Ereignisse wie Erinnerungen, Fristen und Eskalationen verwenden. Die Methode zum Zuweisen von Geschäftskalenderschlüsseln zu Benutzern ist davon abhängig, ob eine Unternehmens-, eine lokale oder eine Hybriddomäne verwendet wird. (Siehe Geschäftskalender konfigurieren.) 

 Wenn Sie eine Unternehmensdomäne verwenden, können Sie die Einstellung „Geschäftskalender“ einem Feld im LDAP-Ordner zuordnen. Wenn beispielsweise jeder Benutzerdatensatz in Ihrem Ordner ein Feld *country* enthält und Sie Geschäftskalender auf Grundlage des Landes zuweisen möchten, in dem sich der Benutzer befindet, geben Sie den Feldnamen *country* als Wert für die Einstellung „Geschäftskalender“ an. Anschließend können Sie die Geschäftskalenderschlüssel (die für das Feld *country* im LDAP-Ordner definierten Werte) Geschäftskalendern im Arbeitsablauf für Formulare zuordnen. 

 Der Platz zum Anzeigen des Namens des Geschäftskalenderschlüssels auf den Seiten des Arbeitsablaufs für Formulare ist begrenzt. Begrenzen Sie den Namen des Geschäftskalenderschlüssels auf weniger als 53 Zeichen, um zu verhindern, dass der Name auf diesen Seiten abgeschnitten wird.

**Zeitstempel ändern:** Um die Delta-Ordnersynchronisierung zu aktivieren, legen Sie diesen Wert fest, um TimeStamp zu ändern. (Siehe Delta-Ordnersynchronisierung aktivieren.)

**Organisation:** Das Schemaattribut für den Namen der Organisation, zu der der Benutzer gehört.

**Primäre E-Mail:** Das Schemaattribut für die primäre E-Mail-Adresse des Benutzers.

**Sekundäre E-Mail:** Schemaattribut für die sekundäre E-Mail-Adresse des Benutzers.

**Telefon:** Das Schemaattribut für die Telefonnummer des Benutzers.

**Postanschrift:** Das Schemaattribut für die Postanschrift des Benutzers.

**Gebietsschema:** Das Schemaattribut, das die Informationen zum ISO-Gebietsschema enthält. Das Schemaattribut ist ein aus zwei Buchstaben bestehender Sprachencode oder ein Sprachen- und Ländercode.

**Zeitzone:** Das Schemaattribut, das die Zeitzone enthält, in der sich der Benutzer befindet. Der Wert ist eine Zeichenfolge, z. B. City/Country.

**Virtual List View (VLV) Control aktivieren:** Ein LDAP-Steuerelement, mit dem AEM Formulare Daten stapelweise vom Ordnerserver abrufen können. Wenn Sie Sun One als LDAP-Ordner verwenden und der Ordner sehr viele Benutzer enthält, wird bei Aktivieren der VLV-Steuerung ein Index erstellt, den User Management zum Suchen von Benutzern verwenden kann. Diese Funktion ist nützlich, wenn ein normales Benutzerkonto verwendet wird, das nur eine begrenzte Datenmenge synchronisieren kann. Sie können die VLV-Steuerung auch für Gruppen aktivieren. Wenn Sie „VLV-Steuerung (Virtuelle Listenansicht) aktivieren“ auswählen, geben Sie im Feld „Sortierfeld“ einen Namen an.

>[!NOTE]
>
>Zum Aktivieren von VLV konfigurieren Sie Sun One. Siehe [User Management für die Verwendung der virtuellen Listenansicht (VLV)](configuring-directories.md#configure-user-management-to-use-virtual-list-view-vlv) konfigurieren.

**Sortierfeld:** Wenn Sie &quot;VLV-Steuerung (Virtuelle Listenansicht) aktivieren&quot;ausgewählt haben, geben Sie den Attributnamen an, der zum Sortieren des Index verwendet wird. Dieser Attributname (z. B. UID) ist der Name, den Sie beim Erstellen eines Indexes für die virtuelle Listenansicht auf dem Ordnerserver angegeben haben.

### Gruppeneinstellungen {#group-settings}

**Eindeutige Kennung:**  (Obligatorisch) Ein eindeutiges und konstantes Attribut, das zur Identifizierung von Gruppen verwendet wird. Verwenden Sie als eindeutigen Bezeichner ein Nicht-DN-Attribut. Diese Einstellung hängt vom Ordnerserver ab. Der Wert ist objectGUID für Active Directory 2003, nsuniqueID für Sun One und guid für eDirectory.

>[!NOTE]
>
>Stellen Sie sicher, dass ein Attribut eingegeben wird, das in Ihrer Organisation garantiert eindeutig ist. Die Eingabe eines falschen Wertes kann zu schwerwiegenden Systemproblemen führen.

**Basis-DN:**  (Obligatorisch) Der Distinguished Name des Ordners.

Obwohl „Basis-DN“ eine obligatorische Einstellung in Administration Console ist, erfordern einige Ordnerserver, z. B. IBM Domino Enterprise Server, einen leeren Basis-DN. Um einen leeren Basis-DN anzugeben, exportieren Sie die Datei „config.xml“, bearbeiten Sie die Einstellung in dieser Datei und importieren Sie sie dann erneut. (Siehe [Konfigurationsdatei importieren und exportieren](/help/forms/using/admin-help/importing-exporting-configuration-file.md#importing-and-exporting-the-configuration-file).)

**Suchfilter:**  (Obligatorisch) Der Suchfilter, der verwendet werden soll, um den Datensatz zu finden, der mit der Gruppe verknüpft ist. Sie können eine Suche auf einer Ebene oder auf Unterebenen durchführen.

**Beschreibung:** Das Schemaattribut für die Beschreibung der Gruppe

**Vollständiger Name:**  (Obligatorisch) Das Schemaattribut für den vollständigen Namen der Gruppe

**Mitglied-DN:**  (Obligatorisch) Das Schemaattribut für den Distinguished Name der Mitglieder in einer Gruppe

**Eindeutige Kennung des Mitglieds:** Eindeutige Kennung für einen Benutzer oder eine Gruppe, der bzw. die Mitglied der ausgewählten Gruppe ist. Dieser Wert hängt vom Ordnerserver ab. Der Wert ist objectSID für AD2003, nsuniqueID für Sun One und guid für eDirectory.

Wenn der Mitglieder-DN mit einem Nicht-DN-Attribut angegeben wird, verwendet User Management die Angabe für „Eindeutiger Bezeichner für Mitglied“ zum Abfragen von LDAP, um den DN des Benutzers zu erfassen, da dieser einem eindeutigen Bezeichnerwert entspricht.

Wird der DN als eindeutiger Bezeichner angegeben, muss „Eindeutiger Bezeichner für Mitglied“ nicht konfiguriert werden.

**Organisation:** Das Schemaattribut für den Namen der Organisation, zu der die Gruppe gehört

**Primäre E-Mail:** Schemaattribut für die primäre E-Mail-Adresse der Gruppe

**Sekundäre E-Mail:** Schemaattribut für die sekundäre E-Mail-Adresse der Gruppe

**Zeitstempel ändern:** Um die Delta-Ordnersynchronisierung zu aktivieren, legen Sie diesen Wert fest, um TimeStamp zu ändern. (Siehe Delta-Ordnersynchronisierung aktivieren.)

**Virtual List View (VLV) Control aktivieren:** Ein LDAP-Steuerelement, mit dem AEM Formulare Daten stapelweise vom Ordnerserver abrufen können. Wenn Sie Sun One als LDAP-Ordner verwenden und das Ordner sehr viele Gruppen enthält, wird bei Aktivieren der VLV-Steuerung ein Index erstellt, den User Management zum Suchen von Gruppen verwenden kann. Diese Funktion ist nützlich, wenn ein normales Benutzerkonto verwendet wird, das nur eine begrenzte Datenmenge synchronisieren kann. Sie können die VLV-Steuerung auch für Benutzer aktivieren. Wenn Sie „VLV-Steuerung (Virtuelle Listenansicht) aktivieren“ auswählen, geben Sie einen Sortierfeldnamen an.

>[!NOTE]
>
>Zum Aktivieren von VLV konfigurieren Sie Sun One. Siehe [User Management für die Verwendung der virtuellen Listenansicht (VLV)](configuring-directories.md#configure-user-management-to-use-virtual-list-view-vlv) konfigurieren.

**Sortierfeldname:** Wenn Sie &quot;VLV-Steuerung (Virtuelle Listenansicht) aktivieren&quot;ausgewählt haben, geben Sie den Attributnamen an, der zum Sortieren des Index verwendet wird. Dies ist der Attributname, den Sie beim Erstellen eines Indexes für die virtuelle Listenansicht auf dem Ordnerserver angegeben haben.

>[!NOTE]
>
>Klicken Sie auf „Testen“, um zu prüfen, ob die Benutzer- und Gruppeneinstellungen anhand des Basis-DN und der Suchkriterien abgerufen werden.

Wenn Benutzer und Gruppen zurückgegeben werden, zeigen die Ergebnisse die Werte, die jedem Feld gemäß der Attributfestlegung zugewiesen werden.

>[!NOTE]
>
>User Management unterstützt keine doppelten Benutzer-IDs innerhalb einer Domäne. Es wird nur ein Benutzer mit der Benutzer-ID synchronisiert.

## User Management mit der virtuellen Listenansicht (VLV) konfigurieren {#configure-user-management-to-use-virtual-list-view-vlv}

Eine wichtige Voraussetzung für User Management ist die Ordnersynchronisierung. Die Benutzer und Gruppen werden aus einem Unternehmensordner mit der AEM Forms-Datenbank synchronisiert, um Rollen und Berechtigungen zuzuweisen. Die Anzahl der Benutzer liegt (je nach Anforderung) zwischen 100 und über 100.000, was eine technische Herausforderung für eine effiziente Datensynchronisierung darstellt.

Das LDAP-Protokoll bietet in der Form von Anforderungssteuerelementen eine Möglichkeit zum seitenweisen Abarbeiten großer Ergebnismengen. Bei Verwendung von Microsoft Active Directory kommt bei der Synchronisierung zwischen LDAP und der AEM Forms-Datenbank PagedResultsControl zum Abrufen von Daten in Stapeln bestimmter Größe zum Einsatz. Dieses Steuerelement wird vom Sun ONE Directory Server nicht unterstützt. Zum Durchführen einer seitenweisen Abfrage des Sun ONE Directory Server verwenden Sie das VLV-Steuerelement (Virtual List View, virtuelle Listenansicht). Dieses Steuerelement beinhaltet sowohl eine ordnerserverseitige Konfiguration als auch eine clientseitige Implementierung.

>[!NOTE]
>
>In diesem Abschnitt wird die Verwendung des VLV-Steuerelements für den Sun ONE Directory Server beschrieben. Es kann jedoch jeder Ordnerserver, der das VLV-Steuerelement unterstützt, verwendet werden.

1. Wählen Sie beim Konfigurieren des Ordners die Option „VLV-Steuerung (Virtuelle Listenansicht) aktivieren“ sowohl auf der Seite „Benutzereinstellungen“ als auch auf der Seite „Gruppeneinstellungen“ aus. Wenn Sie das Kontrollkästchen aktivieren, müssen Sie außerdem in das Feld „Sortierfeldname“ einen Sortierfeldnamen eingeben. Der Standardwert ist „uid“. (Siehe [Ordner oder benutzerdefinierten SPIs hinzufügen](configuring-directories.md#adding-directories-or-custom-spis) oder [Ordner bearbeiten](configuring-directories.md#edit-a-directory).)
1. Verwenden Sie die Sun ONE Administration Console oder ein Befehlszeilenskript, um die LDAP-VLV-Einträge für Benutzer und Gruppen zu erstellen. Mithilfe eines Befehlszeilenskripts können die Benutzer- und Gruppen-LDIF-Beispieldateien verwendet werden. (Siehe [Sun ONE Directory Server für VLV konfigurieren](configuring-directories.md#configuring-the-sun-one-directory-server-for-vlv).)
1. Beenden Sie den Server und erstellen Sie den erforderlichen Index. (Siehe [Ordnerserverindex für VLV erstellen](configuring-directories.md#create-the-directory-server-index-for-vlv).)

### Sun ONE Directory Server für VLV konfigurieren {#configuring-the-sun-one-directory-server-for-vlv}

Zum Erstellen einer virtuellen Listenansicht muss ein Paar von Einträgen vorhanden sein, zu denen die Objektklassen `vlvSearch` und `vlvIndex` gehören. Der vlvSearch-Eintrag beinhaltet eine Suchbasis und das `vlvFilter`-Attribut, das die Objektklasse angibt, die die Attribute enthält, die sortiert werden sollen. Die Objektklasse `vlvIndex` enthält das Attribut `vlvSort` , das eines oder mehrere zu sortierende Attribute und die Reihenfolge ihrer Sortierung angibt. (Ein Minuszeichen (-) bedeutet umgekehrte alphabetische Reihenfolge). Für die Verwendung der virtuellen Listenansicht mit AEM Forms sind getrennte Einträge für Benutzer und Gruppen erforderlich.

>[!NOTE]
>
>Die Objekteinträge können über die grafische Benutzeroberfläche von Sun ONE oder mithilfe eines Befehlszeilenskripts erstellt werden. Anleitungen zum Erstellen der Objekteinträge mithilfe der grafischen Benutzeroberfläche finden Sie in der Sun ONE-Dokumentation.

Im Folgenden finden Sie eine Beispielskript-LDIF für VLV-Einträge für Benutzer:

```text
 dn: cn=lcuser,cn=userRoot,cn=ldbm database,cn=plugins,cn=config
 objectclass: top
 objectclass: vlvSearch
 cn: lcuser
 vlvBase: dc=corp,dc=adobe,dc=com
 vlvScope: 2
 vlvFilter: (&(objectclass=inetOrgPerson))
 aci: (target="ldap:///cn=lcuser,cn=userRoot,cn=ldbm database,cn=plugins,cn=config")(targetattr="*")(version 3.0; acl "Config"
 ;allow(read,search,compare) userdn="ldap:///all"; )
 dn: cn=lcuser,cn=lcuser,cn=userRoot,cn=ldbm database,cn=plugins,cn=config
 cn: lcuser
 vlvSort: cn
 objectclass: top
 objectclass: vlvIndex
```

**Objekteinträge mit einem Skript erstellen:**

1. Das Beispielskript enthält einen LDAP-Eintrag namens `lcuser`. Dieser Eintrag dient der VLV-bezogenen Konfiguration für die Benutzersynchronisierung in AEM Forms. Ändern Sie die folgenden Eigenschaften entsprechend:

   **Eintragname:** Der Name des Eintrags im Beispiel ist `lcuser`. Wenn `lcuser` geändert wird, muss er in allen Bereichen des Beispielskripts ebenfalls geändert werden.

   **vlvBase:** Der auf der Seite „Benutzereinstellungen“ angegebene Basis-DN.

   **vlvFilter:** Der auf der Seite „Benutzereinstellungen“ angegebene Suchfilter.

   **vlvSort:** Das auf der Seite „Benutzereinstellungen“ im Bereich mit den VLV-Einstellungen angegebene Sortierfeld. Für ein VLV-Steuerelement muss eine Sortiersteuerung angegeben werden. Dieses Feld wird dann als Sortierparameter für den erstellten vlv-Index verwendet.

   **aci:** Das im Beispiel angegebene Zugriffssteuerungselement erlaubt jedem authentifizierten Benutzer den Zugriff auf VLV-Indizes für Lese-, Such- und Vergleichsvorgänge. Der Administrator kann den Zugriff so einschränken, dass er an Benutzer gebunden ist, die auf der Seite für die Ordnerservereinstellungen in der User Management-Benutzeroberfläche konfiguriert sind. Wenn keine Berechtigungen gewährt sind, kann die Benutzersuche die virtuelle Listenansicht nicht verwenden und vom LDAP-Server wird eine Berechtigungsausnahme erzeugt.

   >[!NOTE]
   >
   >Als Konvention wird der vlvIndex-Eintragsname ebenfalls auf `lcuser` festgelegt, jedoch können Sie einen anderen Namen auswählen. Verwenden Sie denselben Namen wie im vlvindex-Tool. (Siehe [Ordnerserverindex für VLV erstellen ](configuring-directories.md#create-the-directory-server-index-for-vlv)*.)*

1. Erstellen Sie mit dem Tool `ldapmodify` im Funktionsumfang des Sun ONE-Servers einen ähnlichen Eintrag für Gruppen unter Verwendung des Basis-DN der jeweiligen Gruppe, des Suchfilters und des Sortierfeldes:

   `server directory\shared\bin>ldapmodify -v -a -h host -p port -D "admin user" -w "password" -f "LDIF file location"`

   Geben Sie beispielsweise folgenden Text ein:

   `D:\tools\ldap\sun\shared\bin> -v -a -h localhost -p 55850 -D "uid=admin,ou=administrators,ou=topologymanagement,o=netscaperoot" -w "admin" -f "D:\tools\ldap\data\vlv feature\users.ldif"`

### Ordnerserverindex für VLV erstellen {#create-the-directory-server-index-for-vlv}

Beenden Sie nach dem Konfigurieren der Ordnereinstellungen und dem Erstellen der LDAP-VLV-Einträge für Benutzer und Gruppen den Server und erstellen Sie den erforderlichen Index.

1. Im Anschluss an das Erstellen der Objekteinträge beenden Sie den Sun ONE Server.
1. Generieren Sie mit dem Tool „vlvindex“ den Index durch Eingabe des folgenden Textes:

   *Ordnerserverinstanz* `\vlvindex.bat -n userRoot -T lcuser`

   Folgende Ausgabe wird erzeugt:

   ```shell
    D:\tools\ldap\sun\shared\bin>..\..\slapd-chetanmeh-xp3\vlvindex.bat -n userRoot -T livecycle
    [21/Nov/2007:16:47:26 +051800] - userRoot: Indexing VLV: livecycle
    [21/Nov/2007:16:47:27 +051800] - userRoot: Indexed 1000 entries (5%).
    [21/Nov/2007:16:47:27 +051800] - userRoot: Indexed 2000 entries (9%).
    ...
    [21/Nov/2007:16:47:29 +051800] - userRoot: Indexed 20000 entries (94%).
    [21/Nov/2007:16:47:29 +051800] - userRoot: Indexed 21000 entries (99%).
    [21/Nov/2007:16:47:29 +051800] - userRoot: Finished indexing.
   ```

   Das vlvindex-Tool befindet sich im Ordner der Ordnerserverinstanz. Wenn der Sun ONE Server zwei Instanzen ausführt (server1 und server2), befindet sich das vlvindex-Tool im Ordner „*Sun ONE-Serverordner*\server1“. Der Wert für den Parameter `-T` ist der Wert des Attributs `cn` des vlvindex-Eintrags, der zuvor in der Beispiel-LDIF erstellt wurde. In diesem Beispiel ist er auf `lcuser` festgelegt.

1. Wenn die virtuelle Listenansicht für Gruppen aktiviert ist, muss auch der entsprechende Index für die Gruppen erstellt werden. Sie können dann überprüfen, ob die Indizes erstellt wurden, indem Sie folgenden Befehl ausführen:

   *Sun one server* `\shared\bin>ldapsearch -h`** `-p`*directoryhostport nr* `-s base -b "" objectclass=*`

   Folgende Ausgabe wird erzeugt (Beispieldaten):

   ```shell
    D:\tools\ldap\sun\shared\bin>ldapsearch.exe -h localhost -p 55850 -s base -b "" objectclass=*
    ldapsearch.exe: started Tue Nov 27 16:34:20 2007
    version: 1
    dn:
    objectClass: top
    namingContexts: dc=corp,dc=adobe,dc=com
    supportedExtension: 2.16.840.1.113730.3.5.7
    ...
    vlvsearch: cn=MCC ou=testdata dc=corp dc=adobe dc=com, cn=userRoot,cn=ldbm dat
        abase,cn=plugins,cn=config
    vlvsearch: cn=lcuser,cn=userRoot,cn=ldbm database,cn=plugins,cn=config
    vlvsearch: cn=Browsing ou=testdata,cn=userRoot,cn=ldbm database,cn=plugins,cn=
        config
    1 matches
   ```
