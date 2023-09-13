---
title: Einführung in die mehrteilige Formularsequenz
description: Mit AEM Forms können Sie eine Abfolge von Formularbereichen definieren, in denen Benutzer in adaptiven Formularen navigieren und diese ausfüllen sollen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
feature: Adaptive Forms
exl-id: 1333c6cb-15cc-429b-a13e-5d23afdee69a
source-git-commit: 474a726058b141985f52a0faec6161a34be1e9dc
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 34%

---

# Einführung in die mehrteilige Formularsequenz{#introduction-to-multi-step-form-sequence}

<span class="preview"> Adobe empfiehlt die Verwendung der modernen und erweiterbaren Datenerfassung [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) für [Erstellen neuer adaptiver Forms](/help/forms/using/create-an-adaptive-form-core-components.md) oder [Hinzufügen von Adaptive Forms zu AEM Sites-Seiten](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Forms dar und sorgen für beeindruckende Benutzererlebnisse. In diesem Artikel wird ein älterer Ansatz zum Erstellen von Adaptive Forms mithilfe von Foundation-Komponenten beschrieben. </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-layout-of-an-adaptive-form/introduction-form-sequence.html) |
| AEM 6.5 | Dieser Artikel |


Mit adaptiven Formularen können Formularautoren eine mehrstufige Datenerfassungserfahrung auf einfache Weise erstellen. Es bietet integrierte Unterstützung für das Erstellen mehrerer Bedienfelder und das Verknüpfen jedes Bedienfelds mit verschiedenen Navigationsmustern. Formularverfasser können Formularfelder in logischen Abschnitten gruppieren und eine Gruppe als Bedienfeld darstellen. Die gesamte Navigation zwischen den Bedienfeldern wird mithilfe des Bedienfeldlayouts gesteuert. Autoren können die Bedienfelder in unterschiedlichen Layouts anordnen, beispielsweise nacheinander mithilfe des Assistentenlayouts, oder ad hoc mithilfe des Registerkartenlayouts. Weitere Informationen zu Bereichslayouts finden Sie unter [Layout-Funktionen adaptiver Formulare](../../forms/using/layout-capabilities-adaptive-forms.md).

In der Regel sind mehr Schritte erforderlich als nur die Erfassung von Daten. Eine vollständige Formularübermittlung kann andere Schritte umfassen, z. B. das digitale Signieren des Formulars, die Überprüfung der im Formular eingegebenen Informationen und die Verarbeitung von Zahlungen. Sie unterscheidet sich von Fall zu Fall.

Wenn Ihr Anwendungsfall eine Reihe von Schritten zur Datenerfassung erfordert oder bestimmte Vorschriften befolgt werden müssen, bietet AEM Forms eine Möglichkeit, diese gemeinsame Struktur formularübergreifend durchzusetzen. Die vorab implementierte Implementierung einer Formularstruktur definiert die Abfolge von Schritten für ein Formular. ![Beispiel für eine mehrstufige Formularsequenz](assets/formpipeline.png)

Beispiel für eine mehrstufige Formularsequenz

Nehmen wir ein Anwendungsbeispiel, in dem Sie eine Sequenz für das Ausfüllen, Überprüfen, Signieren und Bestätigen eines Formulars erstellen müssen. Gehen Sie zur Erstellung einer solchen Sequenz wie folgt vor:

1. Definieren Sie eine Formularvorlage und fügen Sie ihr den erforderlichen Bereich hinzu. Für jeden Schritt der Sequenz sollte ein Bedienfeld vorhanden sein. Sie können jedoch Unterbedienfelder in ein Bedienfeld einfügen.

   In diesem Beispiel können die folgenden Bedienfelder hinzugefügt werden:

   * **Füllung**: Enthält Formularfelder zum Erfassen von Daten. Hier können Sie verschachtelte untergeordnete Bedienfelder einfügen, um Abschnitte für verschiedene Arten von Informationen wie persönliche, familiäre und finanzielle Informationen zu erstellen.

   * **Verify**: Enthält die Komponente **Verify**, die in einem XFA-basierten adaptiven Formular verwendet werden kann. Es werden die Informationen angezeigt, die im Bedienfeld „Fill“ im schreibgeschützten Modus zur Überprüfung erfasst werden.

   * **E-sign**: Enthält die Komponente **Sign**, die in einem XFA-basierten adaptiven Formular verwendet werden kann. Es stellt die folgenden Signaturdienste bereit:

      * Adobe Document Cloud eSignature-Services
      * Freihändige Unterschrift

   * **Bestätigung**: Enthält die Komponente **Zusammenfassung**, in der die Übermittlung in einer Meldung bestätigt wird, nachdem der Benutzer das Formular signiert hat und in der Sequenz den Bestätigungsschritt (Zusammenfassung) erreicht hat. Autoren können den Text der Komponente Zusammenfassung konfigurieren, eine Dankesmeldung oder einen Link zur erstellten PDF-Datei anzeigen usw.

1. Wählen Sie für das Layout des Stammbedienfelds **[!UICONTROL Assistent]** aus.
1. Führen Sie die restlichen Schritte aus, damit Sie die Formularvorlage erstellen können. Siehe [Erstellen einer benutzerdefinierten adaptiven Formularvorlage](../../forms/using/custom-adaptive-forms-templates.md).

Nachdem Sie die Formularsequenz in der Formularvorlage definiert haben, können Sie sie verwenden, um Formulare mit der Basisstruktur zu erstellen, die als Sequenz definiert ist. Sie können das Formular jederzeit an Ihre Anforderungen anpassen.
