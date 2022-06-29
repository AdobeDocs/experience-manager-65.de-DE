---
title: Tipps zum Minimieren des Datenbankwachstums
seo-title: Tips for minimizing database growth
description: Prozesse mit langer Lebensdauer speichern Prozessdaten in der AEM Forms-Datenbank. Das Wachstum der AEM Forms-Datenbank kann mithilfe weniger einfacher Prozessentwurfs- und Produktkonfigurationsstrategien minimiert werden.
seo-description: Long-lived processes store process data in the AEM forms database. The growth of the AEM forms database can be minimized using a few easy process design and product configuration strategies.
uuid: 13f99d4f-848e-451e-90d9-55e202dc0bdb
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 89441336-babc-4d1f-9053-d1566cd42d22
exl-id: f64efb06-815a-4608-ba1c-39e22f344ebb
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '408'
ht-degree: 100%

---

# Tipps zum Minimieren des Datenbankwachstums {#tips-for-minimizing-database-growth}

Prozesse mit langer Lebensdauer speichern Prozessdaten in der AEM Forms-Datenbank. Das Wachstum der AEM Forms-Datenbank kann mithilfe weniger einfacher Prozessentwurfs- und Produktkonfigurationsstrategien minimiert werden.

## Tipps zum Prozessentwurf {#process-design-tips}

Verwenden Sie, wann immer möglich, Prozesse mit kurzer Lebensdauer. Prozesse mit kurzer Lebensdauer speichern keine Prozessdaten in der Datenbank. Der Nachteil beim Verwenden von Prozessen mit kurzer Lebensdauer besteht darin, dass ihr Status und Zustand nicht in Administration Console nachvollzogen wird und es keinen Verlauf des Prozesses und keine BAM-Berichte gibt.

Einige Dienstvorgänge, z. B. „Aufgabe zuweisen“-Vorgänge (User-Dienst), müssen in Prozessen mit langer Lebensdauer verwendet werden. In diesem Fall können Sie den Prozess in mehrere Unterprozesse aufteilen und, wo dies möglich ist, daraus Prozesse mit kurzer Lebensdauer machen. Wenn Sie diese Strategie verwenden, können Prozesse mit kurzer Lebensdauer große Datenelemente, z. B. Dokumentwerte, verarbeiten.

Verwenden Sie Variablen nur sparsam. Wenn Sie Prozesse mit langer Lebensdauer verwenden, wird bei jeder Prozessinstanz für jede Variable im Prozess Speicherplatz in der Datenbank zugewiesen. Wenn Sie Variablen strategisch verwenden, können Sie viel Speicherplatz sparen. Sie können beispielsweise Variablenwerte überschreiben, wenn alte Werte nicht mehr in dem Prozess benötigt werden. Und Sie können alle von Ihnen erstellten Variablen, die Sie nicht mehr verwenden, löschen. Sie können den Prozess überprüfen, um nicht verwendete Variablen zu suchen.

Verwenden Sie einfache Variablentypen (z. B. String oder Int) und vermeiden Sie es, wo immer möglich, komplexe Variablentypen zu verwenden. Speicherplatz in der Datenbank wird Variablen auch dann zugewiesen, wenn diese keinen Wert enthalten. Komplexe Variablen erfordern in der Regel mehr Speicherplatz als einfache Variablen.

## Tipps zur Produktverwaltung {#product-administration-tips}

Verwenden Sie den Stammordner des globalen Dokumentenspeichers (GDS) effizient. Der GDS-Stammordner auf dem Forms-Server wird unter anderem zum Speichern von Dateien, die an Dienste übergeben werden, die Teil von AEM Forms in Prozessen sind, verwendet. Zum Verbessern der Leistung werden kleinere Dokumente stattdessen im Arbeitsspeicher gespeichert und bleiben in der Datenbank erhalten.

Administration Console stellt die Eigenschaft „Standardmäßige Maximalgröße für Inline-Dokumente“ zum Konfigurieren der Maximalgröße von Dokumenten bereit, die im Arbeitsspeicher gespeichert werden und in der Datenbank erhalten bleiben. (Siehe [Allgemeine AEM Forms-Einstellungen konfigurieren](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings).) Wenn Sie diese Eigenschaft auf einen niedrigen Wert festgelegt haben, bleiben die meisten Dokumente im GDS-Ordner und nicht in der Datenbank erhalten. Der Vorteil besteht darin, dass Sie die Dateien, wenn sie im GDS-Ordner gespeichert sind, leichter löschen können, wenn Sie sie nicht mehr benötigen.
