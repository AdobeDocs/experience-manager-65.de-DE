---
title: Übergeben von Anmeldeinformationen mithilfe von WS-Security-Kopfzeilen
description: Erfahren Sie, wie Sie Berechtigungen mithilfe von WS-Security-Headern übergeben.
exl-id: 519d57ad-81ab-4caf-ae25-4390ae2eee13
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Security
role: User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 50158d81-1c06-57f7-8bd7-e8ff76a93f85
    internal-label: Document Security
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
source-wordcount: '228'
ht-degree: 100%
---
# Übergeben von Anmeldeinformationen mithilfe von WS-Security-Kopfzeilen {#using-execute-script-service-aem-forms-jee-workbench}

Beim Aufrufen eines AEM Forms on JEE-Service mithilfe von Webservices können Sie WS-Security-Kopfzeilen verwenden, um die für AEM Forms on JEE erforderlichen Client-Authentifizierungsinformationen zu übergeben. WS-Security definiert SOAP-Erweiterungen zur Implementierung von Client-Authentifizierung, Vertraulichkeit von Nachrichten und Nachrichtenintegrität. Daher können Sie AEM Forms on JEE-Services aufrufen, wenn AEM Forms on JEE als eigenständiger Server oder in einer Cluster-Umgebung bereitgestellt wird.

Wie Sie WS-Security-Kopfzeilen an AEM Forms on JEE übergeben, hängt davon ab, ob Sie Axis-generierte Java-Klassen oder eine .NET-Client-Assembly verwenden, die den nativen SOAP-Stapel eines Service nutzt.

>[!NOTE]
>
>Als Beispiel für das Aufrufen eines Service mithilfe von WS-Security-Kopfzeilen wird in diesem Thema ein PDF-Dokument mit einem Kennwort verschlüsselt, indem der Verschlüsselungs-Service aufgerufen wird.

In diesem Dokument werden folgende Themen behandelt:

* Übergeben der Client-Authentifizierung mit Axis-generierten Java-Klassen

* Generieren von Axis-Bibliotheksdateien zum Aufrufen des Verschlüsselungs-Service

* Aufrufen des Verschlüsselungs-Service mithilfe einer WS-Security-Kopfzeile

* Übergeben der Client-Authentifizierung mit einer .NET-Client-Assembly

* Aufrufen des Verschlüsselungs-Service mithilfe einer WS-Security-Kopfzeile


## Voraussetzungen {#requirements}

Um dieses Dokument optimal nutzen zu können, benötigen Sie ein solides Verständnis der AEM Forms auf JEE-Software.

>[!MORELIKETHIS]
>
>* [Übergeben von Anmeldeinformationen mithilfe von WS-Security-Kopfzeilen](assets/passing-credentials-using-ws-security-headers.pdf)
