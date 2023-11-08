---
title: Veröffentlichen von E-Mails bei E-Mail-Dienstanbietern
seo-title: Publishing an Email to Email Service Providers
description: Sie können Newsletter in E-Mail-Diensten wie ExactTarget und Silverpop Engage veröffentlichen.
seo-description: You can publish newsletters to e-mail services such as ExactTarget and Silverpop Engage.
uuid: 1a7adcfe-8e52-49f4-9a00-99ac99881225
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: b9618913-5433-4baf-9ff6-490a26860505
exl-id: c07692f7-3618-4e8c-96d7-4db09f2d9896
source-git-commit: 38f0496d9340fbcf383a2d39dba8efcbdcd20c6f
workflow-type: tm+mt
source-wordcount: '1105'
ht-degree: 54%

---

# Veröffentlichen von E-Mails bei E-Mail-Dienstanbietern{#publishing-an-email-to-email-service-providers}

Sie können Newsletter in E-Mail-Diensten wie ExactTarget und Silverpop Engage veröffentlichen. In diesem Dokument wird beschrieben, wie Sie AEM konfigurieren, um einen Newsletter in diesen E-Mail-Diensten zu veröffentlichen.

>[!NOTE]
>
>Sie müssen den Dienstanbieter zunächst konfigurieren, bevor Sie E-Mails verfassen und veröffentlichen können. Weitere Informationen finden Sie unter [Konfigurieren von ExactTarget](/help/sites-administering/exacttarget.md) und [Konfigurieren von Silverpop Engage](/help/sites-administering/silverpop.md).

Um Ihre E-Mail beim E-Mail-Dienstleister zu veröffentlichen, müssen Sie die folgenden Schritte ausführen:

1. Erstellen Sie eine E-Mail.
1. Wenden Sie die E-Mail-Dienstkonfiguration auf die E-Mail an.
1. Veröffentlichen Sie die E-Mail.

>[!NOTE]
>
>Wenn Sie E-Mail-Anbieter aktualisieren, einen Testlauf durchführen oder einen Newsletter versenden, schlagen diese Vorgänge fehl, wenn der Newsletter nicht zuerst in der Publishing-Instanz veröffentlicht wird oder die Publishing-Instanz nicht verfügbar ist. Stellen Sie sicher, dass Sie Ihren Newsletter veröffentlichen und die Publishing-Instanz ordnungsgemäß funktioniert.

## E-Mail erstellen {#creating-an-email}

Sie können eine E-Mail oder einen Newsletter, die oder den Sie in einem E-Mail-Dienst veröffentlichen möchten, in Kampagnen mithilfe der Vorlage **Geometrixx-Newsletter** erstellen. Alternativ können Sie auch die Vorlage **Geometrixx Outdoors-E-Mail** verwenden. Beispiel-E-Mails oder -Newsletter, die auf der Vorlage **Geometrixx Outdoors-E-Mail** basieren, finden Sie unter `https://<hostname>:<port>/cf#/content/campaigns/geometrixx-outdoors/e-mails.html`.

So erstellen Sie eine E-Mail, die im konfigurierten E-Mail-Dienst veröffentlicht wird:

