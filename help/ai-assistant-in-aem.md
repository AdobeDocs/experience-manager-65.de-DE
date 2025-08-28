---
title: KI-Assistent in AEM 6.5
description: Verwenden Sie den KI-Assistenten, um Antworten auf die in Adobe Experience Manager verfügbaren Lösungen zu finden und Fehler zu beheben.
solution: Experience Manager, Experience Manager 6.5
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 3b4a484e-55b5-4924-82dd-56735f6ed46d
source-git-commit: c98a66a4b4be23145334b339a793ded1716e9889
workflow-type: tm+mt
source-wordcount: '1296'
ht-degree: 1%

---

# KI-Assistent in AEM 6.5 {#about-ai-assistant-in-aem}

>[!IMPORTANT]
>
>Kunden von AEM 6.5 und AEM 6.5 LTS, die nicht Cloud Manager/Experience Hub verwenden, müssen sich an ihren Adobe Customer Success Engineer wenden, um Zugriff auf den KI-Assistenten zu erhalten.

Der KI-Assistent in AEM 6.5/AEM 6.5 LTS bietet eine Konversationsoberfläche, die darauf ausgelegt ist, die Suche nach Antworten auf Ihre Adobe Experience Manager-bezogenen Abfragen zu optimieren. Damit erhalten Sie sofortige Antworten auf Ihre Fragen zum AEM-Produkt *für alle Benutzer verfügbar* und die Erstellung von Support-Tickets (*für Support-Administratoren*).

Der KI-Assistent unterstützt AEM as a Cloud Service, einschließlich der folgenden Lösungen:

* Experience Hub-Übersichtsseite
* Edge Delivery Services
* Sites
* Assets
* Formulare
* Dynamic Media
* Cloud Manager


Es ist direkt in AEM eingebettet und kann über die AEM Experience Hub-, Cloud Manager- und Authoring-Benutzeroberfläche aufgerufen werden.

Das folgende 3-minütige 39-Sekunden-Video bietet eine schrittweise Anleitung zum KI-Assistenten in AEM.

