---
title: Verwaltung von Benutzern, Gruppen und Zugriffsrechten
seo-title: User, Group and Access Rights Administration
description: Erfahren Sie mehr über die Verwaltung von Benutzern, Gruppen und Zugriffsrechten in AEM.
seo-description: Learn about user, group and access rights administration in AEM.
uuid: 26d7bb25-5a38-43c6-bd6a-9ddba582c60f
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: 66674e47-d19f-418f-857f-d91cf8660b6d
docset: aem65
exl-id: 5808b8f9-9b37-4970-b5c1-4d33404d3a8b
feature: Security
source-git-commit: 30327950779337ce869b6ca376120bc09826be21
workflow-type: tm+mt
source-wordcount: '3120'
ht-degree: 58%

---

# Verwaltung von Benutzern, Gruppen und Zugriffsrechten{#user-group-and-access-rights-administration}

Die Aktivierung des Zugriffs auf ein CRX-Repository umfasst verschiedene Themen:

* [Zugriffsberechtigungen](#how-access-rights-are-evaluated) - die Konzepte, wie sie definiert und ausgewertet werden
* [Benutzerverwaltung](#user-administration) - Verwaltung der einzelnen Konten, die für den Zugriff verwendet werden
* [Gruppenverwaltung](#group-administration): vereinfacht die Benutzerverwaltung durch die Bildung von Gruppen
* [Zugriffsrechteverwaltung](#access-right-management): Definition von Richtlinien, die steuern, wie diese Benutzer und Gruppen auf Ressourcen zugreifen können

Nachfolgend sind die grundlegenden Elemente aufgeführt:

**Benutzerkonten**: CRX authentifiziert den Zugriff durch Identifizieren und Verifizieren eines Benutzers (durch eine Person oder eine andere Anwendung) entsprechend den im Benutzerkonto gespeicherten Details.

In CRX ist jedes Benutzerkonto ein Knoten im Arbeitsbereich. Ein CRX-Benutzerkonto verfügt über die folgenden Eigenschaften:

* Es stellt einen Benutzer von CRX dar.
* Sie enthält einen Benutzernamen und ein Kennwort.
* Gilt für diesen Arbeitsbereich.
* Sie kann keine Unterbenutzer haben. Für hierarchische Zugriffsrechte sollten Sie Gruppen verwenden.

* Sie können Zugriffsberechtigungen für das Benutzerkonto angeben.

   Zur Vereinfachung der Verwaltung raten wir jedoch, (in der Mehrzahl der Fälle) Zugriffsrechte zu Gruppenkonten zuzuweisen. Bei der Zuweisung von Zugriffsrechten zu jedem einzelnen Benutzer kann die Verwaltung schnell sehr schwierig werden (Ausnahmen sind bestimmte Systembenutzer, wenn nur ein oder zwei Instanzen vorhanden sind).

**Gruppenkonten**: Gruppenkonten sind Sammlungen von Benutzern und/oder anderen Gruppen. Diese dienen zur Vereinfachung der Verwaltung, da eine Änderung der einer Gruppe zugewiesenen Zugriffsrechte automatisch auf alle Benutzer dieser Gruppe angewendet wird. Ein Benutzer muss keiner Gruppe angehören, gehört aber oft zu mehreren.

In CRX hat eine Gruppe die folgenden Eigenschaften:

* Es stellt eine Gruppe von Benutzern mit gemeinsamen Zugriffsrechten dar. Beispielsweise Autoren oder Entwickler.
* Gilt für diesen Arbeitsbereich.
* Er kann Mitglieder haben; Hierbei kann es sich um einzelne Benutzer oder andere Gruppen handeln.
* Eine hierarchische Gruppierung kann mit Mitgliederbeziehungen erreicht werden. Sie können eine Gruppe nicht direkt unter einer anderen Gruppe im Repository platzieren.
* Sie können die Zugriffsrechte für alle Gruppenmitglieder definieren.

**Zugriffsrechte**: CRX verwendet Zugriffsrechte zur Steuerung des Zugriffs auf bestimmte Bereiche des Repositorys.

Dies erfolgt über die Zuweisung von Berechtigungen, um den Zugriff auf eine Ressource (Knoten oder Pfad) im Repository zuzulassen oder abzulehnen. Da zahlreiche Berechtigungen zugewiesen werden können, müssen sie ausgewertet werden, um festzustellen, welche Kombination für die aktuelle Anfrage relevant ist.

Mit CRX können Sie die Zugriffsberechtigungen für Benutzer- und Gruppenkonten konfigurieren. Die gleichen Grundprinzipien der Bewertung werden dann auf beide angewendet.

## Auswerten von Zugriffsrechten {#how-access-rights-are-evaluated}

>[!NOTE]
>
>CRX-Implementierungen [Zugriffskontrolle gemäß Definition in JSR-283](https://www.adobe.io/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html).
>
>Eine Standardinstallation eines CRX-Repositorys ist für die Verwendung ressourcenbasierter Zugriffssteuerungslisten konfiguriert. Dies ist eine mögliche Implementierung der Zugriffskontrolle auf JSR-283 und einer der Implementierungen, die mit Jackrabbit vorhanden sind.

### Objekte und Prinzipale {#subjects-and-principals}

CRX verwendet zwei Hauptkonzepte zur Bewertung der Zugriffsrechte:

* A **Prinzipal** ist eine Entität, die Zugriffsrechte besitzt. Zu den Prinzipalen gehören:

   * Ein Benutzerkonto
   * Ein Gruppenkonto

      Wenn ein Benutzerkonto zu einer oder mehreren Gruppen gehört, ist es auch mit jedem dieser Gruppenprinzipale verknüpft.

* Ein **Objekt** repräsentiert die Quelle einer Anfrage.

   Es dient zur Konsolidierung der für diese Anfrage relevanten Zugriffsrechte. Diese stammen von:

   * dem Benutzerprinzipal

      den Rechten, die Sie dem Benutzerkonto direkt zuweisen

   * allen mit diesem Benutzer verknüpften Gruppenprinzipalen

      sowie allen Rechten, die Sie jeder der Gruppen zugewiesen haben, zu denen der Benutzer gehört.
   Das Ergebnis wird dann verwendet, um den Zugriff auf die angeforderte Ressource zu erlauben oder zu verweigern.

#### Kompilieren der Liste der Zugriffsrechte für ein Subjekt {#compiling-the-list-of-access-rights-for-a-subject}

In CRX hängt das Betreff von Folgendem ab:

* Benutzerprinzipal
* alle Gruppenprinzipale, die mit diesem Benutzer verknüpft sind

Die Liste der für den Betreff geltenden Zugriffsrechte wird erstellt aus:

* den Rechten, die Sie dem Benutzerkonto direkt zuweisen
* sowie allen Rechten, die Sie jeder der Gruppen zugewiesen haben, zu denen der Benutzer gehört

![chlimage_1-56](assets/chlimage_1-56.png)

>[!NOTE]
>
>* CRX berücksichtigt keine Benutzerhierarchie bei der Erstellung der Liste.
>* CRX verwendet eine Gruppenhierarchie nur, wenn Sie eine Gruppe als Mitglied einer anderen Gruppe einbeziehen. Es gibt keine automatische Vererbung von Gruppenberechtigungen.
>* Die Reihenfolge, in der Sie die Gruppen angeben, wirkt sich nicht auf die Zugriffsberechtigungen aus.
>


### Auflösen von Anfragen- und Zugriffsrechten {#resolving-request-and-access-rights}

Wenn CRX die Anfrage verarbeitet, vergleicht es die Zugriffsanfrage des Betreffs mit der Zugriffssteuerungsliste auf dem Repository-Knoten:

Wenn also Linda eine Aktualisierung des Knotens `/features` in der folgenden Repository-Struktur anfordert:

![chlimage_1-57](assets/chlimage_1-57.png)

### Rangfolge {#order-of-precedence}

Zugriffsberechtigungen in CRX werden wie folgt bewertet:

* Benutzerprinzipale haben immer Vorrang vor Gruppenprinzipalen, unabhängig von:

   * ihrer Reihenfolge in der Zugriffsteuerungsliste
   * ihre Position in der Knotenhierarchie

* Für einen bestimmten Prinzipal gibt es (höchstens) 1 Ablehnungs- und 1 Zulassungseintrag für einen bestimmten Knoten. Die Implementierung löscht immer redundante Einträge und stellt sicher, dass dieselbe Berechtigung nicht sowohl in den Zulassungs- als auch in den Ablehnungseinträgen aufgeführt wird.

>[!NOTE]
>
>Dieser Bewertungsprozess ist für die ressourcenbasierte Zugriffssteuerung einer CRX-Standardinstallation geeignet.

Nachfolgend sehen Sie zwei Beispiele, in denen der Benutzer `aUser` Mitglied der Gruppe `aGroup` ist:

```xml
   + parentNode
     + acl
       + ace: aUser - deny - write
     + childNode
       + acl
         + ace: aGroup - allow - write
       + grandChildNode
```

Im obigen Fall:

* wird dem Benutzer `aUser` keine Schreibberechtigung für den Knoten `grandChildNode` gewährt.

```xml
   + parentNode
     + acl
       + ace: aUser - deny - write
     + childNode
       + acl
         + ace: aGroup - allow - write
         + ace: aUser - deny - write
       + grandChildNode
```

In diesem Fall:

* wird dem Benutzer `aUser` keine Schreibberechtigung für den Knoten `grandChildNode` gewährt.
* Der zweite ACE-Eintrag für den Benutzer `aUser` ist redundant.

Zugriffsberechtigungen von mehreren Gruppenprinzipalen werden anhand ihrer Reihenfolge bewertet, sowohl innerhalb der Hierarchie als auch innerhalb einer einzigen Zugriffssteuerungsliste.

### Best Practices {#best-practices}

Die nachfolgende Tabelle enthält einige Empfehlungen und Best Practices:

<table>
 <tbody>
  <tr>
   <td>Empfehlung...</td>
   <td>Grund...</td>
  </tr>
  <tr>
   <td><i>Benutzergruppen</i></td>
   <td><p>Vermeiden Sie es, Zugriffsrechte Benutzer für Benutzer zuzuweisen. Dafür gibt es mehrere Gründe:</p>
    <ul>
     <li>Da es viel mehr Benutzende als Gruppen gibt, vereinfachen Gruppen die Struktur.</li>
     <li>Gruppen bieten Ihnen einen Überblick über alle Konten.</li>
     <li>Die Vererbung bei Gruppen ist einfacher.</li>
     <li>Benutzer wechseln häufiger. Gruppen sind auf Langfristigkeit ausgelegt.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><i>Positiv sein</i></td>
   <td><p>Verwenden Sie immer Anweisungen vom Typ „Zulassen“, um die Zugriffsrechte des Gruppenprinzipals anzugeben (sofern möglich). Vermeiden Sie Anweisungen vom Typ „Ablehnen“.</p> <p>Gruppenprinzipale werden der Reihenfolge nach innerhalb der Hierarchie und innerhalb einer einzelnen Zugriffssteuerungsliste bewertet.</p> </td>
  </tr>
  <tr>
   <td><i>Es einfach halten</i></td>
   <td><p>Wenn Sie bei der Konfiguration einer Neuinstallation etwas Zeit investieren und nachdenken, zahlt sich das später aus.</p> <p>Eine klare Struktur vereinfacht die fortlaufende Wartung und Verwaltung, sodass sowohl aktuelle Kollegen als auch Nachfolger die Implementierung problemlos verstehen können.</p> </td>
  </tr>
  <tr>
   <td><i>Testen</i></td>
   <td>Verwenden Sie eine Testinstallation, um zu üben und sicherzustellen, dass Sie die Beziehungen zwischen den verschiedenen Benutzern und Gruppen verstehen.</td>
  </tr>
  <tr>
   <td><i>Standardbenutzer/-gruppen</i></td>
   <td>Aktualisieren Sie die Standardbenutzer und -gruppen immer sofort nach der Installation, um Sicherheitsprobleme zu vermeiden.</td>
  </tr>
 </tbody>
</table>

## Benutzerverwaltung {#user-administration}

Für die **Benutzerverwaltung** wird ein Standard-Dialogfeld verwendet.

Sie müssen beim entsprechenden Arbeitsbereich angemeldet sein und können dann von beiden auf das Dialogfeld zugreifen:

* die **Benutzerverwaltung** Link in der Hauptkonsole von CRX
* die **Sicherheit** Menü des CRX Explorer

![chlimage_1-58](assets/chlimage_1-58.png)

**Eigenschaften**

* **Benutzer-ID**

   Kurzname für das Konto, der beim Zugriff auf CRX verwendet wird

* **Prinzipalname**

   Vollständiger Name des Kontos

* **Kennwort**

   Erforderlich, wenn mit diesem Konto auf CRX zugegriffen wird

* **ntlmhash**

    Wird automatisch jedem neuen Konto zugewiesen und bei Änderung des Kennworts aktualisiert

* Sie können neue Eigenschaften hinzufügen, indem Sie einen Namen, einen Typ und den Wert definieren. Klicken Sie für jede neue Eigenschaft auf Speichern (grünes Häkchen-Symbol).

**Gruppenmitgliedschaft**

Hier werden alle Gruppen angezeigt, die zu diesem Konto gehören. Die Spalte Übernommen zeigt Mitgliedschaften an, die durch eine Mitgliedschaft bei einer anderen Gruppe übernommen wurden.

Durch Klicken auf eine Gruppen-ID (falls verfügbar) wird die [Gruppenverwaltung](#group-administration) für diese Gruppe geöffnet.

**Darsteller**

Mit der Funktion „Stellvertretend agieren“ kann ein Benutzer im Namen eines anderen Benutzers arbeiten.

Das bedeutet, dass ein Benutzerkonto andere Konten (Benutzer oder Gruppe) angeben kann, die mit ihrem Konto arbeiten können. Anders ausgedrückt: Wenn Benutzer B stellvertretend für Benutzer A agieren darf, kann Benutzer B Aktionen unter Verwendung aller Kontodetails des Benutzers A (einschließlich ID, Name und Zugriffsrechte) ausführen.

Dadurch können die stellvertretenden Konten Aufgaben so ausführen, als ob sie das Konto verwenden würden, für das sie stellvertretend agieren. z. B. bei Abwesenheit oder kurzfristiger Lastenteilung.

Wenn ein Konto stellvertretend für ein anderes agiert, ist es sehr schwer zu sehen. Die Protokolldateien enthalten keine Informationen darüber, dass bei den Ereignissen eine Identität aufgetreten ist. Wenn also Benutzer B stellvertretend für Benutzer A agiert, sehen alle Ereignisse so aus, als ob sie von Benutzer A persönlich durchgeführt würden.

### Erstellen eines Benutzerkontos {#creating-a-user-account}

1. Öffnen Sie die **Benutzerverwaltung** angezeigt.
1. Klicken Sie auf **Benutzer erstellen**.
1. Sie können dann die Eigenschaften eingeben:

   * **Benutzer-ID** – wird als Kontoname verwendet
   * **Kennwort** – wird bei der Anmeldung benötigt
   * **Prinzipalname** – dient zur Eingabe des vollständigen Textnamens
   * **Zwischenpfad** – kann zum Erstellen einer hierarchischen Struktur verwendet werden

1. Klicken Sie auf Speichern (grünes Häkchensymbol).
1. Das Dialogfeld wird erweitert, damit Sie Folgendes tun können:

   1. Konfigurieren **Eigenschaften**.
   1. Zeigen Sie die **Gruppenmitgliedschaft** an.
   1. Definieren **Darsteller**.

>[!NOTE]
>
>Manchmal kann es zu Leistungseinbußen kommen, wenn neue Benutzer in Installationen registriert werden, die über eine hohe Anzahl von beiden verfügen:
>
>* Benutzer
>* Gruppen mit vielen Mitgliedern
>


### Aktualisieren von Benutzerkonten {#updating-a-user-account}

1. Öffnen Sie mithilfe des Dialogfelds **Benutzerverwaltung** die Listenansicht aller Konten.
1. Navigieren Sie durch die Baumstruktur.
1. Klicken Sie auf das gewünschte Konto, um es zur Bearbeitung zu öffnen.
1. Nehmen Sie eine Änderung vor und klicken Sie dann auf Speichern (grünes Häkchensymbol) für diesen Eintrag.
1. Klicken **Schließen** bis zum Ende oder **Liste...** , um zur Liste aller Benutzerkonten zurückzukehren.

### Entfernen von Benutzerkonten {#removing-a-user-account}

1. Öffnen Sie mithilfe des Dialogfelds **Benutzerverwaltung** die Listenansicht aller Konten.
1. Navigieren Sie durch die Baumstruktur.
1. Wählen Sie das gewünschte Konto aus und klicken Sie auf **Benutzer löschen**; wird das Konto sofort gelöscht.

>[!NOTE]
>
>Dadurch wird der Knoten für diesen Prinzipal aus dem Repository entfernt.
>
>Einträge mit Zugriffsrechten werden nicht entfernt. So wird die historische Integrität gesichert.

### Definieren von Eigenschaften {#defining-properties}

Sie können **Eigenschaften** für neue oder vorhandene Konten:

1. Öffnen Sie die **Benutzerverwaltung** für das entsprechende Konto.
1. Definieren Sie eine **Eigenschaft** name.
1. Wählen Sie die **Typ** aus der Dropdown-Liste aus.
1. Definieren Sie die **Wert**.
1. Klicken Sie für die neue Eigenschaft auf Speichern (grünes Klicksymbol) .

Vorhandene Eigenschaften können mit dem Papierkorbsymbol gelöscht werden.

Mit Ausnahme des Kennworts können Eigenschaften nicht bearbeitet werden. Sie müssen gelöscht und neu erstellt werden.

#### Ändern des Kennworts {#changing-the-password}

Die **Passwort** ist eine spezielle Eigenschaft, die durch Klicken auf **Kennwort ändern** Link.

Sie können das Kennwort auch in Ihr eigenes Benutzerkonto ändern, indem Sie die **Sicherheit** im CRX Explorer angezeigt.

### Definieren eines Impersonators {#defining-an-impersonator}

Sie können Identifikatoren für neue oder vorhandene Konten definieren:

1. Öffnen Sie die **Benutzerverwaltung** für das entsprechende Konto.
1. Geben Sie das Konto an, das stellvertretend für dieses Konto agieren darf.

   Sie können über die Option „Durchsuchen…“ ein bestehendes Konto auswählen.

1. Klicken Sie für die neue Eigenschaft auf Speichern (grünes Häkchensymbol) .

## Gruppenverwaltung {#group-administration}

Ein Standarddialogfeld wird verwendet für **Gruppenverwaltung**.

Sie müssen beim entsprechenden Arbeitsbereich angemeldet sein und können dann von beiden auf das Dialogfeld zugreifen:

* die **Gruppenverwaltung** Link in der Hauptkonsole von CRX
* die **Sicherheit** Menü des CRX Explorer

![chlimage_1-8](assets/chlimage_1-8.jpeg)

**Eigenschaften**

* **Gruppen-ID**

   Kurzname für das Gruppenkonto

* **Prinzipalname**

   Vollständiger Name des Gruppenkontos

* Sie können neue Eigenschaften hinzufügen, indem Sie einen Namen, einen Typ und den Wert definieren. Klicken Sie für jede neue Eigenschaft auf Speichern (grünes Häkchen-Symbol).

* **Mitglieder**

   Sie können Benutzer oder andere Gruppen als Mitglieder dieser Gruppe hinzufügen.

**Gruppenmitgliedschaft**

Hier werden alle Gruppen angezeigt, die zu diesem aktuellen Gruppenkonto gehören. Die Spalte Übernommen zeigt Mitgliedschaften an, die durch eine Mitgliedschaft bei einer anderen Gruppe übernommen wurden.

Durch Klicken auf eine Gruppen-ID wird das Dialogfeld für diese Gruppe geöffnet.

**Mitglieder**

Listet alle Konten (Benutzer und/oder Gruppen) auf, die Mitglieder der aktuellen Gruppe sind.

Die **Übernommen** gibt die Mitgliedschaft an, die infolge der Mitgliedschaft in einer anderen Gruppe übernommen wurde.

>[!NOTE]
>
>Wenn die Eigentümer-, Bearbeiter- oder Betrachterrolle einem Benutzer in einem beliebigen Asset-Ordner zugewiesen wird, wird eine neue Gruppe erstellt. Der Gruppenname ist vom Format `mac-default-<foldername>` für jeden Ordner, für den die Rollen definiert sind.

### Erstellen eines Gruppenkontos {#creating-a-group-account}

1. Öffnen Sie die **Gruppenverwaltung** angezeigt.
1. Klicken **Gruppe erstellen**.
1. Sie können dann die Eigenschaften eingeben:

   * **Prinzipalname** – dient zur Eingabe des vollständigen Textnamens
   * **Zwischenpfad** – kann zum Erstellen einer hierarchischen Struktur verwendet werden

1. Klicken Sie auf Speichern (grünes Häkchensymbol).
1. Das Dialogfeld wird erweitert, damit Sie Folgendes tun können:

   1. Konfigurieren **Eigenschaften**.
   1. Zeigen Sie die **Gruppenmitgliedschaft** an.
   1. Verwalten **Mitglieder**.

### Aktualisieren eines Gruppenkontos {#updating-a-group-account}

1. Öffnen Sie mithilfe des Dialogfelds **Gruppenverwaltung** die Listenansicht aller Konten.
1. Navigieren Sie durch die Baumstruktur.
1. Klicken Sie auf das gewünschte Konto, um es zur Bearbeitung zu öffnen.
1. Nehmen Sie eine Änderung vor und klicken Sie dann auf Speichern (grünes Häkchensymbol) für diesen Eintrag.
1. Klicken **Schließen** bis zum Ende oder **Liste...** , um zur Liste aller Gruppenkonten zurückzukehren.

### Entfernen von Gruppenkonten {#removing-a-group-account}

1. Öffnen Sie mithilfe des Dialogfelds **Gruppenverwaltung** die Listenansicht aller Konten.
1. Navigieren Sie durch die Baumstruktur.
1. Wählen Sie das gewünschte Konto aus und klicken Sie auf **Gruppe löschen**; wird das Konto sofort gelöscht.

>[!NOTE]
>
>Dadurch wird der Knoten für diesen Prinzipal aus dem Repository entfernt.
>
>Einträge mit Zugriffsrechten werden nicht entfernt. So wird die historische Integrität gesichert.

### Definieren von Eigenschaften {#defining-properties-1}

Sie können Eigenschaften für neue oder vorhandene Konten definieren:

1. Öffnen Sie die **Gruppenverwaltung** für das entsprechende Konto.
1. Definieren Sie eine **Eigenschaft** name.
1. Wählen Sie die **Typ** aus der Dropdown-Liste aus.
1. Definieren Sie die **Wert**.
1. Klicken Sie für die neue Eigenschaft auf Speichern (grünes Häkchensymbol) .

Vorhandene Eigenschaften können mit dem Papierkorbsymbol gelöscht werden.

### Mitglieder {#members}

Sie können Mitglieder zur aktuellen Gruppe hinzufügen:

1. Öffnen Sie die **Gruppenverwaltung** für das entsprechende Konto.
1. Entweder:

   * Geben Sie den Namen des erforderlichen Mitglieds ein (Benutzer- oder Gruppenkonto).
   * Oder verwenden Sie **Durchsuchen...** , um nach dem Prinzipal (Benutzer- oder Gruppenkonto) zu suchen und ihn auszuwählen, den Sie hinzufügen möchten.

1. Klicken Sie für die neue Eigenschaft auf Speichern (grünes Häkchensymbol) .

Oder löschen Sie ein vorhandenes Element mit dem Papierkorbsymbol.

## Verwalten von Zugriffsrechten {#access-right-management}

Auf der Registerkarte **Zugriffssteuerung** von CRXDE Lite können Sie die Richtlinien für die Zugriffssteuerung definieren und die zugehörigen Berechtigungen zuweisen.

Wählen Sie beispielsweise auf der Registerkarte „Zugangssteuerung“ im unteren rechten Bereich für die Option **Aktueller Pfad** die gewünschte Ressource im linken Bereich aus:

![crx_access_control_tab](assets/crx_accesscontrol_tab.png)

Die Richtlinien sind wie folgt kategorisiert:

* **Gültige Richtlinien zur Zugriffssteuerung**

   Diese Richtlinien können angewendet werden.

   Dies sind Richtlinien, die für die Erstellung einer lokalen Richtlinie zur Verfügung stehen. Nachdem Sie eine gültige Richtlinie ausgewählt und hinzugefügt haben, wird sie zu einer lokalen Richtlinie.

* **Lokale Richtlinien zur Zugriffssteuerung**

   Dies sind Richtlinien zur Zugriffssteuerung, die Sie angewendet haben. Sie können sie dann aktualisieren, sortieren oder entfernen.

   Eine lokale Richtlinie überschreibt jedwede Richtlinien, die vom übergeordneten Element übernommen werden.

* **Gültige Richtlinien zur Zugriffssteuerung**

   Dies sind Richtlinien zur Zugriffssteuerung, die jetzt für alle Zugriffsanfragen gelten. Sie zeigen die aggregierten Richtlinien an, die von den lokalen Richtlinien abgeleitet bzw. vom übergeordneten Element übernommenen werden.

### Auswählen von Richtlinien {#policy-selection}

Sie können Richtlinien für Folgendes auswählen:

* **Aktueller Pfad**

   Wählen Sie wie im vorherigen Beispiel eine Ressource innerhalb des Repositorys aus. Die Richtlinien für diesen aktuellen Pfad werden angezeigt.

* **Repository**

   : Wählt die Zugriffssteuerung auf Repository-Ebene aus. Beispiel: Wenn Sie die Berechtigung `jcr:namespaceManagement` festlegen, die nur für das Repository und nicht für einen Knoten relevant ist.

* **Prinzipal**

   Ein Prinzipal, der im Repository registriert ist.

   Sie können entweder den **Prinzipal**-Namen eingeben oder auf das Symbol rechts neben dem Feld klicken, um das Dialogfeld **Prinzipal auswählen** zu öffnen.

   Dort können Sie nach einem **Benutzer** oder einer **Gruppe** **suchen**. Wählen Sie den gewünschten Prinzipal aus der angezeigten Liste aus und klicken Sie dann auf **OK**, um den Wert in das vorherige Dialogfeld zu übernehmen.

![crx_access_control_selectprincipal](assets/crx_accesscontrol_selectprincipal.png)

>[!NOTE]
>
>Um die Verwaltung zu vereinfachen, empfehlen wir, dass Sie Gruppenkonten Zugriffsrechte zuweisen, nicht einzelnen Benutzerkonten.
>
>Es ist einfacher, anstelle vieler Benutzerkonten einige Gruppen zu verwalten.

### Berechtigungen {#privileges}

Die folgenden Berechtigungen können beim Hinzufügen eines Zugangssteuerungseintrags ausgewählt werden (umfassende Details finden Sie in [Sicherheits-API](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/security/Privilege.html)).

<table>
 <tbody>
  <tr>
   <th><strong>Berechtigungsname</strong></th>
   <th><strong>Dies steuert die Berechtigung zum...</strong></th>
  </tr>
  <tr>
   <td><code>jcr:read</code></td>
   <td>Abrufen eines Knotens und Lesen von dessen Eigenschaften und deren Werte.</td>
  </tr>
  <tr>
   <td><code>rep:write</code></td>
   <td>Dies ist eine Jackrabbit-spezifische Aggregat-Berechtigung von jcr:write und jcr:nodeTypeManagement.<br /> </td>
  </tr>
  <tr>
   <td><code>jcr:all</code></td>
   <td>Dies ist eine aggregierte Berechtigung, die alle anderen vordefinierten Berechtigungen enthält.</td>
  </tr>
  <tr>
   <td><strong>Erweitert</strong></td>
   <td> </td>
  </tr>
  <tr>
   <td><code>crx:replicate</code></td>
   <td>Durchführen der Replikation eines Knotens.</td>
  </tr>
  <tr>
   <td><code>jcr:addChildNodes</code></td>
   <td>Erstellen von untergeordneten Knoten eines Knotens.</td>
  </tr>
  <tr>
   <td><code>jcr:lifecycleManagement</code></td>
   <td>Durchführen von Lebenszyklusvorgängen für einen Knoten.</td>
  </tr>
  <tr>
   <td><code>jcr:lockManagement</code></td>
   <td>Sperren und Rntsperren eines Knoten; Aktualisieren einer Sperre.</td>
  </tr>
  <tr>
   <td><code>jcr:modifyAccessControl</code></td>
   <td>Ändern der Richtlinien zur Zugriffssteuerung für einen Knoten.</td>
  </tr>
  <tr>
   <td><code>jcr:modifyProperties</code></td>
   <td>Erstellen, Ändern und Entfernen der Eigenschaften eines Knotens.</td>
  </tr>
  <tr>
   <td><code>jcr:namespaceManagement</code></td>
   <td>Registrieren von Namespace-Definitionen, Aufheben der Registrierung und Ändern der Registrierung.</td>
  </tr>
  <tr>
   <td><code>jcr:nodeTypeDefinitionManagement</code></td>
   <td>Importieren von Knotentypdefinitionen in das Repository.</td>
  </tr>
  <tr>
   <td><code>jcr:nodeTypeManagement</code></td>
   <td>Steuern der Berechtigung zum Hinzufügen und Entfernen von Mixin-Knotentypen sowie Ändern des primären Knotentyps eines Knotens. Dies schließt auch alle Aufrufe der Node.addNode- und XML-Importmethoden ein, bei denen der Mixin-Typ oder primäre Typ des neuen Knotens explizit festgelegt ist.</td>
  </tr>
  <tr>
   <td><code>jcr:readAccessControl</code></td>
   <td>Lesen der Richtlinie zur Zugriffssteuerung für einen Knoten.</td>
  </tr>
  <tr>
   <td><code>jcr:removeChildNodes</code></td>
   <td>Entfernen von untergeordneten Knoten eines Knotens.</td>
  </tr>
  <tr>
   <td><code>jcr:removeNode</code></td>
   <td>Entfernen eines Knotens.</td>
  </tr>
  <tr>
   <td><code>jcr:retentionManagement</code></td>
   <td>Durchführen von Aufbewahrungsverwaltungsvorgängen für einen Knoten.</td>
  </tr>
  <tr>
   <td><code>jcr:versionManagement</code></td>
   <td>Ausführen von Versionierungsvorgängen für einen Knoten.</td>
  </tr>
  <tr>
   <td><code>jcr:workspaceManagement</code></td>
   <td>Das Erstellen und Löschen von Workspaces über die JCR-API.</td>
  </tr>
  <tr>
   <td><code>jcr:write</code></td>
   <td>Dies ist eine aggregierte Berechtigung, die Folgendes enthält:<br /> – jcr:modifyProperties<br /> – jcr:addChildNodes<br /> – jcr:removeNode<br /> – jcr:removeChildNodes</td>
  </tr>
  <tr>
   <td><code>rep:privilegeManagement</code></td>
   <td>Registrieren von neuen Berechtigungen.</td>
  </tr>
 </tbody>
</table>

### Registrieren von neuen Berechtigungen {#registering-new-privileges}

Sie können auch neue Berechtigungen registrieren:

1. Wählen Sie in der Symbolleiste **Tools** und dann **Berechtigungen** aus, um die aktuell registrierten Berechtigungen anzuzeigen.

   ![ac_privileges](assets/ac_privileges.png)

1. Öffnen Sie mithilfe des Symbols **Berechtigung registrieren** (**+**) das entsprechende Dialogfeld und legen Sie eine neue Berechtigung fest:

   ![ac_privilegeregister](assets/ac_privilegeregister.png)

1. Klicken Sie zum Speichern auf **OK**. Die Berechtigung steht jetzt zur Auswahl zur Verfügung.

### Hinzufügen von Zugriffssteuerungseinträgen {#adding-an-access-control-entry}

1. Wählen Sie die Ressource aus und öffnen Sie die Registerkarte **Zugriffssteuerung**.

1. Um neue **Richtlinien zur lokalen Zugriffssteuerung** hinzuzufügen, klicken Sie auf das **+**-Symbol rechts neben der Liste **Gültige Richtlinie für die Zugriffssteuerung**:

   ![crx_accesscontrol_applicable](assets/crx_accesscontrol_applicable.png)

1. Es wird ein neuer Eintrag unter **Richtlinien zur lokalen Zugriffssteuerung** angezeigt:

   ![crx_accesscontrol_newlocal](assets/crx_accesscontrol_newlocal.png)

1. Klicken Sie auf das **+**-Symbol, um einen neuen Eintrag hinzuzufügen:

   ![crx_accesscontrol_addentry](assets/crx_accesscontrol_addentry.png)

   >[!NOTE]
   >
   >Derzeit ist es nur mithilfe einer Übergangslösung möglich, eine leere Zeichenfolge festzulegen.
   >
   >Geben Sie einfach &quot;&quot; ein.

1. Definieren Sie Ihre Zugriffssteuerungsrichtlinie und klicken Sie auf **OK** speichern. Ihre neue Richtlinie wird:

   * wird unter **Richtlinien zur lokalen Zugriffssteuerung** aufgeführt; 
   * reflektiert die Änderungen unter **Gültige Richtlinien zur Zugriffssteuerung**.

CRX überprüft Ihre Auswahl. Bei einem gegebenen Prinzipal ist (maximal) 1 Ablehnungs- und 1 Zulassungseintrag in einem gegebenen Knoten vorhanden. Die Implementierung löscht immer redundante Einträge und stellt sicher, dass dieselbe Berechtigung nicht sowohl in den Zulassungs- als auch in den Ablehnungseinträgen aufgeführt wird.

### Sortieren von Richtlinien zur lokalen Zugriffssteuerung {#ordering-local-access-control-policies}

Die Reihenfolge in der Liste zeigt die Reihenfolge an, in der die Richtlinien angewendet werden.

1. Wählen Sie in der Tabelle **Richtlinien zur lokalen Zugriffssteuerung** den gewünschten Eintrag aus und ziehen Sie ihn an die neue Position in der Tabelle.

   ![crx_accesscontrol_reorder](assets/crx_accesscontrol_reorder.png)

1. Die Änderungen werden in den Tabellen **Richtlinien zur lokalen Zugriffssteuerung** und **Gültige Richtlinien zur Zugriffssteuerung** angezeigt.

### Entfernen von Richtlinien zur Zugriffssteuerung {#removing-an-access-control-policy}

1. Klicken Sie in der Tabelle **Richtlinien zur lokalen Zugriffssteuerung** auf das rote Symbol (-) rechts neben dem Eintrag.
1. Der Eintrag wird aus den Tabellen **Richtlinien zur lokalen Zugriffssteuerung** und **Gültige Richtlinien zur Zugriffssteuerung** entfernt.

### Testen von Richtlinien zur Zugriffssteuerung {#testing-an-access-control-policy}

1. Wählen Sie in der CRXDE Lite-Symbolleiste **Tools** und dann **Zugriffssteuerung testen...** aus.
1. Daraufhin wird ein neues Dialogfeld im Bereich rechts oben geöffnet. Wählen Sie den **Pfad** und/oder den **Prinzipal** aus, den Sie testen möchten.
1. Klicken Sie auf **Testen**, um die Ergebnisse für Ihre Auswahl zu sehen:

   ![crx_accesscontrol_test](assets/crx_accesscontrol_test.png)
