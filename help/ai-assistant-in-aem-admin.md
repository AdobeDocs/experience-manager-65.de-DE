---
title: Konfigurieren des KI-Assistenten in AEM
description: Erfahren Sie, wie Sie den KI-Assistenten mithilfe der Admin Console in Adobe Experience Manager einrichten und konfigurieren.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 06824b3d-f912-4922-8fb6-ee2ca04c6326
source-git-commit: 1aa70fc14e41ce4dd76be206723e8a44856e8c09
workflow-type: tm+mt
source-wordcount: '1148'
ht-degree: 4%

---

# Konfigurieren des KI-Assistenten in AEM {#aem-ai-asst-admin-setup}

<!-- An Administrator must configure access, permissions, and settings before users in their organization can use the features in AI Assistant in AEM. -->

<!-- badge: label="Beta" type="Positive" -->

Um den KI-Assistenten in AEM (Adobe Experience Manager) zu verwenden, ist die Berechtigung für den Zugriff auf Produktkenntnisse über den KI-Assistenten obligatorisch. Diese Berechtigung ist standardmäßig aktiviert.

Wenn Sie steuern möchten, wer auf Produktkenntnisse zugreifen kann, senden Sie eine E-Mail an [aemaiassistant@adobe.com](mailto:aemaiassistant@adobe.com) von Ihrer mit Ihrer Adobe ID verknüpften E-Mail-Adresse. Adobe kann die Zugriffssteuerung auf Benutzerebene aktivieren. Wenn diese Option aktiviert ist, kann Ihr Administrator Zugriff auf Benutzerebene gewähren, indem er die unten beschriebenen Schritte ausführt.

Wenn Sie die Zugriffskontrolle auf Benutzerebene angefordert haben, muss sich Ihr Unternehmen über die Adobe Admin Console anmelden. Ein Produktadministrator erstellt (oder wählt) eine Benutzergruppe und gewährt ihr die neue Berechtigung „KI-Assistent“. Jeder, der dieser Gruppe hinzugefügt wird, erhält sofort Zugriff auf den KI-Assistenten in AEM. Wenn das Ziel die unternehmensweite Verfügbarkeit ist, weist der Administrator einfach alle Benutzer dieser Gruppe zu.

Aus Mitarbeitersicht ist der Prozess einfach: Bestimmen Sie den Produktadministrator für Adobe Experience Manager in Ihrem Unternehmen und fordern Sie die Hinzufügung zur KI-aktivierten Benutzergruppe an. Sobald Sie in dieser Gruppe angezeigt werden, wird das Assistentensymbol automatisch angezeigt, wenn Sie sich das nächste Mal anmelden.

Administratoren sollten die normale Cloud Manager-Governance im Auge behalten. Halten Sie Produktadministratorrechte in der Admin Console, um Profile zu erstellen, Benutzergruppen zu verwalten oder Berechtigungen zu bearbeiten. Wenn Benutzende auch die integrierte Funktion „Support-Ticket erstellen **des Assistenten benötigen** fügen Sie die standardmäßige Rolle **Support-Admin** (standardmäßige Admin Console-Rolle) denselben Personen oder derselben Gruppe hinzu.

Der Konfigurationsprozess des KI-Assistenten in AEM umfasst die folgenden Schritte:

1. [Erstellen eines neuen Produktprofils in der Adobe Admin Console](#create-profile).
1. [Berechtigung zum Aktivieren des KI-Assistenten für Produktkenntnisse](#enable-permission).
1. [Erstellen Sie eine neue Benutzergruppe (oder verwenden Sie eine vorhandene Benutzergruppe)](#create-user-group).
1. [Benutzer zur Benutzergruppe hinzufügen](#add-users).
1. [Weisen Sie das Produktprofil der Benutzergruppe zu](#assign-product-profile).

**Voraussetzungen**

Bevor Sie beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllt haben:

* Sie müssen zumindest über Produktadministratorrechte in der Adobe Admin Console verfügen.
* Sie verfügen über Kenntnisse der Benutzerverwaltungsstruktur Ihres Unternehmens.

**Überlegungen zur Konfiguration**

* Verarbeitungszeit: Es kann bis zu 2 Minuten dauern, bis in Cloud Manager erstellte Ressourcen zur Berechtigungskonfiguration in Admin Console angezeigt werden.
* Mehrere Profile: Benutzer können Teil mehrerer Profile sein und Berechtigungen werden aus allen zugewiesenen Profilen kombiniert.
* Organisationsbereich: Einige Berechtigungen können auf Organisationsebene für alle Programme gelten.
* Vordefinierte Profile: Löschen Sie keine vordefinierten Berechtigungsprofile aus der Admin Console.


## &#x200B;1. Erstellen eines neuen Produktprofils in der Adobe Admin Console{#create-profile}

1. Befolgen Sie die detaillierten Anweisungen unter [Erstellen eines neuen Produktprofils in der Adobe Admin Console](https://experienceleague.adobe.com/de/docs/experience-platform/access-control/ui/create-profile) in der Dokumentation zu Experience Platform.

1. Beim Erstellen des neuen Produktprofils können Sie die folgenden empfohlenen Werte für den KI-Assistenten verwenden.

   | Textfeld | Vorgeschlagener Wert |
   | --- | --- |
   | Produktprofilname | `AI Assistant in AEM` (oder Ihr bevorzugter beschreibender Name) |
   | Anzeigename (optional) | `AI Assistant` |
   | Beschreibung (optional) | `Product profile for managing AI Assistant in AEM access` |
   | Benachrichtigung | Konfigurieren auf Grundlage der Voreinstellungen Ihrer Organisation |


## &#x200B;2. KI-Assistenten für Produktkenntnisse aktivieren{#enable-permission}

Der Prozess zum Zuweisen benutzerdefinierter Berechtigungen zu Produktprofilen folgt dem standardmäßigen Workflow für benutzerdefinierte Berechtigungen in Adobe Cloud Manager.

Referenzartikel: [Zuweisen benutzerdefinierter Berechtigungen zum neuen Produktprofil](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-manager/content/requirements/custom-permissions#assign-permissions)

1. Klicken Sie in der Admin Console auf den Namen Ihres neu erstellten Produktprofils (`AI Assistant in AEM`)

   ![Screenshot](/help/assets/assets-ai/ai-assistant-console.png)

1. Um die Liste der bearbeitbaren Berechtigungen anzuzeigen, klicken Sie auf die Registerkarte **Berechtigungen** .

1. Suchen Sie in der Tabellenliste die Berechtigung `AI Assistant Product Knowledge` .

   ![Registerkarte „Berechtigungen für KI-Assistenten“ in Admin Console](/help/assets/assets-ai/ai-assistant-permission.png)

1. Klicken Sie rechts neben dem Berechtigungsnamen auf ![Bleistiftsymbol oder Bearbeitungssymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg).

1. Aktivieren Sie auf **Seite Berechtigungen für KI-** bearbeiten den Umschalter **KI-Assistent - Produktkenntnisse**.

   ![Seite „Berechtigungen bearbeiten“ für die Umschaltoption KI-Assistent für Produktkenntnisse](/help/assets/assets-ai/ai-assistant-prod-knowledge.png)

1. Klicken Sie unten rechts auf der Seite auf **Speichern**.

   Für Ihr Produktprofil ist jetzt die Berechtigung KI-Assistent für Produktkenntnisse aktiviert.


## &#x200B;3. Erstellen Sie eine neue Benutzergruppe (oder verwenden Sie eine vorhandene Benutzergruppe).{#create-user-group}

1. Führen Sie einen der folgenden Schritte aus:

>[!BEGINTABS]

>[!TAB Erstellen Sie eine neue Benutzergruppe]

1. Klicken Sie in der Admin Console auf **Benutzer** > **Benutzergruppen**.

   ![Benutzergruppen](/help/assets/assets-ai/ai-assistant-user-groups.png)

1. Klicken Sie auf **Seite** Benutzergruppen **auf „Neue Benutzergruppe**.

   ![Schaltfläche „Neue Benutzergruppe“ auf der Seite „Benutzergruppen“](/help/assets/assets-ai/ai-assistant-new-user-group.png)

1. Geben **auf der Seite „Neue Benutzergruppe erstellen** die folgenden Informationen ein:

   | Option | Vorgeschlagener Wert |
   | --- | --- |
   | Name der Benutzergruppe | `AI Assistant in AEM` (oder der bevorzugte Name) |
   | Beschreibung (optional) | `User group for managing AI Assistant in AEM access` |

   ![Erstellen Sie eine neue Benutzergruppenseite](/help/assets/assets-ai/ai-assistant-create-new-user-group.png)

1. Klicken Sie unten rechts auf der Seite auf **Speichern**.

>[!TAB Vorhandene Benutzergruppe verwenden]

Sie können eine bestehende AEM-Benutzergruppe verwenden, wenn sie die Zugriffsanforderungen für den KI-Assistenten erfüllt, anstatt eine neue Gruppe zu erstellen.

>[!ENDTABS]

## &#x200B;4. Benutzer zur Benutzergruppe hinzufügen{#add-users}

1. Führen Sie einen der folgenden Schritte aus:

>[!BEGINTABS]

>[!TAB Hinzufügen einzelner Benutzer]

1. Klicken Sie auf **Seite** Benutzergruppen“ in der Tabelle **Gruppenname** auf den Namen der neu erstellten Benutzergruppe oder auf einen vorhandenen Benutzergruppennamen.

   ![Benutzergruppenseite mit dem Namen der AI-Assistentin in der AEM-Benutzergruppe in der Tabelle](/help/assets/assets-ai/ai-assistant-user-group-name-in-table.png)

1. Klicken Sie auf **Seite &quot;**&quot; für den **KI-Assistenten in AEM** auf die Registerkarte **Benutzer** und dann auf **Benutzer hinzufügen**.

   ![KI-Assistent in der Seite &quot;AEM-Benutzergruppen“, auf der die Registerkarte „Benutzer“ und die Schaltfläche „Benutzer hinzufügen“ angezeigt werden](/help/assets/assets-ai/ai-assistant-add-users.png)

1. Suchen Sie auf der Seite **`Add users to this user group`** nach Benutzenden, die Zugriff auf den KI-Assistenten in AEM benötigen, und wählen Sie diese aus.

   ![Benutzer zu dieser Benutzergruppenseite hinzufügen](/help/assets/assets-ai/ai-assistant-add-users-to-this-group.png)

1. Klicken Sie unten rechts auf der Seite auf **Speichern**.
1. Weisen [der Benutzergruppe das Produktprofil zu](#assign-product-profile).

>[!TAB Mehrere Benutzer auf einmal hinzufügen]

Sie können die Funktion für den Massen-Upload in der Admin Console verwenden.

1. Bereiten Sie eine CSV-Datei mit Benutzerinformationen vor.
1. Verwenden Sie die **`Add users by CSV`** Option für eine effiziente Massenhinzufügung.
1. Weisen [der Benutzergruppe das Produktprofil zu](#assign-product-profile).

>[!ENDTABS]


## &#x200B;5. Zuweisen des Produktprofils zur Benutzergruppe{#assign-product-profile}

Dieser Schritt folgt dem standardmäßigen Adobe Admin Console-Workflow für die Zuweisung von Produktprofilen zu Benutzergruppen.

Referenzartikel: [Verwalten von Produktprofilen für Enterprise-Benutzer](https://helpx.adobe.com/de/enterprise/using/manage-product-profiles.html)

1. Klicken Sie noch in Ihrem KI-Assistenten in der AEM-Benutzergruppe von [4 - Benutzer zur Benutzergruppe hinzufügen](#add-users) auf die Registerkarte **Zugewiesene Produktprofile**.
1. Klicken Sie **Profil zuweisen**.

   ![KI-Assistent in der AEM-Benutzergruppenseite mit ausgewählter Registerkarte „Zugewiesene Produktprofile“](/help/assets/assets-ai/ai-assistant-assign-profile.png)

1. Suchen Sie auf der **Produkte und Profile zuweisen** im Dialogfeld **Produktprofile auswählen** nach Ihrem **KI-Assistent**-Produktprofil und wählen Sie es aus.

   ![Die Seite „Produkte und Profile zuweisen“, die das Dialogfeld „Produktprofile auswählen“ anzeigt und das Produktprofil „KI-Assistent“ ausgewählt ist](/help/assets/assets-ai/ai-assistant-select-product-profile.png)

1. Klicken Sie unten rechts im Dialogfeld auf **Übernehmen**.
1. Klicken Sie unten rechts auf der Seite **Produkte und Profile zuweisen** auf **Speichern**.

   ![Produktprofil des KI-Assistenten in der Benutzergruppe &quot;AEM&quot; angezeigt, das dem KI-Assistenten zugewiesen ist](/help/assets/assets-ai/ai-assistant-profile-assigned-to-user-group.png)


## Konfiguration überprüfen

* Vergewissern Sie sich, dass in Ihrem Produktprofil die richtige Anzahl zugewiesener Benutzergruppen angezeigt wird.
* Vergewissern Sie sich, dass in der Benutzergruppe die richtige Anzahl von Benutzern angezeigt wird.
* Vergewissern Sie sich, dass die Berechtigung KI-Assistent für Produktkenntnisse aktiviert und ordnungsgemäß konfiguriert ist.


## Testen der Konfiguration

Bitten Sie einen Benutzer aus der zugewiesenen Gruppe, Folgendes zu tun:

1. Melden Sie sich bei AEM an.
2. Überprüfen, ob die Funktionen des KI-Assistenten verfügbar sind.
3. Testen der Funktionalität des KI-Assistenten, um eine ordnungsgemäße Aktivierung sicherzustellen.

## Siehe auch

* [KI-Assistent in AEM](/help/ai-assistant-in-aem.md)
* [Adobe Experience Platform-Zugriffskontrolle](https://experienceleague.adobe.com/de/docs/experience-platform/access-control/ui/overview)
<!-- * [Cloud Manager Custom Permissions](/help/implementing/cloud-manager/custom-permissions.md) -->
