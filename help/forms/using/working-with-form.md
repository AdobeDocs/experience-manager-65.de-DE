---
title: Arbeiten mit einem Formular
description: Anzeigen und Aktualisieren des mit einer Aufgabe oder einem Startpunkt verknüpften Formulars in der AEM Forms-App
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: adff5339-e026-4924-a401-f249f37fc6e6
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 38%

---

# Arbeiten mit einem Formular {#working-with-a-form}

Wenn ein Formular für die Synchronisierung in der Forms-App aktiviert ist, wird das Formular heruntergeladen und Sie können es direkt bearbeiten.

Die Formulare werden in Ihre App heruntergeladen und sind offline verfügbar. Angenommen, Sie haben ein Bankgeschäft und ein Kunde füllt auf Ihrer Website einen Antrag aus. Der Antrag ist ein adaptives Formular, das Informationen von Ihren Kunden akzeptiert und zur Überprüfung speichert. Der Administrator überprüft das Formular und erstellt ein Überprüfungsformular in AEM Autoreninstanz. Der Administrator aktiviert die Synchronisierung des Formulars mit der AEM Forms-App. Wenn das Überprüfungsformular in der AEM Forms-App verfügbar ist, kann Ihr Außendienstmitarbeiter die Kundendetails mithilfe eines Mobilgeräts überprüfen. Das Mobilgerät wird mit dem Server synchronisiert und das Überprüfungsformular wird in die App geladen. Ihr Außendienstmitarbeiter kann Ihren Kunden besuchen, die Details überprüfen, Daten als Entwurf speichern oder das Überprüfungsformular übermitteln. Das Formular wird jedes Mal, wenn Ihre App online ist, mit dem Server synchronisiert.

Formular in der AEM Forms-App synchronisieren

1. Wählen Sie in der Autoreninstanz ein Formular aus und klicken Sie auf **Eigenschaften anzeigen**.
1. Klicken Sie auf der Eigenschaftenseite auf **Erweitert**.
1. Aktivieren Sie unter &quot;Erweitert&quot;die Option: **Mit AEM Forms App synchronisieren** und wählen Sie **Speichern**.

Um mehrere Formulare zu synchronisieren, wählen Sie in der Autoreninstanz mehrere Formulare im Forms Manager aus und wählen Sie **Mit AEM Forms App synchronisieren**. Wenn das Formular veröffentlicht wird, wird die AEM Forms App mit dem Server synchronisiert und ruft das Formular ab.

Wenn Ihre AFA (AEM Form Application) Android-App nicht synchronisiert werden kann, führen Sie die folgenden Schritte aus, um das Synchronisierungsproblem zu beheben:

1. Navigieren Sie zu **https://[server]:[port]/system/console/configMgr**.
1. Suchen Sie nach dem **[!UICONTROL Adobe Granite-Token-Authentifizierungs-Handler]** und klicken Sie auf **[!UICONTROL Bearbeiten]**.
1. Wählen Sie die Option **[!UICONTROL Keine]** aus dem Dropdown-Menü für das Attribut **[!UICONTROL SameSite für das Login-Token-Cookie]**.
1. Klicken Sie auf **[!UICONTROL Speichern]**.

![Synchronisieren des Bildes mit der AFA Android-App](/help/forms/using/assets/afaandroid.png)

>[!NOTE]
>
>Unterstützte Formulare:
>
>* Adaptive Formulare (ohne verzögertes Laden)
>* Mobile Forms
>
>Anlagen auf Formularebene werden in den adaptiven Formularen, die in der mit dem AEM Forms OSGi-Server synchronisierten AEM Forms-App abgerufen werden, nicht unterstützt. Benutzer können Dateien in einem Feld anhängen, wenn der Autor zum Zeitpunkt der Formularbearbeitung Anlagen auf Feldebene aktiviert hat.


**So öffnen und aktualisieren Sie ein Formular**

1. Um ein Formular zu öffnen, wählen Sie die **[!UICONTROL Formular]** im Startbildschirm.
1. Sie können die Felder des Formulars aktualisieren, Anlagen auf Feldebene hinzufügen, das Formular als Entwurf speichern und es senden.