>[!VIDEO](https://video.tv.adobe.com/v/3470354?learn=on)

## Zugriff auf den KI-Assistenten in AEM{#get-access}

Um Benutzenden Zugriff auf den KI-Assistenten in AEM zu gewähren, muss Ihr Adobe-Administrator die folgenden benutzerdefinierten Berechtigungen für die Profile konfigurieren, für die Zugriff in der **Adobe Admin Console erforderlich ist**:

* **Zugriff auf KI-Assistent** - Berechtigung, den KI-Assistenten in AEM für Produktkenntnisse zu verwenden, sodass Benutzende produktbezogene Fragen im KI-Assistenten-Chat stellen können. Diese Berechtigung muss aktiviert sein.
* **Support-Zugriff** - Benutzende müssen außerdem über die Berechtigung zum Öffnen von Support-Tickets verfügen. Dafür ist die Rolle **Support-Admin** erforderlich.

KI-Assistentenanfragen in AEM werden über Adobe Identity Management Services (IMS) authentifiziert. Weitere Informationen finden Sie in der [Übersicht über Adobe Identity Management Services](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/corporate/adobe-identity-management-services-security-overview.pdf).

**So erhalten Sie Zugriff auf den KI-Assistenten in AEM:**

1. Kunden müssen über eine zusätzliche Vereinbarung verfügen, um auf die meisten KI-gestützten und agenten Funktionen in Adobe Experience Manager zugreifen zu können. Weitere Informationen erhalten Sie vom Adobe-Support.

<!-- OLD STEP 1 [Customers must sign the Gen AI rider with Adobe](https://fieldreadiness-adobe.highspot.com/items/665f831c9f831b011aeda057#1). 

    The GenAI Rider is a legal agreement between a customer and Adobe, required to use most AI and agentic capabilities. Contact Adobe Customer Care to learn more. -->

1. Der AEM-Administrator konfiguriert den KI-Assistenten für die Verwendung in der Organisation. Siehe [Konfigurieren des KI-Assistenten in AEM](/help/ai-assistant-in-aem-admin.md).

<!--
>[!IMPORTANT]
>Be sure you have reviewed and submitted the user agreement so Adobe can enable the AI Assistant feature for you to test out and participate in the private beta program.
>
>For any questions, send an email to [Grp-AEMAIASSISTANT@adobe.com](mailto:Grp-AEMAIASSISTANT@adobe.com) from your email address associated with your Adobe ID. -->

## Umfang {#scope}

Der aktuelle Umfang des KI-Assistenten in AEM konzentriert sich auf Fragen zum Produktwissen für AEMr.as a Cloud Service. Dieser Umfang umfasst eine umfassende Unterstützung für Schlüsselbereiche. <!--, such as Sites, Assets, Forms, Edge Delivery Services, Dynamic Media, and Cloud Manager. -->

* **Oberflächen**: In AEM Experience Hub, der Authoring-Benutzeroberfläche und Cloud Manager verfügbar.
* **Funktionen**: Produktwissen und erste Anlaufstelle für Fehlerbehebung und Anleitung, automatisierte Erstellung von Support-Tickets und Suche.
* **Wert**: Spart Zeit, beschleunigt das Lernen und die Wertschöpfungszeit, reduziert die Notwendigkeit, Support-Tickets manuell zu erstellen, und verbessert die Effizienz bei der Erstellung von Support-Tickets.

## Datenschutz, Sicherheit und Governance{#privacy-security-governance}

Der KI-Assistent in AEM ist so konzipiert, dass ein besonderer Schwerpunkt auf Datenschutz, Sicherheit und Governance gelegt wird.

In diesem Artikel werden die vertrauensorientierten Funktionen beschrieben, die Sie vom KI-Assistenten in AEM erwarten können:

* KI Assistant verwendet in AEM keine personenbezogenen Daten, auch nicht für Trainingszwecke.
* Der KI-Assistent in AEM hat keinen Zugriff auf Verbraucherdaten.
* Für die Interaktion mit dem KI-Assistenten in AEM ist eine explizite Berechtigung erforderlich.
* Von Benutzenden bereitgestellte Eingabeaufforderungen (Fragen, Abfragen usw.) werden nicht für andere Kundinnen und Kunden freigegeben.

<!-- See also [Security at Adobe whitepaper](). NEED ACTIVE LINK FROM ADRIAN NICOLAE TANASE. CURRENTLY 404. -->

## Lernen Sie den KI-Assistenten in AEM für Produktkenntnisse und die automatisierte Erstellung von Support-Tickets kennen {#ai-prod-insights}

Das Produktwissen umfasst Konzepte und Themen, die aus der Dokumentation zu Adobe Experience League abgeleitet wurden. Diese Fragen lassen sich in die folgenden Untergruppen einteilen:


| Produktkenntnisse | Verfügbar für alle Benutzer<br>Beispiele |
| :--- | :--- |
| Punktuelles Lernen | <ul><li>Was ist der universelle Editor?</li><li>Wie erstelle ich ein Programm in Cloud Manager?</li></ul> |
| Erkennung öffnen | <ul><li>Wie verwende ich den universellen Editor?</li><li>Gibt es eine Möglichkeit, Inhalte von einer Umgebung in eine andere zu kopieren?</li></ul> |
| Fehlerbehebung | <ul><li>Warum kann ich nicht auf den universellen Editor zugreifen?</li><li>Warum schlägt meine Pipeline fehl?</li></ul> |
| **Support-Ticket-Erstellung** | **Nur für Support-Administratoren verfügbar &#x200B;**<br>**Beispiele** |
| Automatisierte Erstellung von Support-Tickets zur Erfassung des Verlaufs und Kontexts des KI-Assistenten | <ul><li>Erstellen Sie ein Support-Ticket für mich.</li></ul> |
| Abrufen des Status des Support-Tickets | <ul><li>Zeigen Sie mir alle Support-Tickets, die ich geöffnet habe.</li><li>Status des Tickets „E“ -----------</li></ul> |

{style="table-layout:auto"}


## Wie man effektive Fragen formuliert {#ai-craft-questions}

Um vom KI-Assistenten in AEM die genauesten Antworten zu erhalten, ist es wichtig, Ihre Fragen klar und kontextbezogen zu formulieren. Verwenden Sie die folgenden Tipps, um sicherzustellen, dass Ihre Abfragen klar und gut strukturiert sind:

* Geben Sie Ihre Aufgabe oder Frage klar und prägnant an.
* Vermeiden Sie mehrdeutige Formulierungen oder eine übermäßig komplexe Syntax, um das Verständnis zu verbessern.
* Binden Sie relevanten Kontext zu Ihrer Aufgabe oder Frage ein, da dieser Ansatz dem KI-Assistenten in AEM hilft, präzisere und relevantere Antworten zu liefern.
In Ihrer Eingabeaufforderung ist es beispielsweise hilfreich, die AEM-Lösung, in der Sie arbeiten, zu benennen - Sites, Assets, Dynamic Media, Edge Delivery Services, Cloud Manager oder Forms.

### Beispiele für nicht unterstützte Fragen {#ai-unsupported-questions}

| Bereich | Beispiele |
| --- | --- |
| Operative Erkenntnisse | <ul><li>Wie viele Entwicklungsumgebungen gibt es in meinem Mandanten?</li><li>Wer hat die letzte Produktions-Pipeline gestartet?</li></ul> |
| Fehlerbehebung | <ul><li>Warum schlägt meine Produktions-Pipeline fehl?</li></ul> |
| Aufgaben und Automatisierung | <ul><li>Konfigurieren Sie eine Code-Qualitäts-Pipeline aus einer Entwicklungsverzweigung für mich.</li></ul> |


## Verwenden des KI-Assistenten in AEM {#ai-use}

<!-- UNHIDE AFTER BETA or at GA
### Enable AI Assistant in AEM access through Admin Console 

To use the AI Assistant in AEM, your organization must opt in at the Admin Console level. A product administrator creates (or chooses) a user group and grants it the new "AI Assistant" permission. Anyone added to that group instantly gains access to the Assistant across AEM. If the goal is company-wide availability, the admin simply assigns all users to that group.

![AI Assistant in AEM in the Admin Console](/help/implementing/cloud-manager/assets/ai-assistant-admin-console.png)

From an employee's perspective, the process is straightforward: identify the product administrator for Adobe Experience Manager in your organization and request to be added to the AI-enabled user group. Once you appear in that group, the Assistant icon shows up automatically the next time you sign in.

Administrators should keep normal Cloud Manager governance in mind. Hold product administrator rights in the Admin Console to create profiles, manage user groups, or edit permissions. If users also need the Assistant's built-in **Create Support Ticket** feature, add the standard **Support Admin** role (standard Admin Console role) to the same individuals or group.

![Technical support ticket creation in the AI Assistant in AEM of the Admin Console](/help/implementing/cloud-manager/assets/ai-assistant-admin-console-support-ticket.png)

For a guided walkthrough of setting up users and groups in AEM as a Cloud Service, see [Configuring access to AEM as a Cloud Service ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/accessing/overview). 

See also [Custom Permissions](/help/implementing/cloud-manager/custom-permissions.md). -->


### Starten eines KI-Assistenten in einer AEM-Unterhaltung

Sie können den KI-Assistenten in AEM zurücksetzen und eine neue Unterhaltung beginnen, wenn Sie Themen ändern möchten. Diese Funktion ist besonders hilfreich bei der Fehlerbehebung bei Abfragen, die fehlschlagen oder falsche Informationen liefern.

**So starten Sie einen KI-Assistenten in einer AEM-Konversation:**

1. Klicken Sie in der rechten oberen Ecke der Benutzeroberfläche von AEM (entweder auf den Cloud Manager-Seiten oder in der Autoreninstanz der AEM-Umgebungen) auf das Symbol **KI-**).

   ![Symbol „KI-Assistent“ in der Symbolleiste](/help/assets/assets-ai/ai-assistant-icon.png)

1. Geben Sie im Textfeld **KI** Assistent“ unten Ihre Frage oder Eingabeaufforderung ein und drücken Sie dann die `Enter` oder klicken Sie auf ![Senden-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Send_18_N.svg).

   >[!NOTE]
   >
   >Personenbezogene Daten sollten nicht in Ihre Eingaben aufgenommen werden, da sie für die Verwendung dieses Tools nicht erforderlich sind.

   ![Textfeld am unteren Rand des Bedienfelds „KI-Assistent“](/help/assets/assets-ai/ai-assistant-prompt-text-box.png)

1. Um eine neue Unterhaltung (neues Thema oder eine Änderung im Thema) zu beginnen, klicken Sie auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) > **Neue Unterhaltung beginnen**.

   ![Beginnen Sie eine neue Konversation im KI-Assistenten über das Symbol mit den Auslassungspunkten](/help/assets/assets-ai/ai-assistant-start-new-conversation.png)

