---
title: Tipps zum Minimieren des Datenbankwachstums
seo-title: Tips for minimizing database growth
description: Prozesse mit langer Lebensdauer speichern Prozessdaten in der AEM Formulardatenbank. Das Wachstum der AEM Forms-Datenbank kann mithilfe einiger einfacher Prozessdesign- und Produktkonfigurationsstrategien minimiert werden.
seo-description: Long-lived processes store process data in the AEM forms database. The growth of the AEM forms database can be minimized using a few easy process design and product configuration strategies.
uuid: 13f99d4f-848e-451e-90d9-55e202dc0bdb
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 89441336-babc-4d1f-9053-d1566cd42d22
exl-id: f64efb06-815a-4608-ba1c-39e22f344ebb
source-git-commit: c4cd9a61a226ace2a72d60b5b7b7432de12cb873
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 3%

---

# Tipps zum Minimieren des Datenbankwachstums {#tips-for-minimizing-database-growth}

Prozesse mit langer Lebensdauer speichern Prozessdaten in der AEM Formulardatenbank. Das Wachstum der AEM Forms-Datenbank kann mithilfe einiger einfacher Prozessdesign- und Produktkonfigurationsstrategien minimiert werden.

## Tipps zur Prozessgestaltung {#process-design-tips}

Verwenden Sie nach Möglichkeit kurzlebige Prozesse. In kurzlebigen Prozessen werden keine Prozessdaten in der Datenbank gespeichert. Der Nachteil bei der Verwendung von kurzlebigen Prozessen besteht darin, dass ihr Status und ihr Status nicht in Administration Console verfolgt werden und es keinen Verlauf des Prozesses gibt.

Einige Dienstvorgänge wie der Vorgang &quot;Assign Task&quot;(User-Dienst) erfordern, dass sie in langlebigen Prozessen verwendet werden. In diesem Fall können Sie den Prozess in mehrere Teilprozesse unterteilen und nach Möglichkeit kurzlebig gestalten. Wenn Sie diese Strategie verwenden, sollten kurzlebige Teilprozesse große Datenelemente wie Dokumentwerte verarbeiten.

Verwenden Sie Variablen sparsam. Bei der Verwendung langlebiger Prozesse wird für jede Prozessinstanz der Datenbank für jede Variable im Prozess Speicherplatz zugewiesen. Die strategische Nutzung von Variablen kann viel Platz sparen. Sie können beispielsweise Variablenwerte überschreiben, wenn alte Werte im Prozess nicht mehr benötigt werden. Löschen Sie alle Variablen, die Sie erstellt haben und nicht verwenden. Sie können den Prozess validieren, um nicht verwendete Variablen zu finden.

Verwenden Sie einfache Variablentypen (z. B. Zeichenfolge oder int) und vermeiden Sie die Verwendung komplexer Variablentypen, wann immer möglich. Datenbankspeicherplatz wird Variablen zugewiesen, selbst wenn sie keinen Wert enthalten. Komplexe Variablen benötigen in der Regel mehr Platz als einfache.

## Tipps zur Produktverwaltung {#product-administration-tips}

Verwenden Sie den globalen Dokumentenspeicher (GDS) effektiv. Der Ordner des globalen Dokumentenspeichers auf dem Forms-Server wird unter anderem zum Speichern von Dateien verwendet, die an Dienste übergeben werden, die Teil AEM Formulare in Prozessen sind. Zur Leistungsverbesserung werden kleinere Dokumente stattdessen im Arbeitsspeicher gespeichert und in der Datenbank beibehalten.

Administration Console stellt die Eigenschaft &quot;Default Document Max Inline Size&quot;zur Konfiguration der maximalen Größe von Dokumenten bereit, die im Speicher gespeichert und in der Datenbank beibehalten werden. (Siehe [Konfigurieren allgemeiner AEM Forms-Einstellungen](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings).) Wenn Sie diese Eigenschaft auf einen niedrigen Wert setzen, werden die meisten Dokumente im Ordner des globalen Dokumentenspeichers und nicht in der Datenbank beibehalten. Der Vorteil besteht darin, dass Sie die Dateien leichter löschen können, wenn sie nicht mehr benötigt werden, wenn sie im Ordner des globalen Dokumentenspeichers gespeichert sind.
