---
title: Correspondence Management | Umgang mit Benutzerdaten
description: Correspondence Management und Umgang mit Benutzerdaten in der AEM Forms-Umgebung.
uuid: d5bb190b-d668-4da3-95da-b7705ad302d9
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 764d8e0d-604d-4c7b-89cd-7686ce5f03ff
role: Admin
exl-id: a0c6a02c-47a3-4e70-a14c-953ee016b8e4
source-git-commit: 0e5b89617d481c69882ec5d4658e76855aa9b691
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 45%

---

# Correspondence Management | Umgang mit Benutzerdaten {#correspondence-management-handling-user-data}

Mit AEM Forms Correspondence Management können Sie sichere und personalisierte Kundenkorrespondenzen erstellen, verwalten und optimieren. Es bietet eine intuitive Benutzeroberfläche, über die Geschäftsbenutzer Korrespondenzen mit vorab genehmigten Inhaltsbausteinen und Medienelementen erstellen können. Weitere Informationen zum Erstellen von Briefen finden Sie unter [Korrespondenz erstellen](/help/forms/using/create-correspondence.md).

Wenn ein Business-Benutzer oder ein Agent eine Korrespondenz als Entwurf speichert oder sendet, wird eine Briefinstanz im AEM Repository gespeichert. Die Briefinstanz enthält Korrespondenzdaten und Metadaten.

>[!NOTE]
>
>In AEM 6.5 Forms ist Correspondence Management nicht standardmäßig verfügbar. Wenn Sie von einer früheren AEM Forms-Version aktualisieren, installieren Sie das Kompatibilitätspaket, und migrieren Sie Ihre Ressourcen für Correspondence Management, um sie weiterhin in AEM 6.5 Forms zu verwenden. Weitere Informationen finden Sie unter [Kompatibilitätspaket](/help/forms/using/compatibility-package.md).

## Benutzerdaten und Datenspeicher {#data}

Correspondence Management speichert nur dann Daten für Entwürfe und gesendete Briefe in AEM Repository, wenn die Veröffentlichungsinstanz für die Verwaltung von Briefinstanzen konfiguriert ist. Weitere Informationen zur Konfiguration finden Sie unter [Konfigurationseigenschaften von Correspondence Management](/help/forms/using/cm-configuration-properties.md).

Je nach der für Ihre AEM-Bereitstellung konfigurierten Datenspeicherpersistenz werden Entwürfe und gesendete Korrespondenzdaten an den folgenden Speicherorten gespeichert.

<table>
 <tbody>
  <tr>
   <td><p><strong>Persistenztyp</strong></p> </td>
   <td><p><strong>Datenspeicher</strong></p> </td>
   <td><p><strong>Speicherort</strong></p> </td>
  </tr>
  <tr>
   <td><p>Standard</p> </td>
   <td><p>AEM Repository der Veröffentlichungsinstanz und Autoreninstanzen, die in der Konfiguration der Rückwärtsreplikation angegeben sind</p> </td>
   <td><p><code>/content/apps/cm/letterInstances/[yyyy]/[mm]/[dd]/[node-id]/[letter-instance-name]/</code><br /> </p> </td>
  </tr>
  <tr>
   <td><p>Remote</p> </td>
   <td><p>AEM Repository der Autoreninstanz der Remote-Verarbeitung</p> </td>
   <td><p><code>/content/apps/cm/letterInstances/[yyyy]/[mm]/[dd]/[node-id]/[letter-instance-name]/</code></p> </td>
  </tr>
 </tbody>
</table>

Im oben angegebenen AEM-Repository-Speicherort:

* `[yyyy]/[mm]/[dd]` ist die Knotenstruktur, basierend auf dem Datum, an dem die Briefinstanz erstellt wurde.
* `[node-id]` ist die ID, die dem Ordner mit dem Brief zugewiesen wurde
* `[letter-instance-name]` ist der Name, der beim Speichern oder Senden eines Briefes angegeben wurde

Unter dem Knoten [letter-instance-name] wird die folgende Knotenstruktur erstellt, und die Daten für jede Briefinstanz werden im AEM-Repository gespeichert:

| Knoten | Beschreibung |
|---|---|
| `extendedProperties` | Speichert Metadateneigenschaften der Briefinstanz. |
| `dataXML` | Speichert eine herunterladbare dataXML-Datei, die die Korrespondenzdaten im Binärformat enthält. |
| `processedXDP` | Enthält die Details der XDP-Vorlage, die zum Erstellen des gesendeten Briefs verwendet wird. Dieser Knoten wird nur für übermittelte Korrespondenzen erstellt. |
| `submittedLetter` | Speichert die übermittelten Briefdaten im herunterladbaren Binärformat. Dieser Knoten wird nur für übermittelte Korrespondenzen erstellt. |

## Zugreifen auf und Löschen von Benutzerdaten {#access-and-delete-user-data}

Sie können in den konfigurierten Datenspeichern auf Entwürfe und übermittelte Korrespondenzdaten zugreifen und diese bei Bedarf löschen.

### Zugreifen auf Benutzerdaten {#access-user-data}

Correspondence Management bietet APIs, mit denen Sie Entwurfs- und gesendete Briefinstanzen finden und darauf zugreifen können. Mithilfe der APIs können Sie Briefinstanzen mithilfe der Briefinstanz-ID oder des Benutzers, der die Korrespondenz gespeichert oder gesendet hat, suchen und öffnen. Weitere Informationen finden Sie unter [APIs zum Zugreifen auf Briefinstanzen](/help/forms/using/cm-apis-to-access-letter-instances.md).

Alternativ können Sie mit CRX DELite zur Briefinstanz im AEM Repository navigieren. Siehe [Benutzerdaten und Datenspeicher](/help/forms/using/correspondence-management-handling-user-data.md#data) für Informationen zu gespeicherten Daten und zum Repository-Speicherort.

### Benutzerdaten löschen {#delete-user-data}

Um eine Briefinstanz zu finden, die die Daten eines bestimmten Benutzers enthält, können Sie:

* Verwenden Sie Correspondence Management-APIs, wenn der Name der Briefinstanz oder der Benutzer, der den Entwurf gespeichert oder die Korrespondenz gesendet hat, bekannt ist
* Verwenden Sie die AEM-Repository-Suche mit persönlich identifizierbaren Informationen wie der E-Mail-ID oder dem Namen, um den Knoten zu finden, auf dem die Informationen gespeichert sind

Um Benutzerdaten vollständig aus Entwurfs- und übermittelter Korrespondenz aus AEM-Systemen zu löschen, müssen Sie den Briefinstanzknoten manuell aus allen anwendbaren AEM-Instanzen löschen.
