---
title: Verwalten von Zielgruppen
description: Mithilfe der Zielgruppenkonsole können Sie Zielgruppen für Ihr Adobe Target-Konto erstellen, organisieren und verwalten oder Segmente für ContextHub bzw. ClientContext verwalten.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
docset: aem65
exl-id: 97e02986-049f-4747-a67a-6aa0677b281e
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Personalization
role: User,Admin,Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 100%

---

# Verwalten von Zielgruppen{#managing-audiences}

Mithilfe der Zielgruppenkonsole können Sie Zielgruppen für Ihr Adobe Target-Konto erstellen, organisieren und verwalten oder Segmente für ContextHub bzw. ClientContext verwalten:

* Zielgruppen hinzufügen – entweder Adobe Target-Zielgruppen oder ContextHub-Segmente.
* Verwalten von Zielgruppen

„Zielgruppen“ werden in ContextHub und ClientContext als *Segment* bezeichnet und sind Besuchergruppen, die durch bestimmte Kriterien definiert werden und mit denen bestimmt wird, wer welche zielgerichteten Inhalte zu sehen bekommt. Wenn Sie eine Aktivität als Ziel auswählen, können Sie Zielgruppen entweder direkt bei der Zielgruppenbestimmung auswählen oder weitere Zielgruppen in der Zielgruppen-Konsole erstellen.

In der Zielgruppen-Konsole werden die Zielgruppen nach Marken geordnet.

Zielgruppen stehen im Targeting-Modus für das [Erstellen zielgerichteter Inhalte](/help/sites-authoring/content-targeting-touch.md) zur Verfügung. In diesem Modus können außerdem auch Zielgruppen erstellt werden (Zielgruppen für Adobe Target müssen hingegen in der Zielgruppen-Konsole erstellt werden). Zielgruppen, die Sie im Targeting-Modus erstellen, werden in der Zielgruppen-Konsole angezeigt.

Zielgruppen werden mit einer Beschriftung angezeigt, die beschreibt, welche Art von Zielgruppe definiert ist:

* CH – ContextHub-Segment
* CC – ClientContext-Segment
* AT – Adobe Target-Zielgruppe

## Erstellen von ContextHub-Segmenten mit der Konsole „Zielgruppen“ {#creating-a-contexthub-segment-in-the-audiences-console}

Sie können ContextHub-Segmente entweder in der Konsole „Zielgruppen“ oder während des Targeting-Verfahrens erstellen.

So erstellen Sie ContextHub-Segmente in der Konsole „Zielgruppen“:

1. Klicken Sie in der Navigationskonsole auf **Personalisierung**. Klicken Sie auf **Zielgruppen**.
1. Klicken Sie auf **ContextHub-Segment erstellen**.

   ![screen-shot_2019-03-05at124034](assets/screen-shot_2019-03-05at124034.png)

1. Geben Sie im Dialogfeld **Neues ContextHub-Segment** einen Titel ein, passen Sie die Verstärkung an und klicken Sie auf **Erstellen**. Das neue ContextHub-Segment erscheint in der Zielgruppenliste.

   >[!NOTE]
   >
   >Sie können die geänderte Liste sortieren, indem Sie auf **Bearbeitet** klicken oder tippen, um Elemente in absteigender Reihenfolge anzuordnen, sodass zuletzt erstellte Zielgruppen ganz oben aufgeführt sind.

Weitere Informationen zum Erstellen von Segmenten mit ContextHub finden Sie in der Dokumentation [Konfigurieren der Segmentierung mit ContextHub](/help/sites-administering/segmentation.md).

## Erstellen von Adobe Target-Zielgruppen mit der Konsole „Zielgruppen“ {#creating-an-adobe-target-audience-using-the-audience-console}

Sie können Adobe Target-Zielgruppen mithilfe der Zielgruppen-Konsole direkt in AEM erstellen.

Zielgruppen werden durch Regeln definiert, die bestimmen, wer in einer Zielgruppenbestimmungs-Aktivität enthalten ist. Eine Zielgruppendefinition kann mehrere Regeln enthalten und jede Regel kann mehrere Parameter enthalten.

Wenn Sie mehr als eine Regel verwenden, werden diese Regeln durch den booleschen Operator AND kombiniert. Das bedeutet, dass jedes potenzielle Mitglied der Zielgruppe alle definierten Bedingungen erfüllen muss, um in die Aktivität aufgenommen zu werden. Wenn Sie beispielsweise eine Betriebssystemregel und eine Browser-Regel definieren, werden nur Besucherinnen und Besucher, die sowohl das definierte Betriebssystem als auch den definierten Browser verwenden, in die Aktivität aufgenommen.

>[!NOTE]
>
>Wird die Option **Target-Zielgruppe erstellen** im Menü **Erstellen** nicht angezeigt, verfügen Sie nicht über die nötigen Berechtigungen zum Erstellung von Zielgruppen. Sie müssen unter **/etc/segmentation** über Schreibrechte verfügen, um Zielgruppen erstellen zu können. Inhaltsautoren der Gruppe verfügen standardmäßig über Schreibrechte.

So erstellen Sie eine Adobe Target-Zielgruppe:

1. Klicken Sie in der Navigationskonsole auf **Personalisierung**. Klicken Sie auf **Zielgruppen**.

   ![screen-shot_2019-03-05at124139](assets/screen-shot_2019-03-05at124139.png)

