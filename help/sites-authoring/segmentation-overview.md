---
title: Grundlegendes zur Segmentierung bei der Erstellung einer Kampagne
description: Die Segmentierung ist ein wichtiger Faktor, der bei der Erstellung einer Kampagne berücksichtigt werden muss.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
exl-id: 61a5875f-ad09-4971-a886-b0d88e0c9967
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Personalization,Integration
role: User,Admin,Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 100%

---

# Grundlegendes zur Segmentierung{#understanding-segmentation}

Die Segmentierung ist bei der Erstellung einer Kampagne eine grundlegende Überlegung. Normalerweise müssen vor dem Start einer Kampagne bereits Segmente definiert sein.

Besucher von Websites haben unterschiedliche Interessen und Ziele, wenn sie eine Site besuchen. Diese Ziele zu verstehen und die Erwartungen zu erfüllen, ist ein wichtiger Erfolgsfaktor für das Online-Marketing.

Dies können Sie mithilfe der Segmentierung erreichen, indem Sie die folgenden Faktoren einer Besucherin oder eines Besuchers analysieren und charakterisieren:

* Aktivität auf der Website
* Profil
* Aktivität auf anderen Websites

Inhalte können dann entsprechend den jeweiligen Segmenten auf die Anforderungen und Interessen der Besucherinnen und Besucher ausgerichtet werden.

## Verwenden von Segmentierung {#using-segmentation}

Segmente werden unter [Konfigurieren einer Segmentierung](/help/sites-administering/campaign-segmentation.md) definiert. Sie werden dazu verwendet, den tatsächlich für Zielgruppen sichtbaren Inhalt zu steuern.

## Segmentierungsterminologie {#segmentation-terminology}

Im Rahmen der Segmentierung wird die folgende Terminologie verwendet:

**Besucher**: Ein Besucher ist eine Person, die eine Website besucht. Der Besuch dieser Person beginnt in der Regel auf einer verweisenden Seite und geht dann über auf eine oder mehrere Seitenansichten auf Ihrer eigenen Website. Aus den Details des Besuchs dieser Person kann ein Verhaltensprofil erstellt werden.

**Benutzer**: Ein Benutzer ist ein Besucher, der sich bei der Website registriert, um ein Kontoprofil zu erhalten. Um ein Profil zu erstellen, geben Benutzende weitere Informationen zu ihrer Person an, z. B. eine E-Mail-Adresse oder ihr Geschlecht. Es können auch weitere Informationen erfasst werden, beispielsweise Aktivitäten in der Community und Kaufmuster. Basierend auf den in dem Profil angegebenen Informationen kann ein demografisches Profil erstellt werden.

**Eigenschaft**: Eine Eigenschaft ist ein Merkmal oder eine Charakteristik eines Besuchers, das bzw. die verwendet werden kann, um die Zugehörigkeit zu einem bestimmten Segment zu bestimmen.

**Segment**: Ein Segment ist eine Sammlung von Besuchern, die bestimmte Eigenschaften teilen. Segmente sollten klar voneinander getrennt sein und so wenig Überlappung wie möglich mit anderen Segmenten aufweisen.

**Verhaltenseigenschaften**: Bei Verhaltenseigenschaften handelt es sich um diejenigen Eigenschaften, die sich auf das Verhalten eines Besuchers auf einer Website beziehen. Dazu gehören:

* Interessensgebiete auf Ihrer Website, einschließlich besuchter Seiten und gekaufter Produkte.
* Interessensgebiete auf der verweisenden Website, einschließlich verwendeter Suchbegriffe oder Anzeigen, auf die geklickt wurde.
* Interessensgebiete auf anderen Sites, die durch Tools wie Spyjax ermittelt werden.
* Loyalität der Besucherinnen und Besucher, Dauer des Besuchs, Häufigkeit der Besuche.

**Demografische Eigenschaften**: Dabei handelt es sich um ausgewählte Merkmale der Population, darunter:

* Alter
* Einkommen
* Größe der Familie
* Familienstand
* Geschlecht
* Standort

**Abgeleitete Merkmale**: Manche demografischen Eigenschaften können ohne Registrierung nur schwer ermittelt werden, lassen sich jedoch durch Kombination von verhaltensbezogenen und demografischen Eigenschaften ableiten.

Beispielsweise können Site-Verantwortliche durch Kombination der verweisenden URL (als Verhaltensmerkmal) mit demografischen Informationen (ermittelt mithilfe von Tools wie [Google Ad Planner](https://www.google.com/adplanner/)) demografische Eigenschaften ihrer Besuchenden ableiten.

**Untersegment**: Ein Segment kann in mehrere Untersegmente unterteilt werden. Dies geschieht über das Definieren weiterer Eigenschaften.

**Teaser-Seite**: Eine Teaser-Seite richtet sich an eine bestimmte Zielgruppe. Sie enthält wiederverwendbare Inhalte, die in dem Teaser-Absatz verwendet werden können.

**Kampagne**: Bei einer Kampagne handelt es sich um eine Sammlung von Teaser-Seiten und E-Mail-Marketing-Seiten, z. B. Newsletter oder Einladungen. Eine Kampagne läuft in der Regel für eine begrenzte Zeitdauer und wird dann von einer anderen Kampagne abgelöst.

**Teaser-Absatz**: Dies ist ein Absatz, der Inhalte in Abhängigkeit von einer Auswahlstrategie von einer anderen Seite abruft. Bei dieser Auswahlstrategie können Segmente und Kampagnen berücksichtigt werden.

**Liste**: Eine Liste wird aus einem Segment registrierter Benutzer extrahiert. Beispielsweise der Ort, der verwendet wird, um die Inhalte des Teaser-Absatzes zu steuern.

>[!NOTE]
>
>Weitere Informationen zu Segmenten in Adobe Experience Manager finden Sie unter [Segmentierung](/help/sites-administering/campaign-segmentation.md).
