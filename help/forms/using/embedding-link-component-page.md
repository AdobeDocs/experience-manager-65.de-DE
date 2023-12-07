---
title: Einbetten einer Link-Komponente in eine Seite
description: Sie können die Verknüpfungskomponente verwenden, um ein adaptives Dokument oder ein adaptives Formular von einer beliebigen Seite aus zu verknüpfen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
docset: aem65
exl-id: eb45adf2-d0f3-4de6-92ac-fb146953e989
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 36%

---

# Einbetten einer Link-Komponente in eine Seite{#embedding-link-component-in-a-page}

## Voraussetzungen {#prerequisites}

Die Verknüpfungskomponente ist ein Mitglied der Document Services-Kategorie. Stellen Sie sicher, dass die Document Services-Kategorie im AEM-Komponentenbrowser verfügbar ist. Wenn die Kategorie nicht aufgeführt ist, führen Sie die Schritte unter [Aktivieren der Komponenten im Forms Portal](/help/forms/using/enabling-forms-portal-components.md).

## Link {#link-component}

Mit der Komponente &quot;Link&quot;können Formularportalautoren von überall auf einer Seite einen Link zu einem adaptiven Formular erstellen. Die Komponente Link ist im Abschnitt Document Services im Komponenten-Browser verfügbar.

Führen Sie die folgenden Schritte aus, um der Seite eine Komponente Link hinzuzufügen:

1. Ziehen Sie die Komponente **Link** auf die Seite. Wählen Sie die Komponente aus und wählen Sie ![cmppr](assets/cmppr.png). Das Komponentendialogfeld „Link bearbeiten“ wird geöffnet.

   ![edit-link-component](assets/edit-link-component.png)

1. Geben Sie auf der Registerkarte **Anzeige** Folgendes an:

   * **Linkbeschriftung**: Linktext oder Beschriftung für den Link.
   * **Link-Tooltip**: QuickInfo für den Link.
   * **Layout-Vorlage**: Vorlage für das Layout der Komponente Link .

1. Öffnen Sie die **Asset-Informationen** und geben Sie den Typ des Assets an. Ein Asset kann ein **Formular** sein. Je nach ausgewähltem Assettyp können die unten aufgeführten Optionen angezeigt werden:

   * **Asset Path**: Pfad für das Repository, in dem das Asset gespeichert ist.

   * **Render Type**: Das Wiedergabeformat – PDF, HTML oder Auto Der Wiedergabetyp &quot;Auto&quot;erkennt die Benutzerumgebung und rendert das Formular entsprechend als HTML oder als PDF. Wenn das Formular beispielsweise von einem Mobilgerät aus aufgerufen wird, gibt der Wiedergabetyp &quot;Auto&quot;das Formular auf HTML wieder.
   * **Sende-URL**: URL zu dem Servlet, an das die Formulardaten gesendet werden.
   * **HTML-Profil**: Profil für die Wiedergabe des Formulars als HTML.
   * **PDF-Profil**: Profil für die Wiedergabe des Formulars als PDF-Dokument.

1. Öffnen Sie die Registerkarte **Erweitert**. Sie können zusätzliche Parameter in Form von Schlüssel-Wert-Paaren angeben. Wenn auf den Link geklickt wird, werden diese zusätzlichen Parameter zusammen mit dem Formular übergeben.

   Wählen Sie **Fertig** aus, um die Konfiguration zu speichern.

## Best Practices für die Verwendung der Komponente „Link“  {#best-practices-for-using-link-component-br}

* Stellen Sie sicher, dass Sie PDF als Rendertyp auswählen, wenn der im Formularpfad angegebene Pfad auf ein Dokument verweist, dessen Renderformat PDF ist.
* Die Sende-URL für ein Formular kann an mehreren Stellen angegeben werden und die Rangfolge lautet wie folgt:

   1. Die Sende-URL, die in das Formular eingebettet ist (in der Senden-Schaltfläche), hat die höchste Priorität.
   1. Die Sende-URL, die in Forms Manager erwähnt wird, hat die mittlere Priorität.
   1. Die Sende-URL, die im Forms Portal erwähnt wird, hat die niedrigste Priorität.
