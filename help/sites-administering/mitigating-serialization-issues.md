---
title: Beheben von Serialisierungsproblemen in AEM
seo-title: Mitigating serialization issues in AEM
description: Erfahren Sie, wie Sie Serialisierungsprobleme in AEM vermeiden können.
seo-description: Learn how to mitigate serialization issues in AEM.
uuid: c3989dc6-c728-40fd-bc47-f8427ed71a49
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: f3781d9a-421a-446e-8b49-40744b9ef58e
exl-id: 01e9ab67-15e2-4bc4-9b8f-0c84bcd56862
source-git-commit: 614c4c88f3f09feb5a400ade9f45f634ac4fbcd5
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 30%

---

# Beheben von Serialisierungsproblemen in AEM{#mitigating-serialization-issues-in-aem}

## Überblick {#overview}

Das AEM-Team in der Adobe arbeitete eng mit dem Open-Source-Projekt zusammen [NotSoSerial](https://github.com/kantega/notsoserial) zur Behebung der in **CVE-2015-7501**. NotSoSerial ist unter der [Apache 2-Lizenz](https://www.apache.org/licenses/LICENSE-2.0) lizenziert und beinhaltet ASM-Code, der unter der eigenen [BSD-ähnlichen Lizenz](https://asm.ow2.io/) lizenziert ist.

Bei der in diesem Paket enthaltenen Agent-JAR-Datei handelt es sich um die modifizierte NotSoSerial-Distribution von Adobe.

NotSoSerial ist eine Java™-Level-Lösung für ein Java™-Level-Problem und ist nicht AEM-spezifisch. Sie fügt einem Deserialisierungsversuch für ein Objekt eine Preflight-Prüfung hinzu. Diese Prüfung testet einen Klassennamen anhand einer Zulassungsliste im Firewall-Stil, einer Blockierungsliste oder beidem. Aufgrund der begrenzten Anzahl von Klassen in der standardmäßigen Blockierungsliste ist es unwahrscheinlich, dass dieser Test Auswirkungen auf Ihre Systeme oder Ihren Code hat.

Standardmäßig führt der Agent eine Überprüfung der Blockierungsliste anhand der aktuellen bekannten anfälligen Klassen durch. Diese Blockierungsliste soll Sie vor der aktuellen Liste der Exploits schützen, die diese Art von Verwundbarkeit nutzen.

Die Blockierungsliste- und Zulassungsliste-Konfiguration kann gemäß den Anweisungen im Abschnitt [Konfigurieren des Agenten](/help/sites-administering/mitigating-serialization-issues.md#configuring-the-agent) Abschnitt dieses Artikels.

Der Agent soll dazu beitragen, die neuesten bekannten gefährdeten Klassen zu reduzieren. Wenn Ihr Projekt nicht vertrauenswürdige Daten deserialisiert, kann es dennoch anfällig für Denial-of-Service-Angriffe, Speicherangriffe und unbekannte zukünftige Deserialisierungs-Exploits sein.

Adobe unterstützt offiziell Java™ 6, 7 und 8. Nach Auffassung der Adobe unterstützt NotSoSerial jedoch auch Java™ 5.

## Installieren des Agenten {#installing-the-agent}

>[!NOTE]
>
>Wenn Sie den Serialisierungs-Hotfix für AEM 6.1 bereits installiert haben, entfernen Sie die Befehle zum Starten des Agenten aus Ihrer Java™-Ausführungszeile.

1. Installieren Sie das Bundle **com.adobe.cq.cq-serialization-tester**.

1. Navigieren Sie zur Bundle-Web-Konsole (`https://server:port/system/console/bundles`).
1. Suchen Sie nach dem Serialisierungs-Bundle und starten Sie es. Dadurch wird der NotSoSerial-Agent dynamisch automatisch geladen.

## Installieren des Agenten auf Anwendungs-Servern {#installing-the-agent-on-application-servers}

Der NotSoSerial-Agent ist nicht in der AEM-Standarddistribution für Anwendungs-Server enthalten. Sie können es jedoch aus der AEM JAR-Distribution extrahieren und mit Ihrem Anwendungsserver-Setup verwenden:

1. Laden Sie zunächst die AEM Schnellstartdatei herunter und extrahieren Sie sie:

   ```shell
   java -jar aem-quickstart-6.2.0.jar -unpack
   ```

1. Navigieren Sie zum Speicherort des gerade entpackten Schnellstarts und kopieren Sie den Ordner `crx-quickstart/opt/notsoserial/` in den Ordner `crx-quickstart` der AEM-Anwendungs-Server-Installation.

1. Legen Sie den Benutzer, der den Server betreibt, als Besitzer von `/opt` fest:

   ```shell
   chown -R opt <user running the server>
   ```

1. Konfigurieren Sie den Agenten und vergewissern Sie sich, dass er ordnungsgemäß aktiviert wurde, wie in den folgenden Abschnitten dieses Artikels gezeigt.

## Konfigurieren des Agenten {#configuring-the-agent}

Die Standardkonfiguration ist für die meisten Installationen ausreichend. Diese Konfiguration umfasst eine Blockierungsliste bekannter anfälliger Remote-Klassen und eine Zulassungsliste von Paketen, in denen die Deserialisierung vertrauenswürdiger Daten sicher ist.

Die Firewall-Konfiguration ist dynamisch und kann jederzeit wie folgt geändert werden:

1. Wechseln zur Web-Konsole unter `https://server:port/system/console/configMgr`
1. Suchen nach und Klicken **Deserialisierungs-Firewall-Konfiguration.**

   >[!NOTE]
   Sie können die Konfigurationsseite auch direkt erreichen, indem Sie auf die URL zugreifen:
   * `https://server:port/system/console/configMgr/com.adobe.cq.deserfw.impl.DeserializationFirewallImpl`


Diese Konfiguration enthält die Zulassungsliste, die Blockierungsliste und die Deserialisierungs-Protokollierung.

**Zulassungslisten**

Im Abschnitt zur Zulassungsauflistung sind diese Auflistungen Klassen oder Paketpräfixe, die zur Deserialisierung zugelassen sind. Wenn Sie eigene Klassen deserialisieren, fügen Sie entweder die Klassen oder Pakete zu dieser Zulassungsliste hinzu.

**Blockierungslisten**

Im Abschnitt zur Blockierungsauflistung finden Sie Klassen, die nie zur Deserialisierung zugelassen werden. Standardmäßig umfasst die Liste nur Klassen, die für Remoteausführungsangriffe anfällig sind. Die Blockierungsliste &quot;&quot;wird vor allen in der Zulassungsliste aufgeführten Einträgen angewendet.

**Diagnostische Protokollierung**

Im Abschnitt zur Diagnoseprotokollierung können Sie mehrere Optionen auswählen, die protokolliert werden sollen, wenn eine Deserialisierung stattfindet. Diese Optionen werden nur bei der ersten Verwendung protokolliert und bei nachfolgenden Verwendungen nicht erneut protokolliert.

Der Standardwert von **class-name-only** informiert Sie über die Klassen, die deserialisiert werden.

Sie können auch die **Vollstapel** -Option, die einen Java™-Stapel des ersten Deserialisierungsversuchs protokolliert, um Sie darüber zu informieren, wo Ihre Deserialisierung stattfindet. Diese Option ist nützlich, um Deserialisierungen aus Ihrer Verwendung zu finden und zu entfernen.

## Überprüfen der Agenten-Aktivierung {#verifying-the-agent-s-activation}

Die Konfiguration des Deserialisierungs-Agenten kann unter folgender URL geprüft werden:

* `https://server:port/system/console/healthcheck?tags=deserialization`

Nachdem Sie auf die URL zugegriffen haben, wird eine Liste mit Konsistenzprüfungen im Zusammenhang mit dem Agenten angezeigt. Sie können feststellen, ob der Agent ordnungsgemäß aktiviert ist, indem Sie überprüfen, ob die Konsistenzprüfungen erfolgreich sind. Wenn sie fehlschlagen, müssen Sie den Agenten manuell laden.

Weitere Informationen zum Behandeln von Problemen mit dem Agenten finden Sie weiter unten unter [Behandeln von Fehlern beim dynamischen Laden des Agenten](#handling-errors-with-dynamic-agent-loading).

>[!NOTE]
Wenn Sie `org.apache.commons.collections.functors` auf die Zulassungsliste klicken, schlägt die Konsistenzprüfung immer fehl.

## Behandeln von Fehlern beim dynamischen Laden des Agenten {#handling-errors-with-dynamic-agent-loading}

Wenn Fehler im Protokoll angezeigt werden oder die Überprüfungsschritte ein Problem beim Laden des Agenten erkennen, laden Sie den Agenten manuell. Dieser Workflow wird auch empfohlen, wenn Sie JRE (Java™ Runtime Environment) anstelle eines JDK (Java™ Development Toolkit) verwenden, da die Tools für das dynamische Laden nicht verfügbar sind.

Gehen Sie wie folgt vor, um den Agenten manuell zu laden:

1. Bearbeiten Sie die JVM-Startparameter der CQ-JAR-Datei und fügen Sie die folgende Option hinzu:

   ```shell
   -javaagent:<aem-installation-folder>/crx-quickstart/opt/notsoserial/notsoserial.jar
   ```

   >[!NOTE]
   Erfordert, dass Sie auch die Option -nofork CQ/AEM zusammen mit den entsprechenden JVM-Speichereinstellungen verwenden, da der Agent auf einer abgespalteten JVM nicht aktiviert ist.

   >[!NOTE]
   Die Adobe-Distribution der JAR-Datei des NotSoSerial-Agenten finden Sie im Ordner `crx-quickstart/opt/notsoserial/` Ihrer AEM-Installation.

1. Beenden Sie die JVM-Instanz und starten Sie sie neu.

1. Überprüfen Sie mithilfe der unter [Überprüfen der Agenten-Aktivierung](/help/sites-administering/mitigating-serialization-issues.md#verifying-the-agent-s-activation) beschriebenen Schritte erneut die Aktivierung des Agenten.

## Weitere Überlegungen {#other-considerations}

Wenn Sie mit einer IBM® JVM arbeiten, lesen Sie die Dokumentation zur Unterstützung der Java™ Attach-API unter [dieser Speicherort](https://www.ibm.com/docs/en/sdk-java-technology/8?topic=documentation-java-attach-api).
