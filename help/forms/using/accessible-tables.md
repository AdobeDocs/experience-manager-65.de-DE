---
title: Zugreifbare komplexe Tabellen in HTML5-Formularen erstellen
seo-title: Create accessible complex tables in HTML5 forms
description: Erfahren Sie, wie Sie zugreifbare Tabellen in den HTML5-Formularen erstellen.
seo-description: Learn how to create accessible tables in HTML5 forms.
uuid: e52562d2-4dc3-4359-9dbb-c18614921808
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 3504afe1-abf5-4fbf-a0d2-e093361764bd
feature: Mobile Forms
exl-id: 3b8e3323-9ac4-4f5c-8c52-e2186e9169ea
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '273'
ht-degree: 100%

---

# Zugreifbare komplexe Tabellen in HTML5-Formularen erstellen {#create-accessible-complex-tables-in-html-forms}

Die Standardimplementierung von Tabellen in den HTML5-Formularen verwendet HTML DIV-Elemente, um eine neue Tabelle zu rendern. Das Rendern involviert die Verwendung von ARIA-Rollen, um den Anforderungen für den barrierefreien Zugriff gerecht zu werden.

Um Probleme mit der Barrierefreiheit mit Bildschirmsprachausgaben zu vermeiden, die ARIA-Rollen nicht voll unterstützen, die mit Datentabellen verwendet werden, bieten HTML5-Formulare eine alternative Darstellung für die Tabellen. Diese Tabellen basieren auf dem neuen Tabellenformat, das in Designer eingeführt wurde und das ebenfalls Folgendes unterstützt:

* Zeilenkopf
* Zeilenabschnitt

Um das neue Format in HTML5-Forms zu verwenden, markieren Sie die Tabelle als komplex. Um die Tabelle als komplex zu markieren, fügen Sie den `extras`-Tag in die XML-Quelle des Tabellenteilformulars wie folgt hinzu: 

```xml
</extras>
 <text name="complexTable">1</text>
 </extras>
```

Die Tabellen, die als *complexTable* markiert werden, folgen der nativen HTML-Darstellung und bieten eine bessere Barrierefreiheit für bestimmte Bildschirmsprachausgaben.  Um einen Zeilenabschnitt zu erstellen, wählen Sie mehrere Zellen einer Tabelle in derselben Spalte, klicken Sie mit der rechten Maustaste auf die Auswahl und klicken Sie dann auf **[!UICONTROL Zellen verbinden]**.

>[!NOTE]
>
>Das Erstellen eines Zeilenabschnitts funktioniert nur für die am weitesten links liegenden Zellen.

Um eine Zeile als Zeilenkopf zu markieren, wählen Sie alle Zellen in der Zeile, klicken Sie mit der rechten Maustaste auf die Auswahl und klicken Sie dann auf **[!UICONTROL Kopf markieren]**.

Um eine Zelle als Spaltenkopf zu markieren, wählen Sie eine beliebige Zelle in der Spalte, klicken Sie mit der rechten Maustaste auf die Auswahl und klicken Sie dann auf **[!UICONTROL Kopf markieren]**.

Einschränkungen im neuen *AccessibleTable*-Format:

* Fehlende Unterstützung für vergrößerungsfähige Felder, wenn Zeilenabschnitt in der Tabelle verwendet wird
* Keine Unterstützung für verschachtelte Tabellen (Tabellen in Tabellenzellen)
* Unterstützung für Zeilenabschnitt ist auf die Kopfzeilen und Kopfzellen beschränkt
* Unterstützung ist auf reguläre Tabellen beschränkt
* Keine Unterstützung für Dateneinfügungen in Tabellen mit Zeilenabschnitt > 1