### Eingabeaufforderungen nach Kategorie erkennen

Der KI-Assistent in AEM enthält eine Entdeckungsfunktion, mit der Sie unterstützte Themen und Kategorien erkunden können.

**So ermitteln Sie Eingabeaufforderungen nach Kategorie:**

1. Klicken Sie im Bedienfeld „KI-Assistent“ auf ![Lernsymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Learn_18_N.svg), um das Bedienfeld „Eingabeaufforderung - Erkennung“ einzuschalten.

   ![Bedienfeld, mit dem Sie Eingabeaufforderungen nach Kategorie im KI-Assistenten untersuchen können](/help/assets/assets-ai/ai-assistant-discover-prompts.png)
   *Bedienfeld, das die Aufforderungskategorien im KI-Assistenten anzeigt.*

1. Wählen Sie eine Kategorie aus, um eine Liste der zugehörigen Eingabeaufforderungen anzuzeigen.
1. Wählen Sie eine Eingabeaufforderung aus, um Beispiele für die Arten von Fragen anzuzeigen, die der KI-Assistent beantworten kann.

1. Um das Bedienfeld für die Eingabeaufforderungserkennung auszublenden, klicken Sie erneut ![Symbol „Lernen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Learn_18_N.svg).

### Feedback zum KI-Assistenten in AEM geben

