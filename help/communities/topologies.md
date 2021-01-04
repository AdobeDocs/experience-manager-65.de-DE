---
title: Empfohlene Topologien für Communities
seo-title: Empfohlene Topologien für Communities
description: Vorgehensweise beim Umgang mit benutzergenerierten Inhalten (UGC)
seo-description: Vorgehensweise beim Umgang mit benutzergenerierten Inhalten (UGC)
uuid: 4bc1c423-0ba9-4f2e-b11c-4d6824f45641
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: 46f135de-a0bf-451d-bdcc-fb29188250aa
translation-type: tm+mt
source-git-commit: 612d102b5925704ce459ad818554e487ec0d5355
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 6%

---


# Empfohlene Topologien für Communities {#recommended-topologies-for-communities}

Ab AEM Communities 6.1 wurde ein einzigartiger Ansatz für die Behandlung benutzergenerierter Inhalte (UGC) gewählt, die von Besuchern der Site (Mitglieder) aus der Umgebung &quot;Veröffentlichen&quot;eingereicht wurden.

Dieser Ansatz unterscheidet sich grundsätzlich von der Art und Weise, wie die AEM Plattform Site-Inhalte verarbeitet, die im Allgemeinen von der Autorenversion verwaltet werden.

Die AEM-Plattform verwendet einen Knotenspeicher, der den Site-Inhalt vom Autor bis zur Veröffentlichung repliziert, während AEM Communities einen einzigen gemeinsamen Speicher für UGC verwendet, der nie repliziert wird.

Für den allgemeinen UGC-Store muss ein [Datenspeicherung Resource Provider (SRP)](working-with-srp.md) ausgewählt werden. Die empfohlenen Optionen sind:

* [DSRP - Ressourcenanbieter für relationale Datenspeicherung](dsrp.md)
* [MSRP - MongoDB Datenspeicherung Resource Provider](msrp.md)
* [ASRP - Adobe Datenspeicherung Resource Provider](asrp.md)

Eine andere SRP-Option, [JSRP - JCR Datenspeicherung Resource Provider](jsrp.md), unterstützt keinen gemeinsamen UGC-Store für Autor- und Veröffentlichungseinstellungen für beide Umgebung.

Die Anforderung eines gemeinsamen Speichers führt zu den folgenden empfohlenen Topologien.

>[!NOTE]
>
>Bei AEM Communities wird [UGC nie repliziert](working-with-srp.md#ugc-never-replicated).
>
>Wenn die Bereitstellung keinen [gemeinsamen Speicher](working-with-srp.md) enthält, ist UGC nur auf der AEM- oder Autoreninstanz sichtbar, auf der sie eingegeben wurde.


>[!NOTE]
>
>Weitere Informationen zur AEM finden Sie unter [Empfohlene Bereitstellungen](../../help/sites-deploying/recommended-deploys.md) und [Einführung in die AEM Plattform](../../help/sites-deploying/data-store-config.md).

## Für Produktion {#for-production}

Die Schaffung eines gemeinsamen Speicherplatzes für UGC ist unverzichtbar, und daher hängt der zugrunde liegende Einsatz von seiner Fähigkeit ab, einen gemeinsamen Speicher zu unterstützen.

Zwei Beispiele:

1. Wenn das erwartete Volumen von UGC hoch ist und eine lokale MongoDB-Instanz möglich ist, dann wäre die Auswahl [MSRP](msrp.md).

1. Für eine optimale Leistung bei Seiteninhalten würde die Auswahl einer [Veröffentlichungsfarm](../../help/sites-deploying/recommended-deploys.md#tarmk-farm) und [ASRP](asrp.md) eine optimale Skalierung von UGC bei relativ unkomplizierten Vorgängen bieten.

Für beide kann die Bereitstellung auf einem beliebigen OAK-Mikrokernel basieren.

Um den passenden gemeinsamen Store auszuwählen, sollten Sie die eindeutigen [Merkmale](working-with-srp.md#characteristics-of-srp-options) sorgfältig beachten.

Weitere Informationen zu Oak-Mikrokernen finden Sie unter [Empfohlene Bereitstellungen](../../help/sites-deploying/recommended-deploys.md).

### TarMK-Veröffentlichungsfarm {#tarmk-publish-farm}

Wenn es sich bei der Topologie um eine Veröffentlichungsfarm handelt, sind folgende Themen von Bedeutung:

* [Benutzersynchronisierung](sync.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)

### Empfohlen: DSRP, MSRP oder ASRP {#recommended-dsrp-msrp-or-asrp}

| MicroKernel | SITE-INHALT | BENUTZER GENERIERTE INHALTE | DATENSPEICHERUNG RESOURCE PROVIDER | HÄUFIG GESPEICHERT |
|-------------|------------------------|----------------------------------|---------------------------|---------------|
| beliebig | JCR | MySQL | DSRP | Ja |
| beliebig | JCR | MongoDB | MSRP | Ja |
| beliebig | JCR | On-Demand-Speicher für Adoben | ASRP | Ja |

### JSRP {#jsrp}


| Bereitstellung | SITE-INHALT | BENUTZER GENERIERTE INHALTE | DATENSPEICHERUNG RESOURCE PROVIDER | HÄUFIG GESPEICHERT |
|----------------------|------------------------|----------------------------------|---------------------------|---------------------------------|
| TarMK Farm (Standard) | JCR | JCR | JSRP | Nein |
| Oak-Cluster | JCR | JCR | JSRP | Nur zur Veröffentlichung Umgebung |

## Für Entwicklung {#for-development}

Bei Nicht-Produktions-Umgebung bietet [JSRP](jsrp.md) eine einfache Möglichkeit, eine Development-Umgebung mit einer Autoreninstanz und einer Veröffentlichungsinstanz einzurichten.

Wenn Sie für die Produktion [ASRP](asrp.md), [DSRP](dsrp.md) oder [MSRP](msrp.md) auswählen, ist es auch möglich, eine ähnliche Umgebung für die Entwicklung mit Adobe On-Demand-Datenspeicherung oder MongoDB einzurichten. Ein Beispiel finden Sie unter [HowTo Setup MongoDB for Demo](demo-mongo.md).

## Verweise {#references}

* [Benutzersynchronisierung](sync.md)

   Behandelt die Synchronisierung von Benutzerdaten zwischen Instanzen im Veröffentlichungsmodus.

* [Verwalten von Benutzern und Benutzergruppen](users.md)

   Erläutert die Rollen von Benutzern und Benutzergruppen in den Umgebung zum Erstellen und Veröffentlichen.

* UGC [gemeinsamer Speicher](working-with-srp.md)

   Beschreibt die Datenspeicherung von Community-Inhalten, die vom Site-Inhalt getrennt sind.

* [Node Stores und Data Stores](../../help/sites-deploying/data-store-config.md)

   Grundsätzlich wird der Site-Inhalt in einem Node Store gespeichert. Bei Assets kann ein Datenspeicher konfiguriert werden, um Binärdaten zu speichern. Bei Communities muss ein gemeinsamer Store zur Auswahl des SRP konfiguriert werden.

* [Datenspeicherung](../../help/sites-deploying/storage-elements-in-aem-6.md)

   Beschreibt die beiden Node-Datenspeicherung-Implementierungen: Tar und MongoDB.
