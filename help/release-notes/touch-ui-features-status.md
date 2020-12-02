---
title: Status der Funktionen der Touch-optimierten Benutzeroberfläche
description: 'Spezifische Versionshinweise zur touchaktivierten Benutzeroberfläche. [!DNL Adobe Experience Manager] '
translation-type: tm+mt
source-git-commit: d938f52766154b68df2f6db2c8c49a0ad97e7e6d
workflow-type: tm+mt
source-wordcount: '1063'
ht-degree: 49%

---


# Status der Funktionen der Touch-optimierten Benutzeroberfläche {#touch-ui-feature-status}

Ab AEM 6.4 [Klassische Benutzeroberfläche ist veraltet](../release-notes/deprecated-removed-features.md). Die Benutzeroberfläche von Classic wird durch Adobe nicht weiter verbessert, und Benutzer sollten die leistungsstarken neuen Funktionen der touchfähigen Benutzeroberfläche nutzen.

Ab Version 6.0 hat AEM eine neue Benutzeroberfläche eingeführt, die als &quot;touchfähige Benutzeroberfläche&quot;(einfach &quot;Touch UI&quot; genannt) bezeichnet wird und an den [!DNL Adobe Experience Cloud]- und den allgemeinen Adobe-Benutzeroberflächenrichtlinien ausgerichtet ist. Da die Funktionsparität nahezu erreicht ist, wurde diese zur Standard-Benutzeroberfläche in AEM mit der alten, Desktop-orientierten Oberfläche, die als &quot;klassische Benutzeroberfläche&quot;bezeichnet wird.

Die meisten Funktionen sind zwar in der Touch-optimierten Benutzeroberfläche vorhanden, allerdings ist die Entwicklung einiger Funktionen noch nicht abgeschlossen. Diese werden dann in künftigen Versionen hinzugefügt.

Die folgende Liste zeigt den aktuellen Status der in AEM 6.5 implementierten Funktionen.

Empfehlungen für Kunden, die auf AEM 6.5 aktualisieren, finden Sie unter [Empfehlungen für die Benutzeroberfläche für Kunden](/help/sites-deploying/ui-recommendations.md).

>[!NOTE]
>
>Diese Seite behandelt nur die Funktionsparität mit der klassischen Benutzeroberfläche. Funktionen, die der Touch-fähigen Benutzeroberfläche hinzugefügt wurden und die in der klassischen Benutzeroberfläche nicht vorhanden sind, werden nicht aufgeführt.

>[!NOTE]
>
>Diese Liste ist vollständig, aber nicht erschöpfend.

## Legende {#legend}

* **Abgeschlossen**: Die Funktion ist in der touchfähigen Benutzeroberfläche vollständig verfügbar.
* **Meistens**: Die Funktion ist hauptsächlich in der touchfähigen Benutzeroberfläche verfügbar.
* **Fehlt**: Die Funktion ist nicht in der Touch-optimierten Benutzeroberfläche verfügbar. Um die entsprechende Aktion durchzuführen, müssen Sie die klassische Benutzeroberfläche verwenden.
* **Ersetzt**: Diese Funktion wurde durch eine neue Implementierung ersetzt, die anders funktioniert.
* **Entfernt**: Die Funktion ist nicht mehr in der Touch-optimierten Benutzeroberfläche verfügbar und wird nicht ersetzt.

## Funktionsstatus: Sites Admin {#feature-status-sites-admin}

Dies ist eine Liste von Funktionen, die der klassische Site-Administrator der Benutzeroberfläche (`/siteadmin`) hat und den Status in der touchfähigen Benutzeroberfläche (`/sites.html`).

