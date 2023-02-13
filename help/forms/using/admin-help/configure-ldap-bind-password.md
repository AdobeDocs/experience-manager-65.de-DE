---
title: Konfigurieren des LDAP-Bindungskennworts
seo-title: Configure the LDAP bind password
description: Erfahren Sie, wie Sie das Feld für das Bindungskennwort konfigurieren, bevor Sie die Konfigurationsdatei in ein anderes System importieren.
seo-description: Learn how to configure the bind password field before you import the configuration file into another system.
uuid: 1ab1907c-8b55-4b6f-bd5b-49f22d78b8a8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 165b3950-b03f-4848-8361-ffb0a26d2658
exl-id: c72794f5-8767-409e-a1df-91a8fdc54d18
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '183'
ht-degree: 100%

---

# Konfigurieren des LDAP-Bindungskennworts{#configure-the-ldap-bind-password}

Um Sicherheitsrisiken zu vermeiden, ist das Feld für das Bindungskennwort in der exportierten Konfigurationsdatei („config.xml“) nicht konfiguriert. Konfigurieren Sie dieses Kennwort unbedingt, bevor Sie die Konfigurationsdatei in ein anderes System importieren. Dieses Kennwort setzt ein bestehendes, in der Datenbank gespeichertes Kennwort außer Kraft. Ein Null-Kennwort setzt einen vorhandenen Nicht-Null-Kennwortwert nicht außer Kraft.

1. Klicken Sie in der Administration-Console auf „Einstellungen“ > „Benutzerverwaltung“ > „Konfiguration“ > „Konfigurationsdateien importieren und exportieren“.
1. Um die aktuellen Konfigurationseinstellungen in eine Datei zu exportieren, klicken Sie auf „Exportieren“ und speichern die Konfigurationsdatei an einem anderen Speicherort.
1. Suchen Sie in der Datei den Knoten `Domains` > *[Ihr Domain-Name]* > `DirectoryConfigs` > `LDAPGroupConfig`. Beispiel:

   ```xml
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

1. Suchen Sie in der Datei den Knoten `Domains` > *[Ihr Domain-Name]* > `DirectoryConfigs` > `LDAPGroupConfig` > `LDAPUserConfig`. Beispiel:

   ```xml
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

1. Um die aktualisierte Datei zu importieren, klicken Sie in „Benutzerverwaltung“ auf „Konfiguration“ > „Konfigurationsdateien importieren und exportieren“.
1. Klicken Sie auf „Durchsuchen“, um die Datei zu suchen, dann auf „Importieren“ und anschließend auf „OK“.
