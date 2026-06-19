---
title: Beheben von Serialisierungsproblemen in AEM Forms JEE | Adobe Experience Manager
description: Erfahren Sie, wie Sie Java-Deserialisierungsprobleme in AEM Forms JEE beheben, wenn es auf JDK 8 ausgeführt wird.
solution: Experience Manager, Experience Manager Forms
feature: Security
version: Experience Manager 6.5
type: Documentation
role: Admin
source-git-commit: ec3941675081255879065c3be9d5af77474b2072
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 1%

---


# Beheben von Serialisierungsproblemen in AEM Forms JEE {#mitigating-serialization-issues-in-aem-forms-jee}

AEM Forms JEE enthält eine Deserialisierungs-Firewall, die vor jedem Deserialisierungsversuch eines Objekts eine Preflight-Prüfung hinzufügt. Diese Prüfung testet einen Klassennamen anhand einer Firewall-ähnlichen Zulassungsliste, oder beidem und lehnt Klassen ab, die bekanntermaßen durch Java™-Deserialisierungsangriffe ausnutzbar sind. Der zugrunde liegende Agent ist Adobes modifizierte Distribution des Open-Source-Projekts [NotSoSerial](https://github.com/kantega/notsoserial), das unter der [Apache 2-Lizenz](https://www.apache.org/licenses/LICENSE-2.0) lizenziert ist.

Bei Installationen, die **JDK 11 oder höher** ausführen, wird dieser Schutz durch die native Serialisierungsfilterung der Plattform aktiviert und erfordert keine manuellen Schritte. In Installationen, die **JDK 8** ausführen, ist die native Serialisierungsfilterung nicht wirksam, sodass der Agent beim Start explizit an die JVM angehängt werden muss. In diesem Artikel wird beschrieben, wie Sie dies tun können.

>[!NOTE]
>
>Wenn die Konsistenzprüfung des Deserialisierungsfilters bereits als auf Ihrem Server aktiv gemeldet wird (siehe [Überprüfen der Agenten-Aktivierung](#verifying-the-agents-activation)), ist Ihr Anwendungsserver bereits geschützt und Sie können die verbleibenden Schritte in diesem Dokument überspringen.

## Bevor Sie beginnen {#before-you-begin}

Bestätigen Sie die Java™-Version, mit der Ihr Anwendungs-Server ausgeführt wird:

```shell
java -version
```

Wenn die gemeldete Version `1.8.x` (JDK 8) ist, gelten die Schritte in diesem Artikel. Wenn es 11 oder höher ist, ist keine manuelle Aktion erforderlich. Überprüfen Sie den Schutz mithilfe der Konsistenzprüfung, die unter [Überprüfen der Agenten-Aktivierung“ beschrieben &#x200B;](#verifying-the-agents-activation).

In den folgenden Schritten bezieht sich `<jee-installation-directory>` auf den Stamm Ihrer AEM Forms JEE-Installation.

## Anwenden des Agenten {#applying-the-agent}

>[!IMPORTANT]
>
>Für diese Schritte ist ein Neustart des Anwendungsservers erforderlich. Wenden Sie sie auf jede betroffene Instanz an.

1. **Überprüfen Sie den aktuellen Status.** Navigieren Sie zur Konsistenzprüfung des Deserialisierungsfilters:

   ```text
   https://<server>:<port>/system/console/healthcheck?tags=deserialization
   ```

   Wenn die Prüfung als aktiv meldet, ist die Instanz bereits geschützt und es sind keine weiteren Maßnahmen erforderlich. Wenn er fehlschlägt, fahren Sie mit den folgenden Schritten fort.

1. **Überprüfen Sie, ob die Agent-JAR bereits vorhanden ist.** Suchen Sie unter dem folgenden Speicherort nach `notsoserial.jar`:

   ```text
   <jee-installation-directory>/crx-quickstart/opt/notsoserial/
   ```

1. **Fügen Sie die JAR-Datei hinzu, wenn sie fehlt.** Laden Sie [`notsoserial.jar`](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/notsoserial.jar) herunter und kopieren Sie es in den oben genannten Ordner für jede Instanz:

   ```text
   <jee-installation-directory>/crx-quickstart/opt/notsoserial/notsoserial.jar
   ```

   >[!NOTE]
   >
   >Ersetzen Sie diesen Schritt durch den offiziellen Adobe-Download-Speicherort für die Forms JEE-Distribution des Agenten vor der Veröffentlichung.

1. **Aktualisieren Sie die JVM** Startparameter Ihres Anwendungsservers, um den Agenten anzuhängen. Fügen Sie die folgende Option zur Java™-Ausführungszeile hinzu:

   ```shell
   -javaagent:<jee-installation-directory>/crx-quickstart/opt/notsoserial/notsoserial.jar
   ```

   Der genaue Speicherort der Java™-Ausführungszeile hängt von Ihrem Anwendungsserver ab (z. B. JBoss, WebLogic oder WebSphere®). Fügen Sie die Option den JVM-Optionen hinzu, die zum Starten des AEM Forms JEE-Anwendungsservers verwendet werden.

1. **Starten Sie den JEE-Server neu** sodass der Agent beim JVM-Start geladen wird.

1. **Erneut überprüfen.** Navigieren Sie erneut zur Konsistenzprüfung:

   ```text
   https://<server>:<port>/system/console/healthcheck?tags=deserialization
   ```

   Die Konsistenzprüfung sollte jetzt als fehlerfrei gemeldet werden.

## Überprüfen der Agenten-Aktivierung {#verifying-the-agents-activation}

Sie können die Konfiguration des Deserialisierungsagenten jederzeit überprüfen, indem Sie die folgende URL aufrufen:

```text
https://<server>:<port>/system/console/healthcheck?tags=deserialization
```

Eine Liste mit Konsistenzprüfungen für den Agenten wird angezeigt. Wenn die Prüfungen bestanden werden, wird der Agent ordnungsgemäß aktiviert. Wenn sie auf einer JDK 8-Instanz fehlschlagen, wurde der Agent nicht geladen, und Sie müssen ihn manuell unter Verwendung der Schritte in [Anwenden des Agenten“ &#x200B;](#applying-the-agent).

## Konfigurieren des Agenten {#configuring-the-agent}

Die folgenden Schritte gelten, wenn die Java™-Version Ihres Anwendungsservers mit JDK 8 ausgeführt wird. Sie können den Agenten konfigurieren, nachdem Sie ihn angehängt haben, und ihn laden, indem Sie die Schritte in [Anwenden des Agenten](#applying-the-agent) ausführen.

Die Standardkonfiguration ist für die meisten Installationen ausreichend. Es enthält eine Blockierungsliste von bekannten remote verwertbaren Klassen und eine Zulassungsliste von Paketen, in denen die Deserialisierung vertrauenswürdiger Daten sicher ist. Die Blockierungsliste wird vor allen auf die Zulassungsliste gesetzt Einträgen angewendet.

Die Firewall-Konfiguration ist dynamisch und kann jederzeit geändert werden:

1. Wechseln Sie zur Web-Konsole unter `https://<server>:<port>/system/console/configMgr`.

1. Suchen Sie nach „Deserialisierungs **Firewallkonfiguration“ und klicken Sie**.

Diese Konfiguration enthält die Optionen für die Zulassungsliste-, Blockierungsliste- und Diagnoseprotokollierung:

* **Zulassungsauflistung** - Klassen oder Paketpräfixe, die für die Deserialisierung zulässig sind. Wenn Sie eigene Klassen deserialisieren, fügen Sie hier die entsprechenden Klassen oder Pakete hinzu.
* **Blockierungsauflistung** - Klassen, die nie für die Deserialisierung zugelassen sind. Der anfängliche Satz ist auf Klassen beschränkt, die für Remoteausführungsangriffe anfällig sind.
* **Diagnoseprotokollierung** - Optionen zum Protokollieren bei Deserialisierung. Der Standardwert **class-name-only** meldet die Klassen, die deserialisiert werden. Die **full-stack**-Option protokolliert einen Java™-Stack für den ersten Deserialisierungsversuch, der nützlich ist, um nicht vertrauenswürdige Deserialisierungen in Ihrer Verwendung zu finden und zu entfernen. Diese Optionen werden nur bei der ersten Verwendung protokolliert.

## Weitere Überlegungen {#other-considerations}

* Der Agent dient der Abmilderung derzeit bekannter Klassen mit Sicherheitsrisiko. Wenn Ihr Projekt nicht vertrauenswürdige Daten deserialisiert, kann es dennoch Denial-of-Service-, Speichermangel- oder unbekannten zukünftigen Deserialisierungs-Angriffen ausgesetzt sein.
* Wenn Sie statt auf einem JDK (Java™ Runtime Environment) auf einem JRE (Java™ Development Kit) ausführen, sind die für das dynamische Laden des Agenten erforderlichen Tools nicht verfügbar und der Agent muss beim Start manuell angehängt werden, wie in [Anwenden des Agenten](#applying-the-agent) beschrieben.
* Wenn Sie auf einer IBM® JVM ausführen, lesen Sie die Dokumentation zur Unterstützung der Java™ Attach-API.
