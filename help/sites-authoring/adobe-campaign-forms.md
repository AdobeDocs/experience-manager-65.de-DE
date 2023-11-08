---
title: Erstellen von Adobe Campaign-Formularen in Adobe Experience Manager
description: Mit AEM können Sie Formulare erstellen und bearbeiten, die auf Ihrer Website mit Adobe Campaign interagieren
uuid: 61778ea7-c4d7-43ee-905f-f3ecb752aae2
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
discoiquuid: d53ef3e2-14ca-4444-b563-be67be15c040
exl-id: 7d60673e-484a-4447-83cf-d62a0d7ad745
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '1286'
ht-degree: 95%

---

# Erstellen von Adobe Campaign-Formularen in AEM {#creating-adobe-campaign-forms-in-aem}

Mit AEM können Sie Formulare erstellen und bearbeiten, die auf Ihrer Website mit Adobe Campaign interagieren. Bestimmte Felder können in Ihre Formulare eingefügt und der Adobe Campaign-Datenbank zugeordnet werden.

Sie können neue Kontaktanmeldungen, -abmeldungen und Benutzerprofildaten verwalten und gleichzeitig deren Daten in Ihre Adobe Campaign-Datenbank integrieren.

Um Adobe Campaign-Formulare in AEM zu verwenden, müssen Sie die folgenden Schritte ausführen, die in diesem Dokument beschrieben werden:

1. Stellen Sie eine Vorlage zur Verfügung.
1. Erstellen Sie ein Formular.
1. Bearbeiten Sie den Formularinhalt.

Standardmäßig sind drei Formulartypen für Adobe Campaign verfügbar:

* Profil speichern
* Service abonnieren
* Von einem Service abmelden

Diese Formulare definieren einen URL-Parameter, der den verschlüsselten Primärschlüssel eines Adobe Campaign-Profils akzeptiert. Basierend auf diesem URL-Parameter aktualisiert das Formular die Daten des zugehörigen Adobe Campaign-Profils.

Obwohl Sie diese Formulare unabhängig voneinander erstellen, generieren Sie in einem typischen Anwendungsfall einen personalisierten Link zu einer Formularseite innerhalb des Newsletter-Inhalts, damit Empfängerinnen und Empfänger den Link öffnen und Anpassungen an ihren Profildaten vornehmen können (unabhängig davon, ob sie sich abmelden, abonnieren oder ihr Profil aktualisieren).

