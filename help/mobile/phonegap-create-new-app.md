---
title: Erstellen einer neuen AEM Mobile-App mit dem Assistenten zum Erstellen
seo-title: Erstellen einer neuen AEM Mobile-App mit dem Assistenten zum Erstellen
description: AEM Mobile-Apps basieren auf einem Entwurf, der eine Seitenstruktur und Eigenschaften definiert. Auf dieser Seite erfahren Sie, wie Sie eine neue App erstellen, die auf einer App-Vorlage basiert.
seo-description: AEM Mobile-Apps basieren auf einem Entwurf, der eine Seitenstruktur und Eigenschaften definiert. Auf dieser Seite erfahren Sie, wie Sie eine neue App erstellen, die auf einer App-Vorlage basiert.
uuid: c2bd63a5-3dff-4a72-b1fb-0c776e0afa33
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-adobe-phonegap-enterprise
discoiquuid: 27605eb7-59b2-42d4-8cc5-02cfa52b4491
translation-type: tm+mt
source-git-commit: 70b18dbe351901abb333d491dd06a6c1c1c569d6
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 5%

---


# Erstellen einer neuen AEM Mobile-App mit dem Assistenten zum Erstellen{#creating-a-new-aem-mobile-app-using-create-wizard}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

AEM Mobile-Apps basieren auf einem Entwurf, der eine Seitenstruktur und Eigenschaften definiert. Sie können die folgenden Anwendungseigenschaften konfigurieren:

* **Titel:** Der Titel der Anwendung.
* **Zielpfad:** Der Speicherort im Repository, in dem die Anwendung gespeichert wird. Lassen Sie die Standardeinstellung, um einen Pfad basierend auf dem App-Namen zu erstellen.

* **Name:** Der Standardwert ist der Wert der Title-Eigenschaft, bei der Leerzeichen entfernt werden. Der Name wird in AEM verwendet, um auf die Anwendung zu verweisen, z. B. auf den Repository-Knoten, der die Anwendung darstellt.
* **Beschreibung:** Eine Beschreibung des Antrags.
* **Server-URL:** Die URL, die OTA-Inhalte (Over-the-Air) bereitstellt, wird der Anwendung aktualisiert. Der Standardwert ist die Veröffentlichungsserver-URL der Instanz, die zum Erstellen einer Anwendung verwendet wird (vom Externalisierungs-Dienst genommen). Beachten Sie, dass es sich hierbei nicht um einen Autor, sondern um eine Instanz im Veröffentlichungsserver handeln muss. Hierfür ist eine Authentifizierung erforderlich.

Sie können auch eine Bilddatei zur Verwendung als Anwendungsminiaturansicht angeben, die PhoneGap Build-Konfiguration auswählen und die zu verwendende Mobile App-Analysekonfiguration auswählen. Dieses Bild wird nur als Miniaturansicht für Ihre Mobilanwendung in der App-Konsole in Experience Manager verwendet.

Zusätzliche (und optionale) Registerkarten sind vorhanden, um den Cloud-Dienst zu erstellen und das Adobe Mobile Services SDK-Plug-In in Ihre App zu integrieren.

* Erstellen: Klicken Sie auf Konfigurationen verwalten und richten Sie hier Ihren Build-Dienst build.phonegap.com ein. Dann können Sie aus der Dropdownliste den neu erstellten PhoneGap Build Cloud-Dienst auswählen.
* Analytics: Klicken Sie auf Konfigurationen verwalten und richten Sie Ihren [Adobe Mobile Services SDK](https://docs.adobe.com/content/help/en/mobile-services/using/home.html) -Cloud-Dienst ein. Anschließend können Sie aus der Dropdownliste den neu erstellten Mobile Service auswählen, der in Ihre mobile App integriert werden soll.

## Verwenden von App-Vorlagen {#using-app-templates}

App-Vorlagen bieten eine einfache Möglichkeit, vorhandene Designs zu nutzen, die von Entwicklern erstellt wurden und für die Erstellung neuer Apps in AEM verwendet werden.

Was ist eine App-Vorlage? Stellen Sie sich dies als eine Sammlung von Seitenvorlagen und Komponenten vor, die eine Grundlage oder Grundlage einer App darstellen.
Wenn Sie eine neue App erstellen, die auf der Vorlage einer anderen App basiert, erhalten Sie eine App mit einem Startpunkt, der der App entspricht, aus der sie erstellt wurde.

Sie müssen über eine vorhandene mobile App-Vorlage verfügen (oder eine App mit einer App-Vorlage installiert haben), um diese Funktion nutzen zu können.

Das neueste AEM Apps-Beispielpaket enthält eine aktualisierte Version der Geometrixx-App mit einer App-Vorlage. Alternativ können Sie auch das [StarterKit](https://github.com/Adobe-Marketing-Cloud-Apps/aem-phonegap-starter-kit) installieren, das auch eine Vorlage bereitstellt.

Schritte zum Erstellen einer neuen App basierend auf einer App-Vorlage:

1. Navigieren Sie zum AEM Mobile-App-Katalog: &lt;*server-url*>aem/apps.html/content/mobileapps
1. Wählen Sie **Erstellen** und dann **App** wie unten dargestellt

![chlimage_1-158](assets/chlimage_1-158.png)

Wählen Sie eine App-Vorlage aus, die Ihnen von einem AEM-Entwickler zur Verfügung gestellt wird. Weitere Informationen finden Sie unter [Struktur einer AEM Mobile-App](/help/mobile/phonegap-structure-an-app.md) .

![chlimage_1-159](assets/chlimage_1-159.png)

Füllen Sie nach Bedarf die Details Ihrer neuen App aus, einschließlich der optionalen Änderung des Miniaturbilds. Diese Werte können später über die Kachel App **verwalten** bearbeitet werden.

![chlimage_1-160](assets/chlimage_1-160.png)

## Die nächsten Schritte {#the-next-steps}

Weitere Informationen zu anderen Authoring-Rollen finden Sie in den folgenden Ressourcen:

* [Bereich „App verwalten“](/help/mobile/phonegap-app-details-tile.md)
* [Bearbeiten von App-Metadaten](/help/mobile/phonegap-editmetadata.md)
* [App-Definitionen](/help/mobile/phonegap-app-definitions.md)
* [Vorhandene Hybrid-App importieren](/help/mobile/phonegap-adding-content-to-imported-app.md)
* [Content Services](/help/mobile/develop-content-as-a-service.md)

## Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Verantwortlichkeiten von Administratoren und Entwicklern finden Sie in den nachfolgend aufgeführten Ressourcen:

* [Entwickeln für Adobe PhoneGap Enterprise mit AEM](/help/mobile/developing-in-phonegap.md)
* [Verwalten von Inhalten für Adobe PhoneGap Enterprise mit AEM](/help/mobile/administer-phonegap.md)
