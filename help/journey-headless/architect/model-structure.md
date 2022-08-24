---
title: Erfahren Sie mehr über das Erstellen von Inhaltsfragmentmodellen in AEM
description: Erfahren Sie mehr über die Konzepte und Methoden der Modellierung von Inhalten für Ihr Headless-CMS mithilfe von Inhaltsfragmentmodellen.
exl-id: b377e01f-e392-4ef5-a259-73ce9ff941d0
source-git-commit: ed11891c27910154df1bfec6225aecd8a9245bff
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 100%

---

# Erfahren Sie mehr über das Erstellen von Inhaltsfragmentmodellen in AEM {#architect-headless-content-fragment-models}

## Die bisherige Entwicklung {#story-so-far}

Am Anfang der [AEM Headless-Inhaltsautoren-Tour](overview.md) wurden in den [Grundlagen der Inhaltsmodellierung für Headless mit AEM](basics.md) die grundlegenden Konzepte und die Terminologie behandelt, die für das Authoring für Headless relevant sind.

Dieser Artikel baut auf diesen auf, damit Sie verstehen, wie Sie Ihre eigenen Inhaltsfragmentmodelle für Ihr AEM Headless-Projekt erstellen können.

## Ziel {#objective}

* **Zielgruppe**: Anfänger
* **Ziel**: Konzepte und Methoden zur Modellierung von Inhalten für Ihr Headless-CMS mithilfe von Inhaltsfragmentmodellen.

<!-- which persona does this? -->
<!-- and who allows the configuration on the folders? -->

<!--
## Enabling Content Fragment Models {#enabling-content-fragment-models}

At the very start you need to enable Content Fragment Models for your site, this is done in the Configuration Browser; under Tools -> General -> Configuration Browser. You can either select to configure the global entry, or create a new configuration. For example:

![Define configuration](/help/assets/content-fragments/assets/cfm-conf-01.png)

>[!NOTE]
>
>See Additional Resources - Content Fragments in the Configuration Browser
-->

## Erstellen von Inhaltsfragmentmodellen {#creating-content-fragment-models}

Anschließend können die Inhaltsfragmentmodelle erstellt und die Struktur definiert werden. Dies kann unter „Tools“ > „Assets“ > „Inhaltsfragmentmodelle“ erfolgen.

![Inhaltsfragmentmodelle in Tools](assets/cfm-tools.png)

Nachdem Sie diese Option ausgewählt haben, gehen Sie zum Speicherort für Ihr Modell und klicken Sie auf **Erstellen**. Hier können Sie verschiedene wichtige Details eingeben.

Die Option **Modell aktivieren** ist standardmäßig aktiviert. Das bedeutet, dass Ihr Modell zur Verwendung verfügbar ist (beim Erstellen von Inhaltsfragmenten), sobald Sie es gespeichert haben. Sie können dies bei Bedarf deaktivieren – es gibt auch später Möglichkeiten, ein vorhandenes Modell zu aktivieren (oder zu deaktivieren).

![Erstellen von Inhaltsfragmentmodellen](/help/assets/content-fragments/assets/cfm-models-02.png)

Bestätigen Sie mit **Erstellen** und Sie können Ihr Modell **Öffnen**, um mit der Definition der Struktur zu beginnen.

## Definieren von Inhaltsfragmentmodellen {#defining-content-fragment-models}

Wenn Sie ein neues Modell zum ersten Mal öffnen, sehen Sie einen großen leeren Bereich links und eine lange Liste von **Datentypen** rechts:

![Leeres Modell](/help/assets/content-fragments/assets/cfm-models-03.png)

Was ist also zu tun?

Sie können Instanzen der **Datentypen** auf den linken Bereich ziehen – Sie definieren bereits Ihr Modell!

![Felder definieren](/help/assets/content-fragments/assets/cfm-models-04.png)

Nachdem Sie einen Datentyp hinzugefügt haben, müssen Sie die **Eigenschaften** für dieses Feld definieren. Diese hängen vom verwendeten Typ ab. Beispiel:

![Dateneigenschaften](/help/assets/content-fragments/assets/cfm-models-05.png)

Sie können beliebig viele Felder hinzufügen. Beispiel:

![Inhaltsfragmentmodell](/help/assets/content-fragments/assets/cfm-models-07.png)

### Ihre Inhaltsautoren {#your-content-authors}

