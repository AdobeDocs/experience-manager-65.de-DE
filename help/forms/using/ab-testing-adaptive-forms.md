---
title: Erstellen und Verwalten von A/B-Tests für adaptive Formulare
seo-title: Create and manage A/B test for adaptive forms
description: AEM Forms kann mit Adobe Target integriert werden, sodass Sie A/B-Tests für adaptive Formulare durchführen können, um das Kundenerlebnis zu verbessern und Konversionsraten zu verbessern.
seo-description: AEM Forms integrates with Adobe Target that allows running A/B tests for adaptive forms to enhance customer experience and improve conversion rates.
uuid: e258805c-4da8-4c5d-ae91-7bea78a6a71b
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integrations
discoiquuid: 8f776f30-ff93-4d19-94c6-c4bfe6f1fae2
docset: aem65
exl-id: be2444df-c772-4a8e-83f9-0f565c15a44e
source-git-commit: ccbb6a33c2ee8029d2e82d9098c07de18af166ac
workflow-type: tm+mt
source-wordcount: '1569'
ht-degree: 58%

---

# Erstellen und Verwalten von A/B-Test für adaptive Formulare{#create-and-manage-a-b-test-for-adaptive-forms}

|Negativ|[!BADGE Abbruch]{type=negative tooltip="Diese Funktion ist jetzt eingestellt"}|
<div class="preview"> Die A/B-Tests für adaptive Formulare haben das Ende der Lebensdauer erreicht und werden nicht mehr unterstützt. </div>

## Übersicht {#overview-br}

Ihre Kunden werden ein Formular wahrscheinlich verlassen, wenn sie nicht davon angesprochen fühlen. Für die Kunden ist dies ein frustrierendes Erlebnis. Für Ihr Unternehmen kann es zusätzlichen Supportaufwand und Mehrkosten bedeuten. Das Kundenerlebnis optimal zu gestalten und dadurch eine höhere Konvertierungsrate zu erzielen, ist absolut unverzichtbar und stellt zugleich eine große Herausforderung dar. Adobe Experience Manager Forms ist der Schlüssel zu diesem Problem.

AEM Forms kann mit der Adobe Marketing Cloud-Lösung Adobe Target integriert werden, um den Kunden ein personalisiertes und ansprechendes Erlebnis über verschiedene digitale Kanäle zu bieten. Eine der wichtigsten Funktionen von Target sind A/B-Tests, mit denen Sie schnell gleichzeitige A/B-Tests einrichten, zielgruppenrelevante Inhalte präsentieren und Erlebnisse ermitteln können, die zu einer besseren Konversionsrate führen.

Mit AEM Forms können Sie A/B-Tests für adaptive Formulare in Echtzeit durchführen. Es bietet außerdem vordefinierte und anpassbare Berichtsfunktionen, mit denen Sie die Echtzeit-Leistung Ihrer Formulare visualisieren und diejenigen identifizieren können, die die Benutzerinteraktion und -konvertierung maximieren.

## Target einrichten und in AEM Forms integrieren {#set-up-and-integrate-target-in-aem-forms}

Bevor Sie mit der Erstellung und Analyse von A/B-Tests für adaptive Formulare beginnen, müssen Sie Ihren Target-Server einrichten und in AEM Forms integrieren.

### Target einrichten {#set-up-target}

Um AEM mit Target zu integrieren, stellen Sie sicher, dass Sie über ein gültiges Adobe Target-Konto verfügen. Nach der Registrierung bei Adobe Target erhalten Sie einen Clientcode. Sie benötigen den Clientcode, die mit dem Target-Konto verknüpfte E-Mail-Adresse und das Kennwort, um AEM mit Target zu verbinden.

