---
title: Bereinigen von Prozessdaten
description: Prozessdaten, die beim Aufrufen eines langlebigen Prozesses generiert werden, können zu groß werden, was zu einer geringeren AEM der Formularleistung und zur Verwendung unnötigen Festplattenspeichers führt. Erfahren Sie, wie Sie Prozessdaten bereinigen können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 0da59dbe-f050-4ee5-b74c-4380b3543b97
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 3%

---

# Bereinigen von Prozessdaten {#purging-process-data}

Prozessdaten, die beim Aufrufen eines langlebigen Prozesses generiert werden, können zu groß werden, was zu einer geringeren AEM der Formularleistung und zur Verwendung unnötigen Festplattenspeichers führt. Es empfiehlt sich, Prozessdaten zu bereinigen, wenn Datensätze nicht mehr benötigt werden. AEM Formulare bieten mehrere Möglichkeiten, Prozessdaten zu bereinigen:

* Sie können Administration Console verwenden, um eine einmalige Bereinigung veralteter Datensätze im Zusammenhang mit langlebigen Prozessen durchzuführen oder regelmäßige automatische Bereinigungen zu planen. (Siehe [Job Manager-Datenbank um Datensätze bereinigen](/help/forms/using/admin-help/purge-records-job-manager-database.md#purge-records-from-the-job-manager-database).
* Sie können die Java-API und Webdienst-API von AEM Forms verwenden, um Prozessdaten im Zusammenhang mit langlebigen Prozessen programmgesteuert zu bereinigen. (Siehe &quot;Bereinigen von Prozessdaten&quot;in [Programmieren mit AEM](https://www.adobe.com/go/learn_aemforms_programming_63_de).
* Verwenden Sie das Tool zur Prozessbereinigung, um Prozesse basierend auf dem Prozessnamen und anderen Parametern zu bereinigen. Weitere Informationen finden Sie in der Datei &quot;Bitte lesen&quot;des Prozessbereinigungs-Tools unter *[aem_forms-Stamm]*\sdk\misc\Foundation\ProcessPurgeTool\ReadMe.txt
