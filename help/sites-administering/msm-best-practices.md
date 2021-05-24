---
title: Best Practices für MSM
seo-title: Best Practices für MSM
description: Hier finden Sie Best Practices für die Einrichtung und Verwendung von AEM MSM (Multi Site Manager) – zusammengestellt von Technik- und Beratungsteams von Adobe.
seo-description: Hier finden Sie Best Practices für die Einrichtung und Verwendung von AEM MSM (Multi Site Manager) – zusammengestellt von Technik- und Beratungsteams von Adobe.
uuid: cbb598bb-ec8f-4985-97af-7c87f5891c66
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features, best-practices
content-type: reference
discoiquuid: 04344537-7485-40a9-ad14-804ba448f1e2
feature: Multi-Site-Manager
exl-id: 3fedc1ba-64f5-4fbe-9ee5-9b96b75dda58
source-git-commit: cb4b0cb60b8709beea3da70495a15edc8c4831b8
workflow-type: tm+mt
source-wordcount: '1667'
ht-degree: 69%

---

# Best Practices für MSM{#msm-best-practices}

## Allgemein {#general}

MSM ist ein konfigurierbares Framework für die Automatisierung der Inhaltsbereitstellung. Implementierungen umfassen häufig große Teile einer Website und erstrecken sich über Organisationen und geografische Regionen. Es wird daher dringend empfohlen, MSM-Implementierungen mit der gleichen Sorgfalt zu planen wie Ihre Website:

* **Planen Sie zunächst sorgfältig die Struktur und den Inhaltsfluss**, bevor Sie mit der Implementierung beginnen.
* **Halten Sie die Anzahl der Live Copies auf ein Minimum beschränkt.** Die Verarbeitung von Live Copies ist eine ressourcenintensive Aufgabe. Je mehr Live Copies in Ihrem System vorhanden sind, desto mehr Leistung kann betroffen sein: von der Verarbeitung interner Live Copy-Indizes über Live Copy-Vorgänge wie Rollouts bis hin zu UI-Vorgängen wie der Anzeige von Live Copy-Beziehungen in der Leiste &quot;Sites-Admin-Verweise&quot;. Es empfiehlt sich, Live Copies von Sites oder Zweigen einer Site zu erstellen, in denen die Live Copy-Beziehungen zu Seiten der Site oder des Zweigs vererbt werden. Vermeiden Sie das Erstellen einzelner Live Copies für Seiten in einer Site oder einem Zweig, wenn die gesamte Struktur in eine Live Copy erstellt werden kann.
* **Beschränken Sie Anpassungen auf das Nötigste.** MSM unterstützt zwar ein hohes Maß an Anpassung (z. B. Rollout-Konfigurationen), doch ist es in der Regel die Best Practice für die Leistung, Zuverlässigkeit und Upgrade Ihrer Website, die Anpassung zu minimieren.
* Etablieren Sie frühzeitig ein **Governance-Modell** und schulen Sie die Benutzer entsprechend. Eine Best Practice aus Governance-Sicht besteht darin, **die Autorität zu minimieren, über die lokale Inhaltsersteller** verfügen, um Inhalte anderen lokalen Benutzern und ihren jeweiligen Live Copies zuzuweisen/zu verbinden. Das liegt daran, dass nicht regulierte verkettete Vererbungen die Komplexität einer MSM-Struktur erheblich erhöhen und ihre Leistung und Zuverlässigkeit beeinträchtigen.

* Sobald ein Plan für Ihre Struktur, Inhaltsflüsse, Automatisierung und Governance besteht - **Prototyp und testen Sie Ihr System** gründlich, bevor Sie mit der Live-Implementierung beginnen.
* **Adobe Consulting und führende Systemintegratoren** sind bestens mit der Planung und Implementierung der Inhaltsautomatisierung mit MSM vertraut und können Sie sowohl bei den ersten Schritten mit Ihrem MSM-Projekt als auch im weiteren Verlauf der Implementierung unterstützen.

