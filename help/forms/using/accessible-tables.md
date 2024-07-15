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
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 100%

---

# Zugreifbare komplexe Tabellen in HTML5-Formularen erstellen {#create-accessible-complex-tables-in-html-forms}

Die Standardimplementierung von Tabellen in den HTML5-Formularen verwendet HTML DIV-Elemente, um eine neue Tabelle zu rendern. Das Rendern involviert die Verwendung von ARIA-Rollen, um den Anforderungen für den barrierefreien Zugriff gerecht zu werden.

Um Probleme mit der Barrierefreiheit mit Bildschirmsprachausgaben zu vermeiden, die ARIA-Rollen nicht voll unterstützen, die mit Datentabellen verwendet werden, bieten HTML5-Formulare eine alternative Darstellung für die Tabellen. Diese Tabellen basieren auf dem neuen Tabellenformat, das in Designer eingeführt wurde und das ebenfalls Folgendes unterstützt:

* Zeilenkopf
* Zeilenabschnitt

Um das neue Format in HTML5 Forms zu verwenden, markieren Sie die Tabelle als komplex. Um die Tabelle als komplex zu markieren, fügen Sie den `extras`-Tag in die XML-Quelle des Tabellenteilformulars wie folgt hinzu: 

```xml
</extras>
 <text name="complexTable">1</text>
 </extras>
```

Die Tabellen, die als *complexTable* markiert werden, folgen der nativen HTML-Darstellung und bieten eine bessere Barrierefreiheit für bestimmte Bildschirmsprachausgaben.  Um einen Zeilenabschnitt zu erstellen, wählen Sie mehrere Zellen einer Tabelle in derselben Spalte, klicken Sie mit der rechten Maustaste auf die Auswahl und klicken Sie dann auf **[!UICONTROL Zellen verbinden]**.

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
