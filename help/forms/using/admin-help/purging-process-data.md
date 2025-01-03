---
title: Bereinigen von Prozessdaten
description: Prozessdaten, die beim Aufrufen eines Prozesses mit langer Lebensdauer generiert werden, können zu stark anwachsen, was zu einer Beeinträchtigung der Leistung von AEM Forms und zur unnötigen Belegung von Speicherplatz führt.  Erfahren Sie, wie Sie Prozessdaten bereinigen können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 0da59dbe-f050-4ee5-b74c-4380b3543b97
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 100%

---

# Bereinigen von Prozessdaten {#purging-process-data}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Administratorberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Prozessdaten, die beim Aufrufen eines Prozesses mit langer Lebensdauer generiert werden, können zu stark anwachsen, was zu einer Beeinträchtigung der Leistung von AEM Forms und zur unnötigen Belegung von Speicherplatz führt.  Es ist empfehlenswert, Prozessdaten zu bereinigen, wenn die Einträge nicht mehr benötigt werden.  AEM Forms bietet mehrere Möglichkeiten, Prozessdaten zu bereinigen:

* Sie können die Administrationskonsole verwenden, um eine einmalige Bereinigung von veralteten Einträgen im Zusammenhang mit dauerhaft genutzten Prozessen auszuführen oder regelmäßige automatische Bereinigungen zu planen. (Weitere Informationen finden Sie unter [Bereinigen von Einträgen in der Job Manager-Datenbank](/help/forms/using/admin-help/purge-records-job-manager-database.md#purge-records-from-the-job-manager-database).)
* Sie können die AEM Forms Java-API und die Webservice-API verwenden, um Prozessdaten im Zusammenhang mit dauerhaft genutzten Prozessen programmgesteuert zu bereinigen.  (Siehe „Bereinigen von Prozessdaten“ in [Programmieren mit AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63_de).)
* Verwenden Sie das Prozessbereinigungswerkzeug zum Bereinigen von Prozessen anhand des Prozessnamens und anderer Parameter.  Weitere Informationen finden Sie in der Datei „Bitte lesen“ zum Prozessbereinigungswerkzeug, die sich unter „*[aem_forms root]*\sdk\misc\Foundation\ProcessPurgeTool\ReadMe.txt“ befindet.
