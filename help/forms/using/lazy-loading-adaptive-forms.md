---
title: Leistung großer Formulare mit verzögertem Laden verbessern
seo-title: Leistung großer Formulare mit verzögertem Laden verbessern
description: Verzögertes Laden verbessert die Leistung von großen und komplexen adaptiven Formularen erheblich, weil Formularfragmente erst initialisiert und geladen werden, wenn sie sichtbar sind.
seo-description: Verzögertes Laden verbessert die Leistung von großen und komplexen adaptiven Formularen erheblich, weil Formularfragmente erst initialisiert und geladen werden, wenn sie sichtbar sind.
uuid: 6be3d2f0-1b2a-4090-af66-2b08487c31bc
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: a20736b7-f7b4-4da1-aa32-2408049b1209
docset: aem65
feature: Adaptive Formulare
exl-id: f7e3e2cd-0cbe-4b26-9e55-7afc6dc3af63
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1045'
ht-degree: 81%

---

# Leistung großer Formulare mit verzögertem Laden verbessern{#improve-performance-of-large-forms-with-lazy-loading}

## Einführung in das verzögerte Laden {#introduction-to-lazy-loading}

Wenn Formulare durch Hunderte und Tausende von Feldern groß und komplex werden, erleben die Endbenutzer lange Reaktionszeiten während des Abspielens von Formularen zur Laufzeit. Um die Reaktionszeiten zu minimieren, können Sie adaptive Formulare in logische Fragmente unterteilen und konfigurieren, dass die Initialisierung oder das Laden von Fragmenten aufgeschoben wird, bis das Fragment sichtbar sein soll. Dies wird als „verzögertes Laden“ bezeichnet. Darüber hinaus werden die für verzögertes Laden konfigurierten Fragmente entladen, sobald der Benutzer zu anderen Abschnitten im Formular navigiert und die Fragmente nicht mehr sichtbar sind.

Im Folgenden werden zunächst die Anforderungen und vorbereitenden Schritte vor dem Konfigurieren des verzögerten Ladens erklärt.

## Vorbereiten der Konfiguration von verzögertem Laden {#preparing-to-configure-lazy-loading}

Bevor Sie verzögertes Laden von Fragmenten in Ihrem adaptiven Formular konfigurieren, müssen Sie Strategien entwickeln für das Erstellen von Fragmenten, Identifizieren von Werten, die in den Skripten verwendet oder in andere Fragment referenziert werden, und Definieren von Regeln, die die Sichtbarkeit von Feldern in verzögert geladenen Fragmenten steuern.

* **Identifizieren und Erstellen von**
FragmentenSie können nur adaptive Formularfragmente für verzögertes Laden konfigurieren. Ein Fragment ist ein eigenständiges Segment, das sich außerhalb eines adaptiven Formulars befindet und über mehrere Formulare hinweg wiederverwendet werden kann. Der erste Schritt zur Implementierung von verzögertem Laden besteht darin, logische Abschnitte in einem Formular zu identifizieren und sie in Fragmente zu konvertieren. Sie können ein Fragment von Grund auf neu erstellen oder ein vorhandenes Formularfeld als Fragment speichern.

    Weitere Informationen zum Erstellen von Fragmenten finden Sie unter [Adaptive Formularfragmente](../../forms/using/adaptive-form-fragments.md).

