---
title: Überblick über die Konfiguration von SSL
seo-title: Überblick über die Konfiguration von SSL
description: Erfahren Sie, wie Sie die Sicherheit der Kommunikation erhöhen, indem Sie SSL konfigurieren.
seo-description: Erfahren Sie, wie Sie die Sicherheit der Kommunikation erhöhen, indem Sie SSL konfigurieren.
uuid: 3e99d2bf-137b-45ba-8384-309624094623
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 8e107abb-861f-4063-b600-c87e34639019
exl-id: fbe1487e-c830-4be8-9841-6022e6a98ae7
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 100%

---

# Überblick über die Konfiguration von SSL {#overview-of-configuring-ssl}

In diesem Kapitel werden die Erstellung von Secure Sockets Layer (SSL)-Berechtigungen und die Konfiguration von SSL auf dem Anwendungsserver beschrieben, um die Sicherheit Ihrer Daten bei der Kommunikation mit dem Anwendungsserver zu erhöhen.

Als Sicherheitsprodukt macht Rights Management die Konfiguration von SSL erforderlich. Stellen Sie bei der Konfiguration von SSL-Zertifikaten sicher, dass Sie nur RSA-Schlüssel verwenden. SSL-Zertifikate mit DSA-Schlüsseln werden nicht unterstützt.

Die bereitgestellten Informationen gelten für Turnkey-Installationen sowie für automatische und manuelle Installationen. Sie finden hier ein Beispiel für eine Methode zum Konfigurieren von SSL. Sie können auch andere Methoden verwenden, falls diese besser für Ihr Netzwerk oder Unternehmen geeignet sind.

>[!NOTE]
>
>Vor dem Konfigurieren von SSL auf dem Anwendungsserver sollten Sie die Installation, Konfiguration und Bereitstellung Ihrer AEM Forms-Module durchführen und sicherstellen, dass die Produkte korrekt ausgeführt werden.

>[!NOTE]
>
>Verwenden Sie beim Erstellen von SSL-Sicherheitszertifikaten und -berechtigungen dieselben Benutzerkontoberechtigungen, die Sie zum Ausführen des Anwendungsservers verwendet haben. Wird der Anwendungsserver mit anderen Benutzerberechtigungen ausgeführt, wird das Formular bei der Wiedergabe von PDF-Formularen eventuell nicht korrekt wiedergegeben, wenn InhaltsStammURI auf HTTPS zeigt.

Wenn Sie einen SSL-aktivierten LDAP-Server verwenden, konfigurieren Sie User Management für die Zusammenarbeit mit dem Server. (Siehe [User Management für einen SSL-aktivierten LDAP-Server konfigurieren](/help/forms/using/admin-help/configure-user-management-ssl-enabled.md#configure-user-management-for-an-ssl-enabled-ldap-server).)
