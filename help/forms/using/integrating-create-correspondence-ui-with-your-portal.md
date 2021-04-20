---
title: Integrieren der Benutzeroberfläche „Korrespondenz erstellen“ in Ihr benutzerdefiniertes Portal
seo-title: Integrieren der Benutzeroberfläche „Korrespondenz erstellen“ in Ihr benutzerdefiniertes Portal
description: Erfahren Sie, wie Sie die Benutzeroberfläche „Korrespondenz erstellen“ in Ihr benutzerdefiniertes Portal integrieren.
seo-description: Erfahren Sie, wie Sie die Benutzeroberfläche „Korrespondenz erstellen“ in Ihr benutzerdefiniertes Portal integrieren.
uuid: 68ef5bf2-b271-4c44-8840-6c495069164d
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
discoiquuid: 0d3bb98e-7139-4d8e-b110-6ebd11debda1
docset: aem65
feature: Correspondence Management
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 76%

---


# Integrieren der Benutzeroberfläche „Korrespondenz erstellen“ in Ihr benutzerdefiniertes Portal{#integrating-create-correspondence-ui-with-your-custom-portal}

## Überblick {#overview}

In diesem Artikel wird erläutert, wie Sie die Lösung „Korrespondenz erstellen“ in Ihre Umgebung integrieren können.

## URL-basierter Aufruf {#url-based-invocation}

Eine Möglichkeit, die Anwendung „Korrespondenz erstellen“ von einem Clusterportal aufzurufen, ist die URL mit folgenden Anforderungsparametern vorzubereiten:

* der Bezeichner für die Briefvorlage (unter Verwendung des cmLetterId-Parameters).

* die URL für die XML-Datei, die aus der gewünschten Datenquelle (unter Verwendung des cmDataUrl-Parameters) erfasst wurde

Beispielsweise würde das benutzerdefinierte Portal die URL als\
`https://'[server]:[port]'/[contextPath]/aem/forms/createcorrespondence.html?random=[timestamp]&cmLetterId=[letter identifier]&cmDataUrl=[data URL]`, was die href eines Links im Portal sein könnte.

>[!NOTE]
>
>Den Aufruf auf diese Weise durchzuführen, ist nicht sicher, da die erforderlichen Parameter als eine GET-Anforderung übergeben werden, indem die Parameter (sichtbar) in der URL offengelegt werden.

>[!NOTE]
>
>Bevor Sie die Anwendung „Korrespondenz erstellen“ aufrufen, speichern und laden Sie die Daten, um die Benutzeroberfläche „Korrespondenz erstellen“ unter der angegebenen URL aufzurufen. Dies kann entweder vom benutzerdefinierten Portal aus oder über einen anderen Vorgang im Back-End ausgeführt werden.

## Auf Daten basierter Inline-Aufruf  {#inline-data-based-invocation}

Eine weitere (und sicherere) Möglichkeit, die Anwendung &quot;Korrespondenz erstellen&quot;aufzurufen, besteht darin, einfach die URL unter https://&#39;[server]:[port]&#39;/[contextPath]/aem/forms/createcorrespondence.html zu drücken, während die Parameter und Daten gesendet werden, um die Anwendung &quot;Korrespondenz erstellen&quot;als Anforderung der POST aufzurufen (d. Dies bedeutet auch, dass Sie jetzt die XML-Datei für die Anwendung „Korrespondenz erstellen“ „inline“ (als Teil der gleichen Anforderung, unter Verwendung des cmData-Parameters) übergeben können, was bei der vorigen Herangehensweise nicht möglich/ideal war.

### Parameter für das Festlegen des Briefs  {#parameters-for-specifying-letter}

| **Name** | **Typ** | **Beschreibung** |
|---|---|---|
| cmLetterInstanceId | Zeichenfolge | Der Bezeichner für die Briefinstanz. |
| cmLetterId | Zeichenfolge | Der Name der Briefvorlage. |

Die Reihenfolge der Parameter in der Tabelle gibt die Voreinstellungen von Parametern an, die zum Laden des Briefs verwendet werden.

### Parameter für die Angabe der XML-Datenquelle  {#parameters-for-specifying-the-xml-data-source}

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

### Andere Parameter  {#other-parameters}

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

Wenn Sie das HTTP- oder cq-Protokoll für cmDataURL verwenden, sollte die URL von http/cq anonym zugänglich sein.
