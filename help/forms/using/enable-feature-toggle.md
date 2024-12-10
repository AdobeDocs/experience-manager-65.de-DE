---
title: Aktivieren Sie Feature Toggle, um die Funktionen Frühzeitige Anmeldung und Vorabversion zu integrieren.
description: Feature Toggle ist eine Funktion in AEM, mit der Administratoren neue Funktionen in einer Laufzeitumgebung aktivieren können.
feature: Adaptive Forms, Foundation Components
role: User, Developer
hidefromtoc: true
source-git-commit: 794d93d890ba752f9036a85831f7cbc8391fb545
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 7%

---

# Funktionswechsel in Adobe Experience Manager (AEM 6.5){#enable-feature-toggle-aem-forms-65}

Feature Toggle ist eine Funktion in AEM, mit der Administratoren bestimmte Funktionen dynamisch aktivieren oder deaktivieren können. Diese Funktion ist besonders nützlich für die Verwaltung von **Funktionen des frühen Anwenders** und **Funktionen der Vorabversion**, ohne dass umfangreiche Bereitstellungen oder Änderungen an der Codebasis erforderlich sind. Es ermöglicht Flexibilität und Kontrolle darüber, welche Funktionen in einer AEM verfügbar sind.

## Umschalten zwischen Funktionen aktivieren {#enable-feature-toggle-65}

Umschalter für Funktionen für frühe Anwender oder neue Funktionen können über die **AEM Web-Konsole** konfiguriert werden, indem Sie die folgenden Schritte ausführen:

1. Melden Sie sich bei Ihrer AEM Forms-Instanz an.
2. Navigieren Sie zu `http://<author-instance-url>:portnumber/system/console/configMgr`.
3. Suchen Sie im Configuration Manager nach **Adobe Granite Dynamic Toggle Provider** .
4. Klicken Sie auf das Symbol ![Stiftsymbol](assets/illustratorcc_penciltool_cur_edit_2_17.png).
5. Klicken Sie im Abschnitt [!UICONTROL Aktiviert/Umschalter] auf ![Bleistiftsymbol](assets/aem6forms_add.png).
6. Fügen Sie die Umschalter-ID für die Funktion hinzu, wie in der Abbildung unten dargestellt.
   ![Umschalter hinzufügen](assets/add_toggle_number_forms.png)

   >[!NOTE]
   >
   >Sie finden die Feature-Umschalter-ID im Dokument, das speziell für die Funktionen für frühe Anwender gilt.

7. Klicken Sie auf „Speichern“.

## Funktionswechsel deaktivieren {#disable-feature-toggle-65}

Gehen Sie wie folgt vor, um den/die Feature-Umschalter für Funktionen zu deaktivieren, deren Umschalter aktiviert ist:

1. Melden Sie sich bei Ihrer AEM Forms-Instanz an.
2. Navigieren Sie zu `http://<author-instance-url>:portnumber/system/console/configMgr`.
3. Suchen Sie im Configuration Manager nach **Adobe Granite Dynamic Toggle Provider** .
4. Klicken Sie auf das Symbol ![Stiftsymbol](assets/illustratorcc_penciltool_cur_edit_2_17.png).
5. Klicken Sie im Abschnitt [!UICONTROL Deaktivierte Umschalter] auf ![Bleistiftsymbol](assets/aem6forms_add.png).
6. Fügen Sie die Umschalter-Nummer hinzu, damit die Funktion deaktiviert werden kann.
   ![Umschalter entfernen](assets/remove_toggle_feature_forms.png)
7. Klicken Sie auf „Speichern“.

## Technische Aspekte

Feature-Umschalter sind umgebungsspezifisch und werden zur Laufzeit verwaltet, sodass kein Server-Neustart erforderlich ist. Einige Funktionen erfordern jedoch möglicherweise, dass die relevanten Seiten aktualisiert oder der Cache geleert wird, um Änderungen widerzuspiegeln.
Sie können über den Umschalter für Funktionen über `http://<author-instance-url>:4502/etc.clientlibs/toggles.json` auf die Liste der für Ihre Umgebung aktivierten Funktionen zugreifen.