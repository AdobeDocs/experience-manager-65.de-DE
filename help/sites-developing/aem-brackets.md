---
title: AEM Brackets-Erweiterung
seo-title: AEM Brackets-Erweiterung
description: 'null'
seo-description: 'null'
uuid: 2f0dfa42-eb34-44ae-90eb-b5f321c03b79
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: 8231a30a-dcb7-4156-bb45-c5a23e5b56ef
translation-type: tm+mt
source-git-commit: 6d216e7521432468a01a29ad2879f8708110d970

---


# AEM Brackets-Erweiterung{#aem-brackets-extension}

## Überblick {#overview}

Die AEM Brackets-Erweiterung bietet einen reibungslosen Workflow für die Bearbeitung von AEM-Komponenten und Client-Bibliotheken und nutzt die Leistungsfähigkeit des [Brackets](https://brackets.io/)-Code-Editors, der den Zugriff auf Photoshop-Dateien und -Ebenen über den Code-Editor ermöglicht. Die durch die Erweiterung gebotene einfache Synchronisation (kein Maven oder File Vault erforderlich) erhöht die Effizienz der Entwickler und hilft auch Frontend-Entwicklern mit begrenztem AEM-Wissen, an Projekten teilzunehmen. This extension also provides some support for the [HTML Template Language (HTL)](https://docs.adobe.com/content/help/en/experience-manager-htl/using/overview.html), which takes away the complexity of JSP to make component development easier and more secure.

![chlimage_1-53](assets/chlimage_1-53a.png)

### Funktionen {#features}

Die Hauptmerkmale der AEM Brackets-Erweiterung sind:

* Automatisierte Synchronisierung geänderter Dateien mit der AEM-Entwicklungsinstanz.
* Manuelle bidirektionale Synchronisierung von Dateien und Ordnern.
* Vollständige Synchronisierung des Inhaltspakets des Projekts.
* HTL code completion for expressions and `data-sly-*` block statements.

Zusätzlich bietet Brackets viele nützliche Funktionen für AEM-Frontend-Entwickler:

* Photoshop-Dateiunterstützung zum Extrahieren von Informationen aus einer PSD-Datei, wie Schichten, Maße, Farben, Schriftarten, Texte usw.
* Codehinweise aus der PSD, um diese extrahierten Informationen im Code einfach wiederzuverwenden.
* CSS-Vorprozessorunterstützung, wie LESS und SCSS.
* Und Hunderte zusätzlicher Erweiterungen, die spezifischere Anforderungen abdecken.

## Installation {#installation}

### Brackets {#brackets}

Die AEM Brackets-Erweiterung unterstützt Brackets Version 1.0 oder höher.

Download the latest Brackets version from [brackets.io](https://brackets.io/).

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

1. ein `jcr_root` Ordner (z. `myproject/jcr_root`)

1. a `filter.xml` file (e.g. `myproject/META-INF/vault/filter.xml`); for more details about the structure of the `filter.xml` file please see the [Workspace Filter definition](https://jackrabbit.apache.org/filevault/filter.html).

Im Menü **Datei** von Brackets wählen Sie **Ordner öffnen...** und wählen Sie entweder den Ordner `jcr_root` oder den übergeordneten Projektordner.

>[!NOTE]
>
>If you don&#39;t have of your own a project with a content-package, you can try the [HTL TodoMVC Example](https://github.com/Adobe-Marketing-Cloud/aem-sightly-sample-todomvc). On GitHub, click **Download ZIP**, extract the files locally, and as instructed above, open the `jcr_root` folder in Brackets. Then follow the steps below to setup the **Project Settings**, and finally upload the whole package to your AEM development instance by doing an **Export Content Package** as instructed further down in the Full Content-Package Synchronization section.
>
>After these steps, you should be able to access the `/content/todo.html` URL on your AEM development instance and you can start doing modifications to the code in Brackets and see how, after doing a refresh in the web browser, the changes were immediately synchronized to the AEM server.

### Projekteinstellungen {#project-settings}

Um Ihren Inhalt mit einer AEM-Entwicklungsinstanz zu synchronisieren, müssen Sie Ihre Projekteinstellungen definieren. This can be done by going to the **AEM** menu and choosing **Project Settings…**

![chlimage_1-55](assets/chlimage_1-55a.png)

Die Projekteinstellungen erlauben die Definition von Folgendem:

1. The server URL (e.g. `http://localhost:4502`)
1. Tolerieren von Servern ohne gültiges HTTPS-Zertifikat (deaktivieren Sie nicht, sofern nicht erforderlich)
1. Benutzername, der für die Synchronisierung von Inhalten verwendet wird (z. B. `admin`)
1. The user&#39;s password (e.g. `admin`)

## Synchronisieren von Inhalten {#synchronizing-content}

The AEM Brackets Extension provides following types of content synchronization for files and folders that are allowed by the filtering rules defined in `filter.xml`:

### Automatisierte Synchronisierung von geänderten Dateien {#automated-synchronization-of-changed-files}

Diese synchronisiert nur Änderungen von Brackets mit der AEM-Instanz, aber niemals umgekehrt.

### Manuelle bidirektionale Synchronisierung {#manual-bidirectional-synchronization}

In the Project Explorer, open the contextual menu by right-clicking on any file or folder, and the **Export to Server** or **Import from Server** options can be accessed.

![chlimage_1-56](assets/chlimage_1-56a.png)

>[!NOTE]
>
>If the selected entry is outside of the `jcr_root` folder, the **Export to Server** and **Import from Server** contextual menu entries are disabled.

### Vollständige Content-Package-Synchronisierung {#full-content-package-synchronization}

In the **AEM** menu, the **Export Content Package** or **Import Content Package** options allow to synchronize the whole project with the server.

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
>Additionally, `.vltignore` files are supported for excluding content from synchronizing to and from the repository.

## Bearbeiten von HTL-Code {#editing-htl-code}

Die AEM Brackets-Erweiterung bietet auch eine automatische Vervollständigung, um das Schreiben von HTL-Attributen und -Ausdrücken zu vereinfachen.

### Automatische Vervollständigung von Attributen {#attribute-auto-completion}

1. Geben Sie in einem HTML-Attribut `sly` ein. Das Attribut wird automatisch zu `data-sly-` - vervollständigt.
1. Wählen Sie das HTL-Attribut in der Dropdown-Liste aus.

### Automatische Vervollständigung von Ausdrücken {#expression-auto-completion}

Within an expression `${}`, common variable names are auto-completed.

## Weitere Informationen {#more-information}

Die AEM Brackets-Erweiterung ist ein Open-Source-Projekt, das von [Adobe Marketing Cloud](https://github.com/Adobe-Marketing-Cloud) unter der Apache-Lizenz Version 2.0 auf GitHub gehostet wird:

* Code-Repository: [https://github.com/Adobe-Marketing-Cloud/aem-sightly-brackets-extension](https://github.com/Adobe-Marketing-Cloud/aem-sightly-brackets-extension)
* Apache License, version 2.0: [https://www.apache.org/licenses/LICENSE-2.0.html](https://www.apache.org/licenses/LICENSE-2.0.html)

The Brackets code editor is also an open-source project, hosted on GitHub by the [Adobe Systems Incorporated](https://github.com/adobe) organization:

* Code repository: [https://github.com/adobe/brackets](https://github.com/adobe/brackets)

Sie können gern dazu beitragen!
