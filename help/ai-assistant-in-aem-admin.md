---
title: Konfigurieren des KI-Assistenten in AEM
description: Erfahren Sie, wie Sie den KI-Assistenten mithilfe der Admin Console in Adobe Experience Manager einrichten und konfigurieren.
solution: Experience Manager
feature: Authoring, AI Assistant, AI Tools
role: Admin, Developer, User
exl-id: 06824b3d-f912-4922-8fb6-ee2ca04c6326
autotag-review: '2026-05-18T18:35:37.980Z'
TQID: 'https://experienceleague.adobe.com/5YTQUJbJPlJuxToS6AVhJww1KQ20tuOlRoCVquyfSng'
product_v2:
  - id: e14eb250-3c22-4a07-9061-a78112b2b826
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: ac5ecfc1-cc78-4ecc-a90a-0362685062ce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: c7d04a2c-412a-4c9d-9d7a-4456eaa5adeb
source-git-commit: 9c96b6744c7af2f061b4dfbf403560047485f9b5
workflow-type: tm+mt
source-wordcount: 1202
ht-degree: 98%

---

# Konfigurieren des KI-Assistenten in AEM {#aem-ai-asst-admin-setup}

<!-- An Administrator must configure access, permissions, and settings before users in their organization can use the features in AI Assistant in AEM. -->

<!-- badge: label="Beta" type="Positive" -->

Um den KI-Assistenten in AEM (Adobe Experience Manager) zu verwenden, ist eine Berechtigung für den Zugriff auf Produktkenntnisse über den KI-Assistenten obligatorisch. Diese Berechtigung ist standardmäßig AKTIVIERT.

Wenn Sie steuern möchten, wer auf Produktkenntnisse zugreifen kann, senden Sie von der mit Ihrer Adobe ID verknüpften E-Mail-Adresse eine E-Mail an [aemaiassistant@adobe.com](mailto:aemaiassistant@adobe.com). Adobe kann die Zugriffssteuerung auf Benutzerebene aktivieren. Wenn die Option aktiviert ist, kann Ihr Admin mittels der unten beschriebenen Schritte Zugriff auf Benutzerebene gewähren.

Wenn Sie Zugriffskontrolle auf Benutzerebene angefordert haben, muss Ihre Organisation dies über die Adobe Admin Console aktivieren. Eine bzw. ein Produkt-Admin erstellt (oder wählt) eine Benutzergruppe und gewährt ihr die neue Berechtigung „KI-Assistent“. Jede Person, die dieser Gruppe hinzugefügt wird, erhält sofort Zugriff auf den KI-Assistenten in AEM. Wenn das Ziel unternehmensweite Verfügbarkeit ist, weist die bzw. der Admin einfach alle Benutzenden dieser Gruppe zu.

Aus Mitarbeitersicht ist der Prozess einfach: Bestimmen Sie den Produkt-Admin für Adobe Experience Manager in Ihrer Organisation und fordern Sie das Hinzufügen zur KI-fähigen Benutzergruppe an. Sobald Sie in dieser Gruppe angezeigt werden, erscheint automatisch das Assistentensymbol, wenn Sie sich das nächste Mal anmelden.

Admins sollten die normale Cloud Manager-Governance im Auge behalten. Mit Produktadministratorrechten in der Admin Console können Sie Profile erstellen, Benutzergruppen verwalten oder Berechtigungen bearbeiten. Wenn Benutzende auch die integrierte Funktion **Support-Ticket erstellen** des Assistenten benötigen, fügen Sie denselben Personen oder derselben Gruppe die standardmäßige Rolle **Support-Admin** (standardmäßige Admin Console-Rolle) hinzu.

Der Konfigurationsprozess des KI-Assistenten in AEM umfasst die folgenden Schritte:

