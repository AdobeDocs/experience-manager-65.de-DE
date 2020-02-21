---
title: Abwesenheitseinstellungen konfigurieren
seo-title: Abwesenheitseinstellungen konfigurieren
description: Abwesenheitseinstellungen konfigurieren
seo-description: Abwesenheitseinstellungen konfigurieren
translation-type: tm+mt
source-git-commit: 7ed5c2d0121029811d8ddeca3b1121912bc761f4

---



# Abwesenheitseinstellung konfigurieren {#configure-out-of-office-settings}

Wenn Sie planen, abwesend zu sein, können Sie angeben, was mit Artikeln geschieht, die Ihnen für diesen Zeitraum zugewiesen wurden.

Sie haben die Möglichkeit, ein Anfangs- und Enddatum sowie eine Anfangs- und Enduhrzeit für die Gültigkeit der Abwesenheitseinstellungen anzugeben. Wenn Sie sich in einer anderen Zeitzone als der Server befinden, wird die Zeitzone des Clients verwendet.

Sie können eine Standardperson festlegen, an die alle Elemente gesendet werden. Sie können auch Ausnahmen für Elemente bestimmter Prozesse festlegen, die an einen anderen Benutzer gesendet werden oder bis zur Rückkehr in Ihrem Posteingang bleiben sollen. Ist die angegebene Person auch nicht im Büro, wird der Artikel an den von ihnen benannten Benutzer weitergeleitet. Wenn das Element nicht einem Benutzer zugewiesen werden kann, der nicht abwesend ist, bleibt das Element in Ihrem Posteingang.

Sie können die Elementübertragung auf Grundlage der Workflow-Modelle trennen. Sie können beispielsweise ein Element im Zusammenhang mit Workflow A Benutzer A zuweisen und ein Element im Zusammenhang mit Workflow B Benutzer B zuweisen.


>[!NOTE]
>
> * Wenn Sie die Abwesenheitseinstellung aktivieren, bleiben alle Elemente, die in Ihrem Posteingang verfügbar sind, bevor Sie die Einstellung aktivieren, im Posteingang. Nur Artikel, die nach Aktivierung der Einstellung empfangen wurden, werden delegiert.
> * Wenn Sie die Abwesenheitseinstellung deaktivieren, werden die übertragenen Elemente nicht automatisch wieder zugewiesen. Mithilfe der Anforderungsfunktion können Sie Elemente zuweisen.
> * Wenn Benutzer A Elemente an Benutzer B und Benutzer B weiter an Benutzer C delegiert, werden Elemente nur Benutzer C und nicht Benutzer B zugewiesen.
> * Wenn eine Schleife in der Zuweisung vorhanden ist, bleiben die Aufgaben beim ursprünglichen Benutzer. Wenn Benutzer A beispielsweise Elemente an Benutzer B Benutzer B delegiert, an Benutzer C, Benutzer C an Benutzer D delegiert und Benutzer D an Benutzer B delegiert, wird eine Schleife erstellt. In einem solchen Fall verbleibt der Artikel beim ursprünglichen Benutzer. Benutzer A ist der ursprüngliche Benutzer im obigen Beispiel.


## Abwesenheitseinstellung für Ihr Konto aktivieren {#enable-out-of-office}

Führen Sie die folgenden Schritte aus, um die Abwesenheitseinstellung für Ihr Konto zu aktivieren und Ihre Posteingangselemente an einen anderen Benutzer zu delegieren:

