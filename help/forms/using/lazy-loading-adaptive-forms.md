---
title: Verbessern der Performance umfangreicher Formulare durch verzögertes Laden
seo-title: Improve performance of large forms with lazy loading
description: Verzögertes Laden verbessert die Leistung großer und komplexer adaptiver Formulare erheblich, indem die Initialisierung und das Laden von Formularfragmenten verzögert werden, bis sie sichtbar sind.
seo-description: Lazy loading significantly improves the performance of large and complex adaptive forms by deferring initialization and loading of form fragments until they are visible.
uuid: 6be3d2f0-1b2a-4090-af66-2b08487c31bc
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: a20736b7-f7b4-4da1-aa32-2408049b1209
docset: aem65
feature: Adaptive Forms
exl-id: f7e3e2cd-0cbe-4b26-9e55-7afc6dc3af63
source-git-commit: 1683338f02d01d5d9843368955fa42f309718f26
workflow-type: tm+mt
source-wordcount: '1034'
ht-degree: 50%

---

# Verbessern der Performance umfangreicher Formulare durch verzögertes Laden {#improve-performance-of-large-forms-with-lazy-loading}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/lazy-loading-adaptive-forms.html) |
| AEM 6.5 | Dieser Artikel |

## Einführung in das verzögerte Laden {#introduction-to-lazy-loading}

Wenn Formulare infolge von Hunderten oder Tausenden von Feldern groß und komplex werden, bemerken die Endbenutzer während des Renderns von Formularen zur Laufzeit lange Reaktionszeiten. Um die Reaktionszeit zu minimieren, können Sie mit adaptiven Formularen Formulare in logische Fragmente unterteilen und so konfigurieren, dass die Initialisierung oder das Laden von Fragmenten verzögert wird, bis das Fragment sichtbar sein muss. Dies wird als „verzögertes Laden“ bezeichnet. Darüber hinaus werden die für verzögertes Laden konfigurierten Fragmente entladen, sobald der Benutzer zu anderen Abschnitten im Formular navigiert und die Fragmente nicht mehr sichtbar sind.

Im Folgenden werden zunächst die Anforderungen und vorbereitenden Schritte vor dem Konfigurieren des verzögerten Ladens erklärt.

## Vorbereiten der Konfiguration von verzögertem Laden {#preparing-to-configure-lazy-loading}

Bevor Sie verzögertes Laden von Fragmenten in Ihrem adaptiven Formular konfigurieren, müssen Sie Strategien zum Erstellen von Fragmenten definieren, Werte identifizieren, die in Skripten verwendet oder in anderen Fragmenten referenziert werden, und Regeln definieren, um die Sichtbarkeit von Feldern in verzögert geladenen Fragmenten zu steuern.

* **Identifizieren und Erstellen von Fragmenten**
Sie können nur adaptive Formularfragmente für Lazy Loading (verzögertes Laden) konfigurieren. Ein Fragment ist ein unabhängiges Segment, das sich außerhalb eines adaptiven Formulars befindet und für mehrere Formulare wiederverwendet werden kann. Somit besteht der erste Schritt beim Implementieren des verzögerten Ladens in der Bestimmung der logischen Abschnitte in einem Formular und deren Konvertierung in Fragmente. Sie können ein Fragment von Grund auf neu erstellen oder einen vorhandenen Formularbereich als Fragment speichern.

   Weitere Informationen zum Erstellen von Fragmenten finden Sie unter [Adaptive Formularfragmente](../../forms/using/adaptive-form-fragments.md).

