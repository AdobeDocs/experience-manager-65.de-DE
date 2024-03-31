---
title: Veröffentlichen von E-Mails bei E-Mail-Dienstanbietern
description: Sie können Newsletter in E-Mail-Diensten wie ExactTarget und Silverpop Engage veröffentlichen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
exl-id: c07692f7-3618-4e8c-96d7-4db09f2d9896
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1106'
ht-degree: 100%

---

# Veröffentlichen von E-Mails bei E-Mail-Dienstanbietern{#publishing-an-email-to-email-service-providers}

Sie können Newsletter in E-Mail-Diensten wie ExactTarget und Silverpop Engage veröffentlichen. In diesem Dokument wird beschrieben, wie Sie AEM zum Veröffentlichen eines Newsletters in diesen E-Mail-Diensten konfigurieren.

>[!NOTE]
>
>Sie müssen den Dienstanbieter zunächst konfigurieren, bevor Sie E-Mails verfassen und veröffentlichen können. Weitere Informationen finden Sie unter [Konfigurieren von ExactTarget](/help/sites-administering/exacttarget.md) und [Konfigurieren von Silverpop Engage](/help/sites-administering/silverpop.md).

Zur Veröffentlichung einer Mail beim E-Mail-Dienstanbieter müssen Sie wie folgt vorgehen:

1. Erstellen Sie eine E-Mail.
1. Wenden Sie die E-Mail-Dienstkonfiguration auf die E-Mail an. 
1. Veröffentlichen Sie die E-Mail.

>[!NOTE]
>
>Wenn Sie E-Mail-Anbieter aktualisieren, einen Testlauf durchführen oder einen Newsletter versenden, schlagen diese Vorgänge fehl, wenn der Newsletter nicht zuerst in der Publishing-Instanz veröffentlicht wird oder die Publishing-Instanz nicht verfügbar ist. Stellen Sie sicher, dass Sie Ihren Newsletter veröffentlichen und die Publishing-Instanz ordnungsgemäß funktioniert.

## Erstellen einer E-Mail {#creating-an-email}

Sie können eine E-Mail oder einen Newsletter, die oder den Sie in einem E-Mail-Dienst veröffentlichen möchten, in Kampagnen mithilfe der Vorlage **Geometrixx-Newsletter** erstellen. Alternativ können Sie auch die Vorlage **Geometrixx Outdoors-E-Mail** verwenden. Beispiel-E-Mails oder -Newsletter, die auf der Vorlage **Geometrixx Outdoors-E-Mail** basieren, finden Sie unter `https://<hostname>:<port>/cf#/content/campaigns/geometrixx-outdoors/e-mails.html`.

So erstellen Sie eine neue E-Mail, die im konfigurierten E-Mail-Dienst veröffentlicht wird:

1. Gehen Sie zu **Websites** und dann zu **Kampagnen**. Wählen Sie eine Kampagne.
1. Wählen Sie **Neu**, um das Fenster **Seite erstellen** zu öffnen.
1. Geben Sie den Titel sowie den Namen ein und wählen Sie in der Liste der verfügbaren Vorlagen den **Geometrixx-Newsletter** aus.
1. Klicken Sie auf **Erstellen**.
1. Öffnen Sie die erstellte E-Mail.
1. Wechseln Sie zum Designmodus und wählen Sie die Komponenten aus, die Sie im Sidekick anzeigen möchten.
1. Wechseln Sie in den Bearbeitungsmodus und beginnen Sie damit, Ihrer E-Mail Inhalte (Text, Bilder, [E-Mail-Tools](#adding-exacttarget-email-tools-to-your-email), [Personalisierungsvariablen](#adding-text-and-personalization-tool-to-your-e-mail) usw.) hinzuzufügen.

### Hinzufügen von ExactTarget-E-Mail-Tools zu Ihrer E-Mail {#adding-exacttarget-email-tools-to-your-email}

>[!NOTE]
>
>Dieser Abschnitt beschäftigt sich speziell mit dem ExactTarget-Dienst.

Mit der Komponente **E-Mail-Tools** für ExactTarget können Sie Ihrer E-Mail/Ihrem Newsletter zusätzliche E-Mail-Funktionen hinzufügen.

1. Öffnen Sie eine E-Mail, die in ExactTarget veröffentlicht werden soll.
1. Fügen Sie Ihrer Seite über den Sidekick die Komponente **ET - E-Mail-Tools** hinzu. Öffnen Sie die Komponente im Bearbeitungsmodus.

   ![chlimage_1](assets/chlimage_1.gif)

1. Wählen Sie im Menü **Optionen** eine Option aus:

<table>
 <tbody>
  <tr>
   <td>Postanschrift (Erforderlich)</td>
   <td>Mit dieser Komponente wird die Postanschrift Ihres Unternehmens in die E-Mail eingefügt.</td>
  </tr>
  <tr>
   <td>Profilzentrum (Erforderlich)</td>
   <td>Das Profilzentrum ist eine Web-Seite, auf der Abonnentinnen und Abonnenten die persönlichen Daten, die Sie über sie speichern, eingeben und verwalten können.</td>
  </tr>
  <tr>
   <td>E-Mail als Webseite anzeigen</td>
   <td>Mit dieser Komponente können Benutzende die E-Mail als Web-Seite anzeigen.</td>
  </tr>
  <tr>
   <td>Datenschutzrichtlinie</td>
   <td>Mit dieser Komponente wird ein Link zu Ihren Datenschutzrichtlinien in die E-Mail eingefügt.<br /> </td>
  </tr>
  <tr>
   <td>Abmeldungszentrum</td>
   <td>Mit dieser Komponenten wird es Benutzenden ermöglicht, sich von Ihrer Mailing-Liste abzumelden.</td>
  </tr>
  <tr>
   <td>Abonnementzentrum</td>
   <td>Ein Abonnementzentrum ist eine Web-Seite, auf der ein Abonnent festlegen kann, welche Mitteilungen er von Ihrem Unternehmen erhalten möchte.</td>
  </tr>
  <tr>
   <td>Öffnen der E-Mail verfolgen</td>
   <td>Hierbei handelt es sich um eine verborgene Komponente, mit der Sie die ExactTarget-Tracking-Funktion verwenden können.<br /> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Das Dropdown-Menü **Optionen** enthält nur dann Einträge, wenn eine ExactTarget-Konfiguration auf die E-Mail angewendet wurde. Weitere Informationen finden Sie unter [Anwenden von E-Mail-Dienstkonfigurationen auf E-Mail-Einstellungen](#applying-e-mail-service-configuration-to-e-mail-settings).

1. Veröffentlichen Sie die E-Mail in ExactTarget.

   Die E-Mail mit den E-Mail-Tools ist im konfigurierten ExactTarget-Konto verfügbar.

>[!NOTE]
>
>* Die URLs innerhalb der E-Mail-Tools werden (in der empfangenen E-Mail) nur dann durch die eigentlichen Werte ersetzt, wenn die E-Mail über **einfachen** oder **geführten Versand** versendet wird, nicht jedoch beim **Testversand**.
>
>* Zwei der E-Mail-Tools sind erforderlich: **Postanschrift (Erforderlich)** und **Profilzentrum (Erforderlich)**. Diese beiden E-Mail-Tools werden bei der Veröffentlichung der E-Mail in ExactTarget standardmäßig am Ende jeder E-Mail hinzugefügt.
>

### Hinzufügen des Tools für Text und Personalisierung zu Ihrer E-Mail {#adding-text-and-personalization-tool-to-your-e-mail}

Durch Hinzufügen der Komponente **Text und Personalisierung** zur Seite können Sie E-Mails um benutzerdefinierte Felder erweitern:

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
1. Klicken Sie auf der Registerkarte **Cloud-Services** auf **Service hinzufügen**. Die Liste der Dienste wird angezeigt. Wählen Sie die gewünschte Konfiguration (**ExactTarget** oder **Silverpop**) aus der Dropdown-Liste aus.

   ![chlimage_1-5](assets/chlimage_1-5a.jpeg)

1. Klicken Sie auf **OK**.

## Veröffentlichen von E-Mails im E-Mail-Dienst {#publishing-emails-to-email-service}

So veröffentlichen Sie E-Mails/Newsletter in Ihrem E-Mail-Dienst:

1. Öffnen Sie die E-Mail.
1. Bevor Sie eine E-Mail veröffentlichen, vergewissern Sie sich, dass Sie die korrekte Konfiguration auf die E-Mail angewendet haben.
1. Klicken Sie auf **Veröffentlichen**. Das Fenster **Newsletter bei E-Mail-Dienstanbieter veröffentlichen** wird geöffnet.
1. Füllen Sie das Feld **Newsletter-Name** aus. Die E-Mail/der Newsletter wird unter diesem Namen im E-Mail-Dienst veröffentlicht. Wenn kein E-Mail-Name angegeben wurde, wird die E-Mail unter dem Seitennamen des Newsletters in AEM veröffentlicht.
1. Klicken Sie auf **Veröffentlichen**.

   ![chlimage_1-6](assets/chlimage_1-6.jpeg)

   Wenn der Vorgang erfolgreich war, erhalten Sie in AEM eine Meldung, dass Sie die E-Mail in ExactTarget oder Silverpop Engage anzeigen können.

   Bei ExactTarget kann die veröffentlichte E-Mail durch einen Klick auf **Veröffentlichte E-Mail anzeigen** angezeigt werden. Sie werden direkt zum veröffentlichten Newsletter in ExactTarget weitergeleitet ([https://members.exacttarget.com/](https://members.exacttarget.com/)).

>[!NOTE]
>
>Wenn eine E-Mail/ein Newsletter unter einem Namen veröffentlicht wird, unter dem bereits eine andere E-Mail/ein anderer Newsletter vorhanden ist, wird die ältere E-Mail/der ältere Newsletter nicht ersetzt. Stattdessen wird eine neue E-Mail/ein neuer Newsletter mit demselben Namen erstellt (die IDs der beiden E-Mails/Newsletter unterscheiden sich jedoch).
>
>Wenn Sie die E-Mail/den Newsletter beim E-Mail-Dienstanbieter veröffentlichen, wird die E-Mail/der Newsletter auch in der AEM-Veröffentlichungsinstanz veröffentlicht.
>

### Aktualisieren von veröffentlichten E-Mails {#updating-a-published-e-mail}

Mit der Schaltfläche **Aktualisieren** im Dialogfeld „Veröffentlichen“ können Sie einen bereits beim E-Mail-Dienstanbieter veröffentlichten Newsletter aktualisieren. Falls der Newsletter noch nicht veröffentlicht wurde und Sie auf die Schaltfläche **Aktualisieren** klicken, wird die Meldung **Newsletter wurde nicht veröffentlicht** angezeigt.

So aktualisieren Sie eine veröffentlichte E-Mail:

1. Öffnen Sie die E-Mail/den Newsletter, die oder der bereits in einem E-Mail-Dienstanbieter veröffentlicht wurde und die oder der nach vorgenommenen Änderungen erneut veröffentlicht werden soll.
1. Klicken Sie auf **Veröffentlichen**. Das Fenster **Newsletter bei E-Mail-Dienstanbieter veröffentlichen** wird geöffnet. Klicken Sie auf **Aktualisieren**.

   Prüfen Sie, ob die E-Mail/der Newsletter in ExactTarget aktualisiert wurde, indem Sie auf die Schaltfläche **Veröffentlichte E-Mail anzeigen** klicken. Sie werden zur veröffentlichten E-Mail in ExactTarget weitergeleitet.

   Möchten Sie prüfen, ob die E-Mail/der Newsletter im Silverpop-E-Mail-Dienst aktualisiert wurde, rufen Sie die Silverpop Engage-Site auf.
