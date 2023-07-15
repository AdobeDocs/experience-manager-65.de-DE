---
title: Community-Site-Grundlagen
description: Exportieren und Löschen von Community-Sites und Erstellen benutzerdefinierter Site-Vorlagen
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 1dc568cd-315c-4944-9a3e-e5d7794e5dc0
source-git-commit: e161c37544c3391607cbe495644f3353b9f77fe3
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 2%

---

# Community-Site-Grundlagen {#community-site-essentials}

## Benutzerdefinierte Site-Vorlage {#custom-site-template}

Eine benutzerdefinierte Site-Vorlage kann für jede Sprachkopie einer Community-Site separat angegeben werden.

Gehen Sie dazu wie folgt vor:

* Erstellen Sie eine benutzerdefinierte Vorlage.
* Überlagern Sie den Standardpfad der Site-Vorlage.
* Fügen Sie die benutzerdefinierte Vorlage zum Überlagerungspfad hinzu.
* Geben Sie die benutzerdefinierte Vorlage an, indem Sie eine `page-template` -Eigenschaft auf `configuration` Knoten.

**Standardvorlage**:

`/libs/social/console/components/hbs/sitepage/sitepage.hbs`

**Benutzerdefinierte Vorlage im Überlagerungspfad**:

`/apps/social/console/components/hbs/sitepage/template-name.hbs`

**Eigenschaft**: page-template

**Typ**: Zeichenfolge

**Wert**: `template-name` (keine Erweiterung)

**Konfigurationsknoten**:

`/content/community site path/lang/configuration`

Beispiel: `/content/sites/engage/en/configuration`

>[!NOTE]
>
>Alle Knoten im überlagerten Pfad müssen nur vom Typ `Folder`.

>[!CAUTION]
>
>Wenn die benutzerdefinierte Vorlage den Namen erhält *sitepage.hbs*, werden alle Community-Sites angepasst.

### Beispiel für eine benutzerdefinierte Site-Vorlage {#custom-site-template-example}

Beispiel: `vertical-sitepage.hbs` ist eine Site-Vorlage, die dazu führt, dass Menülinks unten auf der Seite vertikal platziert werden, anstatt horizontal unter dem Banner.

[Datei abrufen](assets/vertical-sitepage.hbs)
Platzieren Sie die benutzerdefinierte Site-Vorlage im Überlagerungsordner:

`/apps/social/console/components/hbs/sitepage/vertical-sitepage.hbs`

Identifizieren Sie die benutzerdefinierte Vorlage, indem Sie eine `page-template` Eigenschaft zum Konfigurationsknoten:

`/content/sites/sample/en/configuration`

![crxde-siteconfiguration](assets/crxde-siteconfiguration.png)

Stellen Sie sicher, dass **Alle speichern** und replizieren benutzerspezifischen Code für alle Adobe Experience Manager (AEM)-Instanzen (benutzerspezifischer Code ist nicht enthalten, wenn der Community-Site-Inhalt über die Konsole veröffentlicht wird).

Es wird empfohlen, benutzerdefinierten Code zu replizieren, indem Sie [Package erstellen](../../help/sites-administering/package-manager.md#creating-a-new-package) und stellen Sie sie auf allen Instanzen bereit.

## Exportieren einer Community-Site {#exporting-a-community-site}

Nachdem eine Community-Site erstellt wurde, ist es möglich, die Site als AEM Package zu exportieren, das im Package Manager gespeichert und zum Herunterladen und Hochladen verfügbar ist.

Dies ist im Abschnitt [Communities Sites-Konsole](sites-console.md#exporting-the-site).

UGC und benutzerspezifischer Code sind nicht im Community-Site-Paket enthalten.

Verwenden Sie zum Exportieren von benutzergenerierten Inhalten die [AEM Communities UGC Migration Tool](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration), ein Open-Source-Migrationstool, das auf GitHub verfügbar ist.

## Löschen einer Community-Site {#deleting-a-community-site}

Ab AEM Communities 6.3 Service Pack 1 wird das Symbol Website löschen angezeigt, wenn Sie den Mauszeiger über die Community-Site von **[!UICONTROL Communities]** > **[!UICONTROL Sites]** Konsole. Wenn während der Entwicklung eine Community-Site gelöscht und neu gestartet werden soll, können Sie diese Funktion verwenden. Beim Löschen einer Community-Site werden die folgenden Elemente entfernt, die mit dieser Site verbunden sind:

* [UGC](#user-generated-content)
* [Benutzergruppen](#community-user-groups)
* [Datenbankdatensätze](#database-records)

### Community Unique Site-ID {#community-unique-site-id}

So identifizieren Sie die eindeutige Site-ID, die mit der Community-Site verknüpft ist, mithilfe von CRXDE:

* Navigieren Sie zum Sprachstamm der Site, z. B. `/content/sites/*<site name>*/en/rep:policy`.

* Suchen Sie die `allow<#>` Knoten mit `rep:principalName` in diesem Format `rep:principalName = *community-enable-nrh9h-members*`.

* Die Site-ID ist die dritte Komponente von `rep:principalName`

  Wenn beispielsweise `rep:principalName = community-enable-nrh9h-members`

   * **Site-Name** = *enable*
   * **Site-ID** = *nrh9h*
   * **eindeutige Site-ID** = *enable-nrh9h*

### Benutzergenerierte Inhalte {#user-generated-content}

Rufen Sie das Projekt communities-srp-tools von GitHub ab:

* [https://github.com/Adobe-Marketing-Cloud/aem-communities-srp-tools](https://github.com/Adobe-Marketing-Cloud/aem-communities-srp-tools)

Dies enthält ein Servlet zum Löschen aller benutzergenerierten Inhalte aus einem SRP.

Alle benutzergenerierten Inhalte können entfernt werden oder für eine bestimmte Site, z. B.:

* `path=/content/usergenerated/asi/mongo/content/sites/engage`

Dadurch werden nur benutzergenerierte Inhalte (in der Veröffentlichungsinstanz eingegeben) und nicht erstellte Inhalte (in der Autoreninstanz eingegeben) entfernt. Daher [Shadow-Knoten](srp.md#shadownodes) nicht betroffen sind.

### Community-Benutzergruppen {#community-user-groups}

In allen Autoren- und Veröffentlichungsinstanzen von der [Sicherheitskonsole](../../help/sites-administering/security.md), suchen und entfernen Sie die [Benutzergruppen](users.md) die sind:

* Präfix mit `community`
* Gefolgt von [eindeutige Site-ID](#community-unique-site-id)

Beispiel: `community-engage-x0e11-members`.
