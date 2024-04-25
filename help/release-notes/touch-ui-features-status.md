---
title: Status der Funktionen der Touch-optimierten Benutzeroberfläche
description: Spezifische Versionshinweise für die Touch-optimierte Benutzeroberfläche von  [!DNL Adobe Experience Manager] .
exl-id: 7b71e8db-e8c6-4470-bc22-db3d4600b7fc
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
workflow-type: tm+mt
source-wordcount: '1076'
ht-degree: 100%

---

# Status der Funktionen der Touch-optimierten Benutzeroberfläche {#touch-ui-feature-status}

Ab Adobe Experience Manager (AEM) 6.4 aufwärts: [Die klassische Benutzeroberfläche ist veraltet](../release-notes/deprecated-removed-features.md). Adobe wird keine weiteren Verbesserungen an der klassischen Benutzeroberfläche vornehmen, und Benutzerinnen und Benutzer werden ermutigt, die leistungsstarken neuen Funktionen der Touch-optimierten Benutzeroberfläche zu nutzen.

Seit Einführung von Version 6.0 verfügt AEM über eine neue, Touch-optimierte Benutzeroberfläche (kurz Touch-Oberfläche genannt), die auf [!DNL Adobe Experience Cloud] und die allgemeinen Richtlinien für Benutzeroberflächen von Adobe abgestimmt ist. Da sich die Funktionalitäten der beiden Benutzeroberflächen inzwischen nahezu entsprechen, ist dies nun die Standardbenutzeroberfläche von AEM. Die alte, Desktop-artige Benutzeroberfläche wird hingegen als „klassische Benutzeroberfläche“ bezeichnet.

Die meisten Funktionen sind zwar in der Touch-optimierten Benutzeroberfläche vorhanden, allerdings ist die Entwicklung einiger Funktionen noch nicht abgeschlossen. Diese werden dann in künftigen Versionen hinzugefügt.

In der folgenden Liste ist der Status der in AEM 6.5 verfügbaren Funktionen aufgeführt.

Empfehlungen für Kunden, die ein Upgrade auf AEM 6.5 durchführen, finden Sie unter [Benutzeroberflächenempfehlungen für Kunden](/help/sites-deploying/ui-recommendations.md).

>[!NOTE]
>
>Diese Seite behandelt nur die Funktionsgleichheit mit der klassischen Benutzeroberfläche. Zusätzliche spezifische Funktionen der Touch-optimierten Benutzeroberfläche, die nicht in der klassischen Benutzeroberfläche verfügbar sind, werden hier nicht aufgeführt.

>[!NOTE]
>
>Diese Liste erhebt keinen Anspruch auf Vollständigkeit, strebt sie aber an.

## Legende {#legend}

* **Umfassend**: Die Funktion ist nahezu umfassend in der Touch-optimierten Benutzeroberfläche verfügbar.
* **Nahezu umfassend**: Die Funktion ist nahezu umfassend in der Touch-optimierten Benutzeroberfläche verfügbar.
* **Fehlt**: Die Funktion ist in der Touch-optimierten Benutzeroberfläche nicht vorhanden. Für diese Aktion muss die klassische Benutzeroberfläche verwendet werden.
* **Ersetzt**: Die Funktion wurde durch eine neue Implementierung ersetzt, die anders funktioniert.
* **Entfernt**: Die Funktion ist nicht mehr in der Touch-optimierten Benutzeroberfläche verfügbar und wird nicht ersetzt.

## Funktionsstatus: Sites Admin {#feature-status-sites-admin}

Dies ist eine Liste der Sites Admin-Funktionen der klassischen Benutzeroberfläche (`/siteadmin` ) sowie deren Status in der Touch-optimierten Benutzeroberfläche (`/sites.html`).

