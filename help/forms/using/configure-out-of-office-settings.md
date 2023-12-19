---
title: Konfigurieren von Abwesenheitseinstellungen
description: Erfahren Sie, wie Sie Abwesenheitseinstellungen für Ihre Adobe Experience Manager Forms-Instanz konfigurieren.
exl-id: e4c9d74c-e08d-4675-91f2-4f9fc2f1bcea
source-git-commit: bd86d647fdc203015bc70a0f57d5b94b4c634bf9
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 72%

---

# Konfigurieren von Abwesenheitseinstellungen {#configure-out-of-office-settings}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/configure-out-of-office-settings.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

Für geplante Abwesenheitszeiten können Sie festlegen, was während dieser Zeit mit den Ihnen zugeordneten Elementen passieren soll.

Sie haben die Möglichkeit, ein Anfangs- und Enddatum sowie eine Anfangs- und Enduhrzeit für die Gültigkeit der Abwesenheitseinstellungen anzugeben. Wenn Sie sich in einer anderen Zeitzone als der Server befinden, wird die Zeitzone des Clients verwendet.

Sie können eine Person festlegen, an die Ihre Elemente standardmäßig gesendet werden. Zudem können Sie Ausnahmen für Elemente aus speziellen Prozessen festlegen, die an einen anderen Benutzer gesendet oder bis zu Ihrer Rückkehr in Ihrem Posteingang bleiben sollen. Wenn die angegebene Person ebenfalls abwesend ist, wird das Element an den von dieser Person angegebenen Vertreter weitergeleitet. Sind alle Benutzer abwesend, denen das Element zugewiesen werden könnte, bleibt es im Posteingang.

Sie können die Elementzuweisung auf der Basis der Workflow-Modelle differenzieren. Sie können beispielsweise ein Element aus Workflow A an Benutzer A und ein Element aus Workflow B an Benutzer B übertragen.


>[!NOTE]
>
>* Wenn Sie die Einstellung &quot;Abwesenheit&quot;aktivieren, bleiben alle Elemente in Ihrem Posteingang, die vor der Aktivierung der Einstellung verfügbar sind, in Ihrem Posteingang. Nur Elemente, die nach Aktivierung der Abwesenheitseinstellungen empfangen wurden, werden delegiert.
>* Wenn Sie die Abwesenheitseinstellung deaktivieren, werden die delegierten Elemente nicht automatisch an Sie zurückverwiesen. Mithilfe der Anforderungsfunktion können Sie Elemente an sich selbst übertragen.
>* Wenn Benutzer A Elemente an Benutzer B delegiert und Benutzer B an Benutzer C weiterdelegiert, werden die Elemente nur Benutzer C und nicht Benutzer B zugewiesen.
>* Wenn eine Schleife in der Aufgabenzuweisung entsteht, bleiben die Aufgaben beim ursprünglichen Benutzer. Eine solche Schleife besteht beispielsweise, wenn ein Element von Benutzer A an Benutzer B, von Benutzer B an Benutzer C, von Benutzer C an Benutzer D und schließlich von Benutzer D an Benutzer B delegiert wird. In einem solchen Fall verbleibt das Element beim ursprünglichen Benutzer. Beim Beispiel oben ist Benutzer A der ursprüngliche Benutzer.

## Aktivieren der Abwesenheitseinstellung für Ihr Konto {#enable-out-of-office}

Führen Sie folgende Schritte aus, um die Abwesenheitseinstellung für Ihr Konto zu aktivieren und Ihre Posteingangselemente an einen anderen Benutzer zu delegieren:

