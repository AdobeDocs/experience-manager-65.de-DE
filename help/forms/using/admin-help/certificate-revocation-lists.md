---
title: Verwalten von Zertifikatsperrlisten
description: Erfahren Sie, wie Sie Zertifikatsperrlisten verwalten. Mit der Trust Store-Verwaltung können Sie Zertifikatsperrlisten importieren, bearbeiten und löschen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 01e966f6-a650-4565-80d1-e2297f25da5c
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: ht
source-wordcount: '179'
ht-degree: 100%

---

# Verwalten von Zertifikatsperrlisten{#managing-certificate-revocationlists}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Mithilfe der Trust Store-Verwaltung können Sie Zertifikatsperrlisten (CRLs) importieren, bearbeiten und löschen. Es werden Base64- und DER-kodierte Zertifikatsperrlisten unterstützt.

## Importieren einer Zertifikatssperrliste {#import-a-crl}

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Trust Store-Verwaltung“ > „Zertifikatsperrliste“ und dann auf „Importieren“.
1. Geben Sie in das Feld „Alias“ eine Kennung für die Zertifikatssperrliste ein.
1. Klicken Sie auf „Durchsuchen“, um nach der Zertifikatssperrliste zu suchen, und anschließend auf „OK“.

## Exportieren einer Zertifikatssperrliste {#export-a-crl}

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Trust Store-Verwaltung“ > „Zertifikatsperrlisten“.
1. Klicken Sie auf den Aliasnamen der Zertifikatssperrliste, die exportiert werden soll, und anschließend auf „Exportieren“.
1. Befolgen Sie die Anweisungen zum Exportieren der Zertifikatssperrliste. Zertifikatssperrlisten werden mit Base64-Kodierung exportiert.
1. Klicken Sie auf OK.

## Löschen einer Zertifikatssperrliste {#delete-a-crl}

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Trust Store-Verwaltung“ > „Zertifikatsperrlisten“.
1. Aktivieren Sie die Kontrollkästchen für die zu löschenden Zertifikatssperrlisten und klicken Sie erst auf „Löschen“ und anschließend auf „OK“.
