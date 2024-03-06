---
title: Installieren und Konfiguration von Designer
description: Designer ist als eigenständiges Installationsprogramm sowie als Teil von WorkBench verfügbar. Erfahren Sie, wie Sie Designer als eigenständige Anwendung installieren.
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: designer
geptopics: SG_AEMFORMS/categories/jee
docset: aem65
role: Admin
feature: Forms Designer
exl-id: 90503d29-e079-43f4-a5dc-ce90ed7844c6
source-git-commit: 518207a0d8a95ef17b0972855a58f124fb215c85
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 78%

---

# Designer installieren und konfigurieren{#installing-and-configuring-designer}

## Voraussetzungen {#pre-requisites}

+++ Für 64-Bit-AEM Forms Designer (empfohlen)

* 64-Bit-Version von installieren  [Visual C++ 2019 Redistributable (x64)](https://learn.microsoft.com/de-de/cpp/windows/latest-supported-vc-redist?view=msvc-170). Stellen Sie vor Installationsbeginn sicher, dass die oben genannten Redistributable Runtime Packages installiert sind.
* Eine Benutzerin bzw. ein Benutzer mit Administratorrechten zum Installieren oder Deinstallieren von AEM Forms Designer.

+++

+++ Für 32-Bit-AEM Forms Designer

* 32-Bit-Version von installieren  [Visual C++ 2019 Redistributable (x64)](https://learn.microsoft.com/de-de/cpp/windows/latest-supported-vc-redist?view=msvc-170). Stellen Sie vor Installationsbeginn sicher, dass die oben genannten Redistributable Runtime Packages installiert sind.
* Eine Benutzerin bzw. ein Benutzer mit Administratorrechten zum Installieren oder Deinstallieren von AEM Forms Designer.

+++

>[!NOTE]
>
> Die 64-Bit-Version des Designers wurde mit AEM 6.5 Forms Service Pack 19 (6.5.19.0) eingeführt.



## Installieren von AEM Forms Designer {#install-designer}

Designer ist als eigenständiges Installationsprogramm sowie als Teil von WorkBench verfügbar. Wenn Sie ein eigenständiges Installationsprogramm für AEM Forms Designer verwenden, führen Sie die folgenden Schritte aus:

1. Deinstallieren Sie die vorherige Version von AEM Forms Designer, falls sie installiert ist.
1. Laden Sie den 64-Bit-AEM Forms Designer (empfohlen) oder den 32-Bit-AEM Forms-Designer entsprechend Ihren Anforderungen herunter.

   >[!NOTE]
   > 
   >* Forms Designer mit 32-Bit-Version wird ab AEM Version 6.5 Forms Service Packs 20 (6.5.20.0) nicht mehr unterstützt. Adobe empfiehlt ein Upgrade auf Forms Designer 64-Bit.
   >* Forms Designer mit 64 Bit ist nur für AEM 6.5 Forms Service Packs 19 (6.5.19.0) oder neuere Versionen verfügbar.
   >* Ab Adobe Experience Manager 6.5 Forms Service Pack 15 (6.5.15.0) umfasst die Version von Forms Designer auch die Version des Service Packs. Beispielsweise ist 6.5.15.20221112.1.0 die Versionsnummer für Service Pack 15. Hier ist 6.5.15 die Version des Service Packs.

1. Starten Sie das Installationsprogramm für AEM Forms Designer, indem Sie auf die Datei „setup.exe“ doppelklicken.
1. Fahren Sie fort und geben Sie Ihre Details und die Seriennummer auf dem Bildschirm „Personalisierung“ an.

   >[!NOTE]
   >
   >* Forms Designer-Lizenzschlüssel abrufen von [Adobe Licensing-Website](https://licensing.adobe.com/).

1. Wenn Sie die Lizenzvereinbarung akzeptieren, klicken Sie auf Weiter, um fortzufahren.
1. (Optional) Ändern Sie den standardmäßigen Installationspfad, wenn Sie Designer an einem anderen Speicherort installieren möchten. Klicken Sie auf Weiter.
1. Klicken Sie auf Zurück, um gegebenenfalls die Voreinstellungen zu ändern. Um Designer zu installieren, klicken Sie auf Installieren.
1. Klicken Sie auf Fertig stellen, wenn die Installation abgeschlossen ist.

Alternativ können Sie AEM Forms Designer über die Befehlszeile im passiven oder stillen Modus installieren.

* Passives Befehlszeileninstall: Das Installationsprogramm zeigt eine Fortschrittsleiste an, die anzeigt, dass die Installation noch nicht abgeschlossen ist, jedoch keine Eingabeaufforderungen oder Fehlermeldungen angezeigt werden. Nach dem Start kann die Installation nicht mehr abgebrochen werden.

```shell
msiexec /i "<absolute path>\Designer.msi" /passive SERIALNUMBER=****-****-****-****-****-****
```

* Stille Befehlszeilen-Installation: Das Installationsprogramm führt die Installation aus, ohne eine Benutzeroberfläche anzuzeigen. Es werden keine Eingabeaufforderungen, Meldungen oder Dialogfelder angezeigt. Nach dem Start kann die Installation nicht mehr abgebrochen werden.

```shell
msiexec /i "<absolute path>\Designer.msi" /quiet SERIALNUMBER=****-****-****-****-****-****
```

## Aktualisieren von AEM Forms Designer {#update-forms-designer}

Beim Aktualisieren der neuesten Version (6.5.16.0) von AEM Forms Designer gibt es zwei Fälle:

* **1. Fall**: Wenn die Benutzerin bzw. der Benutzer eine frühere Version von AEM Forms Designer als 6.5.15.0 verwendet.
* **2. Fall**: Wenn die Benutzerin bzw. der Benutzer die Version 6.5.15.0 von AEM Forms Designer verwendet.

+++**Wenn die Benutzerin bzw. der Benutzer eine frühere Version von AEM Forms Designer als 6.5.15.0 verwendet.**

Wenn Sie ein eigenständiges Installationsprogramm für AEM Forms Designer verwenden, führen Sie die folgenden Schritte aus:

1. Vor der Installation von **AEM Forms Designer 6.5.16.0** müssen Benutzende alle vorherigen Versionen deinstallieren.
1. Laden Sie [AEM Forms Designer 6.5.15.0](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) von der Seite von AEM Forms-Versionen herunter und installieren Sie es.
1. Nach erfolgreicher Installation von **AEM Forms Designer 6.5.15.0** laden Sie [AEM Forms Designer 6.5.16.0](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) herunter und installieren Sie es durch Doppelklick auf die heruntergeladene Installationsdatei.

+++

+++**Wenn die Benutzerin bzw. der Benutzer über die AEM Forms Designer-Version 6.5.15.0 verfügt**

Wenn Sie ein eigenständiges Installationsprogramm für AEM Forms Designer verwenden, führen Sie die folgenden Schritte aus:
1. Laden Sie die neueste Version von AEM Forms Designer vom [Software Distribution-Portal](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) herunter.
1. Installieren Sie die neueste Version von AEM Forms Designer, indem Sie auf die heruntergeladene Installationsdatei doppelklicken.

+++