---
title: Verwaltungskonsolen für Mitglieder und Gruppen
seo-title: Verwaltungskonsolen für Mitglieder und Gruppen
description: Zugriff auf die Verwaltungskonsolen für Mitglieder und Gruppen
seo-description: Zugriff auf die Verwaltungskonsolen für Mitglieder und Gruppen
uuid: 2e93e861-a066-4189-91db-f8b784bc5aea
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: ccabf301-b417-48aa-8501-8360fd9f3e36
role: Administrator
exl-id: b64e24d2-8407-484c-8216-8d328ef5fa4f
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '963'
ht-degree: 4%

---

# Mitglieder und Gruppenverwaltungskonsolen {#members-groups-management-consoles}

## Überblick {#overview}

AEM Communities-Funktionen erfordern häufig, dass Besucher der Site registriert und angemeldet sind, bevor sie an einer Community in der Veröffentlichungsumgebung teilnehmen. Ihre Benutzerregistrierung muss nur in der Veröffentlichungsumgebung vorhanden sein. Sie werden häufig als *Mitglieder* bezeichnet, um sie von *Benutzern* zu unterscheiden, die in der Autorenumgebung registriert sind.

### Mitglieder (Benutzer) auf Publish {#members-users-on-publish}

Mithilfe der Communities Mitglieder und Gruppen-Konsolen können Mitglieder und Mitgliedergruppen, die in der Umgebung *publish* registriert sind, aus der Umgebung *author* erstellt und verwaltet werden. Dies ist nur möglich, wenn der [Tunneldienst](deploy-communities.md#tunnel-service-on-author) aktiviert ist.

### Benutzer in der Autoreninstanz {#users-on-author}

Für die Verwaltung von Benutzern und Gruppen, die in der Umgebung *author* registriert sind, ist die Verwendung der Sicherheitskonsole der Plattform erforderlich:

* Wählen Sie in der globalen Navigation **[!UICONTROL Tools]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]** aus.
* Wählen Sie in der globalen Navigation **[!UICONTROL Tools]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Gruppen]** aus.

>[!NOTE]
>
>Wenn Beispielinhalte bereitgestellt und aktiviert sind, gibt es viele Beispielbenutzer sowohl in der Autoren- als auch in der Veröffentlichungsumgebung. Diese Benutzer sind nicht vorhanden, wenn sie mit [nosamplecontent-Ausführungsmodus](../../help/sites-administering/production-ready.md) ausgeführt werden.

## Mitgliederkonsole {#members-console}

Um in der Autorenumgebung zur Mitgliederkonsole für die Verwaltung von in der Veröffentlichungsumgebung registrierten Mitgliedern zu gelangen, gehen Sie folgendermaßen vor:

* Wählen Sie in der globalen Navigation **[!UICONTROL Navigation]** > **[!UICONTROL Communities]** > **[!UICONTROL Mitglieder]**

