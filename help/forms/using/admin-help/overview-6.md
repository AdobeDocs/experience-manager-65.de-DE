---
title: Überblick über die Konfiguration von SSL
description: Erfahren Sie, wie Sie die Kommunikationssicherheit durch die Konfiguration von SSL verbessern können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: fbe1487e-c830-4be8-9841-6022e6a98ae7
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 3%

---

# Überblick über die Konfiguration von SSL {#overview-of-configuring-ssl}

Sie können SSL-Anmeldedaten (Secure Sockets Layer) erstellen und SSL auf dem Anwendungsserver konfigurieren, um die Sicherheit der Kommunikation mit Ihrem Anwendungsserver zu erhöhen.

Als Sicherheitsprodukt erfordert Rights Management die Konfiguration von SSL. Stellen Sie beim Konfigurieren von SSL-Zertifikaten sicher, dass Sie nur RSA-Schlüssel verwenden. SSL-Zertifikate mit DSA-Schlüsseln werden nicht unterstützt.

Die bereitgestellten Informationen gelten für Turnkey-, Automatisch- und manuelle Installationen. Es bietet ein Beispiel für eine Methode zur Konfiguration von SSL. Sie können auch andere Methoden verwenden, die für Ihr Netzwerk oder Ihre Organisation besser geeignet sind.

>[!NOTE]
>
>Es wird empfohlen, die Installation, Konfiguration und Bereitstellung Ihrer AEM Formularmodule abzuschließen und sicherzustellen, dass die Produkte ordnungsgemäß ausgeführt werden, bevor Sie SSL auf dem Anwendungsserver konfigurieren.

>[!NOTE]
>
>Verwenden Sie beim Erstellen von SSL-Sicherheitszertifikaten und -berechtigungen dieselben Benutzerkontoberechtigungen wie beim Ausführen des Anwendungsservers. Wenn der Anwendungsserver mit anderen Benutzerberechtigungen ausgeführt wird, wird das Formular für PDFForm-Ausgabeformate möglicherweise nicht ordnungsgemäß wiedergegeben, wenn der ContentRootURI auf HTTPS verweist.

Wenn Sie über einen SSL-aktivierten LDAP-Server verfügen, konfigurieren Sie User Management für die Verwendung mit diesem Server. (Siehe [User Management für einen SSL-aktivierten LDAP-Server konfigurieren](/help/forms/using/admin-help/configure-user-management-ssl-enabled.md#configure-user-management-for-an-ssl-enabled-ldap-server).
