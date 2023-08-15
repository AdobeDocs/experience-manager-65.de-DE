---
title: Testen der globalisierten Site-Struktur von We.Retail
description: Testen der globalisierten Site-Struktur von We.Retail
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: e1de20b0-6d7a-4bda-b62f-c2808fd0af28
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 27%

---

# Testen der globalisierten Site-Struktur von We.Retail{#trying-out-the-globalized-site-structure-in-we-retail}

We.Retail wurde mit einer globalisierten Site-Struktur erstellt, die einen Sprach-Master bietet, der live auf länderspezifische Websites kopiert werden kann. Alles ist vorkonfiguriert, damit Sie mit dieser Struktur und den integrierten Übersetzungsfunktionen experimentieren können.

## Testen {#trying-it-out}

1. Öffnen Sie die Sites-Konsole über **Globale Navigation -> Sites**.
1. Wechseln Sie zur Spaltenansicht (falls noch nicht aktiv) und wählen Sie We.Retail aus. Beachten Sie die Beispiellandstruktur mit der Schweiz, den USA, Frankreich usw. neben dem Sprachmaster.

   ![chlimage_1-87](assets/chlimage_1-87a.png)

1. Wählen Sie die Schweiz aus und sehen Sie sich die Sprachstämme für die Sprachen dieses Landes an. Unter diesen Wurzeln gibt es noch keinen Inhalt.

   ![chlimage_1-88](assets/chlimage_1-88a.png)

1. Wechseln Sie in die Listenansicht, um zu sehen, dass es sich bei den Sprachkopien für die Länder um Live Copies handelt.

   ![chlimage_1-89](assets/chlimage_1-89a.png)

1. Kehren Sie zur Spaltenansicht zurück, klicken Sie auf den Sprach-Master und sehen Sie sich die Sprach-Master-Stämme mit Inhalt an. Nur Englisch hat Inhalt.

   We.Retail enthält keine übersetzten Inhalte, doch die Struktur und Konfiguration sind vorhanden, um Ihnen die Übersetzungsdienste zu demonstrieren.

   ![chlimage_1-90](assets/chlimage_1-90a.png)

1. Lassen Sie den englischen Sprach-Master ausgewählt, öffnen Sie die Leiste **Verweise** in der Sites-Konsole und wählen Sie **Sprachkopien** aus.

   ![chlimage_1-91](assets/chlimage_1-91.png)

1. Aktivieren Sie das Kontrollkästchen neben dem **Sprachkopien** Beschriftung zur Auswahl aller Sprachkopien. Im **Sprachkopien aktualisieren** Wählen Sie in der Leiste die Option **Neues Übersetzungsprojekt erstellen**. Geben Sie einen Namen für das Projekt ein und klicken Sie auf **Aktualisieren**.

   ![chlimage_1-92](assets/chlimage_1-92.png)

1. Für jede Sprachübersetzung wird ein Projekt erstellt. Anzeigen unter **Navigation -> Projekte**.

   ![chlimage_1-93](assets/chlimage_1-93.png)

1. Klicken Sie auf Deutsch , um die Details des Übersetzungsprojekts anzuzeigen. Der Status befindet sich in **Entwurf**. Um die Übersetzung mit dem Übersetzungsdienst von Microsoft® zu starten, klicken Sie auf den Pfeil neben dem **Übersetzungsauftrag** Überschrift und Auswahl **Starten**.

   ![chlimage_1-94](assets/chlimage_1-94.png)

1. Das Übersetzungsprojekt beginnt. Klicken Sie unten auf der Karte mit der Bezeichnung Übersetzungsauftrag auf das Auslassungszeichen, um die Details anzuzeigen. Seiten mit dem Status **Bereit zur Überprüfung** wurden bereits vom Übersetzungsdienst übersetzt.

   ![chlimage_1-95](assets/chlimage_1-95.png)

1. Wählen Sie in der Liste eine der Seiten und dann in der Symbolleiste die Option **Vorschau in Sites** aus, um die übersetzte Seite im Seiteneditor zu öffnen.

   ![chlimage_1-96](assets/chlimage_1-96.png)

>[!NOTE]
>
>Dieses Verfahren zeigt die integrierte Integration mit der maschinellen Übersetzung von Microsoft®. Verwenden der [AEM Framework für die Übersetzungsintegration](/help/sites-administering/translation.md), können Sie mit vielen Standardübersetzungsdiensten integrieren, um die Übersetzung von AEM zu koordinieren.

## Weiterführende Informationen {#further-information}

Weitere Informationen sowie vollständige technische Details finden Sie im Dokument [Übersetzen von Inhalten für mehrsprachige Sites](/help/sites-administering/translation.md).
