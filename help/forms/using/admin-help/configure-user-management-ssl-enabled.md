---
title: User Management für einen SSL-aktivierten LDAP-Server konfigurieren
description: Erfahren Sie, wie Sie User Management für einen SSL-aktivierten LDAP-Server konfigurieren, damit die Synchronisierung aktiviert wird, um Über LDAPS ordnungsgemäß zu funktionieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 606e84f2-6728-47a9-a439-dbe2e55100ad
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 100%

---

# Konfigurieren der Benutzerverwaltung für einen SSL-aktivierten LDAP-Server {#configure-user-management-for-an-ssl-enabled-ldap-server}

Damit die Synchronisierung ordnungsgemäß über LDAPS erfolgen kann, müssen die von einer Zertifizierungsstelle ausgestellten LDAP-Zertifikate in der JRE-Umgebung (Java Runtime Environment) des Anwendungs-Servers vorhanden sein. Importieren Sie das Zertifikat in die Datei „cacerts“ des Anwendungsservers, die sich in der Regel im Ordner „*[JAVA_HOME]*/jre/lib/security/cacerts“ befindet.

1. Aktivieren Sie SSL auf dem Verzeichnis-Server. Weitere Informationen finden Sie in der Dokumentation des Verzeichnisanbieters.
1. Exportieren Sie ein Client-Zertifikat vom Verzeichnisserver.
1. Verwenden Sie das Programm Keytool, um die Datei mit dem Clientzertifikat in den standardmäßigen JVM-Zertifikatspeicher (Java Virtual Machine™) des AEM Forms-Anwendungs-Servers zu importieren. Das hierfür verwendete Verfahren ist von den Installationspfaden für JVM und Client abhängig. Wenn Sie z. B. BEA WebLogic Server mit JDK 1.5 verwenden, geben Sie über eine Eingabeaufforderung Folgendes ein:

   `keytool -import -alias`*alias* `-file certificatename -keystore C:\bea\jdk15_04\jre\lib\security\cacerts`

1. Geben Sie auf Anforderung das Kennwort ein. (Für Java lautet das Standardkennwort `changeit`.) In einer Meldung wird angezeigt, dass das Zertifikat erfolgreich importiert wurde.
1. Geben Sie nach Aufforderung `Yes` ein, um das Zertifikat als vertrauenswürdig festzulegen.
1. Aktivieren Sie SSL in User Management, wählen Sie beim Konfigurieren der Verzeichniseinstellungen für die SLL-Option die Einstellung „Ja“ und ändern Sie die Port-Einstellung entsprechend. Die Standardportzahl ist 636.

>[!NOTE]
>
>Falls beim Einsatz von SSL Probleme auftreten, verwenden Sie einen LDAP-Browser, um zu überprüfen, ob dieser bei Verwendung von SSL auf das LDAP-System zugreifen kann. Ist der Zugriff durch den LDAP-Browser nicht möglich, ist Ihr Zertifikat oder Ihr Anwendungs-Server nicht ordnungsgemäß konfiguriert. Wenn der LDAP-Browser ordnungsgemäß funktioniert und dennoch Probleme auftreten, ist User Management nicht richtig konfiguriert.
