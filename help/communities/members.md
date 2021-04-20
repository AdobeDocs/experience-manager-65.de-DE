---
title: Mitglieder und Gruppenverwaltungskonsolen
seo-title: Mitglieder und Gruppenverwaltungskonsolen
description: Zugriff auf Mitglieder- und Gruppenverwaltungskonsolen
seo-description: Zugriff auf Mitglieder- und Gruppenverwaltungskonsolen
uuid: 2e93e861-a066-4189-91db-f8b784bc5aea
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: ccabf301-b417-48aa-8501-8360fd9f3e36
role: Administrator
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '964'
ht-degree: 4%

---


# Mitglieder und Gruppen-Management-Konsolen {#members-groups-management-consoles}

## Überblick {#overview}

Für AEM Communities-Funktionen müssen Site-Besucher oft registriert und angemeldet sein, bevor sie an einer Community in der Umgebung teilnehmen. Ihre Benutzerregistrierung muss nur in der Veröffentlichungs-Umgebung vorhanden sein. Sie werden häufig als *Member* bezeichnet, um sie von *Benutzern, die in der Authoring-Umgebung registriert sind, zu unterscheiden.*

### Mitglieder (Benutzer) bei Veröffentlichung {#members-users-on-publish}

Mithilfe der Communities-Mitglieder- und -Gruppenkonsolen können Mitglieder und Mitgliedsgruppen, die in der *publish*-Umgebung registriert sind, aus der *author*-Umgebung erstellt und verwaltet werden. Dies ist nur möglich, wenn der [Tunneldienst](deploy-communities.md#tunnel-service-on-author) aktiviert ist.

### Benutzer unter Autor {#users-on-author}

Für die Verwaltung von Benutzern und Gruppen, die in der *author*-Umgebung registriert sind, ist die Sicherheitskonsole der Plattform erforderlich:

* Wählen Sie in der globalen Navigation **[!UICONTROL Tools]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]**.
* Wählen Sie in der globalen Navigation **[!UICONTROL Tools]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Gruppen]**.

>[!NOTE]
>
>Wenn Beispielinhalte bereitgestellt und aktiviert sind, gibt es viele Beispielbenutzer sowohl in der Autor- als auch in der Veröffentlichungs-Umgebung. Diese Benutzer sind nicht vorhanden, wenn sie mit [nosampleContent runmode](../../help/sites-administering/production-ready.md) ausgeführt werden.

## Mitgliederkonsole {#members-console}

In der Umgebung &quot;Autor&quot;erreichen Sie die Mitgliederkonsole, um in der Umgebung &quot;Veröffentlichen&quot;registrierte Mitglieder zu verwalten:

* Wählen Sie in der globalen Navigation **[!UICONTROL Navigation]** > **[!UICONTROL Communities]** > **[!UICONTROL Mitglieder]**

