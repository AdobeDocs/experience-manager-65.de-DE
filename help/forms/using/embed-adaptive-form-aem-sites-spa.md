---
title: Einbetten eines adaptiven Formulars oder einer interaktiven Kommunikation in eine AEM Sites-Einzelseitenanwendung
seo-title: Einbetten adaptiver Formulare oder interaktiver Kommunikation in AEM Sites-Seiten
description: Betten Sie adaptive Formulare oder interaktive Kommunikation in AEM Sites-Seiten ein. Benutzer können Formulare ausfüllen und senden, ohne die Sites-Seite zu verlassen.
seo-description: Sie können adaptive Formulare oder interaktive Kommunikation in AEM Sites-Seiten einbetten. Benutzer können Formulare ausfüllen und senden, ohne die Sites-Seite zu verlassen.
uuid: 4c75494e-e9d2-43b9-bbae-562e0eda8abb
topic-tags: author, interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: a74ed6c1-3006-4baf-bd77-ad4045e23c22
docset: aem65
feature: Adaptive Formulare
exl-id: b549f176-409a-4d81-8c2b-73d0dd0c6649
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1123'
ht-degree: 11%

---

# Einbetten eines adaptiven Formulars oder einer interaktiven Kommunikation in eine AEM Sites-Einzelseitenanwendung{#embed-an-adaptive-form-or-interactive-communication-in-aem-sites-single-page-application}

## Überblick {#overview}

Mit AEM Forms können Formularentwickler adaptive Formulare und interaktive Kommunikation nahtlos in eine AEM Sites-Einzelseiten-App (SPA) einbetten. Das eingebettete adaptive Formular und die interaktive Kommunikation sind voll funktionsfähig und Benutzer können das Formular ausfüllen und senden, ohne die Seite zu verlassen. Dies hilft Benutzern, im Kontext anderer Elemente auf der Webseite zu bleiben und gleichzeitig mit dem adaptiven Formular oder der interaktiven Kommunikation zu interagieren.

