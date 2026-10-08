---
title: KI-Assistent in AEM 6.5
description: Verwenden Sie den KI-Assistenten, um Antworten zu finden und Probleme mithilfe der in Adobe Experience Manager verfügbaren Lösungen zu beheben.
solution: Experience Manager, Experience Manager 6.5
feature: Authoring, AI Assistant, AI Tools
role: Admin, Developer, User
exl-id: 3b4a484e-55b5-4924-82dd-56735f6ed46d
autotag-review: '2026-05-18T18:36:07.915Z'
TQID: 'https://experienceleague.adobe.com/dlFmrtn05S20z96wtAfkpGliITeVJhVkofqPix6QMxk'
product_v2:
  - id: e14eb250-3c22-4a07-9061-a78112b2b826
    internal-label: Experience Manager 6.5
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: ac5ecfc1-cc78-4ecc-a90a-0362685062ce
    internal-label: AI Tools
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
    internal-label: Customer experience
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: c7d04a2c-412a-4c9d-9d7a-4456eaa5adeb
    internal-label: Governance
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
    internal-label: Insights
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
source-git-commit: a6f7741fe575a194732abee7dfc9c531d1c58cc2
workflow-type: tm+mt
source-wordcount: '1327'
ht-degree: 79%
---
# KI-Assistent in AEM 6.5 {#about-ai-assistant-in-aem}

>[!IMPORTANT]
>
>Kundinnen und Kunden von AEM 6.5 und AEM 6.5 LTS, die nicht Cloud Manager/Experience Hub verwenden, müssen sich an ihren Adobe Customer Success Engineer wenden, um Zugriff auf den KI-Assistenten zu erhalten.

Der KI-Assistent in AEM 6.5/AEM 6.5 LTS bietet eine Konversationsoberfläche, die darauf ausgelegt ist, die Suche nach Antworten auf Ihre Adobe Experience Manager-bezogenen Abfragen zu optimieren. Die Dialogoberfläche erlaubt es Ihnen, sofort Antworten auf Ihre produktbezogenen Fragen zu AEM zu erhalten (*für alle Benutzenden verfügbar*) und die Erstellung von Support-Tickets zu automatisieren (*für Support-Admins verfügbar*).

Der KI-Assistent unterstützt AEM as a Cloud Service, einschließlich der folgenden Lösungen:

* Experience Hub-Überblicksseite
* Edge Delivery Services
* Sites
* Assets
* Formulare
* Dynamic Media
* Cloud Manager


Er ist direkt in AEM eingebettet und kann über die AEM Experience Hub-, Cloud Manager- und Authoring-Benutzeroberfläche aufgerufen werden.

Das folgende Video (3 Minuten und 25 Sekunden lang) bietet eine schrittweise Anleitung zum KI-Assistenten in AEM.