* **Identifizieren und Markieren globaler Werte**
Zu formularbasierten Transaktionen gehören dynamische Elemente, die relevante Daten von Benutzern erfassen und verarbeiten und dadurch das Ausfüllen des Formulars vereinfachen. Beispiel: Ihr Formular enthält Feld A in Fragment X, dessen Wert die Gültigkeit von Feld B in einem anderen Fragment bestimmt. Wenn in diesem Fall Fragment X für verzögertes Laden markiert ist, muss der Wert von Feld A verfügbar sein, um Feld B zu validieren, selbst wenn Fragment X nicht geladen wird. Um dies zu erreichen, können Sie Feld A als global markieren, wodurch sichergestellt wird, dass der zugehörige Wert für die Validierung von Feld B verfügbar ist, wenn Fragment X nicht geladen wird.

  Weitere Informationen dazu, wie Sie einen Feldwert als „global“ kennzeichnen, finden Sie unter [Konfigurieren von verzögertem Laden](../../forms/using/lazy-loading-adaptive-forms.md#p-configuring-lazy-loading-p).

* **Erstellen von Regeln zur Steuerung der Sichtbarkeit von Feldern**
Formulare enthalten Felder und Abschnitte, die nicht für alle Benutzer und Bedingungen gelten. Autoren und Entwickler von Forms verwenden Sichtbarkeits- oder Einblenden-Ausblendungsregeln, um ihre Sichtbarkeit anhand von Benutzereingaben zu steuern. Beispielsweise wird das Feld &quot;Office Address&quot;nicht den Benutzern angezeigt, die im Feld Beschäftigungsstatus in einem Formular die Option Arbeitslos auswählen. Weitere Informationen zum Erstellen von Regeln finden Sie unter [Verwenden des Regeleditors](../../forms/using/rule-editor.md).

  Sie können Sichtbarkeitsregeln in verzögert geladenen Fragmenten so einsetzen, dass bedingte Felder nur angezeigt werden, wenn sie benötigt werden. Markieren Sie außerdem das bedingte Feld als „global“, um im Ausdruck für die Sichtbarkeit des verzögert geladenen Fragments darauf zu verweisen.

## Konfigurieren von verzögertem Laden {#configuring-lazy-loading}

Führen Sie die folgenden Schritte aus, um verzögertes Laden in einem adaptiven Formularfragment zu aktivieren:

1. Öffnen Sie das adaptive Formular im Authoring-Modus, das das Fragment enthält, das Sie für verzögertes Laden aktivieren möchten.
1. Wählen Sie das adaptive Formularfragment aus und tippen Sie auf ![cmppr](assets/cmppr.png).
1. Aktivieren Sie in der Randleiste **[!UICONTROL Laden des Fragments träge]** und tippen Sie auf **Fertig**.

   ![Verzögertes Laden für das adaptive Formularfragment aktivieren](assets/lazy-loading-fragment.png)

   Das Fragment ist jetzt für verzögertes Laden aktiviert.

Sie können die Werte von Objekten im verzögert geladenen Fragment als global markieren, damit sie in Skripten verwendet werden können, wenn das übergeordnete Fragment nicht geladen wird. Gehen Sie folgendermaßen vor:

1. Öffnen Sie das adaptive Formularfragment im Bearbeitungsmodus.
1. Tippen Sie auf das Feld, dessen Wert Sie als „global“ markieren möchten, und tippen Sie dann auf ![cmppr](assets/cmppr.png).
1. Aktivieren Sie in der Randleiste **Wert bei verzögertem Laden verwenden**.

   ![Feld „Verzögertes Laden“ in der Randleiste](assets/enable-lazy-loading.png)

   Der Wert wird jetzt als global markiert und kann auch dann in Skripten verwendet werden, wenn das übergeordnete Fragment entladen wird.

## Aspekte und empfohlene Vorgehensweisen beim Konfigurieren von verzögertem Laden {#considerations-and-best-practices-for-configuring-lazy-loading}

Einige der folgenden Einschränkungen, Empfehlungen und wichtigen Aspekte sind beim Arbeiten mit verzögertem Laden zu beachten:

* Es wird empfohlen, XSD-schemabasierte adaptive Formulare anstelle von XFA-basierten adaptiven Formularen zu verwenden, um verzögertes Laden auf großen Formularen zu konfigurieren. Der Leistungsgewinn aufgrund der verzögerten Ladeimplementierung in XFA-basierten adaptiven Formularen ist in XSD-basierten adaptiven Formularen relativ geringer als der Gewinn.
* Konfigurieren Sie kein Lazy Loading (verzögertes Laden) für Fragmente in einem adaptiven Formular, die das Layout **[!UICONTROL Responsiv – alles auf einer Seite ohne Navigation]** für den Stammbereich verwenden. Infolge der Konfiguration „Responsive Layout“ werden in einem adaptiven Formular alle Fragmente gleichzeitig geladen. Dies kann ebenfalls die Performance beeinträchtigen.
* Es wird empfohlen, bei dem ersten Fragment in einem adaptiven Formular Lazy Loading nicht zu konfigurieren.
* Es wird empfohlen, verzögertes Laden nicht für Fragmente im ersten Bereich zu konfigurieren, der beim Laden des adaptiven Formulars gerendert wird.
* Verzögertes Laden wird für bis zu zwei Ebenen in der Fragmenthierarchie unterstützt.
* Stellen Sie sicher, dass Felder, die als global markiert sind, in einem adaptiven Formular eindeutig sind.
* Erwägen Sie, Sichtbarkeitsregeln für Fragmente zu erstellen, die basierend auf einer Bedingung ein- bzw. ausgeblendet werden sollen. Beispielsweise können Sie je nach dem vom Benutzer angegebenen Familienstand das Fragment zum Ehepartner ein- oder ausblenden.
* In verzögert geladenen Fragmenten werden keine Komponenten für Dateianhänge und Geschäftsbedingungen unterstützt.

### Empfohlene Vorgehensweisen für das Entwerfen von Skripten von verzögertem Laden {#scripting-best-practices-for-configuring-lazy-loading}

Weiterhin sollten Sie Folgendes beim Entwickeln von Skripten für das verzögerte Laden beachten:

* Stellen Sie sicher, dass die in den Feldern eines verzögert geladenen Fragments verwendeten Initialisierungs- und Berechnungsskripten idempotent sind. Idempotent-Skripte sind solche, die dieselbe Wirkung auch nach mehreren Ausführungen haben.
* Verwenden Sie die global verfügbare Eigenschaft von Feldern, um den Wert von Feldern in einem Bereich für verzögertes Laden für alle anderen Bereiche eines Formulars verfügbar zu machen.
* Weiterleiten Sie den Referenzwert eines Felds in einem verzögerten Bereich nicht weiter, unabhängig davon, ob das Feld global über Fragmente hinweg markiert ist oder nicht.
* Verwenden Sie die Funktion zum Zurücksetzen des Bedienfelds, um alle im Bedienfeld sichtbaren Elemente mithilfe des folgenden Klickausdrucks zurückzusetzen.\
  guideBridge.resolveNode(guideBridge.getFocus({&quot;focusOption&quot;: &quot;navigablePanel&quot;})).resetData()
