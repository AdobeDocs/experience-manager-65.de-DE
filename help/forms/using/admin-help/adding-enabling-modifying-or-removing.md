---
title: Endpunkte hinzufügen aktivieren, ändern oder entfernen
seo-title: Endpunkte hinzufügen aktivieren, ändern oder entfernen
description: Erfahren Sie, wie Sie Endpunkte hinzufügen, aktivieren, ändern und entfernen.
seo-description: Erfahren Sie, wie Sie Endpunkte hinzufügen, aktivieren, ändern und entfernen.
uuid: c53f225b-3d55-42f6-8982-0cd7dde0c4f5
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 7d0d4f96-fc72-4e2b-a2cc-5741b0a30f74
exl-id: b7461d5c-95d1-4da2-9d2a-f54c410a87f9
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 100%

---

# Endpunkte hinzufügen aktivieren, ändern oder entfernen {#adding-enabling-modifying-or-removing-endpoints}

## Einen Endpunkt zu einem Dienst hinzufügen {#add-an-endpoint-to-a-service}

Endpunkte können nur Diensten hinzugefügt werden. Ein Endpunkt kann nicht selbstständig bestehen bleiben, sondern muss einem Dienst zugeordnet werden.

>[!NOTE]
>
>Beim Hinzufügen von Endpunkten sollten Sie mit eindeutigen Namen arbeiten.

1. Klicken Sie in Administration Console auf „Dienste“ > „Anwendungen und Dienste“ > „Dienstverwaltung“.
1. Klicken Sie auf der Seite „Dienstverwaltung“ auf den zu konfigurierenden Dienst.
1. Wählen Sie auf der Registerkarte „Endpunkte“ in der Liste den hinzuzufügenden Endpunkttyp und klicken Sie auf „Hinzufügen“.
1. Je nach Endpunkttyp müssen weitere Endpunkteinstellungen konfiguriert werden.

[Einstellungen für Endpunkte des Typs „Überwachter Ordner“](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#watched-folder-endpoint-settings)

[E-Mail-Endpunkteinstellungen](/help/forms/using/admin-help/configuring-email-endpoints.md#email-endpoint-settings)

[Task Manager-Endpunkte konfigurieren](/help/forms/using/admin-help/configuring-task-manager-endpoints.md#configuring-task-manager-endpoints)

[Remoting-Endpunkteinstellungen](/help/forms/using/admin-help/configuring-remoting-endpoints.md#remoting-endpoint-settings)

1. Klicken Sie auf „Hinzufügen“.

## Endpunkt aktivieren oder deaktivieren {#enable-or-disable-an-endpoint}

Standardmäßig sind neue Endpunkte automatisch aktiviert. Wenn Sie aber einen Endpunkt deaktiviert haben, müssen Sie ihn aktivieren, damit er funktionsfähig ist.

Wenn mit Diensten Probleme auftreten, deaktivieren Sie die zugeordneten Endpunkte, um das Problem besser analysieren und beheben zu können. Es kann auch ratsam sein, Endpunkte während der normalen Systemwartung oder beim Aktualisieren eines Dienstes zu deaktivieren.

1. Klicken Sie in Administration Console auf „Dienste“ > „Anwendungen und Dienste“ > „Endpunktverwaltung“.
1. Aktivieren bzw. deaktivieren Sie auf der Seite „Endpunktverwaltung“ das Kontrollkästchen für den zu aktivierenden oder zu deaktivierenden Endpunkt und klicken Sie auf „Aktivieren“ oder „Deaktivieren“.

## Endpunkt ändern  {#modify-an-endpoint}

>[!NOTE]
>
>Die Änderungen, die Sie in Administration Console an einer Endpunktkonfiguration vornehmen, werden nicht in den Entwurfskopien Ihrer Anwendungen übernommen. Wenn Sie eine Anwendung erneut bereitstellen, gehen alle Änderungen, die Sie mithilfe von Administration Console an den Endpunkten vorgenommen haben, verloren.

1. Klicken Sie in Administration Console auf „Dienste“ > „Anwendungen und Dienste“ > „Endpunktverwaltung“.
1. Klicken Sie auf der Seite „Endpunktverwaltung“ auf den zu ändernden Endpunkt.
1. Ändern Sie auf der Seite „Endpunkt aktualisieren“ den Endpunktnamen, die Beschreibung und Einstellungen.

   >[!NOTE]
   >
   >Der Name und die Beschreibung dürfen kein &lt;-Zeichen enthalten, weil dadurch die Anzeige des Namens bzw. der Beschreibung in Workspace abgeschnitten wird.

1. Klicken Sie zum Speichern der vorgenommenen Änderungen auf „Aktualisieren“.

Diese Aufgabe kann auch auf der Seite „Dienstverwaltung“ durchgeführt werden, indem Sie einen Dienst auswählen und dann auf die Registerkarte „Endpunkte“ klicken.

## Endpunkt entfernen  {#remove-an-endpoint}

1. Klicken Sie in Administration Console auf „Dienste“ > „Anwendungen und Dienste“ > „Endpunktverwaltung“.
1. Aktivieren Sie auf der Seite „Endpunktverwaltung“ das Kontrollkästchen für den zu entfernenden Endpunkt und klicken Sie auf „Entfernen“. Der Endpunkt wird nicht mehr angezeigt.
