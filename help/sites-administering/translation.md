---
title: Übersetzen von Inhalten für mehrsprachige Sites
seo-title: Übersetzen von Inhalten für mehrsprachige Sites
description: Erfahren Sie mehr zur Übersetzung von Inhalten für mehrsprachige Sites.
seo-description: Erfahren Sie mehr zur Übersetzung von Inhalten für mehrsprachige Sites.
uuid: 69b3e3a9-6773-4759-8178-aaa612e4c170
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 1e0a68c5-1583-4103-9dbb-7a53faa03c06
docset: aem65
legacypath: /content/docs/en/aem/6-0/administer/integration/third-party-services/machine-translation
feature: Sprachkopie
exl-id: 6ccfe612-8cfd-4ca2-ad01-8e4af36d44fa
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 100%

---

# Übersetzen von Inhalten für mehrsprachige Sites {#translating-content-for-multilingual-sites}

Automatisieren Sie die Übersetzung von Seiteninhalten, Assets und benutzergenerierten Inhalten, um mehrsprachige Websites zu erstellen und zu pflegen. Zur Automatisierung von Übersetzungs-Workflows integrieren Sie die Übersetzungsdienstleister in AEM und erstellen Sie Projekte zur Übersetzung von Inhalten in mehrere Sprachen. AEM unterstützt menschliche und maschinelle Übersetzungs-Workflows.

* Menschliche Übersetzung: Inhalte werden an Ihren Übersetzungsdienstleister gesendet und von professionellen Übersetzern übersetzt. Wenn die Inhalte übersetzt wurden, werden sie zurückgesendet und in AEM importiert. Ist Ihr Übersetzungsdienstleister in AEM integriert, werden die Inhalte automatisch von AEM an den Übersetzungsdienstleister gesendet.
* Maschinelle Übersetzung: Der maschinelle Übersetzungs-Service übersetzt sofort Ihre Inhalte.

Die Übersetzung der Inhalte umfasst die folgenden Schritte:

1. [Stellen Sie eine Verbindung zwischen AEM und Ihrem Übersetzungsdienstleister her](/help/sites-administering/tc-tic.md#connecting-to-a-translation-service-provider) und [erstellen Sie Konfigurationen für die Integration des Übersetzungs-Frameworks](/help/sites-administering/tc-tic.md).
1. [Verknüpfen Sie die Seiten Ihres Sprachstamms](/help/sites-administering/tc-tic.md#configuring-pages-for-translation) mit dem Übersetzungsdienstleister und den Framework-Konfigurationen.
1. [Identifizieren Sie die Art der zu übersetzenden Inhalte](/help/sites-administering/tc-rules.md).
1. [Bereiten Sie die Inhalte für die Übersetzung vor](/help/sites-administering/tc-prep.md), indem Sie den Sprachstamm und die Stammseiten der Sprachkopien erstellen.
1. [Erstellen Sie Übersetzungsprojekte](/help/sites-administering/tc-manage.md), um die zu übersetzenden Inhalte zusammenzustellen und den Übersetzungsprozess vorzubereiten.
1. Verwenden Sie die Übersetzungsprojekte, um [den Prozess zur Übersetzung der Inhalte zu verwalten](/help/sites-administering/tc-manage.md).

Wenn Ihr Übersetzungsdienstleister keinen Connector für die Integration in AEM bereitstellt, unterstützt AEM auch die manuelle Extrahierung und das erneute Einfügen von Übersetzungsinhalten im XML-Format.

>[!NOTE]
>
>Ihr Benutzer muss Mitglied der Gruppe „project-administrators“ sein, um die Sprachkopie-Funktionen zu verwenden.

## Best Practices {#best-practices}

Die Seite [Best Practices für die Übersetzung](/help/sites-administering/tc-bp.md) enthält wichtige Informationen zur Implementierung.