1. Gehen Sie zu **Websites** und dann zu **Kampagnen**. Wählen Sie eine Kampagne.
1. Wählen Sie **Neu**, um das Fenster **Seite erstellen** zu öffnen.
1. Geben Sie den Titel und den Namen ein und wählen Sie die **Geometrixx Newsletter** Vorlage aus der Liste der verfügbaren Vorlagen.
1. Klicken Sie auf **Erstellen**.
1. Öffnen Sie die erstellte E-Mail.
1. Wechseln Sie zum Designmodus und wählen Sie die Komponenten aus, die Sie im Sidekick anzeigen möchten.
1. Wechseln Sie in den Bearbeitungsmodus und beginnen Sie damit, Ihrer E-Mail Inhalte (Text, Bilder, [E-Mail-Tools](#adding-exacttarget-email-tools-to-your-email), [Personalisierungsvariablen](#adding-text-and-personalization-tool-to-your-e-mail) usw.) hinzuzufügen.

### Hinzufügen von ExactTarget-E-Mail-Tools zu Ihrer E-Mail {#adding-exacttarget-email-tools-to-your-email}

>[!NOTE]
>
>Dieser Abschnitt ist spezifisch für den ExactTarget-Dienst.

Mit der Komponente **E-Mail-Tools** für ExactTarget können Sie Ihrer E-Mail/Ihrem Newsletter zusätzliche E-Mail-Funktionen hinzufügen.

1. Öffnen Sie eine E-Mail, die in ExactTarget veröffentlicht werden soll.
1. Fügen Sie Ihrer Seite über den Sidekick die Komponente **ET - E-Mail-Tools** hinzu. Öffnen Sie die Komponente im Bearbeitungsmodus.

   ![chlimage_1](assets/chlimage_1.gif)

1. Wählen Sie eine Option aus dem **Optionen** Menü:

<table>
 <tbody>
  <tr>
   <td>Postanschrift (Erforderlich)</td>
   <td>Diese Komponente fügt die physische Postanschrift Ihres Unternehmens in Ihre E-Mail ein.</td>
  </tr>
  <tr>
   <td>Profilzentrum (Erforderlich)</td>
   <td>Das Profilzentrum ist eine Webseite, auf der Abonnenten die persönlichen Daten, die Sie über sie behalten, eingeben und verwalten können.</td>
  </tr>
  <tr>
   <td>E-Mail als Webseite anzeigen</td>
   <td>Mit dieser Komponente kann der Benutzer die E-Mail als Webseite anzeigen.</td>
  </tr>
  <tr>
   <td>Datenschutzrichtlinie</td>
   <td>Diese Komponente fügt den Link zu Ihrer Datenschutzrichtlinie in die E-Mail ein.<br /> </td>
  </tr>
  <tr>
   <td>Abmeldungszentrum</td>
   <td>Gibt dem Benutzer die Möglichkeit, sich von Ihrer Mailingliste abzumelden.</td>
  </tr>
  <tr>
   <td>Abonnementzentrum</td>
   <td>Ein Abonnementzentrum ist eine Web-Seite, auf der ein Abonnent festlegen kann, welche Mitteilungen er von Ihrem Unternehmen erhalten möchte.</td>
  </tr>
  <tr>
   <td>Öffnen der E-Mail verfolgen</td>
   <td>Eine verborgene Komponente, mit der Sie die ExactTarget-Tracking-Funktion verwenden können.<br /> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Das Dropdown-Menü **Optionen** enthält nur dann Einträge, wenn eine ExactTarget-Konfiguration auf die E-Mail angewendet wurde. Weitere Informationen finden Sie unter [Anwenden von E-Mail-Dienstkonfigurationen auf E-Mail-Einstellungen](#applying-e-mail-service-configuration-to-e-mail-settings).

1. Veröffentlichen Sie die E-Mail in ExactTarget.

   Die E-Mail mit den E-Mail-Tools kann im konfigurierten ExactTarget-Konto verwendet werden.

>[!NOTE]
>
>* Die URLs innerhalb der E-Mail-Tools werden (in der empfangenen E-Mail) nur dann durch die eigentlichen Werte ersetzt, wenn die E-Mail über **einfachen** oder **geführten Versand** versendet wird, nicht jedoch beim **Testversand**.
>
>* Zwei der E-Mail-Tools sind erforderlich: **Postanschrift (Erforderlich)** und **Profilzentrum (Erforderlich)**. Wenn die E-Mail in ExactTarget veröffentlicht wird, werden diese beiden E-Mail-Tools standardmäßig am Ende jeder E-Mail hinzugefügt.
>

### Hinzufügen des Tools &quot;Text und Personalisierung&quot;zu Ihrer E-Mail {#adding-text-and-personalization-tool-to-your-e-mail}

Sie können in einer E-Mail personalisierte Felder hinzufügen, indem Sie die **Text und Personalisierung** -Komponente auf der Seite:

1. Öffnen Sie die E-Mail, die in Ihrem E-Mail-Dienst veröffentlicht werden soll.
1. Möchten Sie in Ihrem E-Mail-Dienst benutzerdefinierte Felder freischalten, fügen Sie bei dessen Einrichtung die Framework-Konfiguration hinzu. Weitere Informationen finden Sie unter [Konfigurieren von Silverpop Engage](/help/sites-administering/silverpop.md) und [Konfigurieren von ExactTarget](/help/sites-administering/exacttarget.md).
1. Fügen Sie die Komponente **Text und Personalisierung** aus dem Sidekick hinzu. Diese Komponente ist Teil der Newsletter-Gruppe. Öffnen Sie diese Komponente im Bearbeitungsmodus.

   ![chlimage_1-110](assets/chlimage_1-110a.png)

1. Fügen Sie die erforderlichen personalisierten Felder hinzu, indem Sie die entsprechenden Felder aus dem Dropdown-Menü auswählen und auf **Einfügen** klicken.
1. Klicken Sie auf **OK**, um den Vorgang abzuschließen.

## Anwenden der E-Mail-Dienstkonfiguration auf E-Mail-Einstellungen {#applying-e-mail-service-configuration-to-e-mail-settings}

So wenden Sie Ihre E-Mail-Dienstkonfiguration auf einen Newsletter an:

1. Erstellen Sie eine E-Mail-Dienstkonfiguration.
1. Öffnen Sie die E-Mail/den Newsletter.
1. Öffnen Sie die E-Mail-/Newsletter-Einstellungen, indem Sie entweder auf **Einstellungen** oder im Sidekick auf **Seiteneigenschaften** klicken.
1. Klicken Sie auf der Registerkarte **Cloud-Services** auf **Service hinzufügen**. Die Liste der Dienste wird angezeigt. Wählen Sie die gewünschte Konfiguration aus - entweder **ExactTarget** oder **Silverpop** - aus der Liste aus der Dropdown-Liste.

   ![chlimage_1-5](assets/chlimage_1-5a.jpeg)

1. Klicken Sie auf **OK**.

## Veröffentlichen von E-Mails im E-Mail-Dienst {#publishing-emails-to-email-service}

E-Mails/Newsletter können in Ihrem E-Mail-Dienst veröffentlicht werden, indem Sie die folgenden Schritte ausführen:

1. Öffnen Sie die E-Mail.
1. Bevor Sie eine E-Mail veröffentlichen, stellen Sie sicher, dass Sie die richtige Konfiguration auf Ihre E-Mail angewendet haben.
1. Klicken Sie auf **Veröffentlichen**. Das Fenster **Newsletter bei E-Mail-Dienstanbieter veröffentlichen** wird geöffnet.
1. Füllen Sie das Feld **Newsletter-Name** aus. Die E-Mail/der Newsletter wird unter diesem Namen bei E-Mail Service Provider veröffentlicht. Wenn kein E-Mail-Name angegeben wird, wird die E-Mail mit dem Seitennamen des Newsletters in AEM veröffentlicht.
1. Klicken Sie auf **Veröffentlichen**.

   ![chlimage_1-6](assets/chlimage_1-6.jpeg)

   Wenn der Vorgang erfolgreich war, erhalten Sie in AEM eine Meldung, dass Sie die E-Mail in ExactTarget oder Silverpop Engage anzeigen können.

   Wenn ExactTarget vorhanden ist, kann die veröffentlichte E-Mail durch Klicken auf **Veröffentlichte E-Mail anzeigen**. Sie werden direkt zum veröffentlichten Newsletter in ExactTarget weitergeleitet ([https://members.exacttarget.com/](https://members.exacttarget.com/)).

>[!NOTE]
>
>Wenn eine E-Mail/ein Newsletter mit demselben Namen wie eine bereits veröffentlichte E-Mail/ein bereits veröffentlichter Newsletter veröffentlicht wird, wird die frühere E-Mail/der frühere Newsletter nicht ersetzt. Stattdessen wird eine neue E-Mail/ein neuer Newsletter mit demselben Namen erstellt (die IDs zweier Newsletter unterscheiden sich jedoch).
>
>Durch Veröffentlichen der E-Mail/des Newsletters beim E-Mail-Dienstanbieter wird die E-Mail/der Newsletter auch in der AEM Veröffentlichungsinstanz veröffentlicht.
>

### Aktualisieren von veröffentlichten E-Mails {#updating-a-published-e-mail}

Mit der Schaltfläche **Aktualisieren** im Dialogfeld „Veröffentlichen“ können Sie einen bereits beim E-Mail-Dienstanbieter veröffentlichten Newsletter aktualisieren. Falls der Newsletter noch nicht veröffentlicht wurde und Sie auf die Schaltfläche **Aktualisieren** klicken, wird die Meldung **Newsletter wurde nicht veröffentlicht** angezeigt.

So aktualisieren Sie eine veröffentlichte E-Mail:

1. Öffnen Sie die E-Mail/den Newsletter, die oder der bereits in einem E-Mail-Dienstanbieter veröffentlicht wurde und die oder der nach vorgenommenen Änderungen erneut veröffentlicht werden soll.
1. Klicken Sie auf **Veröffentlichen**. Das Fenster **Newsletter bei E-Mail-Dienstanbieter veröffentlichen** wird geöffnet. Klicken Sie auf **Aktualisieren**.

   Prüfen Sie, ob die E-Mail/der Newsletter in ExactTarget aktualisiert wurde, indem Sie auf die Schaltfläche **Veröffentlichte E-Mail anzeigen** klicken. Dadurch gelangen Sie zur veröffentlichten E-Mail in ExactTarget.

   Um zu überprüfen, ob die E-Mail/der Newsletter beim Silverpop-E-Mail-Dienst aktualisiert wurde, besuchen Sie die Site Silverpop Engage .
