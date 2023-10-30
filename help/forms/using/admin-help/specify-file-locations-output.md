---
title: Angeben der Dateispeicherorte für die Ausgabe
description: Erfahren Sie, wie Sie Dateispeicherorte für die Ausgabe für bestimmte Dateitypen angeben, z. B. Inhaltsstamm-URI, XCI-Konfigurationsdatei, Cache und Standard.
uuid: 3287274f-85b5-4811-8abb-d347a9b80947
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 460bbb31-8187-469c-8102-b310093b6c03
exl-id: 620c69d6-4fe1-46d6-b5d4-3b562142e547
source-git-commit: 6caf3ef4a00275f0f73be52b6a9ccba77d277f1a
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 56%

---

# Angeben der Dateispeicherorte für die Ausgabe {#specify-file-locations-for-output}

Sie können die Speicherorte angeben, an denen Output nach bestimmten erforderlichen Dateitypen sucht.

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Ausgabe“.
1. Geben Sie unter Standorte die entsprechenden Optionen an.
1. Klicken Sie auf Speichern.

## Speicherorteinstellungen {#locations-settings}

**Inhaltsstamm-URI**: Der URI oder der absolute Speicherort des Repositorys, aus dem Formulare abgerufen werden. Dieser Wert wird mit dem Parameter sForm kombiniert, der über die API angegeben wird, um den absoluten Pfad zu dem Formular zu erzeugen, das abgerufen wird. Dieser Wert kann auf einen Ordner oder einen Webspeicherort verweisen, auf den über HTTP zugegriffen werden kann.

 Der Standardwert ist eine leere Zeichenfolge.

**XCI-Konfigurationsdatei**: Der relative oder absolute Speicherort der XCI-Konfigurationsdatei, die der Ausgabe-Service für die Wiedergabe verwendet. Bei einem relativen Wert wird vorausgesetzt, dass sich die XCI-Datei in der von AEM Forms bereitstellbaren EAR-Datei befindet.

Der Standardwert ist `com/adobe/formServer/PA/pa_output.xci`.

**Cache-Speicherort**: Gibt den Speicherort für den Output-Datenträger-Cache an. Wenn Sie diese Einstellung ändern, werden alle vorhandenen Cache-Informationen vom aktuellen Speicherort zurückgesetzt und ein neuer Cache wird am neuen Speicherort erstellt. Wählen Sie eine der folgenden Optionen aus:

**Standardspeicherort:** Dies ist die Standardauswahl. Wenn diese Option ausgewählt ist, wird der Zwischenspeicher an einem Speicherort erstellt, der von dem von Ihnen verwendeten Anwendungsserver abhängig ist:

* **JBoss:** `[JBoss Home]\server\[install type]\svcdata\Output\Cache`
* **WebLogic:** `[WebLogic Home]\user_projects\domains\[aem-forms domain Name]\adobe\[forms server name]\Output\Cache`
* **WebSphere:** `[IBM Home]\WebSphere\AppServer\installedApps\adobe\server1\Output\Cache`

**Temporärer LC-Ordner**: Der Zwischenspeicher wird in einem Unterordner des temporären Ordners von AEM Forms erstellt, der in der Administration-Console unter „Einstellungen“ > „Core-Systemeinstellungen“ > „Konfigurationen“ > „Speicherort des temporären Verzeichnisses“ angegeben ist. Der Unterordner heißt `adobeoutput_[servername]`.

>[!NOTE]
>
>Wenn Sie ein Bereinigungsprogramm für temporäre Dateien verwenden, beachten Sie, dass das Löschen dieser Verzeichnisse zwar keine Auswirkungen auf die Funktionalität hat, die Leistung jedoch für kurze Zeit erheblich beeinträchtigt werden kann, bis der neue Cache erstellt wird. Um dieses Problem zu vermeiden, sollten Sie diese Ordner nicht löschen, während Sie den temporären Ordner für AEM Formulare löschen.