In AEM Sites-Einzelseitenanwendungen können Sie ein adaptives Formular oder eine interaktive Kommunikation mithilfe der Komponente [AEM Forms SPA Container](../../forms/using/embed-adaptive-form-aem-sites-spa.md#af-component)[ hinzufügen.](../../forms/using/embed-adaptive-form-aem-sites-spa.md#af-component) Es handelt sich um eine AEM Forms-Komponente für AEM Sites-SPA, die Sie Ihrer Sites-Seite hinzufügen können.

Weitere Informationen zum Einbetten eines adaptiven Formulars in ein nicht SPA AEM Sites finden Sie unter [Einbetten eines adaptiven Formulars oder einer interaktiven Kommunikation in die AEM Sites-Seite](/help/forms/using/embed-adaptive-form-aem-sites.md).

## Voraussetzungen {#prerequisites}

Um ein adaptives Formular oder eine interaktive Kommunikation in AEM Sites einzubetten, SPA die AEM Forms SPA Container-Komponente verwenden, stellen Sie sicher, dass Sie Folgendes installiert haben:

* Java SE Development Kit 8 oder höher
* Apache Maven 3.3.1 oder höher
* AEM Autoreninstanz
* [AEM Forms 6.4.2 Add-On-Paket ](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) auf der Autoreninstanz

## Installieren der AEM Forms SPA Container-Komponente {#install-aem-forms-spa-container-component}

Führen Sie die folgenden Schritte aus, um die AEM Forms SPA Container-Komponente zu installieren:

1. [Klonen oder laden Sie die AEM Forms-Komponente für SPA](https://github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa) herunter.
1. Installieren Sie die AEM Forms-Komponente für SPA. Die Anweisungen zum Installieren der Komponente finden Sie in der Datei [README.md](https://github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa#aem-form-component) .

   Die Komponente enthält eine [Beispiel-React-Komponente](https://github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa/react-component) , die verwendet werden kann, um SPA Container-Komponente in ein React-basiertes SPA-Projekt zu integrieren.

1. [Klonen oder laden Sie ein React-basiertes SPA-Projekt](https://github.com/adobe/aem-sample-we-retail-journal) herunter.
1. Integrieren Sie SPA Container-Komponente in ein React-basiertes SPA-Projekt mithilfe der Anweisungen in der Datei [README.md](https://github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa/react-component#aem-form-react-component-for-spa---editor) .

   Nachdem Sie die AEM Forms SPA Container-Komponente installiert und die Komponente in ein React-basiertes SPA-Projekt integriert haben, können Sie adaptive Formulare und interaktive Kommunikation in die AEM Sites-Seite einbetten.

## Einbetten eines adaptiven Formulars oder einer interaktiven Kommunikation {#af-component}

So betten Sie ein adaptives Formular oder eine interaktive Kommunikation mit AEM Forms für SPA Container-Komponente ein:

1. Öffnen Sie die Seite AEM Sites im Bearbeitungsmodus, in die Sie ein adaptives Formular oder interaktive Kommunikation einbetten möchten.
1. Fügen Sie die Komponente **AEM Formular für SPA** mit einer der folgenden Optionen auf der Seite ein:

   * Tippen Sie auf den Layout-Container auf der Seite &quot;Sites&quot;auf **+** und wählen Sie die Komponente **AEM Formular für SPA** aus.

   * Ziehen Sie die Komponente **AEM Formular für SPA** aus dem Komponenten-Browser auf die Seite.
   * Suchen Sie nach einem adaptiven Formular oder einer interaktiven Kommunikation im Assets-Browser und ziehen Sie es auf die Seite &quot;Sites&quot;. Es bettet das Formular in einen AEM Forms für SPA Komponentencontainer ein.

   >[!NOTE]
   >
   >Das Rendern mehrerer AEM Forms SPA Container-Komponenten auf einer Seite wird nicht unterstützt. Sie können mehrere AEM Forms SPA-Container auf einer Seite haben, es wird jedoch jeweils nur eine Komponente gerendert. Stellen Sie sicher, dass nur eine Komponente auf einer Seite sichtbar ist, um Diskrepanzen zu vermeiden.

1. Tippen Sie auf die eingebettete AEM Forms SPA Container-Komponente auf der Siteseite und dann auf ![settings_icon](assets/settings_icon.png) in der Aktionsleiste. Das Dialogfeld **AEM Forms SPA Container bearbeiten** wird geöffnet.
1. Geben Sie im Dialogfeld **AEM Forms-Container bearbeiten** Folgendes an:

   * **Asset-Typ:** Wählen Sie den Typ des einzubettenden Assets. Die Optionen sind **Adaptives Formular** und **Interaktive Kommunikation**

   * **Asset-Pfad**: Suchen Sie das einzubettende adaptive Formular oder die interaktive Kommunikation und wählen Sie es aus. Das Feld wird automatisch ausgefüllt, wenn ein adaptives Formular oder eine interaktive Kommunikation mithilfe des Assets-Browsers eingefügt wird.
   * **Kanal**  (nur interaktive Kommunikation): Wählen Sie den Typ des einzubettenden interaktiven Kanals aus. Die Optionen sind **Webkanal** und **Druckkanal**.

   * **Design**: Wählen Sie ein Design aus, das die Formatierung für Komponenten Ihres adaptiven Formulars oder der interaktiven Kommunikation definiert. Die Formatierung enthält Erscheinungsbildeigenschaften wie Schriftart, Hintergrundfarbe, Größe und Ausrichtung ein.

1. Tippen Sie auf ![done_icon](assets/done_icon.png) , um die Einstellungen zu speichern. Das adaptive Formular oder die interaktive Kommunikation ist jetzt in die Seite eingebettet.

## Veröffentlichen eingebetteter adaptiver Formulare und interaktiver Kommunikation {#publish-embedded-adaptive-form-and-interactive-communication}

Beachten Sie die folgenden Szenarien zum Veröffentlichen eines eingebetteten Assets (adaptives Formular oder interaktive Kommunikation) auf der AEM Sites-Seite:

* Wenn Sie die AEM Sites-Seite zum ersten Mal veröffentlichen und sie ein eingebettetes adaptives Formular oder eine interaktive Kommunikation enthält, veröffentlichen Sie die Sites-Seite und das eingebettete Asset.
* Wenn Sie nur das eingebettete adaptive Formular oder die interaktive Kommunikation auf einer veröffentlichten Sites-Seite geändert haben, veröffentlichen Sie das ursprüngliche Asset und die Änderungen werden auf der veröffentlichten Sites-Seite übernommen. Die veröffentlichte Sites-Seite enthält einen Verweis auf das Asset und erfordert keine erneute Veröffentlichung der Seite.
* Wenn Sie die Sites-Seite und das eingebettete adaptive Formular oder die interaktive Kommunikation geändert haben, veröffentlichen Sie die Sites-Seite und das eingebettete Asset erneut.

## Ändern des eingebetteten adaptiven Formulars und der interaktiven Kommunikation {#modify-embedded-adaptive-form-and-interactive-communication}

AEM Siteseite behält einen Verweis auf das adaptive Formular und die interaktive Kommunikation im AEM Forms-Container bei. Daher werden alle Konfigurationen und Eigenschaften wie das Design, die Stile und die Sendeaktion, die im ursprünglichen adaptiven Formular konfiguriert sind, sowie die interaktive Kommunikation im eingebetteten adaptiven Formular und in der interaktiven Kommunikation beibehalten.

Um eine Konfiguration oder Eigenschaft des eingebetteten adaptiven Formulars und der interaktiven Kommunikation zu ändern, führen Sie einen der folgenden Schritte aus.

* Öffnen Sie das Originalformular in adaptiven Formularen oder in der interaktiven Kommunikation in den entsprechenden Editoren und ändern Sie es.
* Tippen Sie im Bearbeitungsmodus auf das adaptive Formular oder die interaktive Kommunikation auf der Seite Sites und dann auf **In einem neuen Fenster bearbeiten**. Das ursprüngliche Formular wird im Bearbeitungsmodus geöffnet.

## Überlegungen und Best Practices {#considerations-and-best-practices}

Beachten Sie die folgenden Punkte, wenn Sie adaptive Formulare in AEM-Siteseiten einbetten:

* Die Kopf- und Fußzeile im Originalformular werden im eingebetteten Formular nicht übernommen.
* Benutzerentwürfe und Übermittlungen von eingebetteten Formularen werden unterstützt und sind auf der entsprechenden Registerkarte im Forms Portal sichtbar.
* Die im Originalformular konfigurierte Aktion wird im eingebetteten Formular beibehalten.
* Die im Originalformular konfigurierten Erlebnis-Targeting und A/B-Tests funktionieren im eingebetteten Formular nicht. Sie können jedoch Erlebnis-Targeting auf der Seite &quot;Sites&quot;verwenden, um basierend auf Benutzerprofilen verschiedene Formulare anzuzeigen.
* Wenn Sie Adobe Analytics für das Originalformular konfiguriert haben, werden die Analysedaten des eingebetteten Formulars in Adobe Analytics erfasst. Sie sind jedoch nicht im Formularanalysebericht verfügbar.
