---
title: Verwenden von Launches zur Entwicklung von Inhalten für eine zukünftige Version
description: Mit Launches können Sie effizient Inhalte für eine zukünftige Version entwickeln. Sie ermöglichen es Ihnen, Änderungen für eine spätere Veröffentlichung vorzunehmen, während Sie Ihre aktuellen Seiten beibehalten.
uuid: 4bbd9865-735d-4232-b69c-b64193ac5d83
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: e145afd8-7391-47aa-b389-16fb303749d0
docset: aem65
exl-id: b25d3f8e-5687-49ab-95e1-19ec75c87f6e
source-git-commit: f4b6eb2ded17ec641f23a1fc3b977ce77169c8a1
workflow-type: ht
source-wordcount: '833'
ht-degree: 100%

---

# Launches{#launches}

Launches helfen Ihnen, Inhalte für eine künftige Version effizient zu entwickeln.

Ein Launch wird erstellt, damit Sie (unter Beibehaltung der aktuellen Seiten) Änderungen für eine spätere Veröffentlichung vornehmen können. Wenn Sie die Launch-Seiten bearbeitet und aktualisiert haben, leiten Sie diese wieder zurück in die Quelle und aktivieren dann die Quellseiten (auf der obersten Ebene). Durch die Weiterleitung wird der Launch-Inhalt wieder auf die Quellseiten kopiert und kann entweder manuell oder automatisch ausgeführt werden (abhängig von den Feldern, die beim Erstellen und Bearbeiten des Launches festgelegt wurden).

Beispiel: Die saisonalen Produktseiten in Ihrem Online-Shop werden einmal pro Quartal aktualisiert, damit die präsentierten Produkte der aktuellen Saison entsprechen. Zur Vorbereitung auf die nächste Quartals-Aktualisierung können Sie einen Launch der relevanten Web-Seiten erstellen. Während des Quartals werden die folgenden Änderungen in der Launch-Kopie gesammelt:

* Änderungen an den Quellseiten, die die Folge normaler Wartungsarbeiten sind. Diese Änderungen werden automatisch in den Launch-Seiten dupliziert.
* Änderungen, die direkt auf den Launch-Seiten in Vorbereitung auf das nächste Quartal vorgenommen werden.

Wenn ein neues Quartal beginnt, leiten Sie die Launch-Seiten weiter, damit Sie die Quellseiten veröffentlichen können, die den aktualisierten Inhalt enthalten. Sie können entweder alle Seiten weiterleiten oder nur die Seiten, die Sie geändert haben.

Launches können auch:

* Für mehrere Stammverzweigungen erstellt werden. Sie können zwar den Launch für die gesamte Site erstellen (und die Änderungen dort vornehmen), dies kann jedoch sehr umständlich sein, da die gesamte Site kopiert werden muss. Wenn Hunderte oder sogar Tausende von Seiten beteiligt sind, wirken sich die Kopieraktion und später die für die Promotions-Aufgaben erforderlichen Vergleiche auf die Systemanforderungen und die Leistung aus.
* Verschachtelt (ein Launch innerhalb eines Launches), um Ihnen die Möglichkeit zu geben, einen Launch aus einem bestehenden Launch zu erstellen, sodass Autoren und Autorinnen die bereits vorgenommenen Änderungen nutzen können, anstatt dieselben Änderungen mehrfach für jeden Launch vornehmen zu müssen.

