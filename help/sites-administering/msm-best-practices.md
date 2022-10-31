---
title: Best Practices für MSM
description: Hier finden Sie Best Practices für die Einrichtung und Verwendung von AEM MSM (Multi Site Manager) – zusammengestellt von Technik- und Beratungsteams von Adobe.
topic-tags: site-features, best-practices
feature: Multi Site Manager
exl-id: 3fedc1ba-64f5-4fbe-9ee5-9b96b75dda58
source-git-commit: a5f3e33a6abe7ac1bbd610a8528fd599d1ffd2aa
workflow-type: tm+mt
source-wordcount: '1616'
ht-degree: 100%

---

# Best Practices für MSM{#msm-best-practices}

## Allgemein {#general}

MSM ist ein konfigurierbares Framework für die Automatisierung der Inhaltsbereitstellung. Implementierungen umfassen häufig große Teile einer Website und erstrecken sich über Organisationen und geografische Regionen. Es wird daher dringend empfohlen, MSM-Implementierungen mit der gleichen Sorgfalt zu planen wie Ihre Website:

* **Planen Sie zunächst sorgfältig die Struktur und den Inhaltsfluss**, bevor Sie mit der Implementierung beginnen.
* **Halten Sie die Anzahl der Live Copies auf ein Minimum beschränkt.** Die Verarbeitung von Live Copies ist eine ressourcenintensive Aufgabe. Je mehr Live Copies in Ihrem System vorhanden sind, desto mehr kann die Leistung beeinträchtigt werden: von der Verarbeitung interner Live Copy-Indizes über Live Copy-Vorgänge wie Rollouts bis hin zu Benutzeroberflächen-Vorgängen wie der Anzeige von Live Copy-Beziehungen in der Sites Admin-Referenzleiste. Es empfiehlt sich, Live Copies von Websites oder Verzweigungen einer Website zu erstellen, wobei die Beziehungen der Live Copy auf die Seiten der Website oder Verzweigung vererbt werden. Vermeiden Sie die Erstellung einzelner Live Copies für Seiten in einer Website oder einer Verzweigung, wenn die gesamte Struktur in eine Live Copy umgewandelt werden kann.
* **Beschränken Sie Anpassungen auf das Nötigste.** MSM unterstützt zwar ein hohes Maß an Anpassungen (beispielsweise Rollout-Konfigurationen). Es empfiehlt sich jedoch, nicht zu viele Anpassungen vorzunehmen, um die Leistung und Zuverlässigkeit Ihrer Website nicht zu beeinträchtigen und Website-Upgrades durchführen zu können.
* Etablieren Sie frühzeitig ein **Governance-Modell** und schulen Sie die Benutzer entsprechend. Bei der Governance empfiehlt es sich, die **Autorität zu minimieren, über die lokale Inhaltsersteller verfügen**, um Inhalt anderen lokalen Benutzern oder ihren jeweiligen Live Copies zuzuordnen oder mit ihnen zu verknüpfen. Das liegt daran, dass nicht regulierte verkettete Vererbungen die Komplexität einer MSM-Struktur erheblich erhöhen und ihre Leistung und Zuverlässigkeit beeinträchtigen.

* Wenn Sie über einen Plan für Ihre Struktur, Ihren Inhaltsfluss, Ihre Automatisierung und die Governance verfügen, **erstellen Sie einen Prototyp und testen Sie Ihr System sorgfältig**, bevor Sie mit der Live-Implementierung beginnen.
* **Adobe Consulting und führende Systemintegratoren** sind bestens mit der Planung und Implementierung der Inhaltsautomatisierung mit MSM vertraut und können Sie sowohl bei den ersten Schritten mit Ihrem MSM-Projekt als auch im weiteren Verlauf der Implementierung unterstützen.

>[!NOTE]
>
>Weitere Information zur Verwendung von MSM finden Sie in den entsprechenden Knowledge Base-Artikeln:
>
>* [Beheben von Problemen mit MSM und häufig gestellte Fragen](troubleshoot-msm.md)
>


