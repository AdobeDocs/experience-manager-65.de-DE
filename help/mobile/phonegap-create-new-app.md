---
title: Erstellen einer neuen AEM Mobile-App mit dem Assistenten zum Erstellen
seo-title: Erstellen einer neuen AEM Mobile-App mit dem Assistenten zum Erstellen
description: AEM Mobile-Apps basieren auf einem Blueprint, der eine Seitenstruktur und Eigenschaften definiert. Auf dieser Seite erfahren Sie, wie Sie eine neue App basierend auf einer App-Vorlage erstellen.
seo-description: AEM Mobile-Apps basieren auf einem Blueprint, der eine Seitenstruktur und Eigenschaften definiert. Auf dieser Seite erfahren Sie, wie Sie eine neue App basierend auf einer App-Vorlage erstellen.
uuid: c2bd63a5-3dff-4a72-b1fb-0c776e0afa33
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-adobe-phonegap-enterprise
discoiquuid: 27605eb7-59b2-42d4-8cc5-02cfa52b4491
exl-id: be093025-b19f-4499-a7b5-aae5ab74f966
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 5%

---

# Erstellen einer neuen AEM Mobile-App mit dem Assistenten zum Erstellen{#creating-a-new-aem-mobile-app-using-create-wizard}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

AEM Mobile-Apps basieren auf einem Blueprint, der eine Seitenstruktur und Eigenschaften definiert. Sie können die folgenden Anwendungseigenschaften konfigurieren:

* **Titel:** Der Titel der Anwendung.
* **Zielpfad:** Der Speicherort im Repository, in dem die Anwendung gespeichert ist. Behalten Sie die Standardeinstellung bei, um einen Pfad basierend auf dem App-Namen zu erstellen.

* **Name:** Der Standardwert ist der Wert der Eigenschaft &quot;Title&quot;, wobei Leerzeichen entfernt werden. Der Name wird in AEM verwendet, um auf die Anwendung zu verweisen, z. B. für den Repository-Knoten, der die Anwendung darstellt.
* **Beschreibung:** Eine Beschreibung der Anwendung.
* **Server-URL:** Die URL, die Over-the-Air (OTA)-Inhaltsaktualisierungen für die Anwendung bereitstellt. Der Standardwert ist die Veröffentlichungs-Server-URL der Instanz, die zum Erstellen einer Anwendung verwendet wird (vom Externalizer-Dienst abgerufen). Beachten Sie, dass es sich hierbei nicht um einen Autor, sondern um eine Veröffentlichungs-Server-Instanz handeln muss, für die eine Authentifizierung erforderlich ist.

Sie können auch eine Bilddatei bereitstellen, die als Anwendungsminiaturansicht verwendet werden soll, die zu verwendende PhoneGap Build auswählen und die zu verwendende Mobile App-Analysekonfiguration auswählen. Dieses Bild wird nur als Miniaturansicht für Ihre Mobile App in der Mobile Apps-Konsole in Experience Manager verwendet.

Es gibt zusätzliche (und optionale) Registerkarten für den Build-Cloud-Service und die Integration des Adobe Mobile Services SDK-Plug-ins in Ihre App.

* Build: Klicken Sie hier auf Konfigurationen verwalten und richten Sie Ihren Build-Dienst build.phonegap.com ein. Wählen Sie dann aus der Dropdown-Liste den neu erstellten PhoneGap Build-Cloud-Service aus.
* Analytics: Klicken Sie auf Konfigurationen verwalten und richten Sie den Cloud-Dienst [Adobe Mobile Services SDK](https://docs.adobe.com/content/help/en/mobile-services/using/home.html) ein. Wählen Sie dann aus der Dropdown-Liste den neu erstellten Mobile Service aus, der in Ihre Mobile App integriert werden soll.

## Verwenden von App-Vorlagen {#using-app-templates}

App-Vorlagen bieten eine einfache Möglichkeit, vorhandene, von Entwicklern erstellte Designs zu nutzen, die für die Erstellung neuer Apps in AEM verwendet werden.

Was ist eine App-Vorlage? Stellen Sie sich dies als Sammlung von Seitenvorlagen und Komponenten vor, die eine Grundlinie oder Grundlage einer App darstellen.
Wenn Sie eine neue App basierend auf der Vorlage einer anderen App erstellen, erhalten Sie eine App mit einem Startpunkt, der für die App steht, aus der sie erstellt wurde.

Sie müssen über eine vorhandene Vorlage für mobile Apps (oder eine installierte App, die über eine App-Vorlage verfügt) verfügen, um diese Funktion nutzen zu können.

Das neueste Beispielpaket für AEM Apps enthält eine aktualisierte Version der Geometrixx App mit einer App-Vorlage. Alternativ können Sie [StarterKit](https://github.com/Adobe-Marketing-Cloud-Apps/aem-phonegap-starter-kit) installieren, das auch eine Vorlage bereitstellt.

Schritte zum Erstellen einer neuen App basierend auf einer App-Vorlage:

1. Navigieren Sie zum AEM Mobile-App-Katalog: &lt;*server-url*>aem/apps.html/content/mobileapps
1. Wählen Sie **Erstellen** und dann **App** wie unten dargestellt aus.

![chlimage_1-158](assets/chlimage_1-158.png)

Wählen Sie eine App-Vorlage aus, die Ihnen von einem AEM-Entwickler zur Verfügung gestellt wird. Hilfe für Entwickler finden Sie unter [Struktur einer AEM Mobile App](/help/mobile/phonegap-structure-an-app.md) .

![chlimage_1-159](assets/chlimage_1-159.png)

Füllen Sie bei Bedarf die Details Ihrer neuen App aus, einschließlich der optionalen Änderung des Miniaturbilds. Diese Werte können später über die Kachel **App verwalten** bearbeitet werden.

![chlimage_1-160](assets/chlimage_1-160.png)

## Die nächsten Schritte {#the-next-steps}

Weitere Informationen zu anderen Authoring-Rollen finden Sie in den folgenden Ressourcen:

* [Bereich „App verwalten“](/help/mobile/phonegap-app-details-tile.md)
* [Bearbeiten von App-Metadaten](/help/mobile/phonegap-editmetadata.md)
* [App-Definitionen](/help/mobile/phonegap-app-definitions.md)
* [Vorhandene Hybrid-App importieren](/help/mobile/phonegap-adding-content-to-imported-app.md)
* [Content Services](/help/mobile/develop-content-as-a-service.md)

## Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Zuständigkeiten von Administratoren und Entwicklern finden Sie in den folgenden Ressourcen:

* [Entwickeln für Adobe PhoneGap Enterprise mit AEM](/help/mobile/developing-in-phonegap.md)
* [Verwalten von Inhalten für Adobe PhoneGap Enterprise mit AEM](/help/mobile/administer-phonegap.md)