Das Formular wird basierend auf der Benutzerin bzw. dem Benutzer automatisch aktualisiert. Siehe [Formularinhalt bearbeiten](#editing-form-content), um weitere Informationen zu erhalten.

## Verfügbarmachen von Vorlagen {#making-a-template-available}

Damit Sie für Adobe Campaign spezifische Formulare erstellen können, müssen Sie die verschiedenen Vorlagen in Ihrer AEM-Anwendung verfügbar machen.

Weitere Informationen hierzu finden Sie in der [Vorlagendokumentation](/help/sites-developing/templates.md#template-availability).

## Erstellen von Formularen {#creating-a-form}

Überprüfen Sie zunächst, ob die Verbindung zwischen der Authoring- und der Publishing-Instanz und Adobe Campaign funktioniert. Siehe [Integration mit Adobe Campaign Standard](/help/sites-administering/campaignstandard.md) bzw. [Integration mit Adobe Campaign Classic](/help/sites-administering/campaignonpremise.md).

>[!NOTE]
>
>Stellen Sie sicher, dass die Eigenschaft **acMapping** im Knoten **jcr:content** der Seite auf den Wert **mapRecipient** bzw. **profile** eingestellt ist, wenn Sie mit Adobe Campaign Classic oder Adobe Campaign Standard arbeiten.
>

1. Navigieren Sie in AEM in Sites an die Stelle, an der Sie eine Seite erstellen möchten.
1. Erstellen Sie eine Seite, wählen Sie **Adobe Campaign Classic-Profil** oder **Adobe Campaign Standard-Profil** aus und klicken Sie auf **Weiter**.

   ![chlimage_1-43](assets/chlimage_1-43a.png)

   >[!NOTE]
   >
   >Ist die gewünschte Vorlage nicht verfügbar, finden Sie weitere Informationen hierzu unter [Verfügbarmachen von Vorlagen](/help/sites-developing/templates.md#template-availability).

1. Fügen Sie im Feld **Name** den Namen der Seite hinzu. Es muss ein gültiger JCR-Name sein.
1. Geben Sie im Feld **Titel** den Titel ein und klicken Sie auf **Erstellen**.
1. Öffnen Sie die Seite und wählen Sie **Eigenschaften öffnen** aus. Fügen Sie in Cloud Services die Adobe Campaign-Konfiguration hinzu und klicken Sie auf das Häkchen, um die Änderungen zu speichern.

   ![chlimage_1-44](assets/chlimage_1-44a.png)

1. Wählen Sie auf der Seite in der Komponente **Formularstart** den Formulartyp aus – **Abonnieren, Abmelden** oder **Profil speichern**. Pro Formular kann nur ein Typ gewählt werden. Sie können den [Inhalt des Formulars nun bearbeiten](#editing-form-content).

## Bearbeiten von Formularinhalten {#editing-form-content}

Eigens für Adobe Campaign erstellte Formulare haben bestimmte Komponenten. Diese Komponenten bieten die Möglichkeit, jedes Formularfeld mit einem Feld in der Adobe Campaign-Datenbank zu verknüpfen.

>[!NOTE]
>
>Ist die gewünschte Vorlage nicht verfügbar, finden Sie weitere Informationen hierzu unter [Verfügbarmachen von Vorlagen](/help/sites-authoring/adobe-campaign.md).

In diesem Abschnitt werden nur für Adobe Campaign spezifische Verknüpfungen behandelt. Weitere Informationen und einen allgemeineren Überblick darüber, wie Sie Formulare in Adobe Experience Manager verwenden, finden Sie unter [Komponenten des Bearbeitungsmodus](/help/sites-authoring/default-components-foundation.md).

1. Wählen Sie **Eigenschaften öffnen** aus. Fügen Sie den Cloud-Services die Adobe Campaign-Konfiguration hinzu und klicken Sie auf das Häkchen, um die Änderungen zu übernehmen.

   ![chlimage_1-45](assets/chlimage_1-45a.png)

1. Klicken Sie auf der Seite in der Komponente **Formular-Start** auf das Symbol für die Konfiguration.

   ![chlimage_1-46](assets/chlimage_1-46a.png)

1. Klicken Sie auf die Registerkarte **Erweitert**, wählen Sie den Formulartyp (**Abonnieren, Abonnement kündigen** oder **Profil speichern**) aus und klicken Sie auf **OK.** Pro Formular kann nur ein Typ gewählt werden.

   * **Adobe Campaign: Profil speichern**: ermöglicht das Erstellen oder Aktualisieren einer Empfängerin oder eines Empfängers in Adobe Campaign (Standardwert).
   * **Adobe Campaign: Abonnieren von Diensten**: ermöglicht das Verwalten der Abonnements einer Empfängerin oder eines Empfängers in Adobe Campaign.
   * **Adobe Campaign: Abmeldung von Diensten**: ermöglicht Ihnen, die Abonnements einer Empfängerin oder eines Empfängers in Adobe Campaign zu stornieren.

1. Sie müssen in jedem Formular eine Komponente **Verschlüsselter Primärschlüssel** haben. Diese Komponente definiert, welcher URL-Parameter zum Akzeptieren des verschlüsselten Primärschlüssels eines Adobe Campaign-Profils verwendet wird. Wählen Sie aus den Komponenten Adobe Campaign aus, sodass nur die entsprechenden Komponenten angezeigt werden.
1. Ziehen Sie die Komponente **Verschlüsselter Primärschlüssel** an eine beliebige Stelle im Formular und klicken oder tippen Sie auf Sie das Symbol für die **Konfiguration**. Geben Sie auf der Registerkarte **Adobe Campaign** einen beliebigen Namen für den URL-Parameter an. Klicken oder tippen Sie auf das Häkchen, um Ihre Änderungen zu speichern.

   Generierte Links zu diesem Formular müssen diesen URL-Parameter verwenden und ihn dem verschlüsselten Primärschlüssel eines Adobe Campaign-Profils zuweisen. Der verschlüsselte Primärschlüssel muss ordnungsgemäß URL-codiert (Prozent) sein.

   ![chlimage_1-47](assets/chlimage_1-47a.png)

1. Fügen Sie dem Formular nach Bedarf Komponenten hinzu, z. B. ein Textfeld, ein Datumsfeld, ein Kontrollkästchen, ein Optionsfeld usw. Siehe [Adobe Campaign-Formularkomponenten](/help/sites-authoring/adobe-campaign-components.md), um weitere Informationen zu den einzelnen Komponenten zu erhalten.
1. Klicken Sie auf das Symbol „Konfiguration“, um die Komponente zu öffnen. Ändern Sie beispielsweise in der Komponente **Textfeld (Kampagne)** den Titel und den Text.

   Klicken Sie auf **Adobe Campaign**, um das Formularfeld mit einer Adobe Campaign-Metadatenvariable zu verknüpfen. Wenn Sie das Formular senden, wird das zugeordnete Feld in Adobe Campaign aktualisiert. In der Variablenauswahl sind nur Felder mit übereinstimmenden Typen verfügbar (z. B. Zeichenfolgenvariablen für Textfelder).

   ![chlimage_1-48](assets/chlimage_1-48a.png)

   >[!NOTE]
   >
   >Sie können in der Empfängertabelle aufgeführte Felder wie auf der folgenden Seite beschrieben hinzufügen oder entfernen: [https://blogs.adobe.com/experiencedelivers/experience-management/aem-campaign-integration/](https://blogs.adobe.com/experiencedelivers/experience-management/aem-campaign-integration/)

1. Klicken Sie auf **Seite veröffentlichen**. Die Seite wird auf Ihrer Site aktiviert. Sie können sie anzeigen, indem Sie zu Ihrer AEM-Publishing-Instanz wechseln. Sie können auch ein [Formular testen](#testing-a-form).

   >[!CAUTION]
   >
   >Sie müssen anonymen Benutzerinnen und Benutzern im Cloud-Service Leseberechtigungen erteilen, um Formulare in der Publishing-Umgebung verwenden zu können. Beachten Sie jedoch die potenziellen Sicherheitsprobleme bei der Gewährung von Leseberechtigungen für anonyme Benutzerinnen und Benutzer und stellen Sie sicher, dass Sie diese abmildern, indem Sie beispielsweise den Dispatcher konfigurieren.

## Testen eines Formulars {#testing-a-form}

Nachdem Sie ein Formular erstellt und den Formularinhalt bearbeitet haben, können Sie manuell testen, ob das Formular erwartungsgemäß funktioniert.

>[!NOTE]
>
>Jedes Formular muss eine Komponente des Typs **Verschlüsselter Primärschlüssel** aufweisen. Wählen Sie aus den Komponenten Adobe Campaign aus, sodass nur die entsprechenden Komponenten angezeigt werden.
>
>Obwohl Sie bei diesem Verfahren die Nummer des verschlüsselten Primärschlüssels manuell eingeben, erhalten Benutzerinnen und Benutzer in der Praxis einen Link zu dieser Seite (egal ob sie sich abmelden, abonnieren oder Ihr Profil aktualisieren möchten) in einem Newsletter. Je nach Benutzerin bzw. Benutzer wird der verschlüsselte Primärschlüssel automatisch aktualisiert.
>
>Verwenden Sie zum Erstellen dieses Links die Variable **Hauptressourcenkennung** (Adobe Campaign Standard) oder **Verschlüsselte Kennung** (Adobe Campaign Classic) (beispielsweise in einer Komponente des Typs **Text und Personalisierung (Kampagne)**), die eine Verknüpfung mit dem EPK in Adobe Campaign herstellt.

Dazu müssen Sie den verschlüsselten Primärschlüssel eines Adobe Campaign-Profils manuell abrufen und an die URL anhängen:

1. So rufen Sie den verschlüsselten Primärschlüssel (EPK) eines Adobe Campaign-Profils ab:

   * Navigieren Sie in Adobe Campaign Standard zu **Profile und Zielgruppen** > **Profile**. Hier werden alle vorhandenen Profile aufgeführt. Stellen Sie sicher, dass das Feld **Hauptressourcenkennung** in einer der Spalten angezeigt wird (dies kann durch Klicken oder Tippen auf **Liste konfigurieren** eingestellt werden). Kopieren Sie die Hauptressourcenkennung des gewünschten Profils.
   * Navigieren Sie in Adobe Campaign Classic zu **Profile und Ziele** > **Empfänger**. Hier sind alle vorhandenen Profile aufgeführt. Stellen Sie sicher, dass das Feld **Verschlüsselte Kennung** in einer der Spalten angezeigt wird (dies kann durch einen Rechtsklick auf einen Eintrag und die Auswahl von **Liste konfigurieren…** eingestellt werden). Kopieren Sie die verschlüsselte Kennung des gewünschten Profils.

1. Öffnen Sie in AEM die Formularseite in der Veröffentlichungsinstanz und fügen Sie den EPK aus Schritt 1 als URL-Parameter an: Verwenden Sie den gleichen Namen, den Sie zuvor in der EPK-Komponente beim Erstellen des Formulars verwendet haben (Beispiel: `?epk=...`).
1. Mit dem Formular können jetzt die mit dem verknüpften Adobe Campaign-Profil verknüpften Daten und Abonnements geändert werden. Nachdem Sie einige Felder geändert und das Formular übermittelt haben, können Sie in Adobe Campaign überprüfen, ob die entsprechenden Daten aktualisiert wurden.

Die Daten in der Adobe Campaign-Datenbank werden aktualisiert, sobald ein Formular validiert wurde.
