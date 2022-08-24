---
title: Konfigurieren von Acrobat Reader DC Extensions für die Datenerfassung
seo-title: Configuring Acrobat Reader DC extensions for data capture
description: Erfahren Sie, wie Sie Acrobat Reader DC-Erweiterungen für Datenerfassung konfigurieren.
seo-description: Learn how to configure Acrobat Reader DC extensions for data capture.
uuid: af6b3c72-601e-4f54-8343-a323eeee5906
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 8f8367fe-a8e9-46ee-a980-1633be02932d
exl-id: 0f8e1e46-4fc5-43f6-abb1-19a3f20e1f1d
source-git-commit: 0c7dba43dad8608b4a5de271e1e44942c950fb16
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 100%

---

# Konfigurieren von Acrobat Reader DC Extensions für die Datenerfassung {#configuring-acrobat-reader-dc-extensions-for-data-capture}

Wenn Benutzer Ihrer AEM Forms-Installation die Datenerfassungsfunktion von Content Services (nicht mehr unterstützt) verwenden, empfiehlt es sich, eine Rolle mit schreibgeschütztem Zugriff für diese Benutzer zu erstellen.

***Hinweis **: Adobe® LiveCycle® Content Services ES (nicht mehr unterstützt) ist ein Content-Management-System, das mit LiveCycle installiert wird. Es ermöglicht es Benutzern, am Menschen orientierte Prozesse zu entwerfen, zu verwalten, zu überwachen und zu optimieren. Die Unterstützung von Content Services (veraltet) endet am 31.12.2014. Weitere Informationen finden Sie unter [Adobe Produkt-Lifecycle-Dokument](https://www.adobe.com/de/support/products/enterprise/eol/eol_matrix.html).*

Für die Datenerfassung ist es erforderlich, dass eine Benutzerrolle für den Zugriff auf „SampleReaderExtensionsCredential“ zugewiesen wird. Sie können die Standardrolle „Vertrauensadministrator“ zuweisen, sollten dabei allerdings bedenken, dass diese Rolle allgemeinen, nicht administrativen Benutzern die umfassenden Administratorberechtigungen gewährt, mit denen die PKI-Vertrauenseinstellungen gesteuert und PKI-Berechtigungen verwaltet werden, wodurch die Sicherheit Ihrer AEM Forms-Installation in einer Produktionsumgebung gefährdet werden kann. Es empfiehlt sich, dass der AEM Forms-Systemadministrator eine Rolle erstellt, die nur schreibgeschützten Zugriff auf den Trust Store gewährt, und diese neue Rolle nicht administrativen Benutzern zuweist, die die Datenerfassung verwenden.

## Neue Rolle für Datenerfassungsbenutzer erstellen {#create-a-role-for-data-capture-users}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Rollenverwaltung“ und dann auf „Neue Rolle“.
1. Geben Sie in den entsprechenden Feldern den Rollennamen (z. B. „Datenerfassungsbenutzer“) und eine Beschreibung ein und klicken Sie dann auf „Weiter“.
1. Klicken Sie im Bildschirm „Rollenberechtigungen“ auf „Berechtigungen suchen“ und wählen Sie dann „Berechtigung lesen“ aus der Liste verfügbarer Berechtigungen aus.
1. Klicken Sie auf „OK“ und dann auf „Fertig stellen“.

## Datenerfassungsrolle zuweisen {#assign-the-data-capture-role}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Rollenverwaltung“ und dann auf „Suchen“.
1. Klicken Sie auf die erstellte Datenerfassungsbenutzerrolle.
1. Klicken Sie auf der Registerkarte „Rollenbenutzer/-gruppen“ auf „Benutzer/Gruppen suchen“.
1. Klicken Sie im Bildschirm „Benutzer/Gruppen suchen“ auf „Suchen“, wählen Sie die Benutzer aus, die die Datenerfassungsbenutzerrolle benötigen, und klicken Sie auf „OK“.
1. Klicken Sie im Bildschirm „Rolle bearbeiten“ auf „Speichern“.
