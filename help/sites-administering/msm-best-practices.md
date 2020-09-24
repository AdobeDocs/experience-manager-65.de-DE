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
translation-type: tm+mt
source-git-commit: a929252a13f66da8ac3e52aea0655b12bdd1425f
workflow-type: tm+mt
source-wordcount: '1530'
ht-degree: 65%

---


# Best Practices für MSM{#msm-best-practices}

## Allgemein {#general}

MSM ist ein konfigurierbares Framework für die Automatisierung der Inhaltsbereitstellung. Implementierungen umfassen häufig große Teile einer Website und erstrecken sich über Organisationen und geografische Regionen. Es wird daher dringend empfohlen, MSM-Implementierungen mit der gleichen Sorgfalt zu planen wie Ihre Website:

* Carefully **plan structure and content flows** before starting implementation.
* **Beschränken Sie Anpassungen auf das Nötigste.** MSM unterstützt zwar einen hohen Grad an Anpassung (z.B. Rollout-Konfigurationen), ist aber in der Regel die beste Methode für die Leistung, Zuverlässigkeit und Upgradefähigkeit Ihrer Website, die Anpassung zu minimieren.
* Establish a **governance** model early, and train users accordingly, to ensure success. A best practice from a governance point of view is to **minimize the authority that local content producers have** to allocate/connect content to other local users and their respective live copies. Das liegt daran, dass ungesteuerte, verkettete Erbschaften die Komplexität einer MSM-Struktur deutlich erhöhen und ihre Leistung und Zuverlässigkeit beeinträchtigen können.

* Once a plan exists for your structure, content flows, automation and governance - **prototype and thoroughly test your system**, before starting live implementation.
* Keep in mind that **Adobe Consulting and leading System Integrators** have deep experience planning and implementing content automation with MSM, so they can help you both get started with your MSM project and throughout its entire implementation.

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

* Allow the author to use the **Rollout** option on a blueprint - to (explicitly) push modifications to live copies that inherit from this blueprint.
* Allow the author to use **Create Site**; this allows the user to easily select languages and configure the structure of the live copy.
* Sie definiert eine standardmäßige Rollout-Konfiguration für Live Copies, die über eine Beziehung mit dem Blueprint verfügen.

Ohne Verweis auf eine Blueprint-Konfiguration können Rollouts nur von Live Copies selbst initiiert werden, wobei im Wesentlichen Inhalt aus der Quelle abgerufen wird.

Wenn Sie eine neue Website mit Live Copy erstellen, empfiehlt es sich, Blueprint-Konfigurationen zu erstellen, um die Verfügbarkeit sämtlicher MSM-Features sicherzustellen.

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

* When [creating a Live Copy](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page)

   Dies kann als allgemeiner Ansatz betrachtet werden, der es Ihnen ermöglicht, Live-Kopien von jeder Seite zu erstellen. Die Inhaltsstruktur einer Live Copy entspricht exakt der Quelle.

* Beim [Erstellen einer Site](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration)

   Dies ist ein speziellerer Ansatz, vor allem zur Erstellung von Websites mit mehrsprachiger Struktur.

Berücksichtigen Sie beim Erstellen einer Website folgende Punkte:

