---
title: Zeitlimitwerte zur Verwendung mit Acrobat Reader DC Extensions festlegen
seo-title: Zeitlimitwerte zur Verwendung mit Acrobat Reader DC Extensions festlegen
description: Erfahren Sie, wie Sie Timeout-Werte für die Verwendung mit Acrobat Reader DC-Erweiterungen festlegen.
seo-description: Erfahren Sie, wie Sie Timeout-Werte für die Verwendung mit Acrobat Reader DC-Erweiterungen festlegen.
uuid: d6d072a0-0a30-417a-98b1-df8b4ff8f911
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: a9aeeb89-45e9-4d5d-aa25-8145c89b64f2
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 85%

---


# Zeitlimitwerte zur Verwendung mit Acrobat Reader DC Extensions festlegen  {#setting-timeout-values-for-use-with-acrobat-reader-dc-extensions}

Beim Arbeiten mit einer großen Anzahl von PDF-Dateien in Acrobat Reader DC Extensions sollten Sie sicherstellen, dass die folgenden Zeitlimitwerte entsprechend festgelegt sind, damit es bei Aufträgen nicht zu Zeitüberschreitungen und somit zu Fehlern kommt:

**Standard-Zeitsperre für Entsorgung:**

Dieser Wert kann in Administration Console festgelegt werden. Wählen Sie „Einstellungen“ > „Core-Systemeinstellungen“ > „Konfigurationen“ und geben Sie einen Wert für „Standard-Zeitsperre für Entsorgung“ an.

**User Manager AEM Forms Timeout:** Dieser Wert kann durch Bearbeiten der Datei &quot;config.xml&quot;festgelegt werden. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Konfiguration“ > „Konfigurationsdateien im- und exportieren“ und klicken Sie dann auf „Exportieren“. Öffnen Sie die exportierte Datei „config.xml“ und bearbeiten Sie die folgenden Zeilen:

&lt;entry key=&quot;assertionValidityInMinutes&quot; value=&quot;600&quot;/>

&lt;entry key=&quot;SessionTimeout&quot; value=&quot;600&quot;/>

Speichern Sie die Datei „config.xml“ und importieren Sie sie wieder zurück in Administration Console.

**Sitzungszeitlimit des Anwendungsservers:** Dieser Wert kann auf dem Anwendungsserver festgelegt werden. Weitere Informationen finden Sie in der Dokumentation des entsprechenden Anwendungsservers.
