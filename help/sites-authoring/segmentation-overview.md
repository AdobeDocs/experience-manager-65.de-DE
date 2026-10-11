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
role: User,Admin,Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: e2c1b6d3-bb7e-4fe8-8c72-f7b403298e91
    internal-label: Authoring
  - id: eb3ad9f8-54a2-45f3-abb1-d3976415a718
    internal-label: Personalization
  - id: 243139ec-8e41-5296-a287-31343ab1bc0f
    internal-label: Integration
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '549'
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
* Treue der Besucherinnen und Besucher, Dauer des Besuchs, Häufigkeit der Besuche.

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
