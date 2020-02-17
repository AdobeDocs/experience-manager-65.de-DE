---
title: AEM Repo Tool
seo-title: AEM Repo Tool
description: Das AEM Repo Tool ist eine einfache Lösung, mit der Sie JCR-Inhalte ähnlich wie bei FTP über die Befehlszeile zwischen Ihrem lokalen Dateisystem und dem AEM-Server übertragen können. Das AEM Repo Tool ähnelt dem Jackrabbit FileVault-Tool, ist aber schneller, hat minimale Abhängigkeiten und besteht aus einem einfachen Bash-Skript.
seo-description: Das AEM Repo Tool ist eine einfache Lösung, mit der Sie JCR-Inhalte ähnlich wie bei FTP über die Befehlszeile zwischen Ihrem lokalen Dateisystem und dem AEM-Server übertragen können. Das AEM Repo Tool ähnelt dem Jackrabbit FileVault-Tool, ist aber schneller, hat minimale Abhängigkeiten und besteht aus einem einfachen Bash-Skript.
uuid: 6c4a3504-e8e8-46c0-83cb-c18d9791f93e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: 7de7b2f9-770e-4af3-8a31-c7b4de64fd43
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# AEM Repo Tool{#aem-repo-tool}

Das AEM Repo Tool ist eine einfache Lösung, mit der Sie JCR-Inhalte ähnlich wie bei FTP über die Befehlszeile zwischen Ihrem lokalen Dateisystem und dem AEM-Server übertragen können. The AEM Repo Tool is similar to the [Jackrabbit FileVault tool](/help/sites-developing/ht-vlttool.md), but is faster, has minimal dependencies, and is a simple bash script.

Dieses Tool vereinfacht die Dateiübertragung für Entwickler und lässt sich auch in IntelliJ und Eclipse integrieren, um die Entwicklung noch effizienter zu gestalten.

## Überblick {#overview}

For a given path inside a `jcr_root` filevault structure on the filesystem, AEM Repo Tool creates a package with a single filter for the entire subtree and pushes that to the server (similar to FTP `put`), fetches it from the server ( `get`) or compares the differences ( `status` and `diff`).

The tool does not support multiple filter paths or FileVault&#39;s `filter.xml`.

>[!CAUTION]
>
>Beachten Sie, dass das AEM Repo Tool immer die gesamte angegebene Datei bzw. das gesamte angegebene Verzeichnis überschreibt.

## Download und Dokumentation {#download-and-documentation}

The [AEM Repo Tool is available on GitHub via this link](https://github.com/Adobe-Marketing-Cloud/tools/tree/master/repo) along with detailed installation and usage instructions.

Wenn Sie den Quellcode des AEM Repo Tools herunterladen möchten, sehen Sie sich das unten verlinkte GitHub-Projekt an.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub

* [Open Tools-Projekt auf GitHub](https://github.com/Adobe-Marketing-Cloud/tools)
* Laden Sie das Projekt als [ZIP-Datei](https://github.com/Adobe-Marketing-Cloud/tools/archive/master.zip) herunter

