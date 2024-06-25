---
title: Hinzufügen, Aktivieren, Ändern oder Entfernen von Endpunkten
description: Erfahren Sie, wie Sie Endpunkte hinzufügen, aktivieren, ändern und entfernen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: b7461d5c-95d1-4da2-9d2a-f54c410a87f9
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: ht
source-wordcount: '369'
ht-degree: 100%

---

# Hinzufügen, Aktivieren, Ändern oder Entfernen von Endpunkten {#adding-enabling-modifying-or-removing-endpoints}

## Hinzufügen eines Endpunkts zu einem Dienst {#add-an-endpoint-to-a-service}

Endpunkte können nur zu Diensten hinzugefügt werden. Ein Endpunkt kann nicht selbstständig bestehen bleiben, sondern muss einem Dienst zugeordnet werden.

>[!NOTE]
>
>Beim Hinzufügen von Endpunkten sollten Sie mit eindeutigen Namen arbeiten.

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Anwendungen und Dienste“ > „Dienstverwaltung“.
1. Klicken Sie auf der Seite „Dienstverwaltung“ auf den zu konfigurierenden Dienst.
1. Wählen Sie in der Liste auf der Registerkarte „Endpunkte“ den hinzuzufügenden Endpunkttyp aus und klicken Sie auf „Hinzufügen“.
1. Je nach Endpunkttyp müssen weitere Endpunkteinstellungen konfiguriert werden.

[Einstellungen für Endpunkte des Typs „Überwachter Ordner“](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#watched-folder-endpoint-settings)

[E-Mail-Endpunkteinstellungen](/help/forms/using/admin-help/configuring-email-endpoints.md#email-endpoint-settings)

[Task Manager-Endpunkte konfigurieren](/help/forms/using/admin-help/configuring-task-manager-endpoints.md#configuring-task-manager-endpoints)

[Remoting-Endpunkteinstellungen](/help/forms/using/admin-help/configuring-remoting-endpoints.md#remoting-endpoint-settings)

1. Klicken Sie auf Hinzufügen.

## Aktivieren oder Deaktivieren eines Endpunkts {#enable-or-disable-an-endpoint}

Standardmäßig sind neue Endpunkte automatisch aktiviert. Wenn Sie aber einen Endpunkt deaktiviert haben, müssen Sie ihn aktivieren, damit er verwendet werden kann.

Wenn mit Diensten Probleme auftreten, deaktivieren Sie die zugeordneten Endpunkte, um das Problem besser analysieren und beheben zu können. Es kann auch ratsam sein, Endpunkte während der normalen Systemwartung oder beim Upgrade eines Dienstes zu deaktivieren.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Anwendungen und Dienste“ > „Endpunktverwaltung“.
1. Aktivieren bzw. deaktivieren Sie auf der Seite „Endpunktverwaltung“ das Kontrollkästchen für den zu aktivierenden oder zu deaktivierenden Endpunkt und klicken Sie auf „Aktivieren“ oder „Deaktivieren“.

## Ändern eines Endpunkts {#modify-an-endpoint}

>[!NOTE]
>
>Die Änderungen, die Sie in der Administrationskonsole an einer Endpunktkonfiguration vornehmen, werden nicht in die Entwurfskopien Ihrer Anwendungen übernommen. Wenn Sie eine Anwendung erneut bereitstellen, gehen alle Änderungen verloren, die Sie mithilfe der Administrationskonsole an den zugehörigen Endpunkten vorgenommen haben.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Anwendungen und Dienste“ > „Endpunktverwaltung“.
1. Klicken Sie auf der Seite „Endpunktverwaltung“ auf den zu ändernden Endpunkt.
1. Ändern Sie auf der Seite „Endpunkt aktualisieren“ den Namen, die Beschreibung und die Einstellungen für den Endpunkt.

   >[!NOTE]
   >
   >Der Name und die Beschreibung dürfen kein Kleiner-als-Zeichen (&lt;) enthalten, weil dadurch die Anzeige des Namens bzw. der Beschreibung in Workspace abgeschnitten würde.

1. Klicken Sie auf „Aktualisieren“, um die vorgenommenen Änderungen zu speichern.

Dieser Vorgang kann auch auf der Seite „Dienstverwaltung“ durchgeführt werden, indem Sie einen Dienst auswählen und dann auf die Registerkarte „Endpunkte“ klicken.

## Entfernen eines Endpunkts {#remove-an-endpoint}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Anwendungen und Dienste“ > „Endpunktverwaltung“.
1. Aktivieren Sie auf der Seite „Endpunktverwaltung“ das Kontrollkästchen für den zu entfernenden Endpunkt und klicken Sie auf „Entfernen“. Der Endpunkt wird nicht mehr angezeigt.