>[!NOTE]
>
>Sie können auch die [Bezugskomponente](/help/sites-authoring/default-components-foundation.md#reference) verwenden, um eine einzelne Seite oder einen Absatz wiederzuverwenden. Bedenken Sie jedoch Folgendes:
>
>* MSM ist flexibler und ermöglicht eine differenziertere Steuerung von Art und Zeitpunkt der Inhaltssynchronisierung.
>* [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) werden nun anstelle der Foundation-Komponenten empfohlen.
>


## Live Copy-Quellen und Blueprint-Konfigurationen {#live-copy-sources-and-blueprint-configurations}

Eine Live Copy kann entweder unter Verwendung [regulärer Seiten](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page) oder unter Verwendung einer [Blueprint-Konfiguration](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) erstellt werden. Beide Varianten sind zulässig.

Die Verwendung einer Blueprint-Konfiguration hat allerdings folgende Vorteile:

* Der Autor kann für eine Blueprint die Option **Rollout** verwenden und so (explizit) Änderungen an Live Copies pushen, die von dieser Blueprint erben.
* Der Autor kann **Website erstellen** nutzen, wodurch der Benutzer einfach Sprachen auswählen und die Struktur der Live Copy konfigurieren kann;
* Sie definiert eine standardmäßige Rollout-Konfiguration für Live Copies, die über eine Beziehung mit der Blueprint verfügen.

Ohne Verweis auf eine Blueprint-Konfiguration können Rollouts nur von Live Copies selbst initiiert werden, wobei im Wesentlichen Inhalt aus der Quelle abgerufen wird.

Wenn Sie eine neue Website mit Live Copy erstellen, empfiehlt es sich, Blueprint-Konfigurationen zu erstellen, um die Verfügbarkeit sämtlicher MSM-Features sicherzustellen.

>[!NOTE]
>
>Beachten Sie, dass CUGs auf der Registerkarte „Berechtigungen“ aus Blueprints nicht zu Live Copies ausgerollt werden können. Planen Sie dies ein, wenn Sie eine Live Copy konfigurieren.

## Komponenten- und Container-Synchronisierung {#components-and-container-synchronization}

Für die Synchronisierung von Komponenten gilt in MSM im Allgemeinen folgende Rollout-Regel:

* Beim Rollout der Komponenten werden alle in der Blueprint enthaltenen Ressourcen synchronisiert.
* Container synchronisieren nur die aktuelle Ressource.

Das bedeutet, dass Komponenten als Aggregat behandelt und bei einem Rollout die Komponente selbst und alle ihre untergeordneten Elemente durch die Elemente aus den Blueprints ersetzt werden. Wenn also eine Ressource einer solchen Komponente lokal hinzugefügt wird, geht sie beim Rollout der Blueprint verloren.

Um die Schachtelung von Komponenten zu unterstützen, sodass lokal hinzugefügte Komponenten bei einem Rollout erhalten bleiben, muss die Komponente als Container deklariert werden. Ein Beispiel: Die parsys-Standardkomponente wird als Container deklariert, um lokal hinzugefügten Inhalt zu unterstützen.

>[!NOTE]
>
>Fügen Sie der Komponente die Eigenschaft `cq:isContainer` hinzu, um sie als Container zu kennzeichnen.

## Erstellen einer Website {#create-site}

Live Copies können mit AEM auf zwei Arten erstellt werden:

* Beim [Erstellen einer Live Copy](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page)

   Hierbei handelt es sich um den allgemeineren Ansatz, mit dem Sie Live Copies von einer beliebigen Seite aus erstellen können. Die Inhaltsstruktur einer Live Copy entspricht exakt der Quelle.

* Beim [Erstellen einer Website](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration)

   Dies ist ein speziellerer Ansatz, der hauptsächlich für die Erstellung von Websites mit einer mehrsprachigen Struktur gedacht ist.

Berücksichtigen Sie beim Erstellen einer Website folgende Punkte:

* Für die Erstellung einer neuen Website benötigen Sie eine [Blueprint-Konfiguration](/help/sites-administering/msm-livecopy.md#managing-blueprint-configurations).
* Um das Auswählen von Sprachpfaden zu ermöglichen, die für eine neue Website erstellt werden sollen, muss die Blueprint (Quelle) die entsprechenden Sprachstämme enthalten.
* Nach der [Erstellung einer neuen Website als Live Copy](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) (mithilfe von **Erstellen** > **Website**) sind die ersten beiden Ebenen dieser Live Copy *flach*. Untergeordnete Elemente der Seite sind nicht Teil der Live-Beziehung, werden bei einem Rollout aber trotzdem berücksichtigt, wenn eine dem Auslöser entsprechende Live-Beziehung gefunden wird.

   Dadurch lässt sich Folgendes vermeiden:

   * Manuelles Hinzufügen von Sprachen in der Blueprint (unterhalb der ersten Ebene)
   * Manuelles Hinzufügen von Inhalt unmittelbar unter dem Sprach-Stamm
   * Automatische Übertragung des neuen Inhalts auf die Live Copy beim Rollout

## MSM und mehrsprachige Websites {#msm-and-multilingual-websites}

MSM kann Sie auf zwei Arten beim Erstellen mehrsprachiger Websites unterstützen:

* Beim Erstellen von primären Sprachdateien

   * MSM bietet zwar selbst **keine Inhaltsübersetzung**, kann jedoch mit entsprechenden Übersetzungs-Connectors von Dritten integriert werden. Beachten Sie Folgendes:

      * Mit MSM können Sie die Vererbung auf Seiten- und/oder Komponentenebene unterbinden. So können Sie verhindern, dass übersetzter Inhalt aus einer Live Copy beim nächsten Rollout durch noch nicht übersetzten Inhalt aus einer Blueprint überschrieben wird.
      * Einige Übersetzungs-Connectoren von Dritten bieten eine automatisierte Verwaltung der MSM-Vererbung.

         Weitere Informationen erhalten Sie von Ihrem Übersetzungsdienstleister.

      * Eine Alternative für die Erstellung und Übersetzung von Sprachstämmen ist die Verwendung von Sprachkopien in Verbindung mit dem vorgefertigten AEM-Framework für die Übersetzungsintegration.

* Beim Rollout von Inhalt auf der Grundlage von primären Sprachdateien.

   * Beispielsweise auf der Grundlage der französischen primären Sprachdatei für länderspezifische Websites wie etwa Frankreich/Französisch, Kanada/Französisch und Schweiz/Französisch.

Weitere Informationen finden Sie unter [Übersetzen von Inhalt für mehrsprachige Websites](/help/sites-administering/translation.md) und in den [Best Practices zur Übersetzung](/help/sites-administering/tc-bp.md).

## Strukturänderungen und Rollouts {#structure-changes-and-rollouts}

Änderungen an der Inhaltsstruktur in einer Blueprint/Quellstruktur werden in einer Live Copy unterschiedlich umgesetzt. Dies ist abhängig von der Art der Änderung:

* Wenn Sie neue Seiten in einer Blueprint **erstellen**, werden nach dem Rollout mit der standardmäßigen Rollout-Konfiguration entsprechende Seiten in Live Copies erstellt.

* Wenn Sie Seiten in einer Blueprint **löschen**, werden die entsprechenden Seiten nach dem Rollout mit der standardmäßigen Rollout-Konfiguration aus Live Copies gelöscht.

* Wenn Sie Seiten in einer Blueprint **verschieben**, werden die entsprechenden Seiten nach dem Rollout mit der standardmäßigen Rollout-Konfiguration in Live Copies **nicht** verschoben:

   * Der Grund hierfür ist, dass eine Seitenverschiebung implizit eine Seitenlöschung beinhaltet. Dies kann bei der Veröffentlichung zu unerwartetem Verhalten führen, da das Löschen von Seiten im Rahmen der Bearbeitung zur Folge hat, dass der entsprechende Inhalt bei der Veröffentlichung automatisch deaktiviert wird. Dies kann sich wiederum auch auf verwandte Elemente wie etwa Links und Lesezeichen auswirken.
   * Die Inhaltsvererbung der jeweiligen Live Copy-Seiten wird aktualisiert, um den neuen Ort ihrer Quellen in der Blueprint widerzuspiegeln.
   * Im Anschluss finden Sie einige Best Practices für die vollständige Umsetzung einer Seitenverschiebung aus einer Blueprint in Live Copies:

>[!NOTE]
>
>Dies funktioniert nur mit dem [Auslöser „Bei Rollout“](/help/sites-administering/msm-sync.md#rollout-triggers).

* Erstellen Sie eine benutzerdefinierte Rollout-Konfiguration:

   * Diese neue Konfiguration muss die folgende Aktion enthalten:

      `PageMoveAction`

      Fügen Sie dieser Konfiguration keine anderen Aktionen hinzu.

* Positionieren Sie die neue Konfiguration:

   * Gehen Sie wie folgt vor, um ein vollständiges Rollout der Seitenverschiebung durchzuführen und gleichzeitig die entsprechenden Seiten an ihrem alten Ort in der Live Copy zu löschen:

      * Positionieren Sie die neu erstellte Konfiguration vor der standardmäßigen Rollout-Konfiguration.

         Die Löschung der Seiten an ihrem alten Ort wird durch die standardmäßige Rollout-Konfiguration übernommen.
   * Gehen Sie wie folgt vor, um das Rollout der Seitenverschiebung durchzuführen und dabei die entsprechenden Seiten an ihrem alten Ort beizubehalten (und somit im Grunde den Inhalt zu duplizieren):

      * Positionieren Sie die neu erstellte Konfiguration nach der standardmäßigen Rollout-Konfiguration.

         Dadurch wird sichergestellt, dass in der Live Copy kein Inhalt gelöscht oder für die Veröffentlichung deaktiviert wird.


## Anpassen von Rollouts {#customizing-rollouts}

Die Rollout-Konfigurationen von MSM sind in hohem Maße anpassbar. Beachten Sie, dass die Automatisierung von Rollouts weitreichende Folgen haben kann. Aus diesem Grund sollte unter anderem den folgenden Schritten eine *sehr* sorgfältige Planung vorausgehen:

* Automatisieren von Rollouts (etwa mit [onModify-Auslösern](#onmodify))
* Anpassen von [Knotentypen/-eigenschaften](#node-types-properties)
* Starten von Folge-Workflows
* Und/oder Aktivieren von Inhalt im Rahmen eines Rollouts.

### onModify {#onmodify}

Beachten Sie bei Verwendung des [Rollout-Auslösers](/help/sites-administering/msm-sync.md#rollout-triggers) `onModify` Folgendes:

* Die Automatisierung von Rollouts mit Auslösern vom Typ `onModify` kann die Leistung bei der Bearbeitung beeinträchtigen, da nach jeder Seitenbearbeitung Rollouts ausgelöst werden.**

* Das Rollout-Ergebnis entspricht aus folgenden Gründen möglicherweise nicht den Erwartungen:

   * Die Reihenfolge der resultierenden Änderungsereignisse kann nicht angegeben werden.
   * Die ereignisbasierte Architektur kann die Reihenfolge der an den Rollout-Manager übergebenen Ereignisse nicht garantieren.

* Die Verwendung einer solchen Rollout-Konfiguration kann im Falle von parallelen Aktualisierungen derselben Ressource zu Bestätigungskonflikten führen.

Auslöser vom Typ `onModify` sollten daher *nur* verwendet werden, wenn die Vorteile einer automatischen Rollout-Initiierung die potenziellen Leistungsprobleme überwiegen.

### Knotentypen/-eigenschaften {#node-types-properties}

Zur Erinnerung:

* Neben der Anpassung von Rollout-Aktionen ermöglicht MSM auch die Anpassung von Knoteneigenschaften, für die ein Rollout durchgeführt wird. Die [MSM-OSGi-Konfiguration ermöglicht das Ausschließen von Knotentypen](/help/sites-administering/msm-sync.md#excluding-properties-and-node-types-from-synchronization), sodass diese nicht aus der Quelle in die Live Copy kopiert werden.

## Weiterführende Informationen {#further-information}

Die entsprechenden Themen werden auf dieser Seite sowie auf den folgenden Seiten behandelt:

* [Erstellen und Synchronisieren von Live Copies](/help/sites-administering/msm-livecopy.md)
* [Konsole „Live Copy-Übersicht“](/help/sites-administering/msm-livecopy-overview.md)
* [Konfigurieren der Synchronisierung von Live Copies](/help/sites-administering/msm-sync.md)
* [MSM-Rollout-Konflikte](/help/sites-administering/msm-rollout-conflicts.md)