* **Identifizieren und Markieren globaler Werte** Zu formularbasierten Transaktionen gehören dynamische Elemente, um relevante Daten von Benutzern zu erfassen und zu verarbeiten und dadurch das Ausfüllen des Formulars zu vereinfachen. Beispiel: Ihr Formular enthält Feld A in Fragment X, dessen Wert die Gültigkeit von Feld B in einem anderen Fragment bestimmt. Wenn in diesem Fall Fragment X für verzögertes Laden markiert ist, muss der Wert von Feld A verfügbar sein, um Feld B zu validieren, selbst wenn Fragment X nicht geladen wird. Um dies zu erreichen, können Sie Feld A als „global“ markieren, wodurch gewährleistet wird, dass der entsprechende Wert für die Validierung von Feld B verfügbar ist, wenn Fragment X nicht geladen wird.

   Weitere Informationen dazu, wie Sie einen Feldwert als „global“ kennzeichnen, finden Sie unter [Konfigurieren von verzögertem Laden](../../forms/using/lazy-loading-adaptive-forms.md#p-configuring-lazy-loading-p).

* **Erstellen von Regeln, um die Sichtbarkeit von Feldern zu steuern** Formulare enthalten einige Felder und Abschnitte, die nicht für alle Benutzer und Bedingungen gelten. Formularersteller und Entwickler verwenden Regeln für Sichtbarkeit oder Einblenden/Ausblenden, um die Sichtbarkeit je nach Benutzereingabe zu steuern. Beispielsweise wird das Feld „Firmenanschrift“ Benutzern, die im Feld „Beschäftigungsstatus“ „Erwerbslos“ ausgewählt haben, nicht angezeigt. Weitere Informationen zum Erstellen von Regeln finden Sie unter [Verwenden des Regeleditors](../../forms/using/rule-editor.md).

   Sie können Sichtbarkeitsregeln in verzögert geladenen Fragmenten verwenden, sodass bedingte Felder nur angezeigt werden, wenn sie benötigt werden. Markieren Sie außerdem das bedingte Feld als „global“, um im Ausdruck für die Sichtbarkeit des verzögert geladenen Fragments darauf verweisen.

## Konfigurieren von verzögertem Laden  {#configuring-lazy-loading}

Führen Sie zum Aktivieren des verzögerten Ladens in einem adaptiven Formularfragment folgende Schritte durch:

1. Öffnen Sie im Bearbeitungsmodus das adaptive Formular, das das Fragment enthält, für das Sie verzögertes Laden aktivieren möchten.
1. Wählen Sie das adaptive Formularfragment aus und tippen Sie auf ![cmppr](assets/cmppr.png).
1. Aktivieren Sie in der Seitenleiste **[!UICONTROL Fragment verzögert laden]** und tippen Sie auf **Fertig**.

   ![Verzögertes Laden für das adaptive Formularfragment aktivieren](assets/lazy-loading-fragment.png)

   Das Fragment ist jetzt für verzögertes Laden aktiviert.

Sie können die Werte von Objekten im verzögert geladenen Fragment als „global“ markieren, sodass sie für die Verwendung in Skripten verfügbar sind, selbst wenn das enthaltende Fragment nicht geladen wird. Gehen Sie folgendermaßen vor:

1. Öffnen Sie das adaptive Formularfragment im Bearbeitungsmodus.
1. Tippen Sie auf das Feld, dessen Wert Sie als global markieren möchten, und dann auf ![cmppr](assets/cmppr.png).
1. Aktivieren Sie in der Randleiste **Wert bei verzögertem Laden verwenden**.

   ![Feld „Verzögertes Laden“ in der Randleiste](assets/enable-lazy-loading.png)

   Der Wert ist jetzt als „global“ markiert und ist für die Verwendung in Skripten verfügbar, selbst wenn das enthaltene Fragment entladen wird.

## Überlegungen und empfohlene Vorgehensweisen für das Konfigurieren von verzögertem Laden  {#considerations-and-best-practices-for-configuring-lazy-loading}

Einige der folgenden Einschränkungen, Empfehlungen und wichtigen Aspekte sind beim Arbeiten mit verzögertem Laden zu beachten:

* Es wird empfohlen, XSD-schemabasierte statt XFA-basierte adaptive Formulare für die Konfiguration von verzögertem Laden bei großen Formularen zu verwenden. Die Leistungsverbesserung aufgrund von verzögertem Laden ist in XFA-basierten adaptiven Formularen verhältnismäßiger geringer als in XSD-basierten adaptiven Formularen.
* Konfigurieren Sie kein verzögertes Laden auf Fragmenten in einem adaptiven Formular, das **[!UICONTROL Responsive -alles auf einer Seite ohne Navigation]** Layout für das Stammbedienfeld verwendet. Aufgrund der Konfiguration für responsives Layout werden alle Fragmente gleichzeitig in einem adaptiven Formular geladen. Dies kann auch zu einer Leistungsverschlechterung führen.
* Es wird empfohlen, das verzögerte Laden auf dem ersten Fragment in einem adaptiven Formular nicht zu konfigurieren.
* Es wird empfohlen, verzögertes Laden nicht in Fragmenten im ersten Bereich zu konfigurieren, das beim Laden des adaptiven Formulars angezeigt wird.
* Verzögertes Laden wird für bis zu zwei Ebenen in der Fragmenthierarchie unterstützt.
* Vergewissern Sie sich, dass als „global“ markierte Felder im gesamten adaptiven Formular eindeutig sind.
* Erwägen Sie, Sichtbarkeitsregeln für Fragmente zu erstellen, die basierend auf einer Bedingung ein- bzw. ausgeblendet werden sollen. Beispielsweise können Sie je nach dem vom Benutzer angegebenen Familienstand das Fragment zum Ehepartner ein- oder ausblenden.
* In verzögert geladenen Fragmenten werden keine Komponenten für Dateianlagen und Geschäftsbedingungen unterstützt.

### Empfohlene Vorgehensweisen für das Entwerfen von Skripten von verzögertem Laden  {#scripting-best-practices-for-configuring-lazy-loading}

Weiterhin sollten Sie Folgendes beim Entwickeln von Skripten für das verzögerte Laden beachten:

* Stellen Sie sicher, dass die initialisierten und berechneten Skripte, die in den Feldern des verzögert geladenen Fragments verwendet werden, idempotent sind. Idempotente Skripte sind diejenigen, die den gleichen Effekt auch nach mehreren Implementierungen haben.
* Verwenden Sie die global verfügbare Eigenschaft von Feldern, um den Wert der Felder, die sich in einem verzögert geladenen Bereich befinden, für alle anderen Bereiche eines Formulars verfügbar zu machen.
* Leiten Sie nicht den Referenzwert eines Feld innerhalb eines verzögert geladenen Bereichs weiter, egal ob das Feld als global in allen Fragmenten markiert ist oder nicht.
* Über die Funktion zum Zurücksetzen des Bereichs können Sie alle sichtbaren Elemente im Bereich zurückzusetzen, indem Sie den folgenden Ausdruck für ein Klickereignis verwenden.\
   guideBridge.resolveNode(guideBridge.getFocus({&quot;focusOption&quot;: &quot;navigablePanel&quot;})).resetData()