| Funktion | Status | Kommentar |
|--- |--- |--- |
| Site-Hierarchie navigieren | Umfassend | Mit AEM 6.4 wurde eine [Inhalts-Baumstrukturbaumansicht](/help/sites-authoring/basic-handling.md#content-tree) eingeführt. |
| Workflow starten | Umfassend |  |
| Neue Seite erstellen | Umfassend |  |
| Neue Site erstellen | Umfassend |  |
| Neuen Launch erstellen | Umfassend |  |
| Neue Live Copy erstellen | Umfassend |  |
| Ordner erstellen | Umfassend |  |
| Veröffentlichungsstatus anzeigen | Umfassend | Ab AEM 6.5 wird der Workflow-Status in der Listenansicht angezeigt. |
| Suchen | Umfassend |  |
| Seite kopieren/einfügen (Duplikat) | Umfassend |  |
| Verschieben von Seiten | Umfassend |  |
| Seiten veröffentlichen | Umfassend |  |
| Seiten ohne Replikationsrechte veröffentlichen | Umfassend |  |
| Später veröffentlichen | Umfassend |  |
| Struktur veröffentlichen | Umfassend |  |
| Veröffentlichung von Seiten aufheben | Umfassend |  |
| Veröffentlichung von Seiten ohne Replikationsrechte aufheben | Umfassend |  |
| Veröffentlichung später rückgängig machen | Umfassend |  |
| Löschen | Umfassend |  |
| Sperren/Entsperren | Umfassend |  |
| Eigenschaften anzeigen/bearbeiten | Umfassend |  |
| Berechtigungen für Seiten festlegen | Umfassend |  |
| Versionsverlauf | Umfassend |  |
| Version wiederherstellen | Umfassend |  |
| Struktur wiederherstellen und gelöschte Seiten wiederherstellen | Fehlt | Verwenden Sie die klassische Benutzeroberfläche. |
| Unterschied zwischen vorheriger und aktueller Version anzeigen | Umfassend |  |
| Live Copy-Aktionen (Rollout) | Umfassend |  |
| Siehe „Sprachkopien“ | Umfassend |  |
| Suchen und Ersetzen | Fehlt | Verwenden Sie die klassische Benutzeroberfläche. |
| Benachrichtigungs-Posteingang (JCR-Ereignisse) | Fehlt | Verwenden Sie die klassische Benutzeroberfläche. Wird in Zukunft durch eine andere Implementierung ersetzt. |
| Verweise | Umfassend | Anzeige eingehender Seitenlinks, die zu AEM 6.5 hinzugefügt wurden. |

## Funktionsstatus: Seiten-Editor {#feature-status-page-editor}

Dies ist eine Liste der Seiten-Editor-Funktionen der klassischen Benutzeroberfläche (`/cf#`) sowie deren Status in der Touch-optimierten Benutzeroberfläche (`/editor.html`).

| Funktion | Status | Kommentar |
|--- |--- |--- |
| Web-Seiten bearbeiten | Umfassend |  |
| Mobile Webseiten bearbeiten | Umfassend |  |
| Per Design-Import-Tool importierte Inhalte bearbeiten | Umfassend |  |
| E-Mails bearbeiten | Umfassend |  |
| Hybride Mobile-Apps bearbeiten | Umfassend |  |
| Formulare bearbeiten | Umfassend |  |
| Angebote bearbeiten | Umfassend |  |
| Workflow-Modelle bearbeiten | Umfassend |  |
| Modus: Bearbeiten und Vorschau | Umfassend |  |
| Responsive Vorschau | Umfassend |  |
| Modus: Design bearbeiten | Umfassend |  |
| Modus: Strukturvorlage | Umfassend |  |
| Modus: Live Copy-Status | Umfassend |  |
| Anmerkungen hinzufügen | Umfassend |  |
| Bearbeiten von Eigenschaften | Umfassend |  |
| Seiten-Rollout | Umfassend |  |
| Workflow starten und anzeigen | Umfassend |  |
| Workflow-Paket-Handling | Nahezu umfassend | Verfügbar über die Touch-optimierte Benutzeroberfläche. In der klassischen Benutzeroberfläche werden weiterhin mehrere Workflow-Payloads angezeigt. |
| Seite sperren/entsperren | Umfassend |  |
| Seite veröffentlichen | Umfassend |  |
| Veröffentlichen einer Seite aufheben | Umfassend |  |
| Kopieren einer Seite | Entfernt | Verwenden Sie Sites Admin, um [Seiten zu kopieren](/help/sites-authoring/managing-pages.md#copying-and-pasting-a-page). |
| Seite verschieben | Entfernt | Verwenden Sie Sites Admin, um [Seiten zu verschieben](/help/sites-authoring/managing-pages.md#moving-or-renaming-a-page). |
| Seite löschen | Entfernt | Verwenden Sie Sites Admin, um [Seiten zu löschen](/help/sites-authoring/managing-pages.md#deleting-a-page). |
| Verweise einblenden | Entfernt | Verwenden Sie Sites Admin, um die [detaillierte Verweisliste](/help/sites-authoring/author-environment-tools.md#references) anzuzeigen. |
| Auditprotokoll | Entfernt | Verwenden Sie Sites Admin und [öffnen Sie die Aktivitätsschiene](/help/sites-authoring/author-environment-tools.md#events-timeline). |
| Version erstellen | Entfernt | Verwenden Sie Sites Admin, um [neue Versionen zu erstellen](/help/sites-authoring/working-with-page-versions.md#creating-a-new-version). |
| Version wiederherstellen | Entfernt | Verwenden Sie Sites Admin, um [Versionen wiederherzustellen](/help/sites-authoring/working-with-page-versions.md#reverting-to-a-page-version). |
| Launches wechseln | Entfernt | Verwenden Sie Sites Admin, um [zwischen Launches zu wechseln](/help/sites-authoring/launches-promoting.md). |
| Seite übersetzen | Entfernt | Verwenden Sie Sites Admin, um [Seiten zu Übersetzungsprojekten hinzufügen](/help/sites-administering/tc-manage.md). |
| Timewarp (Datum/Uhrzeit auswählen und die Website so, wie sie damals aussah, durchsuchen) | Umfassend |  |
| Berechtigungen festlegen | Umfassend |  |
| ClientContext-Benutzeroberfläche | Ersetzt | Verwenden Sie künftig die [ContextHub](/help/sites-authoring/ch-previewing.md)-Benutzeroberfläche. |
| Inhaltssuche für die unterschiedlichen Medientypen | Umfassend |  |
| Komponentenliste | Umfassend |  |
| Komponenten kopieren und einfügen | Umfassend |  |
| Liste der Komponenten in der Zwischenablage | Fehlt |  |
| Rückgängig/Wiederholen | Umfassend |  |
| Inhalte per Drag-and-Drop in den Komponentenplatzhalter einfügen | Umfassend |  |
| Inhalte mit der automatischen Komponentenerstellung direkt per Drag-and in den ParSys-Platzhalter einfügen | Umfassend |  |

## Funktionsstatus: Text-, Tabellen- und Bild-Editoren {#feature-status-text-table-and-image-editors}

Dies ist eine Liste der Funktionen der Text-, Tabellen- und Bild-Editoren der klassischen Benutzeroberfläche sowie deren Status in der Touch-optimierten Benutzeroberfläche.

| Funktion | Status | Kommentar |
|--- |--- |--- |
| Rich-Text-Editor | Umfassend | Verwendbar im Kontext, im Dialogfeld und im Vollbildmodus. |
| RTE-Plug-ins aktivieren/deaktivieren | Umfassend | Kann mithilfe des [Vorlageneditors](/help/sites-authoring/templates.md) erledigt werden. |
| RTE für Nur-Text verwenden | Umfassend |  |
| RTE-Plug-in: Links und Anker | Umfassend |  |
| RTE-Plug-in: Zeichenzuordnung | Umfassend |  |
| RTE-Plug-in: Kopieren/Einfügen | Umfassend |  |
| RTE-Plug-in: Aus Microsoft® Word einfügen | Umfassend |  |
| RTE-Plug-in: Suchen und Ersetzen | Umfassend |  |
| RTE-Plug-in: Textformate (fett, ...) | Umfassend |  |
| RTE-Plug-in: Tiefgestellt und hochgestellt | Umfassend |  |
| RTE-Plug-in: Blocksatz | Umfassend |  |
| RTE-Plug-in: Listen (Aufzählungszeichen/Zahlen) | Umfassend |  |
| RTE-Plug-in: Absatzformat | Umfassend |  |
| RTE-Plug-in: Textstile | Umfassend |  |
| RTE-Plug-in: Quell-Editor (HTML bearbeiten) | Umfassend | Nur im Dialogfeld und im Vollbildmodus verfügbar. |
| RTE-Plug-in: Rechtschreibprüfung | Umfassend |  |
| RTE-Plug-in: Tabelle (eingebetteter Tabellen-Editor) | Umfassend |  |
| RTE-Plug-in: Rückgängig/Wiederherstellen | Umfassend |  |
| RTE-Plug-in: Inline-Bilder zulassen | Umfassend |  |
| Tabelleneditor | Umfassend | Verwendbar im Kontext, im Dialogfeld und im Vollbildmodus. |
| Bild in Tabellenzelle ziehen | Umfassend | In-line-Funktion |
| Bildeditor | Umfassend | Verwendbar im Kontext, im Dialogfeld und im Vollbildmodus. |
| IPE-Plug-ins aktivieren/deaktivieren | Umfassend | Mit AEM 6.3 wurde eine Benutzeroberfläche im [Vorlagen-Editor](/help/sites-authoring/templates.md) eingeführt. |
| IPE-Plug-in: Zuschneiden | Umfassend |  |
| IPE-Plug-in: Spiegeln | Umfassend |  |
| IPE-Plug-in: Rückgängig/Wiederherstellen | Umfassend |  |
| IPE-Plug-in: Imagemap | Umfassend |  |
| IPE-Plug-in: Drehen | Umfassend |  |
| IPE-Plug-in: Zoomen | Umfassend |  |

## Funktionsstatus: Werkzeuge {#feature-status-tools}

Dies ist eine Liste diverser Tools der klassischen Benutzeroberfläche sowie deren Status in der Touch-optimierten Benutzeroberfläche.

| Funktion | Status | Kommentar |
|--- |--- |--- |
| Aufgabenverwaltung | Ersetzt | In 6.0 wurden Projekte und Aufgaben eingeführt. |
| Posteingangs-Workflow | Umfassend |  |
| Konfiguration der Workflow-zu-Seite-Vorlage (`/etc/workflow/wcm/templates.html`) | Fehlt | Verwenden Sie die klassische Benutzeroberfläche. |
| Tagging der Admin-Benutzeroberfläche | Umfassend |  |
| MSM/Blueprint-Steuerungszentrale | Umfassend |  |
| Blueprint-Manager-Benutzeroberfläche | Umfassend |  |
| Benutzeroberfläche für Rollout-Konfiguration | Fehlt | Verwenden Sie die klassische Benutzeroberfläche. |
| Benutzeroberfläche für Benutzende, Gruppen und Berechtigungen | Nahezu umfassend | Verwenden Sie die klassische Benutzeroberfläche für die erweiterte Bearbeitung von Berechtigungen. |
| Versionen bereinigen (`/etc/versioning/purge.html`) | Fehlt | Verwenden Sie die klassische Benutzeroberfläche. |
| Prüfer für externe Links (`/etc/linkchecker.html`) | Fehlt | Verwenden Sie die klassische Benutzeroberfläche. |
| Bulk Editor (`/etc/importers/bulkeditor.html`) | Fehlt | Verwenden Sie die klassische Benutzeroberfläche. |
| Hochladen von Miniaturansichten zum Hinzufügen oder Überschreiben dieser Miniaturansichten | Fehlt | Verwenden Sie die klassische Benutzeroberfläche. |
