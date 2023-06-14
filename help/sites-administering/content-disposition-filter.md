---
title: Content-Disposition-Filter
description: Erfahren Sie, wie Sie mit dem Content-Disposition-Filter XSS-Angriffe verhindern können.
uuid: 145a88e0-9fa8-42db-b189-eda507c33049
contentOwner: trushton
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: Security
discoiquuid: badfaa18-472e-4777-a7dc-9c28441b38b7
exl-id: 1c3d0d48-5c31-42a8-8698-922d7c2127e9
source-git-commit: 78c584db8c35ea809048580fe5b440a0b73c8eea
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 34%

---

# Content-Disposition-Filter {#content-disposition-filter}

Der Inhaltsdispositionsfilter ist eine Sicherheitsfunktion gegen XSS-Angriffe auf SVG-Dateien.

Nach der Installation blockiert der Filter den Zugriff auf alle Assets. Sie können dann beispielsweise keine PDF-Dateien online anzeigen. In diesem Abschnitt wird beschrieben, wie Sie den Filter nach Bedarf konfigurieren.

## Inhaltsdispositionsfilter konfigurieren {#configure-content-disposition-filter}

Sie können den [Apache Sling Content Disposition Filter in GitHub](https://github.com/apache/sling-org-apache-sling-security/blob/master/src/main/java/org/apache/sling/security/impl/ContentDispositionFilterConfiguration.java) anzeigen.

Die Optionen für den Content-Disposition-Filter bieten die folgenden Funktionen:

* **Content Disposition Paths:** Eine Liste der Pfade, auf die der Filter angewendet wird, gefolgt von einer Liste der MIME-Typen, die für diesen Pfad ausgeschlossen werden sollen. Dieser Pfad muss ein absoluter Pfad sein und kann einen Platzhalter (`*`), um jeden Ressourcenpfad mit dem angegebenen Pfadpräfix abzugleichen. Beispiel: `/content/*:image/jpeg,image/svg+xml` wendet den Filter auf jeden Knoten in `/content?` mit Ausnahme von JPG- und SVG-Bildern.

* **Ausgeschlossene Ressourcenpfade:** Eine Liste der ausgeschlossenen Ressourcen. Jeder Ressourcenpfad muss als absoluter und vollständig qualifizierter Pfad angegeben werden. Präfixabgleiche/Platzhalter werden nicht unterstützt.

* **Aktivieren Sie für alle Ressourcenpfade:** Diese Markierung steuert, ob dieser Filter für alle Pfade aktiviert werden soll, mit Ausnahme der ausgeschlossenen Pfade, die von Ausgeschlossenen Ressourcenpfaden definiert werden. Wenn dieses Flag auf &quot;true&quot;gesetzt wird, werden die Inhaltserstellungspfade ignoriert. Unabhängig von der Konfiguration werden nur Ressourcenpfade berücksichtigt, die eine Eigenschaft namens `jcr:data` oder `jcr:content/jcr:data` enthalten.
