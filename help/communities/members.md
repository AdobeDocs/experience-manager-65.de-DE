---
title: Mitglieder- und Gruppenverwaltungskonsolen
description: Zugreifen auf Mitglieder und Gruppen-Management-Konsolen
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: b64e24d2-8407-484c-8216-8d328ef5fa4f
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 2%

---


# Mitglieder- und Gruppenverwaltungskonsolen {#members-groups-management-consoles}

## Überblick {#overview}

AEM Communities-Funktionen erfordern oft, dass Besuchende einer Website registriert und angemeldet sind, bevor sie an einer Community in der Veröffentlichungsumgebung teilnehmen. Ihre Benutzerregistrierung muss nur in der Veröffentlichungsumgebung vorhanden sein und wird gemeinhin als &quot;*&quot; bezeichnet* um sie von &quot;*&quot;* unterscheiden.

### Mitglieder (Benutzer) in Publish {#members-users-on-publish}

Mithilfe der Konsolen „Mitglieder“ und „Gruppen“ von Communities können Mitglieder und Mitgliedergruppen, die in der *Publishing*-Umgebung registriert sind, in der *author*-Umgebung erstellt und verwaltet werden. Dies ist nur möglich, wenn [Tunneldienst](deploy-communities.md#tunnel-service-on-author) aktiviert ist.

### Benutzer in der Autoreninstanz {#users-on-author}

Zum Verwalten von Benutzern und Gruppen, die in der *author*-Umgebung registriert sind, müssen Sie die Sicherheitskonsole der Plattform verwenden:

* Wählen Sie in der globalen Navigation **[!UICONTROL Tools]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]**.
* Wählen Sie in der globalen Navigation **[!UICONTROL Tools]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Gruppen]**.

>[!NOTE]
>
>Wenn Beispielinhalte bereitgestellt und aktiviert sind, gibt es viele Beispielbenutzer sowohl in der Autoren- als auch in der Veröffentlichungsumgebung. Diese Benutzer sind beim Ausführen mit dem Ausführungsmodus [nosamplecontent](../../help/sites-administering/production-ready.md) nicht vorhanden.

## Mitglieder-Konsole {#members-console}

Gehen Sie in der Autorenumgebung wie folgt vor, um zur Mitgliederkonsole zu gelangen und Mitglieder zu verwalten, die in der Veröffentlichungsumgebung registriert sind:

* Wählen Sie in der globalen Navigation **[!UICONTROL Navigation]** > **[!UICONTROL Communities]** > **[!UICONTROL Mitglieder]**

