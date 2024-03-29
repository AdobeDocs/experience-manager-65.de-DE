---
title: Konfigurieren der Übersetzungsintegration
description: Erfahren Sie, wie Sie AEM mit einem Übersetzungs-Service verbinden.
exl-id: a1a4b1ca-d353-46e2-a992-f38be6be338e
source-git-commit: 10b370fd8f855f71c6d7d791c272137bb5e04d97
workflow-type: ht
source-wordcount: '1143'
ht-degree: 100%

---

# Konfigurieren der Übersetzungsintegration {#configure-integration}

Erfahren Sie, wie Sie AEM mit einem Übersetzungsdienst verbinden.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der AEM Headless-Übersetzungs-Tour, [Erste Schritte mit der AEM Headless-Übersetzung](learn-about.md), haben Sie gelernt, wie Sie Ihre Headless-Inhalte organisieren und wie AEM Übersetzungs-Tools funktionieren. Sie sollten jetzt:

* die Bedeutung der Inhaltsstruktur für die Übersetzung verstehen.
* verstehen, wie AEM Headless-Inhalte speichert.
* mit den Übersetzungs-Tools von AEM vertraut sein.

Dieser Artikel baut auf diesen Grundlagen auf, damit Sie den ersten Konfigurationsschritt durchführen und einen Übersetzungsdienst einrichten können, den Sie später in der Tour verwenden werden, um Ihre Inhalte zu übersetzen.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Sie eine AEM-Integration für Ihren ausgewählten Übersetzungsdienst einrichten. Nach dem Lesen sollten Sie:

* die wichtigen Parameter des Translation Integration Framework in AEM verstehen.
* In der Lage sein, Ihre eigene Verbindung zu Ihrem Übersetzungsdienst einzurichten.

## Das Translation Integration Framework {#tif}

Das Framework für die Übersetzungsintegration (Translation Integration Framework, TIF) integriert Übersetzungsdienste von Drittanbietern, um die Übersetzung von AEM-Inhalten zu orchestrieren. Dies umfasst drei grundlegende Schritte.

1. Verbinden Sie sich mit Ihrem Übersetzungsdienstleister.
1. Erstellen Sie eine Framework-Konfiguration für die Übersetzungsintegration.
1. Verknüpfen Sie die Konfiguration mit Ihren Inhalten.

Die folgenden Abschnitte beschreiben diese Schritte detaillierter.

## Herstellen einer Verbindung zu einem Übersetzungsdienstleister {#connect-translation-provider}

Der erste Schritt besteht darin, den gewünschten Übersetzungsdienst auszuwählen. Es gibt viele Möglichkeiten für menschliche und maschinelle Übersetzungen, die in AEM zur Verfügung stehen. Die meisten Anbieter bieten ein Übersetzungspaket zur Installation an. Im Abschnitt [Zusätzliche Ressourcen](#additional-resources) finden Sie eine Auswahl der verfügbaren Optionen.

>[!NOTE]
>
>Der Übersetzungsspezialist ist in der Regel für die Auswahl des zu verwendenden Übersetzungsdienstes verantwortlich. Der Administrator ist jedoch in der Regel für die Installation des erforderlichen Übersetzungs-Connector-Pakets zuständig.

Für diese Tour verwenden wir den Microsoft Translator, der von AEM vorkonfiguriert mit einer Testlizenz geliefert wird. Weitere Informationen über diesen Anbieter finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources).

Wenn Sie einen anderen Anbieter auswählen, muss Ihr Administrator das Connector-Paket gemäß den Anweisungen des Übersetzungsdienstes installieren.

