---
title: Erste Schritte mit der AEM Headless-Übersetzung
description: Erfahren Sie, wie Sie Ihre Headless-Inhalte organisieren und wie AEM Übersetzungs-Tools funktionieren.
exl-id: 764f78a7-1d3d-4406-85b1-b80dffae2350
source-git-commit: 10b370fd8f855f71c6d7d791c272137bb5e04d97
workflow-type: tm+mt
source-wordcount: '1472'
ht-degree: 90%

---

# Erste Schritte mit der AEM Headless-Übersetzung {#getting-started}

Erfahren Sie, wie Sie Ihre Headless-Inhalte organisieren und wie AEM Übersetzungs-Tools funktionieren.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der AEM Headless-Übersetzungs-Tour, [Erfahren Sie mehr über Headless-Inhalte und über die Übersetzung in AEM](learn-about.md), haben Sie die Grundtheorie eines Headless-CMS kennengelernt und sollten jetzt:

* die grundlegenden Konzepte der Headless-Inhaltsbereitstellung verstehen,
* mit der Unterstützung von AEM für Headless und Übersetzung vertraut sein.

Dieser Artikel baut auf diesen Grundlagen auf, sodass Sie verstehen, wie AEM Headless-Inhalte speichert und verwaltet und wie Sie AEM-Übersetzungs-Tools verwenden können, um diese Inhalte zu übersetzen.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Sie mit der Übersetzung von Headless-Inhalten in AEM beginnen. Nach dem Lesen sollten Sie:

* die Bedeutung der Inhaltsstruktur für die Übersetzung verstehen.
* verstehen, wie AEM Headless-Inhalte speichert.
* mit den Übersetzungs-Tools von AEM vertraut sein.

## Anforderungen und Vorbedingungen {#requirements-prerequisites}

Es gibt mehrere Voraussetzungen, bevor Sie mit der Übersetzung Ihrer Headless AEM-Inhalte beginnen.

### Kenntnisse {#knowledge}

* Erfahrung mit der Übersetzung von Inhalten in einem CMS
* Erfahrung mit der Verwendung von grundlegenden Funktionen eines umfangreichen CMS
* Grundlegende Kenntnisse der Handhabung von AEM
* Verständnis des von Ihnen genutzten Übersetzungs-Service
* Ein grundlegendes Verständnis der zu übersetzenden Inhalte

>[!TIP]
>
>Wenn Sie nicht mit der Verwendung eines umfangreichen CMS wie AEM vertraut sind, sollten Sie die Dokumentation [Grundlegende Handhabung](/help/sites-authoring/basic-handling.md) lesen, bevor Sie fortfahren. Die Grundlegende Handling-Dokumentation ist nicht Teil des Journey, daher kehren Sie nach Abschluss zu dieser Seite zurück.

### Tools {#tools}

* Sandbox-Zugriff zum Testen der Übersetzung Ihrer Inhalte
* Anmeldedaten für die Verbindung mit Ihrem bevorzugten Übersetzungs-Service
* Mitglied der Gruppe `projects-administrators` in AEM

## Struktur ist entscheidend {#content-structure}

Inhalte in AEM, seien sie Headless- oder herkömmliche Webseiten, werden durch ihre Struktur gesteuert. AEM stellt nur wenige Anforderungen an die Inhaltsstruktur, doch kann eine sorgfältige Berücksichtigung Ihrer Inhaltshierarchie im Rahmen der Projektplanung die Übersetzung erheblich vereinfachen.

>[!TIP]
>
>Planen Sie die Übersetzung gleich zu Beginn des Headless-Projekts ein. Arbeiten Sie frühzeitig mit dem Projekt-Manager und den Inhaltsarchitekten zusammen.
>
>Es kann erforderlich sein, einen Internationalisierungs-Projekt-Manager als separate Rolle hinzuzuziehen, dessen Aufgabe es ist zu definieren, welche Inhalte übersetzt werden sollen und welche nicht und welche übersetzten Inhalte von regionalen oder lokalen Inhaltserstellern geändert werden können.

## Wie AEM Headless-Inhalte speichert {#headless-content-in-aem}

Für den Übersetzer ist es nicht wichtig, zu verstehen, wie AEM Headless-Inhalte verwaltet. Wenn Sie jedoch mit den grundlegenden Konzepten und der Terminologie vertraut sind, wird dies bei der späteren Verwendung der AEM-Übersetzungs-Tools hilfreich sein. Vor allem müssen Sie Ihre eigenen Inhalte verstehen und wissen, wie sie strukturiert sind, um sie effektiv zu übersetzen.

### Inhaltsmodelle {#content-models}

Damit Headless-Inhalte konsistent über verschiedene Kanäle, Regionen und Sprachen bereitgestellt werden können, müssen die Inhalte stark strukturiert sein. AEM verwendet Inhaltsmodelle, um diese Struktur zu erzwingen. Stellen Sie sich Inhaltsmodelle als eine Art Vorlage oder Muster für die Erstellung von Headless-Inhalten vor. Da jedes Projekt seine eigenen Anforderungen hat, definiert jedes Projekt seine eigenen Inhaltsfragmentmodelle. AEM hat keine festen Anforderungen oder Strukturen für solche Modelle.

