---
title: Einführung in die mehrteilige Formularsequenz
seo-title: Introduction to multi-step form sequence
description: Mit AEM Forms können Sie eine Abfolge von Formularfeldern definieren, in denen Benutzer in adaptiven Formularen navigieren und diese ausfüllen sollen.
seo-description: With AEM Forms, you can define a sequence of form panel in which you want users to navigate and fill an adaptive form.
uuid: db1aac25-fe69-4e43-88d1-4a15389b507f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 0f335ea0-504f-4cc0-b97b-c3fc715bcc2e
docset: aem65
feature: Adaptive Forms
exl-id: 1333c6cb-15cc-429b-a13e-5d23afdee69a
source-git-commit: 1683338f02d01d5d9843368955fa42f309718f26
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 50%

---

# Einführung in die mehrteilige Formularsequenz{#introduction-to-multi-step-form-sequence}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-layout-of-an-adaptive-form/introduction-form-sequence.html) |
| AEM 6.5 | Dieser Artikel |


Adaptive Formulare ermöglichen es Formularautoren, eine mehrstufige Datenerfassungserfahrung auf einfache Weise zu erstellen. Es bietet integrierte Unterstützung für das Erstellen mehrerer Bedienfelder und das Verknüpfen jedes Bedienfelds mit verschiedenen Navigationsmustern. Formularverfasser können Formularfelder in logischen Abschnitten gruppieren und eine Gruppe als Bedienfeld darstellen. Die gesamte Navigation zwischen den Bedienfeldern wird mithilfe des Bedienfeldlayouts gesteuert. Autoren können die Bedienfelder in unterschiedlichen Layouts anordnen, beispielsweise nacheinander mithilfe des Assistentenlayouts, oder ad hoc mithilfe des Registerkartenlayouts. Weitere Informationen zu Bereichslayouts finden Sie unter [Layout-Funktionen adaptiver Formulare](../../forms/using/layout-capabilities-adaptive-forms.md).

In einer typischen Form beim Ausfüllen sind mehr Schritte erforderlich als nur das Erfassen von Daten. Eine vollständige Formularübermittlung kann andere Schritte umfassen, z. B. das digitale Signieren des Formulars, das Überprüfen der im Formular eingegebenen Informationen, das Verarbeiten von Zahlungen usw. Sie unterscheidet sich von Fall zu Fall.

Wenn Ihr Anwendungsfall eine Reihe von Schritten zur Datenerfassung erfordert oder bestimmte Vorschriften befolgt werden müssen, bietet AEM Forms eine Möglichkeit, diese gemeinsame Struktur formularübergreifend durchzusetzen. Mit der Implementierung der vorher festgelegten Formularstruktur wird die Sequenz für ein Formular definiert. ![Beispiel für eine mehrstufige Formularsequenz](assets/formpipeline.png)

Beispiel für eine mehrstufige Formularsequenz

Nehmen wir ein Anwendungsbeispiel, in dem Sie eine Sequenz für das Ausfüllen, Überprüfen, Signieren und Bestätigen eines Formulars erstellen müssen. Die Schritte zum Erstellen einer solchen Sequenz lauten wie folgt:

1. Definieren Sie eine Formularvorlage und fügen Sie ihr den erforderlichen Bereich hinzu. Beachten Sie, dass für jeden Schritt in der Sequenz ein Bedienfeld vorhanden sein sollte. Sie können jedoch Unterbedienfelder in ein Bedienfeld einfügen.

   In diesem Beispiel können wir die folgenden Bedienfelder hinzufügen:

   * **Füllung**: Sie enthält Formularfelder zur Datenerfassung. Hier können Sie verschachtelte untergeordnete Bedienfelder einfügen, um Abschnitte für verschiedene Arten von Informationen zu erstellen, z. B. persönlicher, familiärer, finanzieller Art usw.

   * **Verify**: Enthält die Komponente **Verify**, die in einem XFA-basierten adaptiven Formular verwendet werden kann. Es werden die Informationen angezeigt, die im Bedienfeld „Fill“ im schreibgeschützten Modus zur Überprüfung erfasst werden.

   * **E-sign**: Enthält die Komponente **Sign**, die in einem XFA-basierten adaptiven Formular verwendet werden kann. Es stellt die folgenden Signaturdienste bereit:

      * Adobe Document Cloud eSignature-Services
      * Freihändige Unterschrift

   * **Bestätigung**: Enthält die Komponente **Zusammenfassung**, in der die Übermittlung in einer Meldung bestätigt wird, nachdem der Benutzer das Formular signiert hat und in der Sequenz den Bestätigungsschritt (Zusammenfassung) erreicht hat. Autoren können den Text der Komponente Zusammenfassung konfigurieren, eine Dankesmeldung oder einen Link zur erstellten PDF-Datei anzeigen usw.

1. Wählen Sie für das Layout des Stammbedienfelds **[!UICONTROL Assistent]** aus.
1. Führen Sie die restlichen Schritte aus, um die Formularvorlage zu erstellen. Weitere Informationen finden Sie unter [Erstellen einer benutzerdefinierten adaptiven Formularvorlage](../../forms/using/custom-adaptive-forms-templates.md).

Nachdem Sie die Formularsequenz in der Formularvorlage definiert haben, können Sie sie zum Erstellen von Formularen verwenden, deren Grundstruktur der gegenwärtig definierten Sequenz entspricht. Sie haben jedoch immer die Möglichkeit, das Formular Ihren Bedürfnissen anzupassen.
