---
title: Freigegebene Warteschlangen konfigurieren
seo-title: Freigegebene Warteschlangen konfigurieren
description: Erfahren Sie, wie Sie freigegebene Warteschlangen für Forms-zentrierte Workflows in AEM Forms auf OSGi verwenden.
seo-description: Erfahren Sie, wie Sie freigegebene Warteschlangen für Forms-zentrierte Workflows in AEM Forms auf OSGi verwenden.
topic-tags: process
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
exl-id: 72cd0594-8b5e-4d14-bc6f-bca26bae50f2
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 1%

---

# Freigeben und Anfordern des Zugriffs auf Inbox-Elemente eines Benutzers {#share-and-request-access}

Eine Warteschlange ist eine Liste von Elementen im AEM Posteingang eines Benutzers. Dabei kann es sich um Elemente handeln, die einem Benutzer zugewiesen sind, oder um Elemente, die für die Gruppe freigegeben sind, der ein Benutzer angehört. Sie können auf Ihren Posteingang zugreifen, um das Element &quot;Posteingang&quot;anzuzeigen und zu bearbeiten. Geben Sie beispielsweise ein Element für einen anderen Benutzer frei.

Sie können Ihre Posteingangselemente auch für andere Benutzer freigeben. Sobald ein anderer Benutzer Zugriff auf Ihre Posteingangselemente hat, kann der Benutzer die entsprechenden Aktionen für freigegebene Elemente anfordern. Ebenso können Sie von anderen Benutzern Zugriff auf Posteingangselemente anfordern.

## Voraussetzungen {#pre-requisites}

Der angemeldete Benutzer muss Mitglied der Gruppe `workflow-users` sein. Der Benutzer kann Elemente freigeben oder den Zugriff auf Elemente nur von den Benutzern anfordern, für die der angemeldete Benutzer über Leserechte verfügt, oder nur von den Benutzern, die das öffentliche Profil aktiviert haben.

## Einzelne oder alle Elemente Ihres Posteingangs für einen anderen Benutzer freigeben

Mit AEM Posteingang können Sie einzelne oder alle Elemente in Ihrem Posteingang für einen anderen Benutzer freigeben.

### Alle Posteingangselemente freigeben

Führen Sie die folgenden Schritte aus, um alle Elemente in einem Posteingang für einen anderen Benutzer freizugeben:

1. Melden Sie sich bei Ihrer AEM-Instanz an. Tippen Sie auf das Symbol ![Inbox](assets/bell.svg) und dann auf **[!UICONTROL Alle anzeigen]**. Eine Liste Ihrer Posteingangselemente wird angezeigt.
1. Tippen Sie auf das Symbol ![View Selector](assets/viewlist.svg) oder ![View Selector](assets/calendar.svg) neben der Schaltfläche **[!UICONTROL Create]** und tippen Sie auf **[!UICONTROL Settings]**. Das Dialogfeld &quot;Einstellungen&quot;wird angezeigt.
1. Öffnen Sie die Registerkarte **[!UICONTROL Share]** im Einstellungsdialogfeld.
1. Geben Sie den Namen eines Benutzers in das Textfeld **[!UICONTROL Gewähren des Zugriffs auf Ihre Posteingangselemente]** ein und tippen Sie auf **[!UICONTROL Grant]**. Wiederholen Sie diesen Schritt, um weitere Benutzer hinzuzufügen. Alle Benutzer mit Zugriff auf Ihre Elemente werden im Abschnitt **Benutzername** angezeigt.
1. Tippen Sie auf **[!UICONTROL Speichern]**.

>[!NOTE]
>
>(Nur für Forms-zentrierte Workflow-Elemente) Aktivieren Sie die Option **[Bevollmächtigten erlauben, über die Inbox-Freigabe freizugeben](aem-forms-workflow-step-reference.md)** des Schritts **Aufgabe zuweisen** im Workflow. Für andere Benutzer werden nur Elemente angezeigt, für die die oben genannte Option aktiviert ist.

### Einzelne Elemente freigeben

Führen Sie die folgenden Schritte aus, um ein Posteingangselement für einen anderen Benutzer freizugeben:

1. Melden Sie sich bei Ihrer AEM-Instanz an. Tippen Sie auf das Symbol ![Inbox](assets/bell.svg) und dann auf **[!UICONTROL Alle anzeigen]**. Eine Liste Ihrer Posteingangselemente wird angezeigt.
1. Wählen Sie ein Element aus und tippen Sie auf **[!UICONTROL Share]**. Das folgende Dialogfeld wird angezeigt.
1. Geben Sie den Namen eines Benutzers in das Textfeld Benutzer hinzufügen, um dieses Element freizugeben ein und tippen Sie auf **[!UICONTROL Hinzufügen]**. Wiederholen Sie diesen Schritt, um weitere Benutzer hinzuzufügen. Alle Benutzer mit Zugriff auf Ihre Elemente werden im Abschnitt **[!UICONTROL Benutzername]** angezeigt.
1. Tippen Sie auf **[!UICONTROL Speichern]**.


