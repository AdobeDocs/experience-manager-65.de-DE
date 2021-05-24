---
title: Grundlegendes zur Segmentierung
seo-title: Grundlegendes zur Segmentierung
description: Die Segmentierung ist bei der Erstellung einer Kampagne eine grundlegende Überlegung
seo-description: Die Segmentierung ist bei der Erstellung einer Kampagne eine grundlegende Überlegung
uuid: 900da068-5dda-4b6b-8be3-4b7ad614126d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
discoiquuid: 36c87684-e62a-4983-b123-87f56dbf7bc5
exl-id: 61a5875f-ad09-4971-a886-b0d88e0c9967
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 68%

---

# Grundlegendes zur Segmentierung{#understanding-segmentation}

Die Segmentierung ist bei der Erstellung einer Kampagne eine grundlegende Überlegung. In den meisten Fällen müssen vor dem Start einer Kampagne bereits Segmente definiert sein.

Besucher von Websites haben unterschiedliche Interessen und Ziele, wenn sie eine Site besuchen. Das Verstehen dieser Ziele und das Erfüllen der Erwartungen sind wichtige Erfolgsfaktoren beim Onlinemarketing.

Dies können Sie mithilfe der Segmentierung erreichen, indem Sie die folgenden Faktoren eines Besuchers analysieren und charakterisieren:

* Aktivität auf der Website
* Profil
* Aktivität auf anderen Websites

Inhalte können dann entsprechend den zutreffenden Segmenten speziell auf die Anforderungen und Interessen des Besuchers abgestimmt werden.

## Verwenden von Segmentierung {#using-segmentation}

Segmente werden unter [Konfigurieren von Segmentierung](/help/sites-administering/campaign-segmentation.md) definiert. Sie werden dazu verwendet, den tatsächlich für Zielgruppen sichtbaren Inhalt zu steuern.

## Segmentierungsterminologie {#segmentation-terminology}

Im Rahmen der Segmentierung wird die folgende Terminologie verwendet:

**** BesucherEin Besucher ist eine Person, die eine Website besucht. Der Besuch dieser Person beginnt in der Regel auf einer verweisenden Seite und geht dann über auf eine oder mehrere Seitenansichten auf Ihrer eigenen Website. Aus den Details des Besuchs dieser Person kann ein Verhaltensprofil erstellt werden.

**** BenutzerEin Benutzer ist ein Besucher, der sich bei der Website registriert, um ein Kontoprofil zu erhalten. Um ein Profil zu erstellen, geben Benutzer weitere Informationen zu ihrer Person an, z. B. eine E-Mail-Adresse oder ihr Geschlecht. Es können auch weitere Informationen erfasst werden, beispielsweise Aktivität in der Community und Kaufmuster. Basierend auf den in dem Profil angegebenen Informationen kann ein demografisches Profil erstellt werden.

**** EigenschaftEine Eigenschaft ist ein Merkmal oder eine Eigenschaft eines Besuchers, das bzw. die verwendet werden kann, um die Zugehörigkeit zu einem bestimmten Segment zu bestimmen.

**** SegmentEin Segment ist eine Sammlung von Besuchern, die bestimmte Eigenschaften teilen. Segmente sollten klar voneinander getrennt sein und so wenig Überlappung wie möglich mit anderen Segmenten aufweisen.

**Verhaltenseigenschaften** sind diejenigen, die sich auf das Verhalten eines Besuchers auf der Website beziehen. Dazu gehören:

* Interessensgebiete auf Ihrer Website, einschließlich besuchter Seiten und gekaufter Produkte.
* Interessensgebiete auf der verweisenden Website, einschließlich verwendeter Suchbegriffe oder Anzeigen, auf die geklickt wurde.
* Interessensgebiete auf anderen Sites, die durch Tools wie Spyjax ermittelt werden.
* Loyalität der Besucher, Dauer des Besuchs, Häufigkeit der Besuche.

**Demografische** EigenschaftenHierbei handelt es sich um ausgewählte Populationsmerkmale, darunter:

* Alter
* Einkommen
* Größe der Familie
* Familienstand
* Geschlecht
* Standort

**Abgeleitete** EigenschaftenEinige demografische Eigenschaften lassen sich ohne Registrierung nur schwer ermitteln, können aber durch Kombination von verhaltensbezogenen und demografischen Eigenschaften abgeleitet werden.

Beispielsweise können Besitzer von Sites durch Kombination der verweisenden URL (als Verhaltenseigenschaft) mit demografischen Informationen (ermittelt mithilfe von Tools wie [Google Ad Planner](https://www.google.com/adplanner/)) demografische Eigenschaften ihrer Besucher ableiten.

**** UntersegmentEin Segment kann in mehrere Untersegmente unterteilt werden. Dies geschieht über das Definieren weiterer Eigenschaften.

**Teaser-** SeiteEine Teaser-Seite richtet sich an eine bestimmte Zielgruppe. Sie enthält wiederverwendbare Inhalte, die in dem Teaser-Absatz verwendet werden können.

**** KampagneEine Kampagne ist eine Sammlung von Teaser-Seiten und E-Mail-Marketing-Seiten, z. B. Newsletter oder Einladungen. Eine Kampagne läuft in der Regel für eine begrenzte Zeitdauer und wird dann von einer anderen Kampagne abgelöst.

**Teaser** ParagraphDies ist ein Absatz, der Inhalte von einer anderen Seite abhängig von einer Auswahlstrategie abruft. Bei dieser Auswahlstrategie können Segmente und Kampagnen berücksichtigt werden.

**** ListeEine Liste wird aus einem Segment registrierter Benutzer extrahiert. Beispielsweise der Ort, der verwendet wird, um die Inhalte des Teaser-Absatzes zu steuern.

>[!NOTE]
>
>Weitere Informationen zu Segmenten in AEM finden Sie unter [Segmentierung](/help/sites-administering/campaign-segmentation.md) .
