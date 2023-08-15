---
title: Verwalten von Abonnements
seo-title: Managing Subscriptions
description: Benutzer können über die Formular-Komponente auf einer AEM-Webseite gebeten werden, Mailing-Listen eines E-Mail-Dienstanbieters zu abonnieren. Damit Sie eine AEM-Seite mit einem Abonnementformular erstellen können, das für die Anmeldung bei Mailing-Listen Ihres E-Mail-Diensts konfiguriert ist, müssen Sie die entsprechende Dienstkonfiguration auf die AEM-Seite anwenden, die der potenzielle Abonnent besuchen wird.
seo-description: Users can be asked to subscribe to Email Service Provider's mailing lists with the help of the Form component used on an AEM web page. To prepare an AEM page with a sign-up form for subscription to your e-mail service mailing lists, you must apply the corresponding service configuration to the AEM page that the potential subscriber will visit.
uuid: b2578a3d-dba1-4114-b21a-5f34c0cccc5a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 295cb0a6-29db-42aa-824e-9141b37b5086
exl-id: add05d22-3a11-49e9-a554-2315962552d5
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '914'
ht-degree: 58%

---

# Verwalten von Abonnements{#managing-subscriptions}

>[!NOTE]
>
>Adobe plant nicht, diese Funktionen (Lead- und Listenverwaltung) weiter auszubauen.
>Die Empfehlung lautet, [Adobe Campaign und die AEM-Integration](/help/sites-administering/campaign.md) zu nutzen.

Benutzer können über die Komponente **Formular** auf einer AEM-Web-Seite gebeten werden, Mailing-Listen eines **E-Mail-Dienstanbieters** zu abonnieren. Damit Sie eine AEM-Seite mit einem Abonnementformular erstellen können, das für die Anmeldung bei Mailing-Listen Ihres E-Mail-Diensts konfiguriert ist, müssen Sie die entsprechende Dienstkonfiguration auf die AEM-Seite anwenden, die der potenzielle Abonnent besuchen wird.

## Anwenden der E-Mail-Dienstkonfiguration auf eine Seite {#applying-email-service-configuration-to-a-page}

So konfigurieren Sie eine AEM Seite:

1. Navigieren Sie zum **Websites** Registerkarte.
1. Wählen Sie die Seite, die für den Dienst konfiguriert werden soll. Klicken Sie mit der rechten Maustaste auf die Seite und wählen Sie **Eigenschaften** aus.

1. Wählen Sie **Cloud-Services** und **Service hinzufügen** aus. Wählen Sie eine Konfiguration aus der Liste der verfügbaren Konfigurationen aus.

   ![chlimage_1-164](assets/chlimage_1-164.png)

1. Klicken Sie auf **OK**.

## Erstellen eines Anmeldeformulars auf einer AEM Seite zum Abonnieren/Abmelden von Listen {#creating-a-sign-up-form-on-an-aem-page-for-subscribing-unsubscribing-to-lists}

So erstellen Sie ein Anmeldeformular und konfigurieren es für Abonnements auf den Mailinglisten des E-Mail-Dienstanbieters:

1. Öffnen Sie die AEM Seite, die der Benutzer besuchen wird.
1. Wenden Sie die Konfiguration des E-Mail-Dienstanbieters auf die Seite an.

1. Fügen Sie eine Komponente des Typs **Formular** hinzu, indem Sie sie aus dem Sidekick auf die Seite ziehen. Wenn die Komponente nicht verfügbar ist, wechseln Sie in den Designmodus und aktivieren Sie die **Formulargruppe**.
1. Klicken Sie in der Leiste **Beginn des Formulars** auf **Bearbeiten** und navigieren Sie zur Registerkarte **Erweitert**.
1. Wählen Sie im Dropdown-Menü **Formular** die Option **E-Mail-Dienst: Abonnenten erstellen und zu Liste hinzufügen** aus.
1. Öffnen Sie am unteren Rand des Dialogfelds die **Aktionskonfiguration** Dropdown-Liste, in der Sie eine oder mehrere Abonnementlisten auswählen können.
1. Wählen Sie unter **Liste auswählen** die Liste aus, bei der sich Benutzer anmelden sollen. Über die Schaltfläche mit dem Plus (**Element hinzufügen**) können Sie mehrere Listen hinzufügen.

   ![chlimage_1-10](assets/chlimage_1-10.jpeg)

   >[!NOTE]
   >
   >Ihr Dialogfeld kann je nach E-Mail-Dienstanbieter unterschiedlich sein.

