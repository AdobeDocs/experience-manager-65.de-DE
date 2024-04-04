---
title: Einstellung der JWT-Anmeldedaten in Adobe Developer Console
description: Weitere Informationen zu den Auswirkungen der Einstellung der JWT-Anmeldedaten in Adobe Developer Console auf AEM
exl-id: f19a92de-ba6a-4f6d-9e12-60ad1bad2e74
solution: Experience Manager, Experience Manager Sites
source-git-commit: dec88af3b2345d142d0cc3bc27cfbc27804ab57e
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 53%

---

# Einstellung der JWT-Anmeldedaten in Adobe Developer Console {#jwt-credentials-deprecation-in-adobe-developer-console}

>[!NOTE]
> AEM as a Cloud Service sollte auf [diesem Artikel](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/jwt-credentials-deprecation-in-adobe-developer-console.html) für weitere Informationen.

Mit der [Adobe Developer Console](https://developer.adobe.com/console) können Kundinnen und Kunden von Adobe Anmeldedaten generieren, die den Zugriff auf verschiedene APIs ermöglichen. Dabei können sie unter verschiedenen Anmeldedatentypen wählen, von OAuth Server-zu-Server bis zu Single-Page-App. Einer dieser Anmeldedatentypen, Anmeldedaten für Dienstkonten (JWT), wurde zugunsten der OAuth Server-zu-Server-Anmeldedaten eingestellt. Neue Service Account (JWT)-Anmeldeinformationen können am oder nach dem 3. Juni 2024 nicht erstellt werden und vorhandene JWT-Anmeldeinformationen funktionieren am oder nach dem 27. Januar 2025 nicht mehr. [Weitere Information zur Einstellung der JWT-Anmeldedaten finden Sie hier](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/).

Dieser Artikel bietet einen zusätzlichen Kontext dazu, wie AEM 6.5-Kunden mit der Einstellung umgehen sollten.

Die wichtigste Information ist derzeit, dass AEM-Funktionen die neuen OAuth Server-zu-Server-Anmeldedaten noch nicht unterstützen. Der Support wird bald kommen - bis Ende April 2024 durch ein spezielles Kompatibilitätspaket zu installieren für AEM 6.5, wenn Sie das neueste Service Pack 20 oder niedriger (Service Pack 21 und höher wird es automatisch einschließen). Möglicherweise haben Sie eine E-Mail mit Anweisungen zum Migrieren Ihrer JWT-Anmeldedaten erhalten. Bitte warten Sie jedoch mit der Migration der Anmeldedaten bis AEM den neuen OAuth-Server-zu-Server-Anmeldedatentyp unterstützt.

In den folgenden Abschnitten werden die Szenarien aufgelistet, in denen Kunden ihre JWT-Anmeldeinformationen (Service Account) durch OAuth Server-zu-Server-Anmeldeinformationen ersetzen müssen (oder in einigen Fällen nicht), sobald AEM sie Ende April unterstützt. Weitere Informationen dazu, wie die Anmeldedaten in Zukunft ersetzt werden können, finden Sie [hier](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#migration-overview).

## Integrieren von AEM mit anderen Adobe-Lösungen {#integrating-aem-with-other-adobe-solutions}

**Aktion**: Warten Sie bis zur Migration Ende April 2024, wenn AEM dies unterstützt.

**Relevante AEM**: Adobe Managed Services (Service Pack 20 und höher).


Mit der AEM Author-Benutzeroberfläche können Kundinnen und Kunden von AEM Integrationen mit allen anderen Adobe-Lösungen konfigurieren. Unter anderem Adobe Target, Adobe Analytics, Adobe Launch, AFCS und viele weitere.

![Integrieren von AEM mit anderen Lösungen](/help/sites-administering/assets/jwt-deprecation.png)

Zum Beispiel finden Sie [hier](https://docs.mktossl.com/docs/experience-manager-cloud-service/content/sites/integrations/integration-adobe-target-ims.html?lang=de) die Anweisungen zum Konfigurieren der Integration mit Adobe Target. Der API-Schlüssel im [Abschließen der IMS-Konfiguration in AEM](https://docs.mktossl.com/docs/experience-manager-cloud-service/content/sites/integrations/integration-adobe-target-ims.html?lang=de#completing-the-ims-configuration-in-aem) sollte in den OAuth-Server-zu-Server-Berechtigungstyp migriert werden, sobald AEM diese Anmeldeinformationen Ende April unterstützt. Diese Anweisungen werden Ende April aktualisiert, damit Sie die neuen OAuth Server-zu-Server-Anmeldedaten anwenden können.

## Cloud Manager-APIs {#cloud-manager-apis}

**Aktion**: Warten Sie bis zur Migration Ende April 2024, wenn AEM dies unterstützt.

**Relevante AEM**: Adobe Managed Services (Service Pack 20 und höher).

Kundinnen und Kunden erstellen Adobe Developer Console-Projekte, damit sie die [Cloud Manager-APIs](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/) aufrufen können. Die Anmeldedaten im Adobe Developer-Projekt sollten in den OAuth-Server-zu-Server-Anmeldedatentyp migriert werden, sobald sie von AEM und Cloud Manager unterstützt werden.
