---
title: Grundlegendes zur Segmentierung
seo-title: Understanding Segmentation
description: Die Segmentierung ist bei der Erstellung einer Kampagne eine grundlegende Überlegung. In den meisten Fällen müssen vor dem Start einer Kampagne bereits Segmente definiert sein.
seo-description: Segmentation is a key consideration when creating a campaign. In most cases, you will need to have segments already defined before starting your campaign.
uuid: 609d83b3-df0e-44ad-8e27-90b676d2666b
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: bb75f4ab-d983-45f6-98a3-da8bd9b63751
exl-id: 9092977b-b558-42a3-8092-4615fbc0a08e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '565'
ht-degree: 100%

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

**Besucherin/Besucher**: Eine Besucherin bzw. ein Besucher ist eine Person, die eine Website besucht. Der Besuch dieser Person beginnt in der Regel auf einer verweisenden Seite und geht dann über auf eine oder mehrere Seitenansichten auf Ihrer eigenen Website. Aus den Details des Besuchs dieser Person kann ein Verhaltensprofil erstellt werden.

**Benutzerin/Benutzer**: Eine Benutzerin bzw. ein Benutzer ist eine Besucherin oder ein Besucher, die/der sich bei der Website registriert, um ein Kontoprofil zu erhalten. Um ein Profil zu erstellen, geben Benutzer weitere Informationen zu ihrer Person an, z. B. eine E-Mail-Adresse oder ihr Geschlecht. Es können auch weitere Informationen erfasst werden, beispielsweise Aktivität in der Community und Kaufmuster. Basierend auf den in dem Profil angegebenen Informationen kann ein demografisches Profil erstellt werden.

**Eigenschaft**: Eine Eigenschaft ist ein Merkmal oder eine Charakteristik einer Besucherin oder eines Besuchers, das bzw. die verwendet werden kann, um die Zugehörigkeit zu einem bestimmten Segment zu bestimmen.

**Segment**: Ein Segment ist eine Sammlung von Besuchenden, die bestimmte Eigenschaften gemeinsam haben. Segmente sollten klar voneinander getrennt sein und so wenig Überlappung wie möglich mit anderen Segmenten aufweisen.

**Verhaltenseigenschaften**: Bei Verhaltenseigenschaften handelt es sich um die Eigenschaften, die sich auf das Verhalten einer Besucherin oder eines Besuchers auf einer Website beziehen. Dazu gehören:

* Interessensgebiete auf Ihrer Website, einschließlich besuchter Seiten und gekaufter Produkte.
* Interessensgebiete auf der verweisenden Website, einschließlich verwendeter Suchbegriffe oder Anzeigen, auf die geklickt wurde.
* Interessensgebiete auf anderen Sites, die durch Tools wie Spyjax ermittelt werden.
* Loyalität der Besucher, Dauer des Besuchs, Häufigkeit der Besuche.

**Demografische Eigenschaften**: Dabei handelt es sich um ausgewählte Merkmale der Population, darunter:

* Alter
* Einkommen
* Größe der Familie
* Familienstand
* Geschlecht
* Standort

**Abgeleitete Eigenschaften**  

Manche demografischen Eigenschaften können ohne Registrierung nur schwer ermittelt werden, können jedoch durch Kombination von verhaltensbezogenen und demografischen Eigenschaften abgeleitet werden.

Beispielsweise können Besitzer von Sites durch Kombination der verweisenden URL (als Verhaltenseigenschaft) mit demografischen Informationen (ermittelt mithilfe von Tools wie [Google Ad Planner](https://www.google.com/adplanner/)) demografische Eigenschaften ihrer Besucher ableiten.

**Untersegment**: Ein Segment kann in mehrere Untersegmente unterteilt werden. Dies geschieht über das Definieren weiterer Eigenschaften.

**Teaser-Seite**: Eine Teaser-Seite richtet sich an eine bestimmte Zielgruppe. Sie enthält wiederverwendbare Inhalte, die in dem Teaser-Absatz verwendet werden können.

**Kampagne**: Bei einer Kampagne handelt es sich um eine Sammlung von Teaser-Seiten und E-Mail-Marketing-Seiten, z. B. Newsletter oder Einladungen. Eine Kampagne läuft in der Regel für eine begrenzte Zeitdauer und wird dann von einer anderen Kampagne abgelöst.

**Teaser-Absatz**: Dies ist ein Absatz, der Inhalte in Abhängigkeit von einer Auswahlstrategie von einer anderen Seite abruft. Bei dieser Auswahlstrategie können Segmente und Kampagnen berücksichtigt werden.

**Liste**: Eine Liste wird aus einem Segment registrierter Benutzerinnen und Benutzer extrahiert. Beispielsweise der Ort, der verwendet wird, um die Inhalte des Teaser-Absatzes zu steuern.

>[!NOTE]
>
>Weitere Informationen zu Segmenten in AEM finden Sie unter [Segmentierung](/help/sites-administering/campaign-segmentation.md).
