---
title: Empfohlene Topologien für Communities
description: Vorgehensweise bei der Verarbeitung benutzergenerierter Inhalte (UGC)
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
content-type: reference
topic-tags: deploying
exl-id: b6658330-d862-44e3-aac0-824fb91cd087
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 6%

---

# Empfohlene Topologien für Communities {#recommended-topologies-for-communities}

Ab AEM Communities 6.1 wurde ein einzigartiger Ansatz für die Verarbeitung benutzergenerierter Inhalte (UGC) gewählt, die von Site-Besuchern (Mitgliedern) aus der Veröffentlichungsumgebung eingereicht wurden.

Dieser Ansatz unterscheidet sich grundlegend von der Art und Weise, wie die AEM Plattform Site-Inhalte verarbeitet, die im Allgemeinen aus der Autorenumgebung verwaltet werden.

Die AEM-Plattform verwendet einen Knotenspeicher, der Site-Inhalte vom Autor zur Veröffentlichung repliziert, während AEM Communities einen einzigen, gemeinsamen Speicher für benutzergenerierte Inhalte verwendet, der nie repliziert wird.

Für den gängigen UGC-Store muss ein [Storage Resource Provider (SRP)](working-with-srp.md). Die empfohlenen Optionen sind:

* [DSRP - Resource Provider für relationale Datenbankspeicher](dsrp.md)
* [MSRP - MongoDB Storage Resource Provider](msrp.md)
* [ASRP - Adobe Storage Resource Provider](asrp.md)

eine andere SRP-Option, [JSRP - JCR Storage Resource Provider](jsrp.md)unterstützt keinen gängigen UGC-Store für die Autoren- und Veröffentlichungsumgebungen für beide Zugriffs.

Die Anforderung eines gemeinsamen Stores führt zu den folgenden empfohlenen Topologien.

>[!NOTE]
>
>Für AEM Communities: [UGC wird nie repliziert](working-with-srp.md#ugc-never-replicated).
>
>Wenn die Bereitstellung keine [gemeinsamer Speicher](working-with-srp.md), wird UGC nur in der AEM- oder Autoreninstanz angezeigt, in der sie eingegeben wurde.
>

>[!NOTE]
>
>Weitere Informationen zur AEM finden Sie unter [Empfohlene Bereitstellungen](../../help/sites-deploying/recommended-deploys.md) und [Einführung in die AEM Platform](../../help/sites-deploying/data-store-config.md).

## für die Produktion {#for-production}

Die Einrichtung eines gemeinsamen Stores für benutzergenerierte Inhalte ist unerlässlich, und daher ist die zugrunde liegende Bereitstellung von der Fähigkeit abhängig, einen gemeinsamen Speicher zu unterstützen.

Zwei Beispiele:

1. Wenn das erwartete UGC-Volumen und eine lokale MongoDB-Instanz möglich sind, wäre die Auswahl [MSRP](msrp.md).

1. Um eine optimale Leistung für Seiteninhalte zu erzielen, wählen Sie eine [Veröffentlichungsfarm](../../help/sites-deploying/recommended-deploys.md#tarmk-farm) und [ASRP](asrp.md) würde eine optimale Skalierung der benutzergenerierten Inhalte bei relativ unkomplizierten Vorgängen ermöglichen.

Für beide kann die Bereitstellung auf einem beliebigen OAK-Mikrokernel basieren.

Wenn Sie den entsprechenden gemeinsamen Speicher auswählen möchten, sollten Sie die eindeutige [Merkmale](working-with-srp.md#characteristics-of-srp-options) von jedem.

Weitere Informationen zu Oak-Mikrokernals finden Sie unter [Empfohlene Bereitstellungen](../../help/sites-deploying/recommended-deploys.md).

### TarMK-Veröffentlichungsfarm {#tarmk-publish-farm}

Wenn es sich bei der Topologie um eine Veröffentlichungsfarm handelt, sind folgende Themen von Bedeutung:

* [Benutzersynchronisierung](sync.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)

### Empfohlen: DSRP, MSRP oder ASRP {#recommended-dsrp-msrp-or-asrp}

| MicroKernel | SITE CONTENTREPOSITORY | BENUTZERGENERIERTER CONTENTREPOSITORY | RESSOURCENANBIETER SPEICHERN | HÄUFIGES SPEICHER |
|-------------|------------------------|----------------------------------|---------------------------|---------------|
| Beliebig | JCR | MySQL | DSRP | Ja |
| Beliebig | JCR | MongoDB | MSRP | Ja |
| Beliebig | JCR | Adobe On-Demandstorage | ASRP | Ja |

### JSRP {#jsrp}


| Bereitstellung | SITE CONTENTREPOSITORY | BENUTZERGENERIERTER CONTENTREPOSITORY | RESSOURCENANBIETER SPEICHERN | HÄUFIGES SPEICHER |
|----------------------|------------------------|----------------------------------|---------------------------|---------------------------------|
| TarMK-Farm (Standard) | JCR | JCR | JSRP | Nein |
| Oak-Cluster | JCR | JCR | JSRP | Nur für Veröffentlichungsumgebung |

## Für Entwicklung {#for-development}

Bei Nicht-Produktionsumgebungen: [JSRP](jsrp.md) bietet eine einfache Möglichkeit, eine Entwicklungsumgebung mit einer Autoreninstanz und einer Veröffentlichungsinstanz einzurichten.

Wenn Sie [ASRP](asrp.md), [DSRP](dsrp.md) oder [MSRP](msrp.md) Für die Produktion ist es auch möglich, eine ähnliche Entwicklungsumgebung mit Adobe On-Demand-Speicher oder MongoDB einzurichten. Ein Beispiel finden Sie unter [Einrichten von MongoDB für Demo](demo-mongo.md).

## Verweise {#references}

* [Benutzersynchronisierung](sync.md)

  Beschreibt die Synchronisierung von Benutzerdaten zwischen Veröffentlichungsfarm-Instanzen.

* [Verwalten von Benutzern und Benutzergruppen](users.md)

  Erläutert die Rollen von Benutzern und Benutzergruppen in der Autoren- und Veröffentlichungsumgebung.

* UGC [gemeinsamer Speicher](working-with-srp.md)

  Beschreibt die Speicherung von Community-Inhalten, die von Site-Inhalten getrennt sind.

* [Knotenspeicher und Datenspeicher](../../help/sites-deploying/data-store-config.md)

  Grundsätzlich wird der Site-Inhalt in einem Knotenspeicher gespeichert. Für Assets kann ein Datenspeicher zum Speichern von Binärdaten konfiguriert werden. Für Communities muss ein gemeinsamer Speicher zur Auswahl des SRP konfiguriert werden.

* [Speicherelemente](../../help/sites-deploying/storage-elements-in-aem-6.md)

  Beschreibt die beiden Knotenspeicherimplementierungen Tar und MongoDB.
