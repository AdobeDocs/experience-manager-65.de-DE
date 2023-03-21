---
title: Verwalten von Zielgruppen
seo-title: Managing Audiences
description: Die Konsole „Zielgruppen“ ermöglicht das Erstellen, Organisieren und Verwalten von Zielgruppen für Ihr Adobe Target-Konto und das Verwalten von Segmenten für ContextHub   oder ClientContext.
seo-description: The Audiences console enables you to create, organize, and manage audiences for your Adobe Target account or manage segments for ContextHub or Client Context
uuid: 76408a8c-25db-4e9f-8a69-27e820a2a7cf
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
discoiquuid: 9a7a31f9-aeb8-455f-a07e-7b1d1f0a88b6
docset: aem65
exl-id: 97e02986-049f-4747-a67a-6aa0677b281e
source-git-commit: 4fa868f3ae4778d3a637e90b91f7c5909fe5f8aa
workflow-type: tm+mt
source-wordcount: '979'
ht-degree: 54%

---

# Verwalten von Zielgruppen{#managing-audiences}

Die Konsole „Zielgruppen“ ermöglicht das Erstellen, Organisieren und Verwalten von Zielgruppen für Ihr Adobe Target-Konto und das Verwalten von Segmenten für ContextHub   oder ClientContext:

* Zielgruppen hinzufügen - entweder Adobe Target-Zielgruppen oder ContextHub-Segmente.
* Zielgruppen verwalten.

„Zielgruppen“ werden in ContextHub und ClientContext als *Segment* bezeichnet und sind Besuchergruppen, die durch bestimmte Kriterien definiert werden und mit denen bestimmt wird, wer welche zielgerichteten Inhalte zu sehen bekommt. Wenn Sie eine Aktivität als Ziel auswählen, können Sie entweder Zielgruppen direkt im Targeting-Prozess auswählen oder weitere in der Konsole Zielgruppen erstellen.

In der Konsole &quot;Zielgruppen&quot;werden die Zielgruppen nach Marken geordnet.

Zielgruppen sind im Targeting-Modus für [Verfassen zielgerichteter Inhalte](/help/sites-authoring/content-targeting-touch.md), wo Sie auch Zielgruppen erstellen können (aber Adobe Target-Zielgruppen in der Konsole &quot;Zielgruppen&quot;erstellen müssen). Zielgruppen, die Sie im Targeting-Modus erstellen, werden in der Konsole Zielgruppen angezeigt.

Zielgruppen werden mit einem Titel angezeigt, der beschreibt, welche Art von Zielgruppe definiert ist:

* CH - ContextHub-Segment
* CC - ClientContext-Segment
* AT – Adobe Target-Zielgruppe

## Erstellen von ContextHub-Segmenten mit der Konsole „Zielgruppen“ {#creating-a-contexthub-segment-in-the-audiences-console}

Sie können ContextHub-Segmente entweder in der Konsole „Zielgruppen“ oder während des Targeting-Verfahrens erstellen.

So erstellen Sie ContextHub-Segmente in der Konsole „Zielgruppen“:

1. Klicken oder tippen Sie in der Navigationskonsole auf **Personalisierung**. Klicken oder tippen Sie auf **Zielgruppen**.
1. Klicken oder tippen Sie auf **ContextHub-Segment erstellen**.

   ![screen-shot_2019-03-05at124034](assets/screen-shot_2019-03-05at124034.png)

1. Geben Sie im Dialogfeld **Neues ContextHub-Segment** einen Titel ein, passen Sie die Verstärkung an und klicken Sie auf **Erstellen**. Das neue ContextHub-Segment erscheint in der Zielgruppenliste.

   >[!NOTE]
   >
   >Sie können die geänderte Liste sortieren, indem Sie auf **Bearbeitet** klicken oder tippen, um Elemente in absteigender Reihenfolge anzuordnen, sodass zuletzt erstellte Zielgruppen ganz oben aufgeführt sind.

Weitere Informationen zum Erstellen von Segmenten mit ContextHub finden Sie in der [Konfigurieren der Segmentierung mit ContextHub](/help/sites-administering/segmentation.md) Dokumentation.

## Erstellen von Adobe Target-Zielgruppen mit der Konsole „Zielgruppen“ {#creating-an-adobe-target-audience-using-the-audience-console}

Sie können Adobe Target-Zielgruppen direkt in AEM mithilfe der Konsole Zielgruppen erstellen.

Zielgruppen werden durch Regeln definiert, die bestimmen, wer in einer Zielaktivität enthalten ist. Eine Zielgruppendefinition kann mehrere Regeln enthalten und jede Regel kann mehrere Parameter enthalten.

Wenn Sie mehr als eine Regel verwenden, werden diese Regeln durch den Booleschen Operator UND kombiniert. Das bedeutet, dass jedes potenzielle Mitglied der Zielgruppe alle definierten Bedingungen erfüllen muss, um in die Aktivität aufgenommen zu werden. Wenn Sie beispielsweise eine Betriebssystemregel und eine Browserregel definieren, werden nur Besucher, die sowohl das definierte Betriebssystem als auch den definierten Browser verwenden, in die Aktivität aufgenommen.

>[!NOTE]
>
>Wird die Option **Target-Zielgruppe erstellen** im Menü **Erstellen** nicht angezeigt, verfügen Sie nicht über die nötigen Berechtigungen zum Erstellung von Zielgruppen. Sie müssen unter **/etc/segmentation** über Schreibrechte verfügen, um Zielgruppen erstellen zu können. Inhaltsautoren der Gruppe verfügen standardmäßig über Schreibrechte.

