---
title: AEM Repo Tool
description: Das AEM Repo Tool ist eine einfache Lösung, mit der Sie JCR-Inhalte ähnlich wie bei FTP über die Befehlszeile zwischen Ihrem lokalen Dateisystem und dem AEM-Server übertragen können. Das AEM Repo Tool ähnelt dem Jackrabbit FileVault-Tool, ist aber schneller, hat minimale Abhängigkeiten und besteht aus einem einfachen Bash-Skript.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
exl-id: c46c9f0c-b0d2-4f2f-b95c-90fd3ced32a9
solution: Experience Manager, Experience Manager Sites
feature: Developing,Developer Tools
role: Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: c5d917df-d8bd-5e97-a117-6dde1e9f7103
    internal-label: Developing
  - id: f2d27a5f-0d67-4d85-8a24-86a8d8a3574b
    internal-label: Developer tools
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 98%
---
# AEM Repo Tool{#aem-repo-tool}

Das AEM Repo Tool ist eine einfache Lösung, mit der Sie JCR-Inhalte ähnlich wie bei FTP über die Befehlszeile zwischen Ihrem lokalen Dateisystem und dem AEM-Server übertragen können. Das AEM Repo Tool ähnelt dem [Jackrabbit FileVault-Tool](/help/sites-developing/ht-vlttool.md), ist aber schneller, hat minimale Abhängigkeiten und besteht aus einem einfachen Bash-Skript.

Dieses Tool vereinfacht die Dateiübertragung für Entwickelnde und lässt sich auch in IntelliJ und Eclipse integrieren, um die Entwicklung noch effizienter zu gestalten.

## Übersicht {#overview}

Das AEM Repo Tool erstellt für einen angegebenen Pfad in einer `jcr_root`-filevault-Struktur im Dateisystem ein Paket mit einem einzigen Filter für den gesamten untergeordneten Baum und pusht dieses Paket zum Server (ähnlich wie `put` bei FTP), ruft es vom Server ab (`get`) oder vergleicht die Unterschiede (`status` und `diff`).

Mehrere Filterpfade werden vom Tool ebenso wenig unterstützt wie `filter.xml` von FileVault.

>[!CAUTION]
>
>Das AEM Repo Tool überschreibt immer die gesamte angegebene Datei oder das angegebene Verzeichnis.

## Download und Dokumentation {#download-and-documentation}

Das [AEM Repo Tool ist unter diesem Link auf GitHub verfügbar](https://github.com/Adobe-Marketing-Cloud/tools/tree/master/repo), zusammen mit detaillierten Installations- und Nutzungsanleitungen.

Wenn Sie die Quelle des AEM Repo Tools herunterladen möchten, sehen Sie sich das unten verlinkte GitHub-Projekt an.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub.

* [Projekttools auf GitHub öffnen](https://github.com/Adobe-Marketing-Cloud/tools)
* Laden Sie das Projekt als [ZIP-Datei](https://github.com/Adobe-Marketing-Cloud/tools/archive/master.zip) herunter.
