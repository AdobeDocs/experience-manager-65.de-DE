---
title: Anmerkungen beim Bearbeiten einer Seite
description: Oft muss das Hinzufügen von Inhalten zu den Seiten Ihrer Website vor der tatsächlichen Veröffentlichung besprochen werden. Zur Erleichterung dieses Vorgangs können Sie in vielen Komponenten, die in direkter Verbindung mit dem Inhalt stehen, Anmerkungen hinzufügen.
page-status-flag: de-activated
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
exl-id: d60e9601-d15b-4378-a33e-e90961f63195
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 100%

---

# Anmerkungen beim Bearbeiten einer Seite{#annotations-when-editing-a-page}

Oft muss das Hinzufügen von Inhalten zu den Seiten Ihrer Website vor der tatsächlichen Veröffentlichung besprochen werden. Um diesen Vorgang zu erleichtern, können Sie in vielen Komponenten, die direkt mit dem Inhalt (und nicht mit dem Layout) in Verbindung stehen, Anmerkungen hinzufügen.

Bei einer Anmerkung wird eine farbige Markierung/Haftnotiz auf der Seite platziert. Mit einer Anmerkung können Sie (oder andere Benutzer) Kommentare und/oder Fragen für andere Autoren/Prüfer hinterlassen.

>[!NOTE]
>
>Die Definition einer einzelnen Komponente bestimmt, ob Anmerkungen in Instanzen dieser Komponente möglich sind oder nicht.

>[!NOTE]
>
>In der klassischen Benutzeroberfläche erstellte Anmerkungen werden in der Touch-optimierten Benutzeroberfläche angezeigt. Skizzen sind jedoch benutzeroberflächenspezifisch und werden nur in der Benutzeroberfläche angezeigt, in der sie erstellt wurden.

>[!CAUTION]
>
>Durch Löschen einer Ressource (z. B. eines Absatzes) werden alle Anmerkungen und Skizzen gelöscht, die mit dieser Ressource verbunden sind (unabhängig von ihrer Position auf der Seite als Ganzes).

>[!NOTE]
>
>Je nach Ihren Anforderungen können Sie auch einen Workflow erstellen, damit Benachrichtigungen gesendet werden, wenn Anmerkungen hinzugefügt, aktualisiert oder gelöscht werden.

## Anmerkungen {#annotations}

Je nach Absatzdesign sind Anmerkungen entweder als Option im Kontextmenü (in der Regel über die rechte Maustaste, wenn sich der Absatz über dem gewünschten Absatz befindet) oder als Schaltfläche in der Absatzbearbeitungsleiste verfügbar.

Wählen Sie in beiden Fällen **Anmerken** aus. Daraufhin wird ein farbiger Notizzettel im Absatz platziert. Sie befinden sich sofort im Bearbeitungsmodus und können Text direkt hinzufügen:

![chlimage_1-137](assets/chlimage_1-137.png)

Sie können die Anmerkung an eine neue Position auf der Seite verschieben. Klicken Sie auf den oberen Rahmenbereich und ziehen Sie bei gedrückter Maustaste die Anmerkung an die neue Position. Dies kann überall auf der Seite sein. Es ist jedoch häufig sinnvoll, wenn sie in irgendeiner Weise mit dem Absatz verbunden bleibt.

Anmerkungen (einschließlich zugehöriger Skizzen) sind auch in allen Kopier-, Ausschneide- oder Löschaktionen enthalten, die für den Absatz durchgeführt werden, dem sie zugeordnet sind. Bei Kopier- oder Ausschneideaktionen bleibt die Position der Anmerkung (und der zugehörigen Skizzen) in Bezug auf den ursprünglichen Absatz erhalten.

Die Anmerkung kann auch durch Ziehen der unteren rechten Ecke vergrößert oder verkleinert werden.

Zum Nachverfolgen werden in der Fußzeile die Person, die die Anmerkung erstellt hat, sowie das Datum angegeben. Nachfolgende Autorinnen und Autoren können dieselbe Anmerkung bearbeiten (die Fußzeile wird dann aktualisiert) oder eine neue Anmerkung für denselben Absatz erstellen.

Wenn Sie die Anmerkung löschen möchten, müssen Sie den Vorgang bestätigen (durch Löschen einer Anmerkung werden auch alle mit dieser Anmerkung verbundenen Skizzen gelöscht).

Über die drei Symbole oben links können Sie die Anmerkung (zusammen mit allen damit verbundenen Skizzen) minimieren, die Farbe ändern bzw. Skizzen hinzufügen.

>[!NOTE]
>
>Anmerkungen sind nur im Bearbeitungsmodus der Autorenumgebung sichtbar.
>
>In einer Veröffentlichungsumgebung oder im Vorschau- oder Designmodus einer Autorenumgebung sind sie nicht sichtbar.

>[!NOTE]
>
>Anmerkungen können nicht zu einer Seite hinzugefügt werden, die von einer anderen Benutzerin oder einem anderen Benutzer gesperrt wurde.

## Anmerkungszeichnungen {#annotation-sketches}

>[!NOTE]
>
>Zeichnungen sind im Internet Explorer nicht verfügbar, daher:
>
>* wird das Symbol nicht angezeigt
>* vorhandene Skizzen, die in einem anderen Browser erstellt wurden, werden nicht angezeigt.
>

Skizzen sind eine Funktion von Anmerkungen, über die Sie einfache Liniengrafiken an beliebiger Stelle im Browser-Fenster (sichtbaren Bereich) erstellen können:

![chlimage_1-138](assets/chlimage_1-138.png)

* Wenn Sie sich im Skizzenmodus befinden, wird der Cursor in ein Kreuz geändert. Sie können mehrere separate Linien zeichnen.
* Die Zeichnungslinie spiegelt die Anmerkungsfarbe wider und kann entweder sein:

   * Freihand

     der Standardmodus; Beenden, indem Sie die Maustaste loslassen.

   * gerade:

     Halten Sie die `ALT`-Taste gedrückt, und klicken Sie auf die Start- und Endpunkte; schließen Sie den Vorgang mit einem Doppelklick ab.

* Wenn Sie den Skizzenmodus verlassen haben, können Sie auf eine Skizzenlinie klicken, um diese Skizze auszuwählen.
* Verschieben Sie eine Zeichnung, indem Sie die Zeichnung auswählen und sie dann an die gewünschte Position ziehen.
* Eine Zeichnung überlagert den Inhalt. Das bedeutet, dass Sie innerhalb der vier Ecken der Skizze nicht auf den zugrunde liegenden Absatz klicken können, z. B. wenn Sie einen Link bearbeiten oder aufrufen müssen. Wenn dies ein Problem darstellt (z. B. weil eine Skizze einen großen Bereich der Seite umfasst), minimieren Sie die entsprechende Anmerkung, da dadurch auch alle zugehörigen Skizzen minimiert werden, sodass Sie Zugriff auf den zugrunde liegenden Bereich erhalten.
* So löschen Sie eine einzelne Skizze: Wählen Sie die gewünschte Zeichnung aus und drücken Sie dann die **Löschen**-Taste (**fn**+**Rücktaste** auf einem Mac).

* Wenn Sie einen Absatz verschieben oder kopieren, werden auch alle zugehörigen Anmerkungen und deren Zeichnungen verschoben oder kopiert. Ihre Position in Bezug auf den Absatz bleibt unverändert.
* Wenn Sie eine Anmerkung löschen, werden auch alle Zeichnungen gelöscht, die mit dieser Anmerkung verbunden sind.