1. Im **Formular** Wählen Sie die Dankeseite aus, zu der die Benutzer nach dem Senden des Formulars weitergeleitet werden sollen. (Wenn das Feld leer gelassen wird, wird das Formular bei der Übermittlung erneut angezeigt.) Klicken Sie auf **OK**. Ein **Email-ID** wird im Formular angezeigt, in dem Sie ein Formular erstellen können, über das Benutzer ihre E-Mail-Adressen zur Anmeldung oder Abmeldung von einer Mailingliste senden können.
1. Fügen Sie im Sidekick die Schaltflächenkomponente **Senden** für das **Formular** hinzu.

   Das Formular ist fertig. Veröffentlichen Sie die in den oben genannten Schritten konfigurierte Seite gemeinsam mit der **Dankeseite** in der Veröffentlichungsinstanz. Alle potenziellen Abonnenten, die die Seite besuchen, können das Formular ausfüllen und sich für die in der Konfiguration angegebene Liste anmelden.

   >[!NOTE]
   >
   >Damit das Formular-Abonnement ordnungsgemäß funktioniert, [Verschlüsselungsschlüssel des Autors müssen exportiert und in die Veröffentlichungsinstanz importiert werden](#exporting-keys-from-author-and-importing-on-publish).

## Exportieren von Schlüsseln vom Autor und Importieren in der Veröffentlichungsinstanz {#exporting-keys-from-author-and-importing-on-publish}

Damit das Abonnieren und Abmelden von E-Mail-Diensten über das Anmeldeformular in der Veröffentlichungsinstanz funktioniert, müssen Sie die folgenden Schritte ausführen:

1. Navigieren Sie in der Autoreninstanz zum Package Manager.
1. Erstellen Sie ein neues Paket. Wählen Sie den Filter `/etc/key` aus.
1. Erstellen Sie das Paket und laden Sie es herunter.
1. Navigieren Sie in der Veröffentlichungsinstanz zum Package Manager und laden Sie dieses Paket hoch.
1. Navigieren Sie zur OSGi-Konsole für die Veröffentlichung und starten Sie das Bundle mit dem Namen **Adobe Granite Crypto-Unterstützung**.

## Abmelden von Benutzern von Listen {#unsubscribing-users-from-lists}

So melden Sie Benutzer von Listen ab:

1. Öffnen Sie die Seiteneigenschaften der AEM Seite mit dem Anmeldeformular, um einen Lead abzumelden.
1. Wenden Sie die Dienstkonfiguration auf die Seite an.
1. Erstellen Sie ein Anmeldeformular auf der Seite.
1. Während Sie die Komponente konfigurieren, wählen Sie die Aktion **E-Mail-Dienst**: **Benutzer von Liste entfernen** aus.
1. Wählen Sie in der Dropdown-Liste die Liste, von der der Benutzer beim Abmelden gelöscht wird.

   ![chlimage_1-11](assets/chlimage_1-11.jpeg)

1. Exportieren Sie die Schlüssel des Autors zur Veröffentlichung.

## Konfigurieren von automatischen Benachrichtigungs-E-Mails für E-Mail-Dienst {#configuring-auto-responder-emails-for-email-service}

So konfigurieren Sie eine automatische Nachricht für einen Abonnenten:

1. Öffnen Sie die Seiteneigenschaften der AEM-Seite, auf der sich das Anmeldeformular befindet, um die automatische Antwort für Leads zu konfigurieren.
1. Wenden Sie die ExactTarget-Konfiguration auf die Seite an.

1. Fügen Sie eine Komponente des Typs **Formular** hinzu, indem Sie sie aus dem Sidekick auf die Seite ziehen. Wenn die Komponente nicht verfügbar ist, wechseln Sie in den Designmodus und aktivieren Sie die **Formulargruppe**.
1. Klicken Sie in der Leiste **Beginn des Formulars** auf **Bearbeiten** und navigieren Sie zur Registerkarte **Erweitert**.
1. Wählen Sie im Dropdown-Menü **Formular** die Option **E-Mail-Dienst: Abwesenheitsnachricht senden** aus.
1. **Wählen Sie eine E-Mail aus** (dies ist die E-Mail, die als automatische Antwort gesendet wird).

1. **Wählen Sie eine Klassifikation aus** (diese Klassifikation wird zum Versenden der E-Mail verwendet).
1. Wählen Sie die **Dankeseite** aus (die Seite, auf die Benutzer weitergeleitet werden, wenn sie das Formular senden).

   Wählen Sie auf der Registerkarte **Formular** die Dankeseite aus, die Benutzer sehen sollen, nachdem sie das Formular gesendet haben. (Erfolgt hier keine Angabe, wird das Formular nach der Übermittlung erneut angezeigt.) Klicken Sie auf **OK**.

1. Exportieren Sie die Schlüssel des Autors zur Veröffentlichung.
1. Fügen Sie im Sidekick die Schaltflächenkomponente **Senden** für das **Formular** hinzu.

   Das Anmeldeformular ist fertig. Veröffentlichen Sie die in den oben genannten Schritten konfigurierte Seite gemeinsam mit der **Dankeseite** in der Veröffentlichungsinstanz. Jeder potenzielle Abonnent, der die Seite besucht, kann das Formular ausfüllen und beim Senden des Formulars erhält der Besucher eine automatische Nachricht auf die E-Mail-Adresse, die im Formular ausgefüllt ist.

   >[!NOTE]
   >
   >Damit das Abonnement des Anmeldeformulars ordnungsgemäß funktioniert, [Verschlüsselungsschlüssel des Autors müssen exportiert und in die Veröffentlichungsinstanz importiert werden](#exporting-keys-from-author-and-importing-on-publish).

   ![chlimage_1-12](assets/chlimage_1-12.jpeg)
