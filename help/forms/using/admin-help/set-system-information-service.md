---
title: Einrichten des Systeminformationsdienstes
description: Erfahren Sie, wie Sie den Systeminformationsdienst einrichten.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/system_information_service
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 734ed463-2441-49fc-bacb-deb40851af42
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
source-wordcount: '114'
ht-degree: 100%
---
# Einrichten des Systeminformationsdienstes {#set-up-the-system-information-service}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Der Systeminformationsdienst stellt REST-APIs zum Abrufen von Informationen bereit. Um den Systeminformationsdienst zu verwenden, aktivieren Sie den REST-Endpunkt über die Administrationskonsole. Führen Sie zum Aktivieren des REST-Endpunktes folgende Schritte durch:

1. Melden Sie sich bei der Administration-Console an. Die Standard-URL von Administration Console lautet `https://[hostname]:'port'/adminui.`
1. Wechseln Sie zu „Dienste“ > „Anwendungen und Dienste“ > „Dienstverwaltung“.
1. Klicken Sie auf der Seite „Dienstverwaltung“ auf den Dienst **SystemInfo**.
1. Wählen Sie auf der Registerkarte „Endpunkte“ die Option „REST“ aus und klicken Sie auf **Hinzufügen**.
1. Klicken Sie auf dem Bildschirm „REST-Endpunkt hinzufügen“ auf **Hinzufügen**.
