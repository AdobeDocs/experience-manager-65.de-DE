---
title: Verwenden der automatischen Speicherung in der AEM Forms-App
seo-title: Verwenden der automatischen Speicherung in der AEM Forms-App
description: Erfahren Sie, wie Sie in der AEM-App die automatische Speicherung verwenden, mit der Sie Datenverlust vermeiden können.
seo-description: Erfahren Sie, wie Sie in der AEM-App die automatische Speicherung verwenden, mit der Sie Datenverlust vermeiden können.
uuid: 00fe6a10-1a72-443d-a840-0415dc769199
contentOwner: sashanka
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 2c71cc28-b7c8-4785-9fc2-b47fa80cbd70
docset: aem65
translation-type: tm+mt
source-git-commit: d9975c0dcc02ae71ac64aadb6b4f82f7c993f32c

---


# Verwenden der automatischen Speicherung in der AEM Forms-App{#using-autosave-in-aem-forms-app}

Wenn ein Benutzer Daten in die Adobe Experience Manager Forms-App eingibt, speichert die Funktion sie automatisch in regelmäßigen Abständen. Die automatische Speicherung in der AEM Forms-App hilft Ihnen, Datenverlust zu vermeiden, wenn die App versehentlich geschlossen wird.

Ihre App wird versehentlich geschlossen:

* Wenn sich Ihr Gerät aufgrund niedrigem Akku ausschaltet
* Wenn der Benutzer die App abbricht
* Wenn ein unerwarteter Absturz auftritt

Sie können die Intervalle angeben, in denen die App die eingegebenen Daten speichert.

>[!NOTE]
>
>Wählen Sie den Wert sorgfältig aus. Eine häufige automatische Speicherung kann spürbare Auswirkungen auf die Leistung Ihres Geräts haben.

Führen Sie die folgenden Schritte aus, um die automatische Speicherung in der AEM Forms-App zu verwenden:

1. Melden Sie sich bei der App und navigieren Sie zu **„Settings“ > „General“**.
1. In the General screen, use the **Autosave Frequency** option to select the intervals at which you want the app to save the entered data.
   [![Einstellung „Autosave Frequency“](assets/using-autosave-freq-07.png)](assets/using-autosave-freq-07-1.png)

1. Wenn Sie die App neu starten und sich als derselbe Benutzer anmelden, werden Sie aufgefordert, Ihre Aufgabe mit dem Dialogfeld „Nicht gespeicherte Aufgabe wiederherstellen“ wiederherzustellen. Click **OK** in the Recover Unsaved Task dialog to resume working with the saved task. Klicken Sie auf **Abbrechen**, um die gespeicherten Daten entsprechend der zuletzt ausgelösten automatischen Speicherung zu löschen und an einer neuen Aufgabe zu arbeiten.

   Wenn Sie auf **OK** klicken, wird die Aufgabe mit den Daten entsprechend der zuletzt ausgelösten automatischen Speicherung vor Absturz der App wiederhergestellt. Es enthält die Formulardaten und alle mit der Aufgabe verknüpften Anlagen.
   [![](assets/autosave-flow.png)](assets/using-autosave-freq-06.png)****Aufgabe** wiederherstellen **A. Ein derzeit bearbeitetes Formular** B. App wurde **C.** App mit dem Dialogfeld &quot;Nicht gespeicherte Aufgabe wiederherstellen&quot; **D erneut gestartet. Formular mit Originaldaten wiederhergestellt

