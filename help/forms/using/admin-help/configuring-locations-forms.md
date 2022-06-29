---
title: Speicherorte für Forms konfigurieren
seo-title: Configuring locations for Forms
description: Erfahren Sie, wie Sie einen Speicherort für Forms konfigurieren.
seo-description: Learn how to configure location for Forms.
uuid: ba35888b-492c-4678-890b-160b53e7d659
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 3d2b7cfb-228c-4cc2-8fcd-d500f0010010
exl-id: 0d9eb7fe-28a6-444e-957d-023687158c61
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '804'
ht-degree: 100%

---

# Speicherorte für Forms konfigurieren {#configuring-locations-for-forms}

Sie können die URL-, URI- und Dateispeicherorte von Attributen wie dem Webstamm sowie den Speicherort der abzurufenden Formulare und die bei PDF-Transformationen verwendete Seed-PDF-Datei und den Cache-Speicherort angeben.

1. Klicken Sie in Administration Console auf „Dienste“ > „Forms“.
1. Geben Sie unter „Speicherorte“ die entsprechenden Optionen an. Die Optionen sind im Folgenden beschrieben.
1. Klicken Sie auf Speichern.

## Speicherorteinstellungen {#locations-settings}

**Basis-URL:** Die Basis-URL, an der sich Formularressourcen, z. B. Bilder und Skripte, befinden. Dieser Wert ist für HTML-Transformationen erforderlich, die HREF-Verweise auf externe Abhängigkeiten enthalten, wie z. B. Bilder oder Skripte. Ein solches Skript ist „xfasubset.js“, das erforderlich ist, damit HTML-Formulare intelligente XFA-Funktionen ausführen können. Dieser Wert muss die HTTP-Entsprechung des Inhaltsstamm-URI sein.

>[!NOTE]
>
>Basis-URL unterstützt nur HTTP- oder Repository-Protokolle. Protokolle wie „Datei:///“ werden nicht unterstützt. Wenn Sie auf eine Ressource wie ein benutzerdefiniertes CSS oder ein URI für eine digitale Signatur zugreifen müssen, verwenden Sie den entsprechenden API-Parameterwert zur Angabe des absoluten Speicherorts.

Wenn ein Abhängigkeitspfad absolut ist, wird der Basis-URL-Wert ignoriert. Andernfalls wird der Abhängigkeitspfad mit der Basis-URL kombiniert.

 Der Standardwert ist eine leere Zeichenfolge.

 Das folgende Beispiel verweist auf denselben Inhalt (unter Verwendung von Inhaltsstamm-URI und Basis-URL):

`(ContentRootURI)/subdir/image1.jpg`

`(BaseURL)/subdir/image1.jpg`

**FS-Webstamm-URI:** Die URL der Forms-Webanwendung. Dieses Feld kann leer bleiben, wenn die Forms-Webanwendung und die Clientanwendung auf demselben Anwendungsserver bereitgestellt sind. In diesem Fall wird die Forms-API-Webstamm-URL verwendet.

 Wenn die Forms-Web- und die Clientanwendung nicht auf demselben Anwendungsserver bereitgestellt sind, müssen Sie die URL der Forms-Webanwendung in diesem Feld, wie im folgenden Beispiel gezeigt, angeben:

`https://<host name>:<port>/FormServer`

 `host name`und `port` sind der Server-Name bzw. die Port-Nummer des Servers, der als Host der Forms-Webanwendung dient.

 Der Standardwert ist eine leere Zeichenfolge.

**Webstamm-URI:** Der Webstamm des Programms. Dieser Wert wird mit dem sTargetURL-Parameter (wenn sTargetURL relativ angegeben ist) kombiniert, der über das AEM Forms SDK angegeben wird, um eine absolute URL für den Zugriff auf anwendungsspezifische Webinhalte zu erzeugen.

 Der Standardwert ist eine leere Zeichenfolge.

