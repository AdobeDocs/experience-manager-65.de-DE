---
title: Einstellung der JWT-Anmeldedaten in Adobe Developer Console
description: Weitere Informationen zu den Auswirkungen der Einstellung der JWT-Anmeldedaten in Adobe Developer Console auf AEM
exl-id: f19a92de-ba6a-4f6d-9e12-60ad1bad2e74
solution: Experience Manager, Experience Manager Sites
feature: Security
role: Admin
source-git-commit: 3aa55b88f589749fb49d5ff46340b0912d490157
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 100%

---

# Einstellung der JWT-Anmeldedaten in Adobe Developer Console {#jwt-credentials-deprecation-in-adobe-developer-console}

>[!NOTE]
> Weitere Informationen zu AEM as a Cloud Service finden Sie im [vergleichbaren Artikel für die AEMaaCS-Version](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/jwt-credentials-deprecation-in-adobe-developer-console.html?lang=de).

Mit der [Adobe Developer Console](https://developer.adobe.com/console) können Kundinnen und Kunden von Adobe Anmeldedaten generieren, die den Zugriff auf verschiedene APIs ermöglichen. Dabei können sie unter verschiedenen Anmeldedatentypen wählen, von OAuth Server-zu-Server bis zu Single-Page-App. Einer dieser Anmeldedatentypen, Anmeldedaten für Dienstkonten (JWT), wurde zugunsten der OAuth Server-zu-Server-Anmeldedaten eingestellt. Neue Anmeldedaten für Dienstkonten (JWT) können ab dem 3. Juni 2024 nicht mehr erstellt werden und vorhandene JWT-Anmeldedaten funktionieren ab dem 27. Januar 2025 nicht mehr. [Weitere Information zur Einstellung der JWT-Anmeldedaten finden Sie hier](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/).

Dieser Artikel bietet zusätzliche Informationen dazu, wie Kundinnen und Kunden von Adobe Experience Manager (AEM) 6.5 auf diese Einstellung reagieren sollten.

Die wichtigste Neuerung ist, dass AEM jetzt die neuen OAuth-Server-zu-Server-Anmeldedaten für AEM unterstützt. Möglicherweise haben Sie eine E-Mail mit Anweisungen zum Migrieren Ihrer JWT-Anmeldedaten erhalten. Diese Migration kann jetzt durchgeführt werden.

In den folgenden Abschnitten werden die Szenarien aufgeführt, in denen Kundinnen und Kunden ihre Dienstkonten(JWT)-Anmeldedaten durch OAuth Server-zu-Server-Anmeldedaten ersetzen müssen (oder in einigen Fällen dies nicht tun sollten), jetzt da AEM sie unterstützt. [Hier finden Sie weitere Informationen dazu](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#migration-overview), wie Sie die Anmeldedaten migrieren.

## Integrieren von AEM mit anderen Adobe-Lösungen {#integrating-aem-with-other-adobe-solutions}

**Aktion**: Migrieren Sie Ihre Konfiguration, da AEM jetzt OAuth-Anmeldedaten unterstützt.

**Relevante AEM-Versionen**: Adobe Managed Services (Service Pack 21 und höher).

Kundinnen und Kunden von AEM können AEM verwenden, um Integrationen mit allen anderen Adobe-Lösungen zu konfigurieren. Zum Beispiel Adobe Target, Adobe Analytics und vielen weiteren.

![Integrieren von AEM mit anderen Lösungen](/help/sites-administering/assets/jwt-deprecation.png)

Unter [Einrichten von IMS-Integrationen für AEM](/help/sites-administering/setting-up-ims-integrations-for-aem.md) finden Sie Details zu folgenden Vorgehensweisen:

* Erstellen von Konfigurationen mit OAuth-Anmeldedaten
* Migrieren von Konfigurationen, die mit JWT-Anmeldedaten erstellt wurden, zur Verwendung von OAuth-Anmeldedaten

## Cloud Manager-APIs {#cloud-manager-apis}

**Aktion**: Bestätigen Sie, wann diese von JWT-Anmeldedaten zu OAuth-Anmeldedaten migriert werden können.

**Relevante AEM-Versionen**: Adobe Managed Services (Service Pack 21 und höher).

Kundinnen und Kunden erstellen Adobe Developer Console-Projekte, damit sie die [Cloud Manager-APIs](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/) aufrufen können. Die Anmeldedaten im Adobe Developer-Projekt sollten in den OAuth-Server-zu-Server-Anmeldedatentyp migriert werden, bevor die veralteten JWT-Anmeldedaten im Januar 2025 ablaufen.