1. [Erstellen Sie in der Adobe Admin Console ein neues Produktprofil](#create-profile).
1. [Aktivieren Sie die Berechtigung des KI-Assistenten für Produktkenntnisse](#enable-permission).
1. [Erstellen Sie eine neue Benutzergruppe (oder verwenden Sie eine vorhandene Benutzergruppe)](#create-user-group).
1. [Fügen Sie Benutzende zur Benutzergruppe hinzu](#add-users).
1. [Weisen Sie das Produktprofil der Benutzergruppe zu](#assign-product-profile).

**Voraussetzungen**

Bevor Sie beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:

* Sie müssen in der Adobe Admin Console zumindest über Produktadministratorrechte verfügen.
* Sie kennen sich mit der Benutzerverwaltungsstruktur Ihrer Organisation aus.

**Konfigurationsaspekte**

* Verarbeitungsdauer: Ressourcen, die in Cloud Manager erstellt werden, brauchen bis zu zwei Minuten, bis sie in der Admin Console zur Berechtigungskonfiguration angezeigt werden.
* Verschiedene Profile: Benutzende können verschiedenen Profilen angehören und Berechtigungen werden aus allen zugewiesenen Profilen kombiniert.
* Organisationsumfang: Manche Berechtigungen können auf Organisationsebene für alle Programme gelten.
* Vordefinierte Profile: Löschen Sie keine vordefinierten Berechtigungsprofile aus der Admin Console.


## &#x200B;1. Erstellen eines neuen Produktprofils in der Adobe Admin Console{#create-profile}

1. Befolgen Sie die detaillierten Anweisungen unter [Erstellen eines neuen Produktprofils in der Adobe Admin Console](https://experienceleague.adobe.com/de/docs/experience-platform/access-control/ui/create-profile), die Sie in der Dokumentation zu Experience Platform finden.

1. Beim Erstellen des neuen Produktprofils können Sie die folgenden empfohlenen Werte für den KI-Assistenten verwenden.

   | Textfeld | Vorgeschlagener Wert |
   | --- | --- |
   | Name des Produktprofils | `AI Assistant in AEM` (oder Ihr bevorzugter beschreibender Name) |
   | Anzeigename (optional) | `AI Assistant` |
   | Beschreibung (optional) | `Product profile for managing AI Assistant in AEM access` |
   | Benachrichtigung | Konfigurieren auf Grundlage der Präferenzen Ihrer Organisation |


## &#x200B;2. Aktivieren der Berechtigung des KI-Assistenten für Produktkenntnisse{#enable-permission}

Das Zuweisen benutzerdefinierter Berechtigungen zu Produktprofilen folgt dem standardmäßigen Workflow für benutzerdefinierte Berechtigungen in Adobe Cloud Manager.

Referenzartikel: [Zuweisen benutzerdefinierter Berechtigungen zu dem neuen Produktprofil](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-manager/content/requirements/custom-permissions#assign-permissions)

1. Klicken Sie in der Admin Console auf den Namen des neu erstellten Produktprofils (`AI Assistant in AEM`)

   ![Screenshot](/help/assets/assets-ai/ai-assistant-console.png)

1. Um die Liste der bearbeitbaren Berechtigungen anzuzeigen, klicken Sie auf die Registerkarte **Berechtigungen**.

1. Suchen Sie in der Tabellenliste die Berechtigung `AI Assistant Product Knowledge`.

   ![Registerkarte für Berechtigungen des KI-Assistenten in Admin Console](/help/assets/assets-ai/ai-assistant-permission.png)

1. Klicken Sie rechts neben dem Berechtigungsnamen auf  das ![Bleistiftsymbol oder Bearbeitungssymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg).

1. Aktivieren Sie auf der Seite **Berechtigungen für den KI-Assistenten bearbeiten** den Umschalter **KI-Assistent – Produktkenntnisse**.

   ![Seite „Berechtigungen bearbeiten“ für die Umschaltoption „KI-Assistent – Produktkenntnisse“](/help/assets/assets-ai/ai-assistant-prod-knowledge.png)

1. Klicken Sie in der rechten unteren Ecke der Seite auf **Speichern**.

   Für Ihr Produktprofil ist jetzt die Berechtigung „KI-Assistent – Produktkenntnisse“ aktiviert.


## &#x200B;3. Erstellen einer neuen Benutzergruppe (oder Verwenden einer vorhandenen Benutzergruppe){#create-user-group}

1. Führen Sie einen der folgenden Schritte aus:

>[!BEGINTABS]

>[!TAB Neue Benutzergruppe erstellen]

1. Navigieren Sie in der Admin Console zu **Benutzende** und dann zu **Benutzergruppen**.

   ![Benutzergruppen](/help/assets/assets-ai/ai-assistant-user-groups.png)

1. Klicken Sie auf der Seite **Benutzergruppen** auf **Neue Benutzergruppe**.

   ![Schaltfläche „Neue Benutzergruppe“ auf der Seite „Benutzergruppen“](/help/assets/assets-ai/ai-assistant-new-user-group.png)

1. Geben Sie auf der Seite **Neue Benutzergruppe erstellen** die folgenden Informationen ein:

   | Option | Vorgeschlagener Wert |
   | --- | --- |
   | Name der Benutzergruppe | `AI Assistant in AEM` (oder Ihr bevorzugter Name) |
   | Beschreibung (optional) | `User group for managing AI Assistant in AEM access` |

   ![&#x200B; Seite „Neue Benutzergruppe erstellen“](/help/assets/assets-ai/ai-assistant-create-new-user-group.png)

1. Klicken Sie unten rechts in der Seite auf **Speichern**.

>[!TAB Verwenden einer bestehenden Benutzergruppe]

Sie können eine bestehende AEM-Benutzergruppe nutzen, wenn sie die Zugriffsanforderungen für den KI-Assistenten erfüllt, anstatt eine neue Gruppe zu erstellen.

>[!ENDTABS]

## &#x200B;4. Hinzufügen von Benutzenden zu der Benutzergruppe{#add-users}

1. Führen Sie einen der folgenden Schritte aus:

>[!BEGINTABS]

>[!TAB Hinzufügen von einzelnen Benutzenden]

1. Klicken Sie auf der Seite **Benutzergruppen** in der Tabelle **Gruppenname** auf den Namen der neu erstellten Benutzergruppe oder auf den Namen einer vorhandenen Benutzergruppe.

   ![Seite „Benutzergruppen“ mit dem Benutzergruppennamen KI-Assistent in AEM in der Tabelle](/help/assets/assets-ai/ai-assistant-user-group-name-in-table.png)

1. Klicken Sie auf der Seite **Benutzergruppen** für den **KI-Assistenten in AEM** auf die Registerkarte **Benutzende** und dann auf **Benutzende hinzufügen**.

   ![KI-Assistent in der Seite &quot;AEM-Benutzergruppen“, auf der die Registerkarte „Benutzer“ und die Schaltfläche „Benutzer hinzufügen“ angezeigt werden](/help/assets/assets-ai/ai-assistant-add-users.png)

1. Suchen Sie auf der **`Add users to this user group`**-Seite nach Benutzenden, die Zugriff auf den KI-Assistenten in AEM benötigen, und wählen Sie sie aus.

   ![Seite „Benutzende zu dieser Benutzergruppe hinzufügen“](/help/assets/assets-ai/ai-assistant-add-users-to-this-group.png)

1. Klicken Sie in der rechten unteren Ecke der Seite auf **Speichern**.
1. Weisen Sie nun [das Produktprofil der Benutzergruppe zu](#assign-product-profile).

>[!TAB Mehrere Benutzer auf einmal hinzufügen]

Sie können die Funktion für den Massen-Upload in der Admin Console verwenden.

1. Bereiten Sie eine CSV-Datei mit Benutzerinformationen vor.
1. Verwenden Sie die Option **`Add users by CSV`** für eine effiziente Massenhinzufügung.
1. Weisen Sie nun [das Produktprofil der Benutzergruppe zu](#assign-product-profile).

>[!ENDTABS]


## &#x200B;5. Zuweisen des Produktprofils zur Benutzergruppe{#assign-product-profile}

Dieser Schritt folgt dem standardmäßigen Adobe Admin Console-Workflow für das Zuweisen von Produktprofilen zu Benutzergruppen.

Referenzartikel: [Verwalten von Produktprofilen für Enterprise-Benutzer](https://helpx.adobe.com/de/enterprise/using/manage-product-profiles.html)

1. Klicken Sie in Ihrer Benutzergruppe „KI-Assistent in AEM“ aus [4. Hinzufügen von Benutzenden zur Benutzergruppe](#add-users) auf die Registerkarte **Zugewiesene Produktprofile**.
1. Klicken Sie auf **Profil zuweisen**.

   ![Benutzergruppenseite „KI-Assistent in AEM“ mit ausgewählter Registerkarte „Zugewiesene Produktprofile“](/help/assets/assets-ai/ai-assistant-assign-profile.png)

1. Suchen Sie auf der Seite **Produkte und Profile zuweisen** im Dialogfeld **Produktprofile auswählen** nach dem Produktprofil Ihres **KI-Assistenten** und wählen Sie es aus.

   ![Seite „Produkte und Profile zuweisen“ mit angezeigtem Dialogfeld „Produktprofile auswählen“ und ausgewähltem Produktprofil „KI-Assistent“](/help/assets/assets-ai/ai-assistant-select-product-profile.png)

1. Klicken Sie unten rechts im Dialogfeld auf **Anwenden**.
1. Klicken Sie unten rechts auf der Seite **Produkte und Profile zuweisen** auf **Speichern**.

   ![Produktprofil des KI-Assistenten, angezeigt als der Benutzergruppe „KI-Assistent in AEM“ zugewiesen](/help/assets/assets-ai/ai-assistant-profile-assigned-to-user-group.png)


## Überprüfen der Konfiguration

* Vergewissern Sie sich, dass in Ihrem Produktprofil die richtige Anzahl zugewiesener Benutzergruppen angezeigt wird.
* Stellen Sie sicher, dass in der Benutzergruppe die richtige Anzahl von Benutzenden angezeigt wird.
* Vergewissern Sie sich, dass die Berechtigung „KI-Assistent – Produktkenntnisse“ aktiviert und ordnungsgemäß konfiguriert ist.


## Testen der Konfiguration

Bitten Sie einen Benutzenden aus der zugewiesenen Gruppe, Folgendes zu tun:

1. Melden Sie sich bei AEM an.
2. Überprüfen, ob die Funktionen des KI-Assistenten verfügbar sind.
3. Testen der Funktionalität des KI-Assistenten, um eine ordnungsgemäße Aktivierung sicherzustellen.

## Siehe auch

* [KI-Assistent in AEM](/help/ai-assistant-in-aem.md)
* [Zugriffssteuerung in Adobe Experience Platform](https://experienceleague.adobe.com/de/docs/experience-platform/access-control/ui/overview)
<!-- * [Cloud Manager Custom Permissions](/help/implementing/cloud-manager/custom-permissions.md) -->
