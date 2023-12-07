---
title: Hinzufügen, Aktivieren, Ändern oder Entfernen von Endpunkten
description: Erfahren Sie, wie Sie Endpunkte hinzufügen, aktivieren, ändern und entfernen können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: b7461d5c-95d1-4da2-9d2a-f54c410a87f9
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 10%

---

# Hinzufügen, Aktivieren, Ändern oder Entfernen von Endpunkten {#adding-enabling-modifying-or-removing-endpoints}

## Endpunkt zu einem Dienst hinzufügen {#add-an-endpoint-to-a-service}

Endpunkte können nur zu Diensten hinzugefügt werden. Ein Endpunkt kann nicht allein vorhanden sein. Er muss mit einem Dienst verknüpft sein.

>[!NOTE]
>
>Es wird empfohlen, beim Hinzufügen von Endpunkten eindeutige Namen zu verwenden.

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Anwendungen und Dienste“ > „Dienstverwaltung“.
1. Klicken Sie auf der Seite &quot;Dienstverwaltung&quot;auf den zu konfigurierenden Dienst.
1. Wählen Sie in der Liste auf der Registerkarte &quot;Endpunkte&quot;den Typ des hinzuzufügenden Endpunkts aus und klicken Sie auf &quot;Hinzufügen&quot;.
1. Konfigurieren Sie abhängig vom Endpunkttyp zusätzliche Endpunkteinstellungen.

[Einstellungen für Endpunkte des Typs „Überwachter Ordner“](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#watched-folder-endpoint-settings)

[E-Mail-Endpunkteinstellungen](/help/forms/using/admin-help/configuring-email-endpoints.md#email-endpoint-settings)

[Task Manager-Endpunkte konfigurieren](/help/forms/using/admin-help/configuring-task-manager-endpoints.md#configuring-task-manager-endpoints)

[Remoting-Endpunkteinstellungen](/help/forms/using/admin-help/configuring-remoting-endpoints.md#remoting-endpoint-settings)

1. Klicken Sie auf Hinzufügen.

## Endpunkt aktivieren oder deaktivieren {#enable-or-disable-an-endpoint}

Standardmäßig werden neue Endpunkte automatisch aktiviert. Wenn Sie einen Endpunkt deaktiviert haben, müssen Sie ihn aktivieren, damit er funktioniert.

Wenn Probleme mit Diensten auftreten, deaktivieren Sie die zugehörigen Endpunkte, um das Problem besser zu beheben. Sie können Endpunkte auch während der regulären Systemwartung oder beim Aktualisieren eines Dienstes deaktivieren.

1. Klicken Sie in Administration Console auf Dienste > Anwendungen und Dienste > Endpunktverwaltung.
1. Aktivieren Sie auf der Seite &quot;Endpunktverwaltung&quot;das Kontrollkästchen für den Endpunkt, der aktiviert oder deaktiviert werden soll, und klicken Sie auf &quot;Aktivieren&quot;oder &quot;Deaktivieren&quot;.

## Endpunkt ändern {#modify-an-endpoint}

>[!NOTE]
>
>Die Änderungen, die Sie mit Administration Console an einer Endpunktkonfiguration vornehmen, werden nicht in den Entwurfszeitkopien Ihrer Anwendungen übernommen. Wenn Sie eine Anwendung erneut bereitstellen, gehen alle Änderungen verloren, die Sie mithilfe von Administration Console an ihren Endpunkten vorgenommen haben.

1. Klicken Sie in Administration Console auf Dienste > Anwendungen und Dienste > Endpunktverwaltung.
1. Klicken Sie auf der Seite &quot;Endpunktverwaltung&quot;auf den zu ändernden Endpunkt.
1. Ändern Sie auf der Seite &quot;Endpunkt aktualisieren&quot;den Namen, die Beschreibung und die Einstellungen des Endpunkts.

   >[!NOTE]
   >
   >Der Name oder die Beschreibung darf kein &lt; -Zeichen enthalten, da dadurch der in Workspace angezeigte Name oder die Beschreibung abgeschnitten wird.

1. Klicken Sie zum Speichern der Änderungen auf Aktualisieren.

Sie können diese Aufgabe auch auf der Seite Dienstverwaltung durchführen, indem Sie einen Dienst auswählen und dann auf die Registerkarte Endpunkte klicken.

## Endpunkt entfernen {#remove-an-endpoint}

1. Klicken Sie in Administration Console auf Dienste > Anwendungen und Dienste > Endpunktverwaltung.
1. Aktivieren Sie auf der Seite &quot;Endpunktverwaltung&quot;das Kontrollkästchen für den zu entfernenden Endpunkt und klicken Sie auf &quot;Entfernen&quot;. Der Endpunkt wird nicht mehr angezeigt.
