---
title: Verwalten der in Workspace angezeigten Kategorien
description: In Workspace werden die Prozesse, die ein Benutzer starten kann, in Kategorien im linken Navigationsbereich angezeigt. Erfahren Sie, wie Sie diese in Workspace angezeigten Kategorien verwalten können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_workspace
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 62621fe9-f69f-4bc0-aecc-d7bcc3064516
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 9%

---

# Verwalten der in Workspace angezeigten Kategorien {#managing-the-categories-displayed-in-workspace}

In Workspace werden die Prozesse, die ein Benutzer starten kann, in Kategorien im linken Navigationsbereich angezeigt. Sie können die Kategorien in Administration Console einrichten oder Prozessentwickler können sie in Workbench einrichten. Wenn Prozessentwickler Prozesse erstellen, weisen sie sie Kategorien zu.

Wenn Sie Kategorienamen angeben, erstellen Sie diese so, dass sie im Navigationsbereich von Workspace ordnungsgemäß angezeigt werden. Standardmäßig hat der linke Navigationsbereich eine feste Breite von 210 Pixel, was etwa 24 Zeichen entspricht. Wenn der von Ihnen angegebene Kategoriename zu lang ist, um in die feste Breite des linken Navigationsbereichs zu passen, wird er abgeschnitten. Der vollständige Name wird nur angezeigt, wenn der Mauszeiger darüber angehalten wurde. Versuchen Sie, Kategorienamen zu vermeiden, die abgeschnitten werden. Die folgenden Beispiele veranschaulichen passende und abgeschnittene Kategorienamen:

**Passender Kategoriename für:** An- und Abwesenheit

**Abgeschnittener Kategoriename für:** An- und Abwesenheit (Vereinigte Staaten)

In Workspace werden Prozesse innerhalb einer Kategorie normalerweise als Karten auf der Seite &quot;Prozess starten&quot;angezeigt. Im Allgemeinen können auf dem Bildschirm für eine Kategorie sechs Karten angezeigt werden, bevor der Benutzer einen Bildlauf durchführen muss, um die verbleibenden Karten anzuzeigen. Da das Auffinden eines Prozesses durch Bildlauf erschwert wird, sollten Sie die einzelnen Kategorien auf sechs Prozesse beschränken oder, abhängig von Ihrer Auflösung, die Anzahl der Prozesse begrenzen, die auf dem Bildschirm angezeigt werden können, ohne dass ein Bildlauf erforderlich ist.

Wenn Sie MySQL als Ihre AEM Forms-Datenbank verwenden, kann Administration Console nicht zwischen zwei Kategorienamen unterscheiden, die sich nur in der Verwendung erweiterter Zeichen unterscheiden. Wenn Sie beispielsweise eine Kategorie mit dem Namen abcde und eine Kategorie mit dem Namen âbcdè erstellen, werden diese als identisch betrachtet.

## Kategorie hinzufügen {#add-a-category}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Anwendungen und Dienste&quot;> &quot;Kategorieverwaltung&quot;.
1. Klicken Sie auf Hinzufügen. Wenn Sie eine Unterkategorie hinzufügen möchten, wählen Sie eine Kategorie aus und klicken Sie auf Hinzufügen.
1. Geben Sie im Feld &quot;Name&quot;einen Namen für die Kategorie ein und im Feld &quot;Beschreibung&quot;eine Beschreibung der Kategorie.
1. Klicken Sie auf Hinzufügen. Die Kategorie wird auf der Seite Kategorieverwaltung angezeigt.

   ***Hinweis **: Beim Erstellen von Kategorien können Sie nur bis zu fünf Hierarchieebenen hinzufügen.*

## Bearbeiten von Kategorien {#edit-a-category}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Anwendungen und Dienste&quot;> &quot;Kategorieverwaltung&quot;.
1. Wählen Sie die zu bearbeitende Kategorie aus und klicken Sie auf Bearbeiten. Alternativ können Sie auf eine Kategorie doppelklicken, um sie zu bearbeiten.
1. Bearbeiten Sie den Namen der Kategorie im Feld &quot;Name&quot;.

## Kategorie entfernen {#remove-a-category}

Sie können nur die nicht verwendeten Kategorien entfernen.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Anwendungen und Dienste&quot;> &quot;Kategorieverwaltung&quot;.
1. Aktivieren Sie auf der Seite &quot;Kategorieverwaltung&quot;das Kontrollkästchen der zu entfernenden Kategorie und klicken Sie auf &quot;Entfernen&quot;. Die Kategorie wird nicht mehr angezeigt.
