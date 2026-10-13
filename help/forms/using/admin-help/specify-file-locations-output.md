---
title: Angeben der Dateispeicherorte für die Ausgabe
description: Erfahren Sie, wie Sie Dateispeicherorte für die Ausgabe für bestimmte Dateitypen angeben, z. B. Inhaltsstamm-URI, XCI-Konfigurationsdatei, Cache und Standard.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 620c69d6-4fe1-46d6-b5d4-3b562142e547
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 100%
---
# Angeben der Dateispeicherorte für die Ausgabe {#specify-file-locations-for-output}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Sie können die Speicherorte angeben, an denen die Ausgabe nach bestimmten Typen von erforderlichen Dateien suchen soll.

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Ausgabe“.
1. Geben Sie unter „Speicherorte“ die entsprechenden Optionen an.
1. Klicken Sie auf Speichern.

## Speicherorteinstellungen {#locations-settings}

**Inhaltsstamm-URI**: Der URI oder der absolute Speicherort des Repositorys, aus dem Formulare abgerufen werden. Dieser Wert wird mit dem Parameter sForm kombiniert, der über die API angegeben wird, um den absoluten Pfad zu dem Formular zu erzeugen, das abgerufen wird. Dieser Wert kann auf einen Ordner oder einen Web-Speicherort verweisen, auf den über HTTP zugegriffen werden kann.

Der Standardwert ist eine leere Zeichenfolge.

**XCI-Konfigurationsdatei**: Der relative oder absolute Speicherort der XCI-Konfigurationsdatei, die der Ausgabe-Service für die Wiedergabe verwendet. Bei einem relativen Wert wird vorausgesetzt, dass sich die XCI-Datei in der von AEM Forms bereitstellbaren EAR-Datei befindet.

Der Standardwert ist `com/adobe/formServer/PA/pa_output.xci`.

**Cache-Speicherort**: Gibt den Speicherort für den Output-Datenträger-Cache an. Nachdem Sie diese Einstellung geändert haben, werden alle vorhandenen Cache-Informationen am aktuellen Speicherort zurückgesetzt und es wird ein neuer Cache am neuen Speicherort erstellt. Wählen Sie eine der folgenden Optionen aus:

**Standardspeicherort:** Dies ist die Standardauswahl. Wenn diese Option ausgewählt ist, wird der Zwischenspeicher an einem Speicherort erstellt, der von dem von Ihnen verwendeten Anwendungsserver abhängig ist:

* **JBoss:** `[JBoss Home]\server\[install type]\svcdata\Output\Cache`
* **WebLogic:** `[WebLogic Home]\user_projects\domains\[aem-forms domain Name]\adobe\[Forms Server name]\Output\Cache`
* **WebSphere:** `[IBM Home]\WebSphere\AppServer\installedApps\adobe\server1\Output\Cache`

**Temporärer LC-Ordner**: Der Zwischenspeicher wird in einem Unterordner des temporären Ordners von AEM Forms erstellt, der in der Administration-Console unter „Einstellungen“ > „Core-Systemeinstellungen“ > „Konfigurationen“ > „Speicherort des temporären Verzeichnisses“ angegeben ist. Der Unterordner heißt `adobeoutput_[servername]`.

>[!NOTE]
>
>Wenn Sie ein Bereinigungsprogramm für temporäre Dateien verwenden, hat das Löschen dieser Verzeichnisse zwar keine Auswirkungen auf die Funktionalität, die Leistung kann jedoch kurzzeitig erheblich beeinträchtigt werden, bis der neue Cache erstellt wurde. Um dieses Problem zu vermeiden, sollten Sie diese Ordner nicht löschen, während die temporären Ordner von AEM Forms gelöscht werden.
