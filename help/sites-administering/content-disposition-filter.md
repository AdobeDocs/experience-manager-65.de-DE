---
title: Content-Disposition-Filter
description: Erfahren Sie, wie Sie mit dem Content-Disposition-Filter XSS-Angriffe verhindern können.
contentOwner: trushton
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: Security
exl-id: 1c3d0d48-5c31-42a8-8698-922d7c2127e9
solution: Experience Manager, Experience Manager Sites
feature: Security
role: Admin
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: b1210526-416b-4ef6-bcc0-1692e99f30e9
    internal-label: Administration and security
subfeature_v2:
  - id: c35bc059-fd80-4a01-91a6-e48da3c76758
    internal-label: Security practices
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '244'
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
