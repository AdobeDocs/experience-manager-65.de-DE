---
title: Konfigurieren von Microsoft Dynamics 365 für den Hypotheken-Arbeitsablauf der We.Finance-Referenzwebsite
seo-title: Konfigurieren von Microsoft Dynamics 365 für den Hypotheken-Arbeitsablauf der We.Finance-Referenzwebsite
description: In diesem Dokument erfahren Sie, wie Sie die Microsoft® Dynamics 365-Dienste über adaptive Formularen für den Hypotheken-Arbeitsablauf der We.Finance-Referenzwebsite nutzen.
seo-description: In diesem Dokument erfahren Sie, wie Sie die Microsoft® Dynamics 365-Dienste über adaptive Formularen für den Hypotheken-Arbeitsablauf der We.Finance-Referenzwebsite nutzen.
uuid: a0656d90-84c7-46d1-9a16-dadcc19ff9ef
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: develop, Configuration
discoiquuid: 6b31397a-fb06-4043-9368-59fb4fce8afa
exl-id: 2ac37dc5-d88d-4f98-8576-cd2ca6f0ea3a
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 75%

---

# Konfigurieren von Microsoft Dynamics 365 für den Hypotheken-Arbeitsablauf der We.Finance-Referenzwebsite {#configure-microsoft-dynamics-for-the-home-mortgage-workflow-of-the-we-finance-reference-site}

In diesem Dokument erfahren Sie, wie Sie die Microsoft® Dynamics 365-Dienste über adaptive Formularen für den Hypotheken-Arbeitsablauf der We.Finance-Referenzwebsite nutzen.

## Überblick {#overview}

Microsoft® Dynamics 365 ist eine Software für Customer Relationship Management (CRM) und Enterprise Resource Planning (ERP), die Unternehmenslösungen für die Erstellung und Verwaltung von Kundenkonten, Kontakten, Leads, Chancen und Fällen bietet.

AEM Forms bietet einen Cloud-Service zur Integration von Dynamics 365 mit dem Modul [Forms Data Integration](/help/forms/using/data-integration.md). Bevor Sie die Anleitung zur Hypothekenanwendung mit Microsoft® Dynamics verwenden können, müssen Sie Microsoft® Dynamics 365 für die Verwendung mit der We.Finance-Referenz-Website konfigurieren.

## Voraussetzungen {#prerequisites}

Bevor Sie mit dem Einrichten und Konfigurieren von Dynamics 365 beginnen, stellen Sie sicher, dass folgende Bedingungen erfüllt sind:

* AEM Forms 6.3 Service Pack 1 und höher
* Microsoft® Dynamics 365-Konto
* Registrierte Anwendung für den Dynamics 365-Dienst mit Microsoft® Azure Active Directory
* Client-ID und Client-Geheimnis für die registrierte Anwendung

## Verknüpfen des Hypothekrechners mit Ihrer Site-Homepage {#link-the-home-mortgage-calculator-with-your-site-home-page}

1. Navigieren Sie in der Authoring-Instanz zu der folgenden Seite:

   `https://[server]:[port]/editor.html/content/we-finance/global/en/loan-landing-page.html`

1. Führen Sie einen Bildlauf nach unten zum Hypothekrechner durch.
1. Markieren Sie das Bedienfeld der rechten Spalte (Rechner) und tippen Sie, um das Popupmenü anzuzeigen. Tippen Sie im Popupmenü auf „Konfigurieren“. Das Dialogfeld „AEM Forms-Container bearbeiten“ wird angezeigt.

   ![calculatorconfigurePanel](assets/calculatorconfigurepanel.png)

1. Navigieren Sie im Dialogfeld „AEM Forms-Container bearbeiten“ zum Asset-Pfad, wählen Sie den Hypothekrechner unter dem folgenden Pfad aus und tippen Sie auf **Bestätigen**:

   formsanddocuments/We.Finance/MS Dynamics/

   ![selectassetpath](assets/selectassetpath.png)

1. Tippen Sie auf **Fertig**.
1. Veröffentlichen Sie die bearbeitete Seite.

   >[!NOTE]
   >
   >Die Bindung der Rechnerfelder mit dem FDM ist über die We.Finance-Referenzwebsite vorkonfiguriert. Um die Bindungen anzusehen, können Sie das Formular im Bearbeitungsmodus öffnen und die Feldbindungsverweise anzeigen.

1. Um eine benutzerdefinierte Entität zum Speichern des Antragsteller-Datensatzes für den Hypothekantrag zu erstellen, importieren Sie das AEMFormsFSIRefsite_1_0.zip-Lösungspaket in Ihre Microsoft® Dynamics-Instanz:

   1. Laden Sie das Paket herunter:

      `https://'[server]:[port]'/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/AEMFormsFSIRefsite_1_0.zip`

   1. Importieren Sie das Lösungspaket in Ihre Microsoft® Dynamics-Instanz. Navigieren Sie in Ihrer Microsoft® Dynamics-Instanz zu **Einstellungen** > **Lösungen** und tippen Sie auf **Importieren**.

1. Um die auf der Referenzwebsite verwendeten Benutzerkontaktdaten einzurichten, importieren Sie das Paket „Sarah Rose Contact.CSV“ in Ihre Microsoft® Dynamics-Instanz:

   1. Laden Sie das Paket herunter:

      `https://'[server]:[port]'/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/Sarah%20Rose%20Contact.csv`

   1. Importieren Sie das Paket in Ihre Microsoft® Dynamics-Instanz. Wechseln Sie in Ihrer Microsoft® Dynamics-Instanz zu **Sales** > **Contacts** und tippen Sie dann auf **Daten importieren**.
