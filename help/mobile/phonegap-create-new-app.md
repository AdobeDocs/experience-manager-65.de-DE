---
title: Erstellen einer AEM Mobile-App mit dem Assistenten „Erstellen“
description: AEM Mobile-Apps basieren auf einem Blueprint, der eine Seitenstruktur und Eigenschaften definiert. Auf dieser Seite erfahren Sie, wie Sie eine App erstellen, die auf einer App-Vorlage basiert.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-adobe-phonegap-enterprise
exl-id: be093025-b19f-4499-a7b5-aae5ab74f966
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '604'
ht-degree: 2%

---

# Erstellen einer AEM Mobile-App mit dem Assistenten „Erstellen“{#creating-a-new-aem-mobile-app-using-create-wizard}

{{ue-over-mobile}}

AEM Mobile-Apps basieren auf einem Blueprint, der eine Seitenstruktur und Eigenschaften definiert. Sie können die folgenden Anwendungseigenschaften konfigurieren:

* **Titel:** Der Titel der Anwendung.
* **Zielpfad:** Der Speicherort im Repository, in dem die Anwendung gespeichert ist. Behalten Sie die Standardeinstellung bei, um einen Pfad basierend auf dem App-Namen zu erstellen.

* **Name:** Der Standardwert ist der Wert der Eigenschaft „Title“, wobei Leerzeichen entfernt werden. Der Name wird innerhalb von AEM verwendet, um auf das Programm zu verweisen, z. B. für den Repository-Knoten, der das Programm darstellt.
* **Beschreibung:** Eine Beschreibung der Anwendung.
* **Server-URL:** Die URL, die OTA-Inhaltsaktualisierungen (Over-the-Air) für die Anwendung bereitstellt. Der Standardwert ist die Veröffentlichungs-Server-URL der -Instanz, die zum Erstellen einer Anwendung verwendet wird (entnommen aus dem Externalizer-Service). Beachten Sie, dass es sich hierbei um eine Veröffentlichungs-Server-Instanz und nicht um einen Autor handeln muss, wofür eine Authentifizierung erforderlich ist.

Sie können auch eine Bilddatei bereitstellen, die als Miniaturansicht der Anwendung verwendet werden soll, die zu verwendende PhoneGap Build-Konfiguration auswählen und die zu verwendende Mobile-App-Analysekonfiguration auswählen. Dieses Bild wird nur als Miniaturansicht verwendet, um Ihre Mobile App in der Mobile-Apps-Konsole im Experience Manager darzustellen.

Es gibt zusätzliche (und optionale) Registerkarten für Build Cloud Service und die Integration des Adobe Mobile Services SDK-Plug-ins in Ihre App.

* Build: Klicken Sie auf Konfigurationen verwalten und richten Sie Ihren build.phonegap.com Build-Dienst hier ein. Dann können Sie aus der Dropdown-Liste den neu erstellten PhoneGap-Build-Cloud-Service auswählen.
* Analytics: Klicken Sie auf „Konfigurationen verwalten“ und richten Sie Ihren [Adobe Mobile Services SDK](https://experienceleague.adobe.com/docs/mobile-services/using/home.html)-Cloud-Service ein. Anschließend können Sie aus der Dropdown-Liste den neu erstellten Mobile Service auswählen, der in Ihre Mobile App integriert werden soll.

## Verwenden von App-Vorlagen {#using-app-templates}

App-Vorlagen bieten eine einfache Möglichkeit, vorhandene Designs zu verwenden, die von Entwicklerinnen und Entwicklern erstellt wurden und für die Erstellung neuer Apps in AEM verwendet werden.

Was ist eine App-Vorlage? Stellen Sie sich dies als eine Sammlung von Seitenvorlagen und Komponenten vor, die eine Grundlinie oder die Grundlage einer App darstellen.
Wenn Sie eine App basierend auf der Vorlage einer anderen App erstellen, erhalten Sie eine App, deren Startpunkt repräsentativ für die App ist, aus der sie erstellt wurde.

Sie müssen über eine vorhandene Mobile-App-Vorlage (oder eine installierte App mit einer App-Vorlage) verfügen, um diese Funktion verwenden zu können.

Das neueste Beispielpaket für AEM-Apps enthält eine aktualisierte Version der Geometrixx-App mit einer App-Vorlage. Alternativ können Sie das StarterKit [, ](https://github.com/Adobe-Marketing-Cloud-Apps/aem-phonegap-starter-kit) auch eine Vorlage bereitstellt.

Schritte zum Erstellen einer App basierend auf einer App-Vorlage:

1. Navigieren Sie zum AEM Mobile-App-Katalog: &lt;*server-url*>aem/apps.html/content/mobileapps
1. Wählen Sie **Erstellen** und dann **App** aus, wie unten dargestellt

![chlimage_1-158](assets/chlimage_1-158.png)

Wählen Sie eine App-Vorlage aus, die Ihnen von einem AEM-Entwickler zur Verfügung gestellt wird. Entwicklerhilfe finden [ unter „Struktur ](/help/mobile/phonegap-structure-an-app.md) AEM Mobile-App“.

![chlimage_1-159](assets/chlimage_1-159.png)

Füllen Sie die Details Ihrer neuen App nach Bedarf aus, einschließlich der optionalen Änderung des Miniaturbilds. Diese Werte können später über die Kachel **App verwalten** bearbeitet werden.

![chlimage_1-160](assets/chlimage_1-160.png)

## Die nächsten Schritte {#the-next-steps}

Weitere Informationen zu anderen Authoring-Rollen finden Sie in den folgenden Ressourcen:

* [Verwalten der App-Kachel](/help/mobile/phonegap-app-details-tile.md)
* [Bearbeiten von App-Metadaten](/help/mobile/phonegap-editmetadata.md)
* [App-Definitionen](/help/mobile/phonegap-app-definitions.md)
* [Importieren einer vorhandenen Hybrid-App](/help/mobile/phonegap-adding-content-to-imported-app.md)
* [Content Services](/help/mobile/develop-content-as-a-service.md)

## Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Zuständigkeiten eines Administrators bzw. einer Administratorin und eines Entwicklers finden Sie in den folgenden Ressourcen:

* [Entwickeln für Adobe PhoneGap Enterprise mit AEM](/help/mobile/developing-in-phonegap.md)
* [Verwalten von Inhalten für Adobe PhoneGap Enterprise mit AEM](/help/mobile/administer-phonegap.md)