>[!VIDEO](https://video.tv.adobe.com/v/3475357/?learn=on&enablevpops)

## Zugriff auf den KI-Assistenten in AEM erhalten{#get-access}

Um Zugriff auf den KI-Assistenten in AEM zu erhalten, müssen Kundinnen und Kunden über Folgendes verfügen:

* Zugriff auf Produktkenntnisse, über die Sie im KI-Assistenten-Chat produktbezogene Fragen stellen können. Dieser Zugriff steht standardmäßig allen Benutzern in Ihrer Organisation zur Verfügung.
* Berechtigung zum Öffnen von Support-Tickets, wofür die Rolle **Support-Admin** erforderlich ist.

>[!NOTE]
>
>Anfragen an den KI-Assistenten in AEM werden über Adobe Identity Management Services (IMS) authentifiziert. Weitere Informationen finden Sie im [Überblick über Adobe Identity Management Services](https://www.adobe.com/cc-shared/assets/pdf/trust-center/ungated/whitepapers/corporate/adobe-identity-management-services-security-overview.pdf).

**So erhalten Sie Zugriff auf den KI-Assistenten in AEM:**

1. Kundinnen und Kunden müssen über eine Zusatzvereinbarung verfügen, um auf die meisten KI-gestützten und Agent-basierten Funktionen in Adobe Experience Manager zugreifen zu können. Weitere Informationen erhalten Sie vom Adobe-Support-Personal. Informationen zur Funktionsweise der Aktivierung generativer KI finden Sie unter [Generative KI in CX Enterprise-Programmen](https://experienceleague.adobe.com/de/docs/cx-enterprise-ai/experience-cloud-ai/overview/generative-ai).

1. Sobald Ihr Unternehmen über diese Vereinbarung verfügt, können alle Benutzer standardmäßig den KI-Assistenten für Produktkenntnisse verwenden. Es sind keine zusätzlichen Berechtigungen pro Benutzer oder pro Gruppe erforderlich.


## Umfang {#scope}

Der aktuelle Umfang des KI-Assistenten in AEM konzentriert sich auf Fragen zum Produktwissen für AEM as a Cloud Service. Dieser Anwendungsbereich beinhaltet umfassende Unterstützung für Schlüsselbereiche. <!--, such as Sites, Assets, Forms, Edge Delivery Services, Dynamic Media, and Cloud Manager. -->

* **Oberflächen**: In AEM Experience Hub, der Authoring-Benutzeroberfläche und Cloud Manager verfügbar.
* **Funktionen**: Produktwissen und primäre Ressource für Fehlerbehebung und Anleitung, automatisierte Erstellung von Support-Tickets und Suche.
* **Vorteil**: Spart Zeit, beschleunigt das Auffinden von Informationen und die Wertschöpfungszeit, reduziert die Notwendigkeit einer manuellen Erstellung von Support-Tickets und erhöht die Effizienz beim Erstellen von Support-Tickets.

## Datenschutz, Sicherheit und Governance{#privacy-security-governance}

Der KI-Assistent in AEM ist so konzipiert, dass großer Wert auf Datenschutz, Sicherheit und Governance gelegt wird.

In diesem Artikel werden die Funktionen beschrieben, die Sie vom KI-Assistenten in AEM erwarten können, um Vertrauen zu schaffen:

* KI Assistant in AEM verwendet keine personenbezogenen Daten, auch nicht für Trainingszwecke.
* Der KI-Assistent in AEM hat keinen Zugriff auf Konsumentendaten.
* Für Interaktion mit dem KI-Assistenten in AEM ist eine explizite Berechtigung erforderlich.
* Von Benutzenden gestellte Prompts (Fragen, Abfragen usw.) werden nicht mit anderen Kundinnen und Kunden geteilt.

<!-- See also [Security at Adobe whitepaper](). NEED ACTIVE LINK FROM ADRIAN NICOLAE TANASE. CURRENTLY 404. -->

## Erfahren Sie mehr über den KI-Assistenten in AEM für Produktkenntnisse und die automatisierte Erstellung von Support-Tickets {#ai-prod-insights}

Produktkenntnisse umfassen Konzepte und Themen, die aus der Dokumentation zu Adobe Experience League abgeleitet wurden. Diese Fragen lassen sich in folgende Untergruppen einteilen:


| Produktkenntnisse | Verfügbar für alle Benutzenden<br>Beispiele |
| :--- | :--- |
| Gezieltes Lernen | <ul><li>Was ist der universelle Editor?</li><li>Wie erstelle ich ein Programm in Cloud Manager?</li></ul> |
| Erkennung öffnen | <ul><li>Wie verwende ich den universellen Editor?</li><li>Gibt es eine Möglichkeit, Inhalte von einer Umgebung in eine andere zu kopieren?</li></ul> |
| Fehlerbehebung | <ul><li>Warum kann ich nicht auf den universellen Editor zugreifen?</li><li>Warum schlägt meine Pipeline fehl?</li></ul> |
| **Erstellung von Support-Tickets** | **Nur für Support-Admins verfügbar &#x200B;**<br>**Beispiele** |
| Automatisierte Erstellung von Support-Tickets zur Erfassung des Verlaufs und Kontexts des KI-Assistenten | <ul><li>Erstelle ein Support-Ticket für mich.</li></ul> |
| Status von Support-Ticket abrufen | <ul><li>Zeige mir alle Support-Tickets, die ich geöffnet habe.</li><li>Zeige mir den Status von Ticket „E-----------“</li></ul> |

{style="table-layout:auto"}


## Wie man effektive Fragen schreibt {#ai-craft-questions}

Um vom KI-Assistenten in AEM präzise Antworten zu erhalten, ist es wichtig, dass Sie Ihre Fragen klar und kontextbezogen formulieren. Verwenden Sie folgende Tipps, um dafür zu sorgen, dass Ihre Abfragen klar und gut strukturiert sind:

* Formulieren Sie Ihre Aufgabe oder Frage klar und prägnant.
* Um das Verständnis zu verbessern, vermeiden Sie mehrdeutige Formulierungen oder eine übermäßig komplexe Syntax.
* Binden Sie relevanten Kontext zu Ihrer Aufgabe oder Frage ein, da dies dem KI-Assistenten in AEM hilft, präzisere und relevantere Antworten zu liefern.
Nennen Sie beispielsweise in der Eingabeaufforderung die AEM-Lösung, in der Sie arbeiten.

### Beispiele für nicht unterstützte Fragen {#ai-unsupported-questions}

| Bereich | Beispiele |
| --- | --- |
| Betriebliche Erkenntnisse | <ul><li>Wie viele Entwicklungsumgebungen gibt es in meinem Mandanten?</li><li>Wer hat die letzte Produktions-Pipeline gestartet?</li></ul> |
| Fehlerbehebung | <ul><li>Warum schlägt meine Produktions-Pipeline fehl?</li></ul> |
| Aufgabe und Automatisierung | <ul><li>Konfiguriere für mich aus einer Entwicklungsverzweigung eine Pipeline zur Code-Qualität.</li></ul> |


## KI-Assistent in AEM verwenden {#ai-use}

### Den KI-Assistenten in einer AEM-Unterhaltung starten

Sie können den KI-Assistenten in AEM zurücksetzen und eine neue Unterhaltung beginnen, wenn Sie Themen ändern möchten. Diese Funktion ist besonders nützlich bei der Fehlerbehebung bei Abfragen, die fehlschlagen oder falsche Informationen liefern.

**So starten Sie einen KI-Assistenten in einer AEM-Unterhaltung:**

1. Klicken Sie in der rechten oberen Ecke der Benutzeroberfläche von AEM (entweder auf den Cloud Manager-Seiten oder in der Autoreninstanz der AEM-Umgebungen) auf das Symbol **KI-Assistent**.

   ![Symbol „KI-Assistent“ in der Symbolleiste](/help/assets/assets-ai/ai-assistant-icon.png)

1. Geben Sie im Textfeld **KI-Assistent** unten Ihre Frage oder Ihren Prompt ein und drücken Sie dann `Enter` oder klicken Sie auf das Symbol zum ![Senden](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Send_18_N.svg).

   >[!NOTE]
   >
   >Sie sollten in Ihren Eingaben keine personenbezogenen Daten nutzen, da sie für die Verwendung dieses Tools nicht erforderlich sind.

   ![Textfeld am unteren Rand des Bedienfelds „KI-Assistent“](/help/assets/assets-ai/ai-assistant-prompt-text-box.png)

1. Um eine neue Unterhaltung (neues Thema oder anderes Thema) zu starten, klicken Sie auf das ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) > **Neue Unterhaltung beginnen**.

   ![Eine neue Unterhaltung im KI-Assistenten über das Symbol mit den Auslassungspunkten beginnen](/help/assets/assets-ai/ai-assistant-start-new-conversation.png)

### Prompts nach Kategorie entdecken

Der KI-Assistent in AEM umfasst eine Entdeckungsfunktion, mit der Sie unterstützte Themen und Kategorien erkunden können.

**So entdecken Sie Prompts nach Kategorie:**

1. Klicken Sie im Bedienfeld „KI-Assistent“ auf das ![Infosymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Learn_18_N.svg), um das Bedienfeld für die Entdeckung von Prompts zu aktivieren.

   ![Bedienfeld, mit dem Sie Prompts im KI-Assistenten nach Kategorie erkunden können](/help/assets/assets-ai/ai-assistant-discover-prompts.png)
   *Bedienfeld, das die Prompt-Kategorien im KI-Assistenten anzeigt.*

1. Wählen Sie eine Kategorie aus, um eine Liste der zugehörigen Prompts anzuzeigen.
1. Wählen Sie einen Prompt aus, um Beispiele für die Arten von Fragen zu sehen, die der KI-Assistent beantworten kann.

1. Um das Bedienfeld für die Entdeckung von Prompts auszublenden, klicken Sie erneut auf das ![Infosymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Learn_18_N.svg).

### Feedback zum KI-Assistenten in AEM geben

Ihr Feedback hilft Adobe, den KI-Assistenten zu verbessern, um Leistung und Genauigkeit zu erhöhen.

Geben Sie mithilfe der folgenden Optionen Feedback zu Ihren Erfahrungen mit dem KI-Assistenten in AEM:

![Daumen nach oben-, Daumen nach unten- und Unangemessen-Symbole](/help/assets/assets-ai/ai-assistant-feedback-icons.png)

| Klicken Sie auf | Beschreibung |
| --- | --- |
| ![Daumen nach oben-Kontursymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ThumbUpOutline_18_N.svg) | Geben Sie an, was gut gelaufen ist, und geben Sie positives Feedback. |
| ![Daumen nach unten-Kontursymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ThumbDownOutline_18_N.svg) | Geben Sie Verbesserungsvorschläge. Fügen Sie spezifische Kommentare zu Ihrem Erlebnis hinzu, die täglich überprüft werden. |
| ![Unangemessen-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Flag_18_N.svg) | Melden Sie Probleme oder geben Sie detailliertes Feedback zu Ihrer Interaktion mit dem KI-Assistenten in AEM. |

## Häufig gestellte Fragen zum KI-Assistenten in AEM {#ai-faq}

Im Folgenden finden Sie Antworten auf einige häufig gestellte Fragen zum KI-Assistenten:

* **Sind die Informationen vom KI-Assistenten in AEM in Echtzeit?**\
  Nein. Der KI-Assistent bezieht seinen Content aus der Adobe Experience League-Dokumentation. Es dauert einige Zeit, bis Aktualisierungen des Inhalts in den Antworten widergespiegelt werden.
* **Welche Adobe-Anwendungen unterstützt der KI-Assistant in AEM?**\
  Derzeit unterstützt AI Assistant Anfragen zu Produktkenntnissen in AEM as a Cloud Service.
* **Welche Funktionen hat der KI-Assistent in AEM?**\
  Der KI-Assistent in AEM beantwortet Fragen zu Adobe-Produktwissen.
* **Verwendet der KI-Assistent in AEM personenbezogene Daten für Trainings-Daten?**\
  Nein. Der KI-Assistent in AEM verwendet keine personenbezogenen Daten für Trainings-Zwecke. Vermeiden Sie es, persönliche Daten über sich selbst oder andere, einschließlich Namen oder Kontaktdaten, mit dem KI-Assistenten in AEM zu teilen.

<!--
IS THE DOCUMENTATION BELOW STILL NEEDED? IF SO, GO AHEAD AND DELETE THE COMMENT TAGS!!

## AEM Forms AI Assistant (Forms Experience Builder) {#ai-forms-builder}

In addition to the general AI Assistant in AEM for product knowledge, AEM offers a specialized **[AEM Forms AI Assistant (Forms Experience Builder)](/help/edge/docs/forms/forms-ai-assistant.md)**. This enhanced assistant can actively help you create and configure forms through natural language prompts and answer questions specific to forms.

### Key capabilities

The AEM Forms AI Assistant provides:

* **Form Creation**: Create new forms from scratch using natural language descriptions.
* **Design Import**: Convert existing designs (PDF, Figma, images) into functional AEM Forms. 
* **Form Configuration**: Add fields, panels, validation rules, and conditional logic.
* **Layout Management**: Organize form structure and optimize for different devices.
* **Integration Setup**: Configure form submissions and data handling.
* **Product Knowledge**: Answer questions about AEM Forms features and best practices.

### Where to access

The AEM Forms AI Assistant is available in the following:

* **Universal Editor**: For Edge Delivery Services forms with visual editing capabilities.
* **Adaptive Forms Editor**: For detailed form configuration and advanced features.
* **Forms Management UI**: For high-level form creation and management tasks.

### Getting started

>[!NOTE]
>
> The AEM Forms AI Assistant (Forms Experience Builder) is available under the private beta program. Send an email from your work address to [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) to request access.

To learn more about using the AEM Forms AI Assistant , see the [AEM Forms AI Assistant](/help/edge/docs/forms/forms-ai-assistant.md) documentation.

### Example Use Cases

* **"Create a customer feedback form with name, email, rating, and comments fields"**
* **"Convert this uploaded PDF application form into a digital adaptive form"**  
* **"Add conditional logic to show spouse information only when marital status is 'Married'"**
* **"Configure this form to submit data to the Customer Relationship Management system"**

This specialized AEM Forms AI Assistant represents the next evolution in form building, combining the power of AI with AEM's robust forms capabilities to streamline your form creation workflow.
-->
