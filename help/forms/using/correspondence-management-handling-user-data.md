---
title: Correspondence Management | Umgang mit Benutzerdaten
seo-title: Correspondence Management | Umgang mit Benutzerdaten
description: Correspondence Management | Umgang mit Benutzerdaten
uuid: d5bb190b-d668-4da3-95da-b7705ad302d9
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 764d8e0d-604d-4c7b-89cd-7686ce5f03ff
role: Administrator
exl-id: a0c6a02c-47a3-4e70-a14c-953ee016b8e4
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 89%

---

# Correspondence Management | Umgang mit Benutzerdaten {#correspondence-management-handling-user-data}

Mit Correspondence Management von AEM Forms können Sie sichere und personalisierte Kundenkorrespondenzen erstellen, verwalten und optimieren. Es bietet eine intuitive Benutzerschnittstelle für Geschäftsbenutzer, um Mitteilungen unter Verwendung vorab genehmigter Inhaltsblöcke und Medienelemente zu erstellen. Weitere Informationen zum Erstellen von Schriftstücken finden Sie unter [Korrespondenz erstellen](/help/forms/using/create-correspondence.md).

Wenn ein Geschäftsbenutzer oder ein Agent eine Korrespondenz als Entwurf speichert oder übermittelt, wird eine Briefinstanz im AEM-Repository gespeichert. Die Briefinstanz enthält Korrespondenzdaten und Metadaten.

>[!NOTE]
>
>In AEM 6.5 Forms ist Correspondence Management nicht standardmäßig verfügbar. Wenn Sie von einer früheren AEM Forms-Version aktualisieren, installieren Sie das Kompatibilitätspaket, und migrieren Sie Ihre Ressourcen für Correspondence Management, um sie weiterhin in AEM 6.5 Forms zu verwenden. Weitere Informationen finden Sie unter [Kompatibilitätspaket](/help/forms/using/compatibility-package.md).

## Benutzerdaten und Datenspeicher {#data}

Correspondence Management speichert Daten für Entwurf und gesendete Briefe im AEM-Repository nur, wenn die Veröffentlichungs-Instanz für die Verwaltung von Briefinstanzen konfiguriert ist. Weitere Informationen zur Konfiguration finden Sie unter [Konfigurationseigenschaften von Correspondence Management](/help/forms/using/cm-configuration-properties.md).

Abhängig von der für Ihre AEM-Bereitstellung konfigurierten Datenspeicherpersistenz werden Entwürfe und übermittelte Korrespondenzdaten an den folgenden Speicherorten gespeichert.

<table>
 <tbody>
  <tr>
   <td><p><strong>Persistenztyp</strong></p> </td>
   <td><p><strong>Datenspeicher</strong></p> </td>
   <td><p><strong>Standort</strong></p> </td>
  </tr>
  <tr>
   <td><p>Default</p> </td>
   <td><p>AEM-Repository der Veröffentlichungsinstanz und der Author-Instanzen, die in der umgekehrten Replikationskonfiguration angegeben wurden</p> </td>
   <td><p><code>/content/apps/cm/letterInstances/[yyyy]/[mm]/[dd]/[node-id]/[letter-instance-name]/</code> </p> </td>
  </tr>
  <tr>
   <td><p>Remote</p> </td>
   <td><p>AEM-Repository der Remote-Verarbeitungs-Author-Instanz</p> </td>
   <td><p><code>/content/apps/cm/letterInstances/[yyyy]/[mm]/[dd]/[node-id]/[letter-instance-name]/</code></p> </td>
  </tr>
 </tbody>
</table>

Im oben angegebenen AEM-Repository-Speicherort:

* `[yyyy]/[mm]/[dd]` ist die Knotenstruktur basierend auf dem Datum, an dem die Briefinstanz erstellt wurde
* `[node-id]` ist die ID, die dem Ordner mit dem Brief zugewiesen wurde
* `[letter-instance-name]` ist der Name, der beim Speichern oder Senden eines Briefes angegeben wurde

Unter dem Knoten [letter-instance-name] wird die folgende Knotenstruktur erstellt und die Daten für jede Briefinstanz werden im AEM Repository gespeichert:

| Node | Beschreibung |
|---|---|
| `extendedProperties` | Speichert Metadateneigenschaften der Briefinstanz. |
| `dataXML` | Speichert eine herunterladbare dataXML-Datei, die die Korrespondenzdaten im Binärformat enthält. |
| `processedXDP` | Enthält die Details der XDP-Vorlage, die zum Erstellen des übermittelten Briefs verwendet wurde. Dieser Knoten wird nur für übermittelte Korrespondenzen erstellt. |
| `submittedLetter` | Speichert die übermittelten Briefdaten im herunterladbaren Binärformat. Dieser Knoten wird nur für übermittelte Korrespondenzen erstellt. |

## Zugreifen auf und Löschen von Benutzerdaten {#access-and-delete-user-data}

Sie können in den konfigurierten Datenspeichern auf Entwürfe und übermittelte Korrespondenzdaten zugreifen und diese ggf. löschen.

### Zugreifen auf Benutzerdaten {#access-user-data}

Die Korrespondenzverwaltung stellt APIs bereit, mit denen Sie Entwürfe und übermittelte Briefinstanzen finden und darauf zugreifen können. Mit den APIs können Sie Briefinstanzen mit der Briefinstanz-ID oder dem Benutzer, der die Korrespondenz gespeichert oder übermittelt hat, finden und öffnen. Weitere Informationen finden Sie unter [APIs für den Zugriff auf Briefinstanzen](/help/forms/using/cm-apis-to-access-letter-instances.md).

Alternativ können Sie mithilfe von CRX DELite zur Briefinstanz im AEM-Repository navigieren. Weitere Informationen über gespeicherte Daten und den Repository-Speicherort finden Sie unter [Benutzerdaten und Datenspeicher](/help/forms/using/correspondence-management-handling-user-data.md#data).

### Benutzerdaten löschen  {#delete-user-data}

Um eine Briefinstanz zu finden, die die Daten eines bestimmten Benutzers enthält, können Sie Folgendes tun:

* Verwenden Sie die Correspondence Management-APIs, wenn der Name der Briefinstanz oder des Benutzers, der den Entwurf gespeichert oder die Korrespondenz übermittelt hat, bekannt ist
* Verwenden Sie die AEM-Repository-Suche mit persönlich identifizierbaren Informationen wie der E-Mail-ID oder dem Namen, um den Knoten zu finden, auf dem die Informationen gespeichert sind

Um Benutzerdaten vollständig aus Entwurfs- und übermittelter Korrespondenz aus AEM-Systemen zu löschen, müssen Sie den Briefinstanzknoten manuell aus allen anwendbaren AEM-Instanzen löschen.
