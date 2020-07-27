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
translation-type: tm+mt
source-git-commit: eb5317be52eec39b947ccb3c456d21d567ef2841
workflow-type: tm+mt
source-wordcount: '963'
ht-degree: 4%

---


# Mitglieder und Gruppenverwaltungskonsolen {#members-groups-management-consoles}

## Übersicht {#overview}

AEM Communities-Funktionen erfordern häufig, dass Site-Besucher registriert und angemeldet sind, bevor sie an einer Community in der Umgebung teilnehmen. Ihre Benutzerregistrierung muss nur in der Veröffentlichungs-Umgebung vorhanden sein. Sie werden häufig als *Mitglieder* bezeichnet, um sie von den in der Autorenversion registrierten *Benutzern* zu unterscheiden.

### Mitglieder (Benutzer) bei der Veröffentlichung {#members-users-on-publish}

Mithilfe der Community-Mitglieder- und -Gruppenkonsolen können in der *Veröffentlichungs* -Umgebung registrierte Mitglieder und Mitgliedsgruppen von der *AutorenUmgebung* erstellt und verwaltet werden. Dies ist nur möglich, wenn der [Tunneldienst](deploy-communities.md#tunnel-service-on-author) aktiviert ist.

### Benutzer im Autorenmodus {#users-on-author}

Für die Verwaltung der in der *Autor* -Umgebung registrierten Benutzer und Gruppen ist erforderlich, um die Sicherheitskonsole der Plattform zu verwenden:

* Wählen Sie in der globalen Navigation **[!UICONTROL Werkzeuge]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]**.
* Wählen Sie in der globalen Navigation **[!UICONTROL Werkzeuge]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Gruppen]**.

>[!NOTE]
>
>Wenn Beispielinhalte bereitgestellt und aktiviert sind, gibt es viele Beispielbenutzer sowohl in der Autor- als auch in der Veröffentlichungs-Umgebung. Diese Benutzer sind nicht vorhanden, wenn sie mit [nosampleContent-Ausführungsmodus](../../help/sites-administering/production-ready.md)ausgeführt werden.


## Mitgliederkonsole {#members-console}

In der Umgebung &quot;Autor&quot;erreichen Sie die Mitgliederkonsole, um in der Umgebung &quot;Veröffentlichen&quot;registrierte Mitglieder zu verwalten:

* Wählen Sie in der globalen Navigation **[!UICONTROL Navigation]** > **[!UICONTROL Communities]** > **[!UICONTROL Member]**