1. Melden Sie sich bei Ihrer AEM-Instanz an. Wählen Sie die ![Posteingang](assets/bell.svg) Symbol und wählen Sie **[!UICONTROL Alle anzeigen]**. Eine Liste Ihrer Posteingangselemente wird angezeigt.
1. Wählen Sie die ![Ansichtauswahl](assets/viewlist.svg) oder ![Ansichtauswahl](assets/calendar.svg) Symbol neben **[!UICONTROL Erstellen]** Schaltfläche und wählen Sie **[!UICONTROL Einstellungen]**. Das Dialogfeld „Einstellungen“ wird angezeigt.
1. Öffnen Sie im Dialogfeld „Einstellungen“ die Registerkarte **[!UICONTROL Abwesenheit]**.
1. Wählen Sie die **[!UICONTROL Aktivieren/Deaktivieren]** -Schaltfläche, um die Abwesenheitseinstellung zu aktivieren.
1. Geben Sie die Zeiten für **[!UICONTROL Startzeit]** und **[!UICONTROL Endzeit]** an. Die Elemente werden nur während des angegebenen Zeitraums delegiert. Lassen Sie das Feld **[!UICONTROL Ende]** leer, um Elemente auf unbestimmte Zeit zu übertragen.
1. Aktivieren Sie das Kontrollkästchen **[!UICONTROL Meine Aufgaben während dieser Zeit weiterleiten]**. Wenn Sie die Option nicht auswählen und keine Bevollmächtigten angeben, werden Ihre Elemente nicht an andere Benutzende weitergeleitet. Obwohl Sie weg sind und die Einstellung aktiviert ist, bleiben die Elemente in Ihrem Posteingang.
1. Auswählen **[!UICONTROL Bevollmächtigten hinzufügen]**. Geben Sie einen Benutzer im **[!UICONTROL Bevollmächtigter]** -Feld, damit Sie die Elemente delegieren können. Geben Sie die **[!UICONTROL Workflow-Modell]** damit Sie an den angegebenen Benutzer delegieren können. Sie können mehrere Workflow-Modelle auswählen.

   Wenn Sie einem bestimmten Benutzer alle Elemente unabhängig vom Workflow-Modell zuweisen möchten, wählen Sie in der Dropdown-Liste des Workflow-Modells die Option **[!UICONTROL Alle Workflows]**. <br>

   Um einem bestimmten Benutzer Elemente für alle Workflow-Modelle außer einigen zuzuweisen, wählen Sie **[!UICONTROL Alle Workflows]** Wählen Sie in der Dropdown-Liste Workflow-Modell die Option **[!UICONTROL + Ausnahmen hinzufügen]**und geben Sie die Workflow-Modelle an, die ausgeschlossen werden sollen.
   <br>

   Wiederholen Sie diesen Schritt, damit Sie weitere Zuweisungselemente hinzufügen können. <br>

   >[!NOTE]
   >
   >Die Reihenfolge der Empfänger ist wichtig. Wenn ein Element einem Benutzer zugewiesen wird, der die Abwesenheitseinstellung aktiviert hat, wird das Element anhand der angegebenen Zielgruppenliste ausgewertet, in der die Bestellzuweisungen hinzugefügt werden. Wenn ein Element den Kriterien entspricht, wird es dem Bevollmächtigten zugewiesen und der nächste Bevollmächtigte wird nicht überprüft.

1. Wählen Sie **[!UICONTROL Speichern]** aus. Die Einstellung wird zum angegebenen Startzeitpunkt wirksam. Selbst wenn Sie sich während Ihrer Abwesenheit am System anmelden, gelten Sie erst wieder als anwesend, wenn Sie die Einstellungen ändern.

Nun werden alle während des Abwesenheitszeitraums empfangenen Elemente automatisch dem ausgewählten Empfänger zugewiesen.
![Abwesenheit](assets/out-of-office.png)

>[!NOTE]
>
>(Nur bei Formular-zentrierten Workflow-Elementen) Aktivieren Sie die Option **Zulassen, dass der Beauftragte mithilfe von Abwesenheits-Einstellungen delegiert** des Schritts **Aufgabe zuweisen**. Nur Elemente, bei denen die zuvor genannte Option aktiviert ist, werden an andere Benutzende delegiert.

## Beschränkungen {#limitations}

* Die Zuweisung von Elementen an eine Gruppe wird nicht unterstützt.
* Die Aktivierung von Abwesenheitszeiten für Projektaufgaben wird derzeit nicht unterstützt.