>[!CAUTION]
>
>Es ist nicht möglich, die Mitgliederkonsole zu verwenden, wenn der [Tunneldienst](deploy-communities.md#tunnel-service-on-author) nicht aktiviert ist.

![member-console1](assets/member-console1.png)

### Suche {#search-features}

Wählen Sie auf der linken Seite der Kopfzeile `Members` das Symbol für das seitliche Bedienfeld aus, um das Bedienfeld für die Suchseite zu öffnen.

![](assets/leftpanel-icon.png)


![member-console2](assets/member-console2.png)

Wählen Sie das Suchsymbol auf der linken Seite der Kopfzeile `Members` aus, um den Bereich für die Suchseite zu schließen.

### Mitgliederstatistiken {#member-statistics}

Die Spalten, die `Views`, `Posts`, `Follows` und `Likes` anzeigen, werden aktualisiert, wenn der Benutzer Mitglied einer oder mehrerer Community-Sites mit Adobe Analytics [enabled](sites-console.md#analytics) ist.

### CSV exportieren {#export-csv}

Wenn Sie den Link `Export CSV` auswählen, werden alle Mitglieder als Liste kommagetrennter Werte heruntergeladen, die für den Import in eine Tabelle geeignet sind.

Die Spaltenüberschriften sind

`| Screen Name |Last Name |First Name |Status |Views |Posts |Follows |Likes |`

## Neues Mitglied erstellen {#create-new-member}

Wählen Sie `Create Member` aus, um einen Benutzer in der Veröffentlichungsumgebung zu erstellen.

![create-member1](assets/create-member1.png)

### ALLGEMEIN - Mitgliederdetails {#general-member-details}

Die meisten Felder sind optionale Felder, die das Mitglied später in seinem Profil ausfüllen kann.

* **[!UICONTROL ID]**

(*Erforderlich*) Die autorisierbare ID ist die Anmelde-ID des Mitglieds.
Standardmäßig ist die ID auf den Wert der erforderlichen E-Mail-Adresse gesetzt.
*Nach der Erstellung kann die ID nicht mehr geändert* werden.

* **[!UICONTROL E-Mail-Adresse]**

(*Erforderlich*) Die E-Mail-Adresse des Mitglieds.
Das Mitglied kann seine E-Mail-Adresse bei der Profilaktualisierung ändern.I
Wenn die Standard-ID die E-Mail-Adresse ist, ändert sich die Kennung *nicht*, wenn die E-Mail-Adresse geändert wird.

* **[!UICONTROL Kennwort]**

   (*Erforderlich*) Das Anmeldekennwort.

* **[!UICONTROL Kennwortwdh.]**

   (*Erforderlich*) Geben Sie das Kennwort zur Überprüfung erneut ein.

* **[!UICONTROL Mitglied zu Sites hinzufügen]**

   (*Optional*) Wählen Sie aus vorhandenen Community-Sites aus, um das Mitglied zur Mitgliedergruppe der Community-Site hinzuzufügen.

* **[!UICONTROL Mitglied zu Gruppen hinzufügen]**

   (*Optional*) Wählen Sie aus vorhandenen Mitgliedergruppen aus, um das Mitglied zu dieser Gruppe hinzuzufügen.

* Wählen Sie **[!UICONTROL Speichern]** aus

### ALLGEMEIN - Kontoeinstellungen {#general-account-settings}

Unter &quot;Kontoeinstellungen&quot;kann ein Community-Administrator Folgendes tun:

* **[!UICONTROL Status]**
   * Verboten
Ein Mitglied kann sich nicht anmelden, was es daran hindert, Seiten anzuzeigen oder an Aktivitäten teilzunehmen, bei denen eine Anmeldung erforderlich ist. Sie können weiterhin anonym eine offene Community-Site besuchen.

   * Nicht verboten
Ein Mitglied hat vollen Zugriff auf die Community-Site.

   Der Standardwert ist `Not Banned`.

* **[!UICONTROL Anteilslimits]**

   Wenn diese Option aktiviert ist, ist die Fähigkeit des Mitglieds, Inhalte zu posten, eingeschränkt.
Der Standardwert hängt von der Konfiguration der Beitragsbeschränkungen ab.
Siehe [Mitgliederbeitragsbeschränkungen](limits.md).

* **[!UICONTROL Kennwort ändern]**

   Ein Link, der beim Ändern eines vorhandenen Mitglieds vorhanden ist. Bietet die Möglichkeit für einen Community-Administrator, ein Kennwort für ein Mitglied zurückzusetzen.

### ALLGEMEIN - Foto {#general-photo}

Um einen Avatar für das Mitglied bereitzustellen, wählen Sie zunächst **[!UICONTROL Bild hochladen]** und wählen Sie ein Bild vom Typ .jpg, .png, .tif oder .gif. Die bevorzugte Größe für ein Bild ist 240 x 240 Pixel bei 72 dpi.

### ALLGEMEIN - Mitglieder zu Sites hinzufügen {#general-add-member-to-sites}

Das Mitglied kann zu einer oder mehreren Mitgliedergruppen der Community-Sites hinzugefügt werden. Geben Sie zunächst Text in das Textfeld ein.

### ALLGEMEIN - Mitglieder zu Gruppen hinzufügen {#general-add-member-to-groups}

Das Mitglied kann einer oder mehreren Mitgliedergruppen hinzugefügt werden. Geben Sie zunächst Text in das Textfeld ein.

### Registerkarte BADGES {#badges-tab}

Das Bedienfeld `BADGES` bietet die Möglichkeit, Abzeichen manuell zuzuweisen und zu widerrufen. Die Abzeichen können für zugewiesene Rollen sowie für gewöhnlich verdiente Abzeichen verwendet werden.

Siehe auch [Scoring und Abzeichen](implementing-scoring.md).

![create-member2](assets/create-member2.png)

* **[!UICONTROL Hinzufügen von Abzeichen]**
   * Beginnen Sie mit der Eingabe, um [verfügbare Badges](badges.md) auszuwählen. Nachdem ein Badge ausgewählt wurde, wählen Sie jede Website oder alle Sites aus, auf denen das Badge zusammen mit dem Avatar des Mitglieds angezeigt werden soll.
   * Es können mehrere Abzeichen und Sites ausgewählt werden.
* **[!UICONTROL Entfernen von Abzeichen]**
   * Wählen Sie das Papierkorbsymbol neben einem Zeichen aus, um es zu entfernen.

## Gruppenkonsole {#groups-console}

Die in der Autorenumgebung verfügbare Gruppenkonsole ermöglicht die Erstellung und Verwaltung von in der Veröffentlichungsumgebung registrierten Mitgliedergruppen. Dies ist besonders nützlich für:
* [Privilegierte Mitgliedergruppen](users.md#privilegedmembersgroups)
* Gruppenbasierte Zuweisung von [Aktivierungsressourcen](resources.md)

So greifen Sie auf die Gruppenkonsole zu:
* Wählen Sie in der globalen Navigation **[!UICONTROL Navigation]** > **[!UICONTROL Communities]** > **[!UICONTROL Gruppen]** aus.

>[!CAUTION]
>
>Die Gruppenkonsole kann nicht verwendet werden, wenn der [Tunneldienst](deploy-communities.md#tunnel-service-on-author) nicht aktiviert ist.

### Neue Gruppe erstellen {#create-new-group}

Wählen Sie `Add Group` aus, um eine Gruppe in der Veröffentlichungsumgebung zu erstellen.

![group-console1](assets/group-console1.png)

Die erforderlichen Felder zum Erstellen einer neuen veröffentlichungsseitigen Mitgliedergruppe sind:

* **[!UICONTROL ID]**

   (*Erforderlich*) Die eindeutige Kennung der Gruppe.

   *Nach der Erstellung kann die ID nicht mehr geändert werden.*

* **[!UICONTROL Name]**

   (*Optional*) Der Anzeigename für die Gruppe.

   Der Standardwert ist die ID.

* **[!UICONTROL Beschreibung]**

   (*Optional*) Eine Beschreibung des Zwecks und der Berechtigungen der Gruppe.

* **[!UICONTROL Mitglieder zu Gruppe hinzufügen]**

   (*Optional*) Wählen Sie veröffentlichungsseitige Mitglieder aus, die als anfängliche Mitglieder der Gruppe aufgenommen werden sollen.

* Wählen Sie **[!UICONTROL Speichern]** aus

## Autorisierte Administratoren {#authorized-administrators}

Bei der Arbeit mit Mitgliedern in der Mitgliederkonsole von Communities muss als Benutzer mit entsprechenden Berechtigungen angemeldet werden und der Replikationsagent, der vom [Tunneldienst](deploy-communities.md#tunnel-service-on-author) verwendet wird, muss ordnungsgemäß konfiguriert werden.

Wenn der angemeldete Benutzer nicht als `admin` angemeldet ist, muss er Mitglied der Benutzergruppe `administrators` sein.

Siehe auch [Replikationsagenten auf der Autoreninstanz](deploy-communities.md#replication-agents-on-author).