>[!CAUTION]
>
>Die Mitgliederkonsole kann nicht verwendet werden, wenn der [Tunneldienst](deploy-communities.md#tunnel-service-on-author) nicht aktiviert ist.


![member-console1](assets/member-console1.png)

### Suche {#search-features}

Klicken Sie auf das Symbol für das Seitenbedienfeld auf der linken Seite der `Members` Kopfzeile, um das Suchseitenbedienfeld zu öffnen.

![](assets/leftpanel-icon.png)


![member-console2](assets/member-console2.png)

Klicken Sie auf das Suchsymbol auf der linken Seite der `Members` Kopfzeile, um das Suchseitenbedienfeld zu schließen.

### Mitgliederstatistiken {#member-statistics}

Die Spalten `Views`, `Posts`und `Follows` werden aktualisiert, wenn der Benutzer Mitglied einer oder mehrerer Community-Sites ist, auf denen Adobe Analytics `Likes` aktiviert [](sites-console.md#analytics)ist.

### CSV exportieren {#export-csv}

Wenn Sie den `Export CSV` Link auswählen, werden alle Mitglieder als Liste mit kommagetrennten Werten heruntergeladen, die für den Import in eine Tabelle geeignet sind.

Die Spaltenüberschriften sind

`| Screen Name |Last Name |First Name |Status |Views |Posts |Follows |Likes |`

## Neues Mitglied erstellen {#create-new-member}

Wählen Sie diese Option, `Create Member` um einen Benutzer in der Umgebung &quot;Veröffentlichen&quot;zu erstellen.

![create-member1](assets/create-member1.png)

### ALLGEMEINE - Mitgliederdetails {#general-member-details}

Bei den meisten Feldern handelt es sich um optionale Felder, die das Mitglied später auf seinem Profil ausfüllen kann.

* **[!UICONTROL ID]**

(*Erforderlich*) Die autorisierbare ID ist die Anmelde-ID des Mitglieds.
Standardmäßig wird die ID auf den Wert der erforderlichen E-Mail-Adresse eingestellt.
*Nach der Erstellung kann die ID nicht mehr geändert* werden.

* **[!UICONTROL E-Mail-Adresse]**

(*Erforderlich*) Die E-Mail-Adresse des Mitglieds.
Das Mitglied kann seine E-Mail-Adresse beim Aktualisieren seines Profils ändern.Wenn die ID standardmäßig auf die E-Mail-Adresse gesetzt ist, ändert sich die ID *nicht* , wenn die E-Mail-Adresse geändert wird.

* **[!UICONTROL Kennwort]**

   (*Erforderlich*) Das Anmeldekennwort.

* **[!UICONTROL Kennwortwdh.]**

   (*Erforderlich*) Geben Sie das Kennwort zur Überprüfung erneut ein.

* **[!UICONTROL Mitglied zu Sites hinzufügen]**

   (*Optional*) Wählen Sie aus vorhandenen Community-Sites aus, um das Mitglied zur Mitgliedergruppe der Community-Site hinzuzufügen.

* **[!UICONTROL Mitglied zu Gruppen hinzufügen]**

   (*Optional*) Wählen Sie aus vorhandenen Mitgliedsgruppen aus, um das Mitglied dieser Gruppe hinzuzufügen.

* Wählen Sie **[!UICONTROL Speichern]** aus

### GENERAL - Account settings {#general-account-settings}

Unter &quot;Kontoeinstellungen&quot;kann ein Community-Administrator:

* **[!UICONTROL Status]**
   * Verbotene Benutzer Ein Mitglied kann sich nicht anmelden, was verhindert, dass es Seiten anzeigt oder an Aktivitäten teilnimmt, für die eine Anmeldung erforderlich ist. Sie können immer noch anonym eine offene Community-Site besuchen.

   * Nicht verbotenEin Mitglied hat vollen Zugriff auf die Community-Site.

   Der Standardwert ist `Not Banned`.

* **[!UICONTROL Anteilslimits]**

   Wenn diese Option aktiviert ist, ist die Fähigkeit des Mitglieds, Inhalte zu posten, eingeschränkt.
Der Standardwert hängt von der Konfiguration der Beitragsgrenzen ab.
Siehe [Mitgliederbeitragsbeschränkungen](limits.md).

* **[!UICONTROL Kennwort ändern]**

   Ein Link, der beim Ändern eines vorhandenen Mitglieds vorhanden ist. Bietet einem Community-Administrator die Möglichkeit, ein Kennwort für ein Mitglied zurückzusetzen.

### ALLGEMEIN - Foto {#general-photo}

Um einen Avatar für das Element bereitzustellen, wählen Sie zunächst &quot;Bild **[!UICONTROL hochladen&quot;]** und wählen Sie dann ein Bild vom Typ .jpg, .png, .tif oder .gif. Die bevorzugte Größe eines Bildes ist 240 x 240 Pixel bei 72 dpi.

### GENERAL - Add Member to Sites {#general-add-member-to-sites}

Das Mitglied kann einer oder mehreren Mitgliedergruppen der Community-Sites hinzugefügt werden. Beginnen Sie mit der Eingabe von Text in das Textfeld.

### GENERAL - Add Member to Groups {#general-add-member-to-groups}

Das Mitglied kann einer oder mehreren Mitgliedergruppen hinzugefügt werden. Beginnen Sie mit der Eingabe von Text in das Textfeld.

### Registerkarte &quot;BADGES&quot; {#badges-tab}

Das `BADGES` Bedienfeld bietet die Möglichkeit, Kennzeichen manuell zuzuweisen und zu sperren. Die Abzeichen können für zugewiesene Rollen sowie für gewöhnlich verdiente Abzeichen verwendet werden.

Siehe auch [Scoring und Badges](implementing-scoring.md).

![create-member2](assets/create-member2.png)

* **[!UICONTROL Hinzufügen]**
   * Geben Sie mit der Eingabe an, um aus den [verfügbaren Abzeichen](badges.md)auszuwählen. Wählen Sie nach Auswahl eines Kennzeichens jede Website oder alle Sites aus, auf denen das Kennzeichen zusammen mit dem Avatar des Mitglieds angezeigt werden soll.
   * Es können mehrere Abzeichen und Sites ausgewählt werden.
* **[!UICONTROL Entfernen von Markierungen]**
   * Wählen Sie das Papierkorbsymbol neben einer Markierung aus, um sie zu entfernen.

## Gruppenkonsole {#groups-console}

Die in der Umgebung &quot;Autor&quot;verfügbare Gruppenkonsole ermöglicht die Erstellung und Verwaltung von in der Umgebung &quot;Veröffentlichen&quot;registrierten Mitgliedsgruppen. Sie ist besonders nützlich für:
* [Privilegierte Mitgliedergruppen](users.md#privilegedmembersgroups)
* Gruppenbasierte Zuweisung von [Aktivierungsressourcen](resources.md)

So greifen Sie auf die Konsole &quot;Gruppen&quot;zu:
* Wählen Sie in der globalen Navigation **[!UICONTROL Navigation]** > **[!UICONTROL Communities]** > **[!UICONTROL Groups]**.

>[!CAUTION]
>
>Die Konsole Gruppen kann nicht verwendet werden, wenn der [Tunneldienst](deploy-communities.md#tunnel-service-on-author) nicht aktiviert ist.


### Neue Gruppe erstellen {#create-new-group}

Wählen Sie diese Option, `Add Group` um eine Gruppe in der Umgebung &quot;Veröffentlichen&quot;zu erstellen.

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

   (*Optional*) Wählen Sie Veröffentlichungsbasierte Mitglieder aus, die als erste Mitglieder der Gruppe aufgenommen werden sollen.

* Wählen Sie **[!UICONTROL Speichern]** aus

## Autorisierte Administratoren {#authorized-administrators}

Bei der Arbeit mit Mitgliedern in der Communities-Mitgliederkonsole ist es erforderlich, als Benutzer mit entsprechenden Berechtigungen angemeldet zu sein und den Replizierungsagenten, der vom [Tunneldienst](deploy-communities.md#tunnel-service-on-author) verwendet wird, korrekt zu konfigurieren.

Wenn der angemeldete Benutzer nicht als angemeldet angemeldet `admin`ist, muss er Mitglied der `administrators` Benutzergruppe sein.

Siehe auch [Replizierungsagenten beim Autor](deploy-communities.md#replication-agents-on-author).