>[!NOTE]
>
>Weitere Information zur Verwendung von MSM finden Sie in den entsprechenden Knowledge Base-Artikeln:
>
>* [Häufig gestellte Fragen zu MSM](https://helpx.adobe.com/experience-manager/kb/index/msm_faq.html)
>* [Beheben von Problemen mit MSM](https://helpx.adobe.com/experience-manager/kb/troubleshooting-aem-msm-issues.html)

>



>[!NOTE]
>
>Sie können auch die [Bezugskomponente](/help/sites-authoring/default-components-foundation.md#reference) verwenden, um eine einzelne Seite oder einen Absatz wiederzuverwenden. Bedenken Sie Folgendes:
>
>* MSM ist flexibler und ermöglicht eine differenziertere Steuerung von Art und Zeitpunkt der Inhaltssynchronisierung.
>* [Kernkomponenten](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/introduction.html) werden nun anstelle der Foundation-Komponenten empfohlen.

>



## Live Copy-Quellen und Blueprint-Konfigurationen {#live-copy-sources-and-blueprint-configurations}

Eine Live Copy kann entweder unter Verwendung [regulärer Seiten](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page) oder unter Verwendung einer [Blueprint-Konfiguration](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) erstellt werden. Beide Varianten sind zulässig.

Die Verwendung einer Blueprint-Konfiguration hat allerdings folgende Vorteile:

* Erlauben Sie dem Autor, die Option **Rollout** auf einem Blueprint zu verwenden, um (explizit) Änderungen an Live Copies zu pushen, die von diesem Blueprint erben.
* Lassen Sie den Autor zu, **Site erstellen** zu verwenden. Dadurch kann der Benutzer einfach Sprachen auswählen und die Struktur der Live Copy konfigurieren.
* Sie definiert eine standardmäßige Rollout-Konfiguration für Live Copies, die über eine Beziehung mit dem Blueprint verfügen.

Ohne Verweis auf eine Blueprint-Konfiguration können Rollouts nur von Live Copies selbst initiiert werden, wobei im Wesentlichen Inhalt aus der Quelle abgerufen wird.

Wenn Sie eine neue Website mit Live Copy erstellen, empfiehlt es sich, Blueprint-Konfigurationen zu erstellen, um die Verfügbarkeit sämtlicher MSM-Features sicherzustellen.

>[HINWEIS!]
>
> Beachten Sie, dass CUGs auf der Registerkarte &quot;Berechtigungen&quot;nicht für Live Copies aus Blueprints bereitgestellt werden können. Planen Sie dies ein, wenn Sie eine Live Copy konfigurieren.

## Komponenten- und Containersynchronisierung {#components-and-container-synchronization}

Für die Synchronisierung von Komponenten gilt in MSM im Allgemeinen folgende Rollout-Regel:

* Beim Rollout der Komponenten werden alle im Blueprint enthaltenen Ressourcen synchronisiert.
* Container synchronisieren nur die aktuelle Ressource.

Das bedeutet, dass Komponenten als Aggregat behandelt und bei einem Rollout die Komponente selbst und alle ihre untergeordneten Elemente durch die Elemente aus den Blueprints ersetzt werden. Wenn also eine Ressource einer solchen Komponente lokal hinzugefügt wird, geht sie beim Rollout des Blueprints verloren.

Um die Schachtelung von Komponenten zu unterstützen, sodass lokal hinzugefügte Komponenten bei einem Rollout erhalten bleiben, muss die Komponente als Container deklariert werden. Ein Beispiel: Die parsys-Standardkomponente wird als Container deklariert, um lokal hinzugefügten Inhalt zu unterstützen.

>[!NOTE]
>
>Fügen Sie der Komponente die Eigenschaft `cq:isContainer` hinzu, um sie als Container zu kennzeichnen.

## Erstellen einer Website {#create-site}

Live Copies können mit AEM auf zwei Arten erstellt werden:

* Wenn [eine Live Copy](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page) erstellt wird

   Dies kann als allgemeinerer Ansatz betrachtet werden, mit dem Sie Live Copies von jeder Seite aus erstellen können. Die Inhaltsstruktur einer Live Copy entspricht exakt der Quelle.

* Wenn [eine Site](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) erstellt wird

   Dies ist ein speziellerer Ansatz, vor allem für die Erstellung von Websites mit mehrsprachiger Struktur.

Berücksichtigen Sie beim Erstellen einer Website folgende Punkte:

* Für die Erstellung einer neuen Website benötigen Sie eine [Blueprint-Konfiguration](/help/sites-administering/msm-livecopy.md#managing-blueprint-configurations).
* Um das Auswählen von Sprachpfaden zu ermöglichen, die für eine neue Website erstellt werden sollen, muss der Blueprint (Quelle) die entsprechenden Sprachstämme enthalten.
* Nachdem eine [neue Site als Live Copy](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) erstellt wurde (mit **Erstellen** und **Site**), sind die ersten beiden Ebenen dieser Live Copy *flach*. Untergeordnete Elemente der Seite sind nicht Teil der Live-Beziehung, werden bei einem Rollout aber trotzdem berücksichtigt, wenn eine dem Auslöser entsprechende Live-Beziehung gefunden wird.

   Dadurch lässt sich Folgendes vermeiden:

   * Manuelles Hinzufügen von Sprachen im Blueprint (unterhalb der ersten Ebene)
   * Manuelles Hinzufügen von Inhalt unmittelbar unter dem Sprach-Stamm
   * Automatische Übertragung des neuen Inhalts auf die Live Copy beim Rollout

## MSM und mehrsprachige Websites {#msm-and-multilingual-websites}

MSM kann Sie auf zwei Arten beim Erstellen mehrsprachiger Websites unterstützen:

* Beim Erstellen von Sprach-Mastern

   * MSM bietet zwar selbst **keine Inhaltsübersetzung**, kann jedoch mit entsprechenden Übersetzungs-Connectors von Dritten integriert werden. Beachten Sie Folgendes:

      * Mit MSM können Sie die Vererbung auf Seiten- und/oder Komponentenebene unterbinden. So können Sie verhindern, dass übersetzter Inhalt aus einer Live Copy beim nächsten Rollout durch noch nicht übersetzten Inhalt aus einem Blueprint überschrieben wird.
      * Einige Übersetzungs-Connectoren von Dritten bieten eine automatisierte Verwaltung der MSM-Vererbung.

         Weitere Informationen erhalten Sie von Ihrem Übersetzungsdienstleister.

      * Eine Alternative für die Erstellung und Übersetzung von Sprach-Mastern ist die Verwendung von Sprachkopien in Verbindung mit dem vorgefertigten AEM-Framework für die Übersetzungsintegration.

* Beim Rollout von Inhalt auf der Grundlage von Sprach-Mastern

   * Beispielsweise auf der Grundlage des französischen Sprach-Masters für länderspezifische Websites wie etwa Frankreich/Französisch, Kanada/Französisch und Schweiz/Französisch.

Weitere Informationen finden Sie unter [Übersetzen von Inhalt für mehrsprachige Websites](/help/sites-administering/translation.md) und in den [Best Practices zur Übersetzung](/help/sites-administering/tc-bp.md).

## Strukturänderungen und Rollouts {#structure-changes-and-rollouts}

Änderungen an der Inhaltsstruktur in einem Blueprint/einer Quellstruktur werden in einer Live Copy unterschiedlich umgesetzt. Dies ist abhängig von der Art der Änderung:

* **** Das Erstellen neuer Seiten in einem Blueprint führt dazu, dass entsprechende Seiten in Live Copies nach dem Rollout mit der standardmäßigen Rollout-Konfiguration erstellt werden.

* **** Das Löschen von Seiten in einem Blueprint führt dazu, dass die entsprechenden Seiten nach dem Rollout mit der standardmäßigen Rollout-Konfiguration aus den Live Copies gelöscht werden.

* **** Das Verschieben von Seiten in einen Blueprint führt  **** nicht dazu, dass entsprechende Seiten nach dem Rollout mit standardmäßiger Rollout-Konfiguration in Live Copies verschoben werden:

   * Der Grund hierfür ist, dass eine Seitenverschiebung implizit eine Seitenlöschung beinhaltet. Dies kann bei der Veröffentlichung zu unerwartetem Verhalten führen, da das Löschen von Seiten im Rahmen der Bearbeitung zur Folge hat, dass der entsprechende Inhalt bei der Veröffentlichung automatisch deaktiviert wird. Dies kann sich wiederum auch auf verwandte Elemente wie etwa Links und Lesezeichen auswirken.
   * Die Inhaltsvererbung der jeweiligen Live Copy-Seiten wird aktualisiert, um den neuen Ort ihrer Quellen im Blueprint widerzuspiegeln.
   * Beachten Sie die folgenden Best Practices, um einen Seitenwechsel von einem Blueprint zu Live Copies vollständig durchzuführen:

>[!NOTE]
>
>Dies funktioniert nur mit dem Trigger [Bei Rollout](https://helpx.adobe.com/experience-manager/6-3/sites/administering/using/msm-sync.html#rollout-triggers).

* Erstellen Sie eine benutzerdefinierte Rollout-Konfiguration:

   * Diese neue Konfiguration muss die Aktion enthalten:

      `PageMoveAction`

      Fügen Sie dieser Konfiguration keine anderen Aktionen hinzu.

* Positionieren Sie die neue Konfiguration:

   * Um die Seitenverschiebung vollständig auszuführen und gleichzeitig die entsprechenden Seiten an ihrer alten Position in der Live Copy zu löschen:

      * Positionieren Sie die neu erstellte Konfiguration vor der standardmäßigen Rollout-Konfiguration.

         Die Löschung der Seiten an ihrem alten Ort wird durch die standardmäßige Rollout-Konfiguration übernommen.
   * So führen Sie die Seitenverschiebung durch, während die entsprechenden Seiten in den Live Copies an ihrem alten Speicherort bleiben (im Wesentlichen Duplizieren des Inhalts):

      * Positionieren Sie die neu erstellte Konfiguration nach der standardmäßigen Rollout-Konfiguration.

         Dadurch wird sichergestellt, dass in der Live Copy kein Inhalt gelöscht oder für die Veröffentlichung deaktiviert wird.


## Anpassen von Rollouts {#customizing-rollouts}

Die Rollout-Konfigurationen von MSM sind in hohem Maße anpassbar. Beachten Sie, dass die Automatisierung von Rollouts weitreichende Folgen haben kann. Aus diesem Grund sollte unter anderem den folgenden Schritten eine *sehr* sorgfältige Planung vorausgehen:

* Automatisierung von Rollouts; Beispielsweise mit [onModify-Triggern](#onmodify),
* Anpassen von [Knotentypen/-eigenschaften](#node-types-properties)
* Starten nachfolgender Workflows,
* und/oder die Aktivierung von Inhalten im Rahmen von Rollouts.

### onModify {#onmodify}

Beachten Sie bei Verwendung des [Rollout-Auslösers](/help/sites-administering/msm-sync.md#rollout-triggers) `onModify` Folgendes:

* Die Automatisierung von Rollouts mit Auslösern vom Typ `onModify` kann die Leistung bei der Bearbeitung beeinträchtigen, da nach jeder Seitenbearbeitung Rollouts ausgelöst werden.**

* Das Rollout-Ergebnis entspricht aus folgenden Gründen möglicherweise nicht den Erwartungen:

   * Die Reihenfolge der resultierenden Änderungsereignisse kann nicht angegeben werden.
   * Die ereignisbasierte Architektur kann die Reihenfolge der an den Rollout-Manager übergebenen Ereignisse nicht garantieren.

* Die Verwendung einer solchen Rollout-Konfiguration kann im Falle von parallelen Aktualisierungen derselben Ressource zu Bestätigungskonflikten führen.

Daher wird empfohlen, *nur* `onModify`-Trigger zu verwenden, wenn die Vorteile des automatischen Rollout-Starts gegenüber möglichen Leistungsproblemen überwiegen.

### Knotentypen/-eigenschaften {#node-types-properties}

Zur Erinnerung:

* Neben der Anpassung von Rollout-Aktionen ermöglicht MSM auch die Anpassung von Knoteneigenschaften, für die ein Rollout durchgeführt wird. Die [MSM-OSGi-Konfiguration ermöglicht das Ausschließen von Knotentypen](/help/sites-administering/msm-sync.md#excluding-properties-and-node-types-from-synchronization), sodass diese nicht aus der Quelle in die Live Copy kopiert werden.

## Weiterführende Informationen {#further-information}

Die entsprechenden Themen werden auf dieser Seite sowie auf den folgenden Seiten behandelt:

* [Erstellen und Synchronisieren von Live Copies](/help/sites-administering/msm-livecopy.md)
* [Konsole „Live Copy-Übersicht“](/help/sites-administering/msm-livecopy-overview.md)
* [Konfigurieren der Synchronisierung von Live Copies](/help/sites-administering/msm-sync.md)
* [MSM-Rollout-Konflikte](/help/sites-administering/msm-rollout-conflicts.md)
