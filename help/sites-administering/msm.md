---
title: '„Wiederverwenden von Inhalten: Multi Site Manager und Live Copy“'
description: Erfahren Sie mehr über die Wiederverwendung von Inhalten mit Live Copies und dem Multi Site Manager.
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
exl-id: 1e839845-fb5c-4200-8ec5-6ff744a96943
source-git-commit: 6799f1d371734b69c547f3c0c68e1e633aa63229
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Wiederverwenden von Inhalten: Multi Site Manager und Live Copy{#reusing-content-multi-site-manager-and-live-copy}

Mit Multi Site Manager (MSM) können Sie denselben Site-Inhalt an mehreren Orten verwenden. MSM verwendet seine Live Copy-Funktion, um Folgendes zu erreichen:

* Mit MSM können Sie:

   * Inhalte einmalig erstellen und diese
   * Kopieren Sie diesen Inhalt in andere Bereiche ([Live Copies](#live-copies)) der gleichen oder anderen Sites.

* MSM behält dann die (Live-)Beziehungen zwischen Ihren Quellinhalten und deren Live Copies bei, sodass:

   * Wenn Sie den Quellinhalt ändern, werden die Quelle und die Live Copies synchronisiert (um diese Änderungen auch auf die Live Copies anzuwenden).
   * Sie können den Inhalt der Live Copies anpassen, indem Sie die Live-Beziehung für einzelne Unterseiten, Komponenten oder beides trennen. Auf diese Weise werden Änderungen an der Quelle nicht mehr auf die Live Copy angewendet.

Diese und die folgenden Seiten behandeln die zugehörigen Probleme:

* [Erstellen und Synchronisieren von Live Copies](/help/sites-administering/msm-livecopy.md)
* [Konsole „Live Copy-Übersicht“](/help/sites-administering/msm-livecopy-overview.md)
* [Konfigurieren der Synchronisierung von Live Copies](/help/sites-administering/msm-sync.md)
* [MSM-Rollout-Konflikte](/help/sites-administering/msm-rollout-conflicts.md)
* [Best Practices für MSM](/help/sites-administering/msm-best-practices.md)

## Mögliche Szenarien {#possible-scenarios}

Es gibt viele Anwendungsfälle für MSM und Live Copies. Einige Szenarien umfassen:

* **Multinational - Global zu Local Company**

  Ein typisches Anwendungsbeispiel, das MSM unterstützt, ist die Wiederverwendung von Inhalten auf mehreren multinationalen Websites mit derselben Sprache. Dadurch kann der Kerninhalt wiederverwendet werden, wobei nationale Varianten berücksichtigt werden.

  Beispielsweise wird der englische Abschnitt der We.Retail-Referenz-Site für Kunden in den USA erstellt. Der Großteil der Inhalte dieser Website kann auch für andere We.Retail-Websites verwendet werden, die englischsprachigen Kunden aus verschiedenen Ländern und Kulturen gerecht werden. Der Kerninhalt bleibt auf allen Sites gleich, wobei regionale Anpassungen vorgenommen werden können.

  Die folgende Struktur kann für Sites in den USA, Großbritannien, Kanada und Australien verwendet werden:

  ```xml
  /content
      |- we.retail
          |- language-masters
              |- en
      |- we.retail
          |- us
              |- en
      |- we.retail
          |- gb
              |- en
      |- we.retail
          |- ca
              |- en
      |- we.retail
          |- au
              |- en
  ```

  >[!NOTE]
  >
  >MSM übersetzt die Inhalte nicht. Er wird zur Erstellung der erforderlichen Struktur und zur Bereitstellung von Inhalten verwendet.
  >
  >
  >Unter [Übersetzen von Inhalten für mehrsprachige Sites](/help/sites-administering/translation.md) finden Sie weitere Informationen zu einem solchen Beispiel.

* **National – Zentrale zu Zweigstellen**

  Alternativ kann ein Unternehmen mit einem Händlernetz separate Websites für seine einzelnen Händler anbieten, wobei es sich jeweils um eine Abwandlung der Hauptsite handelt, die vom Hauptbüro bereitgestellt wird. Dies könnte für ein einzelnes Unternehmen mit mehreren regionalen Niederlassungen oder ein nationales Franchisesystem mit einem zentralen Franchisegeber und mehreren lokalen Franchisenehmern gelten.

  Die Hauptverwaltung kann die zentralen Informationen bereitstellen, während die regionalen Stellen lokale Informationen hinzufügen können, wie z. B. Kontaktdaten, Öffnungszeiten und Veranstaltungen.

  ```xml
  /content
      |- head-office-Berlin
      |- branch-Hamburg
      |- branch-Stuttgart
      |- branch-Munich
      |- branch-Frankfurt
  ```

* **Mehrere Versionen**

  Sie können MSM auch verwenden, um Versionen einer bestimmten Unterverzweigung zu erstellen. Beispielsweise eine Support-Subsite, die Details zu den verschiedenen Versionen eines bestimmten Produkts enthält, wobei die Basisinformationen konstant bleiben und nur die aktualisierten Funktionen geändert werden müssen:

  ```xml
  /content
      |- support
          |- product X
              |- v5.0
              |- v4.0
              |- v3.0
              |- v2.0
              |- v1.0
  ```

  >[!NOTE]
  >
  >In einem solchen Szenario müssen Sie entscheiden, ob Sie eine einfache Kopie erstellen oder Live Copies verwenden möchten.
  >
  >Es gibt ein Gleichgewicht zwischen:
  >
  >  * Wie viel des Kerninhalts muss über mehrere Versionen aktualisiert werden?
  >
  >und
  >
  >  * Wie viel der einzelnen Kopien angepasst werden muss.

## MSM über die Benutzeroberfläche {#msm-from-the-ui}

Auf MSM kann mithilfe verschiedener Optionen der jeweiligen Konsole direkt über die Benutzeroberfläche zugegriffen werden. Um eine Einführung zu erhalten, werden die wichtigsten Standorte aufgeführt:

* **Website erstellen** (**Sites**)

   * MSM unterstützt Sie bei der Verwaltung mehrerer Websites, die gemeinsame Inhalte enthalten. So werden beispielsweise Websites oft für internationale Zielgruppen bereitgestellt, sodass der Großteil der Inhalte in allen Ländern verwendet wird und nur eine Untergruppe der Inhalte für die einzelnen Länder bereitgestellt wird. Mit MSM können Sie [Erstellen von Live Copies, die basierend auf Ihrer Quellsite automatisch eine oder mehrere Sites aktualisieren](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration). Dies hilft Ihnen auch dabei, eine gemeinsame Basisstruktur zu erzwingen, den gemeinsamen Inhalt über mehrere Sites hinweg zu verwenden, ein gemeinsames Erscheinungsbild zu erhalten und Anstrengungen zur Verwaltung des Inhalts zu unternehmen, der sich zwischen den Sites tatsächlich unterscheidet.
   * Es ist eine vordefinierte Blueprint-Konfiguration erforderlich, um die Quelle anzugeben.
   * Erstellt eine Live Copy der vordefinierten Quelle.
   * Er stellt dem Benutzer die **Rollout** Schaltfläche.

* **Erstellen einer Live Copy** (**Sites**)

   * Mit MSM können Sie [Erstellen einer Ad-hoc-Live Copy (einmalig) einer einzelnen Seite oder Unterverzweigung einer Website](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page); zum Beispiel das Duplizieren einer Unterverzweigung, um Informationen über eine neue/aktualisierte Version eines Produkts bereitzustellen.
   * Erstellt eine Ad-hoc-Live Copy (keine Blueprint-Konfiguration erforderlich).
   * Sie kann verwendet werden, um (sofort) eine Live Copy einer beliebigen Seite/Verzweigung zu erstellen.
   * Erfordert die Option **Synchronisieren** (die **Rollout**-Schaltfläche wird nicht bereitgestellt).

* **Eigenschaften anzeigen** (**Sites**)

   * Bei Bedarf hilft Ihnen diese Option bei der [Überwachung Ihrer Live Copy](/help/sites-administering/msm-livecopy.md#monitoring-your-live-copy) durch Bereitstellung von Informationen zur zugehörigen **Live Copy** oder zur **Blueprint**.

* **Verweise** (**Sites**)

   * Die Leiste [Verweise](/help/sites-authoring/basic-handling.md#references) stellt Ihnen Informationen zu den **Live Copies** sowie den Zugriff auf die entsprechenden Aktionen bereit.

* **Live Copy-Übersicht** (**Sites**)

   * Mithilfe dieser Konsole können Sie [Anzeigen und Verwalten Ihres Blueprints und seiner Live Copies](/help/sites-administering/msm-livecopy-overview.md).

* **Blueprints** (**Tools** – **Sites**)

   * Mithilfe dieser Konsole können Sie [Erstellen und Verwalten von Blueprint-Konfigurationen](/help/sites-administering/msm-livecopy.md#creating-a-blueprint-configuration).

>[!NOTE]
>
>Aspekte der MSM-Funktionalität werden in mehreren anderen Adobe Experience Manager-Funktionen (AEM) verwendet (z. B. Launches, Catalog). In diesen Fällen wird die Live Copy von dieser Funktion verwaltet.

### Verwendete Begriffe {#terms-used}

Als Einführung bietet die folgende Tabelle einen Überblick über die wichtigsten Begriffe, die mit MSM verwendet werden. Diese werden in den nachfolgenden Abschnitten und Seiten ausführlicher behandelt:

<table>
 <tbody>
  <tr>
   <td><strong>Begriff</strong></td>
   <td><strong>Definition</strong></td>
   <td><strong>Weitere Einzelheiten</strong></td>
  </tr>
  <tr>
   <td><strong>Quelle</strong></td>
   <td>Die Originalseiten.</td>
   <td>Synonym für Blueprints und/oder Blueprint-Seiten.</td>
  </tr>
  <tr>
   <td><strong>Live Copy</strong></td>
   <td>Die Kopie (der Quelle), die wie durch die Rollout-Konfigurationen definiert von Synchronisierungsaktionen aufrechterhalten wird. </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Live Copy-Konfiguration</strong></td>
   <td>Festlegen der Konfigurationsdetails für eine Live Copy.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Live-Beziehung</strong><br /> </td>
   <td>Effektive Definition der Vererbung für eine bestimmte Ressource; Verbindungen zwischen Quelle und Live Copies.<br /> </td>
   <td>Stellt sicher, dass Änderungen an der Quelle mit der Live Copy synchronisiert werden können.</td>
  </tr>
  <tr>
   <td><strong>Blueprint</strong></td>
   <td>Synonym für Quelle.</td>
   <td>Sie kann durch eine Blueprint-Konfiguration definiert werden.</td>
  </tr>
  <tr>
   <td><strong>Blueprint-Konfiguration</strong></td>
   <td>Vordefinierte Konfiguration zur Angabe eines Quellpfads.</td>
   <td>Wenn in einer Blueprint-Konfiguration auf eine Blueprint-Seite verwiesen wird, ist der Befehl "Rollout"verfügbar.</td>
  </tr>
  <tr>
   <td><strong>Synchronisierung</strong></td>
   <td>Der allgemeine Begriff für die Synchronisierung von Inhalten zwischen der Quelle und den Live Copies (sowohl durch <strong>Rollout</strong> als auch <strong>Synchronisieren</strong>).</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Rollout</strong><br /> </td>
   <td>Synchronisiert von der Quelle mit der Live Copy.<br /> Sie kann von einem Autor (auf einer Blueprint-Seite) oder von einem Systemereignis (wie durch die Rollout-Konfiguration definiert) ausgelöst werden.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Rollout-Konfiguration</strong></td>
   <td>Regeln, die bestimmen, welche Eigenschaften wie und wann synchronisiert werden.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Synchronisieren</strong></td>
   <td>Eine manuelle Synchronisierungsanfrage, die von den Live Copy-Seiten ausgeführt wird.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Vererbung</strong></td>
   <td>Eine Live Copy-Seite/-Komponente übernimmt bei einer Synchronisierung Inhalte von der Quellseite/-komponente.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Aussetzen</strong></td>
   <td>Entfernt vorübergehend die Live-Beziehung zwischen einer Live Copy und der zugehörigen Blueprint-Seite.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Trennen</strong></td>
   <td>Entfernt dauerhaft die Live-Beziehung zwischen einer Live Copy und der zugehörigen Blueprint-Seite.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Zurücksetzen</strong></td>
   <td><p>Zurücksetzen einer Live Copy-Seite auf:</p>
    <ul>
     <li>alle abgebrochenen Vererbungsvorgänge zu entfernen und<br /> </li>
     <li>die Seite in denselben Status wie die Quellseite zurückzuversetzen.</li>
    </ul> <p>Zurücksetzen wirkt sich auf alle Änderungen aus, die Sie an den Seiteneigenschaften, am Absatzsystem und an den Komponenten vorgenommen haben.</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Flach</strong></td>
   <td>Eine Live Copy einer einzelnen Seite.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Tief</strong></td>
   <td>Eine Live Copy einer Seite zusammen mit ihren untergeordneten Seiten.</td>
   <td> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Siehe [Übersicht über die Java™-API](/help/sites-developing/extending-msm.md#overview-of-the-java-api) für die Objektnamen.

## Live Copies {#live-copies}

Eine MSM-Live Copy ist eine Kopie spezifischer Site-Inhalte, für die eine Live-Beziehung zur ursprünglichen Quelle beibehalten wird:

* Die Live Copy erbt Inhalt von ihrer Quelle.
* Die Synchronisierung führt die tatsächliche Übertragung von Inhalten durch, wenn Änderungen an der Quelle vorgenommen werden.
* Eine Live Copy kann wie folgt betrachtet werden:

   * Flach: eine einzelne Seite
   * Tief: die Seite mit ihren untergeordneten Seiten

* Synchronisierungsregeln - so genannte Rollout-Konfigurationen - bestimmen, welche Eigenschaften synchronisiert werden und wann die Synchronisierung erfolgt.

Im vorherigen Beispiel ist `/content/we-retail/language-masters/en` die globale primäre Site in englischer Sprache. Zur Wiederverwendung des Inhalts dieser Site werden MSM-Live Copies erstellt:

* Der Inhalt unter `/content/we-retail/language-masters/en` ist die Quelle.

* Der Inhalt unter `/content/we-retail/language-masters/en` wird unter die Knoten `/content/we-retail/us/en/`, `/content/we-retail/gb/en`, `/content/we-retail/ca/en` und `/content/we-retail/au/en` kopiert. Dies sind die Live Copies.

* Autoren können Seiten unten ändern `/content/we-retail/language-masters/en`.
* Nach der Auslösung synchronisiert MSM diese Änderungen mit den Live Copies.

### Live Copies – Komposition {#live-copies-composition}

>[!NOTE]
>
Die Diagramme und Beschreibungen in diesem Abschnitt stellen Momentaufnahmen der potenziellen Live Copies dar. Sie erheben keinen Anspruch auf Vollständigkeit, stellen jedoch einen Überblick bereit, um bestimmte Merkmale hervorzuheben.

Wenn Sie zum ersten Mal eine Live Copy erstellen, werden die ausgewählten Quellseiten 1:1 in der Live Copy angezeigt. Danach können neue Ressourcen (Seiten und/oder Absätze) auch direkt in der Live Copy erstellt werden. Daher ist es nützlich, sich dieser Varianten bewusst zu sein und zu erfahren, wie sie sich auf die Synchronisierung auswirken. Mögliche Kompositionen umfassen:

* [Live Copy mit Live Copy-fremden Seiten](#live-copy-with-non-live-copy-pages)
* [Verschachtelte Live Copies](#nested-live-copies)

Die grundlegende Form der Live Copy hat:

* Live Copy-Seiten, die die ausgewählten Quellseiten 1:1 widerspiegeln.
* Eine Konfigurationsdefinition.
* Eine für jede Ressource definierte Live-Beziehung:

   * Verknüpft die Live Copy-Ressource mit ihrer Blueprint/Quelle
   * Wird bei der Realisierung von Vererbung und Rollout verwendet.

* Abhängig von den Anforderungen können Änderungen [synchronisiert](/help/sites-administering/msm-livecopy.md#synchronizing-your-live-copy) werden.

![Synchronisieren](assets/chlimage_1-367.png)

#### Live Copy mit Live Copy-fremden Seiten {#live-copy-with-non-live-copy-pages}

Wenn Sie eine Live Copy in AEM erstellen, können Sie die Live Copy-Verzweigung sehen und durch sie navigieren und die normale AEM auf der Live Copy-Verzweigung verwenden. Das bedeutet, dass Sie (oder ein Prozess) Ressourcen (Seiten, Absätze oder beides) innerhalb des Live Copy-Zweigs erstellen können. Zum Beispiel: `myCanadaOnlyProduct`.

* Solche Ressourcen verfügen über keine Live-Beziehung zu Quell-/Blueprint-Seiten und werden nicht synchronisiert.
* Es können Szenarien auftreten, die das MSM als Sonderfälle behandelt. Ein Beispiel hierfür wäre, wenn Sie (oder ein Prozess) eine Seite mit der gleichen Position und dem gleichen Namen sowohl in der Quelle/Blueprint als auch in den Live Copy-Zweigen erstellen. Informationen zu solchen Situationen finden Sie unter [MSM-Rollout-Konflikte](/help/sites-administering/msm-rollout-conflicts.md) für weitere Informationen.

![Rollout-Konflikte](assets/chlimage_1-368.png)

#### Verschachtelte Live Copies {#nested-live-copies}

Wenn Sie (oder einen Prozess) eine [Seite in einer vorhandenen Live Copy](#live-copy-with-non-live-copy-pages), kann diese neue Seite auch als Live Copy eines anderen Blueprints eingerichtet werden. Dies wird als verschachtelte Live Copy bezeichnet. Hier wird das Verhalten der zweiten (inneren) Live Copy durch die zweite (äußere) Live Copy auf folgende Weise beeinflusst:

* Ein tiefes Rollout, das für die Live Copy der obersten Ebene ausgelöst wurde, kann in einer verschachtelten Live Copy fortgeführt werden (zum Beispiel bei übereinstimmendem Auslöser).
* Alle Verknüpfungen zwischen den Quellen werden in den Live Copies neu geschrieben.

  Beispielsweise werden Links vom zweiten zum ersten Blueprint als Links von der verschachtelten/zweiten Live Copy zur ersten Live Copy neu geschrieben.

![Relationen zwischen Quellen](assets/chlimage_1-369.png)

>[!NOTE]
>
Wenn Sie eine Seite innerhalb des Live Copy-Zweigs verschieben/umbenennen, wird dies (intern) als verschachtelte Live Copy behandelt, damit AEM die Beziehungen verfolgen können.

#### Gestapelte Live Copies {#stacked-live-copies}

Eine Live Copy wird als gestapelte Live Copy bezeichnet, wenn sie als untergeordnetes Element einer flachen Live Copy erstellt wird. Sie verhält sich wie ein [Verschachtelte Live Copy](#nested-live-copies).

### Quell-, Blueprints- und Blueprint-Konfigurationen {#source-blueprints-and-blueprint-configurations}

Jede Seite oder jeder Zweig von Seiten kann als Quelle einer Live Copy verwendet werden.

Mit MSM können Sie jedoch auch eine Blueprint-Konfiguration definieren, die einen Quellpfad angibt. Eine Blueprint-Konfiguration hat die folgenden Vorteile:

* Der Autor kann für eine Blueprint die Option **Rollout** verwenden und so (explizit) Änderungen an Live Copies pushen, die von dieser Blueprint erben.
* Der Autor kann **Website erstellen** nutzen, wodurch der Benutzer einfach Sprachen auswählen und die Struktur der Live Copy konfigurieren kann;
* Sie definiert eine standardmäßige Rollout-Konfiguration für Live Copies, die über eine Beziehung mit der Blueprint verfügen.

Die Quelle für eine Live Copy kann entweder normale Seiten oder Seiten sein, die von einer Blueprint-Konfiguration erfasst werden. Beide sind gültige Anwendungsfälle.

Die Quelle bildet die Blueprint für die Live Copy. Die Blueprint wird durch eine der folgenden Maßnahmen definiert:

* [Erstellen einer Blueprint-Konfiguration](/help/sites-administering/msm-livecopy.md#creating-a-blueprint-configuration)

  Die Konfiguration definiert (vorab) die zur Erstellung der Live Copy zu verwendenden Seiten.

* [Erstellen von Live Copies einer Seite](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page)

  Die zum Erstellen der Live Copy (der Quellseiten) verwendeten Seiten sind Blueprint-Seiten.

  Die Quellseite kann von einer Blueprint-Konfiguration referenziert werden oder nicht.

### Rollout und Synchronisieren {#rollout-and-synchronize}

Ein Rollout ist die zentrale MSM-Aktion, die Live Copies mit ihrer Quelle synchronisiert. Sie können Rollouts manuell ausführen oder sie werden automatisch durchgeführt:

* Es kann eine [Rollout-Konfiguration](#rollout-configurations) definiert werden, sodass spezifische [Ereignisse](/help/sites-administering/msm-sync.md#rollout-triggers) eine automatische Ausführung eines Rollouts bewirken.
* Bei der Erstellung einer Blueprint-Seite können Sie die [Rollout](/help/sites-administering/msm-livecopy.md#rolling-out-a-blueprint) -Befehl, um Änderungen an die Live Copy zu übertragen.

  **Der Befehl Rollout** ist auf einer Blueprint-Seite verfügbar, die von einer Blueprint-Konfiguration referenziert wird.

  ![Rollout](assets/chlimage_1-370.png)

* Beim Bearbeiten einer Live Copy-Seite können Sie die [Synchronisieren](/help/sites-administering/msm-livecopy.md#synchronizing-a-live-copy) -Befehl, um Änderungen von der Quelle an die Live Copy zu ziehen.

  Die **Synchronisieren** -Befehl ist immer auf der Live Copy-Seite verfügbar (unabhängig davon, ob die Quell-/Blueprint-Seite durch eine Blueprint-Konfiguration abgedeckt ist).

  ![Synchronisieren](assets/chlimage_1-371.png)

### Rollout-Konfigurationen {#rollout-configurations}

Eine Rollout-Konfiguration definiert, wann und wie eine Live Copy mit dem Quellinhalt synchronisiert wird. Eine Rollout-Konfiguration besteht aus einem Trigger und einer oder mehreren Synchronisierungsaktionen:

* **Auslöser**

  Ein Trigger ist ein Ereignis, das die Synchronisierung der Live-Aktion verursacht, z. B. die Aktivierung einer Quellseite. MSM definiert die Auslöser, die Sie verwenden können.

* **Synchronisierungsaktionen**

  Wird an der Live Copy ausgeführt, um sie mit der Quelle zu synchronisieren. Beispielaktionen sind das Kopieren von Inhalten, das Sortieren von untergeordneten Knoten und das Aktivieren der Live Copy-Seite. MSM bietet mehrere Synchronisierungsaktionen.

  >[!NOTE]
  >
  Sie können benutzerdefinierte Aktionen für Ihre Instanz mithilfe der Java™-API erstellen.

Rollout-Konfigurationen können wiederverwendet werden, sodass mehrere Live Copies dieselbe Rollout-Konfiguration verwenden können. Mehrere [Rollout-Konfigurationen](/help/sites-administering/msm-sync.md#installed-rollout-configurations) sind in einer Standardinstallation enthalten.

### Rollout-Konflikte {#rollout-conflicts}

Rollouts können kompliziert werden, insbesondere wenn Autoren Inhalte sowohl in der Quelle als auch in der Live Copy bearbeiten. Daher ist es nützlich, sich darüber im Klaren zu sein, wie AEM mit allen [Konflikte, die während des Rollouts auftreten können](/help/sites-administering/msm-rollout-conflicts.md).

### Aussetzen und Abbrechen der Vererbung und Synchronisierung {#suspending-and-cancelling-inheritance-and-synchronization}

Jede Seite und Komponente in einer Live Copy wird über eine Live-Beziehung mit ihrer Quellseite und Komponente verknüpft. Die Live-Beziehung konfiguriert die Synchronisierung von Live Copy-Inhalt aus der Quelle.

Sie können **Aussetzen** die Live Copy-Vererbung für eine Live Copy-Seite, damit Sie Seiteneigenschaften und -komponenten ändern können. Wenn Sie die Vererbung aussetzen, werden die Seiteneigenschaften und Komponenten nicht mehr mit der Quelle synchronisiert.

Bei der Bearbeitung einer einzelnen Seite können Autoren für eine Komponente die **Vererbung abbrechen**. Wenn die Vererbung abgebrochen wird, wird die Live-Beziehung ausgesetzt und die Synchronisierung für diese Komponente erfolgt nicht. Das Abbrechen der Vererbung und Synchronisierung ist nützlich, wenn Unterabschnitte des Inhalts angepasst werden müssen.

### Trennen von Live Copies {#detaching-a-live-copy}

Sie können auch [eine Live Copy von ihrer Blueprint trennen](/help/sites-administering/msm-livecopy.md#detaching-a-live-copy), um alle Verbindungen zu entfernen.

>[!CAUTION]
>
Die Trennung ist dauerhaft und kann nicht rückgängig gemacht werden.

Durch das Trennen wird die Live-Beziehung zwischen einer Live Copy und ihrer Blueprint-Seite dauerhaft entfernt. Alle MSM-bezogenen Eigenschaften werden aus der Live Copy entfernt, und die Live Copy-Seiten werden zu einer eigenständigen Kopie.

>[!NOTE]
>
Die vollständigen Details, einschließlich der damit verbundenen Auswirkungen auf Unterseiten und übergeordnete Seiten, finden Sie unter [Trennen von Live Copies](/help/sites-administering/msm-livecopy.md#detaching-a-live-copy).

## Standardschritte zur Verwendung von MSM {#standard-steps-for-using-msm}

Die folgenden Schritte beschreiben die standardmäßige Vorgehensweise für die Verwendung von MSM zur Wiederverwendung von Inhalten und zur Synchronisierung von Änderungen an den Live Copies.

1. Entwickeln Sie die Inhalte der Quellseite.
1. Legen Sie die zu verwendende Rollout-Konfiguration fest.

   1. MSM [installiert mehrere Rollout-Konfigurationen](/help/sites-administering/msm-sync.md#installed-rollout-configurations) die verschiedenen Anwendungsfällen entsprechen können.
   1. Optional können Sie [Erstellen einer Rollout-Konfiguration](/help/sites-administering/msm-sync.md#creating-a-rollout-configuration) falls erforderlich.

1. Bestimmen, wo Sie [Festlegen der zu verwendenden Rollout-Konfigurationen](/help/sites-administering/msm-sync.md#specifying-the-rollout-configurations-to-use) und konfigurieren Sie sie nach Bedarf.
1. Falls erforderlich, [Erstellen einer Blueprint-Konfiguration](/help/sites-administering/msm-livecopy.md#creating-a-blueprint-configuration) , der den Quellinhalt der Live Copy angibt.
1. [Erstellen Sie eine Live Copy](/help/sites-administering/msm-livecopy.md#creating-a-live-copy).
1. Ändern Sie den Quellinhalt nach Bedarf. Verwenden Sie den normalen Prozess zur Inhaltsüberprüfung und -genehmigung, den Ihre Organisation eingerichtet hat.
1. Führen Sie ein [Rollout](/help/sites-administering/msm-livecopy.md#rolling-out-a-blueprint) der Blueprint durch oder [synchronisieren Sie die Live Copy](/help/sites-administering/msm-livecopy.md#synchronizing-a-live-copy) mit den Änderungen.

## Anpassen von MSM {#customizing-msm}

MSM stellt Tools bereit, damit Ihre Implementierung sich an die außergewöhnlichen Komplexitäten anpasst, die bei der Freigabe von Inhalten auftreten können:

* **Benutzerdefinierte Rollout-Konfigurationen**
  [Erstellen Sie eine Rollout-Konfiguration](/help/sites-administering/msm-sync.md#creating-a-rollout-configuration), wenn die installierten Rollout-Konfigurationen Ihre Anforderungen nicht erfüllen. Sie können jeden verfügbaren Rollout-Auslöser und jede verfügbare Synchronisierungsaktion verwenden.

* **Benutzerdefinierte Synchronisierungsaktionen**
  Wenn die installierten Aktionen Ihre spezifischen Anwendungsanforderungen nicht erfüllen, können Sie [eine Synchronisierungsaktion erstellen](/help/sites-developing/extending-msm.md#creating-a-new-synchronization-action). MSM bietet eine Java™-API zum Erstellen benutzerdefinierter Synchronisierungsaktionen.

## Best Practices {#best-practices}

Die Seite [Best Practices für MSM](/help/sites-administering/msm-best-practices.md) enthält wichtige Informationen zur Implementierung.
