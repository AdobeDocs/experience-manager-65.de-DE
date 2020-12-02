---
title: Freigegebene Warteschlangen konfigurieren
seo-title: Freigegebene Warteschlangen konfigurieren
description: Erfahren Sie, wie Sie freigegebene Warteschlangen für Forms-zentrierte Workflows auf AEM Forms unter OSGi verwenden.
seo-description: Erfahren Sie, wie Sie freigegebene Warteschlangen für Forms-zentrierte Workflows auf AEM Forms unter OSGi verwenden.
topic-tags: process
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
translation-type: tm+mt
source-git-commit: a873cf3e7efd3bc9cd4744bf09078d9040efcdda
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 1%

---


# Freigeben und Anfordern des Zugriffs auf Posteingangselemente eines Benutzers {#share-and-request-access}

Eine Warteschlange ist eine Liste von Elementen in AEM Posteingang eines Benutzers. Dabei kann es sich um Elemente handeln, die einem Benutzer zugewiesen sind, oder um Elemente, die für die Gruppe freigegeben sind, der ein Benutzer angehört. Sie können auf Ihren Posteingang zugreifen, um Ansichten auszuführen und Maßnahmen für das Posteingangselement zu ergreifen. Geben Sie beispielsweise ein Element für einen anderen Benutzer frei.

Sie können Ihre Posteingangselemente auch für andere Benutzer freigeben. Sobald ein anderer Benutzer Zugriff auf Ihre Posteingangselemente hat, kann der Benutzer für freigegebene Elemente entsprechende Aktionen anfordern. Ebenso können Sie von anderen Benutzern den Zugriff auf Posteingangselemente anfordern.

## Voraussetzungen {#pre-requisites}

Der angemeldete Benutzer muss Mitglied der Gruppe `workflow-users` sein. Der Benutzer kann Elemente freigeben oder den Zugriff auf Elemente nur von Benutzern anfordern, für die der angemeldete Benutzer über Leserechte verfügt, oder nur von Benutzern, die öffentliches Profil aktiviert haben.

## Teilen eines einzelnen oder aller Elemente Ihres Posteingangs mit einem anderen Benutzer

Mit AEM Posteingang können Sie einzelne oder alle Elemente in Ihrem Posteingang für einen anderen Benutzer freigeben.

### Alle Posteingangselemente freigeben

Führen Sie die folgenden Schritte aus, um alle Elemente in einem Posteingang für einen anderen Benutzer freizugeben:

1. Melden Sie sich bei Ihrer AEM an. Tippen Sie auf das Symbol ![Inbox](assets/bell.svg) und dann auf **[!UICONTROL Ansicht All]**. Eine Liste Ihrer Posteingangselemente wird angezeigt.
1. Tippen Sie auf das Symbol ![Ansicht-Selektor](assets/viewlist.svg) oder ![Ansicht-Selektor](assets/calendar.svg) neben der Schaltfläche **[!UICONTROL Erstellen]** und dann auf **[!UICONTROL Einstellungen]**. Das Dialogfeld &quot;Einstellungen&quot;wird angezeigt.
1. Öffnen Sie im Dialogfeld &quot;Einstellungen&quot;die Registerkarte **[!UICONTROL Freigeben]**.
1. Geben Sie den Namen eines Benutzers in das Textfeld **[!UICONTROL Zugriff auf Ihre Posteingangselemente]** gewähren ein und tippen Sie auf **[!UICONTROL Förderung]**. Wiederholen Sie den Schritt, um weitere Benutzer hinzuzufügen. Alle Benutzer mit Zugriff auf Ihre Elemente werden im Abschnitt **Benutzername** angezeigt.
1. Tippen Sie auf **[!UICONTROL Speichern]**.

>[!NOTE]
>
>(Nur für Forms-zentrierte Workflow-Elemente) Aktivieren Sie die Option **[Den Verantwortlichen die Freigabe per Inbox-Freigabe zulassen](aem-forms-workflow-step-reference.md)** im Schritt **Aufgabe zuweisen**. Für andere Benutzer werden nur Elemente angezeigt, für die die oben genannte Option aktiviert ist.

### Freigeben einzelner Elemente

Führen Sie die folgenden Schritte aus, um ein Posteingangselement für einen anderen Benutzer freizugeben:

1. Melden Sie sich bei Ihrer AEM an. Tippen Sie auf das Symbol ![Inbox](assets/bell.svg) und dann auf **[!UICONTROL Ansicht All]**. Eine Liste Ihrer Posteingangselemente wird angezeigt.
1. Wählen Sie ein Element aus und tippen Sie auf **[!UICONTROL Freigeben]**. Das folgende Dialogfeld wird angezeigt.
1. Geben Sie den Namen eines Benutzers in das Textfeld Hinzufügen Benutzer ein, um dieses Element freizugeben, und tippen Sie auf **[!UICONTROL Hinzufügen]**. Wiederholen Sie den Schritt, um weitere Benutzer hinzuzufügen. Alle Benutzer mit Zugriff auf Ihre Elemente werden im Abschnitt **[!UICONTROL Benutzername]** angezeigt.
1. Tippen Sie auf **[!UICONTROL Speichern]**.


