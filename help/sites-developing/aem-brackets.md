---
title: AEM Brackets-Erweiterung
seo-title: AEM Brackets Extension
description: AEM Brackets-Erweiterung
seo-description: null
uuid: 2f0dfa42-eb34-44ae-90eb-b5f321c03b79
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: 8231a30a-dcb7-4156-bb45-c5a23e5b56ef
exl-id: 829d8256-b415-4a44-a353-455ac16950f3
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 55%

---

# AEM Brackets-Erweiterung{#aem-brackets-extension}

## Übersicht {#overview}

Die AEM Brackets-Erweiterung bietet einen reibungslosen Workflow für die Bearbeitung von AEM-Komponenten und Client-Bibliotheken und nutzt die Leistungsfähigkeit des [Brackets](https://brackets.io/)-Code-Editors, der den Zugriff auf Photoshop-Dateien und -Ebenen über den Code-Editor ermöglicht. Die durch die Erweiterung gebotene einfache Synchronisation (kein Maven oder File Vault erforderlich) erhöht die Effizienz der Entwickler und hilft auch Frontend-Entwicklern mit begrenztem AEM-Wissen, an Projekten teilzunehmen. Diese Erweiterung bietet auch Unterstützung für die [HTML Template Language (HTL)](https://docs.adobe.com/content/help/de-DE/experience-manager-htl/using/overview.html), wodurch die Komplexität von JSP entfällt, um die Komponentenentwicklung einfacher und sicherer zu machen.

![chlimage_1-53](assets/chlimage_1-53a.png)

### Funktionen {#features}

Die Hauptmerkmale der AEM Brackets-Erweiterung sind:

* Automatisierte Synchronisierung geänderter Dateien mit der AEM Entwicklungsinstanz.
* Manuelle bidirektionale Synchronisation von Dateien und Ordnern.
* Vollständige Inhaltspaketsynchronisierung des Projekts.
* HTL-Code-Abschluss für Ausdrücke und `data-sly-*` -Blockanweisungen.

Zusätzlich bietet Brackets viele nützliche Funktionen für AEM-Frontend-Entwickler:

* Photoshop-Dateiunterstützung zum Extrahieren von Informationen aus einer PSD-Datei, wie Schichten, Maße, Farben, Schriftarten, Texte usw.
* Codehinweise aus der PSD, um diese extrahierten Informationen im Code einfach wiederzuverwenden.
* CSS-Präprozessor-Unterstützung, wie LESS und SCSS.
* Und Hunderte zusätzlicher Erweiterungen, die spezifischere Anforderungen abdecken.

## Installation {#installation}

### Brackets {#brackets}

Die AEM Brackets-Erweiterung unterstützt Brackets Version 1.0 oder höher.

Laden Sie die neueste Brackets-Version von herunter. [brackets.io](https://brackets.io/).

### Die Erweiterung {#the-extension}

Um die Erweiterung zu installieren, gehen Sie wie folgt vor:

1. Öffnen Sie Brackets. Wählen Sie im Menü **Datei** den **Extension Manager...**
1. Geben Sie **AEM** in die Suchleiste ein und suchen Sie nach **AEM Brackets-Erweiterung**.

   ![chlimage_1-54](assets/chlimage_1-54a.png)

1. Klicken Sie auf **Installieren**.
1. Schließen Sie das Dialogfeld und den Extension Manager nach Abschluss der Installation.

## Erste Schritte {#getting-started}

### Das Content-Package-Projekt {#the-content-package-project}

Nachdem die Erweiterung installiert wurde, können Sie mit der Entwicklung von AEM-Komponenten beginnen, indem Sie mit Brackets einen content-package-Ordner aus Ihrem Dateisystem öffnen.

Das Projekt muss mindestens enthalten:

1. a `jcr_root` Ordner (z. B. `myproject/jcr_root`)

1. a `filter.xml` Datei (z. B. `myproject/META-INF/vault/filter.xml`); Weitere Informationen zur Struktur der `filter.xml` Datei finden Sie unter [Definition von Workspace-Filtern](https://jackrabbit.apache.org/filevault/filter.html).

Im Menü **Datei** von Brackets wählen Sie **Ordner öffnen...** und wählen Sie entweder den Ordner `jcr_root` oder den übergeordneten Projektordner.

>[!NOTE]
>
>Wenn Sie kein eigenes Projekt mit einem Inhaltspaket haben, können Sie die [HTL TodoMVC-Beispiel](https://github.com/Adobe-Marketing-Cloud/aem-sightly-sample-todomvc). Klicken Sie auf GitHub auf **ZIP herunterladen**, extrahieren Sie die Dateien lokal und öffnen Sie wie oben beschrieben die `jcr_root` Ordner in Brackets. Gehen Sie dann wie folgt vor, um die **Projekteinstellungen** und laden Sie schließlich das gesamte Paket in Ihre AEM-Entwicklungsinstanz hoch, indem Sie eine **Inhaltspaket exportieren** wie im Abschnitt Vollständige Inhaltspaketsynchronisierung weiter unten beschrieben.
>
>Nach diesen Schritten sollten Sie auf die `/content/todo.html` URL auf Ihrer AEM Entwicklungsinstanz. Sie können Änderungen am Code in Brackets vornehmen und sehen, wie die Änderungen nach einer Aktualisierung im Webbrowser sofort mit dem AEM-Server synchronisiert wurden.

### Projekteinstellungen {#project-settings}

Um Ihren Inhalt mit einer AEM-Entwicklungsinstanz zu synchronisieren, müssen Sie Ihre Projekteinstellungen definieren. Gehen Sie dazu zum **AEM** Menü und Auswahl **Projekteinstellungen...**

![chlimage_1-55](assets/chlimage_1-55a.png)

Die Projekteinstellungen erlauben die Definition von Folgendem:

1. Die Server-URL (z. B. `http://localhost:4502`)
1. Ob Server ohne gültiges HTTPS-Zertifikat toleriert werden sollen (deaktivieren Sie diese Option, falls nicht erforderlich)
1. Benutzername, der für die Synchronisierung von Inhalten verwendet wird (z. B. `admin`)
1. Das Kennwort des Benutzers (z. B. `admin`)

## Synchronisieren von Inhalten {#synchronizing-content}

Die AEM Brackets-Erweiterung bietet die folgenden Arten der Inhaltssynchronisierung für Dateien und Ordner, die durch die in `filter.xml`:

### Automatisierte Synchronisierung von geänderten Dateien {#automated-synchronization-of-changed-files}

Diese synchronisiert nur Änderungen von Brackets mit der AEM-Instanz, aber niemals umgekehrt.

### Manuelle bidirektionale Synchronisierung {#manual-bidirectional-synchronization}

Öffnen Sie im Projekt-Explorer das Kontextmenü, indem Sie mit der rechten Maustaste auf eine beliebige Datei oder einen beliebigen Ordner klicken, und **Export auf Server** oder **Import von Server** -Optionen aufgerufen werden.

![chlimage_1-56](assets/chlimage_1-56a.png)

>[!NOTE]
>
>Wenn sich der ausgewählte Eintrag außerhalb der `jcr_root` Ordner, die **Export auf Server** und **Import von Server** Kontextmenüeinträge sind deaktiviert.

### Vollständige Content-Package-Synchronisierung {#full-content-package-synchronization}

Im **AEM** Menü, **Inhaltspaket exportieren** oder **Inhaltspaket importieren** -Optionen ermöglichen die Synchronisierung des gesamten Projekts mit dem Server.

![chlimage_1-57](assets/chlimage_1-57a.png)

### Synchronisierungsstatus {#synchronization-status}

Die AEM Brackets-Erweiterung verfügt über ein Benachrichtigungssymbol in der Symbolleiste rechts im Fenster „Brackets“, das den Status der letzten Synchronisierung angibt:

* grün - alle Dateien wurden erfolgreich synchronisiert
* blau - eine Synchronisierung wird ausgeführt
* gelb - einige der Dateien wurden nicht synchronisiert
* rot - keine Dateien wurden synchronisiert

Wenn Sie auf das Benachrichtigungssymbol klicken, wird das Dialogfeld „Synchronisierungsstatusbericht“ geöffnet, das den Status aller synchronisierten Dateien anzeigt.

![chlimage_1-58](assets/chlimage_1-58a.png)

>[!NOTE]
>
>Nur Inhalt, der in den Filterregeln von `filter.xml` als enthalten gekennzeichnet ist, wird unabhängig von der verwendeten Synchronisierungsmethode synchronisiert.
>
>Zusätzlich `.vltignore` -Dateien werden zum Ausschließen von Inhalten aus der Synchronisierung mit und aus dem Repository unterstützt.

## Bearbeiten von HTL-Code {#editing-htl-code}

Die AEM Brackets-Erweiterung bietet auch eine automatische Vervollständigung, um das Schreiben von HTL-Attributen und -Ausdrücken zu vereinfachen.

### Automatische Vervollständigung von Attributen {#attribute-auto-completion}

1. Geben Sie in einem HTML-Attribut `sly` ein. Das Attribut wird automatisch zu `data-sly-` - vervollständigt.
1. Wählen Sie das HTL-Attribut in der Dropdown-Liste aus.

### Automatische Vervollständigung von Ausdrücken {#expression-auto-completion}

Innerhalb eines Ausdrucks `${}`, werden allgemeine Variablennamen automatisch vervollständigt.

## Weitere Informationen {#more-information}

Die AEM Brackets-Erweiterung ist ein Open-Source-Projekt, das von [Adobe Marketing Cloud](https://github.com/Adobe-Marketing-Cloud) unter der Apache-Lizenz Version 2.0 auf GitHub gehostet wird:

* Code-Repository: [https://github.com/Adobe-Marketing-Cloud/aem-sightly-brackets-extension](https://github.com/Adobe-Marketing-Cloud/aem-sightly-brackets-extension)
* Apache-Lizenz, Version 2.0: [https://www.apache.org/licenses/LICENSE-2.0.html](https://www.apache.org/licenses/LICENSE-2.0.html)

Der Brackets-Code-Editor ist auch ein Open-Source-Projekt, das auf GitHub vom [Adobe Systems Incorporated](https://github.com/adobe) -Organisation:

* Code-Repository: [https://github.com/adobe/brackets](https://github.com/adobe/brackets)

Sie können gern dazu beitragen!
