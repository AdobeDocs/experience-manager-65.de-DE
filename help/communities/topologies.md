---
title: Empfohlene Topologien für Communities
description: Vorgehensweise beim Umgang mit benutzergenerierten Inhalten
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

Seit AEM Communities 6.1 gibt es einen einzigartigen Ansatz für die Verarbeitung von benutzergenerierten Inhalten (User Generated Content, UGC), die von Seitenbesuchern (Mitgliedern) aus der Veröffentlichungsumgebung gesendet werden.

Dieser Ansatz unterscheidet sich grundlegend von der Art und Weise, wie die AEM-Plattform Website-Inhalte verarbeitet, die im Allgemeinen von der Autorenumgebung aus verwaltet werden.

Die AEM-Plattform verwendet einen Knotenspeicher, der Website-Inhalte von der Autoren- zur Veröffentlichungsinstanz repliziert, während AEM Communities einen einzigen, gemeinsamen Speicher für UGC verwendet, der nie repliziert wird.

Für den gemeinsamen UGC-Speicher muss ein Speicherressourcenanbieter (Storage Resource [, SRP) ausgewählt werden](working-with-srp.md) Die empfohlenen Optionen sind:

* [DSRP - Relationaler Datenbankspeicher-Ressourcenanbieter](dsrp.md)
* [MSRP - MongoDB Storage Resource Provider](msrp.md)
* [ASRP - Adobe Storage Resource Provider](asrp.md)

Eine andere SRP-Option, [JSRP - JCR Storage Resource Provider](jsrp.md), unterstützt keinen gemeinsamen UGC-Speicher für die Autoren- und Veröffentlichungsumgebungen, auf die beide zugreifen können.

Die Anforderung eines gemeinsamen Speichers führt zu den folgenden empfohlenen Topologien.

>[!NOTE]
>
>Für AEM Communities [UGC nie repliziert](working-with-srp.md#ugc-never-replicated).
>
>Wenn die Bereitstellung keinen [Common Store](working-with-srp.md) enthält, ist der benutzergenerierte Inhalt (UGC) nur in der AEM-Veröffentlichungs- oder Autoreninstanz sichtbar, in der er eingegeben wurde.
>

>[!NOTE]
>
>Weitere Informationen zur AEM-Plattform finden Sie unter [Empfohlene &#x200B;](../../help/sites-deploying/recommended-deploys.md)&quot; und [Einführung in die AEM-Plattform](../../help/sites-deploying/data-store-config.md).

## Für die Produktion {#for-production}

Die Einrichtung eines gemeinsamen Speichers für benutzergenerierten Inhalt ist von entscheidender Bedeutung. Daher hängt die zugrunde liegende Bereitstellung von der Fähigkeit ab, einen gemeinsamen Speicher zu unterstützen.

Zwei Beispiele:

1. Wenn die erwartete Menge an benutzergenerierten Inhalten hoch und eine lokale MongoDB-Instanz möglich ist, wäre die Wahl [MSRP](msrp.md).

1. Für eine optimale Leistung bei Seiteninhalten würde die Auswahl einer [Veröffentlichungsfarm](../../help/sites-deploying/recommended-deploys.md#tarmk-farm) und [ASRP](asrp.md) eine optimale Skalierung von benutzergenerierten Inhalten mit relativ einfachen Vorgängen ermöglichen.

Für beide kann die Bereitstellung auf einem beliebigen OAK-Mikrokernel basieren.

Bei der Auswahl des geeigneten gemeinsamen Speichers sollten die individuellen [&#x200B; (](working-with-srp.md#characteristics-of-srp-options)) sorgfältig berücksichtigt werden.

Weitere Informationen zu Oak-Mikrokernels finden Sie unter [Empfohlene Bereitstellungen](../../help/sites-deploying/recommended-deploys.md).

### TarMK-Veröffentlichungsfarm {#tarmk-publish-farm}

Wenn es sich bei der Topologie um eine Veröffentlichungsfarm handelt, sind folgende wichtige Themen wichtig:

* [Benutzersynchronisierung](sync.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)

### Empfohlen: DSRP, MSRP oder ASRP {#recommended-dsrp-msrp-or-asrp}

| Mikrokernel | SITE CONTENTREPOSITORY | BENUTZERGENERIERTES CONTENTREPOSITORY | SPEICHERRESSOURCENANBIETER | GEMEINSCHAFTSGESCHÄFT |
|-------------|------------------------|----------------------------------|---------------------------|---------------|
| Beliebig | JCR | MySQL | DSRP | Ja |
| Beliebig | JCR | MongoDB | MSRP | Ja |
| Beliebig | JCR | Adobe On-Demand-Speicher | ASRP | Ja |

### JSRP {#jsrp}


| Bereitstellung | SITE CONTENTREPOSITORY | BENUTZERGENERIERTES CONTENTREPOSITORY | SPEICHERRESSOURCENANBIETER | GEMEINSCHAFTSGESCHÄFT |
|----------------------|------------------------|----------------------------------|---------------------------|---------------------------------|
| TarMK-Farm (Standard) | JCR | JCR | JSRP | Nein |
| Oak-Cluster | JCR | JCR | JSRP | Ja, nur für die Veröffentlichungsumgebung |

## Zur Entwicklung {#for-development}

Für Nicht-Produktionsumgebungen bietet [JSRP](jsrp.md) Einfachheit beim Einrichten einer Entwicklungsumgebung mit einer Autoreninstanz und einer Veröffentlichungsinstanz.

Wenn Sie [ASRP](asrp.md), [DSRP](dsrp.md) oder [MSRP](msrp.md) für die Produktion auswählen, ist es auch möglich, eine ähnliche Entwicklungsumgebung mit Adobe-On-Demand-Speicher oder MongoDB einzurichten. Ein Beispiel finden Sie unter [Einrichten von MongoDB für Demo](demo-mongo.md).

## Verweise {#references}

* [Benutzersynchronisierung](sync.md)

  Erörtert die Synchronisierung von Benutzerdaten zwischen Instanzen der Veröffentlichungsfarm.

* [Verwalten von Benutzern und Benutzergruppen](users.md)

  Erörtert die Rollen von Benutzern und Benutzergruppen in der Autoren- und Veröffentlichungsumgebung.

* UGC [Common Store](working-with-srp.md)

  Beschreibt das Speichern von Community-Inhalten getrennt von Site-Inhalten.

* [Knotenspeicher und Datenspeicher](../../help/sites-deploying/data-store-config.md)

  Grundsätzlich werden Site-Inhalte in einem Knotenspeicher gespeichert. Für Assets kann ein Datenspeicher zum Speichern binärer Daten konfiguriert werden. Für Communities muss ein Common Store konfiguriert werden, um das SRP auszuwählen.

* [Speicherelemente](../../help/sites-deploying/storage-elements-in-aem-6.md)

  Beschreibt die beiden Knotenspeicher-Implementierungen TAR und MongoDB.
