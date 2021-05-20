---
title: User Management für einen SSL-aktivierten LDAP-Server konfigurieren
seo-title: User Management für einen SSL-aktivierten LDAP-Server konfigurieren
description: Erfahren Sie, wie Sie User Management für einen SSL-aktivierten LDAP-Server konfigurieren, damit die Synchronisierung aktiviert wird, um Über LDAPS ordnungsgemäß zu funktionieren.
seo-description: Erfahren Sie, wie Sie User Management für einen SSL-aktivierten LDAP-Server konfigurieren, damit die Synchronisierung aktiviert wird, um Über LDAPS ordnungsgemäß zu funktionieren.
uuid: 4b3f8ac7-fa38-4adf-a851-82d55fe431fe
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e6e7e2fa-579d-4b36-8598-6ced469a94b1
exl-id: 606e84f2-6728-47a9-a439-dbe2e55100ad
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 90%

---

# User Management für einen SSL-aktivierten LDAP-Server konfigurieren {#configure-user-management-for-an-ssl-enabled-ldap-server}

Damit die Synchronisierung ordnungsgemäß über LDAPS erfolgen kann, müssen die von einer Zertifizierungsstelle ausgestellten LDAP-Zertifikate in der JRE-Umgebung (Java Runtime Environment) des Anwendungsservers vorhanden sein. Importieren Sie das Zertifikat in die Datei &quot;JRE cacerts&quot;des Anwendungsservers, die sich normalerweise im Ordner &quot;*[JAVA_HOME]*/jre/lib/security/cacerts&quot;befindet.

1. Aktivieren Sie SSL auf dem Ordnerserver. Weitere Informationen finden Sie in der Dokumentation des Ordneranbieters.
1. Exportieren Sie ein Clientzertifikat vom Ordnerserver.
1. Verwenden Sie das Programm Keytool, um die Datei mit dem Clientzertifikat in den standardmäßigen JVM-Zertifikatspeicher (Java Virtual Machine™) des AEM Forms-Anwendungsservers zu importieren . Das hierfür verwendete Verfahren ist von den Installationspfaden für JVM und Client abhängig. Wenn Sie z. B. BEA WebLogic Server mit JDK 1.5 verwenden, geben Sie an einer Eingabeaufforderung Folgendes ein:

   `keytool -import -alias`*alias* `-file certificatename -keystore C:\bea\jdk15_04\jre\lib\security\cacerts`

1. Geben Sie auf Anforderung das Kennwort ein. (Für Java lautet das Standardkennwort `changeit`.) In einer Meldung wird angezeigt, dass das Zertifikat erfolgreich importiert wurde.
1. Wenn Sie dazu aufgefordert werden, geben Sie `Yes` ein, um dem Zertifikat zu vertrauen.
1. Aktivieren Sie SSL in User Management, wählen Sie beim Konfigurieren der Ordnereinstellungen für die Option SSL die Einstellung „Ja“ und ändern Sie die Anschlusseinstellung entsprechend. Der Standardanschluss ist 636.

>[!NOTE]
>
>Falls beim Einsatz von SSL Probleme auftreten, verwenden Sie einen beliebigen LDAP-Browser, um zu überprüfen, ob dieser bei Verwendung von SSL auf das LDAP-System zugreifen kann. Ist der Zugriff durch den LDAP-Browser nicht möglich, ist Ihr Zertifikat oder Ihr Anwendungsserver nicht ordnungsgemäß konfiguriert. Wenn der LDAP-Browser ordnungsgemäß funktioniert und dennoch Probleme auftreten, ist User Management nicht richtig konfiguriert.
