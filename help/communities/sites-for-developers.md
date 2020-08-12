---
title: Community Site Essentials
seo-title: Community Site Essentials
description: Exporting and deleting community sites and creating custom site templates
seo-description: Exporting and deleting community sites and creating custom site templates
uuid: f0ec0e71-64e9-415a-b14a-939a9b1611c1
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: dc7a085e-d6de-4bc8-bd7e-6b43f8d172d2
translation-type: tm+mt
source-git-commit: e49acbc042d84ae970058b4e99ab6f980866db5a
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 3%

---


# Community Site Essentials {#community-site-essentials}

## Custom Site Template {#custom-site-template}

A custom site template may be specified separately for each language copy of a community site.

Gehen Sie dazu wie folgt vor:

* Create a custom template.
* Overlay the default site template path.
* Add the custom template to the overlay path.
* Specify the custom template by adding a `page-template` property to the `configuration` node.

**Default template**:

`/libs/social/console/components/hbs/sitepage/sitepage.hbs`

**Custom template in overlay path**:

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
>If the custom template is given the name *sitepage.hbs*, then all community sites will be customized.


### Beispiel für eine benutzerdefinierte Site {#custom-site-template-example}

As an example, `vertical-sitepage.hbs` is a site template that results in the placement of menu links vertically down the left side of the page, instead of horizontally below the banner.

[Get File](assets/vertical-sitepage.hbs)
Place the custom site template in the overlay folder:

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
   * **site ID** = *nrh9h*
   * **unique site ID** = *enable-nrh9h*

### Benutzergenerierte Inhalte {#user-generated-content}

Obtain the communities-srp-tools project from Github:

* [https://github.com/Adobe-Marketing-Cloud/communities-srp-tools](https://github.com/Adobe-Marketing-Cloud/communities-srp-tools)

This contains a servlet to delete all UGC from any SRP.

All UGC may be removed or for a specific site, for example:

* `path=/content/usergenerated/asi/mongo/content/sites/engage`

This only removes user generated content (entered on publish) and not authored content (entered on author). Therefore, [shadow nodes](srp.md#shadownodes) are not affected.

### Community User Groups {#community-user-groups}

On all author and publish instances, from the [security console](../../help/sites-administering/security.md), locate and remove the [user groups](users.md) that are:

* Prefixed with `community`
* Followed by [unique site id](#community-unique-site-id)

Beispiel: `community-engage-x0e11-members`.

### Enablement Assets {#enablement-assets}

In der Hauptkonsole:

* Select **[!UICONTROL Assets]**.
* Enter **[!UICONTROL Select]** mode.
* Wählen Sie den Ordner mit der [eindeutigen Site-ID](#community-unique-site-id)aus.
* Wählen Sie &quot; **[!UICONTROL Löschen]** &quot;(unter **[!UICONTROL Mehr...]**).

### Datenbankdatensätze {#database-records}

There is no tool for selectively deleting database entries for one specific enablement community site.

Wenn alle Community-Sites gelöscht werden, lassen Sie die Enablementdb und scormenginedb mit MySQL Workbench fallen.
