---
title: Content-Disposition-Filter
seo-title: Content-Disposition-Filter
description: Erfahren Sie, wie Sie den Filter "Inhaltsanzeige"verwenden, um XSS-Angriffe zu verhindern.
seo-description: Erfahren Sie, wie Sie den Filter "Inhaltsanzeige"verwenden, um XSS-Angriffe zu verhindern.
uuid: 145a88e0-9fa8-42db-b189-eda507c33049
contentOwner: trushton
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: Security
discoiquuid: badfaa18-472e-4777-a7dc-9c28441b38b7
exl-id: 1c3d0d48-5c31-42a8-8698-922d7c2127e9
translation-type: tm+mt
source-git-commit: cd895fcab5adce600ce230fb6867392e45963c16
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 33%

---

# Content-Disposition-Filter {#content-disposition-filter}

Der Content-Disposition-Filter ist eine Sicherheitsfunktion zum Schutz vor XSS-Angriffen auf SVG-Dateien.

Nach der Installation blockiert der Filter den Zugriff auf alle Assets. Beispielsweise konnte eine PDF-Datei nicht online Ansicht werden. In diesem Abschnitt wird beschrieben, wie Sie den Filter Ihren Anforderungen entsprechend konfigurieren.

## Konfigurieren des Content-Disposition-Filters {#configure-content-disposition-filter}

Sie können den Filter [Apache Sling Content Disposition in GitHub](https://github.com/apache/sling-org-apache-sling-security/blob/master/src/main/java/org/apache/sling/security/impl/ContentDispositionFilterConfiguration.java) Ansicht haben.

Die Optionen für den Content-Disposition-Filter bieten die folgenden Funktionen:

* **Pfadtrennungspfade:** eine Liste von Pfaden, auf die der Filter angewendet wird, gefolgt von einer Liste von MIME-Typen, die auf diesem Pfad ausgeschlossen werden sollen. Dieser Pfad muss ein absoluter Pfad sein und kann am Ende einen Platzhalter (`*`) enthalten, damit jeder Ressourcenpfad mit dem angegebenen Pfadpräfix übereinstimmt. Beispiel: `/content/*:image/jpeg,image/svg+xml` wird der Filter auf jeden Knoten in&quot;/content angewendet? außer jpg und svg

* **Ausgeschlossene Ressourcenpfade:** Eine Liste ausgeschlossener Ressourcen. Jeder Ressourcenpfad muss als absoluter und voll qualifizierter Pfad angegeben werden. Präfixabgleiche/Platzhalter werden nicht unterstützt.

* **Für alle Ressourcenpfade aktivieren:** Dieses Flag steuert, ob dieser Filter für alle Pfade aktiviert werden soll, mit Ausnahme der ausgeschlossenen Pfade, die von Ausgeschlossenen Ressourcenpfaden definiert werden. Ist diese Option auf „true“ festgelegt, werden die Content-Disposition-Pfade ignoriert. Unabhängig von der Konfiguration werden nur Ressourcenpfade behandelt, die eine Eigenschaft mit dem Namen `jcr:data` oder `jcr:content/jcr:data` enthalten.