1. Klicken Sie in der Zielgruppen-Konsole auf **Erstellen** und dann auf „Target-Zielgruppe erstellen“.

   ![chlimage_1-168](assets/chlimage_1-168.png)

1. Wählen Sie im Dialogfeld **Adobe Target-Konfiguration** die Zielgruppenkonfiguration aus und klicken Sie dann auf **OK**.
1. Klicken Sie im Bereich für Regel Nr. 1 auf den Attributtyp und geben Sie in die verfügbaren Felder Attributinformationen ein. Wenn Sie fertig sind, wählen Sie das Häkchen rechts neben dem Attribut aus, um es zu speichern. Weitere Informationen zu allen Attributen finden Sie unter [Attribute und zugehörige Optionen](#attributes-and-their-options).
1. Klicken Sie auf **Regel hinzufügen**, um eine weitere Regel hinzuzufügen. Geben Sie so viele Regeln wie erforderlich ein. Regeln werden mit dem booleschen Operator UND kombiniert. Das bedeutet, dass die Zielgruppe alle Anforderungen jeder Regel erfüllen muss, um für eine Aktivität zugelassen zu werden.
1. Klicken Sie auf **Weiter**.
1. Geben Sie einen Namen für die Zielgruppe ein und klicken Sie auf **Speichern**.
1. Klicken Sie auf **Speichern**. Ihre Zielgruppe wird nun in der Zielgruppenliste angezeigt.

### Attribute und zugehörige Optionen {#attributes-and-their-options}

Sie können Targeting-Regeln für jedes der folgenden Attribute erstellen:

| **Attribut** | **Beschreibung** | **Für weitere Informationen** |
|---|---|---|
| **Mobilgerät** | Targeting von Mobilgeräten anhand von Parametern wie Mobilgerät, Gerätetyp, Geräteanbieterfirma, Bildschirmmaße (in Pixeln) usw. | Siehe [Mobile-Dokumentation](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/mobile.html?lang=de) in Adobe Target. |
| **Benutzerdefiniert** | Benutzerdefinierte Parameter sind Mbox-Parameter. Wenn Sie Mbox-Parameter an Mboxes übergeben oder die Funktion „targetPageParams“ verwenden, werden diese Parameter hier angezeigt und können in Zielgruppen verwendet werden. | Siehe [Dokumentation zu benutzerdefinierten Parametern](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/custom-parameters.html?lang=de) in Adobe Target. |
| **BS** | Sie können Besucherinnen und Besucher, die ein bestimmtes Betriebssystem verwenden, als Ziel auswählen. | Targeting von Benutzenden, die Linux®, Macintosh oder Windows verwenden. |
| **Seiten der Site** | Targeting von Besucherinnen und Besuchern, die sich auf einer bestimmten Seite befinden oder die einen bestimmten mBox-Parameter aufweisen. | Weitere Informationen finden Sie in der [Dokumentation für Website-Seiten](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/site-pages.html?lang=de) für Adobe Target. |
| **Browser** | Sie können Benutzerinnen und Benutzer, die beim Besuch Ihrer Seite einen bestimmten Browser oder bestimmte Browser-Optionen verwenden, als Ziel auswählen. | Weitere Informationen finden Sie in der [Dokumentation für Browser-Optionen](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/browser.html?lang=de) für Adobe Target. |
| **Besucherprofil** | Targeting von Besucherinnen und Besuchern, die bestimmte Profilparameter erfüllen. | Weitere Informationen finden Sie in der [Dokumentation für Besucherprofile](https://experienceleague.adobe.com/docs/target/using/audiences/visitor-profiles/visitor-profile.html?lang=de) für Adobe Target. |
| **Traffic-Quellen** | Targeting von Besuchern auf Grundlage der Suchmaschine oder Landingpage, von der sie auf Ihre Site geleitet werden | Weitere Informationen finden Sie in der [Dokumentation für Traffic-Quellen](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/traffic-sources.html?lang=de) für Adobe Target. |

## Bearbeiten von Zielgruppen mithilfe der Konsole „Zielgruppen“ {#modifying-an-audience-in-the-audiences-console}

>[!NOTE]
>
>Sie können nur Adobe Target-Zielgruppen bearbeiten, die in derselben AEM-Instanz erstellt wurden, in der Sie gerade arbeiten. Zielgruppen, die in unterschiedlichen AEM-Umgebungen erstellt wurden, können nicht bearbeitet werden.

ContextHub- oder Client Context-Zielgruppen lassen sich beliebig mit der Zielgruppen-Konsole bearbeiten. Sie können zudem Adobe Target-Zielgruppen bearbeiten, jedoch nur diejenigen, die in AEM erstellt wurden:

1. Klicken Sie in der Navigationskonsole auf **Personalisierung**. Klicken Sie auf **Zielgruppen**.
1. Klicken Sie auf das Symbol neben dem zu bearbeitenden ContextHub- oder ClientContext-Segment und dann auf **Bearbeiten**.
1. Bearbeiten Sie die gewünschten Einstellungen im Editor. Siehe die Dokumentation zu [Client Context](/help/sites-administering/campaign-segmentation.md) bzw. [ContextHub](/help/sites-developing/ch-configuring.md).