Ihre Eingabe hilft Adobe, den KI-Assistenten zu verbessern, um die Leistung und Genauigkeit zu verbessern.

Geben Sie Ihr Feedback zu Ihren Erfahrungen mit dem KI-Assistenten in AEM mithilfe der folgenden Optionen:

![Symbole „Daumen hoch“, „Daumen runter“ und „Markierung“](/help/assets/assets-ai/ai-assistant-feedback-icons.png)

| Klicken Sie auf | Beschreibung |
| --- | --- |
| ![Miniaturansicht nach oben](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ThumbUpOutline_18_N.svg) | Geben Sie an, was gut gelaufen ist, und teilen Sie positives Feedback. |
| ![Miniaturansicht nach unten](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ThumbDownOutline_18_N.svg) | Geben Sie Verbesserungsvorschläge. Fügen Sie spezifische Kommentare zu Ihrem Erlebnis hinzu, die täglich überprüft werden. |
| ![Flag-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Flag_18_N.svg) | Melden Sie Probleme oder geben Sie detailliertes Feedback zu Ihrer Interaktion mit dem KI-Assistenten in AEM. |

## Häufig gestellte Fragen zum KI-Assistenten in AEM {#ai-faq}

Im Folgenden finden Sie Antworten auf einige häufig gestellte Fragen zum KI-Assistenten:

* **Werden die Informationen vom KI-Assistenten in AEM in Echtzeit bereitgestellt?**\
  Nein. Der KI-Assistent bezieht seinen Inhalt aus der Adobe Experience League-Dokumentation. Es kann einige Zeit dauern, bis Aktualisierungen des Inhalts in den Antworten widergespiegelt werden.
* **Welche Adobe-Programme unterstützt AI Assistant in AEM?**\
  Derzeit unterstützt der KI-Assistent Anfragen zu Produktkenntnissen in AEM as a Cloud Service, einschließlich Sites, Assets, Dynamic Media, Cloud Manager und Forms.
* **Welche Funktionen hat der KI-Assistent in AEM?**\
  Der KI-Assistent in AEM beantwortet Fragen zu Adobe-Produktkenntnissen.
* **Verwendet der KI-Assistent in AEM personenbezogene Daten für Trainingsdaten?**\
  Nein. Der KI-Assistent in AEM verwendet keine personenbezogenen Daten für Trainingszwecke. Vermeiden Sie es, persönliche Informationen über sich selbst oder andere, einschließlich Namen oder Kontaktdaten, mit dem KI-Assistenten in AEM zu teilen.

<!-- IS THE DOCUMENTATION BELOW STILL NEEDED? IF SO, GO AHEAD AND DELETE THE COMMENT TAGS!!

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
