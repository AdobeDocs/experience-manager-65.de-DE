---
title: Designer installieren und konfigurieren
seo-title: Installing and configuring Designer
description: 'Designer ist als eigenständiges Installationsprogramm sowie als Teil von WorkBench erhältlich. Erfahren Sie, wie Sie Designer als eigenständige Anwendung installieren.  '
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
source-git-commit: a3cf926bde4a4b3a0810058e84ac01012a4a3a57
workflow-type: ht
source-wordcount: '280'
ht-degree: 100%

---

# Designer installieren und konfigurieren{#installing-and-configuring-designer}

## Voraussetzungen {#pre-requisites}

Für das AEM Forms Designer-Installationsprogramm ist die 32-Bit-Version von [Visual C++ Redistributable Runtime Package 2012](https://support.microsoft.com/de-de/topic/the-latest-supported-visual-c-downloads-2647da03-1eea-4433-9aff-95f26a218cc0) und [Visual C++ Redistributable Runtime Package 2013](https://support.microsoft.com/de-de/help/3179560/update-for-visual-c-2013-and-visual-c-redistributable-package) erforderlich. Stellen Sie sicher, dass die oben genannten Redistributable Runtime Packages vor Installationsbeginn installiert sind. 

Sie benötigen Administratorrechte, um Designer zu installieren oder zu deinstallieren.

## Installieren von Designer {#install-designer}

Designer ist als eigenständiges Installationsprogramm sowie als Teil von WorkBench erhältlich. Wenn Sie ein eigenständiges Installationsprogramm für Designer verwenden, führen Sie die folgenden Schritte aus:

1. Laden Sie Designer von der Adobe [Lizenzierungs-Webseite](https://licensing.adobe.com/) herunter.

   >[!NOTE]
   >
   >Wenn Sie eine frühere Version von Designer installiert haben, deinstallieren Sie diese, bevor Sie fortfahren.

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