>[!NOTE]
>
>(Nur für Forms-zentrierte Workflow-Elemente) Aktivieren Sie die Option **[Den Verantwortlichen die explizite Freigabe in Inbox](aem-forms-workflow-step-reference.md)** des Schritts **Aufgabe zuweisen**. Für andere Benutzer werden nur Elemente angezeigt, für die die oben genannte Option aktiviert ist.

## Zugriff auf Elemente im Posteingang anfordern {#request-access}

Sie können den Zugriff auf die Inbox-Elemente eines anderen Benutzers anfordern. Sobald der Zugriff gewährt wurde, können Sie für freigegebene Elemente entsprechende Ansichten anfordern und entsprechende Maßnahmen ergreifen. Führen Sie die folgenden Schritte aus, um den Zugriff auf Posteingangselemente eines anderen Benutzers anzufordern:

1. Melden Sie sich bei Ihrer AEM an. Tippen Sie auf das Symbol ![Ansicht-Auswahl](assets/bell.svg) und dann auf **[!UICONTROL Ansicht All]**.
1. Tippen Sie auf das Symbol ![Ansicht-Selektor](assets/viewlist.svg) oder ![Ansicht-Selektor](assets/calendar.svg) neben der Schaltfläche **[!UICONTROL Erstellen]** und dann auf **[!UICONTROL Einstellungen]**. Das Dialogfeld &quot;Einstellungen&quot;wird angezeigt.
1. Geben Sie den Namen eines Benutzers in das Textfeld **[!UICONTROL Zugriff auf Posteingangselemente des Benutzers anfordern]** ein und tippen Sie auf **[!UICONTROL Anforderung]**. Eine Anforderung wird an den Benutzer gesendet und der Status der Anforderung wird mit dem Namen des Benutzers angezeigt. Wiederholen Sie den Schritt, um weitere Benutzer hinzuzufügen.
1. Tippen Sie auf **[!UICONTROL Speichern]**. Die Anforderung wird als Posteingangselement an die Benutzer gesendet. Der Benutzer kann das Element auswählen und auf Genehmigen oder Ablehnen tippen, um den Zugriff zu gewähren oder abzulehnen.


## Anfordern von Elementen, die von anderen Benutzern gemeinsam genutzt werden{#claim-items}

Sie können Beginn, die an einem freigegebenen Element arbeiten, erst dann ausführen, wenn Sie es beanspruchen. Dadurch wird verhindert, dass mehrere Benutzer an einem einzelnen Element arbeiten. Führen Sie die folgenden Schritte aus, um ein Element anzufordern:

1. Melden Sie sich bei Ihrer AEM an. Tippen Sie auf das Symbol Inbox ![Inbox](assets/bell.svg) und dann auf **[!UICONTROL Ansicht All]**.
1. Tippen Sie auf das Symbol ![Nur Inhalt](assets/railleft.svg), um die Filterauswahl zu öffnen.
1. Tippen Sie auf die Dropdown-Liste **[!UICONTROL Einen Verantwortlichen auswählen]**, um Ansichten auszuwählen und Benutzer auszuwählen, die ihre Posteingangselemente für Sie freigegeben haben.
1. Wählen Sie ein Element aus und tippen Sie auf **[!UICONTROL Claim]**. Das Element wird Ihrem Posteingang hinzugefügt.

## Angeforderte Elemente {#release-items} freigeben

Sie können ein freigegebenes Element erst bearbeiten, nachdem Sie es angefordert haben. Andere Benutzer können keine Artikel sehen oder bearbeiten, die Sie angefordert haben. Wenn Sie mit der Arbeit an einem Element nicht fortfahren können, können Sie es wieder in den Pool verschieben.   Nachdem Sie das Element freigegeben haben, können andere das Element anfordern und bearbeiten:

Führen Sie die folgenden Schritte aus, um ein Element freizugeben:

1. Melden Sie sich bei Ihrer AEM an. Tippen Sie auf das Symbol Inbox ![Inbox](assets/bell.svg) und dann auf **[!UICONTROL Ansicht All]**. Eine Liste Ihrer Posteingangselemente wird angezeigt.
1. Wählen Sie das zu veröffentlichende Element aus und tippen Sie auf **[!UICONTROL UNClaim]**. Das Element wird wieder zum Pool hinzugefügt. Andere können den Artikel jetzt anfordern.

## Beschränkungen {#limitations}

* Die Freigabe von Elementen für eine Gruppe wird nicht unterstützt.
* Die Freigabe von Aufgaben wird nicht unterstützt.
