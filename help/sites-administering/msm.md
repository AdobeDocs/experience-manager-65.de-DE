---
title: '„Wiederverwenden von Inhalten: Multi Site Manager und Live Copy“'
seo-title: "Reusing Content: Multi Site Manager and Live Copy"
description: Erfahren Sie mehr über die Wiederverwendung von Inhalten mit Live Copies und dem Multi Site Manager.
seo-description: Learn about reusing content with Live Copies and the Multi Site Manager.
uuid: 9f955226-8fc9-4357-b90c-c6896b0dc4b4
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
discoiquuid: c21debc3-ecf4-4aa9-ab5a-18ddd5cf2fff
exl-id: 1e839845-fb5c-4200-8ec5-6ff744a96943
source-git-commit: 785d4897263bfeae6a0cd235abca3c96f2231392
workflow-type: tm+mt
source-wordcount: '2667'
ht-degree: 60%

---

# Wiederverwenden von Inhalten: Multi Site Manager und Live Copy{#reusing-content-multi-site-manager-and-live-copy}

Mit Multi Site Manager (MSM) können Sie denselben Site-Inhalt an mehreren Orten verwenden. MSM verwendet seine Live Copy-Funktion, um Folgendes zu erreichen:

* Mit MSM können Sie:

   * Inhalte einmalig erstellen und diese
   * in andere Bereiche derselben Site oder anderer Sites kopieren und wiederverwenden ([Live Copies](#live-copies)).

* MSM behält dann die (Live-)Beziehungen zwischen Ihren Quellinhalten und deren Live Copies bei, sodass:

   * Die Quelle und die Live Copies synchronisiert werden, wenn Sie Änderungen an den Quellinhalten vornehmen (um diese Änderungen auch auf die Live Copies anzuwenden).
   * Sie Anpassungen am Inhalt der Live Copies vornehmen können, indem Sie die Live-Beziehung zu einzelnen Unterseiten und/oder Komponenten trennen. Auf diese Weise werden Änderungen an der Quelle nicht mehr auf die Live Copy angewendet.

Diese und die folgenden Seiten behandeln die zugehörigen Probleme:

* [Erstellen und Synchronisieren von Live Copies](/help/sites-administering/msm-livecopy.md)
* [Konsole „Live Copy-Übersicht“](/help/sites-administering/msm-livecopy-overview.md)
* [Konfigurieren der Synchronisierung von Live Copies](/help/sites-administering/msm-sync.md)
* [MSM-Rollout-Konflikte](/help/sites-administering/msm-rollout-conflicts.md)
* [Best Practices für MSM](/help/sites-administering/msm-best-practices.md)

## Mögliche Szenarien {#possible-scenarios}

Es gibt viele Nutzungsszenarios für MSM und Live Copies. Einige der Szenarios umfassen Folgendes:

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

  Die Hauptverwaltung kann die zentralen Informationen bereitstellen, während die regionalen Stellen lokale Informationen wie Kontaktdaten, Öffnungszeiten und Veranstaltungen hinzufügen können.

  ```xml
  /content
      |- head-office-Berlin
      |- branch-Hamburg
      |- branch-Stuttgart
      |- branch-Munich
      |- branch-Frankfurt
  ```

* **Mehrere Versionen**

  Oder Sie können MSM verwenden, um Versionen einer bestimmten Unterverzweigung zu erstellen, z. B. eine Support-Unterseite mit Details zu den verschiedenen Versionen eines bestimmten Produkts, auf der die Basisinformationen konstant bleiben und nur die aktualisierten Funktionen geändert werden müssen:

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
  >Bei einem solchen Szenario stellt sich immer die Frage, ob eine direkte Kopie erstellt oder ob Live Copies verwendet werden sollen:
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

   * Mit MSM können Sie mehrere Websites verwalten, die gemeinsame Inhalte haben. Beispielsweise werden Websites häufig für internationale Zielgruppen bereitgestellt, sodass der Großteil der Inhalte in allen Ländern verwendet wird und nur eine Untergruppe der Inhalte für jedes Land bereitgestellt wird. MSM ermöglicht Ihnen die [Erstellung von Live Copies, die automatisch eine oder mehrere Websites basierend auf Ihrer Quell-Site aktualisieren](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration). Dies hilft Ihnen auch dabei, eine gemeinsame Basisstruktur zu erzwingen, die gemeinsamen Inhalte auf mehreren Sites zu nutzen, ein gemeinsames Erscheinungsbild zu erreichen und die Maßnahmen auf die Verwaltung der Inhalte zu konzentrieren, die sich auf den verschiedenen Sites tatsächlich unterscheiden.
   * Für die Angabe der Quelle ist eine vordefinierte Blueprint-Konfiguration erforderlich.
   * Erstellt eine Live Copy der (vordefinierten) Quelle.
   * Stellt dem Benutzer die **Rollout** Schaltfläche.

* **Erstellen einer Live Copy** (**Sites**)

   * MSM ermöglicht Ihnen Folgendes: [eine Ad-hoc-Live Copy (einmalig) einer einzelnen Seite oder Unterverzweigung einer Website erstellen](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page); zum Beispiel das Duplizieren einer Unterverzweigung, um Informationen über eine neue/aktualisierte Version eines Produkts bereitzustellen.
   * Erstellt eine Ad-hoc-Live Copy (keine Blueprint-Konfiguration erforderlich).
   * Kann verwendet werden, um (sofort) eine Live Copy einer beliebigen Seite/Verzweigung zu erstellen.
   * Erfordert die Option **Synchronisieren** (die **Rollout**-Schaltfläche wird nicht bereitgestellt).

* **Eigenschaften anzeigen** (**Sites**)

   * Bei Bedarf hilft Ihnen diese Option bei der [Überwachung Ihrer Live Copy](/help/sites-administering/msm-livecopy.md#monitoring-your-live-copy) durch Bereitstellung von Informationen zur zugehörigen **Live Copy** oder zur **Blueprint**.

* **Verweise** (**Sites**)

   * Die Leiste [Verweise](/help/sites-authoring/basic-handling.md#references) stellt Ihnen Informationen zu den **Live Copies** sowie den Zugriff auf die entsprechenden Aktionen bereit.

* **Live Copy-Übersicht** (**Sites**)

   * Diese Konsole ermöglicht Ihnen die [Ansicht und Verwaltung Ihrer Blueprint und deren Live Copies](/help/sites-administering/msm-livecopy-overview.md).

* **Blueprints** (**Tools** – **Sites**)

   * Diese Konsole ermöglicht Ihnen die [Erstellung und Verwaltung Ihrer Blueprint-Konfigurationen](/help/sites-administering/msm-livecopy.md#creating-a-blueprint-configuration).

>[!NOTE]
>
>Aspekte der MSM-Funktionalität werden in mehreren anderen AEM-Funktionen verwendet (z. B. Launches, Catalog). in diesen Fällen wird die Live Copy von dieser Funktion verwaltet.

### Verwendete Begriffe {#terms-used}

Als Einführung bietet die folgende Tabelle einen Überblick über die wichtigsten Begriffe, die mit MSM verwendet werden. Diese werden in den folgenden Abschnitten und Seiten ausführlicher behandelt:

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
   <td>Effektive Definition der Vererbung für eine bestimmte Ressource, d. h. die Verbindung(en) zwischen der Quelle und den Live Copies.<br /> </td>
   <td>Stellt sicher, dass Änderungen an der Quelle mit der Live Copy synchronisiert werden können.</td>
  </tr>
  <tr>
   <td><strong>Blueprint</strong></td>
   <td>Synonym für Quelle.</td>
   <td>Kann durch eine Blueprint-Konfiguration definiert werden.</td>
  </tr>
  <tr>
   <td><strong>Blueprint-Konfiguration</strong></td>
   <td>Vordefinierte Konfiguration zur Angabe eines Quellpfads.</td>
   <td>Der Rollout-Befehl wird beim Verweis auf eine Blueprint-Seite in einer Blueprint-Konfiguration zur Verfügung gestellt.</td>
  </tr>
  <tr>
   <td><strong>Synchronisierung</strong></td>
   <td>Der allgemeine Begriff für die Synchronisierung von Inhalten zwischen der Quelle und den Live Copies (sowohl durch <strong>Rollout</strong> als auch <strong>Synchronisieren</strong>).</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Rollout</strong><br /> </td>
   <td>Synchronisiert von der Quelle zur Live Copy.<br /> Kann von einem Autor (auf einer Blueprint-Seite) oder von einem Systemereignis (wie durch die Rollout-Konfiguration definiert) ausgelöst werden.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Rollout-Konfiguration</strong></td>
   <td>Regeln, die bestimmen, welche Eigenschaften wie und wann synchronisiert werden.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Synchronisieren</strong></td>
   <td>Eine manuelle Anfrage einer Synchronisierung, die über die Live Copy-Seiten erfolgt.</td>
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
    </ul> <p>Eine Rücksetzung wirkt sich auf alle von Ihnen durchgeführten Änderungen an den Seiteneigenschaften, am Absatzsystem und an den Komponenten aus.</p> </td>
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
>Unter [Überblick über die Java-API](/help/sites-developing/extending-msm.md#overview-of-the-java-api) finden Sie die Objektnamen.

## Live Copies {#live-copies}

Eine MSM-Live Copy ist eine Kopie spezifischer Site-Inhalte, für die eine Live-Beziehung zur ursprünglichen Quelle beibehalten wird:

* Die Live Copy erbt Inhalt von ihrer Quelle.
* Die Synchronisierung führt die tatsächliche Übertragung von Inhalten durch, wenn Änderungen an der Quelle vorgenommen werden.
* Eine Live Copy kann wie folgt betrachtet werden:

   * Flach: eine einzelne Seite
   * Tief: die Seite mit ihren untergeordneten Seiten

* Synchronisierungsregeln, die als Rollout-Konfigurationen bezeichnet werden, bestimmen, welche Eigenschaften synchronisiert werden und wann die Synchronisierung durchgeführt wird.

Im vorherigen Beispiel ist `/content/we-retail/language-masters/en` die globale primäre Site in englischer Sprache. Zur Wiederverwendung des Inhalts dieser Site werden MSM-Live Copies erstellt:

* Der Inhalt unter `/content/we-retail/language-masters/en` ist die Quelle.

* Der Inhalt unter `/content/we-retail/language-masters/en` wird unter die Knoten `/content/we-retail/us/en/`, `/content/we-retail/gb/en`, `/content/we-retail/ca/en` und `/content/we-retail/au/en` kopiert. Dies sind die Live Copies.

* Autoren nehmen an Seiten unter `/content/we-retail/language-masters/en` Änderungen vor.
* Nach der Auslösung synchronisiert MSM diese Änderungen mit den Live Copies.

### Live Copies – Komposition {#live-copies-composition}

>[!NOTE]
>
>Die Diagramme und Beschreibungen in diesem Abschnitt stellen Momentaufnahmen der potenziellen Live Copies dar. Sie erheben keinen Anspruch auf Vollständigkeit, stellen jedoch einen Überblick bereit, um bestimmte Merkmale hervorzuheben.

Wenn Sie zum ersten Mal eine Live Copy erstellen, werden die ausgewählten Quellseiten 1:1 in der Live Copy angezeigt. Danach können neue Ressourcen (Seiten und/oder Absätze) auch direkt in der Live Copy erstellt werden. Daher ist es nützlich, sich dieser Varianten bewusst zu sein und zu erfahren, wie sie sich auf die Synchronisierung auswirken. Mögliche Kompositionen umfassen:

* [Live Copy mit Live Copy-fremden Seiten](#live-copy-with-non-live-copy-pages)
* [Verschachtelte Live Copies](#nested-live-copies)

Die grundlegende Form der Live Copy hat:

* Live Copy-Seiten, die die ausgewählten Quellseiten 1:1 widerspiegeln.
* Eine Konfigurationsdefinition.
* Eine für jede Ressource definierte Live-Beziehung:

   * Verknüpft die Live Copy-Ressource mit ihrer Blueprint/Quelle
   * Wird bei der Umsetzung von Vererbung und Rollout verwendet.

* Abhängig von den Anforderungen können Änderungen [synchronisiert](/help/sites-administering/msm-livecopy.md#synchronizing-your-live-copy) werden.

![Synchronisieren](assets/chlimage_1-367.png)

#### Live Copy mit Live Copy-fremden Seiten {#live-copy-with-non-live-copy-pages}

Wenn Sie eine Live Copy in AEM erstellen, können Sie die Live Copy-Verzweigung sehen und durch sie navigieren und die normale AEM im Live Copy-Zweig verwenden. Dies bedeutet, dass Sie (oder ein Prozess) neue Ressourcen (Seiten und/oder Absätze) innerhalb der Live Copy-Verzweigung (z. B. `myCanadaOnlyProduct`) erstellen können.

* Solche Ressourcen verfügen über keine Live-Beziehung zu Quell-/Blueprint-Seiten und werden nicht synchronisiert.
* Es können Szenarien auftreten, die MSM als Spezialfälle behandelt. Ein Beispiel hierfür wäre, wenn Sie (oder ein Prozess) eine Seite mit der gleichen Position und dem gleichen Namen sowohl in der Quelle/Blueprint als auch in den Live Copy-Zweigen erstellen. Bei solchen Situationen finden Sie unter [MSM-Rollout-Konflikte](/help/sites-administering/msm-rollout-conflicts.md) weitere Informationen.

![Rollout-Konflikte](assets/chlimage_1-368.png)

#### Verschachtelte Live Copies {#nested-live-copies}

Wenn Sie (oder ein Prozess) eine [neue Seite innerhalb einer vorhandenen Live Copy](#live-copy-with-non-live-copy-pages) erstellen, kann diese neue Seite auch als Live Copy einer anderen Blueprint eingerichtet werden. Dies wird als verschachtelte Live Copy bezeichnet. Hier wird das Verhalten der zweiten (inneren) Live Copy durch die zweite (äußere) Live Copy auf folgende Weise beeinflusst:

* Ein tiefes Rollout, das für die Live Copy der obersten Ebene ausgelöst wurde, kann in einer verschachtelten Live Copy fortgeführt werden (zum Beispiel bei übereinstimmendem Auslöser).
* Alle Links zwischen den Quellen werden innerhalb der Live Copies neu geschrieben.

  Es werden zum Beispiel Links vom zweiten auf die erste Blueprint neu als Links von der zweiten/verschachtelten Live Copy auf die erste Live Copy geschrieben.

![Relationen zwischen Quellen](assets/chlimage_1-369.png)

>[!NOTE]
>
>Wenn Sie eine Seite innerhalb des Live Copy-Zweigs verschieben/umbenennen, wird dies (intern) als verschachtelte Live Copy behandelt, damit AEM die Beziehungen verfolgen können.

#### Gestapelte Live Copies {#stacked-live-copies}

Eine Live Copy wird als gestapelte Live Copy bezeichnet, wenn sie als untergeordnetes Element einer flachen Live Copy erstellt wird. Sie verhält sich wie ein [Verschachtelte Live Copy](#nested-live-copies).

### Quelle, Blueprints und Blueprint-Konfigurationen {#source-blueprints-and-blueprint-configurations}

Jede Seite oder jeder Zweig von Seiten kann als Quelle einer Live Copy verwendet werden.

MSM ermöglicht Ihnen allerdings die Definition einer Blueprint-Konfiguration, die einen Quellpfad angibt. Eine Blueprint-Konfiguration hat die folgenden Vorteile:

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

* Wenn Sie eine Live Copy-Seite erstellen, können Sie die [Synchronisieren](/help/sites-administering/msm-livecopy.md#synchronizing-a-live-copy) -Befehl, um Änderungen von der Quelle an die Live Copy zu ziehen.

  Die **Synchronisieren** -Befehl ist immer auf der Live Copy-Seite verfügbar (unabhängig davon, ob die Quell-/Blueprint-Seite durch eine Blueprint-Konfiguration abgedeckt ist).

  ![Synchronisieren](assets/chlimage_1-371.png)

### Rollout-Konfigurationen {#rollout-configurations}

Eine Rollout-Konfiguration definiert, wann und wie eine Live Copy mit dem Quellinhalt synchronisiert wird. Eine Rollout-Konfiguration besteht aus einem Trigger und einer oder mehreren Synchronisierungsaktionen:

* **Auslöser**

  Ein Trigger ist ein Ereignis, das die Synchronisierung der Live-Aktion verursacht, z. B. die Aktivierung einer Quellseite. MSM definiert die Auslöser, die Sie verwenden können.

* **Synchronisierungsaktionen**

  werden an der Live Copy ausgeführt, um sie mit der Quelle zu synchronisieren. Beispielaktionen sind das Kopieren von Inhalten, das Sortieren von untergeordneten Knoten und das Aktivieren der Live Copy-Seite. MSM bietet eine Reihe von Synchronisierungsaktionen.

  >[!NOTE]
  >
  >Mithilfe der Java-API erstellen Sie benutzerdefinierte Aktionen für Ihre Instanz.

Rollout-Konfigurationen können wiederverwendet werden, sodass mehrere Live Copies dieselbe Rollout-Konfiguration verwenden können. Mehrere [Rollout-Konfigurationen](/help/sites-administering/msm-sync.md#installed-rollout-configurations) sind in einer Standardinstallation enthalten.

### Rollout-Konflikte {#rollout-conflicts}

Rollouts können kompliziert werden, insbesondere wenn Autoren Inhalte sowohl in der Quelle als auch in der Live Copy bearbeiten. Daher ist es nützlich, sich darüber im Klaren zu sein, wie AEM mit allen [Konflikte, die während des Rollouts auftreten können](/help/sites-administering/msm-rollout-conflicts.md).

### Aussetzen und Abbrechen der Vererbung und Synchronisierung {#suspending-and-cancelling-inheritance-and-synchronization}

Jede Seite und Komponente in einer Live Copy ist über eine Live-Beziehung mit ihrer Quellseite und Komponente verknüpft. Die Live-Beziehung konfiguriert die Synchronisierung von Live Copy-Inhalt aus der Quelle.

Sie können **Aussetzen** die Live Copy-Vererbung für eine Live Copy-Seite, damit Sie Seiteneigenschaften und -komponenten ändern können. Wenn Sie die Vererbung aussetzen, werden die Seiteneigenschaften und Komponenten nicht mehr mit der Quelle synchronisiert.

Bei der Bearbeitung einer einzelnen Seite können Autoren für eine Komponente die **Vererbung abbrechen**. Wird die Vererbung abgebrochen, wird die Live-Beziehung unterbrochen und die Synchronisierung tritt bei dieser Komponente nicht auf. Das Abbrechen der Vererbung und Synchronisierung ist nützlich, wenn Unterabschnitte des Inhalts angepasst werden müssen.

### Trennen von Live Copies {#detaching-a-live-copy}

Sie können auch [eine Live Copy von ihrer Blueprint trennen](/help/sites-administering/msm-livecopy.md#detaching-a-live-copy), um alle Verbindungen zu entfernen.

>[!CAUTION]
>
>Die Trennung ist dauerhaft und kann nicht rückgängig gemacht werden.

Durch das Trennen wird die Live-Beziehung zwischen einer Live Copy und ihrer Blueprint-Seite dauerhaft entfernt. Alle MSM-bezogenen Eigenschaften werden aus der Live Copy entfernt, und die Live Copy-Seiten werden zu einer eigenständigen Kopie.

>[!NOTE]
>
>Die vollständigen Details, einschließlich der damit verbundenen Auswirkungen auf Unterseiten und übergeordnete Seiten, finden Sie unter [Trennen von Live Copies](/help/sites-administering/msm-livecopy.md#detaching-a-live-copy).

## Standardschritte zur Verwendung von MSM {#standard-steps-for-using-msm}

Die folgenden Schritte beschreiben die standardmäßige Vorgehensweise für die Verwendung von MSM zur Wiederverwendung von Inhalten und zur Synchronisierung von Änderungen an den Live Copies.

1. Entwickeln Sie die Inhalte der Quellseite.
1. Legen Sie die zu verwendende Rollout-Konfiguration fest.

   1. MSM [installiert mehrere Rollout-Konfigurationen](/help/sites-administering/msm-sync.md#installed-rollout-configurations), die sich für eine Reihe von Anwendungsfällen eignen.
   1. Optional können Sie [Erstellen einer Rollout-Konfiguration](/help/sites-administering/msm-sync.md#creating-a-rollout-configuration) falls erforderlich.

1. Stellen Sie fest, wo Sie [Festlegen der zu verwendenden Rollout-Konfigurationen](/help/sites-administering/msm-sync.md#specifying-the-rollout-configurations-to-use) und konfigurieren Sie sie nach Bedarf.
1. [Erstellen Sie gegebenenfalls eine Blueprint-Konfiguration](/help/sites-administering/msm-livecopy.md#creating-a-blueprint-configuration), die den Quellinhalt der Live Copy identifiziert.
1. [Erstellen Sie eine Live Copy](/help/sites-administering/msm-livecopy.md#creating-a-live-copy).
1. Nehmen Sie bei Bedarf Änderungen am Quellinhalt vor. Sie sollten den normalen Prozess der Inhaltsüberprüfung und -genehmigung anwenden, den Ihr Unternehmen eingerichtet hat.
1. Führen Sie ein [Rollout](/help/sites-administering/msm-livecopy.md#rolling-out-a-blueprint) der Blueprint durch oder [synchronisieren Sie die Live Copy](/help/sites-administering/msm-livecopy.md#synchronizing-a-live-copy) mit den Änderungen.

## Anpassen von MSM {#customizing-msm}

MSM stellt Tools bereit, damit Ihre Implementierung sich an die außergewöhnlichen Komplexitäten anpasst, die bei der Freigabe von Inhalten auftreten können:

* **Benutzerdefinierte Rollout-Konfigurationen**
  [Erstellen Sie eine Rollout-Konfiguration](/help/sites-administering/msm-sync.md#creating-a-rollout-configuration), wenn die installierten Rollout-Konfigurationen Ihre Anforderungen nicht erfüllen. Sie können jeden verfügbaren Rollout-Auslöser und jede verfügbare Synchronisierungsaktion verwenden.

* **Benutzerdefinierte Synchronisierungsaktionen**
  Wenn die installierten Aktionen Ihre spezifischen Anwendungsanforderungen nicht erfüllen, können Sie [eine Synchronisierungsaktion erstellen](/help/sites-developing/extending-msm.md#creating-a-new-synchronization-action). MSM bietet eine Java-API zum Erstellen benutzerdefinierter Synchronisierungsaktionen.

## Best Practices {#best-practices}

Die Seite [Best Practices für MSM](/help/sites-administering/msm-best-practices.md) enthält wichtige Informationen zur Implementierung.
