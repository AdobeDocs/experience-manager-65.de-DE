---
title: Funktionsumschalter aktivieren, um Funktionen für frühzeitige Anpassungen und Vorabversionen zu integrieren
description: Feature Toggle ist eine Funktion in AEM, mit der Admins neue Funktionen in einer Laufzeitumgebung aktivieren können.
feature: Adaptive Forms, Foundation Components
role: User, Developer
hidefromtoc: true
exl-id: 08815c2b-23b3-4545-a3ab-ba47ba1c3c55
source-git-commit: 4964ef768acbc04760a27efc86e6378420b71a19
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 8%

---

# Umschalten zwischen Funktionen in Adobe Experience Manager (AEM) 6.5{#enable-feature-toggle-aem-forms-65}

Der Feature Toggle ist eine Funktion in AEM, mit der Admins bestimmte Funktionen dynamisch aktivieren oder deaktivieren können. Diese Funktion ist besonders nützlich für die Verwaltung von **Early-Adopter**- und **Vorabversionsfunktionen** ohne größere Bereitstellungen oder Änderungen an der Codebasis. Es gewährleistet Flexibilität und Kontrolle darüber, auf welche Funktionen in einer AEM-Umgebung zugegriffen werden kann.

## Umschalter für Funktionen aktivieren {#enable-feature-toggle-65}

Ein- oder Ausschalten von Funktionen für frühzeitige Benutzende oder neue Funktionen kann über die **AEM-Web-Konsole konfiguriert werden** indem die folgenden Schritte ausgeführt werden:

1. Melden Sie sich bei Ihrer AEM Forms-Instanz an.
2. Navigieren Sie zu `http://<author-instance-url>:portnumber/system/console/configMgr`.
3. Suchen Sie im Konfigurations-Manager nach **Adobe Granite Dynamic** Provider.
4. Klicken Sie auf das Symbol ![Bleistiftsymbol](assets/illustratorcc_penciltool_cur_edit_2_17.png).
5. Klicken Sie [!UICONTROL  Abschnitt „Aktivierte ]&quot; auf ![Bleistiftsymbol](assets/aem6forms_add.png).
6. Fügen Sie die Funktions-Umschalter-ID für die Funktion hinzu, wie in der Abbildung unten dargestellt.
   ![Umschalter hinzufügen](assets/add_toggle_number_forms.png)

   >[!NOTE]
   >
   >Die Umschalter-ID für Funktionen finden Sie im Dokument für die Early-Adopter-Funktionen.

7. Klicken Sie auf „Speichern“.

## Umschalten zwischen Funktionen deaktivieren {#disable-feature-toggle-65}

Gehen Sie wie folgt vor, um die Umschalter für Funktionen zu deaktivieren, deren Umschalter aktiviert sind:

1. Melden Sie sich bei Ihrer AEM Forms-Instanz an.
2. Navigieren Sie zu `http://<author-instance-url>:portnumber/system/console/configMgr`.
3. Suchen Sie im Konfigurations-Manager nach **Adobe Granite Dynamic** Provider.
4. Klicken Sie auf das Symbol ![Bleistiftsymbol](assets/illustratorcc_penciltool_cur_edit_2_17.png).
5. Klicken Sie [!UICONTROL  Abschnitt „Deaktivierte ]&quot; auf ![Bleistiftsymbol](assets/aem6forms_add.png).
6. Fügen Sie die Umschaltnummer hinzu, damit die Funktion deaktiviert wird.
   ![Umschalter entfernen](assets/remove_toggle_feature_forms.png)
7. Klicken Sie auf „Speichern“.

## Technische Überlegung

Funktions-Umschalter sind umgebungsspezifisch und werden zur Laufzeit verwaltet, sodass kein Neustart des Servers erforderlich ist. Bei einigen Funktionen ist es jedoch möglicherweise erforderlich, die relevanten Seiten zu aktualisieren oder den Cache zu löschen, um Änderungen widerzuspiegeln.
Sie können über den Umschalter für Funktionen in Ihrer Umgebung auf die Liste der aktivierten Funktionen über `http://<author-instance-url>:4502/etc.clientlibs/toggles.json` zugreifen.
