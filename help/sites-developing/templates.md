---
title: Vorlagen
seo-title: Vorlagen
description: Vorlagen werden beim Erstellen einer Seite verwendet, die als Basis für die neue Seite verwendet wird
seo-description: Vorlagen werden beim Erstellen einer Seite verwendet, die als Grundlage für die neue Seite verwendet wird
uuid: 6fa3dafc-dfa1-42d8-b296-d4be57449411
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 7c723773-7c23-43d7-85dc-53e54556b648
legacypath: /content/docs/en/aem/6-1/develop/the-basics/templates
translation-type: tm+mt
source-git-commit: 2fc35bfd93585a586cb1d4e3299261611db49ba6

---


# Vorlagen{#templates}

Vorlagen werden an verschiedenen Stellen in AEM verwendet:

* Wenn Sie eine [Seite erstellen, müssen Sie eine Vorlage auswählen](#templates-pages). Diese wird als Basis für die neue Seite verwendet. Die Vorlage definiert die Struktur der resultierenden Seite, jeden anfänglichen Inhalt und die [Komponenten](/help/sites-authoring/default-components.md), die verwendet werden können (Design-Eigenschaften).

* Wenn Sie ein [Inhaltsfragment erstellen, müssen Sie auch eine Vorlage auswählen](#templates-content-fragments). Diese Vorlage definiert die Struktur, die Ausgangselemente und Varianten.

Die folgenden Vorlagen werden im Detail beschrieben:

* [Bearbeitbare Seitenvorlagen](/help/sites-developing/page-templates-editable.md)
* [Seitenvorlagen - statisch](/help/sites-developing/page-templates-static.md)
* [Inhaltsfragmentvorlagen](/help/sites-developing/content-fragment-templates.md)
* [Rendering von adaptiven Vorlagen](/help/sites-developing/templates-adaptive-rendering.md)

## Vorlagen - Seiten {#templates-pages}

AEM bietet jetzt zwei grundlegende Arten von Vorlagen zum Erstellen von Seiten an:

>[!NOTE]
>
>Wenn Sie eine Vorlage zum [Erstellen einer neuen Seite](/help/sites-authoring/managing-pages.md#creating-a-new-page) verwenden, gibt es keinen sichtbaren Unterschied (zum Autor der Seite) und keine Angabe zum Typ der verwendeten Vorlage.

### Bearbeitbare Vorlagen {#editable-templates}

Bearbeitbare Vorlagen gelten nun als Best Practices für die Entwicklung mit AEM.

Die Vorteile von bearbeitbaren Vorlagen:

* Können von den Autoren [erstellt](/help/sites-authoring/templates.md#creating-a-new-template-template-author) und [bearbeitet](/help/sites-authoring/templates.md#editing-a-template-structure-template-author) werden.

* Wurden eingeführt, damit Sie für alle mit der Vorlage erstellten Seiten Folgendes definieren können:

   * die Struktur
   * den ursprünglichen Inhalt
   * Inhaltsrichtlinien

* Nachdem die neue Seite erstellt wurde, wird eine dynamische Verbindung zwischen der Seite und der Vorlage aufrechterhalten. Das bedeutet, dass Änderungen an der Vorlagenstruktur auf allen mit dieser Vorlage erstellten Seiten wiedergegeben werden (Änderungen am ursprünglichen Inhalt werden nicht berücksichtigt).
* Verwendet Inhaltsrichtlinien (die im Vorlageneditor bearbeitet wurden), um die Designeigenschaften beizubehalten (verwendet den Designmodus im Seiteneditor nicht).
* Are stored under `/conf`
* Siehe [Bearbeitbare Vorlagen](/help/sites-developing/page-templates-editable.md) für weitere Informationen.

>[!NOTE]
>
>An AEM Community Article is available explaining how to develop an Experience Manager site with Editable Templates, see [Creating an Adobe Experience Manager 6.5 website using Editable Templates](https://helpx.adobe.com/experience-manager/using/first_aem64_website.html).

### Statische Vorlagen {#static-templates}

Statische Vorlagen:

* Müssen durch Ihre Entwickler definiert und konfiguriert werden.
* Dies war das ursprüngliche Vorlagensystem von AEM und ist seit vielen Versionen verfügbar.
* Eine statische Vorlage ist eine Hierarchie von Knoten, die dieselbe Struktur wie die zu erstellende Seite, jedoch keinen tatsächlichen Inhalt aufweist.
* Werden kopiert, um die neue Seite zu erstellen, danach besteht keine dynamische Verbindung mehr.
* Verwenden den [Designmodus](/help/sites-authoring/default-components-designmode.md), um Designeigenschaften beizubehalten.
* Are stored under `/apps`
* Siehe [Statische Vorlagen](/help/sites-developing/page-templates-static.md) für weitere Informationen.

>[!NOTE]
>
>Ab AEM 6.5 gilt die Verwendung von statischen Vorlagen nicht als bewährte Verfahren. Verwenden Sie stattdessen bearbeitbare Vorlagen.
>
>[Mit den AEM-Moderationstools](modernization-tools.md) können Sie von statischen zu bearbeitbaren Vorlagen migrieren.

### Verfügbarkeit der Vorlage {#template-availability}

>[!CAUTION]
>
>AEM bietet mehrere Eigenschaften, um die unter **Sites** zulässigen Vorlagen zu steuern. Eine Kombination dieser Regeln kann jedoch zu sehr komplexen Regeln führen, die sich nur schwer verfolgen und verwalten lassen.
>
>Daher empfiehlt Adobe, dass Sie mit einem einfachen Einstieg beginnen, indem Sie Folgendes definieren:
>
>* Nur die `cq:allowedTemplates` Eigenschaft
   >
   >
* nur im Site-Stammordner
>
>
For an example, see We.Retail: `/content/we-retail/jcr:content`
>
>Die Eigenschaften `allowedPaths`, `allowedParents`und `allowedChildren` können auch in die Vorlagen eingefügt werden, um komplexere Regeln zu definieren. Es ist jedoch nach Möglichkeit *viel* einfacher, weitere `cq:allowedTemplates` Eigenschaften in Unterabschnitten der Site zu definieren, wenn die zulässigen Vorlagen weiter eingeschränkt werden müssen.
>
>Ein weiterer Vorteil besteht darin, dass die `cq:allowedTemplates` Eigenschaften von einem Autor auf der Registerkarte &quot; **Erweitert** &quot;der **Seiteneigenschaften** aktualisiert werden können. Die anderen Vorlageneigenschaften können nicht über die (Standard-) Benutzeroberfläche aktualisiert werden. Daher benötigen Sie einen Entwickler, der die Regeln und eine Codebereitstellung für jede Änderung pflegt.

Beim Erstellen einer neuen Seite in der Website-Admin-Oberfläche hängt die Liste der verfügbaren Vorlagen vom Speicherort der neuen Seite und den in den einzelnen Vorlagen angegebenen Platzierungsbeschränkungen ab.

Die folgenden Eigenschaften bestimmen, ob eine Vorlage `T` für eine neue Seite verwendet werden darf, die der Seite `P` untergeordnet platziert werden kann. Jede dieser Eigenschaften ist eine mehrwertige Zeichenfolge, welche null oder mehrere regulärere Ausdrücke enthält, die für die Übereinstimmung mit Pfaden verwendet werden:

* The `cq:allowedTemplates` property of the `jcr:content` subnode of `P` or an ancestor of `P`.

* Die `allowedPaths` Eigenschaft von `T`.

* Die `allowedParents` Eigenschaft von `T`.

* The `allowedChildren` property of the template of `P`.

Die Bewertung funktioniert wie folgt:

* The first non-empty `cq:allowedTemplates` property found while ascending the page hierarchy starting with `P` is matched against the path of `T`. Wenn keiner der Werte übereinstimmt, wird `T` abgelehnt.

* If `T` has a non-empty `allowedPaths` property, but none of the values match the path of `P`, `T` is rejected.

* If both of the above properties are either empty or non-existent, `T` is rejected unless it belongs to the same application as `P`. `T` gehört genau dann zurselben Anwendung wie `P`, wenn der Name der zweiten Ebene des Pfades von `T` mit dem Namen der zweiten Ebene des Pfades von `P` übereinstimmt. For example, the template `/apps/geometrixx/templates/foo` belongs to the same application as the page `/content/geometrixx`.

* If `T` has an non-empty `allowedParents` property, but none of the values match the path of `P`, `T` is rejected.

* If the template of `P` has a non-empty `allowedChildren` property, but none of the values match the path of `T`, `T` is rejected.

* In allen anderen Fällen ist `T` zulässig.

Das folgende Diagramm zeigt den Vorlagenauswertungsprozess:

![chlimage_1-176](assets/chlimage_1-176.png)

#### Einschränkende Vorlagen in untergeordneten Seiten {#limiting-templates-used-in-child-pages}

To limit what templates can be used to create child pages under a given page, use the `cq:allowedTemplates` property of `jcr:content` node of the page to specify the list of templates to be allowed as child pages. Each value in the list must be an absolute path to a template for an allowed child page, for example `/apps/geometrixx/templates/contentpage`.

You can use the `cq:allowedTemplates` property on the template&#39;s  `jcr:content` node to have this configuration applied to all newly created pages that use this template.

Wenn Sie mehrere Einschränkungen hinzufügen möchten, z. B. bezüglich der Vorlagenhierarchie, können Sie die Eigenschaften `allowedParents/allowedChildren` auf der Vorlage verwenden. Sie können dann explizit angeben, dass Seiten, die aus einer Vorlage T erstellt wurden, übergeordnet/untergeordnet von Seiten sein müssen, die aus einer Vorlage T erstellt wurden.

## Vorlagen - Inhaltsfragmente {#templates-content-fragments}

Ausführliche Informationen finden Sie unter [Inhaltsfragmentvorlagen](/help/sites-developing/content-fragment-templates.md).
