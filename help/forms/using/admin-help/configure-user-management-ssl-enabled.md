---
title: User Management für einen SSL-aktivierten LDAP-Server konfigurieren
description: Erfahren Sie, wie Sie User Management für einen SSL-aktivierten LDAP-Server konfigurieren, damit die Synchronisierung aktiviert wird, um Über LDAPS ordnungsgemäß zu funktionieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 606e84f2-6728-47a9-a439-dbe2e55100ad
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 30%

---

# Konfigurieren der Benutzerverwaltung für einen SSL-aktivierten LDAP-Server {#configure-user-management-for-an-ssl-enabled-ldap-server}

Damit die Synchronisierung über LDAPS ordnungsgemäß funktioniert, müssen die von der Zertifizierungsstelle ausgestellten LDAP-Zertifikate in der Java Runtime Environment (JRE) des Anwendungsservers vorhanden sein. Importieren Sie das Zertifikat in die Datei „cacerts“ des Anwendungsservers, die sich in der Regel im Ordner „*[JAVA_HOME]*/jre/lib/security/cacerts“ befindet.

1. Aktivieren Sie SSL auf dem Ordnerserver. Weitere Informationen finden Sie in der Dokumentation Ihres Ordneranbieters.
1. Exportieren Sie ein Clientzertifikat vom Ordnerserver.
1. Verwenden Sie das Programm keytool , um die Datei mit dem Clientzertifikat in den standardmäßigen JVM™-Zertifikatspeicher (Java Virtual Machine™) des AEM Forms-Anwendungsservers zu importieren. Das Verfahren für diese Aufgabe variiert je nach JVM- und Client-Installationspfaden. Wenn Sie beispielsweise BEA WebLogic Server mit JDK 1.5 verwenden, geben Sie an einer Eingabeaufforderung den folgenden Text ein:

   `keytool -import -alias`*alias* `-file certificatename -keystore C:\bea\jdk15_04\jre\lib\security\cacerts`

1. Geben Sie auf Anforderung das Kennwort ein. (Für Java lautet das Standardkennwort `changeit`.) In einer Meldung wird angezeigt, dass das Zertifikat erfolgreich importiert wurde.
1. Geben Sie nach Aufforderung `Yes` ein, um das Zertifikat als vertrauenswürdig festzulegen.
1. Aktivieren Sie SSL in User Management, wählen Sie bei der Konfiguration der Ordnereinstellungen für die SSL-Option Ja aus und ändern Sie die Anschlusseinstellung entsprechend. Die Standardportnummer ist 636.

>[!NOTE]
>
>Wenn bei der Verwendung von SSL Probleme auftreten, verwenden Sie einen LDAP-Browser, um zu überprüfen, ob er bei Verwendung von SSL auf das LDAP-System zugreifen kann. Wenn der LDAP-Browser keinen Zugriff erhalten kann, ist Ihr Zertifikat oder Ihr Anwendungsserver nicht ordnungsgemäß konfiguriert. Wenn der LDAP-Browser ordnungsgemäß funktioniert und weiterhin Probleme auftreten, ist User Management nicht ordnungsgemäß konfiguriert.
