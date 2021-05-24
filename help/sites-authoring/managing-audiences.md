---
title: Verwalten von Zielgruppen
seo-title: Verwalten von Zielgruppen
description: Die Konsole „Zielgruppen“ ermöglicht das Erstellen, Organisieren und Verwalten von Zielgruppen für Ihr Adobe Target-Konto und das Verwalten von Segmenten für ContextHub oder ClientContext
seo-description: Die Zielgruppen-Konsole ermöglicht das Erstellen, Organisieren und Verwalten von Zielgruppen für Ihr Adobe Target-Konto und das Verwalten von Segmenten für ContextHub oder ClientContext
uuid: 76408a8c-25db-4e9f-8a69-27e820a2a7cf
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
discoiquuid: 9a7a31f9-aeb8-455f-a07e-7b1d1f0a88b6
docset: aem65
exl-id: 97e02986-049f-4747-a67a-6aa0677b281e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1016'
ht-degree: 93%

---

# Verwalten von Zielgruppen{#managing-audiences}

Mithilfe der Zielgruppenkonsole können Sie Zielgruppen für Ihr Adobe Target-Konto erstellen, organisieren und verwalten oder Segmente für ContextHub oder Client Context verwalten:

* Fügen Sie Zielgruppen hinzu – entweder Adobe Target-Zielgruppen oder ContextHub-Segmente.
* Verwalten Sie Zielgruppen.

Eine Zielgruppe, die in ContextHub und ClientContext als *Segment* bezeichnet wird, ist eine Besuchergruppe, die durch bestimmte Kriterien definiert wird und mit der bestimmt wird, wer welche zielgerichteten Aktivitäten sieht. Beim Targeting von Aktivitäten können Zielgruppen entweder direkt während des Targeting-Verfahrens ausgewählt oder neue Zielgruppen in der Konsole „Zielgruppen“ erstellt werden.

In der Konsole „Zielgruppen“ werden Zielgruppen nach Marken geordnet.

Zielgruppen stehen im Targeting-Modus für [das Verfassen zielgerichteter Inhalte](/help/sites-authoring/content-targeting-touch.md) zur Verfügung. In diesem Modus können außerdem auch Zielgruppen erstellt werden (Zielgruppen für Adobe Target müssen hingegen in der Konsole „Zielgruppen“ erstellt werden). Im Targeting-Modus erstellte Zielgruppen werden in der Konsole „Zielgruppen“ aufgeführt.

Zielgruppen werden mit einer Beschriftung versehen, die beschreibt, um welche Zielgruppenart es sich handelt:

* CH – ContextHub-Segment
* CC – Client Context-Segment
* AT – Adobe Target-Zielgruppe

## Erstellen von ContextHub-Segmenten mit der Konsole „Zielgruppen“   {#creating-a-contexthub-segment-in-the-audiences-console}

Sie können ContextHub-Segmente entweder in der Konsole „Zielgruppen“ oder während des Targeting-Verfahrens erstellen.

So erstellen Sie ContextHub-Segmente in der Konsole „Zielgruppen“:

1. Klicken oder tippen Sie in der Navigationskonsole auf **Personalisierung**. Klicken oder tippen Sie auf **Zielgruppen**.
1. Klicken oder tippen Sie auf **ContextHub-Segment erstellen**.

   ![screen-shot_2019-03-05at124034](assets/screen-shot_2019-03-05at124034.png)

1. Geben Sie im Dialogfeld **Neues ContextHub-Segment** einen Titel ein, passen Sie die Verstärkung an und klicken Sie auf **Erstellen**. Das neue ContextHub-Segment erscheint in der Zielgruppenliste.

   >[!NOTE]
   >
   >Sie können die geänderte Liste sortieren, indem Sie auf **Bearbeitet** klicken oder tippen, um Elemente in absteigender Reihenfolge anzuordnen, sodass zuletzt erstellte Zielgruppen ganz oben aufgeführt sind.

