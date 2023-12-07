---
title: Aktivieren der Protokollierung für HTML5-Formulare
description: Das Protokollfunktionen-Dienstprogramm ermöglicht die Protokollierung für ein Formular und hilft Ihnen beim Debuggen von formularbezogenen Problemen.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
docset: aem65
feature: Mobile Forms
exl-id: 2f574c98-550c-4b84-be1e-46a2700e7277
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 69%

---

# Aktivieren der Protokollierung für HTML5-Formulare{#enable-logging-for-html-forms}

Sie können das Dienstprogramm der Protokollfunktion konfigurieren, um mit der Erstellung von Protokollen für HTML5-Formularen zu beginnen. Das Dienstprogramm der Protokollfunktion bietet mehrere Stufen, unter denen Sie die für Ihre Zwecke geeignete wählen können. Für HTML5-Formulare sind Server- und Client-Komponenten vorhanden. Sie können Protokolle für beide Komponenten konfigurieren.

## Serverseitige Protokollierung konfigurieren {#configuring-server-side-logging}

Führen Sie die folgenden Schritte aus, um serverseitige Protokolle zu konfigurieren:

1. Rufen Sie `https://'[server]:[port]'/system/console/configMgr` auf. Suchen Sie die Option *Apache Sling Logging Logger-Konfiguration* und öffnen Sie sie. Folgendes Dialogfeld wird angezeigt:

   ![ Dialogfeld mit Apache Sling Logging Logger-Konfigurations-Optionen](assets/logconfig.png)

   Apache Sling Logging Logger-Konfigurations-Option

1. Ändern Sie die **Protokollierungsstufe** in **Debug**.

1. Geben Sie den Namen und den Pfad der **Protokolldatei** an.

   >[!NOTE]
   >
   >Wenn Sie Protokolle im Protokollordner für HTML5-Formulare generieren möchten, stellen Sie dem Dateinamen „../logs/“ voran.

1. Ändern Sie **Logger** in **HTMLFormsPerfLogger**. Klicken Sie auf **Speichern**.

## Client-Protokollierung konfigurieren {#configuring-client-logging}

Sie können die folgenden Methoden verwenden, um die clientseitige Protokollierung in HTML5-Formularen zu aktivieren:

* Mithilfe des Anforderungsparameters `log`
* Verwenden von CQ Configuration Manager

### Aktivieren der Protokollierung mithilfe des Anforderungsparameters {#enabling-logging-using-request-parameter}

Mit dieser Methode können Sie Protokolle für eine bestimmte Anforderung generieren. Der Name des Anforderungsparameters lautet `log`. Die Protokoll-URL lautet wie folgt:

`https://<server>:<port>/content/xfaforms/profiles/test.html?contentRoot=<path of the folder containing form xdp>&template=<name of the xdp>&log=<log configuration>.`

Die Protokollkonfiguration besteht aus der Protokollebene und der Protokollfunktionskategorie.

#### Protokollziel {#log-destination}

<table>
 <tbody>
  <tr>
   <th><strong>Protokollziel</strong></th>
   <th><strong>Beschreibung</strong></th>
  </tr>
  <tr>
   <td>1</td>
   <td>Protokolle werden an den Browser weitergeleitet <strong>Konsole</strong></td>
  </tr>
  <tr>
   <td>2</td>
   <td>Die Protokolle werden in einem JavaScript-Objekt auf Client-Seite erfasst und können an den <strong>Server</strong> gesendet werden. </td>
  </tr>
  <tr>
   <td>3</td>
   <td>Beide der oben genannten Optionen<br /> </td>
  </tr>
 </tbody>
</table>

#### Protokollebenen {#log-levels}

<table>
 <tbody>
  <tr>
   <th>Protokollebene</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>0</td>
   <td>AUS<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>1</td>
   <td>FATAL<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>2</td>
   <td>ERROR<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>3</td>
   <td>WARN<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>4</td>
   <td>INFO<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>5</td>
   <td>DEBUG<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>6</td>
   <td>TRACE<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>7</td>
   <td>ALL<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

#### Protokollfunktionskategorien {#logger-categories}