* Für die Erstellung einer neuen Website benötigen Sie eine [Blueprint-Konfiguration](/help/sites-administering/msm-livecopy.md#managing-blueprint-configurations).
* Damit die Auswahl von Sprachpfaden in einer neuen Site möglich ist, müssen die entsprechenden Sprachwurzeln im Entwurf (Quelle) vorhanden sein.
* Once a [new site has been created as a live copy](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) (using **Create**, then **Site**), the first two levels of this live copy are *shallow*. Untergeordnete Elemente der Seite sind nicht Teil der Live-Beziehung, werden bei einem Rollout aber trotzdem berücksichtigt, wenn eine dem Auslöser entsprechende Live-Beziehung gefunden wird.

   Dadurch lässt sich Folgendes vermeiden:

   * Manuelles Hinzufügen von Sprachen im Blueprint (unterhalb der ersten Ebene)
   * Manuelles Hinzufügen von Inhalt unmittelbar unter dem Sprach-Stamm
   * Automatische Übertragung des neuen Inhalts auf die Live Copy beim Rollout

## MSM und mehrsprachige Websites {#msm-and-multilingual-websites}

MSM kann Sie auf zwei Arten beim Erstellen mehrsprachiger Websites unterstützen:

* Beim Erstellen von Sprach-Mastern

   * MSM bietet zwar selbst **keine Inhaltsübersetzung**, kann jedoch mit entsprechenden Übersetzungs-Connectors von Dritten integriert werden. Beachten Sie Folgendes:

      * Mit MSM können Sie die Vererbung auf Seiten- und/oder Komponentenebene unterbinden. So können Sie verhindern, dass übersetzter Inhalt aus einer Live Copy beim nächsten Rollout durch noch nicht übersetzten Inhalt aus einem Blueprint überschrieben wird.
      * Einige Übersetzungs-Connectors von Dritten bieten eine automatisierte Verwaltung der MSM-Vererbung.

         Weitere Informationen erhalten Sie von Ihrem Übersetzungsdienstleister.

      * Eine Alternative für die Erstellung und Übersetzung von Sprach-Mastern ist die Verwendung von Sprachkopien in Verbindung mit dem vorgefertigten AEM-Framework für die Übersetzungsintegration.

* Beim Rollout von Inhalt auf der Grundlage von Sprach-Mastern

   * Beispielsweise auf der Grundlage des französischen Sprach-Masters für länderspezifische Websites wie etwa Frankreich/Französisch, Kanada/Französisch und Schweiz/Französisch.

Weitere Informationen finden Sie unter [Übersetzen von Inhalt für mehrsprachige Websites](/help/sites-administering/translation.md) und in den [Best Practices zur Übersetzung](/help/sites-administering/tc-bp.md).

## Strukturänderungen und Rollouts {#structure-changes-and-rollouts}

Änderungen an der Inhaltsstruktur in einem Blueprint/einer Quellstruktur werden in einer Live Copy unterschiedlich umgesetzt. Dies ist abhängig von der Art der Änderung:

* **Das Erstellen** neuer Seiten in einem Entwurf führt dazu, dass die entsprechenden Seiten in Live-Kopien nach der Aktualisierung mit der standardmäßigen Rollout-Konfiguration erstellt werden.

* **Das Löschen** von Seiten in einem Entwurf führt dazu, dass die entsprechenden Seiten nach der Aktualisierung mit der standardmäßigen Rollout-Konfiguration aus den Live-Kopien gelöscht werden.

* **Das Verschieben** von Seiten in einem Entwurf führt **nicht** dazu, dass die entsprechenden Seiten nach der Einführung mit der standardmäßigen Rollout-Konfiguration in Live-Kopien verschoben werden:

   * Der Grund: Eine Seitenverschiebung beinhaltet implizit eine Seitenlöschung. Dies kann bei der Veröffentlichung zu unerwartetem Verhalten führen, da das Löschen von Seiten im Rahmen der Bearbeitung zur Folge hat, dass der entsprechende Inhalt bei der Veröffentlichung automatisch deaktiviert wird. Dies kann sich wiederum auch auf verwandte Elemente wie etwa Links und Lesezeichen auswirken.
   * Die Inhaltsvererbung der jeweiligen Live Copy-Seiten wird aktualisiert, um den neuen Ort ihrer Quellen im Blueprint widerzuspiegeln.
   * Um eine Seite vollständig von einem Entwurf in Live-Kopien zu verschieben, sollten Sie die folgenden bewährten Verfahren beachten:

>[!NOTE]
>
>This will work only with the [On Rollout trigger](https://helpx.adobe.com/experience-manager/6-3/sites/administering/using/msm-sync.html#rollout-triggers).

* Erstellen Sie eine benutzerdefinierte Rollout-Konfiguration:

   * Diese neue Konfiguration muss die Aktion enthalten:

      `PageMoveAction`

      Fügen Sie dieser Konfiguration keine weiteren Aktionen hinzu.

* Positionieren Sie die neue Konfiguration:

   * Um die Seite vollständig auszurollen, verschieben Sie sie, während Sie die entsprechenden Seiten an ihrer alten Position in der Live-Kopie löschen:

      * Positionieren Sie die neu erstellte Konfiguration vor der standardmäßigen Rollout-Konfiguration.

         Die Löschung der Seiten an ihrem alten Ort wird durch die standardmäßige Rollout-Konfiguration übernommen.
   * So rollen Sie die Seitenverschiebung unter Beibehaltung der jeweiligen Seiten an ihrer alten Position in den Live-Kopien (im Wesentlichen Duplizieren des Inhalts) aus:

      * Positionieren Sie die neu erstellte Konfiguration nach der standardmäßigen Rollout-Konfiguration.

         Dadurch wird sichergestellt, dass in der Live Copy kein Inhalt gelöscht oder für die Veröffentlichung deaktiviert wird.


## Anpassen von Rollouts {#customizing-rollouts}

Die Rollout-Konfigurationen von MSM sind in hohem Maße anpassbar. Beachten Sie, dass die Automatisierung von Rollouts weitreichende Folgen haben kann. Aus diesem Grund sollte unter anderem den folgenden Schritten eine *sehr* sorgfältige Planung vorausgehen:

* automating rollouts; for example, with [onModify triggers](#onmodify),
* Anpassen von [Knotentypen/-eigenschaften](#node-types-properties)
* Beginn nachfolgender Workflows,
* und/oder das Aktivieren von Inhalten im Rahmen von Rollouts.

### onModify {#onmodify}

Beachten Sie bei Verwendung des [Rollout-Auslösers](/help/sites-administering/msm-sync.md#rollout-triggers) `onModify` Folgendes:

* Automating rollouts with `onModify` triggers may have a negative impact on authoring performance as they trigger rollouts after *every* page modification.

* Das Rollout-Ergebnis entspricht aus folgenden Gründen möglicherweise nicht den Erwartungen:

   * Die Reihenfolge der resultierenden Änderungsereignisse kann nicht angegeben werden.
   * Die ereignisbasierte Architektur kann die Reihenfolge der an den Rollout-Manager übergebenen Ereignisse nicht garantieren.

* Die Verwendung einer solchen Rollout-Konfiguration kann im Falle von parallelen Aktualisierungen derselben Ressource zu Bestätigungskonflikten führen.

Therefore, it is recommended that you *only* use `onModify` triggers if the benefits of automatic rollout initiation outweigh any potential performance issues.

### Knotentypen/-eigenschaften {#node-types-properties}

Zur Erinnerung:

* Neben der Anpassung der Rollout-Aktionen können Sie mit MSM auch die Knoteneigenschaften anpassen, für die ein Rollout ausgeführt wird. Die [MSM-OSGi-Konfiguration ermöglicht das Ausschließen von Knotentypen](/help/sites-administering/msm-sync.md#excluding-properties-and-node-types-from-synchronization), sodass diese nicht aus der Quelle in die Live Copy kopiert werden.

## Weiterführende Informationen {#further-information}

Die entsprechenden Themen werden auf dieser Seite sowie auf den folgenden Seiten behandelt:

* [Erstellen und Synchronisieren von Live Copies](/help/sites-administering/msm-livecopy.md)
* [Konsole „Live Copy-Übersicht“](/help/sites-administering/msm-livecopy-overview.md)
* [Konfigurieren der Synchronisierung von Live Copies](/help/sites-administering/msm-sync.md)
* [MSM-Rollout-Konflikte](/help/sites-administering/msm-rollout-conflicts.md)