Der Inhaltsarchitekt wird zu Beginn des Projekts aktiv, um diese Struktur zu definieren. Als Übersetzungsspezialist sollten Sie eng mit dem Inhaltsarchitekten zusammenarbeiten, um die Inhalte zu verstehen und zu organisieren.

>[!NOTE]
>
>Es liegt in der Verantwortung des Inhaltsarchitekten, die Inhaltsmodelle zu definieren. Der Übersetzungsspezialist sollte nur mit ihrer Struktur vertraut sein, wie in den folgenden Schritten beschrieben.

Da die Inhaltsmodelle die Struktur Ihrer Inhalte definieren, müssen Sie wissen, welche Felder Ihrer Modelle übersetzt werden müssen. Im Allgemeinen arbeiten Sie mit dem Inhaltsarchitekten zusammen, um dies zu definieren. Gehen Sie wie folgt vor, um die Felder Ihrer Inhaltsmodelle durchzugehen.

1. Navigieren Sie zu **Instrumente** > **Assets** > **Inhaltsfragmentmodelle**.
1. Inhaltsfragmentmodelle werden im Allgemeinen in einer Ordnerstruktur gespeichert. Klicken Sie auf den Ordner für Ihr Projekt.
1. Die Modelle werden aufgelistet. Klicken Sie auf das Modell, um die Details anzuzeigen.
   ![Inhaltsfragmentmodelle](assets/content-fragment-models.png)
1. Der **Inhaltsfragmentmodell-Editor** wird geöffnet.
   1. Die linke Spalte enthält die Felder des Modells. Diese Spalte interessiert uns.
   1. Die rechte Spalte enthält die Felder, die dem Modell hinzugefügt werden können. Diese Spalte können wir ignorieren.
      ![Inhaltsfragmentmodell-Editor](assets/content-fragment-model-editor.png)
1. Klicken Sie auf eines der Felder des Modells. AEM markiert es und die Details dieses Felds werden in der rechten Spalte angezeigt.
   ![Details des Inhaltsfragmentmodell-Editors](assets/content-fragment-model-editor-detail.png)

Notieren Sie sich den **Eigenschaftsnamen** des Feldes für alle Felder, die übersetzt werden müssen. Sie werden diese Informationen später in der Tour benötigen. Diese **Eigenschaftsnamen** sind erforderlich, um AEM zu informieren, welche Felder Ihrer Inhalte übersetzt werden müssen.

>[!TIP]
>
>Im Allgemeinen stellt der Inhaltsarchitekte dem Übersetzungsanbieter die **Eigenschaftsname** von allen für die Übersetzung erforderlichen Feldern. Diese Feldnamen werden für einen späteren Zeitpunkt in der Tour benötigt. Die vorangegangenen Schritte sind für das Verständnis des Übersetzungsspezialisten vorgesehen.

### Inhaltsfragmente {#content-fragments}

Inhaltsmodelle werden von den Inhaltsautoren verwendet, um die tatsächlichen Headless-Inhalte zu erstellen. Inhaltsautoren wählen das Modell aus, auf dem ihre Inhalte basieren sollen, und erstellen dann Inhaltsfragmente. Inhaltsfragmente sind Instanzen der Modelle und stellen tatsächliche Inhalte dar, die „Headless“ bereitgestellt werden.

Wenn die Inhaltsmodelle die Muster für die Inhalte sind, sind die Inhaltsfragmente die tatsächlichen Inhalte, die auf diesen Mustern basieren. Die Inhaltsfragmente stellen die Inhalte dar, die übersetzt werden müssen.

Inhaltsfragmente werden in AEM als Assets im Rahmen des Digital Asset Management (DAM) verwaltet. Dies ist wichtig, da sie sich alle unter dem Pfad `/content/dam` befinden.

## Empfohlene Inhaltsstruktur {#recommended-structure}

Arbeiten Sie wie zuvor empfohlen mit Ihrem Inhaltsarchitekten zusammen, um die geeignete Inhaltsstruktur für Ihr eigenes Projekt zu ermitteln. Das Folgende ist jedoch eine bewährte, einfache und intuitive Struktur, die sehr effektiv ist.

Definieren Sie unter `/content/dam` einen Basisordner für Ihr Projekt.

```text
/content/dam/<your-project>
```

Die Sprache, in der Ihre Inhalte erstellt werden, wird als Sprachstamm bezeichnet. In unserem Beispiel ist es Englisch und die Inhalte sollten unter diesem Pfad liegen.

```text
/content/dam/<your-project>/en
```

Alle Projektinhalte, die möglicherweise lokalisiert werden müssen, sollten unter dem Sprachstamm platziert werden.

```text
/content/dam/<your-project>/en/<your-project-content>
```

