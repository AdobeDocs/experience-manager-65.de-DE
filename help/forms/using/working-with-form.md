---
title: Arbeiten mit einem Formular
description: Anzeigen und Aktualisieren des mit einer Aufgabe oder einem Startpunkt in der AEM Forms-App verknüpften Formulars
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: adff5339-e026-4924-a401-f249f37fc6e6
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '414'
ht-degree: 100%

---

# Arbeiten mit einem Formular {#working-with-a-form}

Wenn ein Formular für die Synchronisierung in der Forms-App aktiviert ist, wird das Formular heruntergeladen und Sie können es direkt bearbeiten.

Die Formulare werden in Ihre App heruntergeladen und sind offline verfügbar. Angenommen, Sie haben ein Bankgeschäft und ein Kunde füllt auf Ihrer Website einen Antrag aus. Der Antrag ist ein adaptives Formular, in das Ihre Kundschaft Daten einträgt, die dann zur Prüfung gespeichert werden. Die Administratorin oder der Administrator überprüft das Formular und erstellt ein Überprüfungsformular in der AEM-Autoreninstanz. Die Administratorin oder der Administrator aktiviert die Synchronisierung des Formulars mit der AEM Forms-App. Wenn das Überprüfungsformular in der AEM Forms-App verfügbar ist, kann jemand in Ihrem Außendienst die Angaben der Kundin oder des Kunden auf einem Mobilgerät überprüfen. Das Mobilgerät wird mit dem Server synchronisiert und das Überprüfungsformular in der App geladen. Ihre Außendienstmitarbeiterin bzw. Ihr Außendienstmitarbeiter kann die Kundschaft besuchen, die Angaben überprüfen und die Daten als Entwurf speichern oder das Überprüfungsformular übermitteln. Das Formular wird jedes Mal, wenn Ihre App online ist, mit dem Server synchronisiert.

Formular in der AEM Forms-App synchronisieren

1. Wählen Sie in der Autoreninstanz ein Formular aus und klicken Sie auf **Eigenschaften anzeigen**.
1. Klicken Sie auf der Eigenschaftenseite auf **Erweitert**.
1. Aktivieren Sie unter „Erweitert“ die Option **Mit AEM Forms-App synchronisieren** und wählen Sie **Speichern** aus.

Um mehrere Formulare zu synchronisieren, wählen Sie in der Autoreninstanz mehrere Formulare in Forms Manager und dann **Mit AEM Forms-App synchronisieren** aus. Wenn das Formular veröffentlicht wird, wird die AEM Forms App mit dem Server synchronisiert und ruft die Formulare ab.

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
>* Mobile-Formulare
>
>Anhänge auf Formularebene werden für adaptive Formulare, die in der AEM Forms-App mit einem AEM Forms OSGi-Server synchronisiert werden, nicht unterstützt. Benutzende können Dateien in einem Feld anhängen, wenn die Autorin oder der Autor zum Zeitpunkt des Verfassens des Formulars Anhänge auf Feldebene aktiviert hat.


**Öffnen und Aktualisieren eines Formulars**

1. Um ein Formular zu öffnen, wählen Sie auf dem Startbildschirm **[!UICONTROL Formular]** aus.
1. Sie können die Felder des Formulars aktualisieren, Anlagen auf Feldebene hinzufügen, das Formular als Entwurf speichern und es absenden.
