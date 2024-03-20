---
title: AEM Brackets-Erweiterung
description: Erfahren Sie, wie Sie die Adobe Experience Manager-Erweiterung für Brackets verwenden.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
exl-id: 829d8256-b415-4a44-a353-455ac16950f3
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '913'
ht-degree: 52%

---

# AEM Brackets-Erweiterung{#aem-brackets-extension}

## Übersicht {#overview}

Die AEM Brackets-Erweiterung bietet einen reibungslosen Arbeitsablauf zum Bearbeiten AEM Komponenten und Client-Bibliotheken und nutzt die Leistungsfähigkeit des [Brackets](https://brackets.io/) Code-Editor, der den Zugriff von im Code-Editor auf Photoshop-Dateien und -Ebenen ermöglicht. Die durch die Erweiterung gebotene einfache Synchronisation (kein Maven oder File Vault erforderlich) erhöht die Effizienz der Entwickler und hilft auch Frontend-Entwicklern mit begrenztem AEM-Wissen, an Projekten teilzunehmen. Diese Erweiterung bietet auch Unterstützung für die [HTML Template Language (HTL)](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html?lang=de), die JSP die Komplexität nimmt, um die Komponentenentwicklung einfacher und sicherer zu machen.

![chlimage_1-53](assets/chlimage_1-53a.png)

### Funktionen {#features}

Die wichtigsten Funktionen der AEM Brackets-Erweiterung sind:

* Automatische Synchronisierung geänderter Dateien mit der AEM-Entwicklungsinstanz
* Manuelle bidirektionale Synchronisierung von Dateien und Ordnern
* Vollständige Content-Package-Synchronisierung des Projekts
* HTL-Code-Vervollständigung für Ausdrücke und `data-sly-*`-Blockanweisungen.

Darüber hinaus bietet Brackets viele nützliche Funktionen für AEM Schriftartentwickler:

* Photoshop-Dateiunterstützung zum Extrahieren von Informationen aus einer PSD-Datei wie Ebenen, Messungen, Farben, Schriftarten, Texten usw.
* Codehinweise von der PSD, um diese extrahierten Informationen im Code einfach wiederzuverwenden.
* CSS-Präprozessor-Unterstützung wie LESS und SCSS.
* Hunderte von zusätzlichen Erweiterungen, die spezifischere Anforderungen abdecken.

## Installation {#installation}

### Brackets {#brackets}

Die AEM Brackets-Erweiterung unterstützt Brackets-Version 1.0 oder höher.

Laden Sie die neueste Brackets-Version von [brackets.io](https://brackets.io/) herunter.

### Die Erweiterung {#the-extension}

So installieren Sie die Erweiterung:

1. Öffnen Sie Brackets. Im Menü **Datei** auswählen **Extension Manager...**
1. Eingabe **AEM** in der Suchleiste und suchen Sie nach **AEM Brackets-Erweiterung**.

   ![chlimage_1-54](assets/chlimage_1-54a.png)

1. Klicken Sie auf **Installieren**.
1. Schließen Sie das Dialogfeld und den Extension Manager nach Abschluss der Installation.

## Erste Schritte {#getting-started}

### Das Inhaltspaket-Projekt {#the-content-package-project}

Nachdem die Erweiterung installiert wurde, können Sie mit der Entwicklung AEM Komponenten beginnen, indem Sie mit Brackets einen Ordner mit Inhaltspaketen aus Ihrem Dateisystem öffnen.

Das Projekt muss mindestens Folgendes enthalten:

1. a `jcr_root` Ordner (z. B. `myproject/jcr_root`)

1. a `filter.xml` -Datei (z. B. `myproject/META-INF/vault/filter.xml`); für weitere Details zur Struktur der `filter.xml` -Datei sehen Sie die [Definition von Workspace-Filtern](https://jackrabbit.apache.org/filevault/filter.html).

Im Menü **Datei** von Brackets wählen Sie **Ordner öffnen...** und wählen Sie entweder den Ordner `jcr_root` oder den übergeordneten Projektordner.

>[!NOTE]
>
>Wenn Sie kein eigenes Projekt mit einem Inhaltspaket haben, können Sie die [HTL TodoMVC-Beispiel](https://github.com/Adobe-Marketing-Cloud/aem-sightly-sample-todomvc). Klicken Sie auf GitHub auf **Zip-Datei herunterladen**, extrahieren Sie die Dateien lokal und öffnen Sie wie oben beschrieben den Ordner `jcr_root` in Brackets. Führen Sie dann die folgenden Schritte aus, um die **Projekteinstellungen** einzurichten, und laden Sie schließlich das gesamte Paket in Ihre AEM-Entwicklungsinstanz hoch, indem Sie **das Content-Package exportieren**, wie weiter unten im Abschnitt „Vollständige Content-Package-Synchronisierung“ beschrieben.
>
>Nach diesen Schritten sollten Sie in der Lage sein, auf die URL `/content/todo.html` in Ihrer AEM-Entwicklungsinstanz zuzugreifen, und Sie können Änderungen am Code in Brackets vornehmen und sehen, wie nach einer Aktualisierung im Webbrowser die Änderungen sofort mit dem AEM-Server synchronisiert wurden.

### Projekteinstellungen {#project-settings}

Um Ihre Inhalte von und zu einer AEM Entwicklungsinstanz zu synchronisieren, müssen Sie Ihre Projekteinstellungen definieren. Dies erreichen Sie, indem Sie das Menü **AEM** aufrufen und **Projekteinstellungen** wählen.

![chlimage_1-55](assets/chlimage_1-55a.png)

In den Projekteinstellungen können Sie Folgendes definieren:

1. Die Server-URL (z. B. `http://localhost:4502`)
1. Ob Server ohne gültiges HTTPS-Zertifikat toleriert werden sollen (deaktivieren Sie diese Option, falls nicht erforderlich)
1. Der Benutzername, der zum Synchronisieren von Inhalten verwendet wird (z. B. `admin`)
1. Das Kennwort des Benutzers (z. B. `admin`)

## Synchronisieren von Inhalten {#synchronizing-content}

Die AEM Brackets-Erweiterung bietet folgende Arten der Inhaltssynchronisierung für Dateien und Ordner, die von den in `filter.xml` definierten Filterregeln zugelassen sind:

### Automatisierte Synchronisierung geänderter Dateien {#automated-synchronization-of-changed-files}

Dadurch werden nur Änderungen von Brackets mit der AEM-Instanz synchronisiert, aber nie umgekehrt.

### Manuelle bidirektionale Synchronisation {#manual-bidirectional-synchronization}

Öffnen Sie im Projekt-Explorer das Kontextmenü, indem Sie mit der rechten Maustaste auf eine Datei oder einen Ordner klicken. Dort können Sie auf die Optionen **Auf Server exportieren** oder **Von Server importieren** zugreifen.

![chlimage_1-56](assets/chlimage_1-56a.png)

>[!NOTE]
>
>Wenn sich der ausgewählte Eintrag außerhalb des Ordners `jcr_root` befindet, sind die Kontextmenüoptionen **Auf Server exportieren** und **Von Server importieren** deaktiviert.

### Vollständige Content-Package-Synchronisierung {#full-content-package-synchronization}

Im **AEM** Menü, die **Inhaltspaket exportieren** oder **Inhaltspaket importieren** können Sie das gesamte Projekt mit dem Server synchronisieren.

![chlimage_1-57](assets/chlimage_1-57a.png)

### Synchronisierungsstatus {#synchronization-status}

Die AEM Brackets-Erweiterung verfügt über ein Benachrichtigungssymbol in der Symbolleiste rechts neben dem Brackets-Fenster, das den Status der letzten Synchronisation angibt:

* grün - alle Dateien wurden erfolgreich synchronisiert
* blau - ein Synchronisierungsvorgang wird ausgeführt
* gelb - einige der Dateien wurden nicht synchronisiert
* rot - keine der Dateien wurde synchronisiert

Wenn Sie auf das Benachrichtigungssymbol klicken, wird das Dialogfeld Synchronisierungsstatus -Bericht geöffnet, in dem alle Status für jede synchronisierte Datei aufgelistet sind.

![chlimage_1-58](assets/chlimage_1-58a.png)

>[!NOTE]
>
>Nur Inhalt, der in den Filterregeln von `filter.xml` als enthalten gekennzeichnet ist, wird unabhängig von der verwendeten Synchronisierungsmethode synchronisiert.
>
>Darüber hinaus werden `.vltignore`-Dateien unterstützt, um Inhalte von der Synchronisierung zum und vom Repository auszuschließen.

## Bearbeiten von HTL-Code {#editing-htl-code}

Die AEM Brackets-Erweiterung bietet auch eine automatische Vervollständigung, um das Schreiben von HTL-Attributen und -Ausdrücken zu vereinfachen.

### Automatische Vervollständigung von Attributen {#attribute-auto-completion}

1. Geben Sie in einem HTML-Attribut `sly` ein. Das Attribut wird automatisch zu `data-sly-` vervollständigt.
1. Wählen Sie in der Dropdown-Liste das HTL-Attribut aus.

### Ausdruck - Automatische Vervollständigung {#expression-auto-completion}

Innerhalb eines `${}`-Ausdrucks werden allgemeine Variablennamen automatisch vervollständigt.

## Weitere Informationen {#more-information}

Die AEM Brackets-Erweiterung ist ein Open-Source-Projekt, das von [Adobe Marketing Cloud](https://github.com/Adobe-Marketing-Cloud) unter der Apache-Lizenz Version 2.0 auf GitHub gehostet wird:

* Code-Repository: [https://github.com/Adobe-Marketing-Cloud/aem-sightly-brackets-extension](https://github.com/Adobe-Marketing-Cloud/aem-sightly-brackets-extension)
* Apache License, Version 2.0: [https://www.apache.org/licenses/LICENSE-2.0.html](https://www.apache.org/licenses/LICENSE-2.0.html)

Der Brackets-Code-Editor ist ebenfalls ein Open-Source-Projekt, das von [Adobe Systems Incorporated](https://github.com/adobe) auf GitHub gehostet wird:

* Code-Repository: [https://github.com/adobe/brackets](https://github.com/adobe/brackets)

Sie können gern dazu beitragen!
