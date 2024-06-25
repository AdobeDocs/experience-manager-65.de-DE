---
title: Überblick über die Konfiguration von SSL
description: Erfahren Sie, wie Sie die Sicherheit der Kommunikation erhöhen, indem Sie SSL konfigurieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: fbe1487e-c830-4be8-9841-6022e6a98ae7
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: ht
source-wordcount: '211'
ht-degree: 100%

---

# Überblick über die Konfiguration von SSL {#overview-of-configuring-ssl}

In diesem Kapitel werden die Erstellung von Secure Sockets Layer(SSL)-Berechtigungen und die Konfiguration von SSL auf dem Anwendungs-Server beschrieben, um die Sicherheit Ihrer Daten bei der Kommunikation mit dem Anwendungs-Server zu erhöhen.

Als Sicherheitsprodukt macht Rights Management die Konfiguration von SSL erforderlich.  Stellen Sie bei der Konfiguration von SSL-Zertifikaten sicher, dass Sie nur RSA-Schlüssel verwenden.  SSL-Zertifikate mit DSA-Schlüsseln werden nicht unterstützt.

Die bereitgestellten Informationen gelten für Turnkey-Installationen sowie für automatische und manuelle Installationen.  Sie finden hier ein Beispiel für eine Methode zum Konfigurieren von SSL.  Sie können auch andere Methoden verwenden, falls diese besser für Ihr Netzwerk oder Unternehmen geeignet sind.

>[!NOTE]
>
>Vor dem Konfigurieren von SSL auf dem Anwendungs-Server sollten Sie die Installation, Konfiguration und Bereitstellung Ihrer AEM Forms-Module durchführen und sicherstellen, dass die Produkte korrekt ausgeführt werden.

>[!NOTE]
>
>Verwenden Sie beim Erstellen von SSL-Sicherheitszertifikaten und -berechtigungen dieselben Benutzerkontoberechtigungen, die Sie zum Ausführen des Anwendungs-Servers verwendet haben. Wird der Anwendungs-Server mit anderen Benutzerberechtigungen ausgeführt, wird das Formular beim Rendern von PDF-Formularen eventuell nicht korrekt gerendert, wenn ContentRootURI auf HTTPS zeigt.

Wenn Sie einen SSL-aktivierten LDAP-Server verwenden, konfigurieren Sie die Benutzerverwaltung dafür. (Siehe [Konfigurieren der Benutzerverwaltung für einen SSL-aktivierten LDAP-Server](/help/forms/using/admin-help/configure-user-management-ssl-enabled.md#configure-user-management-for-an-ssl-enabled-ldap-server).)
