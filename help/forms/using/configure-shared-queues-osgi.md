---
title: Freigegebene Warteschlangen konfigurieren
description: Erfahren Sie, wie Sie freigegebene Warteschlangen für Forms-zentrierte Workflows für AEM Forms unter OSGi verwenden.
topic-tags: process
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
exl-id: 72cd0594-8b5e-4d14-bc6f-bca26bae50f2
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '840'
ht-degree: 100%

---

# Freigeben und Anfordern von Zugriff auf Elemente im Posteingang eines Benutzers {#share-and-request-access}

Eine Warteschlange ist eine Liste von Elementen im AEM-Posteingang eines Benutzers. Dabei kann es sich um Elemente handeln, die einem Benutzer zugewiesen sind, oder um Elemente, die für die Gruppe freigegeben sind, der ein Benutzer angehört. Sie können auf Ihren Posteingang zugreifen, um das Posteingangselement anzuzeigen und eine Aktion damit auszuführen. Geben Sie beispielsweise ein Element für einen anderen Benutzer frei.

Sie können Ihre Posteingangselemente auch für einen anderen Benutzer freigeben. Sobald ein anderer Benutzer Zugriff auf Ihre Posteingangselemente hat, kann er sie beanspruchen und entsprechende Aktionen durchführen. Ebenso können Sie von anderen Benutzern Zugriff auf Posteingangselemente anfordern.

## Voraussetzungen {#pre-requisites}

Der angemeldete Benutzer muss Mitglied der Gruppe `workflow-users` sein. Der Benutzer kann Elemente freigeben oder Zugriff auf Elemente nur von Benutzern anfordern, für die der angemeldete Benutzer über Leserechte verfügt, oder nur von Benutzern, die ein öffentliches Profil aktiviert haben.

## Teilen eines einzelnen oder aller Elemente Ihres Posteingangs mit einem anderen Benutzer

Beim AEM-Posteingang können Sie einzelne oder alle Elemente in Ihrem Posteingang für andere Benutzende freigeben.

### Alle Posteingangselemente freigeben

Führen Sie folgende Schritte aus, um alle Elemente in einem Posteingang für einen anderen Benutzer freizugeben:

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an. Wählen Sie das Symbol ![Posteingang](assets/bell.svg) und dann **[!UICONTROL Alle anzeigen]** aus. Eine Liste Ihrer Posteingangselemente wird angezeigt.
1. Wählen Sie den ![Ansichtselektor](assets/viewlist.svg) oder das Symbol ![Ansichtselektor](assets/calendar.svg) neben der Schaltfläche **[!UICONTROL Erstellen]** und dann **[!UICONTROL Einstellungen]** aus. Das Dialogfeld „Einstellungen“ wird angezeigt.
1. Öffnen Sie im Dialogfeld „Einstellungen“ die Registerkarte **[!UICONTROL Freigeben]**.
1. Geben Sie den Namen eines Benutzers oder einer Benutzerin in das Textfeld **[!UICONTROL Zugriff auf Ihre Posteingangselemente gewähren]** ein und wählen Sie **[!UICONTROL Gewähren]** aus. Wiederholen Sie den Schritt, um weitere Benutzer hinzuzufügen. Alle Benutzer mit Zugriff auf Ihre Elemente werden im Abschnitt **Benutzername** angezeigt.
1. Wählen Sie **[!UICONTROL Speichern]** aus.

>[!NOTE]
>
>(Nur für Forms-zentrierte Workflow-Elemente) Aktivieren Sie die Option **[Zulassen, dass Verantwortlicher per Freigabe des Posteingangs freigibt](aem-forms-workflow-step-reference.md)** im Schritt **Aufgabe zuweisen**. Für andere Benutzer werden nur Elemente angezeigt, für die die oben genannte Option aktiviert ist.

### Freigeben einzelner Elemente

Führen Sie folgende Schritte aus, um ein Posteingangselement für einen anderen Benutzer freizugeben:

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an. Wählen Sie das Symbol ![Posteingang](assets/bell.svg) und dann **[!UICONTROL Alle anzeigen]** aus. Eine Liste Ihrer Posteingangselemente wird angezeigt.
1. Wählen Sie ein Element aus und wählen Sie **[!UICONTROL Freigeben]** aus. Ein Dialogfeld wird angezeigt.
1. Geben Sie den Namen eines Benutzers oder einer Benutzerin in das Textfeld „Benutzer hinzufügen, um dieses Element freizugeben“ ein und tippen Sie auf **[!UICONTROL Hinzufügen]**. Wiederholen Sie den Schritt, um weitere Benutzer hinzuzufügen. Alle Benutzer mit Zugriff auf Ihre Elemente werden im Abschnitt **[!UICONTROL Benutzername]** angezeigt.
1. Wählen Sie **[!UICONTROL Speichern]** aus.


