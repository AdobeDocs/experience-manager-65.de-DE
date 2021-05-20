---
title: Status der Funktionen der Touch-optimierten Benutzeroberfläche
description: 'Spezifische Versionshinweise zur Touch-optimierten Benutzeroberfläche. [!DNL Adobe Experience Manager] '
exl-id: 7b71e8db-e8c6-4470-bc22-db3d4600b7fc
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1063'
ht-degree: 50%

---

# Status der Funktionen der Touch-optimierten Benutzeroberfläche {#touch-ui-feature-status}

Ab AEM 6.4 ist [Klassische Benutzeroberfläche veraltet](../release-notes/deprecated-removed-features.md). Adobe bietet keine weiteren Verbesserungen an der klassischen Benutzeroberfläche. Es wird empfohlen, die leistungsstarken neuen Funktionen der Touch-optimierten Benutzeroberfläche zu nutzen.

Ab Version 6.0 führte AEM eine neue Benutzeroberfläche ein, die als &quot;Touch-optimierte Benutzeroberfläche&quot;(einfach &quot;Touch-Benutzeroberfläche&quot;) bezeichnet wird und an die [!DNL Adobe Experience Cloud] und die allgemeinen Richtlinien für die Benutzeroberfläche der Adobe angepasst ist. Da die Funktionsparität nahezu erreicht wurde, ist diese inzwischen die Standard-Benutzeroberfläche in AEM mit der veralteten, Desktop-orientierten Benutzeroberfläche, die als &quot;klassische Benutzeroberfläche&quot;bezeichnet wird.

Die meisten Funktionen sind zwar in der Touch-optimierten Benutzeroberfläche vorhanden, allerdings ist die Entwicklung einiger Funktionen noch nicht abgeschlossen. Diese werden dann in künftigen Versionen hinzugefügt.

Die folgende Liste zeigt den aktuellen Status der in AEM 6.5 implementierten Funktionen.

Empfehlungen für Kunden, die auf AEM 6.5 aktualisieren, finden Sie unter [Empfehlungen zur Benutzeroberfläche für Kunden](/help/sites-deploying/ui-recommendations.md).

>[!NOTE]
>
>Diese Seite behandelt nur die Funktionsparität mit der klassischen Benutzeroberfläche. Funktionen, die der Touch-optimierten Benutzeroberfläche hinzugefügt wurden und die nicht in der klassischen Benutzeroberfläche vorhanden sind, werden nicht aufgeführt.

>[!NOTE]
>
>Diese Liste ist vollständig, aber nicht vollständig.

## Legende {#legend}

* **Umfassend**: Die Funktion ist in vollem Umfang in der Touch-optimierten Benutzeroberfläche verfügbar..
* **Hauptsächlich**: Die Funktion ist größtenteils in der Touch-optimierten Benutzeroberfläche verfügbar.
* **Fehlt**: Die Funktion ist nicht in der Touch-optimierten Benutzeroberfläche verfügbar. Um die entsprechende Aktion durchzuführen, müssen Sie die klassische Benutzeroberfläche verwenden.
* **Ersetzt**: Diese Funktion wurde durch eine neue Implementierung ersetzt, die anders funktioniert.
* **Entfernt**: Die Funktion ist nicht mehr in der Touch-optimierten Benutzeroberfläche verfügbar und wird nicht ersetzt.

## Funktionsstatus: Sites Admin {#feature-status-sites-admin}

Dies ist eine Liste der Funktionen, die der Site-Administrator der klassischen Benutzeroberfläche (`/siteadmin`) hat, und der Status in der Touch-optimierten Benutzeroberfläche (`/sites.html`).

