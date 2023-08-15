---
title: Suchen nach Formularen und Assets
seo-title: Searching for forms and assets
description: Sie können Formulare und Assets in Ihrer AEM-Instanz mithilfe AEM Suche suchen. Mit der einfachen und erweiterten Suche können Sie Ihre Assets schnell finden.
seo-description: You can search forms and assets in your AEM instance using AEM search. Basic and advanced search lets you quickly locate your assets.
uuid: 0928a453-3dc4-448b-9320-dcbf20606dd9
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
discoiquuid: e65925ff-1fbf-4da6-bf09-0cf056c86e5a
docset: aem65
role: Admin
exl-id: 1f4f49b7-5f32-47dd-9dc7-a6974faf2bdf
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 30%

---

# Suchen nach Formularen und Assets{#searching-for-forms-and-assets}

Sie können mithilfe einer Textzeichenfolge oder einer Textzeichenfolge zusammen mit Platzhaltern nach Formularen oder Formular-Assets suchen. Sie können Ihre Suche auch mithilfe der Kriterien einschränken, die in verschiedenen Kategorien im Suchbereich verfügbar sind.

Wenn Sie ein oder mehrere Kriterien auswählen und auch eine Textzeichenfolge angeben, wird die Schnittmenge des Texts und der Kriterien als Suchergebnisse zurückgegeben. Die Suchergebnisse sind so gut wie die zur Verfügung gestellten Formular- und Asset-Metadaten.

Klicken Sie auf ![aem6forms_search](assets/aem6forms_search.png), um das Suchfeld ein- oder auszublenden.

## Grundlegende Suche {#basic-search}

Eine einfache Suche ist die Standardsuche, die ohne Angabe von Filtern ausgeführt wird. Eine Volltextsuche in Metadateneigenschaften wird von AEM Forms durchgeführt.

Um eine einfache Suche auszuführen, geben Sie die Suchabfrage in das Textfeld ein und drücken Sie die Eingabetaste. Sie können auch das Platzhalterzeichen (&#42;) eingeben, um eine beliebige Anzahl von Zeichen zu ersetzen.

Adobe Experience Manager sucht in den Metadateneigenschaften nach dem eingegebenen Text und gibt die entsprechenden Ergebnisse zurück. Wenn Sie mehr als ein Wort eingeben, stimmt der Suchvorgang mit dem vollständigen Text für die Suche überein.

Beachten Sie die folgenden Punkte zur einfachen Suche:

* Die Suche wird mithilfe der Formular- und Asset-Metadateneigenschaften durchgeführt.
* Wenn Sie mehr als ein Wort eingeben, stimmt der Suchvorgang mit dem vollständigen Text für die Suche überein.
* Bei der Suche wird nicht zwischen Groß- und Kleinschreibung unterschieden. Wenn Sie z. B. `geometrixx` eingeben, werden Assets mit den Titeln `Geometrixx`, `GEOMETRIXX` und `GeoMetRixx` in den Suchergebnissen angezeigt.

* Unvollständige Übereinstimmungen mit einem Wort werden nicht unterstützt. Um mit unvollständigen Zeichenfolgen zu suchen, verwenden Sie den Platzhalter &#42;. Wenn die Suchabfrage jedoch mit einem vollständigen Wort übereinstimmt, wird das entsprechende Formular oder Asset angezeigt.
* Zusätzliche Leerzeichen werden berücksichtigt und bei der Suche nicht abgeschnitten. Zum Beispiel ist `My form` nicht die gleiche Suchanfrage wie `My form`.

* Wenn die Daten und Anzeigewerte der Felder in den Metadateneigenschaften unterschiedlich sind, können Sie Anzeigewerte nicht als Suchparameter verwenden. Sie können beispielsweise nicht nach einem Status wie &quot;Geändert&quot;oder &quot;Veröffentlicht&quot;suchen, da diese Eigenschaften in einem anderen Format gespeichert sind.

## Erweiterte Suche {#advanced-search}

In den Suchkriterien können Sie neben der Abfrage einige Suchparameter angeben, um die einfache Suche effizienter und fokussierter zu gestalten.

![Suchfeld und Parameter bzw. Filter für die AEM-Formular- und die AEM-Asset-Suche](assets/search_forms_assets.png)

Suchfeld und Parameter bzw. Filter für die Suche nach AEM-Formularen und -Assets

### Asset-Pfad {#asset-path}

Mithilfe des Asset-Pfadfilters können Sie die Suchergebnisse auf das aktuelle Verzeichnis beschränken. Wenn die Option „Suche im aktuellen Verzeichnis“ nicht ausgewählt ist, enthalten die Suchergebnisse Assets aus dem Basisverzeichnis. Wenn es sich bei der aktuellen Seite um kein Verzeichnis handelt und die Option „Suche im aktuellen Verzeichnis“ ausgewählt ist, werden bei der Suche die Assets wiedergegeben, die im übergeordneten Verzeichnis vorhanden sind.

### Asset-Änderung {#asset-modification}

Wählen Sie eine der folgenden Optionen aus, um alle Assets zu durchsuchen, die innerhalb eines bestimmten Zeitraums geändert wurden.

| **Option** | **Beschreibung** |
|---|---|
| Vor zwei Stunden | Durchsuchen Sie alle Assets, die in den letzten zwei Stunden geändert wurden. |
| Vor einer Woche | Durchsuchen Sie alle Assets, die in der letzten Woche geändert wurden. |
| Vor einem Monat | Durchsuchen Sie alle Assets, die im letzten Monat geändert wurden. |
| Vor einem Jahr | Durchsuchen Sie alle Assets, die im letzten Jahr geändert wurden. |

### Asset-Status {#asset-status}

Sie können mit einem der folgenden Status nach Assets suchen:

* **Veröffentlicht**: Suchen Sie alle veröffentlichten Assets, die nach der Veröffentlichung nicht geändert wurden.

* **Veröffentlichung rückgängig gemacht**: Suchen Sie alle Assets, die nie veröffentlicht werden.

* **Geändert**: Suchen Sie alle Assets, die nach der Veröffentlichung geändert wurden oder deren Veröffentlichung rückgängig gemacht wurde.

### Asset-Typ {#asset-type}

Sie können eine beliebige Anzahl von Asset-Typen auswählen. Die Suche gibt die Vereinigung aller ausgewählten Asset-Typen zurück.

<table>
 <tbody>
  <tr>
   <th>Option</th> 
   <th>Beschreibung</th> 
  </tr>
  <tr>
   <td>Formularvorlage<br /> </td> 
   <td>Durchsuchen Sie alle Formularvorlagen.<br /> </td> 
  </tr>
  <tr>
   <td>PDF-Formular</td> 
   <td>Durchsuchen Sie alle PDF-Dokumente.</td> 
  </tr>
  <tr>
   <td>Dokument</td> 
   <td>Durchsuchen Sie alle Dokumente.</td> 
  </tr>
  <tr>
   <td>Adaptives Formular<br /> </td> 
   <td>Durchsuchen Sie alle adaptiven Formulare.</td> 
  </tr>
  <tr>
   <td>Ressource</td> 
   <td>Durchsuchen Sie alle Ressourcen.<br /> </td> 
  </tr>
 </tbody>
</table>

### Tags {#tags}

Tags sind Beschriftungen, die zur Identifizierung an Assets angehängt werden. Wählen Sie bei der Suche eine beliebige Anzahl von Tags aus der Dropdown-Liste aus oder fügen Sie ggf. benutzerdefinierte Tags hinzu. Ein Suchergebnis enthält die Schnittmenge der ausgewählten Tags.
