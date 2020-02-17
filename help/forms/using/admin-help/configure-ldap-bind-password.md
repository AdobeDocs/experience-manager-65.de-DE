---
title: LDAP-Bind-Kennwort konfigurieren
seo-title: LDAP-Bind-Kennwort konfigurieren
description: Erfahren Sie, wie Sie das Feld für das Bindungskennwort konfigurieren, bevor Sie die Konfigurationsdatei in ein anderes System importieren.
seo-description: Erfahren Sie, wie Sie das Feld für das Bindungskennwort konfigurieren, bevor Sie die Konfigurationsdatei in ein anderes System importieren.
uuid: 1ab1907c-8b55-4b6f-bd5b-49f22d78b8a8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 165b3950-b03f-4848-8361-ffb0a26d2658
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# LDAP-Bind-Kennwort konfigurieren{#configure-the-ldap-bind-password}

Um Sicherheitsrisiken zu vermeiden, ist das Feld für das Bindungskennwort in der exportierten Konfigurationsdatei („config.xml“) nicht konfiguriert. Konfigurieren Sie dieses Kennwort unbedingt, bevor Sie die Konfigurationsdatei in ein anderes System importieren. Dieses Kennwort setzt ein bestehendes, in der Datenbank gespeichertes Kennwort außer Kraft. Ein Null-Kennwort setzt einen vorhandenen Nicht-Null-Kennwortwert nicht außer Kraft.

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Konfiguration“ > „Konfigurationsdateien importieren und exportieren“.
1. Um die aktuellen Konfigurationseinstellungen in eine Datei zu exportieren, klicken Sie auf „Exportieren“ und speichern die Konfigurationsdatei an einem anderen Speicherort.
1. In the file, locate the `Domains` > *[Your domain name]* > `DirectoryConfigs` > `LDAPGroupConfig` node. Beispiel:

   ```as3
    <node name="LDAPGroupConfig">
        <map>
            <entry key="bindanonymously" value="false" />
            <entry key="basedn" value="dc=corp,dc=adobe,dc=com" />
            <entry key="batchSize" value="200" />
            <entry key="binduser" value="cn=Directory Manager" />
            <entry key="bindpassword" value="" />
        </map>
   ```

   Geben Sie einen Wert für `bindpassword` ein und speichern Sie die Änderungen.

1. In the file, locate the `Domains` > *[Your domain name]* > `DirectoryConfigs` > `LDAPGroupConfig` > `LDAPUserConfig` node. Beispiel:

   ```as3
    <node name="LDAPUserConfig">
        <map>
            <entry key="bindanonymously" value="false" />
            <entry key="batchSize" value="200" />
            <entry key="basedn" value="dc=corp,dc=adobe,dc=com" />
            <entry key="bindpassword" value="" />
            <entry key="binduser" value="cn=Directory Manager" />
        </map>
   ```

   Geben Sie einen Wert für `bindpassword` ein und speichern Sie die Änderungen.

1. Um die aktualisierte Datei zu importieren, klicken Sie in User Management auf „Konfiguration“ > „Konfigurationsdateien im- und exportieren“.
1. Klicken Sie auf „Durchsuchen“, um die Datei zu suchen, klicken Sie dann auf „Importieren“ und anschließend auf „OK“.

