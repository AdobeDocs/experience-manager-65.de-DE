---
title: Übersetzen von Inhalten für mehrsprachige Sites
description: Erfahren Sie, wie Sie Inhalte für mehrsprachige Sites übersetzen.
contentOwner: Guillaume Carlino
feature: Language Copy
exl-id: 6ccfe612-8cfd-4ca2-ad01-8e4af36d44fa
solution: Experience Manager, Experience Manager Sites
role: Admin
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: d9d38edd-df1b-480c-8f5e-72b62576f390
    internal-label: Site and page features
subfeature_v2:
  - id: e15a4109-ae5d-497d-b301-31149e35aed4
    internal-label: Language Copy Wizard
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 751e1826ed53df7522418e50a206f0fe622256a4
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 100%
---
# Übersetzen von Inhalten für mehrsprachige Sites {#translating-content-for-multilingual-sites}

Automatisieren Sie die Übersetzung von Seiteninhalten, Assets und benutzergenerierten Inhalten, um mehrsprachige Websites zu erstellen und zu pflegen. Um Übersetzungs-Workflows zu automatisieren, integrieren Sie Übersetzungsdienstleister in AEM und erstellen Sie Projekte für die Übersetzung von Inhalten in mehrere Sprachen. AEM unterstützt Workflows für menschliche und maschinelle Übersetzungen.

* Menschliche Übersetzung: Inhalte werden an Ihren Übersetzungsdienstleister gesendet und von professionellen Übersetzern übersetzt. Wenn die Inhalte übersetzt wurden, werden sie zurückgesendet und in AEM importiert. Ist Ihr Übersetzungsdienstleister in AEM integriert, werden die Inhalte automatisch von AEM an den Übersetzungsdienstleister gesendet.
* Maschinelle Übersetzung: Der maschinelle Übersetzungs-Service übersetzt sofort Ihre Inhalte.

Die Übersetzung der Inhalte umfasst die folgenden Schritte:

1. [Stellen Sie eine Verbindung zwischen AEM und Ihrem Übersetzungsdienstleister her](/help/sites-administering/tc-tic.md#connecting-to-a-translation-service-provider) und [erstellen Sie Konfigurationen für die Integration des Übersetzungs-Frameworks](/help/sites-administering/tc-tic.md).
1. [Verknüpfen Sie die Seiten Ihres Sprachstamms](/help/sites-administering/tc-tic.md#configuring-pages-for-translation) mit dem Übersetzungsdienstleister und den Framework-Konfigurationen.
1. [Identifizieren Sie die Art der zu übersetzenden Inhalte](/help/sites-administering/tc-rules.md).
1. [Bereiten Sie die Inhalte für die Übersetzung vor](/help/sites-administering/tc-prep.md), indem Sie den Sprachstamm und die Stammseiten der Sprachkopien erstellen.
1. [Erstellen Sie Übersetzungsprojekte](/help/sites-administering/tc-manage.md), um die zu übersetzenden Inhalte zusammenzustellen und den Übersetzungsprozess vorzubereiten.
1. Verwenden Sie die Übersetzungsprojekte, um [den Prozess zur Übersetzung der Inhalte zu verwalten](/help/sites-administering/tc-manage.md).

Wenn Ihr Übersetzungsanbieter keinen Connector zur Integration mit AEM bereitstellt, unterstützt AEM auch die manuelle Extraktion und das erneute Einfügen von Übersetzungsinhalten im XML-Format.

>[!NOTE]
>
>Ihre Benutzerin bzw. Ihr Benutzer muss Mitglied der Gruppe „project-administrators“ sein, um die Sprachkopie-Funktionen verwenden zu können.

## Best Practices {#best-practices}

Die Seite [Best Practices für die Übersetzung](/help/sites-administering/tc-bp.md) enthält wichtige Informationen zur Implementierung.
