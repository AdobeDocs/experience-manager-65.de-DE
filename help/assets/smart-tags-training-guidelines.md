---
title: Richtlinien für die intelligente Inhaltserstellung
description: AI-Dienst von Adobe Sensei schulen, um intelligente Tags auf Assets anzuwenden
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
contentOwner: AG
translation-type: tm+mt
source-git-commit: a39ee0f435dc43d2c2830b2947e91ffdcf11c7f6

---


# Smart Content Service training guidelines {#smart-content-service-training-guidelines}

Um Ihre Markenbilder effektiv mit Tags versehen zu können, erfordert der Smart Content Service, dass die Schulungsbilder bestimmten Richtlinien entsprechen.

## Richtlinien für das Training {#guidelines-for-training}

Für optimale Ergebnisse sollten Bilder im Trainingssatz folgende Richtlinien einhalten:

**** Menge und Größe: Mindestens 30 Bilder pro Tag Mindestens 500 Pixel an der längeren Seite.

**Kohärenz**: Bilder für ein Tag sollten visuell ähnlich sein.

So ist es beispielsweise nicht empfehlenswert, all diese Bilder mit dem Tag `my-party` zu versehen (zu Trainingszwecken), da sie einander visuell nicht ähnlich sind.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](/help/assets/assets/do-not-localize/coherence.png)

**Abdeckung:** Bei den Trainings-Bildern muss eine ausreichende Vielfalt vorhanden sein. Der Grundgedanke ist, einige Beispiele bereitzustellen, die jedoch verhältnismäßig vielfältig sind, sodass AEM lernt, sich auf die richtigen Dinge zu konzentrieren. Wenn Sie dasselbe Tag auf visuell unähnliche Bilder anwenden, schließen Sie mindestens fünf Beispiele für jeden Typ ein.

Beispiel: Schließen Sie für das Tag *model-down-pose* mehr Trainingsbilder ein, die dem hervorgehobenen Bild unten ähnlich sind, sodass der Dienst ähnliche Bilder beim Hinzufügen von Tags genauer identifizieren kann.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](/help/assets/assets/do-not-localize/coverage_1.png)

**Ablenkung/Verdeckung**: Der Dienst kann besser mit Bildern trainieren, die weniger Ablenkungen enthalten (hervorgehobenen Hintergründe oder Elemente ohne Bezug wie Objekte/Personen neben dem Hauptsubjekt).

Beispiel: Für das Tag *casual-shoe* ist das zweite Bild kein guter Kandidat für das Training.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](/help/assets/assets/do-not-localize/distraction.png)

**** Vollständigkeit: Wenn ein Bild für mehr als ein Tag qualifiziert ist, fügen Sie alle entsprechenden Tags hinzu, bevor Sie das Bild für eine Schulung einschließen. Beispiel: Fügen Sie im Falle von Tags wie `raincoat` und `model-side-view` beide Tags zum entsprechenden Asset hinzu, bevor Sie dieses für Trainingszwecke verwenden.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](/help/assets/assets/do-not-localize/completeness.png)

## Beschränkungen {#limitations}

Verbesserte Tags basieren auf Lernmodellen von Bildern und deren Tags. Diese Modelle können Tags nicht immer perfekt identifizieren. Bei der aktuellen Version des Smart Content Service gibt es folgende Einschränkungen:

* Subtile Unterschiede in Bildern können nicht erkannt werden. Zum Beispiel schlanke im Vergleich zu normal montierten Hemden.
* Tags können nicht anhand von winzigen Mustern/Teilen eines Bildes identifiziert werden. Beispiel: Logos auf T-Shirts.
* Tagging wird in den Sprachen unterstützt, in denen AEM unterstützt wird. Eine Liste der Sprachen finden Sie in den [Versionshinweisen für Smart Content Services](https://docs.adobe.com/content/help/en/experience-manager-64/release-notes/smart-content-service-release-notes.html).

Verwenden Sie zum Suchen nach Assets mit Smart-Tags (regulär oder erweitert) die Assets-Omniture-Suche (Volltextsuche). Es gibt kein separates Suchprädikat für Smart-Tags.

>[!NOTE]
>
>Die Fähigkeit des Smart Content Service, aus Ihren Tags zu lernen und diese Tags auf andere Bilder anzuwenden, hängt von der Qualität der für das Training verwendeten Bilder ab. Um die bestmöglichen Ergebnisse zu erzielen, empfiehlt Adobe die Verwendung visuell ähnlicher Bilder, um den Dienst für die einzelnen Tags zu trainieren.