Übersetzungen sollten als gleichrangige Ordner neben dem Sprachstamm erstellt werden, wobei ihr Ordnername den ISO-2-Sprach-Code der Sprache darstellt. Beispielsweise hätte Deutsch den folgenden Pfad.

```text
/content/dam/<your-project>/de
```

>[!NOTE]
>
>Der Inhaltsarchitekt ist im Allgemeinen für die Erstellung dieser Sprachordner verantwortlich. Wenn sie nicht erstellt werden, können in AEM später keine Übersetzungsaufträge erstellt werden.

Die endgültige Struktur kann etwa wie folgt aussehen:

```text
/content
    |- dam
        |- your-project
            |- en
                |- some
                |- exciting
                |- headless
                |- content
            |- de
            |- fr
            |- it
            |- ...
        |- another-project
        |- ...
```

Notieren Sie sich den spezifischen Pfad Ihrer Inhalte, da er später zur Konfiguration Ihrer Übersetzung erforderlich ist.

>[!NOTE]
>
>In der Regel ist es Aufgabe des Inhaltsarchitekten, die Inhaltsstruktur zu definieren, er kann jedoch mit dem Übersetzungsspezialisten zusammenarbeiten.
>
>Sie wird hier der Vollständigkeit halber detailliert beschrieben.

## AEM-Übersetzungs-Tools {#translation-tools}

Nachdem Sie nun wissen, was Inhaltsfragmente sind und wie wichtig die Inhaltsstruktur ist, können wir uns ansehen, wie Sie diese Inhalte übersetzen können. Die Übersetzungs-Tools in AEM sind sehr leistungsstark, aber auf einer allgemeinen Ebene einfach zu verstehen.

* **Übersetzungs-Connector**: Der Connector ist die Verknüpfung zwischen AEM und dem von Ihnen verwendeten Übersetzungs-Service.
* **Übersetzungsregeln**: Regeln definieren, welche Inhalte unter bestimmten Pfaden übersetzt werden sollen.
* **Übersetzungsprojekte**: Übersetzungsprojekte sammeln Inhalte, die als einzelner Übersetzungsaufwand angesprochen werden sollten, und verfolgen den Fortschritt der Übersetzung. Sie stellen eine Verbindung mit dem Connector her, damit die zu übersetzenden Inhalte übertragen und vom Übersetzungsdienstleister zurückerhalten werden können.

Im Allgemeinen richten Sie pro Headless-Projekt nur einmal Ihren Connector für Ihre Instanz und die Regeln ein. Danach verwenden Sie Übersetzungsprojekte, um Ihre Inhalte zu übersetzen und die Übersetzungen laufend auf dem neuesten Stand zu halten.

## Wie geht es weiter {#what-is-next}

Nachdem Sie nun diesen Teil der Headless-Übersetzungs-Tour abgeschlossen haben, sollten Sie:

* die Bedeutung der Inhaltsstruktur für die Übersetzung verstehen.
* verstehen, wie AEM Headless-Inhalte speichert.
* mit den Übersetzungs-Tools von AEM vertraut sein.

Auf diesen Erkenntnissen aufbauen und Ihre Journey-zur Headless-AEM-Übersetzung fortsetzen, indem Sie das Dokument erneut überprüfen. [Übersetzungsintegration konfigurieren](configure-connector.md) Hier erfahren Sie, wie Sie AEM mit einem Übersetzungsdienst verbinden.|

## Zusätzliche Ressourcen {#additional-resources}

Es wird zwar empfohlen, zum nächsten Teil der Headless-Übersetzungs-Tour voranzuschreiten, indem Sie das Dokument [Konfigurieren des Übersetzungs-Connectors](configure-connector.md) lesen. Im Folgenden finden Sie einige zusätzliche optionale Ressourcen, die einige in diesem Dokument erwähnte Konzepte vertiefen. Sie sind jedoch nicht erforderlich, um mit der Headless-Tour fortzufahren.

* [Grundlegende Handhabung von AEM](/help/sites-authoring/basic-handling.md): Lernen Sie die Grundlagen der AEM-Benutzeroberfläche kennen, um bequem navigieren und wichtige Aufgaben wie das Auffinden von Inhalten ausführen zu können.
* [Ermitteln von zu übersetzenden Inhalten](/help/sites-administering/tc-rules.md): Erfahren Sie, wie Übersetzungsregeln Inhalte ermitteln, die übersetzt werden müssen.
* [Konfigurieren des Frameworks für die Übersetzungsintegration](/help/sites-administering/tc-tic.md): Erfahren Sie, wie Sie das Translation Integration Framework (TIF) für die Integration mit Übersetzungs-Services von Drittanbietern konfigurieren.
* [Verwalten von Übersetzungsprojekten](/help/sites-administering/tc-manage.md): Erfahren Sie, wie Sie sowohl maschinelle als auch menschliche Übersetzungsprojekte in AEM erstellen und verwalten.
* Ein [Einführung in AEM als Headless-CMS](/help/sites-developing/headless/introduction.md)
* Die [AEM Developer Portal](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=de)
* [Tutorials für Headless in AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=de)