So erstellen Sie eine Adobe Target-Zielgruppe:

1. Klicken oder tippen Sie in der Navigationskonsole auf **Personalisierung**. Klicken oder tippen Sie auf **Zielgruppen**.

   ![screen-shot_2019-03-05at124139](assets/screen-shot_2019-03-05at124139.png)

1. Klicken oder tippen Sie in der Konsole „Zielgruppen“ auf **Erstellen** und anschließend auf **Target-Zielgruppe erstellen**.

   ![chlimage_1-168](assets/chlimage_1-168.png)

1. Wählen Sie im Dialogfeld **Adobe Target-Konfiguration** die Zielkonfiguration aus und klicken oder tippen Sie auf **OK**.
1. Tippen oder klicken Sie im Bereich Regel Nr. 1 auf den Attributtyp und geben Sie in die verfügbaren Felder Attributinformationen ein. Wenn Sie fertig sind, wählen Sie das Häkchen rechts neben dem Attribut aus, um es zu speichern. Siehe [Attribute und zugehörige Optionen](#attributes-and-their-options) für Informationen zu allen Attributen.
1. Klicken Sie auf **Regel hinzufügen**, um eine weitere Regel hinzuzufügen. Geben Sie so viele Regeln wie erforderlich ein. Regeln werden mit dem booleschen Operator UND kombiniert. Das bedeutet, dass die Zielgruppe alle Anforderungen jeder Regel erfüllen muss, um für eine Aktivität zugelassen zu werden.
1. Tippen oder klicken Sie auf **Weiter**.
1. Geben Sie einen Namen für die Zielgruppe ein und tippen oder klicken Sie auf **Speichern**.
1. Tippen oder klicken Sie auf **Speichern**. Ihre Zielgruppe wird nun in der Zielgruppenliste angezeigt.

### Attribute und zugehörige Optionen {#attributes-and-their-options}

Sie können Targeting-Regeln für jedes der folgenden Attribute erstellen:

| **Attribut** | **Beschreibung** | **Für weitere Informationen** |
|---|---|---|
| **Mobilgerät** | Targeting von Mobilgeräten anhand von Parametern wie Mobilgerät, Gerätetyp, Geräteanbieter, Bildschirmmaßen (in Pixeln) usw. | Siehe [Mobile Dokumentation](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/mobile.html?lang=de) in Adobe Target. |
| **Benutzerdefiniert** | Benutzerdefinierte Parameter sind Mbox-Parameter. Wenn Sie Mbox-Parameter an Mboxes übergeben oder die Funktion „targetPageParams“ verwenden, werden diese Parameter hier angezeigt und können in Zielgruppen verwendet werden. | Siehe [Dokumentation zu benutzerdefinierten Parametern](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/custom-parameters.html?lang=de) in Adobe Target. |
| **BS** | Sie können Besucher, die ein bestimmtes Betriebssystem verwenden, als Ziel auswählen. | Geben Sie Benutzer als Ziel an, die Linux®, Macintosh oder Windows verwenden. |
| **Seiten der Site** | Targeting von Besuchern, die sich auf einer bestimmten Seite befinden oder die einen bestimmten Mbox-Parameter aufweisen. | Weitere Informationen finden Sie in der [Dokumentation für Website-Seiten](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/site-pages.html?lang=de) für Adobe Target. |
| **Browser** | Sie können Benutzer, die einen bestimmten Browser oder bestimmte Browseroptionen beim Besuch Ihrer Seite verwenden, als Ziel auswählen. | Weitere Informationen finden Sie in der [Dokumentation für Browser-Optionen](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/browser.html?lang=de?lang=en) für Adobe Target. |
| **Besucherprofil** | Targeting von Besuchern, die bestimmte Profilparameter erfüllen. | Weitere Informationen finden Sie in der [Dokumentation für Besucherprofile](https://experienceleague.adobe.com/docs/target/using/audiences/visitor-profiles/visitor-profile.html?lang=de) für Adobe Target. |
| **Traffic-Quellen** | Targeting von Besuchern auf Grundlage der Suchmaschine oder Landingpage, von der sie auf Ihre Site geleitet werden | Weitere Informationen finden Sie in der [Dokumentation für Traffic-Quellen](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/traffic-sources.html?lang=de) für Adobe Target. |

## Bearbeiten von Zielgruppen mithilfe der Konsole „Zielgruppen“ {#modifying-an-audience-in-the-audiences-console}

>[!NOTE]
>
>Sie können nur Adobe Target-Zielgruppen bearbeiten, die in derselben AEM erstellt wurden, in der Sie gerade arbeiten. Zielgruppen, die in unterschiedlichen AEM erstellt wurden, können nicht bearbeitet werden.

Sie können eine beliebige ContextHub- oder ClientContext-Zielgruppe über die Konsole &quot;Zielgruppen&quot;bearbeiten. Sie können auch Adobe Target-Zielgruppen bearbeiten, jedoch nur die in AEM erstellten Zielgruppen:

1. Klicken oder tippen Sie in der Navigationskonsole auf **Personalisierung**. Klicken oder tippen Sie auf **Zielgruppen**.
1. Klicken oder tippen Sie auf das Symbol neben dem zu bearbeitenden ContextHub- oder Client Context-Segment und tippen oder klicken Sie auf **Bearbeiten**.
1. Bearbeiten Sie die gewünschten Einstellungen im Editor. Siehe [ClientContext](/help/sites-administering/campaign-segmentation.md) oder [ContextHub](/help/sites-developing/ch-configuring.md) Dokumentation.
