---
title: Testen der globalisierten Site-Struktur von We.Retail
description: Erfahren Sie, wie Sie mit We.Retail eine globalisierte Site-Struktur in Adobe Experience Manager ausprobieren.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: e1de20b0-6d7a-4bda-b62f-c2808fd0af28
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 89%

---

# Testen der globalisierten Site-Struktur von We.Retail{#trying-out-the-globalized-site-structure-in-we-retail}

We.Retail wurde mit einer globalisierten Site-Struktur erstellt, die eine Sprachmustervorlage bietet, der live auf länderspezifische Websites kopiert werden kann. Alles ist vorkonfiguriert, damit Sie mit dieser Struktur und den integrierten Übersetzungsfunktionen experimentieren können.

## Probieren Sie es aus {#trying-it-out}

1. Öffnen Sie die Sites-Konsole über **Globale Navigation > Sites**.
1. Wechseln Sie zur Spaltenansicht (falls diese nicht bereits aktiviert ist) und wählen Sie „We.Retail“ aus. Beachten Sie die Beispiel-Landesstruktur inklusive Schweiz, USA, Frankreich usw. sowie die Sprachmustervorlage.

   ![chlimage_1-87](assets/chlimage_1-87a.png)

1. Wählen Sie die Schweiz aus und sehen Sie sich die Sprachstämme für die Sprachen dieses Landes an. Unter diesen Stämmen gibt es noch keinen Inhalt.

   ![chlimage_1-88](assets/chlimage_1-88a.png)

1. Wechseln Sie in die Listenansicht, um zu sehen, dass es sich bei den Sprachkopien für die Länder um Live Copies handelt.

   ![chlimage_1-89](assets/chlimage_1-89a.png)

1. Kehren Sie zur Spaltenansicht zurück, klicken Sie auf den Sprach-Master und sehen Sie sich die Stämme der Sprachmustervorlagen mit Inhalt an. Nur Englisch verfügt über Inhalte.

   We.Retail verfügt nicht von vornherein über übersetzte Inhalte, aber die Struktur und die Konfiguration sind vorhanden, damit Sie die Übersetzungsdienste demonstrieren können.

   ![chlimage_1-90](assets/chlimage_1-90a.png)

1. Lassen Sie den englischen Sprach-Master ausgewählt, öffnen Sie die Leiste **Verweise** in der Sites-Konsole und wählen Sie **Sprachkopien** aus.

   ![chlimage_1-91](assets/chlimage_1-91.png)

1. Aktivieren Sie das Kontrollkästchen neben der Bezeichnung **Sprachkopien**, um alle Sprachkopien auszuwählen. Wählen Sie im Abschnitt **Sprachkopien aktualisieren** der Leiste die Option **Neues Übersetzungsprojekt erstellen**. Geben Sie einen Namen für das Projekt ein und klicken Sie auf **Aktualisieren**.

   ![chlimage_1-92](assets/chlimage_1-92.png)

1. Für jede Sprachübersetzung wird ein Projekt erstellt. Anzeigen unter **Navigation > Projekte**.

   ![chlimage_1-93](assets/chlimage_1-93.png)

1. Klicken Sie auf „Deutsch“, um die Details des Übersetzungsprojekts anzuzeigen. Der Status lautet **Entwurf**. Um die Übersetzung mit dem Microsoft®-Übersetzungsdienst zu starten, klicken Sie auf den Pfeil neben der Überschrift **Übersetzungsauftrag** und wählen Sie **Starten**.

   ![chlimage_1-94](assets/chlimage_1-94.png)

1. Das Übersetzungsprojekt beginnt. Klicken Sie unten auf der Karte mit der Bezeichnung „Übersetzungsauftrag“ auf die Auslassungspunkte, um die Details anzuzeigen. Seiten mit dem Status **Bereit für Überprüfung** wurden bereits vom Übersetzungsdienst übersetzt.

   ![chlimage_1-95](assets/chlimage_1-95.png)

1. Wählen Sie in der Liste eine der Seiten und dann in der Symbolleiste die Option **Vorschau in Sites** aus, um die übersetzte Seite im Seiteneditor zu öffnen.

   ![chlimage_1-96](assets/chlimage_1-96.png)

>[!NOTE]
>
>Dieses Verfahren hat die Integration mit der maschinellen Übersetzung von Microsoft® demonstriert. Mit dem [AEM Translation Integration Framework](/help/sites-administering/translation.md) können Sie viele Standardübersetzungsdienste integrieren, um die Übersetzung von AEM zu organisieren.

## Weitere Informationen {#further-information}

Weitere Informationen finden Sie im Authoring-Dokument . [Übersetzen von Inhalten für mehrsprachige Sites](/help/sites-administering/translation.md) für vollständige technische Details.
