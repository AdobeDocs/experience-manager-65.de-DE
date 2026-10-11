---
title: Erstellen zugänglicher komplexer Tabellen in HTML5-Formularen
description: Erfahren Sie, wie Sie barrierefreie Tabellen in HTML5-Formularen erstellen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 3504afe1-abf5-4fbf-a0d2-e093361764bd
feature: HTML5 Forms,Mobile Forms
exl-id: 3b8e3323-9ac4-4f5c-8c52-e2186e9169ea
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 97aafc4b-2598-52d6-9012-295a95969e38
    internal-label: HTML5 Forms
  - id: 59f95943-e802-56ac-990d-21ab923984c1
    internal-label: Mobile Forms
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 100%
---
# Zugreifbare komplexe Tabellen in HTML5-Formularen erstellen {#create-accessible-complex-tables-in-html-forms}

Die Standardimplementierung von Tabellen in den HTML5-Formularen verwendet HTML DIV-Elemente, um eine neue Tabelle zu rendern. Das Rendern involviert die Verwendung von ARIA-Rollen, um den Anforderungen für den barrierefreien Zugriff gerecht zu werden.

Um Probleme mit der Barrierefreiheit mit Bildschirmsprachausgaben zu vermeiden, die ARIA-Rollen nicht voll unterstützen, die mit Datentabellen verwendet werden, bieten HTML5-Formulare eine alternative Darstellung für die Tabellen. Diese Tabellen basieren auf dem neuen Tabellenformat, das in Designer eingeführt wurde und das ebenfalls Folgendes unterstützt:

* Zeilen-Header
* Zeilenabschnitt

Um das neue Format in HTML5 Forms zu verwenden, markieren Sie die Tabelle als komplex. Um die Tabelle als komplex zu markieren, fügen Sie den `extras`-Tag in die XML-Quelle des Tabellenteilformulars wie folgt hinzu:

```xml
</extras>
 <text name="complexTable">1</text>
 </extras>
```

Die Tabellen, die als *complexTable* markiert werden, folgen der nativen HTML-Darstellung und bieten eine bessere Barrierefreiheit für bestimmte Bildschirmsprachausgaben.  Um einen Zeilenabschnitt zu erstellen, wählen Sie mehrere Zellen einer Tabelle in derselben Spalte, klicken Sie mit der rechten Maustaste auf die Auswahl und klicken Sie dann auf **[!UICONTROL Zellen zusammenführen]**.

>[!NOTE]
>
>Das Erstellen eines Zeilenabschnitts funktioniert nur für die am weitesten links liegenden Zellen.

Um eine Zeile als Zeilenüberschrift zu markieren, wählen Sie alle Zellen in der Zeile aus, klicken Sie mit der rechten Maustaste auf die Auswahl und klicken Sie dann auf **[!UICONTROL Kopfzeile markieren]**.

Um eine Zelle als Spaltenüberschrift zu markieren, wählen Sie eine beliebige Zelle in der Spalte aus, klicken Sie mit der rechten Maustaste auf die Auswahl und klicken Sie dann auf **[!UICONTROL Kopfzeile markieren]**.

Einschränkungen im neuen *AccessibleTable*-Format:

* Fehlende Unterstützung für vergrößerungsfähige Felder, wenn ein Zeilenabschnitt in der Tabelle verwendet wird
* Keine Unterstützung für verschachtelte Tabellen (Tabellen in Tabellenzellen)
* Unterstützung für Zeilenabschnitte ist auf die Kopfzeilen und Kopfzellen beschränkt
* Unterstützung ist auf reguläre Tabellen beschränkt
* Keine Unterstützung für Datenvorfüllungen in Tabellen mit Zeilenabschnitt > 1