>[!CAUTION]
>
>Die Mitgliederkonsole kann nicht verwendet werden, wenn der [Tunneldienst](deploy-communities.md#tunnel-service-on-author) nicht aktiviert ist.

![member-console1](assets/member-console1.png)

### Suche {#search-features}

Wählen Sie das Seitensymbol auf der linken Seite der `Members`-Kopfzeile aus, um das Suchseitenbedienfeld zu öffnen.

![](assets/leftpanel-icon.png)


![member-console2](assets/member-console2.png)

Wählen Sie das Suchsymbol auf der linken Seite der `Members`-Kopfzeile aus, um das Suchseitenbedienfeld zu schließen.

### Mitgliederstatistiken {#member-statistics}

Die Spalten `Views`, `Posts`, `Follows` und `Likes` werden aktualisiert, wenn der Benutzer Mitglied einer oder mehrerer Community-Sites mit aktiviertem Adobe Analytics [ist.](sites-console.md#analytics)

### CSV exportieren {#export-csv}

Wenn Sie den Link `Export CSV` auswählen, werden alle Mitglieder als Liste mit kommagetrennten Werten heruntergeladen, die für den Import in eine Tabelle geeignet sind.

Die Spaltenüberschriften sind

`| Screen Name |Last Name |First Name |Status |Views |Posts |Follows |Likes |`

## Neues Mitglied erstellen {#create-new-member}

Wählen Sie `Create Member` aus, um einen Benutzer in der Umgebung &quot;Veröffentlichen&quot;zu erstellen.

![create-member1](assets/create-member1.png)

### ALLGEMEINE - Mitgliederdetails {#general-member-details}

Bei den meisten Feldern handelt es sich um optionale Felder, die das Mitglied später auf seinem Profil ausfüllen kann.

* **[!UICONTROL ID]**

(*Erforderlich*) Die autorisierbare ID ist die Anmelde-ID des Mitglieds.
Standardmäßig wird die ID auf den Wert der erforderlichen E-Mail-Adresse eingestellt.
*Nach der Erstellung kann die ID nicht mehr geändert* werden.

* **[!UICONTROL E-Mail-Adresse]**

(*Erforderlich*) Die E-Mail-Adresse des Mitglieds.
Das Mitglied kann seine E-Mail-Adresse ändern, wenn es sein Profil aktualisiert.I
Wenn die ID standardmäßig auf die E-Mail-Adresse festgelegt ist, ändert sich die ID bei Änderung der E-Mail-Adresse.**

* **[!UICONTROL Kennwort]**

   (*Erforderlich*) Das Anmeldekennwort.

* **[!UICONTROL Kennwortwdh.]**

   (*Erforderlich*) Geben Sie das Kennwort zur Überprüfung erneut ein.

* **[!UICONTROL Mitglied zu Sites hinzufügen]**

   (*Optional*) Wählen Sie aus vorhandenen Community-Sites aus, um das Mitglied zur Mitgliedergruppe der Community-Site hinzuzufügen.

* **[!UICONTROL Mitglied zu Gruppen hinzufügen]**

   (*Optional*) Wählen Sie aus vorhandenen Mitgliedsgruppen aus, um das Mitglied dieser Gruppe hinzuzufügen.

* Wählen Sie **[!UICONTROL Speichern]** aus

### ALLGEMEIN - Kontoeinstellungen {#general-account-settings}

Unter &quot;Kontoeinstellungen&quot;kann ein Community-Administrator:

* **[!UICONTROL Status]**
   * Verboten
Ein Mitglied kann sich nicht anmelden, was verhindert, dass es Seiten anzeigt oder an Aktivitäten teilnimmt, für die eine Anmeldung erforderlich ist. Sie können immer noch anonym eine offene Community-Site besuchen.

   * Nicht verboten
Ein Mitglied hat vollen Zugriff auf die Community-Site.

   Der Standardwert ist `Not Banned`.

* **[!UICONTROL Anteilslimits]**

   Wenn diese Option aktiviert ist, ist die Fähigkeit des Mitglieds, Inhalte zu posten, eingeschränkt.
Der Standardwert hängt von der Konfiguration der Beitragsgrenzen ab.
Siehe [Mitgliederbeitragsbeschränkungen](limits.md).

* **[!UICONTROL Kennwort ändern]**

   Ein Link, der beim Ändern eines vorhandenen Mitglieds vorhanden ist. Bietet einem Community-Administrator die Möglichkeit, ein Kennwort für ein Mitglied zurückzusetzen.

### ALLGEMEIN - Foto {#general-photo}

Um einen Avatar für das Mitglied bereitzustellen, wählen Sie zunächst **[!UICONTROL Bild hochladen]** und wählen Sie dann ein Bild vom Typ .jpg, .png, .tif oder .gif. Die bevorzugte Größe eines Bildes ist 240 x 240 Pixel bei 72 dpi.

### ALLGEMEIN - Hinzufügen Mitglied bei Sites {#general-add-member-to-sites}

Das Mitglied kann einer oder mehreren Mitgliedergruppen der Community-Sites hinzugefügt werden. Beginnen Sie mit der Eingabe von Text in das Textfeld.

### ALLGEMEIN - Hinzufügen Mitglied bei Gruppen {#general-add-member-to-groups}

Das Mitglied kann einer oder mehreren Mitgliedergruppen hinzugefügt werden. Beginnen Sie mit der Eingabe von Text in das Textfeld.

### Registerkarte BADGES {#badges-tab}

Das Bedienfeld `BADGES` bietet die Möglichkeit, Kennzeichen manuell zuzuweisen und zu sperren. Die Abzeichen können für zugewiesene Rollen sowie für gewöhnlich verdiente Abzeichen verwendet werden.

Siehe auch [Scoring and Badges](implementing-scoring.md).

![create-member2](assets/create-member2.png)

* **[!UICONTROL hinzufügen]**
   * Geben Sie mit der Auswahl unter [Verfügbare Abzeichen](badges.md) an. Wählen Sie nach Auswahl eines Kennzeichens jede Website oder alle Sites aus, auf denen das Kennzeichen zusammen mit dem Avatar des Mitglieds angezeigt werden soll.
   * Es können mehrere Abzeichen und Sites ausgewählt werden.
* **[!UICONTROL Entfernen von Markierungen]**
   * Wählen Sie das Papierkorbsymbol neben einer Markierung aus, um sie zu entfernen.

## Gruppenkonsole {#groups-console}

Die in der Umgebung &quot;Autor&quot;verfügbare Gruppenkonsole ermöglicht die Erstellung und Verwaltung von in der Umgebung &quot;Veröffentlichen&quot;registrierten Mitgliedsgruppen. Sie ist besonders nützlich für:
* [Privilegierte Mitgliedergruppen](users.md#privilegedmembersgroups)
* Gruppenbasierte Zuweisung von [Aktivierungsressourcen](resources.md)

So greifen Sie auf die Konsole &quot;Gruppen&quot;zu:
* Wählen Sie in der globalen Navigation **[!UICONTROL Navigation]** > **[!UICONTROL Communities]** > **[!UICONTROL Gruppen]**.

>[!CAUTION]
>
>Die Konsole Gruppen kann nicht verwendet werden, wenn der [Tunneldienst](deploy-communities.md#tunnel-service-on-author) nicht aktiviert ist.

### Neue Gruppe erstellen {#create-new-group}

Wählen Sie `Add Group` aus, um eine Gruppe in der Umgebung &quot;Veröffentlichen&quot;zu erstellen.

![group-console1](assets/group-console1.png)

Die folgenden Felder sind zum Erstellen einer neuen Gruppe von Mitgliedern auf der Seite der Veröffentlichung erforderlich:

* **[!UICONTROL ID]**

   (*Erforderlich*) Die eindeutige ID der Gruppe.

   *Nach der Erstellung kann die ID nicht mehr geändert werden.*

* **[!UICONTROL Name]**

   (*Optional*) Der Anzeigename für die Gruppe.

   Der Standardwert ist die ID.

* **[!UICONTROL Beschreibung]**

   (*Optional*) Eine Beschreibung des Zwecks und der Berechtigungen der Gruppe.

* **[!UICONTROL Mitglieder zu Gruppe hinzufügen]**

   (*Optional*) Wählen Sie Veröffentlichungsseitige Mitglieder aus, die als erste Mitglieder der Gruppe aufgenommen werden sollen.

* Wählen Sie **[!UICONTROL Speichern]** aus

## Autorisierte Administratoren {#authorized-administrators}

Bei der Arbeit mit Mitgliedern in der Communities-Mitgliederkonsole ist es erforderlich, als Benutzer mit entsprechenden Berechtigungen angemeldet zu sein und den Replizierungsagenten, der vom [tunnel-Dienst](deploy-communities.md#tunnel-service-on-author) verwendet wird, korrekt zu konfigurieren.

Wenn der angemeldete Benutzer nicht als `admin` angemeldet ist, muss er Mitglied der Benutzergruppe `administrators` sein.

Siehe auch [Replizierungsagenten bei Autor](deploy-communities.md#replication-agents-on-author).
