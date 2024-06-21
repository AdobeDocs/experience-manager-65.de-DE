---
title: Erstellen und Verwalten von A/B-Tests für adaptive Formulare
description: AEM Forms kann mit Adobe Target integriert werden, sodass Sie A/B-Tests für adaptive Formulare durchführen können, um das Kundenerlebnis und die Konversionsraten zu verbessern.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integrations
docset: aem65
exl-id: be2444df-c772-4a8e-83f9-0f565c15a44e
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: Admin, User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '1558'
ht-degree: 100%

---

# Erstellen und Verwalten von A/B-Test für adaptive Formulare{#create-and-manage-a-b-test-for-adaptive-forms}

[!BADGE Eingestellt]{type=negative tooltip="Diese Funktion wurde jetzt eingestellt"}

<div class="preview"> Die Funktion der A/B-Tests für adaptive Formulare hat das Ende der Lebensdauer erreicht und wird nicht mehr unterstützt. </div>

## Übersicht {#overview-br}

Ihre Kunden werden ein Formular wahrscheinlich verlassen, wenn sie nicht davon angesprochen fühlen. Für die Kundschaft ist dies ein frustrierendes Erlebnis, und für Ihr Unternehmen kann es zusätzlichen Support-Aufwand und Mehrkosten bedeuten. Das Kundenerlebnis optimal zu gestalten und dadurch eine höhere Konversionsrate zu erzielen, ist absolut unverzichtbar und stellt zugleich eine große Herausforderung dar. Adobe Experience Manager Forms ist der Schlüssel zu diesem Problem.

AEM Forms kann mit Adobe Target, einer Adobe Experience Cloud-Lösung, integriert werden, um Kundinnen und Kunden ein personalisiertes und ansprechendes Erlebnis über verschiedene digitale Kanäle zu bieten. Zu den Schlüsselfunktionen von Target gehören A/B-Tests. Diese Funktion ermöglicht die rasche Einrichtung parallel durchführbarer A/B-Tests, mit denen Sie speziell ausgewählten Benutzenden relevante Inhalte präsentieren können, um zu ermitteln, welche Variante zu besseren Konversionsraten führt.

Mit Adobe Experience Manager (AEM) Forms können Sie A/B-Tests für adaptive Formulare in Echtzeit durchführen. Es bietet außerdem vordefinierte und anpassbare Berichtsfunktionen, mit denen Sie die Wirkung Ihrer Formulare in Echtzeit visualisieren und dasjenige identifizieren können, das zur stärksten Benutzerinteraktion und maximalen Konversionen führt.

## Einrichten und Integrieren von Target in AEM Forms {#set-up-and-integrate-target-in-aem-forms}

Bevor Sie mit der Erstellung und Analyse von A/B-Tests für adaptive Formulare beginnen, müssen Sie den Target-Server einrichten und in AEM Forms integrieren.

### Einrichten von Target {#set-up-target}

Um AEM mit Target zu integrieren, stellen Sie sicher, dass Sie über ein gültiges Adobe Target-Konto verfügen. Nach der Registrierung bei Adobe Target erhalten Sie einen Clientcode. Sie benötigen den Clientcode, die E-Mail-Adresse, die mit dem Target-Konto verknüpft sind, und das Kennwort, um AEM mit Target zu verbinden.

