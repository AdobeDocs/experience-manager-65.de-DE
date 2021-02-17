---
title: Beheben von Serialisierungsproblemen in AEM
seo-title: Beheben von Serialisierungsproblemen in AEM
description: Hier erfahren Sie, wie Sie Serialisierungsprobleme in AEM beheben.
seo-description: Hier erfahren Sie, wie Sie Serialisierungsprobleme in AEM beheben.
uuid: c3989dc6-c728-40fd-bc47-f8427ed71a49
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: f3781d9a-421a-446e-8b49-40744b9ef58e
translation-type: tm+mt
source-git-commit: 3cbbad3ce9d93a353f48fc3206df989a8bf1991a
workflow-type: tm+mt
source-wordcount: '969'
ht-degree: 66%

---


# Beheben von Serialisierungsproblemen in AEM{#mitigating-serialization-issues-in-aem}

## Überblick {#overview}

 Das AEM-Team von Adobe arbeitet eng mit dem Open-Source-Projekt [NotSoSerial](https://github.com/kantega/notsoserial) zusammen, um Sie bei der Behandlung der in **CVE-2015-7501** beschriebenen Sicherheitsrisiken zu unterstützen. NotSoSerial ist unter der [Apache 2-Lizenz](https://www.apache.org/licenses/LICENSE-2.0) lizenziert und beinhaltet ASM-Code, der unter der eigenen [BSD-ähnlichen Lizenz](https://asm.ow2.org/license.html) lizenziert ist.

Bei der in diesem Paket enthaltenen Agent-JAR-Datei handelt es sich um die modifizierte NotSoSerial-Distribution von Adobe.

NotSoSerial ist eine Lösung auf Java-Ebene für ein Problem auf Java-Ebene und nicht AEM-spezifisch. Sie fügt einem Deserialisierungsversuch für ein Objekt eine Preflight-Prüfung hinzu. Mit dieser Prüfung wird ein Klassenname gegen eine Firewall-ähnliche Zulassungsliste und/oder Blockierungsliste getestet. Aufgrund der begrenzten Anzahl von Klassen in der Standardklasse ist es unwahrscheinlich, dass sich dies auf Ihre Blockierungslisten oder Ihren Code auswirkt.

Standardmäßig führt der Agent eine Blockierungsliste-Prüfung für aktuelle bekannte verwundbare Klassen durch. Diese Blockierungsliste soll Sie vor der aktuellen Liste von Exploits schützen, die diese Art von Verwundbarkeit nutzen.

Die Blockierungsliste und Zulassungsliste können gemäß den Anweisungen im Abschnitt [Konfigurieren des Agenten](/help/sites-administering/mitigating-serialization-issues.md#configuring-the-agent) dieses Artikels konfiguriert werden.

Der Agent unterstützt Sie bei der Behandlung der neuesten bekannten Klassen mit Sicherheitsrisiko. Wenn Ihr Projekt nicht vertrauenswürdige Daten deserialisiert, ist es unter Umständen weiterhin anfällig für Denial-of-Service-Angriffe, Out-of-Memory-Angriffe und bislang noch unbekannte Deserialisierungs-Exploits.

Adobe unterstützt offiziell Java 6, 7 und 8. Nach unserem Kenntnisstand unterstützt NotSoSerial aber auch Java 5.

## Installieren des Agents {#installing-the-agent}

>[!NOTE]
>
>Falls Sie bereits das Serialisierungshotfix für AEM 6.1 installiert haben, entfernen Sie die Startbefehle für den Agent aus Ihrer Java-Ausführungszeile.

1. Installieren Sie das Bundle **com.adobe.cq.cq-serialization-tester**.

1. Wechseln Sie zur Bundle Web Console unter `https://server:port/system/console/bundles`
1. Suchen Sie nach dem Serialisierungsbundle und starten Sie es. Daraufhin wird der NotSoSerial-Agent automatisch dynamisch geladen.

## Installieren des Agents auf Anwendungsservern {#installing-the-agent-on-application-servers}

Der NotSoSerial-Agent ist nicht in der Standardverteilung von AEM für Anwendungsserver enthalten. Sie können ihn jedoch aus der AEM-JAR-Distribution extrahieren und mit Ihrer Anwendungsservereinrichtung verwenden:

1. Laden Sie zuerst die AEM-Schnellstartdatei herunter und extrahieren Sie sie:

   ```shell
   java -jar aem-quickstart-6.2.0.jar -unpack
   ```

1. Wechseln Sie zum Speicherort des neu entpackten AEM Schnellstarts und kopieren Sie den Ordner `crx-quickstart/opt/notsoserial/` in den Ordner `crx-quickstart` der Installation des AEM Anwendungsservers.

1. Ändern Sie das Eigentumsrecht an `/opt` in den Benutzer, der den Server ausführt:

   ```shell
   chown -R opt <user running the server>
   ```

1. Konfigurieren Sie den Agent und vergewissern Sie sich, dass er ordnungsgemäß aktiviert wurde, wie in den folgenden Abschnitten dieses Artikels gezeigt.

## Konfigurieren des Agents  {#configuring-the-agent}

Die Standardkonfiguration ist für die meisten Installationen ausreichend. Dies umfasst eine Blockierungsliste bekannter, durch entfernte Ausführung verwundbarer Klassen und eine Zulassungsliste von Paketen, bei denen die Deserialisierung vertrauenswürdiger Daten relativ sicher sein sollte.

Die Firewallkonfiguration ist dynamisch und kann jederzeit wie folgt geändert werden:

1. Wechseln zur Webkonsole unter `https://server:port/system/console/configMgr`
1. Suchen Sie nach **Deserialization Firewall Configuration** und klicken Sie darauf.

   >[!NOTE]
   >
   >Die Konfigurationsseite kann auch direkt über die URL aufgerufen werden:
   >
   >* `https://server:port/system/console/configMgr/com.adobe.cq.deserfw.impl.DeserializationFirewallImpl`


Diese Konfiguration enthält die Protokollierung von Zulassungsliste, Blockierungsliste und Deserialisierung.

**Listen zulassen**

Im Abschnitt Listen zulassen sind dies Klassen oder Paket-Präfixe, die zur Deserialisierung zugelassen werden. Beachten Sie, dass Sie, wenn Sie eigene Klassen deserialisieren, entweder die Klassen oder Pakete zu dieser Zulassungsliste hinzufügen müssen.

**Blockliste**

Im Abschnitt Blockauflistungen finden Sie Klassen, die niemals deserialisiert werden dürfen. Standardmäßig umfasst die Liste nur Klassen, die für Remoteausführungsangriffe anfällig sind. Die Blockierungsliste wird vor allen zulässigen Einträgen angewendet.

**Diagnoseprotokollierung**

Im Abschnitt zur Diagnoseprotokollierung können Sie mehrere Optionen auswählen, die protokolliert werden sollen, wenn eine Deserialisierung stattfindet. Diese werden nur bei der ersten Verwendung protokolliert. Bei erneuter Verwendung findet keine erneute Protokollierung statt.

Der Standardwert **class-name-only** gibt Aufschluss über die Klassen, die deserialisiert werden.

Sie können auch die Option **full-stack** festlegen. In diesem Fall wird ein Java-Stack des ersten Deserialisierungsversuchs protokolliert, um Sie darüber zu informieren, wo Ihre Deserialisierung stattfindet. Dies kann hilfreich sein, um Deserialisierungsvorkommen zu ermitteln und zu entfernen.

## Überprüfen der Agent-Aktivierung {#verifying-the-agent-s-activation}

Die Konfiguration des Deserialisierungs-Agents kann unter folgender URL geprüft werden:

* `https://server:port/system/console/healthcheck?tags=deserialization`

Unter der URL wird eine Liste mit Integritätsprüfungen für den Agent angezeigt. Sind die Integritätsprüfungen erfolgreich, wurde der Agent ordnungsgemäß aktiviert. Im Falle eines Fehlers muss der Agent ggf. manuell geladen werden.

Weitere Informationen zum Behandeln von Problemen mit dem Agent finden Sie weiter unten unter [Behandeln von Fehlern beim dynamischen Laden des Agents](#handling-errors-with-dynamic-agent-loading).

>[!NOTE]
>
>Wenn Sie der Zulassungsliste `org.apache.commons.collections.functors` hinzufügen, schlägt die Gesundheitsprüfung immer fehl.

## Behandeln von Fehlern beim dynamischen Laden des Agents {#handling-errors-with-dynamic-agent-loading}

Wenn das Protokoll Fehler enthält oder bei den Überprüfungsschritten ein Ladeproblem für den Agent festgestellt wird, muss der Agent ggf. manuell geladen werden. Dies empfiehlt sich auch, wenn Sie anstelle eines JDK (Java Development Kit) eine JRE (Java Runtime Environment) verwenden, da in diesem Fall die Tools für dynamisches Laden nicht zur Verfügung stehen.

Gehen Sie zum manuellen Laden des Agents wie folgt vor:

1. Ändern Sie die JVM-Startparameter der CQ-JAR-Datei, indem Sie folgende Option hinzufügen:

   ```shell
   -javaagent:<aem-installation-folder>/crx-quickstart/opt/notsoserial/notsoserial.jar
   ```

   >[!NOTE]
   >
   >Dies erfordert auch die Verwendung der Option „-nofork CQ/AEM“ und der entsprechenden JVM-Arbeitsspeichereinstellungen, da der Agent für eine geforkte JVM-Instanz nicht aktiviert wird.

   >[!NOTE]
   >
   >Die Distribution der Adobe der NotSoSerial Agent JAR finden Sie im Ordner `crx-quickstart/opt/notsoserial/` Ihrer AEM.

1. Beenden Sie die JVM-Instanz und starten Sie sie neu.

1. Überprüfen Sie mithilfe der unter [Überprüfen der Agent-Aktivierung](/help/sites-administering/mitigating-serialization-issues.md#verifying-the-agent-s-activation) beschriebenen Schritte erneut die Aktivierung des Agents.

## Weitere Überlegungen  {#other-considerations}

Lesen Sie bei Verwendung einer JVM von IBM die Dokumentation zur Unterstützung der Java Attach-API. Diese finden Sie [hier](https://www.ibm.com/support/knowledgecenter/SSSTCZ_2.0.0/com.ibm.rt.doc.20/user/attachapi.html).