1. Melden Sie sich bei Ihrer AEM-Instanz an. Tippen Sie auf das Symbol &quot; ![Posteingang](assets/bell.svg) &quot;und dann auf &quot;Alle **[!UICONTROL anzeigen&quot;]**. Eine Liste Ihrer Posteingangselemente wird angezeigt.
1. Tippen Sie auf das Symbol ![Ansichtsauswahl](assets/viewlist.svg) oder ![Ansichtsauswahl](assets/calendar.svg) neben der Schaltfläche **[!UICONTROL Erstellen]** und dann auf **[!UICONTROL Einstellungen]**. Das Dialogfeld &quot;Einstellungen&quot;wird angezeigt.
1. Öffnen Sie im Dialogfeld &quot;Einstellungen&quot;die Registerkarte &quot; **[!UICONTROL Abwesenheit]** &quot;.
1. Tippen Sie auf die Schaltfläche **[!UICONTROL Aktivieren/Deaktivieren]** , um die Abwesenheitseinstellung zu aktivieren.
1. Geben Sie die **[!UICONTROL Startzeit]** und die **[!UICONTROL Endzeit]** für die Einstellung an. Die Elemente werden nur während des angegebenen Zeitraums delegiert. Lassen Sie das Feld **[!UICONTROL Endzeit]** leer, um Elemente auf unbestimmte Zeit zu delegieren.
1. Aktivieren Sie das Kontrollkästchen **[!UICONTROL Meine Elemente während dieses Zeitraums]** weiterleiten. Wenn Sie die Option nicht auswählen und keinen Verantwortlichen angeben, werden Ihre Elemente nicht an einen Benutzer weitergeleitet. Obwohl Sie weg sind und die Einstellung aktiviert ist, bleiben die Elemente in Ihrem Posteingang.
1. Tippen Sie auf Verantwortlichen **[!UICONTROL hinzufügen]**. Geben Sie im Feld &quot; **[!UICONTROL Bevollmächtigter]** &quot;einen Benutzer an, an den die Elemente delegiert werden sollen. Geben Sie das **[!UICONTROL Workflow-Modell]** an, das an den angegebenen Benutzer delegiert werden soll. Sie können mehrere Workflow-Modelle auswählen.

   Um einem bestimmten Benutzer alle Elemente unabhängig vom Workflow-Modell zuzuweisen, wählen Sie in der Dropdownliste Workflow-Modell die Option **[!UICONTROL Alle Workflows]** aus. <br>

   Um einem bestimmten Benutzer Elemente für alle Workflow-Modelle außer einigen zuzuweisen, wählen Sie in der Dropdownliste Workflow-Modell die Option **[!UICONTROL Alle Workflows]** , klicken Sie auf **[!UICONTROL + Ausnahmen]**hinzufügen und geben Sie die Workflow-Modelle an, die ausgeschlossen werden sollen.
   <br>

   Wiederholen Sie den Schritt, um weitere Zuweisungsdaten hinzuzufügen. <br>

   >[!NOTE]
   >Die Reihenfolge der Bevollmächtigten ist wichtig. Wenn ein Element einem Benutzer zugewiesen wird, der die Abwesenheitseinstellung aktiviert hat, wird das Element anhand der Liste der angegebenen Verantwortlichen ausgewertet, in der die zugewiesenen Bevollmächtigten hinzugefügt werden. Entspricht ein Element den Kriterien, wird es dem Verantwortlichen zugewiesen und der nächste Verantwortliche wird nicht überprüft.

1. Tippen Sie auf **[!UICONTROL Speichern]**. Die Einstellung wird am angegebenen Startdatum und zur angegebenen Startzeit wirksam. Selbst wenn Sie sich während Ihrer Abwesenheit am System anmelden, gelten Sie erst wieder als anwesend, wenn Sie die Einstellungen ändern.

Jetzt werden Ihnen während des Abwesenheitszeitraums zugewiesene Artikel automatisch dem angegebenen Verantwortlichen zugewiesen.\
![Abwesenheit](assets/out-of-office.png)

>[!NOTE]
>(Nur für formularorientierte Workflow-Elemente) Aktivieren Sie die Option **Delegieren durch den Verantwortlichen über die Abwesenheitseinstellungen** im Schritt Aufgabe **** zuweisen im Workflow zulassen. Nur Artikel, für die die oben genannte Option aktiviert ist, werden an andere Benutzer übertragen.

## Beschränkungen {#limitations}

* Das Zuweisen von Elementen zu einer Gruppe wird nicht unterstützt.
* Die Aktivierung von Abwesenheitszeiten für Projektaufgaben wird derzeit nicht unterstützt.