In diesem Abschnitt wird beschrieben, wie Sie Launch-Seiten innerhalb der Sites-Konsole oder der [Launch-Konsole](#the-launches-console) erstellen, bearbeiten und weiterleiten (und bei Bedarf [löschen](/help/sites-authoring/launches-creating.md#deleting-a-launch)):

* [Erstellen von Launches](/help/sites-authoring/launches-creating.md)
* [Bearbeiten von Launches](/help/sites-authoring/launches-editing.md)
* [Weiterleiten von Launches](/help/sites-authoring/launches-promoting.md)

## Der Ablauf eines Launches {#launches-the-order-of-events}

Mit Launches können Sie effizient den Inhalt für eine zukünftige Veröffentlichung einer oder mehrerer aktivierter Web-Seiten entwickeln.

Launches ermöglichen Folgendes:

* Erstellen Sie eine Kopie Ihrer Quellseiten:

   * Die Kopie ist Ihr Launch.
   * Die Quellseiten der höchsten Stufe werden als **Produktion** bezeichnet.

      * Die Quellseiten können aus mehreren (verschiedenen) Verzweigungen stammen.

   ![chlimage_1-111](assets/chlimage_1-111.png)

* Bearbeiten Sie die Launch-Konfiguration:

   * Sie können Seiten bzw. Verzweigungen zum Launch hinzufügen oder entfernen.
   * Sie können Launch-Eigenschaften bearbeiten, z. B. **Titel**, **Launch-Datum** und die Markierung **Produktionsbereit**.

* Sie können Inhalte entweder manuell oder automatisch weiterleiten und veröffentlichen:

   * Manuell:

      * Leiten Sie Ihren Launch-Inhalt, wenn er zur Veröffentlichung bereit ist, wieder an das **Ziel** (Quellseiten) zurück.
      * Veröffentlichen Sie den Inhalt von den Quellseiten (nachdem die Seiten weitergeleitet wurden).
      * Leiten Sie entweder alle Seiten oder nur die überarbeiteten Seiten weiter.
   * Automatisch (dies beinhaltet Folgendes):

      * Das Feld **Launch-Datum** (**Live**-**Datum)**: Dieses Feld kann beim Erstellen oder Bearbeiten eines Launches festgelegt werden.

      * Die Markierung **Produktionsbereit**: Dies kann nur beim Bearbeiten eines Launches festgelegt werden.
      * Wenn das Flag **Produktionsbereit** gesetzt wurde, wird der Launch automatisch am angegebenen **Launch-Datum** (**Live**-**Datum**) an die Produktionsseiten weitergeleitet. Nach der Promotion werden die Produktionsseiten automatisch veröffentlicht.\
         Wenn kein Datum ausgewählt wurde, hat die Markierung keine Auswirkungen.


* Paralleles Aktualisieren der Quell- und Launch-Seiten:

   * Änderungen an den Quellseiten werden automatisch in der Launch-Kopie implementiert (wenn sie mit Vererbung eingerichtet wurden, z. B. in Form einer Live Copy).
   * Änderungen an der Launch-Kopie können ohne Störung dieser automatischen Aktualisierungen oder der Quellseiten vorgenommen werden.

   ![chlimage_1-112](assets/chlimage_1-112.png)

* [Erstellen eines verschachtelten Launches](/help/sites-authoring/launches-creating.md#creating-a-nested-launch) – ein Launch innerhalb eines Launches:

   * Die Quelle ist ein vorhandener Launch.
   * Sie können [einen verschachtelten Launch](/help/sites-authoring/launches-promoting.md#promoting-a-nested-launch) zu einem beliebigen Ziel weiterleiten; dies kann ein übergeordneter Launch oder die Quellseiten der obersten Ebene (Produktion) sein.

   ![chlimage_1-113](assets/chlimage_1-113.png)

   >[!CAUTION]
   >
   >Durch Löschen eines Launches werden der Launch selbst sowie alle nachfolgenden verschachtelten Launches entfernt.

>[!NOTE]
>
>Für das Erstellen und Bearbeiten von Launches sind Zugriffsrechte auf `/content/launches` erforderlich (wie bei der Standardgruppe `content-authors`).
>
>Wenden Sie sich an Ihren Systemadministrator, falls Probleme auftreten.

>[!CAUTION]
>
>Die Neuanordnung von Komponenten auf einer Launch-Seite wird nicht unterstützt.
>
>Wenn die Seite beworben wird, werden alle Inhaltsänderungen angezeigt, aber die Komponentenpositionen ändern sich nicht.


### Die Konsole „Launches“  {#the-launches-console}

Die Konsole „Launches“ bietet eine Zusammenfassung Ihrer Launches und ermöglicht es Ihnen, die aufgeführten Aktionen auszuführen. Auf die Konsole kann wie folgt zugegriffen werden:

* über die Konsole **Tools**: **Tools** > **Sites** > **Launches**.

* oder direkt mit [https://localhost:4502/libs/launches/content/launches.html](https://localhost:4502/libs/launches/content/launches.html)

## Launches in „Verweise“ (Sites-Konsole) {#launches-in-references-sites-console}

1. Navigieren Sie in der Konsole **Sites** zur Quelle der Launches.
1. Öffnen Sie die Leiste **Referenzen** und wählen Sie die Quellseite aus.
1. Wählen Sie **Launches**, die vorhandenen Launches werden aufgelistet:

   ![screen-shot_2019-03-05at121901-1](assets/screen-shot_2019-03-05at121901-1.png)

1. Tippen/klicken Sie auf den entsprechenden Launch. Die Liste der möglichen Aktionen wird angezeigt:

   ![screen-shot_2019-03-05at121952-1](assets/screen-shot_2019-03-05at121952-1.png)