>[!NOTE]
>
>Die Verwendung des vorkonfigurierten Microsoft Translator in AEM erfordert keine zusätzliche Einrichtung und funktioniert wie gewohnt ohne zusätzliche Connector-Konfiguration.
>
>Wenn Sie den Microsoft Translator-Connector zu Testzwecken verwenden, müssen Sie die Schritte in den folgenden beiden Abschnitten nicht ausführen: [Erstellen einer Konfiguration für die Übersetzungsintegration](#create-config) und [Verknüpfen der Konfiguration mit Ihren Inhalten.](#associate) Es wird jedoch empfohlen, sie zu lesen, damit Sie mit den Schritten vertraut sind, mit denen Sie Ihren bevorzugten Connector konfigurieren müssen.
>
>Die Testlizenz des Microsoft Translator-Connectors ist nicht für Produktionszwecke gedacht. Wenn Sie sich für eine Lizenzierung entscheiden, muss die bzw. der Systemadmin die im Abschnitt [Zusätzliche Ressourcen](#additional-resources) am Ende dieses Dokuments beschriebenen Schritte ausführen, um diese Lizenz zu konfigurieren.

## Erstellen einer Konfiguration für die Übersetzungsintegration {#create-config}

Nachdem das Connector-Paket für Ihren bevorzugten Übersetzungsdienst installiert wurde, müssen Sie eine Konfiguration für das Translation Integration Framework für diesen Dienst erstellen. Die Konfiguration enthält die folgenden Informationen:

* welcher Übersetzungsanbieter eingesetzt werden soll
* ob eine menschliche oder maschinelle Übersetzung erfolgen soll
* ob weitere Inhalte übersetzt werden sollen, die den Inhaltsfragmenten zugeordnet sind, beispielsweise Tags

So erstellen Sie eine Übersetzungskonfiguration:

1. Klicken Sie im globalen Navigationsmenü auf **Tools** > **Cloud-Services** > **Übersetzungs-Cloud-Services**.
1. Navigieren Sie zu der Stelle in Ihrer Inhaltsstruktur, an der Sie die Konfiguration erstellen möchten. Diese bezieht sich oft auf ein bestimmted Projekt oder kann global sein.
   * In diesem Fall kann beispielsweise eine Konfiguration global vorgenommen werden, um sie auf alle Inhalte oder nur auf das WKND-Projekt anzuwenden.

   ![Speicherort der Übersetzungskonfiguration](assets/translation-configuration-location.png)

1. Geben Sie die folgenden Informationen in die Felder ein und klicken Sie dann auf **Erstellen**.
   1. Wählen Sie **Konfigurationstyp** in der Dropdown-Liste aus. Wählen Sie **Übersetzungsintegration** aus der Liste aus.
   1. Geben Sie einen **Titel** für Ihre Konfiguration ein. Durch den **Titel** wird die Konfiguration in der **Cloud Services**-Konsole und in Dropdown-Listen mit den Seiteneigenschaften identifiziert.
   1. Geben Sie optional einen **Namen** für den Repository-Knoten ein, auf dem die Konfiguration gespeichert wird.

   ![Erstellen einer Übersetzungskonfiguration](assets/create-translation-configuration.png)

1. Klicken Sie auf **Erstellen**. Daraufhin wird das Fenster **Konfiguration bearbeiten** angezeigt, in dem Sie die Konfigurationseigenschaften konfigurieren können.

1. Denken Sie daran, dass Inhaltsfragmente in AEM als Assets gespeichert werden. Klicken Sie auf die Registerkarte **Assets**.

![Eigenschaften der Übersetzungskonfiguration](assets/translation-configuration.png)

1. Geben Sie die folgenden Informationen ein.

   1. **Übersetzungsmethode** – Wählen Sie **Maschinelle Übersetzung** oder **Menschliche Übersetzung** aus, abhängig von Ihrem Übersetzungsanbieter. Für diese Tour gehen wir von maschineller Übersetzung aus.
   1. **Übersetzungsanbieter** – Wählen Sie in der Liste den Connector aus, den Sie für Ihren Übersetzungsdienst installiert haben.
   1. **Inhaltskategorie** – Wählen Sie die am besten geeignete Kategorie aus, um die Übersetzung gezielter durchzuführen (nur für maschinelle Übersetzung).
   1. **Übersetzen von Inhaltsfragment-Assets** – Aktivieren Sie diese Option, um Assets zu übersetzen, die mit Inhaltsfragmenten verknüpft sind.
   1. **Übersetzen von Assets** – Aktivieren Sie diese Option, um die Assets zu übersetzen.
   1. **Metadaten übersetzen** – Aktivieren Sie diese Option, um Asset-Metadaten zu übersetzen.
   1. **Tags übersetzen** – Aktivieren Sie diese Option, um Tags zu übersetzen, die mit dem Asset verknüpft sind.
   1. **Übersetzung automatisch ausführen** – Aktivieren Sie diese Eigenschaft, wenn Übersetzungen automatisch an Ihren Übersetzungs-Service gesendet werden sollen.

1. Klicken Sie auf **Speichern und schließen**.

Sie haben jetzt den Connector für Ihren Übersetzungsdienst konfiguriert.

## Verknüpfen der Konfiguration mit Ihren Inhalten {#associate}

AEM ist ein flexibles und leistungsstarkes Tool und unterstützt über mehrere Connectoren und mehrere Konfigurationen mehrere, gleichzeitige Übersetzungsdienste. Die Einrichtung einer solchen Konfiguration sprengt den Rahmen dieser Tour. Diese Flexibilität bedeutet jedoch, dass Sie angeben müssen, welche Connectoren und Konfigurationen für die Übersetzung Ihrer Inhalte verwendet werden sollen, indem Sie diese Konfiguration mit Ihren Inhalten verknüpfen.

Gehen Sie dazu zum Sprachstamm Ihrer Inhalte. Für unsere Beispielzwecke ist dies

```text
/content/dam/<your-project>/en
```

1. Gehen Sie in der globalen Navigation zu **Navigation** > **Assets** > **Dateien**.
1. Wählen Sie in der Assets-Konsole den zu konfigurierenden Sprachstamm aus und klicken Sie auf **Eigenschaften**.
1. Klicken Sie auf die Registerkarte **Cloud-Services**.
1. Wählen Sie unter **Cloud-Service-Konfigurationen** in der Dropdown-Liste **Konfiguration hinzufügen** Ihren Connector aus. Er sollte in der Dropdown-Liste angezeigt werden, wenn Sie das Paket wie [weiter oben beschrieben](#connect-translation-provider) installiert haben.
1. Wählen Sie unter **Cloud-Service-Konfigurationen** in der Dropdown-Liste **Konfiguration hinzufügen** auch Ihre Konfiguration aus.
1. Klicken Sie auf **Speichern und schließen**.

![Wählen Sie Cloud-Service-Konfigurationen aus.](assets/select-cloud-service-configurations.png)

## Wie geht es weiter {#what-is-next}

Nachdem Sie nun diesen Teil der Headless-Übersetzungs-Tour abgeschlossen haben, sollten Sie:

* die wichtigen Parameter des Translation Integration Framework in AEM verstehen.
* in der Lage sein, Ihre eigene Verbindung zu Ihrem Übersetzungs-Service einzurichten.

Bauen Sie auf diesem Wissen auf und setzen Sie Ihre AEM Headless-Übersetzngs-Tour fort, indem Sie als Nächstes das Dokument [Übersetzungsregeln konfigurieren](translation-rules.md) lesen, in dem Sie erfahren, wie Sie festlegen, welche Inhalte übersetzt werden sollen.

## Zusätzliche Ressourcen {#additional-resources}

Es wird zwar empfohlen, zum nächsten Teil der Headless-Übersetzungs-Tour voranzuschreiten, indem Sie das Dokument [Übersetzungsregeln konfigurieren](translation-rules.md) lesen. Im Folgenden finden Sie einige zusätzliche optionale Ressourcen, die einige in diesem Dokument erwähnte Konzepte vertiefen. Sie sind jedoch nicht erforderlich, um mit der Headless-Tour fortzufahren.

* [Konfigurieren des Translation Integration Framework](/help/sites-administering/tc-tic.md) – Überprüfen Sie eine Liste ausgewählter Übersetzungs-Connectoren und erfahren Sie, wie Sie das Translation Integration Framework konfigurieren, um es mit Übersetzungs-Services von Drittanbietern zu integrieren.
* [Verbindung zum Microsoft Translator herstellen](/help/sites-administering/tc-msconf.md) – AEM bietet ein Testkonto für den Microsoft Translator.
