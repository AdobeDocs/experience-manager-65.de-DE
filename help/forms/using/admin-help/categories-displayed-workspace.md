---
title: Die in Workspace angezeigten Kategorien verwalten
seo-title: Die in Workspace angezeigten Kategorien verwalten
description: In Workspace werden die Prozesse, die ein Benutzer starten kann, in Kategorien im linken Navigationsbereich angezeigt. Erfahren Sie, wie Sie diese Kategorien verwalten können, die im Arbeitsbereich angezeigt werden.
seo-description: In Workspace werden die Prozesse, die ein Benutzer starten kann, in Kategorien im linken Navigationsbereich angezeigt. Erfahren Sie, wie Sie diese Kategorien verwalten können, die im Arbeitsbereich angezeigt werden.
uuid: c2a275f5-872e-467f-9f07-4b130631e8a8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_workspace
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 0d1536a2-10ac-4031-bd7f-264b02d0d75f
exl-id: 62621fe9-f69f-4bc0-aecc-d7bcc3064516
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 97%

---

# Die in Workspace angezeigten Kategorien verwalten {#managing-the-categories-displayed-in-workspace}

In Workspace werden die Prozesse, die ein Benutzer starten kann, in Kategorien im linken Navigationsbereich angezeigt. Sie können die Kategorien in Administration Console einrichten oder Prozessdesigner können sie in Workbench einrichten. Wenn Prozessdesigner Prozesse erstellen, weisen sie diesen Kategorien zu.

Beim Angeben von Kategorienamen müssen diese so erstellt werden, dass sie im Navigationsbereich von Workspace ordnungsgemäß angezeigt werden. Der linke Navigationsbereich hat standardmäßig eine feste Breite von 210 Pixel, was ca. 24 Zeichen entspricht. Wenn der von Ihnen angegebene Wert nicht in das Feld mit fester Länge im linken Navigationsbereich passt, wird er abgeschnitten. Der vollständige Name wird nur angezeigt, wenn Sie den Mauszeiger darüber positionieren. Versuchen Sie nach Möglichkeit, das Abschneiden von Kategorienamen zu vermeiden. Die folgenden Beispiele zeigen passende und abgeschnittene Kategorienamen:

**Passender Kategoriename:** Besuch und Urlaub

**Kategoriename, der abgeschnitten ist:** Besuch &amp; Urlaub (USA)

In Workspace werden Prozesse in einer Kategorie zumeist als Karten auf der Seite „Prozess starten“ angezeigt. Im Allgemeinen können auf dem Bildschirm für eine Kategorie sechs Karten angezeigt werden, bevor der Benutzer einen Bildlauf zum Anzeigen der restlichen Karten ausführen muss. Da das Auffinden eines Prozesses durch einen Bildlauf erschwert wird, begrenzen Sie ggf. jede Kategorie auf sechs Prozesse bzw. (abhängig von Ihrer Auflösung) auf die Anzahl von Prozessen, die ohne Bildlauf auf dem Bildschirm angezeigt werden kann.

Bei Verwendung von MySQL als AEM Forms-Datenbank kann Administration Console nicht zwischen zwei Kategorienamen unterscheiden, die sich nur in der Verwendung erweiterter Zeichen unterscheiden. Wenn Sie beispielsweise eine Kategorie namens „abcde“ und eine namens „âbcdè“ erstellen, werden diese Namen als identisch angesehen.

## Eine Kategorie hinzufügen {#add-a-category}

1. Wählen Sie in Administration Console „Dienste“ > „Anwendungen und Dienste“ > „Dienstverwaltung“.
1. Klicken Sie auf Hinzufügen. Wenn Sie eine Unterkategorie hinzufügen möchten, wählen Sie ein Kategorie und klicken Sie dann auf „Hinzufügen“.
1. Geben Sie im Feld „Name“ einen Namen und im Feld „Beschreibung“ eine Beschreibung der Kategorie ein.
1. Klicken Sie auf Hinzufügen. Die Kategorie wird auf der Seite Kategorieverwaltung angezeigt.

   ***Hinweis **: Beim Erstellen von Kategorien können Sie nur bis zu fünf Hierarchieebenen hinzufügen.*

## Kategorie bearbeiten {#edit-a-category}

1. Wählen Sie in Administration Console „Dienste“ > „Anwendungen und Dienste“ > „Dienstverwaltung“.
1. Wählen Sie die zu bearbeitende Kategorie aus und klicken Sie auf „Bearbeiten“. Als Alternative können Sie auf eine Kategorie doppelklicken.
1. Bearbeiten Sie den Namen der Kategorie im Feld „Name“.

## Eine Kategorie entfernen  {#remove-a-category}

Sie können nur nicht verwendete Kategorien entfernen.

1. Wählen Sie in Administration Console „Dienste“ > „Anwendungen und Dienste“ > „Dienstverwaltung“.
1. Aktivieren Sie auf der Seite „Kategorieverwaltung“ das Kontrollkästchen für die zu entfernende Kategorie und klicken Sie auf „Entfernen“. Die Kategorie wird nicht mehr angezeigt.
