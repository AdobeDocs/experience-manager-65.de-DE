---
title: Erstellen und Verwalten von A/B-Test für adaptive Formulare
seo-title: Create and manage A/B test for adaptive forms
description: AEM Forms kann mit Adobe Target integriert werden. Dies ermöglicht die Durchführung von A/B-Tests für adaptive Formulare, um das Kundenerlebnis und die Konvertierungsrate zu verbessern.
seo-description: AEM Forms integrates with Adobe Target that allows running A/B tests for adaptive forms to enhance customer experience and improve conversion rates.
uuid: e258805c-4da8-4c5d-ae91-7bea78a6a71b
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integrations
discoiquuid: 8f776f30-ff93-4d19-94c6-c4bfe6f1fae2
docset: aem65
exl-id: be2444df-c772-4a8e-83f9-0f565c15a44e
source-git-commit: 1def8ff7bc90e2ab82ce8b50277a97da9709c78c
workflow-type: tm+mt
source-wordcount: '1544'
ht-degree: 92%

---

# Erstellen und Verwalten von A/B-Test für adaptive Formulare{#create-and-manage-a-b-test-for-adaptive-forms}

## Übersicht {#overview-br}

Ihre Kunden werden ein Formular wahrscheinlich verlassen, wenn sie nicht davon angesprochen fühlen. Für die Kunden ist dies ein frustrierendes Erlebnis. Für Ihr Unternehmen kann es zusätzlichen Supportaufwand und Mehrkosten bedeuten. Das Kundenerlebnis optimal zu gestalten und dadurch eine höhere Konvertierungsrate zu erzielen, ist absolut unverzichtbar und stellt zugleich eine große Herausforderung dar. Mit Adobe Experience Manager Forms erhalten Sie das entscheidende Werkzeug dafür.

AEM Forms kann mit der Adobe Marketing Cloud-Lösung Adobe Target integriert werden, um den Kunden ein personalisiertes und ansprechendes Erlebnis über verschiedene digitale Kanäle zu bieten. Zu den Schlüsselfunktionen von Target gehören A/B-Tests. Diese Funktion ermöglicht die rasche Einrichtung parallel durchführbarer A/B-Tests, mit denen Sie speziell ausgewählten Benutzern relevante Inhalte präsentieren können, um zu ermitteln, welche Variante zu besseren Konvertierungsraten führt.

Mit AEM Forms können Sie A/B-Tests für adaptive Formulare in Echtzeit durchführen. Darüber hinaus stehen vordefinierte und vom Benutzer anpassbare Berichtsfunktionen zur Verfügung, mit denen Sie die Wirkung Ihrer Formulare in Echtzeit visualisieren und dasjenige identifizieren können, das das stärkste Interesse der Benutzer erweckt und in maximaler Konvertierung resultiert.

## Target einrichten und in AEM Forms integrieren {#set-up-and-integrate-target-in-aem-forms}

Bevor Sie mit der Erstellung und Analyse von A/B-Tests für adaptive Formulare beginnen, müssen Sie den Target-Server einrichten und in AEM Forms integrieren.

### Target einrichten {#set-up-target}

Wenn Sie AEM mit Target integrieren möchten, stellen Sie sicher, dass Sie über ein gültiges Adobe Target-Konto verfügen. Nach der Registrierung bei Adobe Target erhalten Sie einen Clientcode. Sie benötigen den Clientcode, die E-Mail-Adresse, die mit dem Target-Konto verknüpft sind, und das Kennwort, um AEM mit Target zu verbinden. 

