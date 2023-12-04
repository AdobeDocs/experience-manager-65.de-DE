---
title: Konfigurieren von Microsoft Dynamics 365 für den Hypotheken-Workflow der We.Finance-Referenz-Website
description: Erfahren Sie, wie Sie die Dienste Microsoft&reg; Dynamics 365 über adaptive Formulare für den Hypotheken-Workflow der We.Finance-Referenz-Website verwenden.
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: develop, Configuration
exl-id: 2ac37dc5-d88d-4f98-8576-cd2ca6f0ea3a
source-git-commit: bd86d647fdc203015bc70a0f57d5b94b4c634bf9
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 35%

---

# Konfigurieren von Microsoft Dynamics 365 für den Hypotheken-Workflow der We.Finance-Referenz-Website {#configure-microsoft-dynamics-for-the-home-mortgage-workflow-of-the-we-finance-reference-site}

Erfahren Sie, wie Sie die Microsoft® Dynamics 365-Dienste über adaptive Formulare für den Hypotheken-Workflow der We.Finance-Referenz-Website verwenden.

## Übersicht {#overview}

Microsoft® Dynamics 365 ist eine Customer Relationship Management(CRM)- und Enterprise Resource Planning(ERP)-Software, die Enterprise-Lösungen zum Erstellen und Verwalten von Kundenkonten, Kontakten, Leads, Chancen und Fällen bereitstellt.

AEM Forms bietet einen Cloud-Service zur Integration von Dynamics 365 mit dem Modul [Datenintegration für AEM Forms](/help/forms/using/data-integration.md) an. Bevor Sie die schrittweise Anleitung zum Hypothekantrag mit Microsoft® Dynamics verwenden können, müssen Sie Microsoft® Dynamics 365 konfigurieren, damit es mit der We.Finance-Referenzwebsite verwendet werden kann.

## Voraussetzungen {#prerequisites}

Bevor Sie Dynamics 365 einrichten und konfigurieren, stellen Sie Folgendes sicher:

* AEM 6.3 Forms Service Pack 1 und höher
* Microsoft® Dynamics 365-Konto
* Registrierte Anwendung für den Dynamics 365-Dienst mit Microsoft® Azure Active Directory
* Client-ID und Client-Geheimnis für die registrierte Anwendung

## Verknüpfen Sie den Hypothekenrechner mit Ihrer Startseite. {#link-the-home-mortgage-calculator-with-your-site-home-page}

1. Wechseln Sie in der Autoreninstanz zur folgenden Seite:

   `https://[server]:[port]/editor.html/content/we-finance/global/en/loan-landing-page.html`

1. Scrollen Sie nach unten zum Hypothekrechner.
1. Markieren Sie das Bedienfeld der rechten Spalte (Rechner) und wählen Sie aus, um das Popup-Menü anzuzeigen. Wählen Sie im Popup-Menü die Option &quot;Konfigurieren&quot;. Das Dialogfeld &quot;AEM Forms-Container bearbeiten&quot;wird angezeigt.

   ![calculatorconfigurePanel](assets/calculatorconfigurepanel.png)

1. Durchsuchen Sie im Dialogfeld &quot;AEM Forms-Container bearbeiten&quot;den Asset-Pfad, wählen Sie Hypothekenrechner aus dem folgenden Pfad und wählen Sie **Bestätigen**:

   formsanddocuments/We.Finance/MS Dynamics/

   ![selectassetpath](assets/selectassetpath.png)

1. Klicken Sie auf **Fertig**.
1. Veröffentlichen Sie die bearbeitete Seite.

   >[!NOTE]
   >
   >Die Bindung der Rechenfelder mit dem FDM wird über das We.Finance-Referenz-Website-Paket vorkonfiguriert. Um die Bindung anzuzeigen, können Sie das Formular im Authoring-Modus öffnen und die Feldbindeverweise anzeigen.

1. Um eine benutzerdefinierte Entität zum Speichern des Antragstellerdatensatzes für die Hypothekenanwendung zu erstellen, importieren Sie das Lösungspaket AEMFormsFSIRefsite_1_0.zip in Ihre Microsoft® Dynamics-Instanz:

   1. Laden Sie das Paket herunter von:

      `https://'[server]:[port]'/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/AEMFormsFSIRefsite_1_0.zip`

   1. Importieren Sie das Lösungspaket in Ihre Microsoft® Dynamics-Instanz. Wechseln Sie in Ihrer Microsoft® Dynamics-Instanz zu **Einstellungen** > **Lösungen** und wählen Sie **Import**.

1. Um die auf der refsite verwendeten Benutzerkontaktdetails einzurichten, importieren Sie das Paket Sarah Rose Contact.CSV in Ihre Microsoft® Dynamics-Instanz:

   1. Laden Sie das Paket herunter von:

      `https://'[server]:[port]'/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/Sarah%20Rose%20Contact.csv`

   1. Importieren Sie das Paket in Ihre Microsoft® Dynamics-Instanz. Wechseln Sie in Ihrer Microsoft® Dynamics-Instanz zu **Vertrieb** > **Kontakte** und wählen Sie **Daten importieren**.
