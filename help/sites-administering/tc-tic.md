---
title: Konfigurieren des Frameworks für die Übersetzungsintegration
description: Erfahren Sie, wie Sie das Framework für die Übersetzungsintegration in Adobe Experience Manager konfigurieren.
contentOwner: Guillaume Carlino
feature: Language Copy
exl-id: 7562754b-d9fd-441b-8ae5-c7eebe458cef
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: eb4c6ab188cc79eab66647433e60ba97eba6f257
workflow-type: tm+mt
source-wordcount: '1483'
ht-degree: 100%

---

# Konfigurieren des Frameworks für die Übersetzungsintegration{#configuring-the-translation-integration-framework}

Das Framework für die Übersetzungsintegration integriert Übersetzungsdienstleistungen von Drittanbietern, um die Übersetzung von AEM-Inhalten zu orchestrieren.

* Verbinden Sie sich mit Ihrem Übersetzungsdienstleister.
* Erstellen Sie eine Framework-Konfiguration für die Übersetzungsintegration.
* Verknüpfen Sie die Cloud-Konfigurationen mit Ihren Seiten.

Einen Überblick über die Funktionen zur Übersetzung von Inhalten in AEM erhalten Sie unter [Übersetzen von Inhalten für mehrsprachige Sites](/help/sites-administering/translation.md).

## Herstellen einer Verbindung zu einem Übersetzungsdienstleister {#connecting-to-a-translation-service-provider}

Erstellen Sie eine Cloud-Konfiguration, die AEM an Ihren Übersetzungsdienstleister anbindet. AEM enthält die Funktion, standardmäßig eine Verbindung zu Microsoft Translator herzustellen.
Die folgenden Übersetzungsdienstleister bieten eine Implementierung der neuen API für Übersetzungsprojekte. Links für weitere Informationen zur Integration:

* [Translations.com](https://exchange.adobe.com/experiencecloud.details.90104.globallink-connect-plus-for-aem.html)
* [Lionbridge](https://exchange.adobe.com/experiencecloud.details.100064.lionbridge-connector-for-experience-manager-63.html)
* [Memsource](https://exchange.adobe.com/apps/ec/103166/memsource-connector-for-adobe-experience-manager)
* [XTM Cloud](https://exchange.adobe.com/apps/ec/105037/xtm-connect-for-adobe-experience-manager)
* [Lingotek](https://exchange.adobe.com/apps/ec/90088/lingotek-collaborative-translation-platform)
* [RWS](https://exchange.adobe.com/apps/ec/108277/rws-language-cloud)
* [Smartling](https://www.smartling.com/software/integrations/adobe-experience-manager/)
* Microsoft (Microsoft Translator ist in AEM vorinstalliert)

>[!NOTE]
>
>Eine aktuelle Liste der Anbieter von menschlichen und maschinellen Übersetzungen finden Sie auf den folgenden Seiten:
>
>* [AEM – Übersetzung durch Menschen](https://exchange.adobe.com/apps/browse/ec?page=1&amp;partnerLevel=All&amp;product=AEM&amp;q=aem+human+translation&amp;sort=RELEVANCE)
>* [AEM – maschinelle Übersetzung](https://exchange.adobe.com/apps/browse/ec?q=AEM+machine+translation&amp;product=All&amp;partnerLevel=All&amp;sort=RELEVANCE)
>

Wenn Sie ein Connector-Paket installiert haben, können Sie eine Cloud-Konfiguration für den Connector erstellen. In der Regel müssen Sie Ihre Anmeldedaten für die Authentifizierung beim Übersetzungs-Service angeben. Weitere Informationen zum Hinzufügen einer Cloud-Konfiguration für den Microsoft Translator-Connector finden Sie unter [Integrieren mit Microsoft Translator](/help/sites-administering/tc-msconf.md).

Sie können mehrere Cloud-Konfigurationen für denselben Connector erstellen, falls erforderlich. Beispielsweise können Sie eine Konfiguration für jedes Konto oder Projekt erstellen, das Sie bei einem Anbieter haben.

Nach der Konfiguration einer Verbindung können Sie die Framework-Konfiguration für die Übersetzungsintegration erstellen, von der diese Verbindung genutzt wird.

## Erstellen einer Konfiguration für die Übersetzungsintegration {#creating-a-translation-integration-configuration}

Erstellen Sie eine Framework-Konfiguration für die Übersetzungsintegration, um festzulegen, wie Ihre Inhalte übersetzt werden sollen. Die Konfiguration enthält die folgenden Informationen:

* welcher Übersetzungsanbieter eingesetzt werden soll
* ob eine menschliche oder maschinelle Übersetzung erfolgen soll.
* ob andere Inhalte, die mit einer Seite oder einem Asset verknüpft sind, z. B. Tags, übersetzt werden sollen.

Nachdem Sie eine Framework-Konfiguration erstellt haben, verknüpfen Sie die Cloud-Konfiguration mit den Seiten, die Sie gemäß der Konfiguration übersetzen möchten. Wenn der Übersetzungsvorgang gestartet wird, geht der Übersetzungsworkflow entsprechend der verknüpften Framework-Konfiguration vor.

Wenn für verschiedene Bereiche Ihrer Website unterschiedliche Übersetzungsanforderungen vorliegen, erstellen Sie entsprechend mehrere Framework-Konfigurationen. Beispielsweise enthält eine mehrsprachige Website deutsche, englische und japanische Sprachkopien. Der Website-Eigentümer nutzt zwei verschiedene Übersetzungsdienstleister für die englische und die deutsche Übersetzung. Daher werden zwei verschiedene Konfigurationen des Frameworks erstellt. Jede Konfiguration nutzt einen anderen Übersetzungsdienstleister.

Nachdem Sie ein Framework für die Übersetzungsintegration erstellt haben, können Sie es [mit den Seiten verknüpfen](/help/sites-administering/tc-prep.md), die es verwenden.

**Hinweis:** Einen Überblick über die AEM-Funktionen zur Inhaltsübersetzung finden Sie unter [Übersetzen von Inhalten für mehrsprachige Sites](/help/sites-administering/translation.md).

Eine einzelne Framework-Konfiguration steuert, wie Seiten- und Community-Inhalte und Assets übersetzt werden.
![chlimage_1-386](assets/translation-config-65.jpg)

### Website-Konfigurationseigenschaften {#sites-configuration-properties}

Die Sites-Eigenschaften steuern, wie die Übersetzung von Seiteninhalten durchgeführt wird.

<table>
 <tbody>
  <tr>
   <th>Eigenschaft</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>Übersetzungs-Workflow</td>
   <td><p>Wählen Sie die Übersetzungsmethode aus, die das Framework für den Website-Inhalt durchführt:</p>
    <ul>
     <li>Maschinelle Übersetzung: Der Übersetzungsanbieter führt die Übersetzung mithilfe der maschinellen Übersetzung in Echtzeit durch.</li>
     <li>Menschliche Übersetzung: Der Übersetzungsdienstleister bekommt die Inhalte zugesendet und lässt sie durch Übersetzer übersetzen. </li>
     <li>Nicht übersetzen: Inhalte werden nicht zur Übersetzung versendet. Damit können Sie bestimmte Inhaltszweige überspringen, die nicht übersetzt, aber mit den neuesten Inhalten aktualisiert werden sollen.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Übersetzungsanbieter</td>
   <td>Wählen Sie den Übersetzungsanbieter aus, der die Übersetzung durchzuführen soll. Ein Anbieter wird in der Liste angezeigt, wenn sein entsprechender Connector installiert ist.</td>
  </tr>
  <tr>
   <td>Inhaltskategorie</td>
   <td>(Nur maschinelle Übersetzung) Eine Kategorie, die den zu übersetzenden Inhalt beschreibt. Die Kategorie kann beeinflussen, welche Terminologie und welche Formulierungen bei der Übersetzung von Inhalten verwendet werden.</td>
  </tr>
  <tr>
   <td>Komponentenzeichenfolgen übersetzen</td>
   <td>Wählen Sie diese Option aus, um Komponentenzeichenfolgen zu übersetzen, die mit der Seite verknüpft sind.</td>
  </tr>
  <tr>
   <td>Tags übersetzen</td>
   <td>Wählen Sie diese Option aus, um Tags zu übersetzen, die mit der Seite verknüpft sind.</td>
  </tr>
  <tr>
   <td>Seiten-Assets übersetzen</td>
   <td><p>Wählen Sie aus, wie Assets übersetzt werden sollen, die aus dem Dateisystem zu Komponenten hinzugefügt werden oder auf die in Assets verwiesen wird:</p>
    <ul>
     <li>Nicht übersetzen: Seiten-Assets werden nicht übersetzt.</li>
     <li>Workflow für Sites-Übersetzung verwenden: Assets werden entsprechend der Konfigurationseigenschaften auf der Registerkarte „Sites“ bearbeitet.</li>
     <li>Workflow für Asset-Übersetzung verwenden: Assets werden entsprechend der Konfigurationseigenschaften auf der Registerkarte „Assets“ bearbeitet.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Übersetzung automatisch durchführen</td>
   <td>Wählen Sie diese Option aus, um Übersetzungsaufträge nach der Erstellung von Übersetzungsprojekten automatisch auszuführen. Bei dieser Option haben Sie keine Möglichkeit, den Übersetzungsauftrag zu prüfen und seinen Umfang zu ermitteln.</td>
  </tr>
 </tbody>
</table>

### Communities-Konfigurationseigenschaften {#communities-configuration-properties}

Die Communities-Eigenschaften steuern, wie die Übersetzung von nutzergenerierten Inhalten durchgeführt wird. Für die Übersetzung von nutzergenerierten Inhalten wird immer die maschinelle Übersetzung genutzt. Weitere Informationen finden Sie unter [Übersetzen von nutzergenerierten Inhalten](/help/communities/translate-ugc.md).

| Eigenschaft | Beschreibung |
|---|---|
| Übersetzungsanbieter | Wählen Sie den Übersetzungsanbieter aus, der die Übersetzung durchzuführen soll. Die Anbieter, für die Cloudkonfigurationen erstellt wurden, werden in der Liste angezeigt. |
| Inhaltskategorie | Eine Kategorie, die den zu übersetzenden Inhalt beschreibt. Die Kategorie kann beeinflussen, welche Terminologie und welche Formulierungen bei der Übersetzung von Inhalten verwendet werden. |
| Auswählen eines Gebietsschemas zur Verwendung als globaler Freigabespeicher | (Optional) Wenn Sie ein Gebietsschema zum Speichern von benutzergenerierten Inhalten auswählen, werden Beiträge aus allen Sprachkopien in einer globalen Konversation angezeigt. Standardmäßig wählen Sie das Gebietsschema für die [Basissprache](/help/communities/sites-console.md#translation) für die Website. Die Auswahl von „Kein gemeinsamer Speicher“ deaktiviert die globale Übersetzung. Standardmäßig ist die globale Übersetzung deaktiviert. |

### Assets-Konfigurationseigenschaften {#assets-configuration-properties}

Asset-Eigenschaften steuern, wie Assets konfiguriert werden. Weitere Informationen zur Übersetzung von Assets finden Sie unter [Erstellen von Sprachkopien für Assets](/help/assets/translation-projects.md).

<table>
 <tbody>
  <tr>
   <th>Eigenschaft</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>Übersetzungs-Workflow</td>
   <td><p>Wählen Sie den Übersetzungstyp aus, den das Framework für Assets durchführt:</p>
    <ul>
     <li>Maschinelle Übersetzung: Der Übersetzungsanbieter führt die Übersetzung mithilfe der maschinellen Übersetzung sofort durch.</li>
     <li>Menschliche Übersetzung: Der Übersetzungsdienstleister bekommt die Inhalte automatisch zugesendet und lässt sie durch Übersetzer übersetzen. </li>
     <li>Nicht übersetzen: Assets werden nicht zur Übersetzung versendet.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Übersetzungsanbieter</td>
   <td>Wählen Sie den Übersetzungsanbieter aus, der die Übersetzung durchzuführen soll. Ein Anbieter wird in der Liste angezeigt, wenn sein entsprechender Connector installiert ist.</td>
  </tr>
  <tr>
   <td>Inhaltskategorie</td>
   <td>(Nur maschinelle Übersetzung) Eine Kategorie, die den zu übersetzenden Inhalt beschreibt. Die Kategorie kann beeinflussen, welche Terminologie und welche Formulierungen bei der Übersetzung von Inhalten verwendet werden.</td>
  </tr>
  <tr>
   <td>Assets übersetzen</td>
   <td>Wählen Sie diese Option aus, um Assets in das Übersetzungsprojekt aufzunehmen. </td>
  </tr>
  <tr>
   <td>Metadaten übersetzen</td>
   <td>Wählen Sie diese Option aus, um Asset-Metadaten zu übersetzen.</td>
  </tr>
  <tr>
   <td>Tags übersetzen</td>
   <td>Wählen Sie diese Option aus, um Tags zu übersetzen, die mit dem Asset verknüpft sind.</td>
  </tr>
  <tr>
   <td>Übersetzung automatisch durchführen</td>
   <td>Wählen Sie diese Option aus, um Übersetzungsaufträge nach der Erstellung von Übersetzungsprojekten automatisch auszuführen. Bei dieser Option haben Sie keine Möglichkeit, den Übersetzungsauftrag zu prüfen oder seinen Umfang zu ermitteln.</td>
  </tr>
 </tbody>
</table>

1. Klicken Sie in der Seitenleiste auf „Tools“ > „Vorgänge“ > „Cloud“ > „Cloud-Services“.
1. Welche Links im Bereich für die Übersetzungsintegration angezeigt werden, hängt davon ab, ob Konfigurationen erstellt wurden:

   * Wenn keine Konfigurationen erstellt wurden, klicken Sie auf „Jetzt konfigurieren“.
   * Wenn bereits Konfigurationen vorhanden sind, klicken Sie auf „Konfigurationen anzeigen“ und anschließend auf den Link mit dem Pluszeichen (+), der neben „Verfügbare Konfigurationen“ angezeigt wird.

1. Geben Sie einen Namen für die Konfiguration ein und klicken Sie dann auf „Erstellen“.
1. Konfigurieren Sie die Eigenschaften auf den Registerkarten „Sites“, „Communities“ und „Assets“ und klicken Sie anschließend auf „OK“.

## Konfigurieren von Seiten für Übersetzungen {#configuring-pages-for-translation}

Um die Übersetzung Ihrer Quellseiten in andere Sprachen zu konfigurieren, verknüpfen Sie die Seiten mit den folgenden Cloud-Konfigurationen:

* mit der Cloud-Konfiguration, die AEM an Ihren Übersetzungsdienstleister anbindet
* mit dem Framework für die Übersetzungsintegration, das die Details der Übersetzung konfiguriert

Die Cloud-Konfiguration des Frameworks für die Übersetzungsintegration legt fest, mit welcher Cloud-Konfiguration die Verbindung zum Dienstleister hergestellt werden soll. Wenn Sie eine Quellseite mit der Cloud-Konfiguration eines Frameworks verknüpfen, muss die Seite mit der Cloud-Konfiguration des Dienstleisters verknüpft sein, die die Cloud-Konfiguration des Frameworks nutzt.

Wenn Sie eine Seite mit einer Cloud-Konfiguration verknüpfen, erben die untergeordneten Elemente der Seite diese Verknüpfung. Wenn Sie z. B. die Seite /content/geometrixx/en/products mit einem Framework für die Übersetzungsintegration verknüpfen, werden die Produktseite und alle untergeordneten Seiten entsprechend diesem Framework übersetzt.

Bei Bedarf können Sie die Verknüpfung auf einer untergeordneten Seite überschreiben. Beispiel: Die Inhalte einer Website drehen sich größtenteils um das Thema Bekleidung. Ein Zweig an Seiten beschreibt dagegen das Unternehmen. Die Stammseite der Site ist mit einem Framework für die Übersetzungsintegration verknüpft, das vorgibt, dass maschinelle Übersetzung bei der Kategorie „Bekleidung“ angewendet werden soll. Der Verzweigung, die das Unternehmen beschreibt, nutzt dagegen ein Framework, bei dem maschinelle Übersetzung mit der Kategorie „Allgemein“ angewendet wird.

Darüber hinaus steht bei allen [SCF-Komponenten](/help/communities/scf.md) von Communities auf den Seiten für benutzergenerierte Inhalte die Möglichkeit zur Verfügung, dass Benutzer Inhalte übersetzen können. Weitere Informationen finden Sie unter [Übersetzen von benutzergenerierten Inhalten](/help/communities/translate-ugc.md).

### Verknüpfen einer Seite mit einem Übersetzungsdienstleister {#associating-a-page-with-a-translation-provider}

Verknüpfen Sie eine Seite mit Ihrem Übersetzungsdienstleister, um die Seite und ihre untergeordneten Seiten zu übersetzen.

1. Wählen Sie in der Sites-Konsole die zu konfigurierende Seite aus und klicken Sie auf „Eigenschaften anzeigen“.
1. Klicken Sie auf „Bearbeiten“ und anschließend auf die Registerkarte „Cloud-Services“.
1. Klicken Sie auf „Konfiguration hinzufügen“ > „Übersetzungsintegration“.
1. Wählen Sie den gewünschten Übersetzungsdienstleister aus und klicken Sie auf „Fertig“.

### Verknüpfen von Seiten mit einem Framework für die Übersetzungsintegration {#associating-pages-with-a-translation-integration-framework}

Verknüpfen Sie eine Seite mit dem Framework für die Übersetzungsintegration, das festlegt, wie die Übersetzung der Seite und der untergeordneten Seiten durchgeführt werden soll.

1. Wählen Sie in der Sites-Konsole die zu konfigurierende Seite aus und klicken Sie auf „Eigenschaften anzeigen“.
1. Klicken Sie auf „Bearbeiten“ und anschließend auf die Registerkarte „Cloud-Services“.
1. Klicken Sie auf „Konfiguration hinzufügen“ > „Übersetzungsintegration“.
1. Wählen Sie das gewünschte Framework für die Übersetzungsintegration aus und klicken Sie auf „Fertig“.