Der Clientcode identifiziert das Adobe Target-Kundenkonto und wird als Subdomain in einer URL verwendet, wenn er über den Adobe Target-Server aufgerufen wird. Melden Sie sich vor dem Fortfahren bei [https://experience.adobe.com/](https://experience.adobe.com/) an. Wenn Sie Zugriffsrechte haben, schauen Sie sich die [!DNL Adobe Target]-Option in [!UICONTROL Schnellzugriff]-Abschnitt an.

### Integrieren eines laufenden Target-Servers in AEM Forms {#integrate-target-in-aem-forms}

1. Wechseln Sie auf dem AEM-Server zu „https://&lt;*hostname*>:&lt;*port*>/libs/cq/core/content/tools/cloudservices.html“.

1. Klicken Sie im Bereich **Adobe Target** auf **Konfigurationen anzeigen** und anschließend auf das Symbol **+**, um eine neue Konfiguration hinzuzufügen.
Wenn Sie Target zum ersten Mal konfigurieren, klicken Sie auf **Jetzt konfigurieren**.

1. Geben Sie im Dialogfeld „Konfiguration erstellen“ einen **Titel** und optional einen **Namen** für die Konfiguration an.

1. Klicken Sie auf **Erstellen**. Das Dialogfeld „Komponente bearbeiten“ wird geöffnet.
1. Geben Sie Ihre Target-Kontodetails an, z. B. Clientcode, E-Mail-Adresse und Passwort.
1. Wählen Sie **Rest** aus der Dropdownliste „API-Typ“ aus.

1. Klicken Sie auf **Mit Adobe Target verbinden**, um die Verbindung mit Target zu initialisieren. Wenn die Verbindung erfolgreich hergestellt wurde, wird die Meldung „Verbindung erfolgreich“ angezeigt. Klicken Sie auf **OK** und dann auf **OK**. Das Target-Konto wird konfiguriert.

1. Erstellen Sie ein Target-Framework, wie beschrieben in [Framework hinzufügen](/help/sites-administering/target.md).

1. Wechseln Sie zu „https://&lt;*hostname*>:&lt;*port*>/system/console/configMgr“.

1. Klicken Sie auf **AEM Forms-Target-Konfiguration**.
1. Wählen Sie ein **Target-Framework** aus.
1. Geben Sie im Feld **Target-URLs** alle URLs an, für die A/B-Tests durchgeführt werden sollen. Zum Beispiel https://&lt;*hostname*>:&lt;*port*>/ für AEM Forms Server auf OSGi oder https://&lt;*hostname*>:&lt;*port*>/lc/ für AEM Forms Server auf JEE.
Beachten Sie, dass Sie eine Target-URL für eine Veröffentlichungsinstanz konfigurieren und Ihre Kundinnen und Kunden über den Host-Namen oder die IP-Adresse darauf zugreifen können. In diesem Fall müssen Sie beide unter Verwendung des Host-Namens und der IP-Adresse als Ziel-URLs konfigurieren. Wenn Sie nur eine der URLs konfigurieren, ist der A/B-Test für Kundinnen und Kunden, die über die andere URL zugreifen möchten, nicht möglich. Klicken Sie auf **+**, um mehrere URLs anzugeben.

1. Klicken Sie auf **Speichern**.

Ihr Target-Server wird in AEM Forms integriert. Sie können A/B-Tests jetzt aktivieren, wenn Sie über eine vollständige Lizenz verfügen, um Adobe Target zu nutzen.

Wenn Sie über eine vollständige Lizenz verfügen, um Adobe Target zu nutzen, starten Sie den Server mit folgenden Parametern, nachdem Sie Target in AEM Forms integriert haben:

`parameter -Dabtesting.enabled=true java -Xmx2048m -XX:MaxPermSize=512M -jar -Dabtesting.enabled=true`

Wenn die AEM-Instanz auf JBoss® ausgeführt wird, gestartet als Dienst von Turnkey, fügen Sie in der Datei `jboss\bin\standalone.conf.bat` den Parameter -Dabtesting.enabled=true im folgenden Eintrag hinzu:

`set "JAVA_OPTS=%JAVA_OPTS% -Dadobeidp.serverName=server1 -Dfile.encoding=utf8 -Djava.net.preferIPv4Stack=true -Dabtesting.enabled=true"`

Zusätzlich zum JBoss®-Server können Sie das JVM-Argument „-Dabtesting.enabled=true“ im Server-Start-Skript für jeden Anwendungs-Server hinzufügen. Jetzt können Sie A/B-Tests für adaptive Formulare erstellen und ausführen.

>[!NOTE]
>
>Wenn Sie die konfigurierten Target-URLs später aktualisieren, achten Sie darauf, etwaige laufende A/B-Tests ebenfalls zu aktualisieren, sodass sie auf die aktuellen URLs verweisen. Informationen zum Aktualisieren von A/B-Tests finden Sie unter [Aktualisieren von A/B-Tests](/help/forms/using/ab-testing-adaptive-forms.md#p-update-a-b-test-p).
>

## Erstellen von Zielgruppen in AEM {#create-audiences-within-aem}

AEM ermöglicht die Erstellung einer Zielgruppe und ihre Verwendung für A/B-Tests. Die in AEM erstellte Zielgruppe ist in AEM Forms verfügbar. Gehen Sie wie folgt vor, um Zielgruppen zu erstellen:

1. Wählen Sie in der Autoreninstanz **Adobe Experience Manager** > **Personalisierung** > **Zielgruppen** aus.

1. Wählen Sie auf der Seite „Zielgruppen“ die Elemente **Zielgruppe erstellen > Target-Zielgruppe erstellen** aus.
1. Wählen Sie im Dialogfeld „Adobe Target-Konfiguration“ eine Target-Konfiguration und klicken Sie auf **OK**.
1. Erstellen Sie Regeln auf der Seite „Neue Zielgruppe erstellen“. Mit Regeln können Sie die Zielgruppe kategorisieren. Beispielsweise können Sie Zielgruppen basierend auf dem Betriebssystem kategorisieren. Ihre Zielgruppe A kommt von Windows und Audience B von Linux®.

   1. Um die Zielgruppe basierend auf Windows zu kategorisieren, wählen Sie in Regel Nr. 1 den Attributtyp **OS** aus. Aus der Dropdown-Liste „Wann“ wählen Sie **Windows**.

   1. Um die Zielgruppe basierend auf Linux® zu kategorisieren, wählen Sie in Regel Nr. 2 den Attributtyp **OS** aus. Wählen Sie aus der Dropdown-Liste **Wann**, wählen Sie **Linux®**. Klicken Sie dann auf **Weiter**.

1. Geben Sie einen Namen für die erstellte Zielgruppe an und klicken Sie auf **Speichern**.

Sie können die Zielgruppe auswählen, wenn Sie A/B-Tests für ein Formular konfigurieren, wie unten dargestellt.

## Erstellen eines A/B-Tests für ein adaptives Formular {#create-a-b-test}

1. Wechseln Sie zu **Formulare und Dokumente** unter „https://&lt;*hostname*>:&lt;*port*>/aem/forms.html/content/dam/formsanddocuments“.

1. Navigieren Sie zum Ordner mit dem adaptiven Formular.
1. Klicken Sie auf das **Auswählen**-Tool in der Symbolleiste und wählen Sie das adaptive Formular aus.
1. Klicken Sie in der Symbolleiste auf **Mehr** und wählen Sie **A/B-Tests konfigurieren** aus. Die Seite „A/B-Test konfigurieren“ wird geöffnet.

[](assets/ab-test-configure-1.png)

1. Geben Sie für **Name der Aktivität** den Namen des A/B-Tests ein.

1. Wählen Sie in der Dropdown-Liste „Zielgruppe“ die Zielgruppe, deren Reaktionen auf verschiedene Varianten des Formulars Sie testen möchten. Dies könnten beispielsweise **Besucher, die Chrome verwenden** sein. Die Zielgruppenliste wird vom konfigurierten Target-Server ausgefüllt.

1. Geben Sie in den Feldern für **Erlebnisverteilung** für die Erlebnisvarianten A und B deren Verteilung auf die Gesamtzielgruppe in Prozent an. Wenn Sie beispielsweise „40“ und „60“ für Erlebnis A bzw. B angeben, wird Erlebnis A für 40 % der Zielgruppe und Erlebnis B für die verbleibenden 60 % angezeigt.
1. Klicken Sie auf **Konfigurieren**. Es wird ein Dialogfeld angezeigt, um die Erstellung des A/B-Tests zu bestätigen.
1. Klicken Sie auf **Erlebnis B bearbeiten**, um das adaptive Formular im Bearbeitungsmodus zu öffnen. Nehmen Sie Änderungen am Formular vor, um ein anderes Erlebnis zu erstellen, das sich von Erlebnis A unterscheidet. Für Erlebnis B sind die Varianten in den folgenden Bereichen möglich:

   * CSS oder Stil
   * Reihenfolge der Felder in verschiedenen Bereichen oder im selben Bereich
   * Bereichslayout
   * Bereichsnamen
   * Beschreibung, Kennzeichnung und Hilfetext für ein Feld
   * Skripte, die den Übermittlungsfluss nicht beeinflussen oder unterbrechen
   * Validierungen (Client- und Server-seitig)
   * Design für Erlebnis B (Sie können ein alternatives Design für Erlebnis B auswählen)

1. Wechseln Sie zur Benutzeroberfläche „Formulare und Dokumente“, wählen Sie das adaptive Formular aus, klicken Sie auf **Mehr** und wählen Sie **A/B-Tests starten** aus.

Ihr A/B-Test wird jetzt ausgeführt und der angegebenen Zielgruppe werden auf der Grundlage der angegebenen Verteilung zufällig die Erlebnisse bereitgestellt.

## Aktualisieren von A/B-Tests {#update-a-b-test}

Sie können die Zielgruppe und die Verteilung der Erlebnisse eines laufenden A/B-Tests aktualisieren.

Aktualisieren von A/B-Tests:

1. Navigieren Sie in der Benutzeroberfläche von „Formulare und Dokumente“ zu dem Ordner, der das adaptive Formular enthält, für das der A/B-Test ausgeführt wird.
1. Wählen Sie das adaptive Formular aus.
1. Klicken Sie auf **Mehr** und wählen Sie **A/B-Test bearbeiten**. Die Seite „A/B-Test aktualisieren“ wird geöffnet.

1. Aktualisieren Sie die Zielgruppen- und Erlebnisverteilungen nach Bedarf.
1. Klicken Sie auf **Aktualisieren**.

## Anzeigen und Analysieren des A/B-Testberichts {#view-and-analyze-a-b-test-report}

Nachdem der A/B-Test für den gewünschten Zeitraum durchgeführt wurde, können Sie einen Bericht erstellen und prüfen, mit welchem Erlebnis bessere Konvertierungsraten erzielt wurden. Sie können dann das Erlebnis mit den besseren Ergebnissen zum Gewinner erklären oder einen weiteren A/B-Test durchführen.

Anzeigen und Analysieren des A/B-Testberichts:

1. Wählen Sie das adaptive Formular aus, klicken Sie auf **Mehr** und klicken Sie anschließend auf **A/B-Testbericht**. Der Bericht wird angezeigt.

[](assets/ab-test-report-3.png)

1. Analysieren Sie den Bericht und prüfen Sie, ob genügend Datenpunkte vorhanden sind, um eines der Erlebnisse mit besseren Werten als Gewinner zu wählen. Sie können denselben A/B-Test länger laufen lassen oder einen Gewinner wählen und den A/B-Test beenden.
1. Um einen Gewinner zu bestimmen und den A/B-Test zu beenden, klicken Sie im Berichts-Dashboard auf die Schaltfläche **A/B-Test beenden**. Sie werden in einem Dialogfeld aufgefordert, eines der beiden Erlebnisse als Gewinner zu wählen. Wählen Sie einen Gewinner und bestätigen Sie, dass Sie den A/B-Test beenden möchten.
 Alternativ dazu können Sie zuerst den Gewinner bestimmen, indem für das gewünschte Erlebnis auf **Gewinner bekanntgeben** klicken. Sie werden aufgefordert, den Gewinner zu bestätigen. Klicken Sie auf **Ja**, um den A/B-Tests zu beenden.

Wenn Sie Erlebnis A als Gewinner auswählen, wird der A/B-Test beendet und in Zukunft wird nur Erlebnis A für alle Zielgruppen angezeigt.