Ihre Inhaltsautoren sehen nicht die tatsächlichen Datentypen und -eigenschaften, die Sie zum Erstellen Ihrer Modelle verwendet haben. Dies bedeutet, dass Sie möglicherweise Hilfe und Informationen dazu bereitstellen müssen, wie bestimmte Felder ausgefüllt werden. Für grundlegende Informationen können Sie die Feldbeschriftung und den Standardwert verwenden. In komplexeren Fällen sollte jedoch eine projektspezifische Dokumentation in Betracht gezogen werden.

>[!NOTE]
>
>Siehe „Zusätzliche Ressourcen – Inhaltsfragmentmodelle“.

## Verwalten von Inhaltsfragmentmodellen {#managing-content-fragment-models}

<!-- needs more details -->

Die Verwaltung Ihrer Inhaltsfragmentmodelle umfasst Folgendes:

* Aktivieren (oder Deaktivieren) der Modelle – Dadurch werden sie für Autoren beim Erstellen von Inhaltsfragmenten verfügbar.
* Löschen – Eine Löschung kann immer erforderlich sein, aber Sie müssen sich bewusst sein, ob Sie ein Modell löschen, das bereits für Inhaltsfragmente verwendet wird, insbesondere für Fragmente, die bereits veröffentlicht wurden.

## Veröffentlichung {#publishing}

<!-- needs more details -->

Inhaltsfragmentmodelle müssen zeitgleich mit oder im Vorfeld der Veröffentlichung abhängiger Inhaltsfragmente veröffentlicht werden.

>[!NOTE]
>
>Wenn ein Autor versucht, Inhaltsfragmente zu veröffentlichen, deren Modell noch nicht veröffentlicht wurde, wird dies in der Auswahlliste angezeigt und das Modell wird mit dem Fragment veröffentlicht.

Sobald ein Modell veröffentlicht wird, wird es auf der Autoreninstanz in einen SCHREIBGESCHÜTZTEN Modus versetzt und *gesperrt*. Dadurch soll verhindert werden, dass Änderungen zu Fehlern an vorhandenen GraphQL-Schemas und -Abfragen führen, insbesondere in der Veröffentlichungsumgebung. Dies wird in der Konsole durch **Gesperrt** angezeigt.

Wenn das Modell **Gesperrt** ist (im schreibgeschützten Modus), können Sie den Inhalt und die Struktur der Modelle anzeigen, sie jedoch nicht direkt bearbeiten. Sie können **Gesperrte** Modelle aus der Konsole oder dem Modell-Editor heraus verwalten.

## Wie geht es weiter {#whats-next}

Nachdem Sie die Grundlagen gelernt haben, besteht der nächste Schritt darin, Ihre eigenen Inhaltsfragmentmodelle zu erstellen.

## Zusätzliche Ressourcen {#additional-resources}

* [Authoring – Konzepte](/help/sites-authoring/author.md)

* [Grundlegende Handhabung](/help/sites-authoring/basic-handling.md) – Diese Seite basiert hauptsächlich auf der **Sites**-Konsole, aber viele / die meisten Funktionen sind auch für die Navigation zu **Inhaltsfragmentmodellen** und deren Bearbeitung in der **Assets**-Konsole relevant.

* [Arbeiten mit Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md)

   * [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md)

      * [Definieren des Inhaltsfragmentmodells](/help/assets/content-fragments/content-fragments-models.md#defining-your-content-fragment-model)

      * [Aktivieren oder Deaktivieren von Inhaltsfragmentmodellen](/help/assets/content-fragments/content-fragments-models.md#enabling-disabling-a-content-fragment-model)

      * [Zulassen von Inhaltsfragmentmodellen im Asset-Ordner](/help/assets/content-fragments/content-fragments-models.md#allowing-content-fragment-models-assets-folder)

      * [Löschen eines Inhaltsfragmentmodells](/help/assets/content-fragments/content-fragments-models.md#deleting-a-content-fragment-model)

      * [Veröffentlichen eines Inhaltsfragmentmodells](/help/assets/content-fragments/content-fragments-models.md#publishing-a-content-fragment-model)

      * [Rückgängigmachen der Veröffentlichung eines Inhaltsfragmentmodells](/help/assets/content-fragments/content-fragments-models.md#unpublishing-a-content-fragment-model)

      * [Gesperrte (veröffentlichte) Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md#locked-published-content-fragment-models)

* Anleitungen für den Einstieg

   * [Schnellstartanleitung zum Erstellen von Inhaltsfragmentmodellen per Headless-Implementierung](/help/sites-developing/headless/getting-started/create-content-model.md)
