---
title: Konfigurieren von Acrobat Reader DC-Erweiterungen für die Datenerfassung
description: Erfahren Sie, wie Sie Acrobat Reader DC-Erweiterungen für die Datenerfassung konfigurieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 0f8e1e46-4fc5-43f6-abb1-19a3f20e1f1d
source-git-commit: 5af420c8e95fed88a8516cce27b8bbc7d3974e75
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 5%

---

# Konfigurieren von Acrobat Reader DC-Erweiterungen für die Datenerfassung {#configuring-acrobat-reader-dc-extensions-for-data-capture}

Wenn Benutzer Ihrer AEM Forms-Installation die Datenerfassungsfunktion von Content Services (nicht mehr unterstützt) verwenden, wird empfohlen, eine Rolle mit schreibgeschütztem Zugriff für diese Benutzer zu erstellen.

***Hinweis **: Adobe® LiveCycle® Content Services ES (nicht mehr unterstützt) ist ein Content Management System, das mit LiveCycle installiert wird. Sie ermöglicht es Benutzern, am Menschen orientierte Prozesse zu entwerfen, zu verwalten, zu überwachen und zu optimieren. Die Unterstützung von Content Services (veraltet) endet am 31.12.2014. Weitere Informationen finden Sie unter [Adobe Produkt-Lifecycle-Dokument](https://helpx.adobe.com/de/support/programs/eol-matrix.html).*

Für die Datenerfassung müssen Sie eine Benutzerrolle für den Zugriff auf die SampleReaderExtensionsCredential zuweisen. Sie können die standardmäßige Rolle &quot;Vertrauensadministrator&quot;zuweisen. Beachten Sie jedoch, dass diese Rolle allgemeinen Administratorrechten für Benutzer ohne Administratorrechte gewährt, die die PKI-Vertrauenseinstellungen steuern und PKI-Anmeldeinformationen verwalten. Dies könnte die Sicherheit Ihrer AEM Forms-Installation in einer Produktionsumgebung beeinträchtigen. Es wird empfohlen, dass der AEM Forms-Systemadministrator eine Rolle erstellt, die nur schreibgeschützten Zugriff auf den Trust Store gewährt, und diese neue Rolle Benutzern ohne Administratorrechte zuweist, die die Datenerfassung verwenden.

## Rollen für Datenerfassungsbenutzer erstellen {#create-a-role-for-data-capture-users}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Rollenverwaltung&quot;und dann auf &quot;Neue Rolle&quot;.
1. Geben Sie den Rollennamen (z. B. &quot;Datenerfassungsbenutzer&quot;) und die Beschreibung in die entsprechenden Felder ein und klicken Sie dann auf Weiter.
1. Klicken Sie im Bildschirm &quot;Rollenberechtigungen&quot;auf &quot;Berechtigungen suchen&quot;und wählen Sie dann &quot;Berechtigung lesen&quot;aus der Liste der verfügbaren Berechtigungen aus.
1. Klicken Sie auf OK und dann auf Fertigstellen.

## Zuweisen der Datenerfassungsrolle {#assign-the-data-capture-role}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Rollenverwaltung&quot;und dann auf &quot;Suchen&quot;.
1. Klicken Sie auf die von Ihnen erstellte Benutzerrolle für die Datenerfassung.
1. Klicken Sie auf der Registerkarte Rollenbenutzer/-gruppen auf Benutzer/Gruppen suchen .
1. Klicken Sie im Bildschirm &quot;Benutzer und Gruppen suchen&quot;auf &quot;Suchen&quot;, wählen Sie die Benutzer aus, die die Datenerfassungsbenutzerrolle benötigen, und klicken Sie dann auf &quot;OK&quot;.
1. Klicken Sie im Bildschirm Rolle bearbeiten auf Speichern.
