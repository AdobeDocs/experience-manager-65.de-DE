---
title: Seitenvergleich
description: Die Seitenvergleichsfunktion ermöglicht einen bequemen Vergleich von zwei Seiten, indem sie nebeneinander angezeigt werden und die Unterschiede hervorgehoben sind.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
docset: aem65
exl-id: 3beea5cd-5ae0-485b-8dfc-8b3a23c11586
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: e2c1b6d3-bb7e-4fe8-8c72-f7b403298e91
    internal-label: Authoring
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 100%
---
# Seitenvergleich{#page-diff}

## Einführung {#introduction}

Die Inhaltserstellung ist ein iterativer Prozess. Damit ein Autor effizient arbeiten kann, muss er sehen können, was sich von Iteration zu Iteration verändert hat. Es ist ineffizient und bringt Fehler mit sich, wenn eine Seitenversion und danach die andere geprüft wird. Eine Autorin bzw. ein Autor möchte die aktuelle Seite einfach nebeneinander mit einer anderen Version vergleichen können.

Die Seitenvergleichsfunktion ermöglicht einen bequemen Vergleich von zwei Seiten, indem sie nebeneinander angezeigt werden und die Unterschiede hervorgehoben sind.

>[!TIP]
>
>Weitere Informationen zu dieser Funktion finden Sie unter [Entwicklung und Seitenvergleich](/help/sites-developing/pagediff.md#operation-details).

## Verwenden Sie {#use}

Folgendes kann verglichen werden:

* [Versionen](/help/sites-authoring/working-with-page-versions.md#comparing-a-version-with-current-page) – frühere Version einer Seite mit ihrem aktuellen Status
* [Live Copies](/help/sites-administering/msm-livecopy.md#comparing-a-live-copy-page-with-a-blueprint-page) – Live Copy mit ihrer Blueprint
* [Launches](/help/sites-authoring/launches-editing.md#comparing-a-launch-page-to-its-source-page) – Launch mit seiner Quelle
* [Sprachkopien](/help/sites-administering/tc-manage.md#comparing-language-copies) – eine Seite vor und nach der (erneuten) Übersetzung

Informieren Sie sich unter den entsprechenden Themen, wie der Seitenvergleich im gegebenen Zusammenhang verwendet wird.

### Darstellung von Unterschieden {#presentation-of-differences}

Unabhängig vom verglichenen Inhalt bleibt die Darstellung der Unterschiede dieselbe.

* Nachdem Sie den Seitenvergleich gestartet haben, wird der ausgewählte Inhalt auf der linken Seite angezeigt (der Differenzeinstiegspunkt).
* Rechts wird der zu vergleichende Inhalt angezeigt (der mit dem ausgewählten Inhalt verglichen wird).

Wenn Sie beispielsweise Versionen vergleichen, wird die aktuelle Version auf der linken Seite und die vorherige Version auf der rechten Seite angezeigt.

Die Quelle beider Seiten wird deutlich in der Kopfzeile am oberen Rand des Browser-Fensters angezeigt.

![Im Header angezeigte Quelle](assets/chlimage_1-109.png)

Der Vergleich erkennt Änderungen auf Komponenten- und HTML-Ebene. Geänderte Elemente werden mit unterschiedlichen Farben hervorgehoben.

**Komponentenänderungen**

* Hellgrün – Komponente hinzugefügt
* Rosa – Komponente entfernt

**HTML-Änderungen**

* Dunkelgrün – HTML hinzugefügt
* Rot – HTML entfernt

>[!NOTE]
>
>Beim Vergleich von Sprachkopien ist die Hervorhebung deaktiviert, da sich in einer Übersetzung alles ändert und Hervorhebung nutzlos wäre.

### Vollbild und Beenden {#fullscreen-and-exiting}

Damit Sie sich auf einen bestimmten Inhalt konzentrieren können, haben Sie die Möglichkeit, auf jeder Seite des Seitenvergleichs auf das Vollbildsymbol zu klicken, um die Ansicht auf das ganze Browser-Fenster zu vergrößern.

![Vollbildmodussymbol](do-not-localize/chlimage_1-18.png)

Die gewählte Seite füllt dann das gesamte Fenster aus, aber die Leiste am oberen Rand bleibt weiterhin sichtbar und bietet Ihnen die Möglichkeit, zwischen den zwei Seiten zu wechseln.

![Mit der oberen Leiste können Sie zwischen Seiten wechseln.](assets/chlimage_1-110.png)

Sie können die Vollbildansicht auch schließen, indem Sie auf das Symbol „Vollbildmodus beenden“ klicken.

![Vollbild schließen](do-not-localize/chlimage_1-19.png)

Sie können den Seitenvergleich jederzeit beenden, indem Sie in der Kopfzeile auf die Schaltfläche „Schließen“ klicken.

## Beschränkungen {#limitations}

Es gibt Situationen, in denen der Seitenvergleich möglicherweise Unterschiede nicht wie erwartet erkennt.

* Beim Vergleich von Versionen und Launches berücksichtigt der Seitenvergleich keine dynamischen Komponenten wie Breadcrumbs, Menüs, Produktlisten oder Logos (Komponenten, die die Site-Struktur zum Rendern ihres Inhalts nutzen).
* Bei Versionen erstellt der Vergleich die Richtlinien zur Zugriffssteuerung und die Live Copy-Beziehungen nicht neu.
* Wenn eine Seite verschoben wird, können Sie keinen Vergleich mehr mit Versionen durchführen, die vor dem Verschieben erstellt wurden.

  * Wenn Probleme beim Vergleich auftreten, überprüfen Sie in der [Timeline](/help/sites-authoring/basic-handling.md#timeline) der Seite, ob die Seite verschoben wurde.

>[!NOTE]
>
>Versionen können nicht miteinander verglichen werden. Nur die aktuelle Version kann mit anderen Versionen der Seite verglichen werden. Die aktuelle Version ist immer die Version, deren Änderungen hervorgehoben sind.

>[!NOTE]
>
>Weitere Informationen zum Ablauf des Seitenvergleichsmechanismus sowie Einschränkungen, die sich auf den Seitenvergleich auswirken können, finden Sie in der [Entwickler-Dokumentation](/help/sites-developing/pagediff.md) zu dieser Funktion.
