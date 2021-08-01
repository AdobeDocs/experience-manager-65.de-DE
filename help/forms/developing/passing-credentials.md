---
title: Wie übergebe ich Anmeldeinformationen mit WS-Security-Headern?
description: Erfahren Sie, wie Sie Anmeldeinformationen mithilfe von WS-Sicherheitskopfzeilen übergeben.
source-git-commit: 9b118ef4f852e3df1e717bb27b9be272caeb0456
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# Übergeben von Anmeldeinformationen mithilfe von WS-Security-Headern {#using-execute-script-service-aem-forms-jee-workbench}

Beim Aufrufen eines AEM Forms on JEE-Diensts mithilfe von Webdiensten können Sie WS-Sicherheitskopfzeilen verwenden, um für AEM Forms on JEE erforderliche Client-Authentifizierungsinformationen zu übergeben. WS-Security definiert SOAP-Erweiterungen zur Implementierung von Client-Authentifizierung, Vertraulichkeit von Nachrichten und Nachrichtenintegrität. Daher können Sie AEM Forms on JEE-Dienste aufrufen, wenn AEM Forms on JEE als eigenständiger Server oder in einer Clusterumgebung bereitgestellt wird.

Wie Sie WS-Security-Header an AEM Forms on JEE übergeben, hängt davon ab, ob Sie Axis-generierte Java-Klassen oder eine .NET-Client-Assembly verwenden, die den nativen SOAP-Stapel eines Dienstes verbraucht.

>[!NOTE]
>
>Als Beispiel für das Aufrufen eines Dienstes mithilfe von WS-Security-Headern verschlüsselt dieses Thema ein PDF-Dokument mit einem Kennwort, indem der Encryption-Dienst aufgerufen wird.

Dieses Dokument behandelt die folgenden Themen:

* Übergeben der Client-Authentifizierung mit Axis-generierten Java-Klassen

* Generieren von Bibliotheksdateien für Achsen zum Aufrufen des Encryption-Dienstes

* Aufrufen des Encryption-Dienstes mithilfe eines WS-Security-Headers

* Übergeben der Clientauthentifizierung mit einer .NET-Client-Assembly

* Aufrufen des Encryption-Dienstes mithilfe eines WS-Security-Headers


## Voraussetzungen {#requirements}

Um dieses Dokument optimal nutzen zu können, benötigen Sie ein fundiertes Verständnis der AEM Forms on JEE-Software.

>[!MORELIKETHIS]
>
>* [Übergeben von Anmeldeinformationen mithilfe von WS-Security-Headern](assets/passing-credentials-using-ws-security-headers.pdf)


