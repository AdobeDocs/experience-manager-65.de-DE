---
title: Verwalten der in Workspace angezeigten Kategorien
description: In Workspace werden die Prozesse, die Benutzende starten können, in Kategorien im linken Navigationsbereich angezeigt. Erfahren Sie, wie Sie diese in Workspace angezeigten Kategorien verwalten können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_workspace
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 62621fe9-f69f-4bc0-aecc-d7bcc3064516
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 100%
---
# Verwalten der in Workspace angezeigten Kategorien {#managing-the-categories-displayed-in-workspace}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

In Workspace werden die Prozesse, die Benutzende starten können, in Kategorien im linken Navigationsbereich angezeigt. Sie können die Kategorien in der Administrationskonsole einrichten oder beim Prozess-Design in Workbench einrichten lassen. Wenn beim Prozess-Design Prozesse erstellt werden, werden ihnen Kategorien zugewiesen.

Wenn Sie Kategorienamen angeben, erstellen Sie diese so, dass sie im Navigationsbereich von Workspace ordnungsgemäß angezeigt werden. Standardmäßig hat der linke Navigationsbereich eine feste Breite von 210 Pixel, was etwa 24 Zeichen entspricht. Wenn der von Ihnen angegebene Kategoriename zu lang ist, um in die feste Breite des linken Navigationsbereichs zu passen, wird er abgeschnitten. Der vollständige Name wird nur angezeigt, wenn der Mauszeiger darüber gehalten wird. Versuchen Sie, Kategorienamen zu vermeiden, die abgeschnitten werden. Die folgenden Beispiele veranschaulichen passende und abgeschnittene Kategorienamen:

**Passender Kategoriename für:** An- und Abwesenheit

**Abgeschnittener Kategoriename für:** An- und Abwesenheit (Vereinigte Staaten)

In Workspace werden Prozesse in einer Kategorie zumeist als Karten auf der Seite „Prozess starten“ angezeigt. Im Allgemeinen können auf dem Bildschirm für eine Kategorie sechs Karten angezeigt werden, bevor Benutzende scrollen müssen, um die verbleibenden Karten anzuzeigen. Da das Auffinden eines Prozesses durch Scrollen erschwert wird, begrenzen Sie ggf. jede Kategorie auf sechs Prozesse bzw. (abhängig von Ihrer Auflösung) auf die Anzahl von Prozessen, die ohne Scrollen auf dem Bildschirm angezeigt werden kann.

Wenn Sie MySQL als Ihre AEM Forms-Datenbank verwenden, kann die Administrationskonsole nicht zwischen zwei Kategorienamen unterscheiden, die sich nur in der Verwendung erweiterter Zeichen unterscheiden. Wenn Sie beispielsweise eine Kategorie namens „abcde“ und eine namens „âbcdè“ erstellen, werden diese Namen als identisch angesehen.

## Hinzufügen einer Kategorie {#add-a-category}

1. Wählen Sie in der Administrationskonsole „Dienste“ > „Anwendungen und Dienste“ > „Kategorieverwaltung“ aus.
1. Klicken Sie auf Hinzufügen. Wenn Sie eine Unterkategorie hinzufügen möchten, wählen Sie eine Kategorie aus und klicken Sie dann auf „Hinzufügen“.
1. Geben Sie im Feld „Name“ einen Namen und im Feld „Beschreibung“ eine Beschreibung der Kategorie ein.
1. Klicken Sie auf Hinzufügen. Die Kategorie wird auf der Seite „Kategorieverwaltung“ angezeigt.

   ***Hinweis **: Beim Erstellen von Kategorien können Sie nur bis zu fünf Hierarchieebenen hinzufügen.*

## Bearbeiten einer Kategorie {#edit-a-category}

1. Wählen Sie in der Administrationskonsole „Dienste“ > „Anwendungen und Dienste“ > „Kategorieverwaltung“ aus.
1. Wählen Sie die zu bearbeitende Kategorie aus und klicken Sie auf „Bearbeiten“. Alternativ können Sie auf eine Kategorie doppelklicken, um sie zu bearbeiten.
1. Bearbeiten Sie den Namen der Kategorie im Feld „Name“.

## Entfernen einer Kategorie {#remove-a-category}

Sie können nur nicht verwendete Kategorien entfernen.

1. Wählen Sie in der Administrationskonsole „Dienste“ > „Anwendungen und Dienste“ > „Kategorieverwaltung“ aus.
1. Aktivieren Sie auf der Seite „Kategorieverwaltung“ das Kontrollkästchen für die zu entfernende Kategorie und klicken Sie auf „Entfernen“. Die Kategorie wird nicht mehr angezeigt.
