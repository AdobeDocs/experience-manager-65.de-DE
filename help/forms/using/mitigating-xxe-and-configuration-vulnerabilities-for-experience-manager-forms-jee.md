---
title: Behebung der Sicherheitslücken bei XXE, der Struts-Dev-Modus-Konfiguration und der Remote-Code-Ausführung für AEM Forms auf JEE
description: Behebung der Sicherheitslücken bei XXE, Konfiguration und Remote-Code-Ausführung für AEM Forms auf JEE
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Security
geptopics: SG_AEMFORMS/categories/jee
role: Admin
exl-id: 9fade12f-a038-4fd6-8767-1c30966574c5
solution: Experience Manager, Experience Manager Forms
release-date: 2025-08-05T00:00:00Z
source-git-commit: 3f64cfa688ef1f0090b7ce0d821324593cbea693
workflow-type: ht
source-wordcount: '675'
ht-degree: 100%

---

# Fehlerbehebung bei RCE (CVE-2025-49533), der Struts-Dev-Modus-Konfiguration (CVE-2025-54253), XXE (CVE-2025-54254) und Sicherheitslücken für AEM Forms auf JEE {#mitigating-xxe-configuration-rce-vulnerabilities-aem-forms}

## Kurzübersicht

| **Auswirkungsgrad** | **Betroffene Versionen** | **Empfohlene Aktion** |
|---|---|---|
| **Kritisch** | AEM 6.5 Forms auf JEE Service Pack 23 (6.5.23.0) | [Neuesten Hotfix installieren](#option-1-for-users-on-version-65230-install-latest-hotfix) |
| **Kritisch** | AEM 6.5 Forms auf JEE Service Pack 18 bis 22 (6.5.18.0–6.5.22.0) | [Fehlerbehebungen manuell installieren](#option-2-for-users-on-65180---65220-manual-hotfix-installation) |
| **Kritisch** | AEM 6.5 Forms auf JEE Service Pack 17 (6.5.17.0) oder früher | Aktualisieren Sie auf eine unterstützte Service Pack-Version und wenden Sie dann die empfohlenen Schritte zur Risikominderung für Ihre neue Version an |
| **Nicht betroffen** | AEM Forms on OSGi, Workbench, Cloud Service | Keine Aktion erforderlich. |

**Behobene Sicherheitslücken:**

- Remote-Code-Ausführung (CVE-2025-49533)
- Konfigurationsprobleme (CVE-2025-54253)
- Verarbeitung von XML External Entity (XXE) (CVE-2025-54254)

## Überblick

### Betroffene Elemente

| Schwachstelle | Auswirkungen | Betroffene Komponenten |
|---|---|---|
| **CVE-2025-49533**: Remote-Code-Ausführung | Ausführung von nicht authentifiziertem Code in GetDocumentServlet | AEM 6.5 Forms on JEE Service Pack 23 (6.5.23.0) und früher |
| **CVE-2025-54253**: Konfigurationsprobleme | Struts-Entwicklungsmodus in der Admin-Benutzeroberfläche aktiviert | AEM 6.5 Forms on JEE Service Pack 23 (6.5.23.0) und früher |
| **CVE-2025-54254**: XXE-Verarbeitung | Das Modul „Dokumentensicherheit“ ermöglicht unbefugten Dateizugriff | AEM 6.5 Forms on JEE Service Pack 23 (6.5.23.0) und früher |


### Was nicht betroffen ist

- Experience Manager Forms Workbench (alle Versionen)
- Experience Manager Forms auf OSGi (alle Versionen)
- Experience Manager Forms as a Cloud Service

## Optionen zur Auflösung


### Bevor Sie beginnen

Bevor Sie Änderungen vornehmen, sichern Sie die EAR- oder DSC-Datei, die Sie ändern oder aktualisieren möchten:

- Suchen Sie dazu die ursprüngliche EAR- oder DSC-Datei in Ihrem Bereitstellungsverzeichnis.
- Kopieren Sie die Datei an einen sicheren Sicherungsspeicherort außerhalb des Bereitstellungsverzeichnisses.
- Stellen Sie sicher, dass die Sicherung abgeschlossen ist und zugänglich ist, bevor Sie mit Aktualisierungen fortfahren.

Dank dieser Vorsichtsmaßnahme können Sie den Originalzustand wiederherstellen, falls während des Aktualisierungsprozesses Probleme auftreten.

### Option 1: (Für Benutzende mit Version 6.5.23.0) Neuesten Hotfix installieren

1. [Laden Sie den Hotfix für 6.5.23.0](/help/release-notes/aem-forms-hotfix.md) herunter.
1. Befolgen Sie die standardmäßigen [Hotfix/Patch-Installationsanweisungen](/help/release-notes/jee-patch-installer-65.md)
1. Wenn Sie die Dokumentensicherheit (früher Rights Management) auf IBM WebSphere oder Oracle WebLogic verwenden, legen Sie die folgende Java-Systemeigenschaft (JVM-Argument) fest, bevor Sie den AEM Forms-Server starten:

   ```
   -Dcom.adobe.forms.jee.services.allowDoctypeDeclaration=true
   ```

1. Starten Sie den Anwendungs-Server neu.

### Option 2: (Für Benutzende auf 6.5.18.0 – 6.5.22.0) Manuelle Hotfix-Installation

+++Manuelle Hotfix-Installation für 6.5.18.0 bis 6.5.22.0

**Schritt 1: Herunterladen und Extrahieren des Hotfix-Pakets**

- Laden Sie den [Hotfix für 6.5.18.0 – 6.5.22.](/help/release-notes/aem-forms-hotfix.md) vom Adobe-Software-Verteilungsportal herunter.
- Lokal extrahieren

**Schritt 2: Navigieren Sie zum richtigen Versionsordner**

- Gehen Sie je nach der in Ihrer Umgebung installierten Service Pack-Version zum entsprechenden Ordner.

  Beispiel: Der Ordner für Service Pack 20 lautet:

  ```
  <extracted-hotfix>/SP20/
  ```

**Schritt 3: Suchen Sie das Bereitstellungsverzeichnis**

- Wechseln Sie auf Ihrem AEM Forms auf JEE-Server zu:

  ```
  [AEM installation directory]/deploy
  ```

  Beispiel: `adobe/adobe-experience-manager-forms/deploy`



**Schritt 4: Aktualisieren und ersetzen Sie die EAR-Dateien**

>[!BEGINTABS]

>[!TAB JBoss]

1. Öffnen Sie `adobe-core-jboss.ear` und ersetzen Sie `adminui.war` durch

   ```
   adobe-xxe-configuration-hotfix/SP[version]/jboss/adminui.war
   ```

   Zum Beispiel: `adobe-xxe-configuration-hotfix/SP20/jboss/adminui.war`

1. Wechseln Sie innerhalb von `adobe-core-jboss.ear` zum Ordner `lib/` und ersetzen Sie `adobe-uisupport.jar` durch:

   ```
   adobe-xxe-configuration-hotfix/SP[version]/adobe-uisupport.jar
   ```

   Zum Beispiel: `adobe-xxe-configuration-hotfix/SP20/adobe-uisupport.jar`

1. Speichern Sie die EAR-Datei. Stellen Sie sicher, dass die Änderungen ordnungsgemäß gespeichert werden.


1. Ersetzen Sie `adobe-edcserver-jboss.ear` durch

   ```
   adobe-xxe-configuration-hotfix/SP[version]/jboss/adobe-edcserver-jboss.ear
   ```

   Zum Beispiel: `adobe-xxe-configuration-hotfix/SP20/jboss/adobe-edcserver-jboss.ear`

1. Ersetzen Sie `adobe-forms-jboss.ear` durch

   ```
   adobe-xxe-configuration-hotfix/SP[version]/jboss/adobe-forms-jboss.ear
   ```

   Zum Beispiel: `adobe-xxe-configuration-hotfix/SP20/jboss/adobe-forms-jboss.ear`



>[!TAB WebLogic]

1. Öffnen Sie `adobe-core-weblogic.ear` und ersetzen Sie `adminui.war` durch

   ```
   adobe-xxe-configuration-hotfix/SP[version]/weblogic/adminui.war
   ```

   Zum Beispiel: `adobe-xxe-configuration-hotfix/SP20/weblogic/adminui.war`

1. Ersetzen Sie innerhalb von `adobe-core-weblogic.ear` `adobe-uisupport.jar` durch:

   ```
   adobe-xxe-configuration-hotfix/SP[version]/adobe-uisupport.jar
   ```

   Zum Beispiel: `adobe-xxe-configuration-hotfix/SP20/adobe-uisupport.jar`

1. Speichern Sie die EAR-Datei. Stellen Sie sicher, dass die Änderungen ordnungsgemäß gespeichert werden.


1. Ersetzen Sie `adobe-edcserver-weblogic.ear` durch

   ```
   adobe-xxe-configuration-hotfix/SP[version]/weblogic/adobe-edcserver-weblogic.ear
   ```

   Zum Beispiel: `adobe-xxe-configuration-hotfix/SP20/weblogic/adobe-edcserver-weblogic.ear`

1. Ersetzen Sie `adobe-forms-weblogic.ear` durch

   ```
   adobe-xxe-configuration-hotfix/SP[version]/weblogic/adobe-forms-weblogic.ear
   ```

   Zum Beispiel: `adobe-xxe-configuration-hotfix/SP20/weblogic/adobe-forms-weblogic.ear`

>[!TAB WebSphere]

1. Öffnen Sie `adobe-core-websphere.ear` und ersetzen Sie `adminui.war` durch

   ```
   adobe-xxe-configuration-hotfix/SP[version]/websphere/adminui.war
   ```

   Zum Beispiel: `adobe-xxe-configuration-hotfix/SP20/websphere/adminui.war`

1. Ersetzen Sie innerhalb von `adobe-core-websphere.ear` `adobe-uisupport.jar` durch:

   ```
   adobe-xxe-configuration-hotfix/SP[version]/adobe-uisupport.jar
   ```

   Zum Beispiel: `adobe-xxe-configuration-hotfix/SP20/adobe-uisupport.jar`

1. Speichern Sie die EAR-Datei. Stellen Sie sicher, dass die Änderungen ordnungsgemäß gespeichert werden.


1. Ersetzen Sie `adobe-edcserver-websphere.ear` durch

   ```
   adobe-xxe-configuration-hotfix/SP[version]/websphere/adobe-edcserver-websphere.ear
   ```

   Zum Beispiel: `adobe-xxe-configuration-hotfix/SP20/websphere/adobe-edcserver-websphere.ear`

1. Ersetzen Sie `adobe-forms-websphere.ear` durch

   ```
   adobe-xxe-configuration-hotfix/SP[version]/websphere/adobe-forms-websphere.ear
   ```

   Zum Beispiel: `adobe-xxe-configuration-hotfix/SP20/websphere/adobe-forms-websphere.ear`

>[!ENDTABS]



**Schritt 5: Aktualisieren Sie die Datei `adobe-rightsmanagement-<appserver>-dsc.jar` mit**

```
adobe-xxe-configuration-hotfix/SP[version]/<appserver>/adobe-rightsmanagement-<appserver>-dsc.jar
```

Zum Beispiel: `adobe-xxe-configuration-hotfix/SP20/jboss/adobe-rightsmanagement-jboss-dsc.jar`

**Schritt 6: Zusätzliche Konfiguration für die Dokumentensicherheit auf WebSphere und WebLogic**:

Wenn Sie Document Security (früher Rights Management) verwenden, legen Sie die folgende Java-Systemeigenschaft (JVM-Argument) fest, bevor Sie den AEM Forms-Server starten:

```
-Dcom.adobe.forms.jee.services.allowDoctypeDeclaration=true
```


**Schritt 7: Führen Sie den Konfigurations-Manager erneut aus**

- Starten Sie den Konfigurations-Manager, um die aktualisierte EAR-Datei erneut bereitzustellen und den Hotfix anzuwenden

+++

### Option 3: (Für Benutzende mit 6.5.17.0 und früher) Aktualisierungspfad

1. [Aktualisieren auf eine unterstützte Service Pack-Version](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md)
1. Befolgen Sie je nach Ihrer neuen Version Option 1 oder Option 2 oben

## Verweise

- [CWE-611: Unzulässige Einschränkung der XML-Referenz für externe Entitäten](https://cwe.mitre.org/data/definitions/611.html)
- [CWE-16: Konfiguration](https://cwe.mitre.org/data/definitions/16.html)
- [OWASP XXE Prevention-Schnellübersicht](https://owasp.org/www-community/vulnerabilities/XML_External_Entity_XXE_Processing)
- [Best Practices für die Adobe Experience Manager Forms-Sicherheit](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html?lang=de)