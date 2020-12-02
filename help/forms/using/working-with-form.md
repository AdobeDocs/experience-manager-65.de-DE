---
title: Arbeiten mit einem Formular
seo-title: Arbeiten mit einem Formular
description: Anzeigen und Aktualisieren des mit einer Aufgabe oder einem Startpunkt in der AEM Forms-App verknüpften Formulars
seo-description: Anzeigen und Aktualisieren des mit einer Aufgabe oder einem Startpunkt in der AEM Forms-App verknüpften Formulars
uuid: 7481ca5c-a2c0-4697-9008-1e51bce2012e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 8a5e038e-b39a-41de-88a0-47642e5bd5bf
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 92%

---


# Arbeiten mit einem Formular {#working-with-a-form}

Wenn ein Formular für die Synchronisierung in der Forms-App aktiviert ist, wird das Formular heruntergeladen und Sie können es direkt bearbeiten.

Die Formulare werden in Ihre App heruntergeladen und sind offline verfügbar. Sie führen beispielsweise ein Bankunternehmen und ein Kunde füllt einen Antrag auf Ihrer Site aus. Die Anwendung ist ein adaptives Formular, in das Ihre Kunden Daten eingeben, die dann zur Prüfung übermittelt werden. Der Administrator prüft das Formular und erstellt in einer Autoreninstanz von AEM ein Überprüfungsformular. Der Administrator aktiviert die Synchronisierung des Formulars mit der AEM Forms-App. Wenn das Überprüfungsformular in der AEM Forms-App verfügbar ist, kann Ihr Außendienstmitarbeiter die Angaben des Kunden auf einem Mobilgerät überprüfen. Das Mobilgerät wird mit dem Server synchronisiert und das Überprüfungsformular wird in der App geladen. Ihr Außendienstmitarbeiter kann Ihren Kunden besuchen, die Angaben überprüfen und die Daten als Entwurf speichern oder das Überprüfungsformular übermitteln. Das Formular wird jedes Mal, wenn Ihre App online ist, mit dem Server synchronisiert.

Formular in der AEM Forms-App synchronisieren

1. Wählen Sie in der Autoreninstanz ein Formular aus und klicken Sie auf **** Eigenschaften anzeigen.
1. Klicken Sie auf der Eigenschaftenseite auf **Erweitert**.
1. Aktivieren Sie unter Erweitert die Option: **Synchronisieren Sie mit AEM Forms App** und tippen Sie auf **Speichern**.

Um mehrere Formulare zu synchronisieren, wählen Sie in der Autoreninstanz mehrere Formulare in Forms Manager aus und tippen Sie auf **Mit AEM Forms-App synchronisieren**. Wenn das Formular veröffentlicht wird, wird die AEM Forms App mit dem Server synchronisiert und ruft das Formular ab.

>[!NOTE]
>
>Unterstützte Formulare:
>
>* Adaptive Formulare (ohne verzögertes Laden)
>* Mobile Forms

>
>
Anlagen auf Formularebene werden für adaptive Formulare, die in der AEM Forms-App mit einem AEM Forms OSGi-Server synchronisiert werden, nicht unterstützt. Benutzer können Dateien in einem Feld anhängen, wenn der Autor zum Zeitpunkt des Authoring des Formulars Anlagen auf Feldebenen aktiviert hat.

**Öffnen und Aktualisieren eines Formulars**

1. Um ein Formular zu öffnen, tippen Sie auf dem Startbildschirm auf das entsprechende Formular.
1. Sie können die Felder des Formulars aktualisieren, Anlagen auf Feldebene hinzufügen, das Formular als Entwurf speichern und es senden.
