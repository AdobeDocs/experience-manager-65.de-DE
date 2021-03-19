---
title: Forms-Repository-Neustrukturierung in AEM 6.5
seo-title: Forms-Repository-Neustrukturierung in AEM 6.5
description: Erfahren Sie, wie Sie die erforderlichen Änderungen vornehmen können, um die neue Repository-Struktur in AEM 6.5 für Forms zu migrieren.
seo-description: Erfahren Sie, wie Sie die erforderlichen Änderungen vornehmen können, um die neue Repository-Struktur in AEM 6.5 für Forms zu migrieren.
uuid: e60830d4-23ca-4be9-941a-ee4abe4786a6
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 1ce9a622-5968-407f-a74b-d325a2bff669
feature: Aktualisieren
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 83%

---


# Forms-Repository-Neustrukturierung in AEM 6.5{#forms-repository-restructuring-in-aem}

Wie auf der übergeordneten Seite [Repository-Umstrukturierung in AEM 6.5](/help/sites-deploying/repository-restructuring.md) beschrieben, sollten Kunden, die auf AEM 6.5 aktualisieren, diese Seite verwenden, um den Arbeitsaufwand zu bewerten, der mit Repository-Änderungen verbunden ist, die die AEM Forms-Lösung beeinträchtigen. Einige Änderungen erfordern Arbeitsaufwand während des AEM 6.5-Aktualisierungsprozesses, während andere bis zu einem zukünftigen Upgrade verschoben werden können.

**Mit der Aktualisierung auf 6.5**

