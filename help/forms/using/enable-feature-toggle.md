---
title: Aktivieren des Funktionsumschalters, um Early-Adopter- und Vorabversionsfunktionen zu integrieren
description: Der Funktionsumschalter ist eine Funktion in AEM, mit der Admins neue Funktionen in einer Laufzeitumgebung aktivieren können.
feature: Adaptive Forms, Foundation Components
role: User, Developer
hidefromtoc: true
exl-id: 08815c2b-23b3-4545-a3ab-ba47ba1c3c55
source-git-commit: 0e80096b6b49372765b04a3bc1438b93d9cccf6e
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 92%

---

# Umschalten zwischen Funktionen in Adobe Experience Manager (AEM) 6.5{#enable-feature-toggle-aem-forms-65}

Der Funktionsumschalter ist eine Funktion in AEM, mit der Admins bestimmte Funktionen dynamisch aktivieren oder deaktivieren können. Diese Funktion ist besonders nützlich für die Verwaltung von **Early-Adopter**- und **Vorabversionsfunktionen** ohne größere Bereitstellungen oder Änderungen an der Code-Basis. Sie gewährleistet Flexibilität und Kontrolle darüber, auf welche Funktionen in einer AEM-Umgebung zugegriffen werden kann.

## Warum sollten in einem AEM 6.5-Setup Funktionsumschalter verwendet werden?

Beim Arbeiten mit einem AEM 6.5-Setup helfen Funktionsumschalter bei Folgendem:

* Sicheres Testen von Experimentalfunktionen.

* Rollout neuer Komponenten in Phasen.

* Pflege einer einzelnen Code-Basis über mehrere Umgebungen hinweg.

* Reduzierung des Risikos bei Bereitstellungen und Upgrades.

## Voraussetzungen

Stellen Sie vor dem Aktivieren der Funktionsumschalter in Ihrem AEM 6.5-Setup Folgendes sicher:

* Die Benutzerin bzw. der Benutzer ist Mitglied der Gruppe `forms-users`.

* Navigieren Sie zu `http://<author-instance-url>:portnumber/system/console/bundles` und überprüfen Sie, ob das Bundle **(com.adobe.granite.toggle.impl.dev-1.1.8.jar)** vorhanden ist. Falls nicht vorhanden [laden Sie das Bundle über den Link herunter](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2Fcom.adobe.granite.toggle.impl.dev-1.1.8.jar).

![Funktionsumschalter](/help/forms/using/assets/feature-toggle-1.1.8.png)

>[!NOTE]
>
>Sie können je nach Bedarf Funktions-Umschalter in Ihrer AEM 6.5-Umgebung oder in früheren Versionen aktivieren.

## Funktionsumschalter aktivieren {#enable-feature-toggle-65}

Funktionsumschalter für Early Adopters oder neue Funktionen können über die **AEM-Web-Konsole** konfiguriert werden, indem Sie die folgenden Schritte ausführen:

1. Melden Sie sich bei Ihrer AEM Forms-Instanz an.
2. Navigieren Sie zu `http://<author-instance-url>:portnumber/system/console/configMgr`.
3. Suchen Sie im Konfigurations-Manager nach **Adobe Granite Dynamic Toggle Provider**.
4. Klicken Sie auf das Symbol ![Bleistiftsymbol](assets/illustratorcc_penciltool_cur_edit_2_17.png).
5. Klicken Sie im Abschnitt [!UICONTROL Aktivierte Umschalter] auf das ![Bleistiftsymbol](assets/aem6forms_add.png).
6. Fügen Sie die Funktionsumschalter-ID für die Funktion hinzu, wie in der Abbildung unten dargestellt.
   ![Umschalter hinzufügen](assets/add_toggle_number_forms.png)

   >[!NOTE]
   >
   >Die Funktionsumschalter-ID finden Sie im dedizierten Dokument für die Early-Adopter-Funktionen.

7. Klicken Sie auf „Speichern“.

## Deaktivieren des Funktionsumschalters {#disable-feature-toggle-65}

Gehen Sie wie folgt vor, um die Funktionsumschalter für Funktionen zu deaktivieren, deren Umschalter aktiviert sind:

1. Melden Sie sich bei Ihrer AEM Forms-Instanz an.
2. Navigieren Sie zu `http://<author-instance-url>:portnumber/system/console/configMgr`.
3. Suchen Sie im Konfigurations-Manager nach **Adobe Granite Dynamic Toggle Provider**.
4. Klicken Sie auf das Symbol ![Bleistiftsymbol](assets/illustratorcc_penciltool_cur_edit_2_17.png).
5. Klicken Sie im Abschnitt [!UICONTROL Deaktivierte Umschalter] auf das ![Bleistiftsymbol](assets/aem6forms_add.png).
6. Fügen Sie die Umschalternummer für die zu deaktivierende Funktion hinzu.
   ![Umschalter entfernen](assets/remove_toggle_feature_forms.png)
7. Klicken Sie auf „Speichern“.

## Technische Überlegung

Funktionsumschalter sind umgebungsspezifisch und werden zur Laufzeit verwaltet, sodass kein Neustart des Servers erforderlich ist. Bei einigen Funktionen ist es jedoch möglicherweise erforderlich, die relevanten Seiten zu aktualisieren oder den Cache zu löschen, um Änderungen widerzuspiegeln.
Sie können über `http://<author-instance-url>:4502/etc.clientlibs/toggles.json` auf die Liste der Funktionen zugreifen, die über den Funktionsumschalter für Ihre Umgebung aktiviert sind.
