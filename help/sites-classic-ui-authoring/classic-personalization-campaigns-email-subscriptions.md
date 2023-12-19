---
title: Verwalten von Abonnements
description: Benutzer können über die Formular-Komponente auf einer AEM-Webseite gebeten werden, Mailing-Listen eines E-Mail-Dienstanbieters zu abonnieren. Damit Sie eine AEM-Seite mit einem Abonnementformular erstellen können, das für die Anmeldung bei Mailing-Listen Ihres E-Mail-Diensts konfiguriert ist, müssen Sie die entsprechende Dienstkonfiguration auf die AEM-Seite anwenden, die der potenzielle Abonnent besuchen wird.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
exl-id: add05d22-3a11-49e9-a554-2315962552d5
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '917'
ht-degree: 98%

---

# Verwalten von Abonnements{#managing-subscriptions}

>[!NOTE]
>
>Adobe plant nicht, diese Funktionen (Lead- und Listenverwaltung) weiter auszubauen.
>Es wird empfohlen, [Adobe Campaign und seine AEM](/help/sites-administering/campaign.md).

Benutzer können über die Komponente **Formular** auf einer AEM-Web-Seite gebeten werden, Mailing-Listen eines **E-Mail-Dienstanbieters** zu abonnieren. Damit Sie eine AEM-Seite mit einem Abonnementformular erstellen können, das für die Anmeldung bei Mailing-Listen Ihres E-Mail-Diensts konfiguriert ist, müssen Sie die entsprechende Dienstkonfiguration auf die AEM-Seite anwenden, die der potenzielle Abonnent besuchen wird.

## Anwenden der E-Mail-Dienstkonfiguration auf eine Seite {#applying-email-service-configuration-to-a-page}

So konfigurieren Sie eine AEM-Seite:

1. Navigieren Sie zur Registerkarte **Websites**.
1. Wählen Sie die Seite, die für den Dienst konfiguriert werden soll. Klicken Sie mit der rechten Maustaste auf die Seite und wählen Sie **Eigenschaften** aus.

1. Wählen Sie **Cloud-Services** und **Service hinzufügen** aus. Wählen Sie eine Konfiguration aus der Liste der verfügbaren Konfigurationen aus.

   ![chlimage_1-164](assets/chlimage_1-164.png)

1. Klicken Sie auf **OK**.

## Erstellen von Abonnementformularen auf einer AEM-Seite für das Abonnieren/Abbestellen von Listen {#creating-a-sign-up-form-on-an-aem-page-for-subscribing-unsubscribing-to-lists}

So erstellen Sie ein Abonnementformular und konfigurieren es für die Anmeldung bei Mailing-Listen von E-Mail-Dienstleistern:

1. Öffnen Sie die AEM-Seite, die besucht werden wird.
1. Wenden Sie die Konfiguration des E-Mail-Dienstanbieters auf die Seite an.

1. Fügen Sie eine Komponente des Typs **Formular** hinzu, indem Sie sie aus dem Sidekick auf die Seite ziehen. Wenn die Komponente nicht verfügbar ist, wechseln Sie in den Designmodus und aktivieren Sie die **Formulargruppe**.
1. Klicken Sie in der Leiste **Beginn des Formulars** auf **Bearbeiten** und navigieren Sie zur Registerkarte **Erweitert**.
1. Wählen Sie im Dropdown-Menü **Formular** die Option **E-Mail-Dienst: Abonnenten erstellen und zu Liste hinzufügen** aus.
1. Öffnen Sie unten im Dialogfeld die Dropdown-Liste **Aktionskonfiguration**, in der Sie eine oder mehrere Abonnementlisten auswählen können.
1. Wählen Sie unter **Liste auswählen** die Liste aus, bei der sich Benutzer anmelden sollen. Über die Schaltfläche mit dem Plus (**Element hinzufügen**) können Sie mehrere Listen hinzufügen.

   ![chlimage_1-10](assets/chlimage_1-10.jpeg)

   >[!NOTE]
   >
   >Ihr Dialogfeld unterscheidet sich je nach E-Mail-Dienstleister möglicherweise vom hier beschriebenen.

