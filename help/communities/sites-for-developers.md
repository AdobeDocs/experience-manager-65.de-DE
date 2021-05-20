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
exl-id: 1dc568cd-315c-4944-9a3e-e5d7794e5dc0
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 3%

---

# Community-Site-Grundlagen {#community-site-essentials}

## Benutzerdefinierte Site-Vorlage {#custom-site-template}

Eine benutzerdefinierte Site-Vorlage kann für jede Sprachkopie einer Community-Site separat angegeben werden.

Gehen Sie dazu wie folgt vor:

* Erstellen Sie eine benutzerdefinierte Vorlage.
* Überlagern Sie den Standardpfad der Site-Vorlage.
* Fügen Sie die benutzerdefinierte Vorlage zum Überlagerungspfad hinzu.
* Geben Sie die benutzerdefinierte Vorlage an, indem Sie dem Knoten `configuration` die Eigenschaft `page-template` hinzufügen.

**Standardvorlage**:

`/libs/social/console/components/hbs/sitepage/sitepage.hbs`

**Benutzerdefinierte Vorlage im Überlagerungspfad**:

`/apps/social/console/components/hbs/sitepage/template-name.hbs`

**Eigenschaft**: page-template

**Typ**: String

**Wert**:  `template-name` (keine Erweiterung)

**Konfigurationsknoten**:

`/content/community site path/lang/configuration`

Beispiel: `/content/sites/engage/en/configuration`

>[!NOTE]
>
>Alle Knoten im überlagerten Pfad müssen nur vom Typ `Folder` sein.

>[!CAUTION]
>
>Wenn die benutzerdefinierte Vorlage den Namen *sitepage.hbs* erhält, werden alle Community-Sites angepasst.

### Beispiel für benutzerdefinierte Site-Vorlage {#custom-site-template-example}

`vertical-sitepage.hbs` ist beispielsweise eine Site-Vorlage, die dazu führt, dass Menülinks unten auf der Seite und nicht horizontal unter dem Banner platziert werden.

[Datei ](assets/vertical-sitepage.hbs)
abrufen Platzieren Sie die benutzerdefinierte Site-Vorlage im Überlagerungsordner:

`/apps/social/console/components/hbs/sitepage/vertical-sitepage.hbs`

Identifizieren Sie die benutzerdefinierte Vorlage, indem Sie dem Konfigurationsknoten die Eigenschaft `page-template` hinzufügen:

`/content/sites/sample/en/configuration`

![crxde-siteconfiguration](assets/crxde-siteconfiguration.png)

Stellen Sie sicher, dass Sie **Alle speichern** verwenden und benutzerdefinierten Code für alle AEM-Instanzen replizieren (benutzerspezifischer Code ist nicht enthalten, wenn der Community-Site-Inhalt über die Konsole veröffentlicht wird).

Die empfohlene Vorgehensweise zum Replizieren von benutzerdefiniertem Code ist [Erstellen eines Pakets](../../help/sites-administering/package-manager.md#creating-a-new-package) und Bereitstellen dieses Pakets auf allen Instanzen.

## Exportieren einer Community-Site {#exporting-a-community-site}

Nachdem eine Community-Site erstellt wurde, ist es möglich, die Site als AEM Package zu exportieren, das im Paketmanager gespeichert und zum Herunterladen und Hochladen verfügbar ist.

Dies ist in der [Communities Sites-Konsole](sites-console.md#exporting-the-site) verfügbar.

Beachten Sie, dass benutzerspezifischer Code und benutzerspezifischer Code nicht im Community-Site-Paket enthalten sind.

Verwenden Sie zum Exportieren von benutzergenerierten Inhalten das [AEM Communities UGC Migration Tool](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration), ein Open-Source-Migrationstool, das auf GitHub verfügbar ist.

## Löschen einer Community-Site {#deleting-a-community-site}

Ab AEM Communities 6.3 Service Pack 1 wird das Symbol Website löschen angezeigt, wenn Sie den Mauszeiger über die Community-Site von der Konsole **[!UICONTROL Communities]** > **[!UICONTROL Sites]** bewegen. Wenn während der Entwicklung eine Community-Site gelöscht und neu gestartet werden soll, können Sie diese Funktion verwenden. Beim Löschen einer Community-Site werden die folgenden Elemente entfernt, die mit dieser Site verbunden sind:

* [UGC](#user-generated-content)
* [Benutzergruppen](#community-user-groups)
* [Assets](#enablement-assets)
* [Datenbankdatensätze](#database-records)

### Community Unique Site-ID {#community-unique-site-id}

So identifizieren Sie die eindeutige Site-ID, die mit der Community-Site verknüpft ist, mithilfe von CRXDE:

* Navigieren Sie zum Sprachstamm der Site, z. B. `/content/sites/*<site name>*/en/rep:policy`.

* Suchen Sie den Knoten `allow<#>` mit einem `rep:principalName` in diesem Format `rep:principalName = *community-enable-nrh9h-members*`.

* Die Site-ID ist die dritte Komponente von `rep:principalName`

   Wenn z. B.`rep:principalName = community-enable-nrh9h-members`

   * **site name**  =  *enable*
   * **Site-ID**  =  *nrh9h*
   * **eindeutige Site-ID**  =  *enable-nrh9h*

### Benutzergenerierte Inhalte {#user-generated-content}

Rufen Sie das Projekt communities-srp-tools von Github ab:

* [https://github.com/Adobe-Marketing-Cloud/communities-srp-tools](https://github.com/Adobe-Marketing-Cloud/communities-srp-tools)

Dies enthält ein Servlet zum Löschen aller benutzergenerierten Inhalte aus einem SRP.

Alle benutzergenerierten Inhalte können entfernt werden oder für eine bestimmte Site, z. B.:

* `path=/content/usergenerated/asi/mongo/content/sites/engage`

Dadurch werden nur benutzergenerierte Inhalte (in der Veröffentlichungsinstanz eingegeben) und nicht erstellte Inhalte (in der Autoreninstanz eingegeben) entfernt. Daher sind [Shadow-Knoten](srp.md#shadownodes) nicht betroffen.

### Community-Benutzergruppen {#community-user-groups}

Suchen und entfernen Sie in allen Autoren- und Veröffentlichungsinstanzen in der [Sicherheitskonsole](../../help/sites-administering/security.md) die [Benutzergruppen](users.md), die:

* Mit dem Präfix `community`
* Gefolgt von [eindeutiger Site-ID](#community-unique-site-id)

Beispiel: `community-engage-x0e11-members`.

### Aktivierungselemente {#enablement-assets}

In der Hauptkonsole:

* Wählen Sie **[!UICONTROL Assets]** aus.
* Wechseln Sie in den Modus **[!UICONTROL Wählen Sie]** aus.
* Wählen Sie einen Ordner mit dem Namen [eindeutige Site-ID](#community-unique-site-id) aus.
* Wählen Sie **[!UICONTROL Löschen]** (möglicherweise müssen Sie unter **[!UICONTROL Mehr..]**).

### Datenbankdatensätze {#database-records}

Es gibt kein Tool zum selektiven Löschen von Datenbankeinträgen für eine bestimmte Community-Site für die Aktivierung.

Wenn alle Community-Sites gelöscht werden, legen Sie mithilfe von MySQL Workbench die Enablementdb- und Scormenginedb-Datei ab.
