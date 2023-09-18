---
title: Festlegen von Zeitüberschreitungswerten für die Verwendung mit Acrobat Reader DC-Erweiterungen
description: Erfahren Sie, wie Sie Zeitüberschreitungswerte für die Verwendung mit Acrobat Reader DC-Erweiterungen festlegen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 0a55aab3-14a3-41ad-8533-dc2cd116a848
source-git-commit: ab3d016c7c9c622be361596137b150d8719630bd
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 24%

---

# Festlegen von Zeitüberschreitungswerten für die Verwendung mit Acrobat Reader DC-Erweiterungen  {#setting-timeout-values-for-use-with-acrobat-reader-dc-extensions}

Stellen Sie bei der Arbeit an vielen PDF-Dateien in Acrobat Reader DC Extensions sicher, dass die folgenden Zeitlimitwerte angemessen festgelegt sind, um zu verhindern, dass Aufträge zeitlich nicht ausfallen und fehlschlagen:

**Standard-Zeitsperre für Entsorgung:**

Dieser Wert kann in der Administration Console festgelegt werden. Klicken Sie auf Einstellungen > Core-Systemeinstellungen > Konfigurationen und geben Sie einen Wert für Standard-Zeitüberschreitung bei Dokumentenbereitstellung an.

**Maximale Wartezeit des User Managers von AEM Forms:** Dieser Wert kann durch Bearbeiten der Datei config.xml festgelegt werden. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Konfiguration&quot;> &quot;Konfigurationsdateien importieren und exportieren&quot;und dann auf &quot;Exportieren&quot;. Öffnen Sie die exportierte Datei &quot;config.xml&quot;und bearbeiten Sie die folgenden Zeilen:

&lt;entry key=&quot;assertionValidityInMinutes&quot; value=&quot;600&quot;/>

&lt;entry key=&quot;SessionTimeout&quot; value=&quot;600&quot;/>

Speichern Sie die Datei &quot;config.xml&quot;und importieren Sie sie dann wieder in die Administration Console.

**Maximale Wartezeit bei einer Anwendungsserversitzung:** Dieser Wert kann auf dem Anwendungsserver festgelegt werden. Weitere Informationen finden Sie in der Dokumentation des entsprechenden Anwendungsservers.
