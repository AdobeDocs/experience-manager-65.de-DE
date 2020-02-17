---
title: Speichern einer Aufgabe oder eines Formulars als Entwurf
seo-title: Speichern einer Aufgabe oder eines Formulars als Entwurf
description: Schritte zum Speichern eines Entwurfs für eine Aufgabe oder ein Formular in der AEM Forms-App
seo-description: Schritte zum Speichern eines Entwurfs für eine Aufgabe oder ein Formular in der AEM Forms-App
uuid: 1192d2c2-05a4-4a96-9015-e56111aa2646
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 9950288c-b5a2-4945-afad-be9ce2abc8e9
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Speichern einer Aufgabe oder eines Formulars als Entwurf {#saving-a-task-or-form-as-a-draft}

Bei der Option „Als Entwurf speichern“ wird ein Schnappschuss einer Aufgabe oder eines Formulars zusammen mit den Daten im dazugehörigen Formular gespeichert. Sie können einen Entwurf aus einer Vorlage erstellen. Die Entwürfe werden auf dem Mobilgerät gespeichert und mit Adobe Experience Manager Forms-Server für den späteren Abruf synchronisiert.

You can [update the form](/help/forms/using/working-with-form.md), [annotate it](/help/forms/using/add-attachments.md) with photographs, and scribble notes. Wenn Sie ein Formular aktualisieren, wird empfohlen, es als Entwurf zu speichern. Wenn Sie ein ausgefülltes Formular zu einem späteren Zeitpunkt senden möchten, kann ein gespeicherter Entwurf sehr hilfreich sein.

To enable save as draft feature for forms saved on forms portal, see [Saving an HTML5 form as a draft](/help/forms/using/saving-html5-form-draft.md).
To configure submission of adaptive forms, see [Drafts and submissions component](/help/forms/using/draft-submission-component.md). (Nicht gültig für Formulare, die mit dem AEM Forms JEE-Server synchronisiert werden.)

To create a draft, open the form and tap the **Save as Draft** ![save-as-draft](assets/save-as-draft.png). Geben Sie den Namen des Entwurfs an und tippen Sie auf **Speichern**. Der Entwurf wird im Ordner „Entwürfe“ gespeichert und mit dem Server synchronisiert. Er wird in dem Ordner „Outbox“ gespeichert, falls die Anwendung offline ist.

Falls Sie sich das entsprechende Formular anschließend aktualisieren, werden die Änderungen sofort übernommen. Wenn Sie die AEM Forms App mit dem AEM Forms-Server synchronisieren, wird der Entwurf auf den AEM Forms-Server hochgeladen. Zudem wird der Entwurf aus der Outbox in den Aufgaben- oder Entwurfsordner verschoben. Das Symbol „Bearbeiten“ wird daneben angezeigt.

Während Sie weiterhin mehrere Aufgaben und Startpunkte bearbeiten und speichern, werden diese Entwürfe gespeichert. Jedes Mal, wenn Sie Ihre App mit den AEM Forms-Server synchronisieren, wird der Entwurf auf dem Server gespeichert. Dadurch wird sichergestellt, dass Sie Ihre Entwürfe jederzeit im Zustand des zuletzt gespeicherten Zeitpunkts wiederherstellen können. Wenn Sie beispielsweise die App neu installieren oder Ihr mobiles Gerät austauschen, können Sie den Entwurf vom Server herunterladen.

## Löschen von Entwürfen {#delete-a-draft}

Der Ordner „Entwürfe“ enthält alle Entwürfe. Sie können die Option „Entwurf löschen“ verwenden, um die Entwürfe dauerhaft vom Gerät bzw. Server zu löschen.

Die Option, Entwürfe aus einer Aufgabe zu löschen, ist nicht verfügbar. Beim Löschen eines Entwurfs einer Aufgabe wird die Aufgabe verlassen.

Sie können Entwürfe in Online- und im Offlinemodus verwerfen. Beim Verwerfen von Entwürfen im Offline-Modus werden die Entwürfe erst vom Server gelöscht, wenn die Verbindung zum Server wiederhergestellt wird.

Führen Sie die folgenden Schritte aus, um einen Entwurf zu löschen:

1. In the AEM Forms app, navigate to **Forms.**
1. Select **Drafts** from the drop-down next to Search.
1. A form with the edit icon ![edit-draft-app](assets/edit-draft-app.png) denotes a draft. Tippen Sie auf das horizontale Auslassungszeichen neben dem Entwurf.
1. Wählen Sie in den Optionen, die angezeigt werden, wenn Sie auf das horizontale Auslassungszeichen tippen, **Entwurf löschen**.

**[Support kontaktieren](https://www.adobe.com/account/sign-in.supportportal.html)**