1. Wählen Sie auf der Registerkarte **Formular** die Dankeseite aus, auf die Benutzende nach Absenden des Formulars weitergeleitet werden sollen (wird dieses Feld leer gelassen, wird nach dem Absenden erneut das Formular angezeigt). Klicken Sie auf **OK**. Im Formular wird eine **E-Mail-ID**-Komponente angezeigt, mit deren Hilfe Sie ein Formular erstellen können, in das Benutzende ihre E-Mail-Adresse zur Anmeldung oder Abmeldung aus der Mailingliste eingeben können.
1. Fügen Sie im Sidekick die Schaltflächenkomponente **Senden** für das **Formular** hinzu.

   Ihr Formular ist fertig. Veröffentlichen Sie die in den oben genannten Schritten konfigurierte Seite gemeinsam mit der **Dankeseite** in der Veröffentlichungsinstanz. Alle potenziellen Abonnentinnen und Abonnenten, die die Seite besuchen, können das Formular ausfüllen und sich bei der in der Konfiguration angegebenen Liste anmelden.

   >[!NOTE]
   >
   >Damit das Abonnieren über das Formular ordnungsgemäß funktioniert, [müssen die Verschlüsselungsschlüssel aus der Autoreninstanz exportiert und in die Veröffentlichungsinstanz importiert werden](#exporting-keys-from-author-and-importing-on-publish).

## Exportieren der Schlüssel aus der Autoreninstanz und Importieren in die Veröffentlichungsinstanz {#exporting-keys-from-author-and-importing-on-publish}

Damit das Abonnieren und Abbestellen von E-Mail-Diensten über Abonnementformulare auf Veröffentlichungsinstanzen funktioniert, müssen Sie die folgenden Schritte ausführen:

1. Navigieren Sie in der Autoreninstanz zum Package Manager.
1. Erstellen Sie ein Paket. Wählen Sie den Filter `/etc/key` aus.
1. Erstellen Sie das Paket und laden Sie es herunter.
1. Navigieren Sie in der Veröffentlichungsinstanz zum Package Manager und laden Sie dieses Paket hoch.
1. Navigieren Sie zu der OSGi-Konsole für die Veröffentlichung und starten Sie das Bundle **„Adobe Granite Crypto Support“** neu.

## Abmelden von Benutzenden aus Listen {#unsubscribing-users-from-lists}

So melden Sie Benutzende aus Listen ab:

1. Öffnen Sie die Seiteneigenschaften der AEM-Seite, die das Anmeldeformular enthält, über das sich ein Lead abmelden kann.
1. Wenden Sie die Dienst-Konfiguration auf die Seite an.
1. Erstellen Sie ein Abonnementformular auf der Seite.
1. Während Sie die Komponente konfigurieren, wählen Sie die Aktion **E-Mail-Dienst**: **Benutzer von Liste entfernen** aus.
1. Wählen Sie in der Dropdown-Liste die Liste, von der der Benutzer beim Abmelden gelöscht wird.

   ![chlimage_1-11](assets/chlimage_1-11.jpeg)

1. Exportieren Sie die Schlüssel des Autors zur Veröffentlichung.

## Konfigurieren von automatischen Antwort-E-Mails für einen E-Mail-Dienst {#configuring-auto-responder-emails-for-email-service}

So konfigurieren Sie eine automatische Antwort-E-Mail für einen E-Mail-Dienst:

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

   Das Anmeldeformular ist jetzt einsatzbereit.  Veröffentlichen Sie die in den oben genannten Schritten konfigurierte Seite gemeinsam mit der **Dankeseite** in der Veröffentlichungsinstanz. Alle potenziellen Abonnentinnen und Abonnenten, die die Seite besuchen, können das Formular ausfüllen. Beim Absenden des Formulars erhält die Person eine automatische Antwort an die E-Mail-Adresse, die sie im Formular angegeben hat.

   >[!NOTE]
   >
   >Damit das Abonnieren eines Anmeldeformulars ordnungsgemäß funktioniert, [müssen die Verschlüsselungsschlüssel aus der Autoreninstanz exportiert und in die Veröffentlichungsinstanz importiert werden](#exporting-keys-from-author-and-importing-on-publish).

   ![chlimage_1-12](assets/chlimage_1-12.jpeg)
