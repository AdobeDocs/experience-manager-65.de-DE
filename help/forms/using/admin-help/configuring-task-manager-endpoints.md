---
title: Konfigurieren der Task Manager-Endpunkte
description: Erfahren Sie, wie Sie Task Manager-Endpunkte konfigurieren, um den Dienst aufzurufen. Zum Konfigurieren von Task Manager-Endpunkten sind verschiedene Einstellungen erforderlich.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 8495a3d7-6ac9-41f5-b1f9-31decaba118a
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 100%
---
# Konfigurieren der Task Manager-Endpunkte {#configuring-task-manager-endpoints}

Task Manager-Endpunkte ermöglichen es Workspace-Benutzenden, den Dienst aufzurufen.

**Task Manager-Endpunkteinstellungen**

Mithilfe der folgenden Einstellungen können Sie einen Task Manager-Endpunkt konfigurieren.

**Name:** (Obligatorisch) Identifiziert den Endpunkt. Der Name wird in Workspace in der Kartenansicht angezeigt. Der Name darf kein &lt;-Zeichen enthalten, weil dadurch die Anzeige des Namens in Workspace abgeschnitten wird. Wenn Sie eine URL als Name des Endpunktes angeben, vergewissern Sie sich, dass sie den in RFC1738 angegebenen Syntaxregeln entspricht.

**Beschreibung:** Eine Beschreibung des Endpunktes. Der Name darf kein &lt;-Zeichen enthalten, weil dadurch die Anzeige des Namens in Workspace abgeschnitten wird.

**Aufgabenanweisungen:** Anweisungen für den Benutzer, der diesen Workflow startet.

**Prozesseigentümer:** Der Name der für den Prozess verantwortlichen Person.

**Benutzer kann Aufgabe weiterleiten:** Ermöglicht dem Benutzer die Weiterleitung der ursprünglichen Aufgabe.

**Anlagenfenster anzeigen:** Ermöglicht dem Benutzer, das Anlagenfenster zu sehen.

**Hinzufügen von Anhängen zulassen:** Ermöglicht dem Benutzer das Hinzufügen von Anlagen und Notizen.

**Aufgabe ursprünglich gesperrt:** Sperrt die ursprüngliche Aufgabe.

**ACLs für freigegebene Warteschlangen hinzufügen:** Die ursprüngliche Aufgabe wird mit ACLs für Benutzer freigegebener Warteschlangen erstellt.

**Kategorsierung:** (Obligatorisch) Die Kategorie, in der das Formular in Workspace dem Benutzer angezeigt wird. Wählen Sie eine Kategorie aus der Liste aus oder wählen Sie „Neue Kategorie“, um eine Kategorie hinzuzufügen.

**Vorgangsname:** (Obligatorisch) Eine Liste von Vorgängen, die dem Endpunkt zugewiesen werden können.
