---
title: AEM Repo Tool
description: Das AEM Repo Tool ist eine einfache Lösung, um JCR-Inhalte über eine mit FTP vergleichbare Befehlszeile zwischen Ihrem lokalen Dateisystem und dem AEM-Server zu übertragen. Das AEM Repo Tool ähnelt dem Jackrabbit FileVault-Tool, ist aber schneller, hat minimale Abhängigkeiten und besteht aus einem einfachen Bash-Skript.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
exl-id: c46c9f0c-b0d2-4f2f-b95c-90fd3ced32a9
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 74%

---

# AEM Repo Tool{#aem-repo-tool}

Das AEM Repo Tool ist eine einfache Lösung, mit der Sie JCR-Inhalte ähnlich wie bei FTP über die Befehlszeile zwischen Ihrem lokalen Dateisystem und dem AEM-Server übertragen können. Das AEM Repo Tool ähnelt dem [Jackrabbit FileVault-Tool](/help/sites-developing/ht-vlttool.md), ist aber schneller, hat minimale Abhängigkeiten und besteht aus einem einfachen Bash-Skript.

Dieses Tool vereinfacht die Übertragung von Dateien für Entwickler und kann auch in IntelliJ und Eclipse integriert werden, um die Entwicklung noch effizienter zu gestalten.

## Übersicht {#overview}

Das AEM Repo Tool erstellt für einen angegebenen Pfad in einer `jcr_root`-filevault-Struktur im Dateisystem ein Paket mit einem einzigen Filter für den gesamten untergeordneten Baum und pusht dieses Paket zum Server (ähnlich wie `put` bei FTP), ruft es vom Server ab (`get`) oder vergleicht die Unterschiede (`status` und `diff`).

Mehrere Filterpfade werden vom Tool ebenso wenig unterstützt wie `filter.xml` von FileVault.

>[!CAUTION]
>
>Das AEM Repo Tool überschreibt immer die gesamte angegebene Datei oder das angegebene Verzeichnis.

## Download und Dokumentation {#download-and-documentation}

Das [AEM Repo Tool ist unter diesem Link auf GitHub verfügbar](https://github.com/Adobe-Marketing-Cloud/tools/tree/master/repo), zusammen mit detaillierten Installations- und Nutzungsanleitungen.

Wenn Sie die Quelle des AEM Repo Tool herunterladen möchten, lesen Sie das unten verlinkte GitHub-Projekt.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub.

* [Öffnen Sie das Projekt „Tools“ auf GitHub.](https://github.com/Adobe-Marketing-Cloud/tools)
* Laden Sie das Projekt als [ZIP-Datei](https://github.com/Adobe-Marketing-Cloud/tools/archive/master.zip) herunter.