| Funktion | Status | Kommentar |
|--- |--- |--- |
| Site-Hierarchie navigieren | Fertig stellen | AEM 6.4 wurde eine [Content Tree-Ansicht](/help/sites-authoring/basic-handling.md#content-tree) eingeführt. |
| Workflow starten | Fertig stellen |  |
| Neue Seite erstellen | Umfassend |  |
| Neue Site erstellen | Umfassend |  |
| Neuen Launch erstellen | Umfassend |  |
| Neue Live Copy erstellen | Fertig stellen |  |
| Ordner erstellen | Umfassend |  |
| Veröffentlichungsstatus anzeigen | Fertig stellen | Ab AEM 6.5 wird der Workflow-Status in der Ansicht Liste angezeigt. |
| Suchen | Fertig stellen |  |
| Seite kopieren und einfügen (Duplikat) | Fertig stellen |  |
| Seite(n) verschieben | Umfassend |  |
| Seite(n) veröffentlichen | Umfassend |  |
| Seite(n) ohne Replikationsberechtigung veröffentlichen | Umfassend |  |
| Später veröffentlichen | Umfassend |  |
| Struktur veröffentlichen | Umfassend |  |
| Veröffentlichung der Seite(n) rückgängig machen | Umfassend |  |
| Veröffentlichung der Seite(n) ohne Replikationsberechtigungen rückgängig machen | Umfassend |  |
| Veröffentlichung später rückgängig machen | Fertig stellen |  |
| Löschen | Umfassend |  |
| Sperren/Entsperren | Umfassend |  |
| Eigenschaften anzeigen/bearbeiten | Umfassend |  |
| Berechtigungen für Seite(n) festlegen | Umfassend |  |
| Versionsverlauf | Umfassend |  |
| Version wiederherstellen | Fertig stellen |  |
| Baum wiederherstellen und gelöschte Seiten wiederherstellen | Fehlt | Verwenden Sie die klassische Benutzeroberfläche. |
| Unterschied zwischen vorheriger und aktueller Version anzeigen | Fertig stellen |  |
| Live Copy-Aktionen (Rollout) | Umfassend |  |
| Sprachkopien anzeigen | Umfassend |  |
| Suchen und Ersetzen | Fehlt | Verwenden Sie die klassische Benutzeroberfläche. |
| Benachrichtigungs-Posteingang (JCR-Ereignisse) | Fehlt | Verwenden Sie die klassische Benutzeroberfläche. Wird durch andere Implementierung ersetzt. |
| Verweise | Fertig stellen | Anzeige von Links zu eingehenden Seiten, die AEM 6.5 hinzugefügt wurden. |

## Funktionsstatus: Seiten-Editor {#feature-status-page-editor}

Dies ist eine Liste von Funktionen, die der klassische UI-Seiten-Editor (`/cf#`) hat und den Status in der touchfähigen (`/editor.html`).

| Funktion | Status | Kommentar |
|--- |--- |--- |
| Webseiten bearbeiten | Umfassend |  |
| Mobile Webseiten bearbeiten | Fertig stellen |  |
| Per Design-Importtool importierte Inhalte bearbeiten | Fertig stellen |  |
| E-Mails bearbeiten | Umfassend |  |
| Bearbeiten von Hybrid-Mobil-Apps | Fertig stellen |  |
| Formulare bearbeiten | Fertig stellen |  |
| Angebote bearbeiten | Fertig stellen |  |
| Workflow-Modelle bearbeiten | Fertig stellen |  |
| Modus: Bearbeiten und Vorschau | Fertig stellen |  |
| Responsive Vorschau | Fertig stellen |  |
| Modus: Entwurf bearbeiten | Umfassend |  |
| Modus: Strukturvorlagen-Modus | Umfassend |  |
| Modus: Live Copy-Status | Fertig stellen |  |
| Anmerkungen hinzufügen | Umfassend |  |
| Eigenschaften bearbeiten | Fertig stellen |  |
| Roll-out-Seite | Fertig stellen |  |
| Arbeitsablauf für Beginn und Anzeige | Fertig stellen |  |
| Handling von Workflow-Paketen | Nahezu umfassend | Vollständig verfügbar in der touchfähigen Benutzeroberfläche. Mehrere Workflow-Nutzdaten werden weiterhin in der klassischen Benutzeroberfläche angezeigt. |
| Seite sperren/entsperren | Umfassend |  |
| Seite veröffentlichen | Fertig stellen |  |
| Veröffentlichen einer Seite rückgängig machen | Umfassend |  |
| Kopieren einer Seite | Entfernt | Verwenden Sie Sites Admin, um [Seiten zu kopieren](/help/sites-authoring/managing-pages.md#copying-and-pasting-a-page). |
| Seite verschieben | Entfernt | Verwenden Sie Sites Admin, um [Seiten zu verschieben](/help/sites-authoring/managing-pages.md#moving-or-renaming-a-page). |
| Seite löschen | Entfernt | Verwenden Sie Sites Admin, um [Seiten zu löschen](/help/sites-authoring/managing-pages.md#deleting-a-page). |
| Verweise einblenden | Entfernt | Verwenden Sie Site-Administrator, um die [detaillierte Referenz-Liste](/help/sites-authoring/author-environment-tools.md#references) anzuzeigen. |
| Auditprotokoll | Entfernt | Verwenden Sie Sites Admin und [öffnen Sie die Aktivitätsschiene](/help/sites-authoring/author-environment-tools.md#events-timeline). |
| Version erstellen | Entfernt | Verwenden Sie Sites Admin, um [neue Versionen zu erstellen](/help/sites-authoring/working-with-page-versions.md#creating-a-new-version). |
| Version wiederherstellen | Entfernt | Verwenden Sie Sites Admin, um [Versionen wiederherzustellen](/help/sites-authoring/working-with-page-versions.md#reverting-to-a-page-version). |
| Zwischen Launches wechseln | Entfernt | Verwenden Sie Sites Admin, um [zwischen Launches zu wechseln](/help/sites-authoring/launches-promoting.md). |
| Seite übersetzen | Entfernt | Verwenden Sie Sites Admin, um [Seiten zu Übersetzungsprojekten hinzufügen](/help/sites-administering/tc-manage.md). |
| Timewarp (Zeit auswählen und Site in vorherigem Zustand durchsuchen) | Fertig stellen |  |
| Berechtigungen festlegen | Umfassend |  |
| ClientContext-Benutzeroberfläche | Ersetzt | Verwenden Sie künftig die [ContextHub](/help/sites-authoring/ch-previewing.md)-Benutzeroberfläche. |
| Inhaltssuche für die unterschiedlichen Medientypen | Fertig stellen |  |
| Komponentenliste | Fertig stellen |  |
| Kopieren und Einfügen von Komponenten | Fertig stellen |  |
| Komponentenliste in Zwischenablage kopieren | Fehlt |  |
| Rückgängig/Wiederholen | Umfassend |  |
| Ziehen von Inhalten in Platzhalter für Komponenten | Fertig stellen |  |
| Ziehen Sie Inhalte direkt in den Platzhalter parsys mit automatischer Komponentenerstellung | Fertig stellen |  |

## Funktionsstatus: Text-, Tabellen- und Bild-Editoren {#feature-status-text-table-and-image-editors}

Dies ist eine Liste von Funktionen, die die klassischen Benutzeroberflächentext-, Tabellen- und Bild-Editor haben und den Status in der touchfähigen Benutzeroberfläche.

| Funktion | Status | Kommentar |
|--- |--- |--- |
| Rich-Text-Editor | Fertig stellen | Einsetzbar, im Dialog und im Vollbildmodus. |
| RTE-Plug-ins aktivieren/deaktivieren | Fertig stellen | Kann mit dem [Vorlagen-Editor](/help/sites-authoring/templates.md) ausgeführt werden. |
| RTE für Text verwenden | Fertig stellen |  |
| RTE-Plug-in: Links und Anker | Fertig stellen |  |
| RTE-Plug-in: Zeichenzuordnung | Fertig stellen |  |
| RTE-Plug-in: Kopieren/Einfügen | Fertig stellen |  |
| RTE-Plug-in: Aus Microsoft Word einfügen | Fertig stellen |  |
| RTE-Plug-in: Suchen und ersetzen | Fertig stellen |  |
| RTE-Plug-in: Textformate (fett, ...) | Fertig stellen |  |
| RTE-Plug-in: Tiefgestellt | Fertig stellen |  |
| RTE-Plug-in: Blocksatz | Fertig stellen |  |
| RTE-Plug-in: Listen (Aufzählungszeichen/Nummern) | Fertig stellen |  |
| RTE-Plug-in: Absatzformat | Fertig stellen |  |
| RTE-Plug-in: Textstile | Fertig stellen |  |
| RTE-Plug-in: Quell-Editor (HTML bearbeiten) | Fertig stellen | Nur im Dialog und Vollbild verfügbar. |
| RTE-Plug-in: Rechtschreibprüfung | Fertig stellen |  |
| RTE-Plug-in: Tabelle (eingebetteter Tabelleneditor) | Fertig stellen |  |
| RTE-Plug-in: Rückgängig/Wiederholen | Fertig stellen |  |
| RTE-Plug-In: Inline-Bilder zulassen | Fertig stellen |  |
| Tabelleneditor | Fertig stellen | Einsetzbar, im Dialog und im Vollbildmodus. |
| Bild in Tabellenzelle ziehen | Fertig stellen | In-line-fähig |
| Bildeditor | Fertig stellen | Einsetzbar, im Dialog und im Vollbildmodus. |
| IPE-Plug-ins aktivieren/deaktivieren | Fertig stellen | In AEM 6.3 wurde eine Benutzeroberfläche im [Vorlagen-Editor](/help/sites-authoring/templates.md) eingeführt. |
| IPE-Plug-in: Beschneiden | Fertig stellen |  |
| IPE-Plug-in: Spiegeln | Fertig stellen |  |
| IPE-Plug-in: Rückgängig/Wiederholen | Fertig stellen |  |
| IPE-Plug-in: Imagemap | Fertig stellen |  |
| IPE-Plug-in: Drehen | Fertig stellen |  |
| IPE-Plug-in: Zoom | Fertig stellen |  |

## Funktionsstatus: Werkzeuge {#feature-status-tools}

Dies ist eine Liste der verschiedenen Werkzeuge der klassischen Benutzeroberfläche sowie deren Status in der Touch-optimierten Benutzeroberfläche.

| Funktion | Status | Kommentar |
|--- |--- |--- |
| Aufgabenverwaltung | Ersetzt | 6.0 Einführung von Projekten und Aufgaben. |
| Workflow-Posteingang | Fertig stellen |  |
| Workflow zur Konfiguration von Seitenvorlagen (`/etc/workflow/wcm/templates.html`) | Fehlt | Verwenden Sie die klassische Benutzeroberfläche. |
| Tagging-Admin-Benutzeroberfläche | Fertig stellen |  |
| MSM/Blueprint Control Center | Fertig stellen |  |
| Blueprint Manager-Benutzeroberfläche | Fertig stellen |  |
| Benutzeroberfläche der Roll-out-Konfiguration | Fehlt | Verwenden Sie die klassische Benutzeroberfläche. |
| Benutzeroberfläche &quot;Benutzer, Gruppen und Berechtigungen&quot; | Meist abgeschlossen | Für erweiterte Bearbeitung von Berechtigungen verwenden Sie die klassische Benutzeroberfläche. |
| Versionen bereinigen (`/etc/versioning/purge.html`) | Fehlt | Verwenden Sie die klassische Benutzeroberfläche. |
| Prüfer für externe Links (`/etc/linkchecker.html`) | Fehlt | Verwenden Sie die klassische Benutzeroberfläche. |
| Masseneditor (`/etc/importers/bulkeditor.html`) | Fehlt | Verwenden Sie die klassische Benutzeroberfläche. |
| Miniaturansichten hochladen, um diese hinzuzufügen oder zu überschreiben | Fehlt | Verwenden Sie die klassische Benutzeroberfläche. |
