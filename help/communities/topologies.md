---
title: Empfohlene Topologien für Communities
seo-title: Empfohlene Topologien für Communities
description: Vorgehensweise bei der Verarbeitung von benutzergenerierten Inhalten (UGC)
seo-description: Vorgehensweise bei der Verarbeitung von benutzergenerierten Inhalten (UGC)
uuid: 4bc1c423-0ba9-4f2e-b11c-4d6824f45641
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: 46f135de-a0bf-451d-bdcc-fb29188250aa
exl-id: b6658330-d862-44e3-aac0-824fb91cd087
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 7%

---

# Empfohlene Topologien für Communities {#recommended-topologies-for-communities}

Ab AEM Communities 6.1 wurde ein einzigartiger Ansatz für die Verarbeitung benutzergenerierter Inhalte (UGC) gewählt, die von Site-Besuchern (Mitgliedern) aus der Veröffentlichungsumgebung eingereicht wurden.

Dieser Ansatz unterscheidet sich grundlegend von der Art und Weise, wie die AEM Plattform Site-Inhalte verarbeitet, die im Allgemeinen aus der Autorenumgebung verwaltet werden.

Die AEM-Plattform verwendet einen Knotenspeicher, der Site-Inhalte vom Autor zur Veröffentlichung repliziert, während AEM Communities einen einzigen, gemeinsamen Speicher für benutzergenerierte Inhalte verwendet, der nie repliziert wird.

Für den gängigen UGC-Speicher ist es erforderlich, einen [Speicherressourcenanbieter (SRP)](working-with-srp.md) auszuwählen. Die empfohlenen Optionen sind:

* [DSRP - Resource Provider für relationale Datenbankspeicher](dsrp.md)
* [MSRP - MongoDB Storage Resource Provider](msrp.md)
* [ASRP - Adobe Storage Resource Provider](asrp.md)

Eine andere SRP-Option, [JSRP - JCR Storage Resource Provider](jsrp.md), unterstützt keinen gängigen UGC-Speicher für die Autoren- und Veröffentlichungsumgebungen für beide Zugriffe.

Die Anforderung eines gemeinsamen Stores führt zu den folgenden empfohlenen Topologien.

>[!NOTE]
>
>Bei AEM Communities wird [UGC nie repliziert](working-with-srp.md#ugc-never-replicated).
>
>Wenn die Bereitstellung keinen [gemeinsamen Speicher](working-with-srp.md) enthält, ist die benutzergenerierte Inhalte nur in der AEM- oder Autoreninstanz sichtbar, in der sie eingegeben wurde.


>[!NOTE]
>
>Weitere Informationen zur AEM finden Sie unter [Empfohlene Bereitstellungen](../../help/sites-deploying/recommended-deploys.md) und [Einführung in die AEM Plattform](../../help/sites-deploying/data-store-config.md).

## Für die Produktion {#for-production}

Die Einrichtung eines gemeinsamen Stores für benutzergenerierte Inhalte ist unerlässlich, und daher ist die zugrunde liegende Bereitstellung von der Fähigkeit abhängig, einen gemeinsamen Speicher zu unterstützen.

Zwei Beispiele:

1. Wenn das erwartete Volumen von UGC hoch ist und eine lokale MongoDB-Instanz möglich ist, wählen Sie [MSRP](msrp.md) aus.

1. Für eine optimale Leistung für Seiteninhalte würde die Auswahl einer [Veröffentlichungsfarm](../../help/sites-deploying/recommended-deploys.md#tarmk-farm) und [ASRP](asrp.md) eine optimale Skalierung der benutzergenerierten Inhalte bei relativ unkomplizierten Vorgängen liefern.

Für beide kann die Bereitstellung auf einem beliebigen OAK-Mikrokernel basieren.

Um den entsprechenden gemeinsamen Speicher auszuwählen, beachten Sie sorgfältig die eindeutigen [Merkmale](working-with-srp.md#characteristics-of-srp-options).

Weitere Informationen zu Oak-Mikrokernals finden Sie unter [Empfohlene Bereitstellungen](../../help/sites-deploying/recommended-deploys.md).

### TarMK-Veröffentlichungsfarm {#tarmk-publish-farm}

Wenn es sich bei der Topologie um eine Veröffentlichungsfarm handelt, sind folgende Themen von Bedeutung:

* [Benutzersynchronisierung](sync.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)

### Empfohlen: DSRP, MSRP oder ASRP {#recommended-dsrp-msrp-or-asrp}

| MicroKernel | SITE CONTENTREPOSITORY | BENUTZERGENERIERTER CONTENTREPOSITORY | RESSOURCENANBIETER SPEICHERN | HÄUFIGES SPEICHER |
|-------------|------------------------|----------------------------------|---------------------------|---------------|
| beliebig | JCR | MySQL | DSRP | Ja |
| beliebig | JCR | MongoDB | MSRP | Ja |
| beliebig | JCR | Adobe On-Demand-Speicher | ASRP | Ja |

### JSRP {#jsrp}


| Bereitstellung | SITE CONTENTREPOSITORY | BENUTZERGENERIERTER CONTENTREPOSITORY | RESSOURCENANBIETER SPEICHERN | HÄUFIGES SPEICHER |
|----------------------|------------------------|----------------------------------|---------------------------|---------------------------------|
| TarMK-Farm (Standard) | JCR | JCR | JSRP | Nein |
| Oak-Cluster | JCR | JCR | JSRP | Nur für Veröffentlichungsumgebung |

## Für Entwicklung {#for-development}

Bei Nicht-Produktionsumgebungen bietet [JSRP](jsrp.md) eine einfache Möglichkeit, eine Entwicklungsumgebung mit einer Autoreninstanz und einer Veröffentlichungsinstanz einzurichten.

Wenn Sie [ASRP](asrp.md), [DSRP](dsrp.md) oder [MSRP](msrp.md) für die Produktion auswählen, ist es auch möglich, eine ähnliche Entwicklungsumgebung mit Adobe On-Demand-Speicher oder MongoDB einzurichten. Ein Beispiel finden Sie unter [So richten Sie MongoDB für Demo](demo-mongo.md) ein.

## Verweise {#references}

* [Benutzersynchronisierung](sync.md)

   Beschreibt die Synchronisierung von Benutzerdaten zwischen Veröffentlichungsfarm-Instanzen.

* [Verwalten von Benutzern und Benutzergruppen](users.md)

   Erläutert die Rollen von Benutzern und Benutzergruppen in der Autoren- und Veröffentlichungsumgebung.

* UGC [Common Store](working-with-srp.md)

   Beschreibt die Speicherung von Community-Inhalten, die von Site-Inhalten getrennt sind.

* [Knotenspeicher und Datenspeicher](../../help/sites-deploying/data-store-config.md)

   Grundsätzlich wird der Site-Inhalt in einem Knotenspeicher gespeichert. Für Assets kann ein Datenspeicher zum Speichern von Binärdaten konfiguriert werden. Für Communities muss ein gemeinsamer Speicher zur Auswahl des SRP konfiguriert werden.

* [Speicherelemente](../../help/sites-deploying/storage-elements-in-aem-6.md)

   Beschreibt die beiden Implementierungen des Knotenspeichers: Tar und MongoDB.