* [Verschiedenes](/help/sites-deploying/forms-repository-restructuring-in-aem-6-5.md#misc)

**Vor der zukünftigen Aktualisierung**

* [Echosign-Cloud-Service-Konfiguration](/help/sites-deploying/forms-repository-restructuring-in-aem-6-5.md#echosign-cloud-service-configuration)
* [Recaptcha-Cloud-Service-Konfigurationen](/help/sites-deploying/forms-repository-restructuring-in-aem-6-5.md#recaptcha-cloud-service-configurations)
* [Typekit-Cloud-Service-Konfigurationen](/help/sites-deploying/forms-repository-restructuring-in-aem-6-5.md#typekit-cloud-service-configurations)
* [Verschiedenes](/help/sites-deploying/forms-repository-restructuring-in-aem-6-5.md#misc)

## Mit der Aktualisierung auf 6.5 {#with-upgrade}

### Verschiedenes {#misc}

| **Vorheriger Speicherort** | `/etc/clientlibs/fd/fp` |
|---|---|
| **Neuer Speicherort** | `/libs/fd/fp/components` |
| **Leitfaden für die Neustrukturierung** | Alle expliziten Verweise im benutzerdefinierten Code auf den Speicherort &quot;Veraltet&quot;müssen auf den Speicherort &quot;Neu&quot;aktualisiert werden. |
| **Hinweise** | Diese Client-Bibliotheken sollten nicht modifiziert oder erweitert werden. |

| **Vorheriger Speicherort** | `/etc/clientlibs/fd/rte` |
|---|---|
| **Neuer Speicherort** | `/libs/fd/rte` |
| **Leitfaden für die Neustrukturierung** | Für die Ressourcen in den Client-Bibliotheken, die über absolute Pfade referenziert werden können, müssen Sie in neuen Assets neuere Pfade verwenden. |
| **Hinweise** | Nicht zutreffend |

| **Vorheriger Speicherort** | `/etc/clientlibs/fd/af` |
|---|---|
| **Neuer Speicherort** | `/libs/fd/af/authoring/clientlibs` |
| **Leitfaden für die Neustrukturierung** | Für die Ressourcen in den Client-Bibliotheken, die über absolute Pfade referenziert werden können, müssen Sie in neuen Assets neuere Pfade verwenden. |
| **Hinweise** | Nicht zutreffend |

| **Vorheriger Speicherort** | `/etc/clientlibs/fd/xfaforms` |
|---|---|
| **Neuer Speicherort** | `/libs/fd/xfaforms/clientlibs/` |
| **Leitfaden für die Neustrukturierung** | Für die Ressourcen in den Client-Bibliotheken, die über absolute Pfade referenziert werden können, müssen Sie in neuen Assets neuere Pfade verwenden. |
| **Hinweise** | Nicht zutreffend |

| **Vorheriger Speicherort** | `/etc/clientlibs/fd/af` |
|---|---|
| **Neuer Speicherort** | `/libs/fd/af/runtime/clientlibs` |
| **Leitfaden für die Neustrukturierung** | Für die Ressourcen in den Client-Bibliotheken, die über absolute Pfade referenziert werden können, müssen Sie in neuen Assets neuere Pfade verwenden. |
| **Hinweise** | Nicht zutreffend |

| **Vorheriger Speicherort** | `/etc/clientlibs/fd/af` |
|---|---|
| **Neuer Speicherort** | `/libs/fd/af/runtime/clientlibs` |
| **Leitfaden für die Neustrukturierung** | Für die Ressourcen in den Client-Bibliotheken, die über absolute Pfade referenziert werden können, müssen Sie in neuen Assets neuere Pfade verwenden. |
| **Hinweise** | Nicht zutreffend |

| **Vorheriger Speicherort** | `/etc/clientlibs/fd/expeditor` |
|---|---|
| **Neuer Speicherort** | `/libs/fd/expeditor/clientlibs` |
| **Leitfaden für die Neustrukturierung** | Für die Ressourcen in den Client-Bibliotheken, die über absolute Pfade referenziert werden können, müssen Sie in neuen Assets neuere Pfade verwenden. |
| **Hinweise** | Nicht zutreffend |

| **Vorheriger Speicherort** | `/etc/clientlibs/fd/fmaddon` |
|---|---|
| **Neuer Speicherort** | `/libs/fd/fmaddon` |
| **Leitfaden für die Neustrukturierung** | Das Ändern dieser Client-Bibliotheken wurde nie empfohlen oder unterstützt. Wenn Änderungen an diesen Client-Bibliotheken vorgenommen wurden, sollten diese auf den von AEM bereitgestellten Code zurückgesetzt werden. |
| **Hinweise** | Nicht zutreffend |

| **Vorheriger Speicherort** | `/etc/aep` |
|---|---|
| **Neuer Speicherort** | `/var/fd/content/annotations` |
| **Leitfaden für die Neustrukturierung** | Das Ändern dieser Client-Bibliotheken wurde nie empfohlen oder unterstützt. Wenn Änderungen an diesen Client-Bibliotheken vorgenommen wurden, sollten diese auf den von AEM bereitgestellten Code zurückgesetzt werden. |
| **Hinweise** | Nicht zutreffend |

## Vor der zukünftigen Aktualisierung {#prior-to-upgrade}

### Echosign-Cloud-Service-Konfiguration {#echosign-cloud-service-configuration}

| **Vorheriger Speicherort** | `/etc/cloudservices/echosign` |
|---|---|
| **Neuer Speicherort** | `/conf/<tenant>/settings/cloudconfigs/echosign` |
| **Leitfaden für die Neustrukturierung** | Das Dienstprogramm [Erleichterte Inhaltsmigration](/help/sites-deploying/lazy-content-migration.md) wird von der Migrationsoberfläche von Forms ausgelöst. |
| **Hinweise** | Nicht zutreffend |

### Recaptcha-Cloud-Service-Konfigurationen {#recaptcha-cloud-service-configurations}

| **Vorheriger Speicherort** | `/etc/cloudservices/recaptcha` |
|---|---|
| **Neuer Speicherort** | `/conf/<tenant>/settings/cloudconfigs/recaptcha` |
| **Leitfaden für die Neustrukturierung** | Das Dienstprogramm [Erleichterte Inhaltsmigration](/help/sites-deploying/lazy-content-migration.md) wird von der Migrationsoberfläche von Forms ausgelöst. |
| **Hinweise** | Nicht zutreffend |

### Typekit-Cloud-Service-Konfigurationen  {#typekit-cloud-service-configurations}

| **Vorheriger Speicherort** | `/etc/cloudservices/typekit` |
|---|---|
| **Neuer Speicherort** | `/conf/<tenant>/settings/cloudconfigs/typekit` |
| **Leitfaden für die Neustrukturierung** | Das Dienstprogramm [Erleichterte Inhaltsmigration](/help/sites-deploying/lazy-content-migration.md) wird von der Migrationsoberfläche von Forms ausgelöst. |
| **Hinweise** | Nicht zutreffend |

### Verschiedenes  {#misc-1}

| **Vorheriger Speicherort** | `/etc/cloudservices/fdm` |
|---|---|
| **Neuer Speicherort** | `/conf/<tenant>/settings/cloudconfigs/fdm` |
| **Leitfaden für die Neustrukturierung** | Das Dienstprogramm [Erleichterte Inhaltsmigration](/help/sites-deploying/lazy-content-migration.md) wird von der Migrationsoberfläche von Forms ausgelöst. |
| **Hinweise** | Nicht zutreffend |

| **Vorheriger Speicherort** | `/etc/designs/fd/fp` |
|---|---|
| **Neuer Speicherort** | `/libs/fd/fp` |
| **Leitfaden für die Neustrukturierung** | Alle Verweise auf die /etc-Vorlagen sollten irgendwann aktualisiert werden, um auf ihre `/libs`-Entsprechungen zu verweisen. |
| **Hinweise** | Nicht zutreffend |

