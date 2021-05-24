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
exl-id: c46c9f0c-b0d2-4f2f-b95c-90fd3ced32a9
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 80%

---

# AEM Repo Tool{#aem-repo-tool}

Das AEM Repo Tool ist eine einfache Lösung, mit der Sie JCR-Inhalte ähnlich wie bei FTP über die Befehlszeile zwischen Ihrem lokalen Dateisystem und dem AEM-Server übertragen können. Das AEM Repo Tool ähnelt dem [Jackrabbit FileVault Tool](/help/sites-developing/ht-vlttool.md), ist jedoch schneller, weist minimale Abhängigkeiten auf und ist ein einfaches Bash-Skript.

Dieses Tool vereinfacht die Dateiübertragung für Entwickler und lässt sich auch in IntelliJ und Eclipse integrieren, um die Entwicklung noch effizienter zu gestalten.

## Überblick {#overview}

Für einen bestimmten Pfad innerhalb einer `jcr_root` filevault-Struktur im Dateisystem erstellt AEM Repo Tool ein Paket mit einem einzigen Filter für die gesamte Unterstruktur und pusht es auf den Server (ähnlich wie FTP `put`), ruft es vom Server ab ( `get`) oder vergleicht die Unterschiede ( `status` und `diff`).

Mehrere Filterpfade werden vom Tool ebenso wenig unterstützt wie `filter.xml` von FileVault.

>[!CAUTION]
>
>Beachten Sie, dass das AEM Repo Tool immer die gesamte angegebene Datei bzw. das gesamte angegebene Verzeichnis überschreibt.

## Download und Dokumentation   {#download-and-documentation}

Das [AEM Repo Tool ist unter diesem Link auf GitHub verfügbar](https://github.com/Adobe-Marketing-Cloud/tools/tree/master/repo), zusammen mit detaillierten Installations- und Nutzungsanleitungen.

Wenn Sie den Quell-Code des AEM Repo Tools herunterladen möchten, sehen Sie sich das unten verlinkte GitHub-Projekt an.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub.

* [Öffnen Sie das Projekt „Tools“ auf GitHub.](https://github.com/Adobe-Marketing-Cloud/tools)
* Laden Sie das Projekt als [ZIP-Datei](https://github.com/Adobe-Marketing-Cloud/tools/archive/master.zip) herunter.