**Inhaltsstamm-URI:** Der URI oder der absolute Speicherort, von dem Formulare abgerufen werden. Dieser Wert wird mit dem sFormQuery-Parameter kombiniert, der über die API angegeben wird, um den absoluten Pfad zu dem Formular zu erzeugen, das abgerufen wird. Dieser Wert kann auf einen Ordner oder einen Webspeicherort verweisen, auf den über HTTP zugegriffen werden kann. 

 Der Standardwert ist eine leere Zeichenfolge.

**XCI-Konfigurationsdatei-URI:** Der relative oder absolute Speicherort, an dem sich die für die Wiedergabe verwendete XCI-Konfigurationsdatei befindet. Bei einem relativen Wert wird vorausgesetzt, dass sich die XCI-Datei in der bereitstellbaren AEM Forms-EAR-Datei befindet. 

Der Standardwert ist `com/adobe/formServer/PA/pa.xci`.

**Schriftzuordnungs-URI:** Der relative oder absolute Speicherort der Schriftzuordnungsdatei. Bei einem relativen Wert wird vorausgesetzt, dass sich diese Datei in der bereitstellbaren AEM Forms-EAR-Datei befindet.

Die Schriftartzuordnungsdatei wird verwendet, um benutzerdefinierte Schriftartzuordnungen für HTML-Transformationen in Forms zu erstellen. Auf diese Weise können Sie dann angeben, welche Schriftart ersetzt wird, wenn diese auf dem Clientcomputer nicht verfügbar ist.

Der Standardwert ist `com/adobe/formServer/client-font-map.properties`.

Im Folgenden finden Sie ein Beispiel für einen Eintrag in der Schriftartzuordnungsdatei: 

`Arial=Arial,Helvetica,sans-serif`

**Seed-PDF-Datei:** Die anfängliche PDF-Datei, die bei einer PDFForm-Transformation zur Optimierung der Übermittlung verwendet wird. Die Seed-PDF-Datei ist eine angepasste PDF-Datei (die nur XFA-Stream-, Bild- und Schriftartressourcen enthält), die dem Formularentwurf und den Formulardaten angehängt wird. Das Formular wird in Acrobat 7 oder höher wiedergegeben und findet bei der PDFForm-Transformation Anwendung. 

Der Standardwert ist eine leere Zeichenfolge.

**Cache-Speicherort:** Gibt den Speicherort des Forms-Datenträger-Cache an. Nachdem Sie diese Einstellung geändert haben, werden alle vorhandenen Zwischenspeicherinformationen am aktuellen Speicherort zurückgesetzt und es wird ein neuer Zwischenspeicher am neuen Speicherort erstellt. Wählen Sie eine der folgenden Optionen aus:

**Standardspeicherort:** Dies ist die Standardauswahl. Wenn diese Option ausgewählt ist, wird der Zwischenspeicher an einem Speicherort erstellt, der von dem von Ihnen verwendeten Anwendungsserver abhängig ist:

* **JBoss:** [JBoss-Startseite]\server\[install type]\svcdata\FormServer\Cache
* **WebLogic:** [WebLogic-Startseite]\user_projects\domains\[AEM Forms-Domain-Name]\adobe\[Name des Formular-Servers]\FormServer\Cache
* **WebSphere:** [IBM Home]\WebSphere\AppServer\installedApps\adobe\server1\FormServer\Cache

**Temporärer LC-Ordner:** Der Zwischenspeicher wird in einem Unterordner des temporären Ordners von AEM Forms erstellt, der in der Administration-Console unter „Einstellungen“ > „Core-Systemeinstellungen“ > „Konfigurationen“ > „Speicherort des temporären Verzeichnisses“ angegeben ist. Der Unterordner heißt adobeform_[Servername].

>[!NOTE]
>
>Wenn Sie ein Bereinigungsprogramm für temporäre Dateien verwenden, beachten Sie, dass das Löschen dieser Ordner zwar keine Auswirkungen auf die Funktionalität hat; die Leistung kann jedoch kurzzeitig erheblich beeinträchtigt werden, bis der neue Zwischenspeicher erstellt ist. Um dieses Problem zu vermeiden, sollten Sie diese Ordner nicht löschen, während die temporären Ordner von AEM Forms gelöscht werden.