Der Clientcode identifiziert das Adobe Target-Kundenkonto und wird als Subdomain in einer URL verwendet, wenn er über den Adobe Target-Server aufgerufen wird. Melden Sie sich vor dem Fortfahren bei [https://experience.adobe.com/](https://experience.adobe.com/) an. Wenn Sie Zugriffsrechte haben, schauen Sie sich die [!DNL Adobe Target]-Option in [!UICONTROL Schnellzugriff]-Abschnitt an.

### Target in AEM Forms integrieren {#integrate-target-in-aem-forms}

Führen Sie die folgenden Schritte aus, um einen laufenden Target-Server in AEM Forms zu integrieren:

1. Wechseln Sie auf dem AEM-Server zu „https://&lt;*hostname*>:&lt;*port*>/libs/cq/core/content/tools/cloudservices.html“.

1. Klicken Sie im Bereich **Adobe Target** auf **Konfigurationen anzeigen** und anschließend auf das Symbol **+**, um eine neue Konfiguration anzuzeigen.
Bei der Erstkonfiguration von Target klicken Sie auf **Jetzt konfigurieren**.

1. Geben Sie im Dialogfeld Konfiguration erstellen eine **Titel** und optional **Name** für die Konfiguration.

1. Klicken Sie auf **Erstellen**. Das Dialogfeld Komponente bearbeiten wird geöffnet.
1. Geben Sie Ihre Target-Kontodetails an, z. B. Clientcode, E-Mail-Adresse und Kennwort.
1. Wählen Sie **Rest** aus der Dropdownliste „API-Typ“ aus.

1. Klicken Sie auf **Mit Adobe Target verbinden**, um die Verbindung mit Target zu initialisieren. Wenn die Verbindung erfolgreich hergestellt wurde, wird die Meldung „Verbindung erfolgreich“ angezeigt. Klicken Sie auf **OK** und dann auf **OK**. Das Target-Konto wird konfiguriert.

1. Erstellen Sie ein Target-Framework, wie beschrieben in [Framework hinzufügen](/help/sites-administering/target.md).

1. Wechseln Sie zu „https://&lt;*hostname*>:&lt;*port*>/system/console/configMgr“.

1. Klicken **AEM Forms Target-Konfiguration**.
1. Wählen Sie eine **Target Framework**.
1. Geben Sie im Feld **Target-URLs** alle URLs an, für die A/B-Tests durchgeführt werden sollen. Zum Beispiel https://&lt;*hostname*>:&lt;*port*>/ für AEM Forms-Server auf OSGi oder https://&lt;*hostname*>:&lt;*port*>/lc/ für AEM Forms-Server auf JEE.
Wenn Sie z. B. eine Target-URL für eine Instanz im Veröffentlichungsmodus konfigurieren möchten und Ihre Kunden über den Hostnamen oder die IP-Adresse darauf zugreifen können, müssen Sie beide konfigurieren – sowohl den Hostnamen als auch die IP-Adresse. Wenn Sie nur eine der URLs konfigurieren, ist der A/B-Test für Kunden, die über die andere URL zugreifen möchten, nicht möglich. Klicken Sie auf **+**, um mehrere URLs anzugeben.

1. Klicken Sie auf **Speichern**.

Ihr Target-Server wird in AEM Forms integriert. Sie können A/B-Tests jetzt aktivieren, wenn Sie über eine vollständige Lizenz verfügen, um Adobe Target zu nutzen.

Wenn Sie über eine vollständige Lizenz verfügen, um Adobe Target zu nutzen, starten Sie den Server mit folgenden Parametern, nachdem Sie Target in AEM Forms integrieren:

`parameter -Dabtesting.enabled=true java -Xmx2048m -XX:MaxPermSize=512M -jar -Dabtesting.enabled=true`

Wenn die AEM-Instanz auf JBoss ausgeführt wird, gestartet als Dienst von Turnkey in der Datei `jboss\bin\standalone.conf.bat` fügen Sie -Dabtesting.enabled=true parameter im folgenden Eintrag hinzu:

`set "JAVA_OPTS=%JAVA_OPTS% -Dadobeidp.serverName=server1 -Dfile.encoding=utf8 -Djava.net.preferIPv4Stack=true -Dabtesting.enabled=true"`

Zusätzlich zum JBoss-Server können Sie das Argument -Dabtesting.enabled=true jvm im Serverstartskript für jeden Anwendungsserver hinzufügen. Jetzt können Sie A/B-Tests für adaptive Formulare erstellen und ausführen.

>[!NOTE]
>
>Wenn Sie die konfigurierten Target-URLs später aktualisieren, achten Sie darauf, etwaige laufende A/B-Tests ebenfalls zu aktualisieren, sodass sie auf die aktuellen URLs verweisen. Informationen zum Aktualisieren von A/B-Tests finden Sie unter [A/B-Test aktualisieren](/help/forms/using/ab-testing-adaptive-forms.md#p-update-a-b-test-p).

## Erstellen von Zielgruppen in AEM {#create-audiences-within-aem}

AEM ermöglicht die Erstellung einer Audience und deren Verwendung für A/B-Tests. Die in AEM erstellte Zielgruppe ist in AEM Forms verfügbar. Führen Sie die folgenden Schritte aus, um Zielgruppen in AEM zu erstellen:

1. Tippen Sie in der Instanz im Autorenmodus auf **Adobe Experience Manager** > **Personalization** > **Audiences**.

1. Tippen Sie auf der Seite „Zielgruppen“ auf **„Zielgruppe erstellen“ > „Target-Zielgruppe erstellen“**.
1. Wählen Sie im Dialogfeld „Adobe Target-Konfiguration“ eine Target-Konfiguration und klicken Sie auf **OK**.
1. Erstellen Sie auf der Seite Neue Zielgruppe erstellen Regeln. Mit Regeln können Sie die Zielgruppe kategorisieren. Sie möchten beispielsweise Zielgruppen basierend auf dem Betriebssystem kategorisieren. Ihre Audience A stammt aus Windows und Audience B aus Linux.

   1. Um die Zielgruppe basierend auf Windows zu kategorisieren, wählen Sie in Regel Nr. 1 den Attributtyp **OS** aus. Aus der Dropdownliste „Wann“ wählen Sie **Windows**.

   1. Um die Zielgruppe basierend auf Linux zu kategorisieren, wählen Sie in Regel Nr. 2 den Attributtyp **OS** aus. Aus der Dropdownliste **„Wann“** wählen Sie **Linux**. Klicken Sie dann auf **Weiter**.

1. Geben Sie einen Namen für die erstellte Zielgruppe an und klicken Sie auf **Speichern**.

Sie können die Zielgruppe auswählen, wenn Sie A/B-Tests für ein Formular konfigurieren, wie unten dargestellt.

## A/B-Test erstellen {#create-a-b-test}

Führen Sie die folgenden Schritte aus, um einen A/B-Test für ein adaptives Formular zu erstellen.

1. Wechseln Sie zu **Formulare und Dokumente** unter „https://&lt;*hostname*>:&lt;*port*>/aem/forms.html/content/dam/formsanddocuments“.

1. Navigieren Sie zum Ordner mit dem adaptiven Formular.
1. Klicken Sie auf **Auswählen** in der Symbolleiste und wählen Sie das adaptive Formular aus.
1. Klicken **Mehr** in der Symbolleiste und wählen Sie **Konfigurieren von A/B-Tests**. Die Seite A/B-Tests konfigurieren wird geöffnet.

[ ](assets/ab-test-configure-1.png)

1. Geben Sie für **Name der Aktivität** den Namen des A/B-Tests ein.

1. Wählen Sie in der Dropdown-Liste „Zielgruppe“ die Zielgruppe, deren Reaktionen auf verschiedene Varianten des Formulars Sie testen möchten. Dies könnten beispielsweise **Besucher, die Chrome verwenden** sein. Die Zielgruppenliste wird vom konfigurierten Target-Server aus gefüllt.

1. Geben Sie in den Feldern für **Erlebnisverteilung** für die Erlebnisvarianten A und B deren Verteilung auf die Gesamtzielgruppe in Prozent an. Wenn Sie beispielsweise 40 bzw. 60 für Erlebnis A bzw. B angeben, wird Erlebnis A für 40 % der Zielgruppe und Erlebnis B für die restlichen 60 % bereitgestellt.
1. Klicken Sie auf **Konfigurieren**. Es wird ein Dialogfeld angezeigt, in dem die Erstellung des A/B-Tests bestätigt wird.
1. Klicken Sie auf **Erlebnis B bearbeiten**, um das adaptive Formular im Bearbeitungsmodus zu öffnen. Nehmen Sie Änderungen am Formular vor, um ein anderes Erlebnis zu erstellen, das sich von Erlebnis A unterscheidet. Für Erlebnis B sind die Varianten in den folgenden Bereichen möglich:

   * CSS oder Stil
   * Reihenfolge der Felder in verschiedenen Bereichen oder im selben Bereich
   * Bereichslayout
   * Bereichsnamen
   * Beschreibung, Beschriftung und Hilfetext für ein Feld
   * Skripte, die den Übermittlungsfluss nicht beeinflussen oder unterbrechen
   * Überprüfungen (client- und serverseitig)
   * Design für Erlebnis B (Sie können ein alternatives Design für Erlebnis B auswählen)

1. Wechseln Sie zur Benutzeroberfläche &quot;Forms und Dokumente&quot;, wählen Sie das adaptive Formular aus und klicken Sie auf **Mehr** und wählen Sie **A/B-Tests starten**.

Ihr A/B-Test wird jetzt ausgeführt und die angegebene Zielgruppe wird auf der Grundlage der angegebenen Verteilung zufällig für die Erlebnisse bereitgestellt.

## A/B-Test aktualisieren {#update-a-b-test}

Sie können die Zielgruppe und die Verteilung der Erlebnisse eines laufenden A/B-Tests aktualisieren. Gehen Sie dazu wie folgt vor:

1. Navigieren Sie in der Benutzeroberfläche von Forms und Dokumenten zu dem Ordner, der das adaptive Formular enthält, für das der A/B-Test ausgeführt wird.
1. Wählen Sie das adaptive Formular aus.
1. Klicken Sie auf **Mehr** und wählen Sie **A/B-Test bearbeiten**. Die Seite „A/B-Test aktualisieren“ wird geöffnet.

1. Aktualisieren Sie die Zielgruppen- und Erlebnisverteilung nach Bedarf.
1. Klicken Sie auf **Aktualisieren**.

## Anzeigen und Analysieren des A/B-Testberichts {#view-and-analyze-a-b-test-report}

Nachdem der A/B-Test für den gewünschten Zeitraum durchgeführt wurde, können Sie einen Bericht erstellen und prüfen, mit welchem Erlebnis bessere Konvertierungsraten erzielt wurden. Sie können dann das Erlebnis mit den besseren Ergebnissen zum Gewinner erklären oder einen weitere A/B-Test durchführen. Führen Sie dazu die folgenden Schritte aus:

1. Wählen Sie das adaptive Formular aus und klicken Sie auf **Mehr** und klicken Sie anschließend auf **A/B-Testbericht**. Der Bericht wird angezeigt.

[ ](assets/ab-test-report-3.png)

1. Analysieren Sie den Bericht und prüfen Sie, ob genügend Datenpunkte vorhanden sind, um eines der Erlebnisse mit besseren Werten als Gewinner zu wählen. Sie können denselben A/B-Test länger laufen lassen oder einen Gewinner wählen und den A/B-Test beenden.
1. Um einen Gewinner zu bestimmen und den A/B-Test zu beenden, klicken Sie auf die Schaltfläche **A/B-Test beenden** im Berichts-Dashboard. Sie werden in einem Dialogfeld aufgefordert, eines der beiden Erlebnisse als Gewinner zu wählen. Wählen Sie einen Gewinner und bestätigen Sie, dass Sie den A/B-Test beenden möchten.
 Alternativ dazu können Sie zuerst den Gewinner bestimmen, indem für das gewünschte Erlebnis auf **Gewinner bekanntgeben** klicken. Sie werden aufgefordert, den Gewinner zu bestätigen. Klicken Sie auf **Ja**, um den A/B-Tests zu beenden.

Wenn Sie Erlebnis A als Gewinner auswählen, wird der A/B-Test beendet und in Zukunft wird nur Erlebnis A für sämtliche Zielgruppen angezeigt.
