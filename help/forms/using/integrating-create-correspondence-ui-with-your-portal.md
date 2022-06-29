---
title: Integrieren der Benutzeroberfläche „Korrespondenz erstellen“ in Ihr benutzerdefiniertes Portal
seo-title: Integrating Create Correspondence UI with your custom portal
description: Erfahren Sie, wie Sie die Benutzeroberfläche „Korrespondenz erstellen“ in Ihr benutzerdefiniertes Portal integrieren.
seo-description: Learn how to integrate create correspondence UI with your custom portal
uuid: 68ef5bf2-b271-4c44-8840-6c495069164d
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
discoiquuid: 0d3bb98e-7139-4d8e-b110-6ebd11debda1
docset: aem65
feature: Correspondence Management
exl-id: c3b6ee31-ccbb-4446-86c8-f618226fefc4
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '413'
ht-degree: 100%

---

# Integrieren der Benutzeroberfläche „Korrespondenz erstellen“ in Ihr benutzerdefiniertes Portal{#integrating-create-correspondence-ui-with-your-custom-portal}

## Übersicht {#overview}

In diesem Artikel wird erläutert, wie Sie die Lösung „Korrespondenz erstellen“ in Ihre Umgebung integrieren können.

## URL-basierter Aufruf {#url-based-invocation}

Eine Möglichkeit, die Anwendung „Korrespondenz erstellen“ von einem Clusterportal aufzurufen, ist die URL mit folgenden Anforderungsparametern vorzubereiten:

* die Kennung für die Briefvorlage (mithilfe des cmLetterId-Parameters).

* die URL für die XML-Datei, die aus der gewünschten Datenquelle (unter Verwendung des cmDataUrl-Parameters) erfasst wurde

Beispielsweise würde das benutzerdefinierte Portal die URL als\
`https://'[server]:[port]'/[contextPath]/aem/forms/createcorrespondence.html?random=[timestamp]&cmLetterId=[letter identifier]&cmDataUrl=[data URL]` vorbereiten, wobei es sich um die href eines Links auf dem Portal handeln könnte.

>[!NOTE]
>
>Den Aufruf auf diese Weise durchzuführen, ist nicht sicher, da die erforderlichen Parameter als eine GET-Anforderung übergeben werden, indem die Parameter (sichtbar) in der URL offengelegt werden.

>[!NOTE]
>
>Bevor Sie die Anwendung „Korrespondenz erstellen“ aufrufen, speichern und laden Sie die Daten, um die Benutzeroberfläche „Korrespondenz erstellen“ unter der angegebenen URL aufzurufen. Dies kann entweder vom benutzerdefinierten Portal aus oder über einen anderen Vorgang im Back-End ausgeführt werden.

## Auf Daten basierter Inline-Aufruf {#inline-data-based-invocation}

Eine weitere (und sicherere) Möglichkeit, die Anwendung „Korrespondenz erstellen“ aufzurufen, besteht darin, die URL https://&#39;[server]:[port]&#39;/[contextPath]/aem/forms/createcorrespondence.html aufzurufen, während die Parameter und Daten zum Aufrufen der Anwendung „Korrespondenz erstellen“ als POST-Anforderung gesendet werden (wodurch sie vor dem Endbenutzer versteckt werden). Dies bedeutet auch, dass Sie jetzt die XML-Datei für die Anwendung „Korrespondenz erstellen“ „inline“ (als Teil der gleichen Anforderung, unter Verwendung des cmData-Parameters) übergeben können, was bei der vorigen Herangehensweise nicht möglich/ideal war.

### Parameter für das Festlegen des Briefs {#parameters-for-specifying-letter}

| **Name** | **Typ** | **Beschreibung** |
|---|---|---|
| cmLetterInstanceId | Zeichenfolge | Der Bezeichner für die Briefinstanz. |
| cmLetterId | Zeichenfolge | Der Name der Briefvorlage. |

Die Reihenfolge der Parameter in der Tabelle gibt die Voreinstellungen von Parametern an, die zum Laden des Briefs verwendet werden.

### Parameter für die Angabe der XML-Datenquelle {#parameters-for-specifying-the-xml-data-source}

<table>
 <tbody>
  <tr>
   <td><strong>Name</strong></td> 
   <td><strong>Typ</strong></td> 
   <td><strong>Beschreibung</strong></td> 
  </tr>
  <tr>
   <td>cmDataUrl<br /> </td> 
   <td>URL</td> 
   <td>XML-Daten aus einer Quelldatei, die Standardprotokolle wie CQ, FTP, HTTP oder FILE verwenden.<br />  </td> 
  </tr>
  <tr>
   <td>cmLetterInstanceId</td> 
   <td>Zeichenfolge</td> 
   <td>Verwenden von XML-Daten, die in der Briefinstanz verfügbar sind.</td> 
  </tr>
  <tr>
   <td>cmUseTestData</td> 
   <td>Boolesch</td> 
   <td>Um die Testdaten wiederzuverwenden, die im Datenwörterbuch angehängt sind.</td> 
  </tr>
 </tbody>
</table>

Die Reihenfolge der Parameter in der Tabelle gibt die Voreinstellungen von Parametern an, die zum Laden der XML-Daten verwendet werden.

### Andere Parameter {#other-parameters}

<table>
 <tbody>
  <tr>
   <td><strong>Name</strong></td> 
   <td><strong>Typ</strong></td> 
   <td><strong>Beschreibung</strong></td> 
  </tr>
  <tr>
   <td>cmPreview<br /> </td> 
   <td>Boolesch</td> 
   <td>„True“, um den Brief im Vorschaumodus zu öffnen<br />  </td> 
  </tr>
  <tr>
   <td>Willkürlich</td> 
   <td>Zeitstempel</td> 
   <td>Um das Problem des Browser Caching zu lösen</td> 
  </tr>
 </tbody>
</table>

Wenn Sie ein HTTP- oder CQ-Protokoll für cmDataURL verwenden, muss die HTTP/CQ-URL anonym zugänglich sein.
