---
title: Ausführen von AEM Forms im Wartungsmodus
description: Der Wartungsmodus ist nützlich, wenn Aufgaben wie das Patchen eines DSC, das Aktualisieren AEM Formulare oder das Anwenden eines Service Packs ausgeführt werden. Erfahren Sie mehr über das Ausführen AEM Formulare im Wartungsmodus.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 6f5ce18b-26b4-4c31-b48a-43ccbb3912f6
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 8%

---

# Ausführen von AEM Forms im Wartungsmodus {#running-aem-forms-in-maintenance-mode}

Der Wartungsmodus ist nützlich, wenn Aufgaben wie das Patchen eines DSC, das Aktualisieren AEM Formulare oder das Anwenden eines Service Packs ausgeführt werden.

Vermeiden Sie das Aufrufen von Prozessen, während sich der Server im Wartungsmodus befindet. Dies geschieht, wenn ein Prozess aufgerufen wird, während sich der Server im Wartungsmodus befindet:

* Wenn der Prozess langlebig ist, wird er der Auftragsdatenbank hinzugefügt, aber nicht gestartet. Wenn Sie den Wartungsmodus beenden, verarbeitet AEM Forms die Aufträge mit langer Lebensdauer in der Warteschlange, auch wenn der Server im Wartungsmodus neu gestartet wurde.
* Wenn der Prozess kurzlebig ist, wird er sofort verarbeitet.

**AEM in den Wartungsmodus versetzen**

1. Geben Sie in einem Webbrowser Folgendes ein:

   `https://[hostname]:[port]/dsc/servlet/DSCStartupServlet?maintenanceMode=pause&user=[administrator username]&password=[password]`

   Im Browserfenster wird die Meldung &quot;Jetzt angehalten&quot; angezeigt.

   >[!NOTE]
   >
   >Wenn Sie den Server herunterfahren, während er sich im Wartungsmodus befindet, befindet er sich beim Neustart noch im Wartungsmodus. Deaktivieren Sie den Wartungsmodus, wenn Sie Ihre Wartungsaufgaben abgeschlossen haben.

**Überprüfen, ob AEM Formulare im Wartungsmodus ausgeführt werden**

1. Geben Sie in einem Webbrowser Folgendes ein:

   `https://[hostname]:[port]/dsc/servlet/DSCStartupServlet?maintenanceMode=isPaused&user=[administrator username]&password=[password]`

   Der Status wird im Browserfenster angezeigt. Der Status &quot;true&quot;zeigt an, dass der Server im Wartungsmodus ausgeführt wird, und &quot;false&quot;zeigt an, dass sich der Server nicht im Wartungsmodus befindet.

**Wartungsmodus deaktivieren**

1. Geben Sie in einem Webbrowser Folgendes ein:

   `https://[hostname]:[port]/dsc/servlet/DSCStartupServlet?maintenanceMode=resume&user=[administrator username]&password=[password]`

   Die Meldung „Wird ausgeführt“ wird im Browserfenster angezeigt.