| Funktion | Status | Kommentar |
|--- |--- |--- |
| Site-Hierarchie navigieren | Fertig stellen | AEM 6.4 wurde eine [Inhaltsbaumansicht](/help/sites-authoring/basic-handling.md#content-tree) eingeführt. |
| Workflow starten | Fertig stellen |  |
| Neue Seite erstellen | Umfassend |  |
| Neue Site erstellen | Umfassend |  |
| Neuen Launch erstellen | Umfassend |  |
| Neue Live Copy erstellen | Fertig stellen |  |
| Ordner erstellen | Umfassend |  |
| Veröffentlichungsstatus anzeigen | Fertig stellen | Ab AEM 6.5 wird der Workflow-Status in der Listenansicht angezeigt. |
| Suchen | Fertig stellen |  |
| Seite kopieren und einfügen (Duplizieren) | Fertig stellen |  |
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
| Verweise | Fertig stellen | Anzeige eingehender Seitenlinks, die zu AEM 6.5 hinzugefügt wurden. |

## Funktionsstatus: Seiten-Editor {#feature-status-page-editor}

Dies ist eine Liste der Funktionen, die der Seiten-Editor der klassischen Benutzeroberfläche (`/cf#`) aufweist, und der Status in der Touch-optimierten Benutzeroberfläche (`/editor.html`).

| Funktion | Status | Kommentar |
|--- |--- |--- |
| Webseiten bearbeiten | Umfassend |  |
| Mobile Webseiten bearbeiten | Fertig stellen |  |
| Per Design-Importtool importierte Inhalte bearbeiten | Fertig stellen |  |
| E-Mails bearbeiten | Umfassend |  |
| Bearbeiten von Hybrid-Apps für Mobilgeräte | Fertig stellen |  |
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
| Rollout-Seite | Fertig stellen |  |
| Workflow starten und anzeigen | Fertig stellen |  |
| Handhabung von Workflow-Paketen | Nahezu umfassend | Vollständiger Zugriff über die Touch-optimierte Benutzeroberfläche. Mehrere Workflow-Nutzdaten werden weiterhin in der klassischen Benutzeroberfläche angezeigt. |
| Seite sperren/entsperren | Umfassend |  |
| Seite veröffentlichen | Fertig stellen |  |
| Veröffentlichen einer Seite rückgängig machen | Umfassend |  |
| Kopieren einer Seite | Entfernt | Verwenden Sie Sites Admin, um [Seiten zu kopieren](/help/sites-authoring/managing-pages.md#copying-and-pasting-a-page). |
| Seite verschieben | Entfernt | Verwenden Sie Sites Admin, um [Seiten zu verschieben](/help/sites-authoring/managing-pages.md#moving-or-renaming-a-page). |
| Seite löschen | Entfernt | Verwenden Sie Sites Admin, um [Seiten zu löschen](/help/sites-authoring/managing-pages.md#deleting-a-page). |
| Verweise einblenden | Entfernt | Verwenden Sie Site Admin, um die [detaillierte Referenzliste](/help/sites-authoring/author-environment-tools.md#references) anzuzeigen. |
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
| Komponenten kopieren und einfügen | Fertig stellen |  |
| Komponentenliste in Zwischenablage kopieren | Fehlt |  |
| Rückgängig/Wiederholen | Umfassend |  |
| Inhalt in Komponenten-Platzhalter ziehen | Fertig stellen |  |
| Ziehen Sie Inhalt direkt in den ParSys-Platzhalter mit automatischer Komponentenerstellung | Fertig stellen |  |

## Funktionsstatus: Text-, Tabellen- und Bild-Editoren {#feature-status-text-table-and-image-editors}

Dies ist eine Liste der Funktionen des Text-, Tabellen- und Bild-Editors der klassischen Benutzeroberfläche sowie des Status in der Touch-optimierten Benutzeroberfläche.

| Funktion | Status | Kommentar |
|--- |--- |--- |
| Rich-Text-Editor | Fertig stellen | Verwendbar im Kontext, im Dialogfeld und im Vollbildmodus. |
| RTE-Plug-ins aktivieren/deaktivieren | Fertig stellen | Kann mit dem [Vorlagen-Editor](/help/sites-authoring/templates.md) durchgeführt werden. |
| RTE für Nur-Text verwenden | Fertig stellen |  |
| RTE-Plug-in: Links und Anker | Fertig stellen |  |
| RTE-Plug-in: Zeichenzuordnung | Fertig stellen |  |
| RTE-Plug-in: Kopieren/Einfügen | Fertig stellen |  |
| RTE-Plug-in: Aus Microsoft Word einfügen | Fertig stellen |  |
| RTE-Plug-in: Suchen und Ersetzen | Fertig stellen |  |
| RTE-Plug-in: Textformate (fett, ...) | Fertig stellen |  |
| RTE-Plug-in: Tiefgestellt und hochgestellt | Fertig stellen |  |
| RTE-Plug-in: Blocksatz | Fertig stellen |  |
| RTE-Plug-in: Listen (Aufzählungszeichen/Zahlen) | Fertig stellen |  |
| RTE-Plug-in: Absatzformat | Fertig stellen |  |
| RTE-Plug-in: Textstile | Fertig stellen |  |
| RTE-Plug-in: Quell-Editor (HTML bearbeiten) | Fertig stellen | Nur im Dialogfeld und im Vollbildmodus verfügbar. |
| RTE-Plug-in: Rechtschreibprüfung | Fertig stellen |  |
| RTE-Plug-in: Tabelle (eingebetteter Tabellen-Editor) | Fertig stellen |  |
| RTE-Plug-in: Rückgängig/Wiederherstellen | Fertig stellen |  |
| RTE-Plug-in: Inline-Bilder zulassen | Fertig stellen |  |
| Tabelleneditor | Fertig stellen | Verwendbar im Kontext, im Dialogfeld und im Vollbildmodus. |
| Bild in Tabellenzelle ziehen | Fertig stellen | In-line-Funktion |
| Bildeditor | Fertig stellen | Verwendbar im Kontext, im Dialogfeld und im Vollbildmodus. |
| IPE-Plug-ins aktivieren/deaktivieren | Fertig stellen | In AEM 6.3 wurde eine Benutzeroberfläche im [Vorlagen-Editor](/help/sites-authoring/templates.md) eingeführt. |
| IPE-Plug-in: Zuschneiden | Fertig stellen |  |
| IPE-Plug-in: Spiegeln | Fertig stellen |  |
| IPE-Plug-in: Rückgängig/Wiederherstellen | Fertig stellen |  |
| IPE-Plug-in: Imagemap | Fertig stellen |  |
| IPE-Plug-in: Drehen | Fertig stellen |  |
| IPE-Plug-in: Zoom | Fertig stellen |  |

## Funktionsstatus: Werkzeuge {#feature-status-tools}

Dies ist eine Liste der verschiedenen Werkzeuge der klassischen Benutzeroberfläche sowie deren Status in der Touch-optimierten Benutzeroberfläche.

| Funktion | Status | Kommentar |
|--- |--- |--- |
| Aufgabenverwaltung | Ersetzt | In 6.0 wurden Projekte und Aufgaben eingeführt. |
| Workflow-Posteingang | Fertig stellen |  |
| Workflow zur Konfiguration der Seitenvorlage (`/etc/workflow/wcm/templates.html`) | Fehlt | Verwenden Sie die klassische Benutzeroberfläche. |
| Tagging der Admin-Benutzeroberfläche | Fertig stellen |  |
| MSM/Blueprint Control Center | Fertig stellen |  |
| Blueprint-Manager-Benutzeroberfläche | Fertig stellen |  |
| Benutzeroberfläche für Rollout-Konfiguration | Fehlt | Verwenden Sie die klassische Benutzeroberfläche. |
| Benutzeroberfläche für Benutzer, Gruppen und Berechtigungen | Nahezu umfassend | Verwenden Sie die klassische Benutzeroberfläche für die erweiterte Bearbeitung von Berechtigungen. |
| Versionen bereinigen (`/etc/versioning/purge.html`) | Fehlt | Verwenden Sie die klassische Benutzeroberfläche. |
| Prüfer für externe Links (`/etc/linkchecker.html`) | Fehlt | Verwenden Sie die klassische Benutzeroberfläche. |
| Bulk Editor (`/etc/importers/bulkeditor.html`) | Fehlt | Verwenden Sie die klassische Benutzeroberfläche. |
| Hochladen von Miniaturansichten zum Hinzufügen oder Überschreiben dieser Miniaturansichten | Fehlt | Verwenden Sie die klassische Benutzeroberfläche. |
