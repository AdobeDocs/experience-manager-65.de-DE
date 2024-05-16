---
title: Correspondence Management | Umgang mit Benutzerdaten
description: Erfahren Sie mehr über Correspondence Management und den Umgang mit Benutzerdaten in einer Adobe Experience Manager Forms-Umgebung.
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
role: Admin,User
exl-id: a0c6a02c-47a3-4e70-a14c-953ee016b8e4
solution: Experience Manager, Experience Manager Forms
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '552'
ht-degree: 100%

---

# Correspondence Management | Umgang mit Benutzerdaten {#correspondence-management-handling-user-data}

Mit AEM Forms Correspondence Management können Sie sichere und personalisierte Kundenkorrespondenz erstellen, verwalten und optimieren. Es bietet eine intuitive Benutzerschnittstelle für Business-Benutzende, um Mitteilungen unter Verwendung vorab genehmigter Inhaltsblöcke und Medienelemente zu erstellen. Weitere Informationen zum Erstellen von Briefen finden Sie unter [Korrespondenz erstellen](/help/forms/using/create-correspondence.md).

Wenn Business-Benutzende oder Agentinnen bzw. Agenten eine Mitteilung als Entwurf speichern oder übermitteln, wird eine Briefinstanz im AEM-Repository gespeichert. Die Briefinstanz umfasst Korrespondenzdaten und Metadaten.

>[!NOTE]
>
>In AEM 6.5 Forms ist Correspondence Management nicht standardmäßig verfügbar. Wenn Sie von einer früheren AEM Forms-Version aktualisieren, installieren Sie das Kompatibilitätspaket, und migrieren Sie Ihre Ressourcen für Correspondence Management, um sie weiterhin in AEM 6.5 Forms zu verwenden. Weitere Informationen finden Sie unter [Kompatibilitätspaket](/help/forms/using/compatibility-package.md).

## Benutzerdaten und Datenspeicher {#data}

Correspondence Management speichert Daten für Entwürfe und gesendete Briefe im AEM-Repository nur, wenn die Veröffentlichungsinstanz für die Verwaltung von Briefinstanzen konfiguriert ist. Weitere Informationen zur Konfiguration finden Sie unter [Eigenschaften der Correspondence Management-Konfiguration](/help/forms/using/cm-configuration-properties.md).

Abhängig von der für Ihre AEM-Bereitstellung konfigurierten Datenspeicherpersistenz werden Entwürfe und übermittelte Korrespondenzdaten an den folgenden Speicherorten gespeichert.

<table>
 <tbody>
  <tr>
   <td><p><strong>Persistenztyp</strong></p> </td>
   <td><p><strong>Datenspeicher</strong></p> </td>
   <td><p><strong>Speicherort</strong></p> </td>
  </tr>
  <tr>
   <td><p>Standard</p> </td>
   <td><p>AEM-Repository der Veröffentlichungsinstanz und der Autoreninstanzen, die in der Konfiguration für die umgekehrte Replikation angegeben wurden</p> </td>
   <td><p><code>/content/apps/cm/letterInstances/[yyyy]/[mm]/[dd]/[node-id]/[letter-instance-name]/</code><br /> </p> </td>
  </tr>
  <tr>
   <td><p>Remote</p> </td>
   <td><p>AEM-Repository der Autoreninstanz zur Remote-Verarbeitung</p> </td>
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
| `processedXDP` | Enthält die Details der XDP-Vorlage, die zum Erstellen des gesendeten Briefs verwendet wurde. Dieser Knoten wird nur für übermittelte Korrespondenzen erstellt. |
| `submittedLetter` | Speichert die übermittelten Briefdaten im herunterladbaren Binärformat. Dieser Knoten wird nur für übermittelte Korrespondenzen erstellt. |

## Zugreifen auf und Löschen von Benutzerdaten {#access-and-delete-user-data}

Sie können in den konfigurierten Datenspeichern auf Entwürfe und übermittelte Korrespondenzdaten zugreifen und diese ggf. löschen.

### Zugreifen auf Benutzerdaten {#access-user-data}

Correspondence Management stellt APIs bereit, mit denen Sie Entwürfe und übermittelte Briefinstanzen finden und darauf zugreifen können. Mit den APIs können Sie Briefinstanzen anhand der Briefinstanz-ID oder der Person, die die Korrespondenz gespeichert oder gesendet hat, finden und öffnen. Weitere Informationen finden Sie unter [APIs zum Zugreifen auf Briefinstanzen](/help/forms/using/cm-apis-to-access-letter-instances.md).

Alternativ können Sie mithilfe von CRXDE Lite zur Briefinstanz im AEM-Repository navigieren. Weitere Informationen über gespeicherte Daten und den Repository-Speicherort finden Sie unter [Benutzerdaten und Datenspeicher](/help/forms/using/correspondence-management-handling-user-data.md#data).

### Benutzerdaten löschen {#delete-user-data}

Um eine Briefinstanz zu finden, die die Daten einer bestimmten Person enthält, können Sie wie folgt vorgehen:

* Verwenden Sie die Correspondence Management-APIs, wenn der Name der Briefinstanz oder der Person, die den Entwurf gespeichert oder die Korrespondenz gesendet hat, bekannt ist.
* Verwenden Sie die AEM-Repository-Suche mit persönlich identifizierbaren Informationen wie der E-Mail-ID oder dem Namen, um den Knoten zu finden, auf dem die Informationen gespeichert sind

Um Benutzerdaten vollständig aus Entwurfs- und übermittelter Korrespondenz aus AEM-Systemen zu löschen, müssen Sie den Briefinstanzknoten manuell aus allen anwendbaren AEM-Instanzen löschen.
