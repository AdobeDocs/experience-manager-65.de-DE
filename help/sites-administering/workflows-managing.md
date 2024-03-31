---
title: Verwalten des Zugriffs auf Workflows
description: Erfahren Sie, wie ACLs entsprechend den Benutzerkonten konfiguriert werden, um den Start von und die Teilnahme an Workflows zu aktivieren (oder zu deaktivieren).
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
exl-id: cc54d637-d66c-49d2-99ee-00d96f1a74e0
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 100%

---

# Verwalten des Zugriffs auf Workflows{#managing-access-to-workflows}

Konfigurieren Sie ACLs entsprechend den Benutzerkonten, um den Start von und die Teilnahme an Workflows zu aktivieren (oder zu deaktivieren).

## Erforderliche Benutzerberechtigungen für Workflows {#required-user-permissions-for-workflows}

Aktionen für Workflows können durchgeführt werden, wenn:

* Sie mit dem `admin`-Konto arbeiten;
* das Konto der Standardgruppe `workflow-users` zugewiesen wurde:

   * Diese Gruppe verfügt über alle Berechtigungen, die für die Benutzenden zur Ausführung von Workflow-Aktionen erforderlich sind.
   * Wenn sich das Konto in dieser Gruppe befindet, hat es nur Zugriff auf von ihm initiierte Workflows.

* das Konto der Standardgruppe `workflow-administrators` zugewiesen wurde:

   * Diese Gruppe verfügt über alle Berechtigungen, die von den berechtigten Benutzenden zur Überwachung und Verwaltung von Workflows erforderlich sind.
   * wenn sich das Konto in dieser Gruppe befindet, hat es Zugriff auf alle Workflows.

>[!NOTE]
>
>Dies sind die Mindestanforderungen. Ihr Konto muss zudem der zugewiesene Teilnehmer oder ein Mitglied der zugewiesenen Gruppe sein, um bestimmte Schritte ausführen zu können.

## Konfigurieren des Zugriffs auf Workflows {#configuring-access-to-workflows}

Workflow-Modelle übernehmen (erben) die Standard-Zugriffssteuerungsliste (ACL, Access Control List), um zu steuern, wie Benutzende mit Workflows interagieren können. Zum Anpassen des Benutzerzugriffs auf einen Workflow bearbeiten Sie die Zugriffssteuerungsliste (ACL) im Repository für den Ordner, der den Knoten des Workflow-Modells enthält:

* [Anwenden einer ACL für das spezifische Workflow-Modell unter /var/workflow/models](/help/sites-administering/workflows-managing.md#apply-an-acl-for-the-specific-workflow-model-to-var-workflow-models)
* [Erstellen eines Unterordners in /var/workflow/models und Anwenden der ACL auf diesen Ordner](/help/sites-administering/workflows-managing.md#create-a-subfolder-in-var-workflow-models-and-apply-the-acl-to-that)

>[!NOTE]
>
>Informationen zur Verwendung von CRXDE Lite zum Konfigurieren von ACLs finden Sie unter [Verwaltung von Zugriffsrechten](/help/sites-administering/user-group-ac-admin.md#access-right-management).

### Anwenden einer ACL für das spezifische Workflow-Modell unter /var/workflow/models {#apply-an-acl-for-the-specific-workflow-model-to-var-workflow-models}

Falls das Workflow-Modell unter `/var/workflow/models` gespeichert ist, können Sie dem folgenden Ordner eine spezifische ACL zuweisen, die nur für diesen Workflow relevant ist:

1. Öffnen Sie CRXDE Lite in Ihrem Webbrowser, z. B. [https://localhost:4502/crx/de](http://localhost:4502/crx/de)
1. Wählen Sie in der Knotenstruktur den Knoten für den Ordner der Workflow-Modelle aus:

   `/var/workflow/models`

1. Klicken Sie auf die Registerkarte **Zugriffssteuerung**.
1. Klicken Sie in der Tabelle **Richtlinien zur lokalen Zugriffssteuerung** (**Zugriffssteuerungsliste**) auf das Plussymbol, um einen **Eintrag hinzuzufügen**.
1. Fügen Sie im Dialogfeld **Neuen Eintrag hinzufügen** ein ACE mit den folgenden Eigenschaften hinzu:

   * **Prinzipal**: `content-authors`
   * **Typ**: `Deny`
   * **Berechtigungen**: `jcr:read`
   * **rep:glob**: Verweis auf den spezifischen Workflow

   ![wf-108](assets/wf-108.png)

   Die Tabelle **Zugriffssteuerungsliste** beinhaltet nun die Beschränkung für `content-authors` im Workflow-Modell `prototype-wfm-01`.

   ![wf-109](assets/wf-109.png)

1. Klicken Sie auf **Alle speichern**.

   Der Workflow `prototype-wfm-01` ist nicht länger für Mitglieder der Gruppe `content-authors` verfügbar.

### Erstellen eines Unterordners in /var/workflow/models und Anwenden der ACL auf diesen Ordner {#create-a-subfolder-in-var-workflow-models-and-apply-the-acl-to-that}

Ihr [Entwicklungs-Team kann die Workflows erstellen in einem Unterordner](/help/sites-developing/workflows-models.md#creating-a-new-workflow) von

`/var/workflow/models`

Vergleichbar mit den DAM-Workflows, die im folgenden Ordner gespeichert sind:

`/var/workflow/models/dam/`

Sie können dann dem Ordner selbst eine ACL hinzufügen.

1. Öffnen Sie CRXDE Lite im Webbrowser (z. B.[http://localhost:4502/crx/de](http://localhost:4502/crx/de)).
1. Wählen Sie in der Knotenstruktur den Knoten für den einzelnen Ordner im Ordner für die Workflow-Modelle aus. Beispiel:

   `/var/workflow/models/prototypes`

1. Klicken Sie auf die Registerkarte **Zugriffssteuerung**.
1. Klicken Sie in der Tabelle **Gültige Richtlinie für die Zugriffssteuerung** auf das Pluszeichen, um einen Eintrag **hinzuzufügen**.
1. Klicken Sie in der Tabelle **Richtlinien zur lokalen Zugriffssteuerung** (**Zugriffssteuerungsliste**) auf das Plussymbol, um einen **Eintrag hinzuzufügen**.
1. Fügen Sie im Dialogfeld **Neuen Eintrag hinzufügen** ein ACE mit den folgenden Eigenschaften hinzu:

   * **Prinzipal**: `content-authors`
   * **Typ**: `Deny`
   * **Berechtigungen**: `jcr:read`

   >[!NOTE]
   >
   >Wie im Abschnitt [Anwenden einer ACL für das spezifische Workflow-Modell unter /var/workflow/models](/help/sites-administering/workflows-managing.md#apply-an-acl-for-the-specific-workflow-model-to-var-workflow-models) können Sie ein „rep:glob“ einfügen, um den Zugriff auf einen spezifischen Workflow zu beschränken.

   ![wf-110](assets/wf-110.png)

   Die Tabelle **Zugriffssteuerungsliste** beinhaltet nun die Beschränkung für `content-authors` im Ordner `prototypes`.

   ![wf-111](assets/wf-111.png)

1. Klicken Sie auf **Alle speichern**.

   Die Modelle im `prototypes`-Ordner sind nicht länger für Mitglieder der Gruppe `content-authors` verfügbar.
