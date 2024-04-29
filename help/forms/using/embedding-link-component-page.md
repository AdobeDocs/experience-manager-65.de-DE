---
title: Einbetten einer Link-Komponente in eine Seite
description: Mithilfe der Komponente „Link“ können Sie Links zu adaptiven Dokumenten oder Formularen von beliebigen Seiten aus erstellen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
docset: aem65
exl-id: eb45adf2-d0f3-4de6-92ac-fb146953e989
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '408'
ht-degree: 100%

---

# Einbetten einer Link-Komponente in eine Seite{#embedding-link-component-in-a-page}

## Voraussetzungen {#prerequisites}

Die Komponente „Link“ gehört zur Kategorie „Dokumentendienste“. Stellen Sie sicher, dass die Document Services-Kategorie im AEM-Komponentenbrowser verfügbar ist. Wenn die Kategorie nicht aufgelistet ist, führen Sie die Schritte unter [Aktivieren der Komponenten im Formularportal](/help/forms/using/enabling-forms-portal-components.md) aus.

## Komponente „Link“ {#link-component}

Mithilfe der Komponente „Link“ können Formularportal-Autorinnen und -Autoren an einer beliebigen Seitenposition eine Verknüpfung zu einem adaptiven Formular erstellen. Die Komponente „Link“ ist im Abschnitt „Dokumentendienste“ im Komponenten-Browser verfügbar.

Gehen Sie wie folgt vor, um der Seite eine Komponente des Typs „Link“ hinzuzufügen:

1. Ziehen Sie die Komponente **Link** auf die Seite. Wählen Sie die Komponente aus und dann ![cmppr](assets/cmppr.png) aus. Das Komponentendialogfeld „Link bearbeiten“ wird geöffnet.

   ![edit-link-component](assets/edit-link-component.png)

1. Geben Sie auf der Registerkarte **Anzeige** Folgendes an:

   * **Link-Titel**: Link-Text oder Beschriftung des Links.
   * **Link-QuickInfo**: QuickInfo für den Link.
   * **Layout-Vorlage**: Vorlage für das Layout der Komponente vom Typ „Link“.

1. Öffnen Sie die Registerkarte **Element-Info** und geben Sie den Typ des Assets an. Ein Asset kann ein **Formular** sein. Je nach ausgewähltem Assettyp können die unten aufgeführten Optionen angezeigt werden:

   * **Asset Path**: Pfad für das Repository, in dem das Asset gespeichert ist.

   * **Render Type**: Das Wiedergabeformat – PDF, HTML oder Auto Der Render-Typ „Auto“ erkennt die Benutzerumgebung und rendert das Formular entsprechend im HTML- oder PDF-Format. Wenn das Formular beispielsweise auf einem Mobilgerät aufgerufen wird, rendert der Render-Typ „Auto“ das Formular im HTML-Format.
   * **Sende-URL**: URL zu dem Servlet, an das die Formulardaten gesendet werden.
   * **HTML-Profil**: Profil für das Rendern des Formulars als HTML.
   * **PDF-Profil**: Profil für das Rendern des Formulars als PDF-Dokument.

1. Öffnen Sie die Registerkarte **Erweitert**. Sie können zusätzliche Parameter in Form von Schlüssel-Wert-Paaren angeben. Wenn auf den Link geklickt wird, werden diese zusätzlichen Parameter zusammen mit dem Formular übergeben.

   Wählen Sie **Fertig** aus, um die Konfiguration zu speichern.

## Best Practices für die Verwendung der Komponente „Link“  {#best-practices-for-using-link-component-br}

* Stellen Sie sicher, dass Sie „PDF“ als Render-Typ auswählen, wenn der im Formularpfad angegebene Pfad auf ein Dokument verweist, bei dem das zulässige Render-Format PDF ist.
* Die Übermittlungs-URL für ein Formular kann an mehreren Stellen festgelegt werden. Ihre Prioritätsreihenfolge lautet wie folgt:

   1. Die in das Formular eingebettete Übermittlungs-URL (in der Senden-Schaltfläche) hat die höchste Priorität.
   1. Die in Forms Manager erwähnte Übermittlungs-URL hat eine mittlere Priorität.
   1. Die Sende-URL, die im Forms Portal erwähnt wird, hat die niedrigste Priorität.
