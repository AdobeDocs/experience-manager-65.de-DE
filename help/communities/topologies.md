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
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Empfohlene Topologien für Communities {#recommended-topologies-for-communities}

Ab AEM Communities 6.1 wurde ein eindeutiger Ansatz für die Behandlung benutzergenerierter Inhalte (UGC) gewählt, die von Besuchern der Site (Mitgliedern) aus der Veröffentlichungsumgebung übermittelt wurden.

Dieser Ansatz unterscheidet sich grundsätzlich von der Art und Weise, wie die AEM-Plattform Site-Inhalte verarbeitet, die im Allgemeinen aus der Autorenumgebung verwaltet werden.

Die AEM-Plattform verwendet einen Knotenspeicher, der den Site-Inhalt vom Autor zur Veröffentlichung repliziert, während AEM Communities einen einzigen, gemeinsamen Speicher für UGC verwendet, der nie repliziert wird.

Für den allgemeinen UGC-Store muss ein [Speicherressourcenanbieter (SRP)](working-with-srp.md)gewählt werden. Die empfohlenen Optionen sind:

* [DSRP - Ressourcenanbieter für den relationalen Datenbankspeicher](dsrp.md)
* [MSRP - MongoDB Storage Resource Provider](msrp.md)
* [ASRP - Adobe Storage Resource Provider](asrp.md)

Eine andere SRP-Option, [JSRP - JCR Storage Resource Provider](jsrp.md), unterstützt keinen gemeinsamen UGC-Store für Autoren- und Veröffentlichungsumgebungen für beide Zugriffe.

Die Anforderung eines gemeinsamen Speichers führt zu den folgenden empfohlenen Topologien.

>[!NOTE]
>
>Bei AEM Communities wird [UGC nie repliziert](working-with-srp.md#ugc-never-replicated).
>
>Wenn die Bereitstellung keinen [gemeinsamen Speicher](working-with-srp.md)enthält, ist UGC nur in der Veröffentlichungs- oder Autoreninstanz von AEM sichtbar, in der sie eingegeben wurde.

>[!NOTE]
>
>Weitere Informationen zur AEM-Plattform finden Sie unter [Empfohlene Bereitstellungen](../../help/sites-deploying/recommended-deploys.md) und [Einführung in die AEM-Plattform](../../help/sites-deploying/data-store-config.md).

## zur Herstellung {#for-production}

Die Schaffung eines gemeinsamen Speicherplatzes für UGC ist unverzichtbar, und daher hängt der zugrunde liegende Einsatz von seiner Fähigkeit ab, einen gemeinsamen Speicher zu unterstützen.

Zwei Beispiele:

1) Wenn das erwartete UGC-Volumen hoch ist und eine lokale MongoDB-Instanz möglich ist, dann wäre die Auswahl [MSRP](msrp.md).

2) Für eine optimale Leistung bei Seiteninhalten würde die Auswahl einer [Veröffentlichungsfarm](../../help/sites-deploying/recommended-deploys.md#tarmk-farm) und eines [ASRP](asrp.md) eine optimale Skalierung von UGC bei relativ unkomplizierten Vorgängen ermöglichen.

Für beide kann die Bereitstellung auf einem beliebigen OAK-Mikrokernel basieren.

Um den passenden gemeinsamen Store auszuwählen, sollten Sie die einzigartigen [Eigenschaften](working-with-srp.md#characteristics-of-srp-options) jedes einzelnen sorgfältig berücksichtigen.

Weitere Informationen zu Oak-Mikrokernen finden Sie unter [Empfohlene Bereitstellungen](../../help/sites-deploying/recommended-deploys.md).

### TarMK-Veröffentlichungsfarm {#tarmk-publish-farm}

Wenn die Topologie eine Veröffentlichungsfarm ist, sind relevante Themen von Bedeutung

* [Benutzersynchronisierung](sync.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)

### Empfohlen: DSRP, MSRP oder ASRP {#recommended-dsrp-msrp-or-asrp}

| MicroKernel | SITE-INHALT | BENUTZER GENERIERTE INHALTE | LAGERRESSOURCENANBIETER | HÄUFIG GESPEICHERT |
|-------------|------------------------|----------------------------------|---------------------------|---------------|
| beliebig | JCR | MySQL | DSRP | Ja |
| beliebig | JCR | MongoDB | MSRP | Ja |
| beliebig | JCR | Adobe On-Demandstorage | ASRP | Ja |

### JSRP {#jsrp}


| Bereitstellung | SITE-INHALT | BENUTZER GENERIERTE INHALTE | LAGERRESSOURCENANBIETER | HÄUFIG GESPEICHERT |
|----------------------|------------------------|----------------------------------|---------------------------|---------------------------------|
| TarMK Farm (Standard) | JCR | JCR | JSRP | Nein |
| Oak-Cluster | JCR | JCR | JSRP | Nur Yesfor-Veröffentlichungsumgebung |

## für Entwicklung {#for-development}

Bei Nicht-Produktionsumgebungen bietet [JSRP](jsrp.md) eine einfache Möglichkeit, eine Entwicklungsumgebung mit einer Autoreninstanz und einer Veröffentlichungsinstanz einzurichten.

Bei Auswahl von [ASRP](asrp.md), [DSRP](dsrp.md) oder [MSRP](msrp.md) für die Produktion ist es auch möglich, eine ähnliche Entwicklungsumgebung mit Adobe On-Demand-Speicher oder MongoDB einzurichten. Ein Beispiel finden Sie unter [Wie Sie MongoDB für Demo](demo-mongo.md)einrichten.

## Verweise {#references}

* [Benutzersynchronisierung](sync.md)

   Behandelt die Synchronisierung von Benutzerdaten zwischen Instanzen im Veröffentlichungsmodus.

* [Verwalten von Benutzern und Benutzergruppen](users.md)

   Erläutert die Rollen von Benutzern und Benutzergruppen in der Autor- und Veröffentlichungsumgebung.

* UGC [Common Store](working-with-srp.md)

   Beschreibt die Speicherung von Community-Inhalten, die vom Site-Inhalt getrennt sind

* [Knotenspeicher und Datenspeicher](../../help/sites-deploying/data-store-config.md)

   Grundsätzlich wird der Site-Inhalt in einem Node Store gespeichert. Bei Assets kann ein Datenspeicher konfiguriert werden, um Binärdaten zu speichern. Bei Communities muss ein gemeinsamer Store zur Auswahl des SRP konfiguriert werden.

* [Speicherelemente in AEM 6.3](../../help/sites-deploying/storage-elements-in-aem-6.md)

   Beschreibt die beiden Knotenspeicherimplementierungen: Tar und MongoDB.
