---
title: Festlegen von Timeout-Werten für die Verwendung mit Acrobat Reader DC-Erweiterungen
description: Erfahren Sie, wie Sie Timeout-Werte für die Verwendung mit Acrobat Reader DC-Erweiterungen festlegen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 0a55aab3-14a3-41ad-8533-dc2cd116a848
source-git-commit: ab3d016c7c9c622be361596137b150d8719630bd
workflow-type: ht
source-wordcount: '175'
ht-degree: 100%

---

# Festlegen von Timeout-Werten für die Verwendung mit Acrobat Reader DC-Erweiterungen  {#setting-timeout-values-for-use-with-acrobat-reader-dc-extensions}

Stellen Sie bei der Arbeit an vielen PDF-Dateien in Acrobat Reader DC-Erweiterungen sicher, dass die folgenden Timeout-Werte angemessen festgelegt sind, damit es bei Aufträgen nicht zu Zeitüberschreitungen und somit zu Fehlern kommt:

**Standard-Zeitsperre für Dokumententsorgung:**

Dieser Wert kann in der Administrationskonsole festgelegt werden. Wählen Sie „Einstellungen“ > „Core-Systemeinstellungen“ > „Konfigurationen“ aus und geben Sie einen Wert für „Standard-Zeitsperre für Dokumententsorgung“ an.

**Maximale Wartezeit des User Managers von AEM Forms:** Dieser Wert kann durch Bearbeiten der Datei config.xml festgelegt werden. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Benutzerverwaltung“ > „Konfiguration“ > „Konfigurationsdateien importieren und exportieren“ und dann auf „Exportieren“. Öffnen Sie die exportierte Datei „config.xml“ und bearbeiten Sie die folgenden Zeilen:

&lt;entry key=&quot;assertionValidityInMinutes&quot; value=&quot;600&quot;/>

&lt;entry key=&quot;SessionTimeout&quot; value=&quot;600&quot;/>

Speichern Sie die Datei „config.xml“ und importieren Sie sie wieder zurück in die Administrationskonsole.

**Maximale Wartezeit bei einer Anwendungsserversitzung:** Dieser Wert kann auf dem Anwendungsserver festgelegt werden. Weitere Informationen finden Sie in der Dokumentation des entsprechenden Anwendungsservers.
