---
title: Content-Disposition-Filter
description: Erfahren Sie, wie Sie mit dem Content-Disposition-Filter XSS-Angriffe verhindern können.
contentOwner: trushton
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: Security
exl-id: 1c3d0d48-5c31-42a8-8698-922d7c2127e9
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 100%

---

# Content-Disposition-Filter {#content-disposition-filter}

Der Content-Disposition-Filter ist eine Sicherheitsfunktion gegen XSS-Angriffe auf SVG-Dateien.

Nach der Installation blockiert der Filter den Zugriff auf alle Assets. Sie können dann beispielsweise keine PDF-Dateien online anzeigen. In diesem Abschnitt wird beschrieben, wie Sie den Filter Ihren Bedürfnissen entsprechend konfigurieren können.

## Konfigurieren des Content-Disposition-Filters {#configure-content-disposition-filter}

Sie können den [Apache Sling Content Disposition Filter in GitHub](https://github.com/apache/sling-org-apache-sling-security/blob/master/src/main/java/org/apache/sling/security/impl/ContentDispositionFilterConfiguration.java) anzeigen.

Die Optionen für den Content-Disposition-Filter bieten die folgenden Funktionen:

* **Content-Disposition-Pfade:** Eine Liste der Pfade, auf die der Filter angewendet wird, gefolgt von einer Liste der MIME-Typen, die für diesen Pfad ausgeschlossen werden sollen. Dieser Pfad muss ein absoluter Pfad sein und kann am Ende einen Platzhalter (`*`) enthalten, um mit jedem Ressourcenpfad mit dem angegebenen Pfadpräfix übereinzustimmen. So wird der Filter mit „`/content/*:image/jpeg,image/svg+xml`“ beispielsweise auf alle Knoten unter „`/content?`“ angewendet, mit Ausnahme von JPEG- und SVG-Bildern.

* **Ausgeschlossene Ressourcenpfade:** Eine Liste der ausgeschlossenen Ressourcen. Alle Ressourcenpfade müssen als absolute und voll qualifizierte Pfade angegeben werden. Präfixabgleiche/Platzhalter werden nicht unterstützt.

* **Für alle Ressourcenpfade aktivieren:** Diese Markierung steuert, ob dieser Filter für alle Pfade aktiviert werden soll. Ausgenommen sind dabei die durch „Ausgeschlossene Ressourcenpfade“ definierten ausgeschlossenen Pfade. Ist diese Markierung auf „true“ festgelegt, werden die Content-Disposition-Pfade ignoriert. Unabhängig von der Konfiguration werden nur Ressourcenpfade berücksichtigt, die eine Eigenschaft namens `jcr:data` oder `jcr:content/jcr:data` enthalten.
