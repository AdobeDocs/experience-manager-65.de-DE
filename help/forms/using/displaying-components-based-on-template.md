---
title: Anzeigen von Komponenten basierend auf der verwendeten Vorlage
description: Erfahren Sie, wie Sie bei der Erstellung eines Formulars Komponenten in der Seitenleiste basierend auf der ausgewählten Vorlage aktivieren können.
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
content-type: reference
docset: aem65
exl-id: 1fc56829-db81-4450-b1d8-b4a31110199e
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms,Foundation Components
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 7da902b6-fe94-5180-8e7c-f6d1e38d01d5
    internal-label: Foundation Components
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
source-wordcount: '354'
ht-degree: 100%
---
# Anzeigen von Komponenten basierend auf der verwendeten Vorlage{#displaying-components-based-on-the-template-used}

Wenn ein Formular anhand einer [Vorlage](../../forms/using/template-editor.md) erstellt wird, lassen sich basierend auf der Vorlagenrichtlinie bestimmte Komponenten sehen und verwenden. Sie können eine Inhaltsrichtlinie für Vorlagen angeben, mit der Sie eine Gruppe von Komponenten auswählen können, die Formularautorinnen und -autoren beim Verfassen des Formulars angezeigt wird.

## Ändern der Inhaltsrichtlinie einer Vorlage {#changing-the-content-policy-of-a-template}

Wenn Sie eine Vorlage erstellen, wird diese unter `/conf` im Content Repository erstellt. Basierend auf den Ordnern, die Sie im Verzeichnis `/conf` erstellt haben, lautet der Pfad zur Vorlage: `/conf/<your-folder>/settings/wcm/templates/<your-template>`.

Führen Sie die folgenden Schritte aus, um die Komponenten basierend auf der Content-Richtlinie einer Vorlage in der Seitenleiste anzuzeigen:

1. Öffnen Sie CRXDE Lite.\
   URL: `https://<server>:<port>/crx/de/index.jsp`
1. Gehen Sie in CRXDE zu dem Ordner, in dem die Vorlage erstellt werden soll.

   Beispiel: `/conf/<your-folder>/`

1. Navigieren Sie in CRXDE zu: `/conf/<your-folder>/settings/wcm/policies/fd/af/layouts/gridFluidLayout/`

   Zum Auswählen einer Komponentengruppe ist eine neue Inhaltsrichtlinie erforderlich. Kopieren Sie zum Erstellen einer Richtlinie die Standardrichtlinie, fügen Sie sie ein und benennen Sie sie um.

   Der Pfad zur Standardinhaltsrichtlinie lautet: `/conf/<your-folder>/settings/wcm/policies/fd/af/layouts/gridFluidLayout/default`

   Kopieren Sie im Ordner `gridFluidLayout` die Standardrichtlinie, fügen Sie sie ein und benennen Sie sie um. Beispiel: `myPolicy`.

   ![Kopieren von Standardrichtlinien](assets/crx-default1.png)

1. Wählen Sie die neu zu erstellende Richtlinie und anschließend im rechten Bedienfeld die Eigenschaft **Komponenten** vom Typ `string[]` aus.

   Wenn Sie die Komponenteneigenschaft auswählen und öffnen, erscheint das Dialogfeld „Komponenten bearbeiten“. Im Dialogfeld „Komponenten bearbeiten“ können Sie Komponentengruppen mit den Tasten **+** und **-** hinzufügen oder entfernen. Sie können Komponentengruppen mit Komponenten hinzufügen, die Autoren für Formulare verwenden sollen.

   ![Hinzufügen oder Entfernen von Komponenten in der Richtlinie](assets/add-components-list1.png)

   Nachdem Sie eine Komponentengruppe hinzugefügt haben, klicken Sie auf **„OK“**, um die Liste zu aktualisieren, und klicken Sie dann auf **Alle speichern** über der CRXDE-Adressleiste und aktualisieren Sie.

1. Ändern Sie die Content-Richtlinie in der Vorlage vom Standard zu der neu erstellten Richtlinie. ( `myPolicy` in diesem Beispiel.)

   Um die Richtlinie zu ändern, navigieren Sie in CRXDE zu `/conf/<your-folder>/settings/wcm/templates/<your-template>/policies/jcr:content/guideContainer/rootPanel/items`.

   Ändern Sie in der Eigenschaft `cq:policy` den Eintrag `default` in den neuen Richtliniennamen (`myPolicy`).

   ![Aktualisierte Content-Richtlinie für Vorlagen](assets/updated-policy.png)

   Wenn Sie ein Formular mit der Vorlage erstellen, werden die hinzugefügten Komponenten in der Seitenleiste angezeigt.
