---
title: Freigegebene Warteschlangen konfigurieren
seo-title: Freigegebene Warteschlangen konfigurieren
description: Erfahren Sie, wie Sie freigegebene Warteschlangen für formularorientierte Workflows auf AEM Forms on OSGi verwenden.
seo-description: Erfahren Sie, wie Sie freigegebene Warteschlangen für formularorientierte Workflows auf AEM Forms on OSGi verwenden.
uuid: null
topic-tags: process
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: null
docset: aem65
translation-type: tm+mt
source-git-commit: 9a250e739adcf094856f1eafa75de2649d6d3d5f

---


# Freigeben und Anfordern des Zugriffs auf Posteingangselemente eines Benutzers {#share-and-request-access}

Eine Warteschlange ist eine Liste von Elementen im AEM-Posteingang eines Benutzers. Dabei kann es sich um Elemente handeln, die einem Benutzer zugewiesen sind, oder um Elemente, die für die Gruppe freigegeben sind, der ein Benutzer angehört. Sie können auf Ihren Posteingang zugreifen, um das Posteingangselement anzuzeigen und Maßnahmen zu ergreifen. Geben Sie beispielsweise ein Element für einen anderen Benutzer frei.

Sie können Ihre Posteingangselemente auch für andere Benutzer freigeben. Sobald ein anderer Benutzer Zugriff auf Ihre Posteingangselemente hat, kann der Benutzer für freigegebene Elemente entsprechende Aktionen anfordern. Ebenso können Sie von anderen Benutzern den Zugriff auf Posteingangselemente anfordern.

## Voraussetzungen {#pre-requisites}

Der angemeldete Benutzer muss Mitglied der `workflow-users` Gruppe sein. Der Benutzer kann Elemente freigeben oder den Zugriff auf Elemente nur von den Benutzern anfordern, denen der angemeldete Benutzer Leserechte erteilt hat, oder nur von den Benutzern, die das öffentliche Profil aktiviert haben.

## Teilen eines einzelnen oder aller Elemente Ihres Posteingangs mit einem anderen Benutzer

Mit AEM Inbox können Sie einzelne oder alle Elemente in Ihrem Posteingang für einen anderen Benutzer freigeben.

### Alle Posteingangselemente freigeben

Führen Sie die folgenden Schritte aus, um alle Elemente in einem Posteingang für einen anderen Benutzer freizugeben:

1. Melden Sie sich bei Ihrer AEM-Instanz an. Tippen Sie auf das Symbol &quot; ![Posteingang](assets/bell.svg) &quot;und dann auf &quot;Alle **[!UICONTROL anzeigen&quot;]**. Eine Liste Ihrer Posteingangselemente wird angezeigt.
1. Tippen Sie auf das Symbol ![Ansichtsauswahl](assets/viewlist.svg) oder ![Ansichtsauswahl](assets/calendar.svg) neben der Schaltfläche **[!UICONTROL Erstellen]** und dann auf **[!UICONTROL Einstellungen]**. Das Dialogfeld &quot;Einstellungen&quot;wird angezeigt.
1. Öffnen Sie im Dialogfeld &quot;Einstellungen&quot;die Registerkarte &quot; **[!UICONTROL Freigeben]** &quot;.
1. Geben Sie den Namen eines Benutzers in das Textfeld Zugriff auf **[!UICONTROL Posteingangselemente]** gewähren ein und tippen Sie auf **[!UICONTROL Förderung]**. Wiederholen Sie den Schritt, um weitere Benutzer hinzuzufügen. Alle Benutzer, die Zugriff auf Ihre Elemente haben, werden im Abschnitt **Benutzername** angezeigt.
1. Tippen Sie auf **[!UICONTROL Speichern]**.

>[!NOTE]
>
> (Nur für formularzentrierte Workflow-Elemente) Aktivieren Sie die Option **[Zulassen der Freigabe](aem-forms-workflow-step-reference.md)**per Posteingang im Schritt Aufgabe ****zuweisen im Workflow. Für andere Benutzer werden nur Elemente angezeigt, für die die oben genannte Option aktiviert ist.

### Freigeben einzelner Elemente

Führen Sie die folgenden Schritte aus, um ein Posteingangselement für einen anderen Benutzer freizugeben:

1. Melden Sie sich bei Ihrer AEM-Instanz an. Tippen Sie auf das Symbol &quot; ![Posteingang](assets/bell.svg) &quot;und dann auf &quot;Alle **[!UICONTROL anzeigen&quot;]**. Eine Liste Ihrer Posteingangselemente wird angezeigt.
1. Wählen Sie ein Element aus und tippen Sie auf **[!UICONTROL Freigeben]**. Das folgende Dialogfeld wird angezeigt.
1. Geben Sie den Namen eines Benutzers in das Textfeld Benutzer hinzufügen ein, um dieses Element freizugeben, und tippen Sie auf **[!UICONTROL Hinzufügen]**. Wiederholen Sie den Schritt, um weitere Benutzer hinzuzufügen. Alle Benutzer, die Zugriff auf Ihre Elemente haben, werden im Abschnitt **[!UICONTROL Benutzername]** angezeigt.
1. Tippen Sie auf **[!UICONTROL Speichern]**.