>[!CAUTION]
>
>Es ist nicht möglich, die Mitglieder -Konsole zu verwenden, wenn [Tunneldienst](deploy-communities.md#tunnel-service-on-author) nicht aktiviert ist.

![Die Mitgliederkonsole](assets/member-console1.png)

### Suchen {#search-features}

Wählen Sie das Symbol für das seitliche Bedienfeld auf der linken Seite der `Members` Kopfzeile, um das seitliche Bedienfeld für die Suche zu öffnen.

![Symbol für seitliches Bedienfeld suchen.](assets/leftpanel-icon.png)


![Filteroptionen für die Mitgliederkonsole](assets/member-console2.png)

Wählen Sie das Suchsymbol links in der `Members` aus, um das seitliche Suchfeld ein-/auszuschalten.

### Mitgliederstatistik {#member-statistics}

Die Spalten mit `Views`, `Posts`, `Follows` und `Likes` werden aktualisiert, wenn der Benutzer Mitglied einer oder mehrerer Community-Sites mit Adobe Analytics ist [aktiviert](sites-console.md#analytics).

### CSV exportieren {#export-csv}

Wenn Sie den Link `Export CSV` auswählen, werden alle Elemente als durch Kommas getrennte Liste heruntergeladen, die in eine Tabelle importiert werden kann.

Die Spaltenüberschriften lauten

`| Screen Name |Last Name |First Name |Status |Views |Posts |Follows |Likes |`

## Neues Mitglied erstellen {#create-new-member}

Wählen Sie `Create Member` aus, um einen Benutzer in der Veröffentlichungsumgebung zu erstellen.

![Das Fenster Neues Mitglied erstellen](assets/create-member1.png)

### ALLGEMEIN - Details zum Mitglied {#general-member-details}

Die meisten Felder sind optionale Felder, die die Mitglieder später in ihrem Profil ausfüllen können.

* **[!UICONTROL ID]**

(*Erforderlich*) Die autorisierbare ID ist die Anmelde-ID des Mitglieds.
Standardmäßig ist die ID auf den Wert der erforderlichen E-Mail-Adresse festgelegt.
*Nach der Erstellung kann die ID nicht mehr geändert werden*.

* **[!UICONTROL E-Mail-Adresse]**

(*Erforderlich*) Die E-Mail-Adresse des Abonnenten.
Das Mitglied kann seine E-Mail-Adresse ändern, wenn es sein Profil aktualisiert.ID
Wenn die ID standardmäßig auf die E-Mail-Adresse festgelegt ist, ändert *ID*, wenn die E-Mail-Adresse geändert wird.

* **[!UICONTROL Kennwort]**

  (*Erforderlich*) Das Anmeldungskennwort.

* **[!UICONTROL Kennwortwdh.]**

  (*Erforderlich*) Geben Sie das Kennwort zur Überprüfung erneut ein.

* **[!UICONTROL Mitglied zu Sites hinzufügen]**

  (*Optional*) Wählen Sie aus vorhandenen Community-Sites aus, um das Mitglied der Mitgliedergruppe der Community-Site hinzuzufügen.

* **[!UICONTROL Mitglied zu Gruppen hinzufügen]**

  (*Optional*) Wählen Sie aus vorhandenen Mitgliedergruppen aus, um das Mitglied dieser Gruppe hinzuzufügen.

* Wählen Sie **[!UICONTROL Speichern]** aus

### ALLGEMEIN - Kontoeinstellungen {#general-account-settings}

Unter Kontoeinstellungen ist es für einen Community-Administrator möglich:

* **[!UICONTROL Status]**
   * Banned
Ein Mitglied kann sich nicht anmelden und kann daher keine Seiten anzeigen oder an Aktivitäten teilnehmen, für die eine Anmeldung erforderlich ist. Sie können weiterhin anonym eine offene Community-Site besuchen.

   * Nicht verboten
Ein Mitglied hat vollen Zugriff auf die Community-Site.

  Der Standardwert ist `Not Banned`.

* **[!UICONTROL Beitragsbeschränkungen]**

  Wenn diese Option aktiviert ist, ist die Möglichkeit des Nutzers, Inhalte zu posten, begrenzt.
Der Standardwert hängt von der Konfiguration der Beitragsbeschränkungen ab.
Siehe [Obergrenze für Mitgliedsbeiträge](limits.md).

* **[!UICONTROL Kennwort ändern]**

  Ein Link, der beim Ändern eines vorhandenen Elements vorhanden ist. Bietet die Möglichkeit für einen Community-Administrator, ein Kennwort für ein Mitglied zurückzusetzen.

### ALLGEMEIN - Foto {#general-photo}

Um einen Avatar für das Element bereitzustellen, wählen Sie zunächst **[!UICONTROL Bild hochladen]** und wählen Sie ein Bild des Typs .jpg, .png, .tif oder .gif aus. Die bevorzugte Größe für ein Bild ist 240 x 240 Pixel bei 72 dpi.

### ALLGEMEIN - Mitglied zu Sites hinzufügen {#general-add-member-to-sites}

Die Mitglieder können einer oder mehreren Community-Sites-Mitgliedergruppen hinzugefügt werden. Beginnen Sie, indem Sie Text in das Textfeld eingeben.

### ALLGEMEIN - Mitglied zu Gruppen hinzufügen {#general-add-member-to-groups}

Das Mitglied kann einer oder mehreren Mitgliedergruppen hinzugefügt werden. Beginnen Sie, indem Sie Text in das Textfeld eingeben.

### Registerkarte „Abzeichen“ {#badges-tab}

Das `BADGES` bietet die Möglichkeit, Abzeichen manuell zuzuweisen und zu widerrufen. Die Abzeichen können für zugewiesene Rollen und Abzeichen verwendet werden, die normalerweise verdient werden.

Siehe auch [Bewertung und Abzeichen](implementing-scoring.md).

![Das Fenster Mitgliedschaftseinstellungen bearbeiten](assets/create-member2.png)

* **[!UICONTROL Abzeichen hinzufügen]**
   * Beginnen Sie mit der Eingabe und wählen Sie aus [verfügbaren Abzeichen](badges.md) aus. Nachdem ein Abzeichen ausgewählt wurde, wählen Sie jede Website oder alle Websites aus, auf denen das Abzeichen zusammen mit dem Avatar des Mitglieds angezeigt werden soll.
   * Es können mehrere Abzeichen und Websites ausgewählt werden.
* **[!UICONTROL Abzeichen entfernen]**
   * Wählen Sie das Papierkorbsymbol neben einem Badge aus, um es zu entfernen.

## Gruppen-Konsole {#groups-console}

Die in der Autorenumgebung verfügbare Gruppenkonsole ermöglicht die Erstellung und Verwaltung von in der Veröffentlichungsumgebung registrierten Mitgliedergruppen. Dies ist besonders nützlich für [Privilegierte Mitgliedergruppen](users.md#privilegedmembersgroups).

So greifen Sie auf die Gruppenkonsole zu:
* Wählen Sie in der globalen Navigation **[!UICONTROL Navigation]** > **[!UICONTROL Communities]** > **[!UICONTROL Groups]**.

>[!CAUTION]
>
>Die Gruppenkonsole kann nicht verwendet werden, wenn der [Tunneldienst](deploy-communities.md#tunnel-service-on-author) nicht aktiviert ist.

### Neue Gruppe erstellen {#create-new-group}

Wählen Sie `Add Group` aus, um eine Gruppe in der Veröffentlichungsumgebung zu erstellen.

![Das Fenster Neue Gruppe erstellen](assets/group-console1.png)

Die erforderlichen Felder zum Erstellen einer Mitgliedergruppe auf der Veröffentlichungsseite sind:

* **[!UICONTROL ID]**

  (*Erforderlich*) Die eindeutige Gruppenkennung.

  *Nach der Erstellung kann die ID nicht mehr geändert werden.*

* **[!UICONTROL Name]**

  (*Optional*) Der Anzeigename für die Gruppe.

  Der Standardwert ist die ID.

* **[!UICONTROL Beschreibung]**

  (*Optional*) Eine Beschreibung des Zwecks und der Berechtigungen der Gruppe.

* **[!UICONTROL Mitglieder zu Gruppe hinzufügen]**

  (*Optional*) Wählen Sie Mitglieder auf Veröffentlichungsseite aus, die als erste Mitglieder der Gruppe aufgenommen werden sollen.

* Wählen Sie **[!UICONTROL Speichern]** aus

## Autorisierte Administratoren {#authorized-administrators}

Wenn Sie mit Mitgliedern in der Mitglieder-Konsole von Communities arbeiten, müssen Sie als Benutzer mit entsprechenden Berechtigungen angemeldet sein, und der vom [Tunneldienst](deploy-communities.md#tunnel-service-on-author) verwendete Replikationsagent muss ordnungsgemäß konfiguriert sein.

Wenn der angemeldete Benutzer nicht als `admin` angemeldet ist, muss er Mitglied der Benutzergruppe `administrators` sein.

Siehe auch [Replikationsagenten in der Autoreninstanz](deploy-communities.md#replication-agents-on-author).
