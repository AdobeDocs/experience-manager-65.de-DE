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
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Content-Disposition-Filter{#content-disposition-filter}

Der Content-Disposition-Filter ist eine Sicherheitsfunktion zum Schutz vor XSS-Angriffen auf SVG-Dateien.

Nach der Installation blockiert der Filter den Zugriff auf alle Assets. Sie können dann beispielsweise keine PDF-Dateien online anzeigen. In diesem Abschnitt wird beschrieben, wie Sie den Filter Ihren Anforderungen entsprechend konfigurieren.

## Konfigurieren des Content-Disposition-Filters {#configure-content-disposition-filter}

You can view the [Apache Sling Content Disposition Filter in GitHub](https://github.com/apache/sling-org-apache-sling-security/blob/master/src/main/java/org/apache/sling/security/impl/ContentDispositionFilterConfiguration.java).

Die Optionen für den Content-Disposition-Filter bieten die folgenden Funktionen:

* Pfade zur Inhaltsanzeige: eine Liste der Pfade, auf die der Filter angewendet wird, gefolgt von einer Liste der Mime-Typen, die auf diesem Pfad ausgeschlossen werden sollen. Dieser Pfad muss ein absoluter Pfad sein und kann am Ende einen Platzhalter (&#39;&amp;ast;&#39;) enthalten, damit jeder Ressourcenpfad mit dem angegebenen Pfadpräfix übereinstimmt. Beispiel: /content/&amp;ast;:image/jpeg,image/svg+xml &quot; wendet den Filter auf jeden Knoten in /content mit Ausnahme von jpg und svg images an

* „Excluded Resource Paths“ (Ausgeschlossene Ressourcenpfade): Eine Liste der ausgeschlossenen Ressourcen. Alle Ressourcenpfade müssen als absolute und voll qualifizierte Pfade angegeben werden. Präfixabgleiche/Platzhalter werden nicht unterstützt.

* „Enable For All Resource Paths“ (Für alle Ressourcenpfade aktivieren): Diese Kennzeichnung steuert, ob dieser Filter für alle Pfade aktiviert werden soll. Ausgenommen sind dabei die durch „Excluded Resource Paths“ definierten ausgeschlossenen Pfade. Ist diese Option auf „true“ festgelegt, werden die Content-Disposition-Pfade ignoriert. Unabhängig von der Konfiguration werden nur Ressourcenpfade behandelt, die eine Eigenschaft mit dem Namen &quot;jcr:data&quot;oder &quot;jcr:content jcr:data&quot;enthalten.