<table>
 <tbody>
  <tr>
   <th>Protokollkategorie</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>eine</td>
   <td>xfa (auf Scripting-Engine bezogene Protokolle)</td>
  </tr>
  <tr>
   <td>b</td>
   <td>xfaView (auf Layout-Engine bezogene Protokolle)<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>c</td>
   <td>xfaPerf (leistungsbezogene Protokolle)<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

#### Protokollkonfiguration {#log-configuration}

In der Protokoll-URL wird der Abfragezeichenfolgenparameter für die Protokollkonfiguration wie folgt definiert:

`{destination}-{a level}-{b level}-{c level}`

Beispiel:

<table>
 <tbody>
  <tr>
   <th>Protokollkonfiguration</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>2-a4-b5-c6<br type="_moz" /> </td>
   <td>Ziel: Server<br /> xfa-Ebene: INFO<br /> xfaView-Ebene: DEBUG<br /> xfaPerf-Ebene: TRACE</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Die standardmäßige Protokollebene für jede Protokollkategorie a (xfa), b (xfaView) und c (xfaPerf) ist 2 (ERROR). Entsprechend lauten für die Protokollkonfiguration 2-b6 die Protokollebenen für verschiedene Kategorien:
>a (xfa): 2 (FEHLER der Standardebene)
>b (xfaView): 6 (vom Benutzer angegebenes TRACE)
>a (xfaPerf): 2 (FEHLER der Standardebene)

### Aktivieren der Protokollierung über den Configuration Manager {#enabling-logging-using-configuration-manager}

Wenn Sie Configuration Manager zur Aktivierung der Protokollierung verwenden, werden für jede Render-Anforderung so lange Protokolle generiert, bis die Protokollierung wieder deaktiviert wird.

1. Melden Sie sich bei CQ Configuration Manager unter `https://'[server]:[port]'/system/console/configMgr` an und melden Sie sich mit Administratorberechtigungen an.
1. Suchen Sie nach und klicken Sie auf **Mobile Forms-Konfigurationen**.
1. Geben Sie im Textfeld „Debug Options“ die Protokollkonfigurationen ein, wie sie im letzten Abschnitt beschrieben sind, z. B. **2a4-b5-c6**

   ![Formularkonfiguration](assets/forms_configuration.png)

   Formularkonfiguration

## Hochladen von Protokollen {#uploading-logs}

Wenn das Ziel auf 1 gesetzt ist, werden alle Protokollmeldungen des Client-Skripts an die Konsole weitergeleitet. Wenn ein Administrator diese Protokolle zusammen mit dem Server-Protokollen benötigt, setzen Sie die Zielebene auf 2. Auf dieser Ebene werden alle Protokolle in einem JS-Objekt auf Client-Seite erfasst. Wenn ein Formular mit einem Standardprofil gerendert wird, wird in der Symbolleiste links neben der Schaltfläche **Vorhandene Felder hervorheben** eine Schaltfläche **Protokolle senden** angezeigt. Wenn der Benutzer auf den Link klickt, werden alle erfassten Protokolle an den Server geleitet und in der konfigurierten Fehlerprotokolldatei auf dem Server protokolliert.

Standardmäßig werden alle Daten der Datei „error.log“ im Ordner „/crx-repository/logs/“ hinzugefügt.

So ändern Sie Speicherort und Namen der Protokolldatei:

1. Melden Sie sich bei Configuration Manager als Admin an. Die Standard-URL von Configuration Manager lautet `https://'[server]:[port]'/system/console/configMgr`.
1. Klicks **Apache Sling Logging Logger-Konfiguration**. Folgendes Dialogfeld wird angezeigt.

   ![logconfig-1](assets/logconfig-1.png)

1. Ändern Sie die **Protokollierungsstufe** in Debug.

1. Geben Sie Pfad und Namen der **Protokolldatei** an.

   >[!NOTE]
   >
   >Um Protokolle im selben Ordner zu erstellen, in dem bereits andere Protokolldateien enthalten sind, geben Sie in den Eigenschaften der Protokolldateien ../logs/&lt;filename> an.

1. Ändern Sie den **Logger** in **HTMLFormsPerfLogger** und klicken Sie auf **Speichern**.
