---
title: Verfassen einer Seite für Mobilgeräte
description: Wenn Sie eine Seite für Mobilgeräte bearbeiten, wird die Seite so angezeigt, dass das Mobilgerät emuliert wird. Beim Bearbeiten der Seite können Sie zwischen mehreren Emulatoren wechseln, um zu sehen, was der Endbenutzer bzw. die Endbenutzerin beim Zugriff auf die Seite sehen.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
exl-id: d5372474-d8aa-4e64-919d-0bd29ba99d99
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 100%

---

# Verfassen einer Seite für Mobilgeräte{#authoring-a-page-for-mobile-devices}

Wenn Sie eine Seite für Mobilgeräte bearbeiten, wird die Seite so angezeigt, dass das Mobilgerät emuliert wird. Beim Bearbeiten der Seite können Sie zwischen mehreren Emulatoren wechseln, um zu sehen, was die Endbenutzerinnen und -benutzer beim Zugriff auf die Seite sehen.

Geräte sind entsprechend ihrer Fähigkeit zur Wiedergabe einer Seite in die Kategorien „Feature“, „Smart“ und „Touch“ eingeteilt. Wenn die Endbenutzerinnen und -benutzer auf eine mobile Seite zugreifen, erkennt AEM das Gerät und übermittelt die Darstellung, die der Gerätegruppe entspricht.

>[!NOTE]
>
>Zur Erstellung einer Website für Mobilgeräte auf der Grundlage einer bestehenden Standard-Site erstellen Sie eine Live Copy der Standard-Site. (Siehe [Erstellen einer Live Copy für unterschiedliche Kanäle](/help/sites-administering/msm-livecopy.md).)
>
>AEM-Entwickler können neue Gerätegruppen erstellen. (Siehe [Erstellen von Gerätegruppen-Filtern](/help/sites-developing/groupfilters.md).)

Gehen Sie wie folgt vor, um eine Seite für Mobilgeräte zu erstellen:

1. Navigieren Sie in Ihrem Browser zur **Siteadmin**-Konsole.
1. Öffnen Sie die Seite **Produkte** unterhalb von **Websites** >> **Geometrixx Mobile Demo Site** >> **Englisch**.

1. Wechseln Sie zu einem anderen Emulator. Dafür haben Sie folgende Möglichkeiten:

   * Klicken Sie oben auf der Seite auf das Suchsymbol.
   * Klicken Sie auf **Bearbeiten** im **Sidekick** und wählen Sie das Gerät im Dropdown-Menü aus.

1. Ziehen Sie die **Text-und-Bild**-Komponente aus der Registerkarte „Mobil“ des Sidekicks auf die Seite.
1. Bearbeiten Sie die Komponente und fügen Sie Text hinzu. Klicken Sie auf **OK**, um die Änderungen zu speichern.

Die Seite sieht genau wie folgt aus:

![mobileipademu](assets/mobileipademu.png)

>[!NOTE]
>
>Die Emulatoren sind deaktiviert, wenn eine Seite in der Autoreninstanz von einem Mobilgerät aus aufgerufen wird. Das Erstellen kann in diesem Fall in der Touch-optimierten Benutzeroberfläche erfolgen.
