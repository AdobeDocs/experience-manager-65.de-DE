---
title: Community-Site-Grundlagen
seo-title: Community-Site-Grundlagen
description: Exportieren und Löschen von Community-Sites und Erstellen benutzerdefinierter Site-Vorlagen
seo-description: Exportieren und Löschen von Community-Sites und Erstellen benutzerdefinierter Site-Vorlagen
uuid: f0ec0e71-64e9-415a-b14a-939a9b1611c1
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: dc7a085e-d6de-4bc8-bd7e-6b43f8d172d2
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Community-Site-Grundlagen {#community-site-essentials}

## Benutzerspezifische Site-Vorlage {#custom-site-template}

Eine benutzerdefinierte Site-Vorlage kann für jede Sprachkopie einer Community-Site separat angegeben werden.

Gehen Sie dazu wie folgt vor,

* Erstellen einer benutzerdefinierten Vorlage
* Überlagern des Standardpfads für die Site-Vorlage
* Hinzufügen der benutzerdefinierten Vorlage zum Überlagerungspfad
* Geben Sie die benutzerdefinierte Vorlage an, indem Sie eine `page-template` Eigenschaft zum `configuration` Knoten hinzufügen

**Standardvorlage**:

/**libs**/social/console/components/hbs/sitepage/**sitepage**.hbs

**Benutzerdefinierte Vorlage im Überlagerungspfad**:

/**apps**/social/console/components/hbs/sitepage/**&lt;*template-name*>**.hbs

**Eigenschaft**: page-template **Type**: Zeichenfolgenwert ****: &lt;*template-name*> (keine Erweiterung)

**Konfigurationsknoten**:

/content/&lt;*Community-Site-Pfad*>/&lt;*lang*>/configuration

Beispiel: /content/sites/engagement/de/configuration

>[!NOTE]
>
>Alle Knoten im überlagerten Pfad müssen nur vom Typ `Folder`sein.

>[!CAUTION]
>
>Wenn die benutzerdefinierte Vorlage den Namen *sitepage.hbs erhält,* werden alle Community-Sites angepasst.

### Beispiel für eine benutzerdefinierte Site {#custom-site-template-example}

Beispiel: `vertical-sitepage.hbs` Eine Sitevorlage, die dazu führt, dass Menülinks vertikal links unten auf der Seite platziert werden, anstatt horizontal unter dem Banner.

[Datei abrufen](assets/vertical-sitepage.hbs)Platzieren Sie die benutzerdefinierte Site-Vorlage im Überlagerungsordner:

/**apps**/social/console/components/hbs/sitepage/**vertical-site**.hbs

Identifizieren Sie die benutzerdefinierte Vorlage, indem Sie eine `page-template` Eigenschaft zum Konfigurationsknoten hinzufügen:

/content/sites/sample/de/configuration

![chlimage_1-80](assets/chlimage_1-80.png)

Stellen Sie sicher, dass Sie &quot;Alle **speichern** &quot;und benutzerdefinierten Code für alle AEM-Instanzen replizieren (benutzerspezifischer Code ist nicht enthalten, wenn der Inhalt der Community-Site in der Konsole veröffentlicht wird).

Es wird empfohlen, benutzerspezifischen Code zu replizieren, indem Sie ein Paket [erstellen](../../help/sites-administering/package-manager.md#creating-a-new-package) und es auf allen Instanzen bereitstellen.

## Exportieren einer Community-Site {#exporting-a-community-site}

Nachdem eine Community-Site erstellt wurde, ist es möglich, die Site als AEM-Paket zu exportieren, das im Package Manager gespeichert ist und zum Herunterladen und Hochladen verfügbar ist.

Diese ist in der [Communities Sites-Konsole](sites-console.md#exporting-the-site)verfügbar.

Beachten Sie, dass UGC und benutzerspezifischer Code nicht im Paket der Community-Site enthalten sind.

Verwenden Sie zum Exportieren von UGC das UGC-Migrationswerkzeug für [AEM Communities, ein Open Source-Migrationswerkzeug, das auf GitHub verfügbar ist](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration).

## Löschen einer Community-Site {#deleting-a-community-site}

Ab AEM Communities 6.3 Service Pack 1 wird das Symbol &quot;Site löschen&quot;angezeigt, wenn Sie den Mauszeiger über die Community-Site über Communities > Sites-Konsole bewegen. Wenn Sie während der Entwicklung eine Community-Site löschen und neu starten möchten, können Sie diese Funktion verwenden. Wenn Sie eine Community-Site löschen, werden die folgenden Elemente entfernt, die mit dieser Site verbunden sind:

* [UGC](#user-generated-content)
* [Benutzergruppen](#community-user-groups)
* [Assets](#enablement-assets)
* [Datenbankdatensätze](#database-records)

### Community Unique Site-ID {#community-unique-site-id}

Identifizieren der eindeutigen Site-ID, die mit der Community-Site verknüpft ist, mithilfe von CRXDE:

* Navigieren Sie zum Sprachstamm der Site, z. B. `/content/sites/*<site name>*/en/rep:policy`

* Suchen Sie den `allow<#>` Knoten mit einem `rep:principalName` im folgenden Format `rep:principalName = *community-enable-nrh9h-members*`

* Die Site-ID ist die dritte Komponente von `rep:principalName`Beispiel: `rep:principalName = community-enable-nrh9h-members`

   * **site name** = *enable*
   * **Site-ID** = *nrh9h*
   * **eindeutige Site-ID** = *enable-nrh9h*

### Benutzergenerierte Inhalte {#user-generated-content}

Besorgen Sie sich das Projekt Communities-srp-tools von Github:

* [https://github.com/Adobe-Marketing-Cloud/communities-srp-tools](https://github.com/Adobe-Marketing-Cloud/communities-srp-tools)

Dies enthält ein Servlet, um alle UGC aus einem SRP zu löschen.

Alle UGC können entfernt werden oder für eine bestimmte Site, z. B.:

* path=/content/usergenerated/asi/mongo/content/sites/engagement

Dadurch werden nur benutzergenerierte Inhalte (die in der Veröffentlichung eingegeben werden) und nicht verfasste Inhalte (die im Autor eingegeben wurden) entfernt. Daher sind [Schattenknoten](srp.md#shadownodes) nicht betroffen.

### Community-Benutzergruppen {#community-user-groups}

Suchen Sie in allen Autoren- und Veröffentlichungsinstanzen in der [Sicherheitskonsole](../../help/sites-administering/security.md)die [Benutzergruppen](users.md) , die folgende Elemente enthalten:

* Präfix mit `community`
* Nach [eindeutiger Site-ID](#community-unique-site-id)

Beispiel, `community-engage-x0e11-members`.

### Aktivierungselemente {#enablement-assets}

In der Hauptkonsole:

* Select **[!UICONTROL Assets]**
* Modus **[!UICONTROL auswählen]** aktivieren
* Wählen Sie den Ordner mit der [eindeutigen Site-ID](#community-unique-site-id)
* Wählen Sie **[!UICONTROL Löschen]** aus (unter **[!UICONTROL Mehr..]**).

### Datenbankdatensätze {#database-records}

Es gibt kein Werkzeug zum selektiven Löschen von Datenbankeinträgen für eine bestimmte Community-Site für die Aktivierung.

Wenn alle Community-Sites gelöscht werden, lassen Sie die Enablementdb und scormenginedb mit MySQL Workbench fallen.
