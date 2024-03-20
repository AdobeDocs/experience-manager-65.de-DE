---
title: Integrieren der Benutzeroberfläche „Korrespondenz erstellen“ in Ihr benutzerdefiniertes Portal
description: Erfahren Sie, wie Sie die Benutzeroberfläche "Korrespondenz erstellen"in Ihr benutzerdefiniertes Portal integrieren
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
docset: aem65
feature: Correspondence Management
exl-id: c3b6ee31-ccbb-4446-86c8-f618226fefc4
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 37%

---

# Integrieren der Benutzeroberfläche „Korrespondenz erstellen“ in Ihr benutzerdefiniertes Portal{#integrating-create-correspondence-ui-with-your-custom-portal}

## Übersicht {#overview}

In diesem Artikel wird beschrieben, wie Sie die Lösung &quot;Korrespondenz erstellen&quot;in Ihre Umgebung integrieren können.

## URL-basierter Aufruf {#url-based-invocation}

Eine Möglichkeit, die Anwendung &quot;Korrespondenz erstellen&quot;über ein benutzerdefiniertes Portal aufzurufen, besteht darin, die URL mit den folgenden Anforderungsparametern vorzubereiten:

* die Kennung für die Briefvorlage (mithilfe des cmLetterId-Parameters).

* die URL für die XML-Datei, die aus der gewünschten Datenquelle (unter Verwendung des cmDataUrl-Parameters) erfasst wurde

Beispielsweise würde das benutzerdefinierte Portal die URL als\
`https://'[server]:[port]'/[contextPath]/aem/forms/createcorrespondence.html?random=[timestamp]&cmLetterId=[letter identifier]&cmDataUrl=[data URL]` vorbereiten, wobei es sich um die href eines Links auf dem Portal handeln könnte.

>[!NOTE]
>
>Ein solcher Aufruf ist nicht sicher, da die erforderlichen Parameter als GET-Anfrage übergeben werden, indem der gleiche (deutlich sichtbare) Parameter in der URL offen gelegt wird.

>[!NOTE]
>
>Bevor Sie die Anwendung &quot;Korrespondenz erstellen&quot;aufrufen, speichern und laden Sie die Daten hoch, um die Benutzeroberfläche &quot;Korrespondenz erstellen&quot;unter der angegebenen dataURL aufzurufen. Dies kann entweder vom benutzerdefinierten Portal selbst oder über einen anderen Back-End-Prozess erfolgen.

## Inline-datenbasierter Aufruf {#inline-data-based-invocation}

Eine weitere (und sicherere) Möglichkeit, die Anwendung „Korrespondenz erstellen“ aufzurufen, besteht darin, die URL https://&#39;[server]:[port]&#39;/[contextPath]/aem/forms/createcorrespondence.html aufzurufen, während die Parameter und Daten zum Aufrufen der Anwendung „Korrespondenz erstellen“ als POST-Anforderung gesendet werden (wodurch sie vor dem Endbenutzer versteckt werden). Dies bedeutet auch, dass Sie jetzt die XML-Daten für die Anwendung &quot;Korrespondenz erstellen&quot;inline übergeben können (als Teil derselben Anforderung, unter Verwendung des cmData-Parameters), was im vorherigen Ansatz nicht möglich/ideal war.

### Parameter für die Angabe von Briefen {#parameters-for-specifying-letter}

| **Name** | **Typ** | **Beschreibung** |
|---|---|---|
| cmLetterInstanceId | Zeichenfolge | Der Bezeichner für die Briefinstanz. |
| cmLetterId | Zeichenfolge | Der Name der Briefvorlage. |

Die Reihenfolge der Parameter in der Tabelle gibt die Voreinstellungen der Parameter an, die zum Laden des Briefs verwendet werden.

### Parameter zum Angeben der XML-Datenquelle {#parameters-for-specifying-the-xml-data-source}

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
   <td>XML-Daten aus einer Quelldatei mit Grundprotokollen wie cq, ftp, http oder file.<br /> </td> 
  </tr>
  <tr>
   <td>cmLetterInstanceId</td> 
   <td>Zeichenfolge</td> 
   <td>Verwenden von XML-Daten, die in der Briefinstanz verfügbar sind.</td> 
  </tr>
  <tr>
   <td>cmUseTestData</td> 
   <td>Boolesch</td> 
   <td>Um die im Datenwörterbuch angehängten Testdaten wiederzuverwenden.</td> 
  </tr>
 </tbody>
</table>

Die Reihenfolge der Parameter in der Tabelle gibt die Voreinstellungen der Parameter an, die zum Laden der XML-Daten verwendet werden.

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
   <td>True zum Öffnen des Briefs im Vorschaumodus<br /> </td> 
  </tr>
  <tr>
   <td>Willkürlich</td> 
   <td>Zeitstempel</td> 
   <td>Beheben von Problemen beim Zwischenspeichern im Browser.</td> 
  </tr>
 </tbody>
</table>

Wenn Sie ein HTTP- oder CQ-Protokoll für cmDataURL verwenden, muss die HTTP/CQ-URL anonym zugänglich sein.