Der Clientcode identifiziert das Adobe Target-Kundenkonto und wird als Subdomäne in einer URL verwendet, wenn er über den Adobe Target-Server aufgerufen wird. Melden Sie sich vor dem Fortfahren bei [https://experience.adobe.com/](https://experience.adobe.com/) an und, falls Sie Zugriff haben, zeigen Sie die Option [!DNL Adobe Target] im Abschnitt [!UICONTROL Schnellzugriff] an.

### Integration von Target in AEM Forms {#integrate-target-in-aem-forms}

Gehen Sie zur Integration eines laufenden Target-Servers in AEM Forms wie folgt vor:

1. Wechseln Sie auf AEM Server zu https://&lt;*Hostname*:&lt;*Port*>/libs/cq/core/content/tools/cloudservices.html.

1. Klicken Sie im Bereich **Adobe Target** auf **Konfigurationen anzeigen** und anschließend auf das Symbol **+**, um eine neue Konfiguration anzuzeigen.
Bei der Erstkonfiguration von Target klicken Sie auf **Jetzt konfigurieren**.

1. Geben Sie im Dialogfeld „Konfiguration erstellen“ einen **Titel** und optional einen **Namen** für die Konfiguration ein.

1. Klicken Sie auf **Erstellen**. Das Dialogfeld „Bearbeiten“ wird geöffnet.
1. Geben Sie Ihre Target-Kontodetails wie Clientcode, E-Mail und Kennwort an.
1. Wählen Sie **Rest** aus der Dropdownliste „API-Typ“ aus.

1. Klicken Sie auf **Mit Adobe Target verbinden**, um die Verbindung mit Target zu initialisieren. Wenn die Verbindung erfolgreich hergestellt wurde, wird die Meldung „Verbindung erfolgreich“ angezeigt. Klicken Sie auf **OK** und dann auf **OK**. Das Target-Konto wird konfiguriert.

1. Erstellen Sie ein Target-Framework, wie beschrieben in [Framework hinzufügen](/help/sites-administering/target.md).

1. Wechseln Sie zu https://&lt;*Hostname*:&lt;*Port*/system/console/configMgr.

1. Klicken Sie auf **AEM Forms Target-Konfiguration**.
1. Wählen Sie ein **Target-Framework** aus.
1. Geben Sie im Feld **Target-URLs** alle URLs an, für die A/B-Tests durchgeführt werden sollen. Beispiel: https://&lt;*Hostname*:&lt;*Port*>/ für AEM Forms-Server unter OSGi oder https://&lt;*Hostname*:&lt;*Port*/lc/ für AEM Forms-Server unter JEE.
Wenn Sie z. B. eine Target-URL für eine Instanz im Veröffentlichungsmodus konfigurieren möchten und Ihre Kunden über den Hostnamen oder die IP-Adresse darauf zugreifen können, müssen Sie beide konfigurieren – sowohl den Hostnamen als auch die IP-Adresse. Wenn Sie nur eine der URLs konfigurieren, ist der A/B-Test für Kunden, die über die andere URL zugreifen möchten, nicht möglich. Klicken Sie auf **+**, um mehrere URLs anzugeben.

1. Klicken Sie auf **Speichern**.

Ihr Target-Server wird in AEM Forms integriert. Sie können A/B-Tests jetzt aktivieren, wenn Sie eine vollständige Lizenz haben, um Adobe Target zu nutzen.

Wenn Sie über eine vollständige Lizenz verfügen, um Adobe Target zu nutzen, starten Sie den Server mit folgenden Parametern, nachdem Sie Target in AEM Forms integrieren:

`parameter -Dabtesting.enabled=true java -Xmx2048m -XX:MaxPermSize=512M -jar -Dabtesting.enabled=true`

Wenn die AEM-Instanz auf JBoss ausgeführt wird, gestartet als Dienst von Turnkey in der Datei `jboss\bin\standalone.conf.bat` fügen Sie -Dabtesting.enabled=true parameter im folgenden Eintrag hinzu:

`set "JAVA_OPTS=%JAVA_OPTS% -Dadobeidp.serverName=server1 -Dfile.encoding=utf8 -Djava.net.preferIPv4Stack=true -Dabtesting.enabled=true"`

Zusätzlich zum Jboss-Server können Sie das -Dabtesting.enabled=true jvm-Argument im Server-Startskript für alle Anwendungsserver hinzufügen. Sie können jetzt A/B-Tests für adaptive Formulare erstellen und ausführen.

>[!NOTE]
>
>Wenn Sie die konfigurierten Target-URLs später aktualisieren, achten Sie darauf, etwaige laufende A/B-Tests ebenfalls zu aktualisieren, sodass sie auf die aktuellen URLs verweisen. Weitere Informationen zur Aktualisierung von A/B-Tests finden Sie unter [A/B-Test aktualisieren](/help/forms/using/ab-testing-adaptive-forms.md#p-update-a-b-test-p).

## Erstellen von Zielgruppen in AEM {#create-audiences-within-aem}

Mit AEM können Sie eine Zielgruppe erstellen und für einen A/B-Test verwenden. Die Zielgruppe, die Sie in AEM erstellen, ist in AEM Forms verfügbar. Führen Sie die folgenden Schritte aus, um Zielgruppen in AEM zu erstellen:

1. Tippen Sie in der Instanz im Autorenmodus auf **Adobe Experience Manager** > **Personalization** > **Audiences**.

1. Tippen Sie auf der Seite „Zielgruppen“ auf **„Zielgruppe erstellen“ > „Target-Zielgruppe erstellen“**.
1. Wählen Sie im Dialogfeld „Adobe Target-Konfiguration“ eine Target-Konfiguration und klicken Sie auf **OK**.
1. Erstellen Sie auf der Seite „Neue Zielgruppe erstellen“ Regeln. Mit Regeln können Sie die Zielgruppe kategorisieren. Beispiel: Sie möchten die Zielgruppen basierend auf dem Betriebssystem kategorisieren. Ihre Zielgruppe A kommt von Windows und Zielgruppe B von Linux.

   1. Um die Zielgruppe basierend auf Windows zu kategorisieren, wählen Sie in Regel 1 den Attributtyp **OS** aus. Wählen Sie aus der Dropdownliste &quot;Wann&quot;die Option **Windows.** aus.

   1. Um die Zielgruppe basierend auf Linux zu kategorisieren, wählen Sie in Regel 2 den Attributtyp **OS** aus. Wählen Sie aus der Dropdownliste **Wenn** die Option **Linux** aus und klicken Sie auf **Weiter**.

1. Geben Sie einen Namen für die erstellte Zielgruppe an und klicken Sie auf **Speichern**.

Wie nachfolgend gezeigt, können Sie die Zielgruppe auswählen, wenn Sie A/B-Test für ein Formular konfigurieren.

## A/B-Test erstellen {#create-a-b-test}

Führen Sie die folgenden Schritte aus, um einen A/B-Test für ein adaptives Formular zu erstellen.

1. Navigieren Sie zu **Forms &amp; Documents** unter https://&lt;*Hostname*:&lt;*Port*>/aem/forms.html/content/dam/formsanddocuments.

1. Navigieren Sie zum Ordner mit dem adaptiven Formular.
1. Klicken Sie auf das Tool **Auswählen** in der Symbolleiste und wählen Sie das adaptive Formular aus.
1. Klicken Sie in der Symbolleiste auf **Mehr** und wählen Sie **A/B-Tests konfigurieren**. Die Seite „A/B-Tests konfigurieren“ wird geöffnet.

[ ](assets/ab-test-configure-1.png)

1. Geben Sie für **Name der Aktivität** den Namen des A/B-Tests ein.

1. Wählen Sie in der Dropdown-Liste „Zielgruppe“ die Zielgruppe, deren Reaktionen auf verschiedene Varianten des Formulars Sie testen möchten. Dies könnten beispielsweise **Besucher, die Chrome verwenden** sein. Die Zielgruppenliste wird vom konfigurierten Target-Server aus mit Werten gefüllt.

1. Geben Sie in den Feldern für **Erlebnisverteilung** für die Erlebnisvarianten A und B deren Verteilung auf die Gesamtzielgruppe in Prozent an. Wenn Sie beispielsweise „40“ und „60“ für Erlebnis A bzw. B angeben, wird Erlebnis A für 40 % der Zielgruppe und Erlebnis B für die verbleibenden 60 % angezeigt.
1. Klicken Sie auf **Konfigurieren**. Es wird ein Dialogfeld angezeigt, in dem die Erstellung des A/B-Tests bestätigt wird.
1. Klicken Sie auf **Erlebnis B bearbeiten**, um das adaptive Formular im Bearbeitungsmodus zu öffnen. Nehmen Sie Änderungen am Formular vor, um ein anderes Erlebnis zu erstellen, das sich von Erlebnis A unterscheidet. Für Erlebnis B sind die Varianten in den folgenden Bereichen möglich:

   * CSS oder Stil
   * Reihenfolge der Felder in verschiedenen Bereichen oder im selben Bereich
   * Bereichslayout
   * Bereichsnamen
   * Beschreibung, Beschriftung und Hilfetext für ein Feld
   * Skripte, die den Ablauf beim Senden nicht stören oder ganz abbrechen
   * Überprüfungen (client- und serverseitig)
   * Design für Erlebnis B (Sie können auch ein alternatives Design für Erlebnis B auswählen)

1. Wechseln Sie zur Benutzeroberfläche für Formulare und Dokumente, wählen Sie das adaptive Formular aus, klicken Sie auf **Mehr** und wählen Sie **A/B-Tests starten**.

Ihr A/B-Test wird jetzt ausgeführt und die Formularvarianten mit ihren unterschiedlichen Kundenerlebnissen werden der angegebenen Zielgruppe in der festgelegten Verteilung nach dem Zufallsprinzip präsentiert.

## A/B-Test aktualisieren {#update-a-b-test}

Sie können die Zielgruppe und die Verteilung der Erlebnisse eines laufenden A/B-Tests aktualisieren. Gehen Sie dazu wie folgt vor:

1. Navigieren Sie in der Benutzeroberfläche für Formulare und Dokumente zum Ordner mit dem adaptiven Formular, für das der A/B-Test durchgeführt wird.
1. Wählen Sie das adaptive Formular aus.
1. Klicken Sie auf **Mehr** und wählen Sie **A/B-Test bearbeiten**. Die Seite „A/B-Test aktualisieren“ wird geöffnet.

1. Aktualisieren Sie nach Bedarf die Zielgruppe und die Erlebnisverteilung.
1. Klicken Sie auf **Aktualisieren**.

## Bericht für A/B-Test anzeigen und analysieren {#view-and-analyze-a-b-test-report}

Nachdem der A/B-Test für den gewünschten Zeitraum durchgeführt wurde, können Sie einen Bericht erstellen und prüfen, mit welchem Erlebnis bessere Konvertierungsraten erzielt wurden. Sie können dann das Erlebnis mit den besseren Ergebnissen zum Gewinner erklären oder einen weitere A/B-Test durchführen. Führen Sie hierfür die folgenden Schritte aus:

1. Wählen Sie das adaptive Formular aus und klicken Sie auf **Mehr** und dann auf **A/B-Testbericht**. Der Bericht wird angezeigt.

[ ](assets/ab-test-report-3.png)

1. Analysieren Sie den Bericht und prüfen Sie, ob genügend Datenpunkte vorhanden sind, um eines der Erlebnisse mit besseren Werten als Gewinner zu wählen. Sie können denselben A/B-Test länger laufen lassen oder einen Gewinner wählen und den A/B-Test beenden.
1. Um einen Gewinner zu bestimmen und den A/B-Test zu beenden, klicken Sie auf die Schaltfläche **A/B-Test beenden** im Berichts-Dashboard. Sie werden in einem Dialogfeld aufgefordert, eines der beiden Erlebnisse als Gewinner zu wählen. Wählen Sie einen Gewinner und bestätigen Sie, dass Sie den A/B-Test beenden möchten.
 Alternativ dazu können Sie zuerst den Gewinner bestimmen, indem für das gewünschte Erlebnis auf **Gewinner bekanntgeben** klicken. Sie werden aufgefordert, den Gewinner zu bestätigen. Klicken Sie auf **Ja**, um den A/B-Tests zu beenden.

Wenn Sie Erlebnis A als Gewinner auswählen, wird der A/B-Test beendet und in Zukunft wird nur Erlebnis A für sämtliche Zielgruppen angezeigt.
