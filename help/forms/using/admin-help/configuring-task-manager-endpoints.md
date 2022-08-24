---
title: Task Manager-Endpunkte konfigurieren
seo-title: Configuring Task Manager endpoints
description: Erfahren Sie, wie Sie Task Manager-Endpunkte konfigurieren.
seo-description: Learn how to configure Task Manager endpoints.
uuid: 07604b10-0bd7-4bce-9624-7ebac4754f56
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 9c55feb9-23d8-4798-a3c5-70ec736df3ad
exl-id: 8495a3d7-6ac9-41f5-b1f9-31decaba118a
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 100%

---

# Task Manager-Endpunkte konfigurieren {#configuring-task-manager-endpoints}

Task Manager-Endpunkte ermöglichen es einem Workspace-Benutzer, den Dienst aufzurufen.

**TaskManager-Endpunkteinstellungen**

Mithilfe der folgenden Einstellungen können Sie einen TaskManager-Endpunkt konfigurieren.

**Name:** (Obligatorisch) Identifiziert den Endpunkt. Der Name wird in Workspace in der Kartenansicht angezeigt. Der Name darf kein &lt;-Zeichen enthalten, weil dadurch die Anzeige des Namens in Workspace abgeschnitten wird. Wenn Sie eine URL als Name des Endpunktes angeben, vergewissern Sie sich, dass sie den in RFC1738 angegebenen Syntaxregeln entspricht.

**Beschreibung**: Eine Beschreibung des Endpunkts. Der Name darf kein &lt;-Zeichen enthalten, weil dadurch die Anzeige des Namens in Workspace abgeschnitten wird.

**Aufgabenanweisungen:** Anweisungen für den Benutzer, der diesen Workflow startet.

**Prozesseigentümer:** Der Name der für den Prozess verantwortlichen Person.

**Benutzer kann Aufgabe weiterleiten:** Ermöglicht dem Benutzer die Weiterleitung der ursprünglichen Aufgabe.

**Anlagenfenster anzeigen:** Ermöglicht dem Benutzer, das Anlagenfenster zu sehen.

**Hinzufügen von Anhängen zulassen:** Ermöglicht dem Benutzer das Hinzufügen von Anlagen und Notizen.

**Aufgabe ursprünglich gesperrt:** Sperrt die ursprüngliche Aufgabe.

**ACLs für freigegebene Warteschlangen hinzufügen:** Die ursprüngliche Aufgabe wird mit ACLs für Benutzer freigegebener Warteschlangen erstellt.

**Kategorsierung:** (Obligatorisch) Die Kategorie, in der das Formular in Workspace dem Benutzer angezeigt wird. Wählen Sie eine Kategorie aus der Liste aus oder wählen Sie „Neue Kategorie“, um eine Kategorie hinzuzufügen.

**Vorgangsname:** (Obligatorisch) Eine Liste von Vorgängen, die dem Endpunkt zugewiesen werden können.
