---
title: Designer installieren und konfigurieren
seo-title: Installing and configuring Designer
description: Designer ist als eigenständiges Installationsprogramm sowie als Teil von WorkBench erhältlich. Erfahren Sie, wie Sie Designer als eigenständige Anwendung installieren.
seo-description: Designer is available as a stand-alone installer and is also bundled with Workbench. Learn how to install stand-alone Designer.
uuid: c5b779d1-cb6a-48f4-87d6-48464753e516
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: designer
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: f3a5b5ce-2262-4d5d-a8ae-d59a3a4229e7
docset: aem65
role: Admin
exl-id: 90503d29-e079-43f4-a5dc-ce90ed7844c6
source-git-commit: 85189a4c35d1409690cbb93946369244e8848340
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 73%

---

# Designer installieren und konfigurieren{#installing-and-configuring-designer}

## Voraussetzungen {#pre-requisites}

* Installieren Sie die 32-Bit-Version von  [Visual C++ 2019 Redistributable (x86)](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170). Stellen Sie sicher, dass die oben genannten Redistributable Runtime Packages vor Installationsbeginn installiert sind. 
* Ein Benutzer mit Administratorrechten zum Installieren oder Deinstallieren von Designer.

## Installieren von Designer {#install-designer}

Designer ist als eigenständiges Installationsprogramm sowie als Teil von WorkBench erhältlich. Wenn Sie ein eigenständiges Installationsprogramm für Designer verwenden, führen Sie die folgenden Schritte aus:

1. Deinstallieren Sie die vorherige Version von AEM Forms Designer, falls sie bereits installiert ist.
1. Designer herunterladen aus [Adobe Licensing-Website](https://licensing.adobe.com/).

   >[!NOTE]
   >
   > * Ab Adobe Experience Manager 6.5 Forms Service Pack 15 (6.5.15.0) umfasst die Forms Designer-Version auch das Service Pack. Beispielsweise ist für Service Pack 15 die Versionsnummer 6.5.15.20221112.1.0. In diesem Beispiel ist 6.5.15 Service Pack-Version.


1. Starten Sie das Designer-Installationsprogramm, indem Sie auf setup.exe doppelklicken.
1. Fahren Sie fort und geben Sie Ihre Details und die Seriennummer im Bildschirm „Anpassung“ ein.
1. Wenn Sie die Lizenzvereinbarung akzeptieren, klicken Sie auf Weiter, um fortzufahren.
1. (Optional) Ändern Sie den Standardinstallationspfad, wenn Sie Designer an einem anderen Speicherort installieren möchten. Klicken Sie auf Weiter.
1. Klicken Sie auf Zurück, um gegebenenfalls die Voreinstellungen zu ändern. Um Designer zu installieren, klicken Sie auf Installieren.
1. Klicken Sie auf Fertig stellen, wenn die Installation abgeschlossen ist.

Alternativ können Sie Designer über die Befehlszeile im passiven oder stillen Modus installieren.

* Passives Befehlszeileninstall: Das Installationsprogramm zeigt eine Fortschrittsleiste an, die anzeigt, dass die Installation noch nicht abgeschlossen ist, jedoch keine Eingabeaufforderungen oder Fehlermeldungen angezeigt werden. Nach dem Start kann die Installation nicht mehr abgebrochen werden.

```shell
msiexec /i "<absolute path>\Designer.msi" /passive SERIALNUMBER=****-****-****-****-****-****
```

* Stille Befehlszeilen-Installation: Das Installationsprogramm führt die Installation aus, ohne eine Benutzeroberfläche anzuzeigen. Es werden keine Eingabeaufforderungen, Meldungen oder Dialogfelder angezeigt. Nach dem Start kann die Installation nicht mehr abgebrochen werden.

```shell
msiexec /i "<absolute path>\Designer.msi" /quiet SERIALNUMBER=****-****-****-****-****-****
```
