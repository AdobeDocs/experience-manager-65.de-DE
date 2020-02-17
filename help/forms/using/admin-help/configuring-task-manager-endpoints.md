---
title: Task Manager-Endpunkte konfigurieren
seo-title: Task Manager-Endpunkte konfigurieren
description: Erfahren Sie, wie Sie Task Manager-Endpunkte konfigurieren.
seo-description: Erfahren Sie, wie Sie Task Manager-Endpunkte konfigurieren.
uuid: 07604b10-0bd7-4bce-9624-7ebac4754f56
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 9c55feb9-23d8-4798-a3c5-70ec736df3ad
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Task Manager-Endpunkte konfigurieren {#configuring-task-manager-endpoints}

Task Manager-Endpunkte ermöglichen es einem Workspace-Benutzer, den Dienst aufzurufen.

**TaskManager-Endpunkteinstellungen**

Mithilfe der folgenden Einstellungen können Sie einen TaskManager-Endpunkt konfigurieren.

**** Name: (Obligatorisch) Gibt den Endpunkt an. Der Name wird in Workspace in der Kartenansicht angezeigt. Der Name darf kein &lt;-Zeichen enthalten, weil dadurch die Anzeige des Namens in Workspace abgeschnitten wird. Wenn Sie eine URL als Name des Endpunktes angeben, vergewissern Sie sich, dass sie den in RFC1738 angegebenen Syntaxregeln entspricht.

**** Beschreibung: Eine Beschreibung des Endpunkts. Der Name darf kein &lt;-Zeichen enthalten, weil dadurch die Anzeige des Namens in Workspace abgeschnitten wird.

**** Aufgabenanweisungen: Anweisungen für den Benutzer, der diesen Workflow startet.

**** Prozesseigentümer: Der Name der Person, die für den Prozess verantwortlich ist.

**** Benutzer kann Aufgabe weiterleiten: Ermöglicht dem Benutzer, die ursprüngliche Aufgabe weiterzuleiten.

**** Anlagenfenster anzeigen: Ermöglicht dem Benutzer das Anzeigen des Anlagenfensters.

**** Hinzufügen von Anlagen zulassen: Ermöglicht dem Benutzer, Anlagen und Notizen hinzuzufügen.

**** Aufgabe ursprünglich gesperrt: Sperrt die ursprüngliche Aufgabe.

**** ACLs für freigegebene Warteschlangen hinzufügen: Die ursprüngliche Aufgabe wird mit ACLs für Benutzer freigegebener Warteschlangen erstellt.

**** Kategorisierung: (Obligatorisch) Die Kategorie, in der dem Benutzer das Formular in Workspace angezeigt wird. Wählen Sie eine Kategorie aus der Liste aus oder wählen Sie „Neue Kategorie“, um eine Kategorie hinzuzufügen.

**** Vorgangsname: (Obligatorisch) Eine Liste der Vorgänge, die dem Endpunkt zugewiesen werden können.
