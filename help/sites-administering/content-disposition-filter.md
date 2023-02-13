---
title: Content-Disposition-Filter
seo-title: Content Disposition Filter
description: Erfahren Sie, wie Sie mit dem Content-Disposition-Filter XSS-Angriffe verhindern können.
seo-description: Learn how to use the Content Disposition Filter to prevent XSS attacks.
uuid: 145a88e0-9fa8-42db-b189-eda507c33049
contentOwner: trushton
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: Security
discoiquuid: badfaa18-472e-4777-a7dc-9c28441b38b7
exl-id: 1c3d0d48-5c31-42a8-8698-922d7c2127e9
source-git-commit: d1fc2ff44378276522c2ff3208f5b3bdc4484bba
workflow-type: ht
source-wordcount: '239'
ht-degree: 100%

---

# Content-Disposition-Filter {#content-disposition-filter}

Der Content-Disposition-Filter ist eine Sicherheitsfunktion zum Schutz vor XSS-Angriffen auf SVG-Dateien.

Nach der Installation blockiert der Filter den Zugriff auf alle Assets. Sie können dann beispielsweise keine PDF-Dateien online anzeigen. In diesem Abschnitt wird beschrieben, wie Sie den Filter Ihren Anforderungen entsprechend konfigurieren.

## Konfigurieren des Content-Disposition-Filters {#configure-content-disposition-filter}

Sie können den [Apache Sling Content Disposition Filter in GitHub](https://github.com/apache/sling-org-apache-sling-security/blob/master/src/main/java/org/apache/sling/security/impl/ContentDispositionFilterConfiguration.java) anzeigen.

Die Optionen für den Content-Disposition-Filter bieten die folgenden Funktionen:

* **„Content Disposition Paths“ (Content-Disposition-Pfade):** Liste von Pfaden, auf die der Filter angewendet wird, gefolgt von einer Liste der MIME-Typen, die für diesen Pfad ausgeschlossen werden sollen. Dieser Pfad muss ein absoluter Pfad sein und kann einen Platzhalter (`*`) am Ende enthalten, um alle Ressourcenpfade mit dem angegebenen Pfadpräfix abzugleichen. So wird der Filter mit „`/content/*:image/jpeg,image/svg+xml`“ beispielsweise auf alle Knoten unter „`/content?`“ angewendet, mit Ausnahme von JPEG- und SVG-Bildern.

* **„Excluded Resource Paths“ (Ausgeschlossene Ressourcenpfade):** Eine Liste der ausgeschlossenen Ressourcen. Alle Ressourcenpfade müssen als absolute und voll qualifizierte Pfade angegeben werden. Präfixabgleiche/Platzhalter werden nicht unterstützt.

* **„Enable For All Resource Paths“ (Für alle Ressourcenpfade aktivieren):** Dieses Flag steuert, ob dieser Filter für alle Pfade aktiviert werden soll. Ausgenommen sind dabei die durch „Excluded Resource Paths“ definierten ausgeschlossenen Pfade. Ist diese Option auf „true“ festgelegt, werden die Content-Disposition-Pfade ignoriert. Unabhängig von der Konfiguration werden nur Ressourcenpfade berücksichtigt, die eine Eigenschaft namens `jcr:data` oder `jcr:content/jcr:data` enthalten.
