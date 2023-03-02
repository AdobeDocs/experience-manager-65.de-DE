---
title: Installieren und Konfiguration von Designer
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
source-git-commit: 1b2d743f8f2172c4e4663917d598734cb1ea1ea4
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 55%

---

# Designer installieren und konfigurieren{#installing-and-configuring-designer}

## Voraussetzungen {#pre-requisites}

* Installieren Sie die 32-Bit-Version von [Visual C++ 2019 Redistributable (x86)](https://learn.microsoft.com/de-de/cpp/windows/latest-supported-vc-redist?view=msvc-170). Stellen Sie vor Installationsbeginn sicher, dass die oben genannten Redistributable Runtime Packages installiert sind. 
* Ein Benutzer mit Administratorrechten zum Installieren oder Deinstallieren von AEM Forms Designer.

## Installieren von AEM Forms Designer {#install-designer}

Designer ist als eigenständiges Installationsprogramm sowie als Teil von WorkBench erhältlich. Wenn Sie ein eigenständiges Installationsprogramm für AEM Forms Designer verwenden, führen Sie die folgenden Schritte aus:

1. Deinstallieren Sie die vorherige Version von AEM Forms Designer, falls sie installiert ist.
1. Laden Sie Designer von der [Lizenzierungs-Webseite von Adobe](https://licensing.adobe.com/) herunter.

   >[!NOTE]
   >
   > * Ab Adobe Experience Manager 6.5 Forms Service Pack 15 (6.5.15.0) umfasst die Version von Forms Designer auch die Version des Service Packs. Beispielsweise ist 6.5.15.20221112.1.0 die Versionsnummer für Service Pack 15. Hier ist 6.5.15 die Version des Service Packs.


1. Starten Sie das Installationsprogramm für AEM Forms Designer, indem Sie auf setup.exe doppelklicken.
1. Fahren Sie fort und geben Sie Ihre Details und die Seriennummer im Bildschirm „Anpassung“ ein.
1. Wenn Sie die Lizenzvereinbarung akzeptieren, klicken Sie auf Weiter, um fortzufahren.
1. (Optional) Ändern Sie den Standardinstallationspfad, wenn Sie Designer an einem anderen Speicherort installieren möchten. Klicken Sie auf Weiter.
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

## AEM Forms Designer aktualisieren {#update-forms-designer}

Beim Aktualisieren der neuesten Version von AEM Forms Designer 6.5.16.0 gibt es zwei Fälle:

* **1. Fall**: Wenn der Benutzer über eine AEM Forms Designer-Version vor 6.5.15.0 verfügt.
* **2. Fall**: Wenn der Benutzer über die AEM Forms Designer-Version 6.5.15.0 verfügt.

+++**Wenn der Benutzer über eine AEM Forms Designer-Version vor 6.5.15.0 verfügt.**

Wenn Sie ein eigenständiges Installationsprogramm für AEM Forms Designer verwenden, führen Sie die folgenden Schritte aus:

1. Vor der Installation **AEM Forms Designer 6.5.16.0**, müssen Benutzer alle vorherigen Versionen deinstallieren.
1. Herunterladen und installieren [AEM Forms Designer 6.5.15.0](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) auf der Seite AEM Formularversionen .
1. Nach erfolgreicher Installation von **AEM Forms Designer 6.5.15.0**, herunterladen und installieren [AEM Forms Designer 6.5.16.0](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) durch Doppelklicken auf die heruntergeladene Installationsdatei .

+++

+++**Wenn der Benutzer über die AEM Forms Designer-Version 6.5.15.0 verfügt**

Wenn Sie ein eigenständiges Installationsprogramm für AEM Forms Designer verwenden, führen Sie die folgenden Schritte aus:
1. Laden Sie die neueste Version von AEM Forms Designer von der [Software Distribution-Portal](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de).
1. Installieren Sie die neueste Version von AEM Forms Designer, indem Sie auf die heruntergeladene Installationsdatei doppelklicken.

+++