---
title: Konfigurieren der Speicherorte für Forms
description: Erfahren Sie, wie Sie den Speicherort für AEM Formular konfigurieren. Sie können die Dateispeicherorte des Attributs, den Speicherort des Formulars, die Seed-PDF-Datei und den Cache-Speicherort angeben.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 0d9eb7fe-28a6-444e-957d-023687158c61
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 42%

---

# Konfigurieren der Speicherorte für Forms {#configuring-locations-for-forms}

Sie können die URL-, URI- und Dateispeicherorte von Attributen wie den Webstamm, den Speicherort der abzurufenden Formulare, die bei PDFForm-Transformationen verwendete Seed-PDF-Datei und den Cache-Speicherort angeben.

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Formulare“.
1. Geben Sie unter Standorte die entsprechenden Optionen an. Die Optionen werden nachfolgend beschrieben.
1. Klicken Sie auf Speichern.

## Speicherorteinstellungen {#locations-settings}

**Basis-URL:** Die Basis-URL, an der sich Formularressourcen, z. B. Bilder und Skripte, befinden. Dieser Wert ist für HTML-Transformationen erforderlich, die HREF-Verweise auf externe Abhängigkeiten enthalten, z. B. Bilder oder Skripte. Ein solches Skript ist xfasubset.js, das erforderlich ist, damit HTML-Formulare XFA-Intelligenz durchführen können. Dieser Wert muss das HTTP-Äquivalent des Inhaltsstamm-URI sein.

>[!NOTE]
>
>Basis-URL unterstützt nur HTTP- oder Repository-Protokolle. Protokolle wie file:/// werden nicht unterstützt. Wenn Sie auf eine Ressource wie ein benutzerdefiniertes CSS oder einen URI für eine digitale Signatur zugreifen müssen, verwenden Sie den entsprechenden API-Parameterwert, um den absoluten Speicherort anzugeben.

Wenn ein Abhängigkeitspfad absolut ist, wird der Basis-URL-Wert ignoriert. Andernfalls wird der Abhängigkeitspfad mit der Basis-URL kombiniert.

 Der Standardwert ist eine leere Zeichenfolge.

Das folgende Beispiel verweist auf denselben Inhalt (unter Verwendung des Inhaltsstamm-URI und der Basis-URL):

`(ContentRootURI)/subdir/image1.jpg`

`(BaseURL)/subdir/image1.jpg`

**FS-Webstamm-URI:** Die URL der Forms-Webanwendung. Sie können dieses Feld leer lassen, wenn die Forms-Webanwendung und die Clientanwendung auf demselben Anwendungsserver bereitgestellt sind. Die Forms-API-Webstamm-URL wird verwendet.

Wenn die Forms-Webanwendung und die Clientanwendung nicht auf demselben Anwendungsserver bereitgestellt sind, geben Sie die URL für die Forms-Webanwendung in dieses Feld ein, wie in diesem Beispiel gezeigt:

`https://<host name>:<port>/FormServer`

 `host name`und `port` sind der Server-Name bzw. die Port-Nummer des Servers, der als Host der Forms-Webanwendung dient.

 Der Standardwert ist eine leere Zeichenfolge.

**Webstamm-URI:** Der Webstamm des Programms. Dieser Wert wird mit dem sTargetURL-Parameter (wenn sTargetURL relativ angegeben ist) kombiniert, der über das AEM Forms SDK angegeben wird, um eine absolute URL für den Zugriff auf anwendungsspezifische Webinhalte zu erzeugen.

 Der Standardwert ist eine leere Zeichenfolge.

**Inhaltsstamm-URI:** Der URI oder der absolute Speicherort, von dem Formulare abgerufen werden. Dieser Wert wird mit dem sFormQuery-Parameter kombiniert, der über die API angegeben wird, um den absoluten Pfad zu dem Formular zu erzeugen, das abgerufen wird. Dieser Wert kann auf einen Ordner oder einen Webspeicherort verweisen, auf den über HTTP zugegriffen werden kann.

 Der Standardwert ist eine leere Zeichenfolge.

**XCI-Konfigurationsdatei-URI:** Der relative oder absolute Speicherort, an dem sich die für die Wiedergabe verwendete XCI-Konfigurationsdatei befindet. Bei einem relativen Wert wird vorausgesetzt, dass sich die XCI-Datei in der bereitstellbaren AEM Forms-EAR-Datei befindet. 

Der Standardwert ist `com/adobe/formServer/PA/pa.xci`.

**Schriftzuordnungs-URI:** Der relative oder absolute Speicherort der Schriftzuordnungsdatei. Bei einem relativen Wert wird davon ausgegangen, dass sich diese Datei in der bereitstellbaren EAR-Datei für AEM Formulare befindet.

Die Schriftzuordnungsdatei wird verwendet, um benutzerdefinierte Schriftartzuordnungen für HTML-Transformationen in Formularen zu erstellen. Auf diese Weise können Sie angeben, welche Schriftart ersetzt wird, wenn eine Schriftart auf dem Clientcomputer nicht verfügbar ist.

Der Standardwert ist `com/adobe/formServer/client-font-map.properties`.

Im Folgenden finden Sie ein Beispiel für einen Eintrag in der Schriftartzuordnungsdatei: 

`Arial=Arial,Helvetica,sans-serif`

**Seed-PDF-Datei:** Die anfängliche PDF-Datei, die bei einer PDFForm-Transformation zur Optimierung der Übermittlung verwendet wird. Die Seed-PDF-Datei gibt eine angepasste PDF-Datei an (die nur XFA-Stream-, Bild- und Schriftartressourcen enthält), die an den Formularentwurf und die Daten angehängt wird. Das Formular wird von Acrobat 7 oder höher wiedergegeben und gilt für die PDFForm-Transformation.

Der Standardwert ist eine leere Zeichenfolge.

**Cache-Speicherort:** Gibt den Speicherort des Forms-Datenträger-Cache an. Wenn Sie diese Einstellung ändern, werden alle vorhandenen Cache-Informationen vom aktuellen Speicherort zurückgesetzt und ein neuer Cache wird am neuen Speicherort erstellt. Wählen Sie eine der folgenden Optionen aus:

**Standardspeicherort:** Dies ist die Standardauswahl. Wenn diese Option ausgewählt ist, wird der Zwischenspeicher an einem Speicherort erstellt, der von dem von Ihnen verwendeten Anwendungsserver abhängig ist:

* **JBoss:** [JBoss-Startseite]\server\[install type]\svcdata\FormServer\Cache
* **WebLogic:** [WebLogic-Startseite]\user_projects\domains\[aem-forms-Domänenname]\adobe\[Forms-Servername]\FormServer\Cache
* **WebSphere:** [IBM Home]\WebSphere\AppServer\installedApps\adobe\server1\FormServer\Cache

**Temporärer LC-Ordner:** Der Zwischenspeicher wird in einem Unterordner des temporären Ordners von AEM Forms erstellt, der in der Administration-Console unter „Einstellungen“ > „Core-Systemeinstellungen“ > „Konfigurationen“ > „Speicherort des temporären Verzeichnisses“ angegeben ist. Der Unterordner heißt adobeform_[Servername].

>[!NOTE]
>
>Wenn Sie ein Bereinigungsprogramm für temporäre Dateien verwenden, während das Löschen dieser Verzeichnisse keine Auswirkungen auf die Funktionalität hat, kann dies die Leistung für kurze Zeit erheblich beeinträchtigen, bis der neue Cache erstellt wird. Um dieses Problem zu vermeiden, sollten Sie diese Ordner nicht löschen, während Sie den temporären Ordner für AEM Formulare löschen.
