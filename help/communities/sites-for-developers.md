---
title: Community-Website-Grundlagen
description: Exportieren und Löschen von Community-Sites und Erstellen benutzerdefinierter Site-Vorlagen
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 1dc568cd-315c-4944-9a3e-e5d7794e5dc0
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 2%

---

# Community-Website-Grundlagen {#community-site-essentials}

## Benutzerdefinierte Site-Vorlage {#custom-site-template}

Eine benutzerdefinierte Site-Vorlage kann für jede Sprachkopie einer Community-Site separat angegeben werden.

Gehen Sie dazu wie folgt vor:

* Erstellen Sie eine benutzerdefinierte Vorlage.
* Überlagern Sie den Standardpfad für Site-Vorlagen .
* Fügen Sie die benutzerdefinierte Vorlage zum Überlagerungspfad hinzu.
* Geben Sie die benutzerdefinierte Vorlage an, indem Sie dem `configuration` eine `page-template` Eigenschaft hinzufügen.

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
>Alle Knoten im überlagerten Pfad müssen nur vom Typ `Folder` sein.

>[!CAUTION]
>
>Wenn die benutzerdefinierte Vorlage den Namen &quot;*.hbs“*, werden alle Community-Sites angepasst.

### Beispiel für eine benutzerdefinierte Site-Vorlage {#custom-site-template-example}

`vertical-sitepage.hbs` ist beispielsweise eine Site-Vorlage, die dazu führt, dass Menülinks vertikal nach links statt horizontal unter dem Banner platziert werden.

[Datei abrufen](assets/vertical-sitepage.hbs)
Platzieren Sie die benutzerdefinierte Site-Vorlage im Überlagerungsordner:

`/apps/social/console/components/hbs/sitepage/vertical-sitepage.hbs`

Identifizieren Sie die benutzerdefinierte Vorlage, indem Sie dem Konfigurationsknoten eine `page-template` Eigenschaft hinzufügen:

`/content/sites/sample/en/configuration`

![crxde-siteConfiguration](assets/crxde-siteconfiguration.png)

Denken Sie daran **„Alle speichern** und benutzerdefinierten Code auf allen Adobe Experience Manager (AEM)-Instanzen zu replizieren (benutzerdefinierter Code ist nicht enthalten, wenn die Inhalte der Community-Site über die Konsole veröffentlicht werden).

Die empfohlene Vorgehensweise für das Replizieren von benutzerdefiniertem Code besteht darin[&#x200B; ein Paket zu erstellen &#x200B;](../../help/sites-administering/package-manager.md#creating-a-new-package) es auf allen Instanzen bereitzustellen.

## Community-Site exportieren {#exporting-a-community-site}

Sobald eine Community-Site erstellt wurde, ist es möglich, die Site als AEM-Paket zu exportieren, das im Package Manager gespeichert ist und zum Herunterladen und Hochladen verfügbar ist.

Dies ist über die [Communities-Sites-Konsole](sites-console.md#exporting-the-site) verfügbar.

UGC und benutzerdefinierter Code sind nicht im Paket der Community-Site enthalten.

Verwenden Sie zum Exportieren von benutzergenerierten Inhalten das [AEM Communities UGC Migration Tool](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration), ein Open-Source-Migrations-Tool, das auf GitHub verfügbar ist.

## Löschen einer Community-Site {#deleting-a-community-site}

Ab AEM Communities 6.3 Service Pack 1 wird das Symbol „Site löschen“ angezeigt, wenn Sie den Mauszeiger über die Community-Site von **[!UICONTROL Communities]** > **[!UICONTROL Sites]**-Konsole bewegen. Wenn Sie während der Entwicklung eine Community-Site löschen und neu beginnen möchten, können Sie diese Funktion verwenden. Durch Löschen einer Community-Site werden die folgenden mit dieser Site verknüpften Elemente entfernt:

* [UGC](#user-generated-content)
* [Benutzergruppen](#community-user-groups)
* [Datenbankeinträge](#database-records)

### Eindeutige Community-Site-ID {#community-unique-site-id}

So identifizieren Sie mit CRXDE die eindeutige Site-ID, die mit der Community-Site verknüpft ist:

* Navigieren Sie zum Sprachstamm der Site, z. B. `/content/sites/*<site name>*/en/rep:policy`.

* Suchen Sie den `allow<#>` Knoten mit einem `rep:principalName` in diesem `rep:principalName = *community-enable-nrh9h-members*`.

* Die Site-ID ist die dritte Komponente von `rep:principalName`

  Beispiel: Wenn `rep:principalName = community-enable-nrh9h-members`

   * **Site name** = *enable*
   * **site ID** = *nrh9h*
   * **eindeutige Site-ID** = *enable-nrh9h*

### Benutzergenerierte Inhalte {#user-generated-content}

Beziehen Sie das Projekt „community-srp-tools“ von GitHub:

* [https://github.com/Adobe-Marketing-Cloud/aem-communities-srp-tools](https://github.com/Adobe-Marketing-Cloud/aem-communities-srp-tools)

Dieses enthält ein Servlet zum Löschen aller benutzergenerierten Inhalte aus einem beliebigen SRP.

Alle benutzergenerierten Inhalte können entfernt werden oder für eine bestimmte Site gelten, z. B.:

* `path=/content/usergenerated/asi/mongo/content/sites/engage`

Dadurch werden nur benutzergenerierte Inhalte (die in der Veröffentlichungsinstanz eingegeben wurden) entfernt und keine erstellten Inhalte (die in der Autoreninstanz eingegeben wurden). Daher sind [Shadow-Knoten](srp.md#shadownodes) nicht betroffen.

### Community-Benutzergruppen {#community-user-groups}

Suchen und entfernen Sie auf allen Autoren- und Veröffentlichungsinstanzen über [Sicherheitskonsole](../../help/sites-administering/security.md) die folgenden [Benutzergruppen](users.md):

* Präfix mit `community`
* gefolgt von [Unique Site ID](#community-unique-site-id)

Zum Beispiel: `community-engage-x0e11-members`.