>[!NOTE]
>
> (Nur für formularzentrierte Workflow-Elemente) Aktivieren Sie die Option &quot; **[Weisen Sie dem Verantwortlichen die explizite Freigabe in der Posteingangsoption](aem-forms-workflow-step-reference.md)**des Schritts **Zuweisen von Aufgaben**im Workflow zu.) Für andere Benutzer werden nur Elemente angezeigt, für die die oben genannte Option aktiviert ist.

## Zugriff auf Elemente im Posteingang anfordern {#request-access}

Sie können den Zugriff auf die Inbox-Elemente eines anderen Benutzers anfordern. Sobald der Zugriff gewährt wurde, können Sie für freigegebene Elemente entsprechende Aktionen anzeigen, anfordern und durchführen. Führen Sie die folgenden Schritte aus, um den Zugriff auf Posteingangselemente eines anderen Benutzers anzufordern:

1. Melden Sie sich bei Ihrer AEM-Instanz an. Tippen Sie auf das Symbol ![Ansichtsauswahl](assets/bell.svg) und dann auf Alle **[!UICONTROL anzeigen]**.
1. Tippen Sie auf das Symbol ![Ansichtsauswahl](assets/viewlist.svg) oder ![Ansichtsauswahl](assets/calendar.svg) neben der Schaltfläche **[!UICONTROL Erstellen]** und dann auf **[!UICONTROL Einstellungen]**. Das Dialogfeld &quot;Einstellungen&quot;wird angezeigt.
1. Geben Sie den Namen eines Benutzers in das Textfeld &quot;Zugriff **[!UICONTROL auf Posteingangselemente anfordern]** &quot;ein und klicken Sie auf &quot; **[!UICONTROL Anforderung]**&quot;. Eine Anforderung wird an den Benutzer gesendet und der Status der Anforderung wird mit dem Namen des Benutzers angezeigt. Wiederholen Sie den Schritt, um weitere Benutzer hinzuzufügen.
1. Tippen Sie auf **[!UICONTROL Speichern]**. Die Anforderung wird als Posteingangselement an die Benutzer gesendet. Der Benutzer kann das Element auswählen und auf Genehmigen oder Ablehnen tippen, um den Zugriff zu gewähren oder abzulehnen.


## Von anderen Benutzern freigegebene Elemente anfordern {#claim-items}

Sie können mit der Arbeit an einem freigegebenen Element erst beginnen, nachdem Sie es angefordert haben. Dadurch wird verhindert, dass mehrere Benutzer an einem einzelnen Element arbeiten. Führen Sie die folgenden Schritte aus, um ein Element anzufordern:

1. Melden Sie sich bei Ihrer AEM-Instanz an. Tippen Sie auf das Symbol &quot; ![Posteingang](assets/bell.svg) &quot;und dann auf &quot;Alle **[!UICONTROL anzeigen&quot;]**.
1. Tippen Sie auf das Symbol Nur![ ](assets/railleft.svg)Inhalt, um die Filterauswahl zu öffnen.
1. Tippen Sie auf die Dropdownliste &quot; **[!UICONTROLSAusgewählter Empfänger]** &quot;, um Benutzer anzuzeigen und auszuwählen, die ihre Posteingangselemente für Sie freigegeben haben.
1. Wählen Sie ein Element aus und tippen Sie auf **[!UICONTROL Anfordern]**. Das Element wird Ihrem Posteingang hinzugefügt.

## Beantragte Elemente freigeben {#release-items}

Sie können ein freigegebenes Element erst bearbeiten, nachdem Sie es angefordert haben. Andere Benutzer können keine Artikel sehen oder bearbeiten, die Sie angefordert haben. Wenn Sie mit der Arbeit an einem Element nicht fortfahren können, können Sie es wieder in den Pool verschieben.   Nachdem Sie das Element freigegeben haben, können andere das Element anfordern und bearbeiten:

Führen Sie die folgenden Schritte aus, um ein Element freizugeben:

1. Melden Sie sich bei Ihrer AEM-Instanz an. Tippen Sie auf das Symbol &quot; ![Posteingang](assets/bell.svg) &quot;und dann auf &quot;Alle **[!UICONTROL anzeigen&quot;]**. Eine Liste Ihrer Posteingangselemente wird angezeigt.
1. Wählen Sie das zu veröffentlichende Element aus und tippen Sie auf **[!UICONTROL NichtAnforderung]**. Das Element wird wieder zum Pool hinzugefügt. Andere können den Artikel jetzt anfordern.

## Beschränkungen {#limitations}

* Die Freigabe von Elementen für eine Gruppe wird nicht unterstützt.
* Das Freigeben von Projektaufgaben wird nicht unterstützt.