Weitere Informationen zum Erstellen von Segmenten mit ContextHub finden Sie in der Dokumentation [Konfiguration der Segmentierung mit ContextHub](/help/sites-administering/segmentation.md).

## Erstellen von Adobe Target-Zielgruppen mit der Konsole „Zielgruppen“ {#creating-an-adobe-target-audience-using-the-audience-console}

Sie können Adobe Target-Zielgruppen mithilfe der Zielgruppenkonsole direkt in AEM erstellen.

Zielgruppen werden durch Regeln definiert, die bestimmen, wer in eine Zielgruppenaktivität eingeschlossen wird. Eine Zielgruppendefinition kann mehrere Regeln enthalten, wobei die einzelnen Regeln wiederum mehrere Parameter aufweisen können.

Arbeiten Sie mit mehr als einer Regel, werden diese Regeln durch den booleschen Operator UND verknüpft. Das bedeutet, dass jedes potenzielle Mitglied der Zielgruppe alle festgelegten Bedingungen erfüllen muss, um in die Aktivität aufgenommen werden zu können. Wenn Sie zum Beispiel eine Betriebssystemregel und eine Browserregel definieren, werden nur die Besucher, die sowohl das definierte Betriebssystem als auch den definierten Browser verwenden, in die Aktivität aufgenommen.

>[!NOTE]
>
>Wenn die Option &quot;Target-Zielgruppe erstellen&quot;im Menü **Erstellen** nicht angezeigt wird, verfügen Sie nicht über die erforderlichen Berechtigungen zum Erstellen einer Zielgruppe. Sie benötigen Schreibberechtigungen unter **/etc/segmentation** , um Zielgruppen erstellen zu können. Inhaltsautoren der Gruppe verfügen standardmäßig über Schreibrechte.

So erstellen Sie eine Adobe Target-Zielgruppe:

1. Klicken oder tippen Sie in der Navigationskonsole auf **Personalisierung**. Klicken oder tippen Sie auf **Zielgruppen**.

   ![screen-shot_2019-03-05at124139](assets/screen-shot_2019-03-05at124139.png)

1. Klicken oder tippen Sie in der Konsole „Zielgruppen“ auf **Erstellen** und anschließend auf „Target-Zielgruppe erstellen“.

   ![chlimage_1-168](assets/chlimage_1-168.png)

1. Wählen Sie im Dialogfeld **Adobe Target-Konfiguration** die Zielkonfiguration aus und klicken oder tippen Sie auf **OK**.
1. Klicken oder tippen Sie im Bereich „Regel#1“ auf den Attributtyp und geben Sie Attributinformationen in die verfügbaren Felder ein. Nach getätigter Eingabe müssen Sie das Häkchen rechts des Attributs auswählen, um die Eingaben zu speichern. Weitere Informationen zu allen Attributen finden Sie unter [Attribute und zugehörige Optionen](#attributes-and-their-options).
1. Klicken Sie auf **Regel hinzufügen**, um eine weitere Regel hinzuzufügen. Geben Sie so viele Regeln wie erforderlich ein. Regeln werden mit dem booleschen Operator UND kombiniert. Das bedeutet, dass die Zielgruppe alle Anforderungen jeder Regel erfüllen muss, um für eine Aktivität zugelassen zu werden.
1. Tippen oder klicken Sie auf **Weiter**.
1. Geben Sie einen Namen für die Zielgruppe ein und tippen oder klicken Sie auf **Speichern**.
1. Tippen oder klicken Sie auf **Speichern**. Ihre Zielgruppe wird nun in der Zielgruppenliste angezeigt.

### Attribute und zugehörige Optionen   {#attributes-and-their-options}

Sie können Targeting-Regeln für jedes der folgenden Attribute erstellen:

| **Attribut** | **Beschreibung** | **Für weitere Informationen** |
|---|---|---|
| **Mobilgerät** | Target-Mobilgeräte auf Basis von Parametern wie Mobilgerät, Gerätetyp, Geräteanbieter, Bildschirmmaße (in Pixeln) usw. | Weitere Informationen finden Sie in der [Dokumentation](https://docs.adobe.com/content/help/de-DE/target/using/audiences/create-audiences/categories-audiences/mobile.html) von Adobe Target. |
| **Benutzerdefiniert** | Benutzerdefinierte Parameter sind Mbox-Parameter. Wenn Sie Mbox-Parameter an Mboxes übergeben oder die Funktion „targetPageParams“ verwenden, werden diese Parameter hier angezeigt und können in Zielgruppen verwendet werden. | Weitere Informationen finden Sie in der [Dokumentation zu benutzerdefinierten Parametern](https://docs.adobe.com/content/help/de-DE/target/using/audiences/create-audiences/categories-audiences/custom-parameters.html) für Adobe Target. |
| **BS** | Sie können Benutzer, die ein bestimmtes Betriebssystem verwenden, als Ziel auswählen. | Richten Sie ihre Inhalte auf Benutzer aus, die Linux, Macintosh oder Windows verwenden. |
| **Seiten der Site** | Targeting von Besuchern, die sich auf einer bestimmten Seite befinden oder die einen bestimmten Mbox-Parameter aufweisen. | Weitere Informationen finden Sie in der [Dokumentation für Website-Seiten](https://docs.adobe.com/content/help/de-DE/target/using/audiences/create-audiences/categories-audiences/site-pages.html) für Adobe Target. |
| **Browser** | Sie können Benutzer, die einen speziellen Browser oder spezielle Browseroptionen beim Besuch Ihrer Seite verwenden, als Ziel auswählen. | Weitere Informationen finden Sie in der [Dokumentation für Browser-Optionen](https://docs.adobe.com/help/de-DE/target/using/audiences/create-audiences/categories-audiences/browser.html) für Adobe Target. |
| **Besucherprofil** | Target-Besucher, die bestimmte Profilparameter erfüllen. | Weitere Informationen finden Sie in der [Dokumentation für Besucherprofile](https://docs.adobe.com/content/help/de-DE/target/using/audiences/visitor-profiles/visitor-profile.html) für Adobe Target. |
| **Traffic-Quellen** | Targeting von Besuchern auf Grundlage der Suchmaschine oder Landingpage, von der sie auf Ihre Site geleitet werden | Weitere Informationen finden Sie in der [Dokumentation für Traffic-Quellen](https://docs.adobe.com/content/help/de-DE/target/using/audiences/create-audiences/categories-audiences/traffic-sources.html) für Adobe Target. |

## Bearbeiten von Zielgruppen mithilfe der Konsole „Zielgruppen“ {#modifying-an-audience-in-the-audiences-console}

>[!NOTE]
>
>Sie können nur Adobe Target-Zielgruppen ändern, die in der AEM-Instanz erstellt wurden, in der Sie gerade arbeiten. Target-Zielgruppen, die in anderen AEM-Umgebungen erstellt wurden, lassen sich nicht bearbeiten.

ContextHub- oder Client Context-Zielgruppen lassen sich beliebig mit der Zielgruppenkonsole bearbeiten. Sie können zudem Adobe Target-Zielgruppen bearbeiten, jedoch nur diejenigen, die in AEM erstellt wurden:

1. Klicken oder tippen Sie in der Navigationskonsole auf **Personalisierung**. Klicken oder tippen Sie auf **Zielgruppen**.
1. Klicken oder tippen Sie auf das Symbol neben dem zu bearbeitenden ContextHub- oder Client Context-Segment und tippen oder klicken Sie auf **Bearbeiten**.
1. Bearbeiten Sie die gewünschten Einstellungen im Editor. Weitere Informationen finden Sie in der Dokumentation für [Client Context](/help/sites-administering/campaign-segmentation.md) oder [ContextHub](/help/sites-developing/ch-configuring.md).
