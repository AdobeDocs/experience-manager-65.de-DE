---
title: Aktualisieren von Inhaltsfragmenten für optimierte GraphQL-Filterung
description: Erfahren Sie, wie Sie Ihre Inhaltsfragmente für optimiertes GraphQL-Filtern in Adobe Experience Manager für die Bereitstellung Headless Content aktualisieren.
exl-id: d78ec052-c091-49ca-9f36-a3d24eb9edd5
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin,Architect,Data Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 37%

---

# Aktualisieren von Inhaltsfragmenten für optimierte GraphQL-Filterung {#updating-content-fragments-for-optimized-graphql-filtering}

Um die Leistung Ihrer GraphQL-Filter zu optimieren, führen Sie ein Verfahren aus, um Ihre Inhaltsfragmente zu aktualisieren.

>[!NOTE]
>
>Nach dem Aktualisieren Ihrer Inhaltsfragmente können Sie den Empfehlungen für [Optimieren von GraphQL-Abfragen](/help/sites-developing/headless/graphql-api/graphql-optimization.md).

## Voraussetzungen {#prerequisites}

Stellen Sie sicher, dass Sie mindestens Version 6.5.17.0 von AEM haben.

## Aktualisieren von Inhaltsfragmenten {#updating-content-fragments}

Gehen Sie wie folgt vor, um das Verfahren auszuführen:

1. [Konfigurieren der OSGi-Einstellungen](/help/sites-deploying/configuring-osgi.md) für die **Konfiguration des Inhaltsfragmentmigrationsauftrags**:

   ![OSGi-Konfiguration für die Migration von Inhaltsfragmenten](assets/cfm-graphql-update-01.png "OSGi-Konfiguration für die Migration von Inhaltsfragmenten")

1. Legen Sie diese beiden Parameter im Dialogfeld wie folgt fest:

   * **ContentFragmentMigration:Enabled** : `1`
   * **ContentFragmentMigration:Enforce** : `1`

1. **Speichern** die Spezifikationen - das Aktualisierungsverfahren beginnt.

1. Warten Sie, bis das Verfahren abgeschlossen ist. Das Verfahren ist abgeschlossen, wenn die Eigenschaft `cfGlobalVersion` erscheint auf `/content/dam` und auf `1`.

1. Kehren Sie zur OSGi-Konfiguration zurück, um den Vorgang zu deaktivieren.

   Im Dialogfeld für die **Konfiguration des Inhaltsfragmentmigrationsauftrags** Legen Sie diese beiden Parameter wie folgt fest:

   * **ContentFragmentMigration:Enabled** : `0`
   * **ContentFragmentMigration:Enforce** : `0`

## Einschränkungen {#limitations}

Beachten Sie die folgenden Einschränkungen:

* Die Leistungsoptimierung von GraphQL-Filtern ist erst nach einer vollständigen Aktualisierung aller Ihrer Inhaltsfragmente möglich (erkennbar am Vorhandensein der Eigenschaft `cfGlobalVersion` für den JCR-Knoten `/content/dam`)

* Wenn Inhaltsfragmente aus einem Inhaltspaket (mit `crx/de`) importiert werden, nachdem das Aktualisierungsverfahren ausgeführt wurde, werden diese Inhaltsfragmente erst dann in den GraphQL-Abfrageergebnissen berücksichtigt, wenn das Aktualisierungsverfahren erneut ausgeführt wird.
