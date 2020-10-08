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
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 3%

---


# Community-Site-Grundlagen {#community-site-essentials}

## Benutzerspezifische Site-Vorlage {#custom-site-template}

Eine benutzerdefinierte Site-Vorlage kann für jede Sprachkopie einer Community-Site separat angegeben werden.

Gehen Sie dazu wie folgt vor:

* Erstellen Sie eine benutzerdefinierte Vorlage.
* Überlagern Sie den Standardpfad für die Site-Vorlage.
* hinzufügen die benutzerdefinierte Vorlage an den Überlagerungspfad.
* Geben Sie die benutzerdefinierte Vorlage an, indem Sie der `page-template` Node eine `configuration` Eigenschaft hinzufügen.

**Standardvorlage**:

`/libs/social/console/components/hbs/sitepage/sitepage.hbs`

**Benutzerdefinierte Vorlage im Überlagerungspfad**:

`/apps/social/console/components/hbs/sitepage/template-name.hbs`

**Eigenschaft**: page-template

**Typ**: String

**Wert**: `template-name` (keine Erweiterung)

**Konfigurationsknoten**:

`/content/community site path/lang/configuration`

Beispiel: `/content/sites/engage/en/configuration`

>[!NOTE]
>
>Alle Knoten im überlagerten Pfad müssen nur vom Typ `Folder`sein.

>[!CAUTION]
>
>Wenn der benutzerdefinierten Vorlage der Name *sitepage.hbs* zugewiesen wird, werden alle Community-Sites angepasst.

### Beispiel für eine benutzerdefinierte Site {#custom-site-template-example}

Beispiel: `vertical-sitepage.hbs` Eine Sitevorlage, die dazu führt, dass Menülinks vertikal links unten auf der Seite platziert werden, anstatt horizontal unterhalb des Banners.

[Datei abrufen](assets/vertical-sitepage.hbs)Platzieren Sie die benutzerdefinierte Site-Vorlage im Überlagerungsordner:

`/apps/social/console/components/hbs/sitepage/vertical-sitepage.hbs`

Identifizieren Sie die benutzerdefinierte Vorlage, indem Sie eine `page-template` Eigenschaft zum Konfigurationsknoten hinzufügen:

`/content/sites/sample/en/configuration`

![crxde-siteconfiguration](assets/crxde-siteconfiguration.png)

Achten Sie darauf, &quot;Alle **speichern** &quot;zu verwenden und benutzerdefinierten Code in allen AEM Instanzen zu replizieren (benutzerspezifischer Code ist nicht enthalten, wenn der Inhalt der Community-Site in der Konsole veröffentlicht wird).

Es wird empfohlen, benutzerspezifischen Code zu replizieren, indem Sie ein Paket [erstellen](../../help/sites-administering/package-manager.md#creating-a-new-package) und es auf allen Instanzen bereitstellen.

## Exportieren einer Community-Site {#exporting-a-community-site}

Nachdem eine Community-Site erstellt wurde, ist es möglich, die Site als AEM Paket zu exportieren, das im Paketmanager gespeichert ist und zum Herunterladen und Hochladen verfügbar ist.

Diese ist in der [Communities Sites-Konsole](sites-console.md#exporting-the-site)verfügbar.

Beachten Sie, dass UGC und benutzerspezifischer Code nicht im Paket der Community-Site enthalten sind.

Um UGC zu exportieren, verwenden Sie das [AEM Communities UGC Migration Tool](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration), ein Open Source-Migrationswerkzeug, das auf GitHub verfügbar ist.

## Löschen einer Community-Site {#deleting-a-community-site}

Ab AEM Communities 6.3 Service Pack 1 wird das Symbol &quot;Site löschen&quot;angezeigt, wenn Sie den Mauszeiger über die Community-Site von **[!UICONTROL Communities]** > **[!UICONTROL Sites]** -Konsole führen. Wenn Sie während der Entwicklung eine Community-Site und einen Beginn löschen möchten, können Sie diese Funktion verwenden. Wenn Sie eine Community-Site löschen, werden die folgenden Elemente, die mit dieser Site verbunden sind, entfernt:

* [UGC](#user-generated-content)
* [Benutzergruppen](#community-user-groups)
* [Assets](#enablement-assets)
* [Datenbankdatensätze](#database-records)

### Community Unique Site-ID {#community-unique-site-id}

Identifizieren der eindeutigen Site-ID, die mit der Community-Site verknüpft ist, mithilfe von CRXDE:

* Navigieren Sie zum Sprachstamm der Site, z. B. `/content/sites/*<site name>*/en/rep:policy`.

* Suchen Sie den `allow<#>` Knoten mit einem `rep:principalName` in diesem Format `rep:principalName = *community-enable-nrh9h-members*`.

* Die Site-ID ist die dritte Komponente von `rep:principalName`

   Wenn z. B.`rep:principalName = community-enable-nrh9h-members`

   * **site name** = *enable*
   * **Site-ID** = *nrh9h*
   * **eindeutige Site-ID** = *enable-nrh9h*

### Benutzergenerierte Inhalte {#user-generated-content}

Besorgen Sie sich das Projekt Communities-srp-tools von Github:

* [https://github.com/Adobe-Marketing-Cloud/communities-srp-tools](https://github.com/Adobe-Marketing-Cloud/communities-srp-tools)

Dies enthält ein Servlet, um alle UGC aus einem SRP zu löschen.

Alle UGC können entfernt werden oder für eine bestimmte Site, z. B.:

* `path=/content/usergenerated/asi/mongo/content/sites/engage`

Dadurch werden nur benutzergenerierte Inhalte (die in der Veröffentlichung eingegeben werden) und nicht verfasste Inhalte (die im Autor eingegeben wurden) entfernt. Daher sind [Schattenknoten](srp.md#shadownodes) nicht betroffen.

### Community-Benutzergruppen {#community-user-groups}

Suchen Sie in allen Autoren- und Veröffentlichungsinstanzen in der [Sicherheitskonsole](../../help/sites-administering/security.md)nach den [Benutzergruppen](users.md) , die folgende Elemente enthalten:

* Präfix mit `community`
* Nach [eindeutiger Site-ID](#community-unique-site-id)

Beispiel: `community-engage-x0e11-members`.

### Aktivierungselemente {#enablement-assets}

In der Hauptkonsole:

* Select **[!UICONTROL Assets]**.
* Starten Sie den **[!UICONTROL Auswahlmodus]** .
* Wählen Sie den Ordner mit der [eindeutigen Site-ID](#community-unique-site-id)aus.
* Wählen Sie &quot; **[!UICONTROL Löschen]** &quot;(unter **[!UICONTROL Mehr...]**).

### Datenbankdatensätze {#database-records}

Es gibt kein Werkzeug zum selektiven Löschen von Datenbankeinträgen für eine bestimmte Community-Site für die Aktivierung.

Wenn alle Community-Sites gelöscht werden, lassen Sie die Enablementdb und scormenginedb mit MySQL Workbench fallen.
