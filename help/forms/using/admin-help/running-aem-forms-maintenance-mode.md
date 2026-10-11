---
title: Ausführen von AEM Forms im Wartungsmodus
description: Der Wartungsmodus bietet sich beim Ausführen von Aufgaben wie dem Hinzufügen von Patches zu DSC, dem Aktualisieren von AEM Forms oder dem Anwenden eines Service Packs an. Erfahren Sie mehr über die Ausführung von AEM Forms im Wartungsmodus.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 6f5ce18b-26b4-4c31-b48a-43ccbb3912f6
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
source-wordcount: '259'
ht-degree: 100%
---
# Ausführen von AEM Forms im Wartungsmodus {#running-aem-forms-in-maintenance-mode}

Der Wartungsmodus bietet sich beim Ausführen von Aufgaben wie dem Hinzufügen von Patches zu DSC, dem Aktualisieren von AEM Forms oder dem Anwenden eines Service Packs an.

Vermeiden Sie das Aufrufen von Prozessen, während sich der Server im Wartungsmodus befindet. Folgendes erfolgt, wenn ein Prozess aufgerufen wird, während sich der Server im Wartungsmodus befindet:

* Wenn der Prozess langlebig ist, wird er der Auftragsdatenbank hinzugefügt, aber nicht gestartet. Wenn Sie den Wartungsmodus beenden, verarbeitet AEM Forms die langlebigen Aufträge in der Warteschlange, auch wenn der Server im Wartungsmodus neu gestartet wurde.
* Wenn der Prozess kurzlebig ist, wird er sofort verarbeitet.

**AEM Forms in den Wartungsmodus versetzen**

1. Geben Sie in einem Webbrowser Folgendes ein:

   `https://[hostname]:[port]/dsc/servlet/DSCStartupServlet?maintenanceMode=pause&user=[administrator username]&password=[password]`

   Die Meldung „Jetzt angehalten“ wird im Browser-Fenster angezeigt.

   >[!NOTE]
   >
   >Wenn Sie den Server herunterfahren, während er sich im Wartungsmodus befindet, befindet er sich beim Neustart weiterhin im Wartungsmodus. Deaktivieren Sie den Wartungsmodus, wenn Sie Ihre Wartungsaufgaben abgeschlossen haben.

**Überprüfen, ob AEM Forms im Wartungsmodus ausgeführt wird**

1. Geben Sie in einem Webbrowser Folgendes ein:

   `https://[hostname]:[port]/dsc/servlet/DSCStartupServlet?maintenanceMode=isPaused&user=[administrator username]&password=[password]`

   Der Status wird im Browser-Fenster angezeigt. Der Status „true“ zeigt an, dass der Server im Wartungsmodus ausgeführt wird, und „false“ zeigt an, dass sich der Server nicht im Wartungsmodus befindet.

**Wartungsmodus deaktivieren**

1. Geben Sie in einem Webbrowser Folgendes ein:

   `https://[hostname]:[port]/dsc/servlet/DSCStartupServlet?maintenanceMode=resume&user=[administrator username]&password=[password]`

   Die Meldung „Wird ausgeführt“ wird im Browserfenster angezeigt.
