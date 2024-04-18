---
title: Suchen
description: Die Autorenumgebung von AEM bietet abhängig vom Ressourcentyp verschiedene Möglichkeiten zur Inhaltssuche.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
docset: aem65
exl-id: 1f46a57f-4966-4dd1-8c99-c0740718ae76
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 100%

---

# Suchen{#searching}

Die Autorenumgebung von AEM bietet abhängig vom Ressourcentyp verschiedene Möglichkeiten zur Inhaltssuche.

>[!NOTE]
>
>Außerhalb der Authoring-Umgebung stehen auch andere Verfahren zur Suche zur Verfügung, wie der [Query Builder](/help/sites-developing/querybuilder-api.md) und [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

## Grundlagen zur Suche {#search-basics}

Um den Suchbereich aufzurufen, klicken Sie in der jeweiligen Konsole im linken Bereich oben auf die Registerkarte **Suchen**.

![chlimage_1-101](assets/chlimage_1-101.png)

Im Suchbereich können Sie alle Seiten Ihrer Website durchsuchen. Er enthält Felder und Widgets für folgende Zwecke:

* **Volltext**: Nach dem angegebenen Text suchen
* **Geändert nach/vor**: Nur nach den Seiten suchen, die zwischen den bestimmten Datumsangaben geändert wurden
* **Vorlage**: Nur nach den Seiten suchen, die auf der angegebenen Vorlage basieren
* **Tags**: Nur nach Seiten mit den angegebenen Tags suchen

>[!NOTE]
>
>Wenn Ihre Instanz für die [Lucene-Recherche](/help/sites-deploying/queries-and-indexing.md) konfiguriert ist, können Sie folgende Elemente unter **Volltext** verwenden:
>
>* [Platzhalter](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Wildcard_Searches) 
>* [Boolesche Operatoren](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Boolean_operators)
>
>* [Reguläre Ausdrücke](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Regexp_Searches)
>* [Feld-Gruppierung](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Field_Grouping) 
>* [Verstärken](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Boosting_a_Term)
>

Starten Sie die Suche, indem Sie unten im Bereich auf **Suchen** klicken. Klicken Sie auf **Zurücksetzen**, um die Suchkriterien zu löschen.

## Filter {#filter}

An verschiedenen Stellen kann ein Filter festgelegt (und gelöscht) werden, um Ihre Ansicht weiter aufzuschlüsseln und zu verfeinern:

![chlimage_1-102](assets/chlimage_1-102.png)

## Suchen und Ersetzen {#find-and-replace}

In der Konsole **Websites** ermöglicht Ihnen die Menüoption **Suchen und Ersetzen**, innerhalb eines Bereichs der Website nach mehreren Vorkommen einer Zeichenfolge zu suchen und diese zu ersetzen.

1. Wählen Sie die Stammseite bzw. den Stammordner aus, in dem die Aktion „Suchen und Ersetzen“ stattfinden soll.
1. Wählen Sie **Tools** und dann **Suchen und Ersetzen**:

   ![screen_shot_2012-02-15at120346pm](assets/screen_shot_2012-02-15at120346pm.png)

1. Der Dialog **Suchen und Ersetzen** bietet die folgenden Möglichkeiten:

   * bestätigt den Stammpfad, in dem die Suchaktion beginnen soll
   * definiert den zu suchenden Begriff
   * definiert den Begriff, der ihn ersetzen soll
   * gibt an, ob bei der Suche die Groß-/Kleinschreibung beachtet werden soll
   * gibt an, ob nur ganze Wörter gesucht werden sollen (andernfalls werden auch Unterzeichenfolgen gesucht)

   Durch Klicken auf **Vorschau** werden die Stellen aufgelistet, an denen der Begriff gefunden wurde. Sie können bestimmte Instanzen markieren bzw. deren Markierung aufheben:

   ![screen_shot_2012-02-15at120719pm](assets/screen_shot_2012-02-15at120719pm.png)

1. Klicken Sie auf **Ersetzen**, um die tatsächliche Ersetzung aller Instanzen durchzuführen. Sie werden aufgefordert, den Vorgang zu bestätigen.

Der Standardumfang für das Servlet „Suchen und Ersetzen“ deckt die folgenden Eigenschaften ab:

* `jcr:title`
* `jcr:description`
* `jcr:text`
* `text`

Dieser Bereich kann mithilfe der Apache Felix Web Management Console geändert werden (z. B. unter`https://localhost:4502/system/console/configMgr`). Wählen Sie `CQ WCM Find Replace Servlet (com.day.cq.wcm.core.impl.servlets.FindReplaceServlet)` aus und konfigurieren Sie den Bereich nach Bedarf.

>[!NOTE]
>
>In einer standardmäßigen AEM-Installation wird bei „Suchen und Ersetzen“ Lucene für die Suchfunktion verwendet.
>
>Lucene indiziert Zeichenfolgen mit bis zu 16K Länge. Darüber hinaus gehende Zeichenfolgen werden nicht gesucht.