>[!NOTE]
>
>(Nur für Forms-zentrierte Workflow-Elemente) Aktivieren Sie die Option **[Zulassen, dass Verantwortlicher explizit im Posteingang freigibt](aem-forms-workflow-step-reference.md)** des Workflow-Schritts **Aufgabe zuweisen**. Für andere Benutzer werden nur Elemente angezeigt, für die die oben genannte Option aktiviert ist.

## Anfordern von Zugriff auf Elemente im Posteingang {#request-access}

Sie können Zugriff auf die Posteingangselemente eines anderen Benutzers anfordern. Sobald der Zugriff gewährt ist, können Sie freigegebene Elemente anzeigen, beanspruchen und entsprechende Aktionen durchführen. Führen Sie folgende Schritte aus, um den Zugriff auf Posteingangselemente eines anderen Benutzers anzufordern:

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an. Tippen Sie auf das Symbol ![Ansichtselektor](assets/bell.svg) und dann auf **[!UICONTROL Alle anzeigen]**.
1. Wählen Sie den ![Ansichtselektor](assets/viewlist.svg) oder das Symbol ![Ansichtselektor](assets/calendar.svg) neben der Schaltfläche **[!UICONTROL Erstellen]** und wählen Sie **[!UICONTROL Einstellungen]**. Das Dialogfeld „Einstellungen“ wird angezeigt.
1. Geben Sie den Namen eines Benutzers oder einer Benutzerin in das Textfeld **[!UICONTROL Zugriff auf Posteingangselemente des Benutzers anfordern]** ein und tippen Sie auf **[!UICONTROL Anfordern]**. Der Benutzer erhält eine Anfrage und der Status der Anfrage wird beim Namen des Benutzers angezeigt. Wiederholen Sie den Schritt, um weitere Benutzer hinzuzufügen.
1. Wählen Sie **[!UICONTROL Speichern]** aus. Die Anfrage wird als Posteingangselement an die Benutzenden gesendet. Die Person kann das Element auswählen und „Genehmigen“ oder „Ablehnen“ wählen, um den Zugriff zu gewähren oder abzulehnen.


## Anfordern von Elementen, die von anderen Benutzern freigegeben werden {#claim-items}

Sie können erst mit einem freigegebenen Element arbeiten, nachdem Sie es beansprucht haben. Dadurch wird verhindert, dass mehrere Benutzer an einem einzelnen Element arbeiten. Führen Sie folgende Schritte aus, um ein Element zu beanspruchen:

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an. Tippen Sie auf das Posteingangssymbol (![Posteingang](assets/bell.svg)) und dann auf **[!UICONTROL Alle anzeigen]**.
1. Tippen Sie auf das Symbol ![Nur Inhalt](assets/railleft.svg), um die Filterauswahl zu öffnen.
1. Tippen Sie auf die Dropdown-Liste **[!UICONTROL Bevollmächtigten auswählen]**, um Benutzende anzuzeigen und auszuwählen, die ihre Posteingangselemente für Sie freigegeben haben. 
1. Wählen Sie ein Element und klicken Sie auf **[!UICONTROL Anfordern]** Das Element wird Ihrem Posteingang hinzugefügt.

## Freigeben angeforderter Elemente {#release-items}

Sie können erst mit einem freigegebenen Element arbeiten, nachdem Sie es beansprucht haben. Andere Benutzer können Elemente, die Sie beansprucht haben, nicht sehen oder bearbeiten. Wenn Sie mit der Arbeit an einem Element nicht fortfahren können, können Sie es wieder in den Pool freigeben.   Nachdem Sie das Element freigegeben haben, können andere das Element beanspruchen und bearbeiten:

Führen Sie folgende Schritte aus, um ein Element freizugeben:

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an. Wählen Sie das Posteingangssymbol (![Posteingang](assets/bell.svg)) und wählen Sie **[!UICONTROL Alle anzeigen]**. Eine Liste Ihrer Posteingangselemente wird angezeigt.
1. Wählen Sie das zu veröffentlichende Element aus und tippen Sie auf **[!UICONTROL Beanspruchung aufheben]**. Das Element wird wieder zum Pool hinzugefügt. Andere können das Element jetzt beanspruchen.

## Einschränkungen {#limitations}

* Die Freigabe von Elementen für eine Gruppe wird nicht unterstützt.
* Die Freigabe von Projektaufgaben wird nicht unterstützt.