>[!NOTE]
>
>(Nur für Forms-zentrierte Workflow-Elemente) Aktivieren Sie die Option **[Bevollmächtigten erlauben, explizit im Posteingang](aem-forms-workflow-step-reference.md)** des Schritts **Aufgabe zuweisen** im Workflow freizugeben. Für andere Benutzer werden nur Elemente angezeigt, für die die oben genannte Option aktiviert ist.

## Zugriff auf Elemente im Posteingang anfordern {#request-access}

Sie können den Zugriff auf die Elemente des Posteingangs eines anderen Benutzers anfordern. Sobald der Zugriff gewährt wurde, können Sie geeignete Aktionen für freigegebene Elemente anzeigen, anfordern und durchführen. Führen Sie die folgenden Schritte aus, um den Zugriff auf Inbox-Elemente eines anderen Benutzers anzufordern:

1. Melden Sie sich bei Ihrer AEM-Instanz an. Tippen Sie auf das Symbol ![Selektor anzeigen](assets/bell.svg) und dann auf **[!UICONTROL Alle anzeigen]**.
1. Tippen Sie auf das Symbol ![View Selector](assets/viewlist.svg) oder ![View Selector](assets/calendar.svg) neben der Schaltfläche **[!UICONTROL Create]** und tippen Sie auf **[!UICONTROL Settings]**. Das Dialogfeld &quot;Einstellungen&quot;wird angezeigt.
1. Geben Sie den Namen eines Benutzers in das Textfeld **[!UICONTROL Anfordern des Zugriffs auf die Posteingangselemente des Benutzers]** ein und tippen Sie auf **[!UICONTROL Anfordern]**. Eine Anfrage wird an den Benutzer gesendet und der Status der Anfrage wird mit dem Namen des Benutzers angezeigt. Wiederholen Sie diesen Schritt, um weitere Benutzer hinzuzufügen.
1. Tippen Sie auf **[!UICONTROL Speichern]**. Die Anfrage wird als Posteingangselement an die Benutzer gesendet. Der Benutzer kann das Element auswählen und auf Genehmigen oder Ablehnen tippen, um den Zugriff zu gewähren oder abzulehnen.


## Anfordern von Elementen, die von anderen Benutzern gemeinsam verwendet werden {#claim-items}

Sie können mit der Arbeit an einem freigegebenen Element erst beginnen, nachdem Sie es angefordert haben. Dadurch wird verhindert, dass mehrere Benutzer an einem einzelnen Element arbeiten. Führen Sie die folgenden Schritte aus, um ein Element anzufordern:

1. Melden Sie sich bei Ihrer AEM-Instanz an. Tippen Sie auf das Symbol Posteingang ![Posteingang](assets/bell.svg) und dann auf **[!UICONTROL Alle anzeigen]**.
1. Tippen Sie auf das Symbol ![Nur Inhalt](assets/railleft.svg) , um die Filterauswahl zu öffnen.
1. Tippen Sie auf das Dropdown-Menü **[!UICONTROL Wählen Sie Zuweisung]** aus, um Benutzer anzuzeigen und auszuwählen, die ihre Inbox-Elemente für Sie freigegeben haben.
1. Wählen Sie ein Element aus und tippen Sie auf **[!UICONTROL Claim]**. Das Element wird Ihrem Posteingang hinzugefügt.

## Veröffentlichte beanspruchte Elemente {#release-items}

Sie können an einem freigegebenen Element erst arbeiten, nachdem Sie es angefordert haben. Andere Benutzer können keine Artikel sehen oder bearbeiten, die Sie angefordert haben. Wenn Sie die Arbeit an einem Element nicht fortsetzen können, können Sie es wieder in den Pool übernehmen.   Nachdem Sie das Element freigegeben haben, können andere das Element anfordern und bearbeiten:

Führen Sie die folgenden Schritte aus, um ein Element freizugeben:

1. Melden Sie sich bei Ihrer AEM-Instanz an. Tippen Sie auf das Symbol Posteingang ![Posteingang](assets/bell.svg) und dann auf **[!UICONTROL Alle anzeigen]**. Eine Liste Ihrer Posteingangselemente wird angezeigt.
1. Wählen Sie das zu veröffentlichende Element aus und tippen Sie auf **[!UICONTROL UnClaim]**. Das Element wird wieder zum Pool hinzugefügt. Andere können den Artikel jetzt anfordern.

## Beschränkungen {#limitations}

* Die Freigabe von Elementen für eine Gruppe wird nicht unterstützt.
* Die Freigabe von Projektaufgaben wird nicht unterstützt.
