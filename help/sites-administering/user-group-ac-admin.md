---
title: Verwaltung von Benutzern, Gruppen und Zugriffsrechten
description: Erfahren Sie mehr über die Verwaltung von Benutzern, Gruppen und Zugriffsrechten in Adobe Experience Manager.
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
docset: aem65
exl-id: 5808b8f9-9b37-4970-b5c1-4d33404d3a8b
feature: Security
source-git-commit: 6799f1d371734b69c547f3c0c68e1e633aa63229
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Verwaltung von Benutzern, Gruppen und Zugriffsrechten{#user-group-and-access-rights-administration}

Die Aktivierung des Zugriffs auf ein CRX-Repository umfasst verschiedene Themen:

* [Zugriffsberechtigungen](#how-access-rights-are-evaluated): Die Konzepte, wie sie definiert und ausgewertet werden
* [Benutzerverwaltung](#user-administration): Verwaltung der einzelnen Konten, die für den Zugriff verwendet werden
* [Gruppenverwaltung](#group-administration): vereinfacht die Benutzerverwaltung durch die Bildung von Gruppen
* [Zugriffsrechteverwaltung](#access-right-management): Definition von Richtlinien, die steuern, wie diese Benutzer und Gruppen auf Ressourcen zugreifen können

Nachfolgend sind die grundlegenden Elemente aufgeführt:

**Benutzerkonten** - CRX authentifiziert den Zugriff durch Identifizieren und Überprüfen eines Benutzers (durch diese Person oder eine andere Anwendung) entsprechend den im Benutzerkonto gespeicherten Details.

In CRX ist jedes Benutzerkonto ein Knoten im Arbeitsbereich. Ein CRX-Benutzerkonto verfügt über die folgenden Eigenschaften:

* Es stellt eine Benutzerin bzw. einen Benutzer von CRX dar.
* Es verfügt über einen Benutzernamen und ein Passwort.
* Gilt für diesen Arbeitsbereich.
* Sie kann keine Unterbenutzer haben. Für hierarchische Zugriffsberechtigungen sollten Sie Gruppen verwenden.

* Sie können Zugriffsberechtigungen für das Benutzerkonto angeben.

  Um die Verwaltung zu vereinfachen, empfiehlt Adobe jedoch, dass Sie (in den meisten Fällen) Gruppenkonten Zugriffsrechte zuweisen. Die Zuweisung von Zugriffsrechten für jeden einzelnen Benutzer wird schnell schwierig zu verwalten (die Ausnahmen sind bestimmte Systembenutzer, wenn nur eine oder zwei Instanzen vorhanden sind).

**Gruppenkonten** - Gruppenkonten sind Sammlungen von Benutzern und/oder anderen Gruppen. Diese dienen zur Vereinfachung der Verwaltung, da eine Änderung der einer Gruppe zugewiesenen Zugriffsrechte automatisch auf alle Benutzenden dieser Gruppe angewendet wird. Eine Benutzerin bzw. ein Benutzer muss nicht unbedingt Mitglied einer Gruppe sein, gehört aber häufig zu mehreren.

In CRX hat eine Gruppe die folgenden Eigenschaften:

* Sie stellt eine Gruppe von Benutzenden mit gleichen Zugriffsrechten dar. Beispielsweise Authoring- oder Entwicklungsfachleute.
* Gilt für diesen Arbeitsbereich.
* Sie kann Mitglieder haben. Hierbei kann es sich um Einzelpersonen oder andere Gruppen handeln.
* Eine hierarchische Gruppierung kann über Mitgliederbeziehungen erreicht werden. Eine Gruppe kann nicht direkt unter einer anderen Gruppe im Repository platziert werden.
* Sie können die Zugriffsrechte für alle Gruppenmitglieder definieren.

**Zugriffsberechtigungen** - CRX verwendet Zugriffsrechte, um den Zugriff auf bestimmte Bereiche des Repositorys zu steuern.

Dies erfolgt über die Zuweisung von Berechtigungen, um den Zugriff auf eine Ressource (Knoten oder Pfad) im Repository zuzulassen oder abzulehnen. Da zahlreiche Berechtigungen zugewiesen werden können, müssen sie ausgewertet werden, um festzustellen, welche Kombination für die aktuelle Anfrage relevant ist.

Mit CRX können Sie die Zugriffsberechtigungen für Benutzer- und Gruppenkonten konfigurieren. Es werden dann dieselben grundlegenden Bewertungsprinzipien auf beide angewendet.

## Auswerten von Zugriffsrechten {#how-access-rights-are-evaluated}

>[!NOTE]
>
>In CRX wird die [Zugriffssteuerung gemäß der Definition in JSR-283](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html) implementiert.
>
>Die Standardinstallation eines CRX-Repositorys ist so konfiguriert, dass sie die ressourcenbasierten Zugriffssteuerungslisten verwendet. Dies ist eine mögliche Implementierung der Zugriffssteuerung nach JSR-283 und einer der Implementierungen, die mit Jackrabbit vorhanden sind.

### Objekte und Prinzipale {#subjects-and-principals}

CRX verwendet zwei Hauptkonzepte zur Bewertung der Zugriffsrechte:

* Ein **Prinzipal** ist eine Entität, die Zugriffsrechte besitzt. Zu den Prinzipalen gehören:

   * Ein Benutzerkonto
   * Ein Gruppenkonto

     Wenn ein Benutzerkonto zu einer oder mehreren Gruppen gehört, ist es auch mit jedem dieser Gruppenprinzipale verknüpft.

* Ein **Objekt** repräsentiert die Quelle einer Anfrage.

  Es dient zur Konsolidierung der für diese Anfrage relevanten Zugriffsrechte. Diese stammen von:

   * dem Benutzerprinzipal

     den Rechten, die Sie dem Benutzerkonto direkt zuweisen

   * allen mit diesem Benutzer verknüpften Gruppenprinzipalen

     Alle Rechte werden einer der Gruppen zugewiesen, zu denen der Benutzer gehört.

  Das Ergebnis wird dann verwendet, um den Zugriff auf die angeforderte Ressource zu erlauben oder zu verweigern.

#### Kompilieren der Liste der Zugriffsrechte für ein Subjekt {#compiling-the-list-of-access-rights-for-a-subject}

In CRX hängt das Betreff von Folgendem ab:

* dem Benutzer-Prinzipal
* allen Gruppenprinzipalen, die mit dieser Person verknüpft sind

Die Liste der für das Subjekt geltenden Zugriffsrechte wird erstellt aus:

* den Rechten, die Sie dem Benutzerkonto direkt zuweisen
* sowie allen Rechten, die Sie jeder der Gruppen zugewiesen haben, zu denen der Benutzer gehört

![chlimage_1-56](assets/chlimage_1-56.png)

>[!NOTE]
>
>* CRX berücksichtigt keine Benutzerhierarchie bei der Kompilierung der Liste.
>* CRX verwendet eine Gruppenhierarchie nur, wenn Sie eine Gruppe als Mitglied einer anderen Gruppe einbeziehen. Es gibt keine automatische Vererbung von Gruppenberechtigungen.
>* Die Reihenfolge, in der Sie die Gruppen festlegen, hat keinen Einfluss auf die Zugriffsrechte.
>

### Auflösen von Anfrage- und Zugriffsrechten {#resolving-request-and-access-rights}

Wenn CRX die Anfrage verarbeitet, vergleicht es die Zugriffsanfrage des Betreffs mit der Zugriffssteuerungsliste auf dem Repository-Knoten:

Wenn also Linda eine Aktualisierung des Knotens `/features` in der folgenden Repository-Struktur anfordert:

![chlimage_1-57](assets/chlimage_1-57.png)

### Rangfolge der Priorität {#order-of-precedence}

Zugriffsberechtigungen in CRX werden wie folgt bewertet:

* Benutzerprinzipale haben immer Vorrang vor Gruppenprinzipalen, unabhängig von:

   * ihrer Reihenfolge in der Zugriffsteuerungsliste
   * ihrer Position in der Knotenhierarchie

* Für einen bestimmten Prinzipal gibt es (höchstens) einen Ablehnungs- und einen Zulassungseintrag für einen bestimmten Knoten. Die Implementierung löscht immer redundante Einträge und stellt sicher, dass dieselbe Berechtigung nicht sowohl in den Zulassungs- als auch in den Ablehnungseinträgen aufgeführt wird.

>[!NOTE]
>
>Dieser Bewertungsprozess ist für die ressourcenbasierte Zugriffskontrolle einer standardmäßigen CRX-Installation geeignet.

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
   <td><p>Es ist gut, Zeit und Gedanken in die Konfiguration einer Neuinstallation zu investieren.</p> <p>Die Anwendung einer klaren Struktur vereinfacht die laufende Wartung und Verwaltung und stellt sicher, dass sowohl Ihre aktuellen Kollegen als auch Ihre zukünftigen Nachfolger leicht verstehen können, was implementiert wird.</p> </td>
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

Sie müssen beim entsprechenden Arbeitsbereich angemeldet sein und können dann über diese beiden Optionen auf das Dialogfeld zugreifen:

* über den Link **Benutzerverwaltung** in der Hauptkonsole von CRX
* über das Menü **Sicherheit** des CRX-Explorers

![chlimage_1-58](assets/chlimage_1-58.png)

**Eigenschaften**

* **Benutzer-ID**

  Der Kurzname für das Konto wird beim Zugriff auf CRX verwendet.

* **Prinzipalname**

  Vollständiger Name des Kontos

* **Kennwort**

  Erforderlich, wenn mit diesem Konto auf CRX zugegriffen wird

* **ntlmhash**

   Wird automatisch jedem neuen Konto zugewiesen und bei Änderung des Kennworts aktualisiert

* Sie können neue Eigenschaften hinzufügen, indem Sie einen Namen, einen Typ und den Wert definieren. Klicken Sie für jede neue Eigenschaft auf „Speichern“ (grünes Häkchensymbol).

**Gruppenmitgliedschaft**

Hier werden alle Gruppen angezeigt, die zu diesem Konto gehören. Die Spalte Übernommen zeigt Mitgliedschaften an, die durch eine Mitgliedschaft bei einer anderen Gruppe übernommen wurden.

Wenn Sie auf eine Gruppen-ID klicken (sofern verfügbar), wird die [Gruppenverwaltung](#group-administration) für diese Gruppe.

**Darsteller**

Mit der Funktion „Stellvertretend agieren“ kann ein Benutzer im Namen eines anderen Benutzers arbeiten.

Das bedeutet, dass ein Benutzerkonto andere Konten (Einzelperson oder Gruppe) angeben kann, die mit ihrem Konto arbeiten können. Wenn also Benutzer B stellvertretend für Benutzer A agieren darf, kann Benutzer B mit den vollständigen Kontodetails von Benutzer A handeln (einschließlich ID, Name und Zugriffsberechtigungen).

Dies ermöglicht es dem Darsteller, Aufgaben so auszuführen, als ob er das Konto, für das er stellvertretend agiert, verwendet hätte, z. B. während einer Abwesenheit oder kurzfristig eine übermäßige Belastung.

Wenn ein Konto stellvertretend für ein anderes agiert, ist es schwer zu sehen. Die Protokolldateien enthalten keine Informationen darüber, dass bei den Ereignissen eine Stellvertretung stattgefunden hat. Wenn also Benutzer B stellvertretend für Benutzer A agiert, können alle Ereignisse so aussehen, als ob sie von Benutzer A persönlich durchgeführt würden.

### Erstellen eines Benutzerkontos {#creating-a-user-account}

1. Öffnen Sie das Dialogfeld **Benutzerverwaltung**.
1. Klicken Sie auf **Benutzer erstellen**.
1. Sie können dann die Eigenschaften eingeben:

   * **Benutzer-ID** – wird als Kontoname verwendet
   * **Kennwort** – wird bei der Anmeldung benötigt
   * **Prinzipalname** – dient zur Eingabe des vollständigen Textnamens
   * **Zwischenpfad** – kann zum Erstellen einer hierarchischen Struktur verwendet werden

1. Klicken Sie auf Speichern (grünes Häkchen-Symbol).
1. Das Dialogfeld wird erweitert, sodass Sie Folgendes tun können:

   1. Konfigurieren Sie **Eigenschaften**.
   1. Zeigen Sie die **Gruppenmitgliedschaft** an.
   1. Definieren Sie **Darsteller**.

>[!NOTE]
>
>Manchmal kann es zu Leistungseinbußen kommen, wenn neue Benutzende in Installationen registriert werden, die über eine hohe Anzahl von diesen beiden Merkmalen verfügen:
>
>* Benutzer
>* Gruppen mit vielen Mitgliedern
>

### Aktualisieren eines Benutzerkontos {#updating-a-user-account}

1. Mit dem **Benutzerverwaltung** die Listenansicht aller Konten.
1. Navigieren Sie durch die Baumstruktur.
1. Klicken Sie auf das gewünschte Konto, damit Sie es zur Bearbeitung öffnen können.
1. Nehmen Sie eine Änderung vor und klicken Sie dann auf Speichern (grünes Häkchensymbol) für diesen Eintrag.
1. Klicken Sie auf **Schließen**, um den Vorgang zu beenden, oder auf **Liste…**, um zur Liste aller Benutzerkonten zurückzukehren.

### Entfernen eines Benutzerkontos {#removing-a-user-account}

1. Mit dem **Benutzerverwaltung** die Listenansicht aller Konten.
1. Navigieren Sie durch die Baumstruktur.
1. Wählen Sie das gewünschte Konto aus und klicken Sie auf **Benutzer löschen**; das Konto wird sofort gelöscht.

>[!NOTE]
>
>Dadurch wird der Knoten für diesen Prinzipal aus dem Repository entfernt.
>
>Einträge mit Zugriffsrechten werden nicht entfernt. So wird die historische Integrität gesichert.

### Definieren von Eigenschaften {#defining-properties}

Sie können **Eigenschaften** für neue oder vorhandene Konten definieren:

1. Öffnen Sie das Dialogfeld **Benutzerverwaltung** für das entsprechende Konto.
1. Geben Sie einen Namen für die **Eigenschaft** an.
1. Wählen Sie den **Typ** aus der Dropdown-Liste aus.
1. Definieren Sie den **Wert**.
1. Klicken Sie auf „Speichern“ (grünes Häkchensymbol) für die neue Eigenschaft.

Vorhandene Eigenschaften können über das Papierkorbsymbol gelöscht werden.

Mit Ausnahme des Kennworts können Eigenschaften nicht bearbeitet werden. Sie müssen gelöscht und neu erstellt werden.

#### Ändern des Passworts {#changing-the-password}

Die **Passwort** ist eine spezielle Eigenschaft, die durch Klicken auf **Kennwort ändern** -Link.

Über das Menü **Sicherheit** im CRX-Explorer können Sie auch das Passwort für Ihr eigenes Benutzerkonto ändern.

### Definieren von Darstellern {#defining-an-impersonator}

Sie können Darsteller zur Stellvertretung für neue oder vorhandene Konten definieren:

1. Öffnen Sie das Dialogfeld **Benutzerverwaltung** für das entsprechende Konto.
1. Geben Sie das Konto an, dem es gestattet sein soll, stellvertretend für dieses Konto zu agieren.

   Sie können über die Option „Durchsuchen…“ ein bestehendes Konto auswählen.

1. Klicken Sie auf „Speichern“ (grünes Häkchensymbol) für die neue Eigenschaft.

## Gruppenverwaltung {#group-administration}

Für die **Gruppenverwaltung** wird ein Standarddialogfeld verwendet.

Sie müssen beim entsprechenden Arbeitsbereich angemeldet sein und können dann über diese beiden Optionen auf das Dialogfeld zugreifen:

* über den Link **Gruppenverwaltung** in der Hauptkonsole von CRX
* über das Menü **Sicherheit** des CRX-Explorers

![chlimage_1-8](assets/chlimage_1-8.jpeg)

**Eigenschaften**

* **Gruppen-ID**

  Kurzname für das Gruppenkonto

* **Prinzipalname**

  Vollständiger Name des Gruppenkontos

* Sie können neue Eigenschaften hinzufügen, indem Sie einen Namen, einen Typ und den Wert definieren. Klicken Sie für jede neue Eigenschaft auf „Speichern“ (grünes Häkchensymbol).

* **Mitglieder**

  Sie können Benutzer oder andere Gruppen als Mitglieder dieser Gruppe hinzufügen.

**Gruppenmitgliedschaft**

Hier werden alle Gruppen angezeigt, die zu diesem aktuellen Gruppenkonto gehören. Die Spalte Übernommen zeigt Mitgliedschaften an, die durch eine Mitgliedschaft bei einer anderen Gruppe übernommen wurden.

Durch Klicken auf eine Gruppen-ID wird das Dialogfeld für diese Gruppe geöffnet.

**Mitglieder**

Listet alle Konten (Einzelpersonen und/oder Gruppen) auf, die Mitglieder der aktuellen Gruppe sind.

Die Spalte **Übernommen** zeigt Mitgliedschaften an, die durch eine Mitgliedschaft bei einer anderen Gruppe übernommen wurden.

>[!NOTE]
>
>Wenn die Eigentümer-, Bearbeiter- oder Betrachterrolle einem Benutzer in einem beliebigen Asset-Ordner zugewiesen wird, wird eine neue Gruppe erstellt. Der Gruppenname ist vom Format `mac-default-<foldername>` für jeden Ordner, für den die Rollen definiert sind.

### Erstellen eines Gruppenkontos {#creating-a-group-account}

1. Öffnen Sie die **Gruppenverwaltung** Dialogfeld.
1. Klicken Sie auf **Gruppe erstellen**.
1. Sie können dann die Eigenschaften eingeben:

   * **Prinzipalname** – dient zur Eingabe des vollständigen Textnamens
   * **Zwischenpfad** – kann zum Erstellen einer hierarchischen Struktur verwendet werden

1. Klicken Sie auf Speichern (grünes Häkchen-Symbol).
1. Das Dialogfeld wird erweitert, sodass Sie:

   1. Konfigurieren Sie **Eigenschaften**.
   1. Zeigen Sie die **Gruppenmitgliedschaft** an.
   1. **Mitglieder** verwalten.

### Aktualisieren eines Gruppenkontos {#updating-a-group-account}

1. Mit dem **Gruppenverwaltung** die Listenansicht aller Konten.
1. Navigieren Sie durch die Baumstruktur.
1. Klicken Sie auf das gewünschte Konto, damit Sie es zur Bearbeitung öffnen können.
1. Nehmen Sie eine Änderung vor und klicken Sie dann auf Speichern (grünes Häkchensymbol) für diesen Eintrag.
1. Klicken Sie auf **Schließen**, um den Vorgang zu beenden oder auf **Liste…**, um zur Liste aller Gruppenkonten zurückzukehren.

### Entfernen eines Gruppenkontos {#removing-a-group-account}

1. Mit dem **Gruppenverwaltung** die Listenansicht aller Konten.
1. Navigieren Sie durch die Baumstruktur.
1. Wählen Sie das gewünschte Konto aus und klicken Sie auf **Gruppe löschen**; das Konto wird sofort gelöscht.

>[!NOTE]
>
>Dadurch wird der Knoten für diesen Prinzipal aus dem Repository entfernt.
>
>Einträge mit Zugriffsrechten werden nicht entfernt. So wird die historische Integrität gesichert.

### Definieren von Eigenschaften {#defining-properties-1}

Sie können Eigenschaften für neue oder vorhandene Konten definieren:

1. Öffnen Sie das Dialogfeld **Gruppenverwaltung** für das entsprechende Konto.
1. Geben Sie einen Namen für die **Eigenschaft** an.
1. Wählen Sie den **Typ** aus der Dropdown-Liste aus.
1. Definieren Sie den **Wert**.
1. Klicken Sie auf „Speichern“ (grünes Häkchensymbol) für die neue Eigenschaft.

Vorhandene Eigenschaften können über das Papierkorbsymbol gelöscht werden.

### Mitglieder {#members}

Sie können Mitglieder zur aktuellen Gruppe hinzufügen:

1. Öffnen Sie das Dialogfeld **Gruppenverwaltung** für das entsprechende Konto.
1. Sie haben folgende Möglichkeiten:

   * Geben Sie den Namen des erforderlichen Mitglieds ein (Benutzer- oder Gruppenkonto).
   * Oder verwenden Sie **Durchsuchen…**, um nach dem Prinzipal (Benutzer- oder Gruppenkonto) zu suchen, den Sie hinzufügen möchten, und wählen Sie diesen aus.

1. Klicken Sie auf „Speichern“ (grünes Häkchensymbol) für die neue Eigenschaft.

Alternativ können Sie ein vorhandenes Mitglied über das Papierkorbsymbol löschen.

## Verwalten von Zugriffsrechten {#access-right-management}

Mit dem **Zugriffssteuerung** -Registerkarte von CRXDE Lite können Sie die Zugriffssteuerungsrichtlinien definieren und die entsprechenden Berechtigungen zuweisen.

Beispiel: für **Aktueller Pfad** Wählen Sie die gewünschte Ressource im linken Bereich und im unteren rechten Bereich die Registerkarte Zugriffssteuerung aus:

![crx_access_control_tab](assets/crx_accesscontrol_tab.png)

Die Richtlinien sind wie folgt kategorisiert:

* **Gültige Richtlinien zur Zugriffssteuerung**

  Diese Richtlinien können angewendet werden.

  Dies sind Richtlinien, die für die Erstellung einer lokalen Richtlinie zur Verfügung stehen. Wenn Sie eine entsprechende Richtlinie auswählen und hinzufügen, wird sie zu einer lokalen Richtlinie.

* **Lokale Richtlinien zur Zugriffssteuerung**

  Dies sind Richtlinien zur Zugriffssteuerung, die Sie angewendet haben. Sie können sie dann aktualisieren, sortieren oder entfernen.

  Eine lokale Richtlinie überschreibt alle Richtlinien, die vom übergeordneten Element übernommen wurden.

* **Gültige Richtlinien zur Zugriffssteuerung**

  Dies sind Richtlinien zur Zugriffssteuerung, die jetzt für alle Zugriffsanfragen gelten. Sie zeigen die aggregierten Richtlinien an, die von den lokalen Richtlinien abgeleitet bzw. vom übergeordneten Element übernommenen werden.

### Auswählen von Richtlinien {#policy-selection}

Sie können Richtlinien für Folgendes auswählen:

* **Aktueller Pfad**

  Wählen Sie wie im vorherigen Beispiel eine Ressource innerhalb des Repositorys aus. Die Richtlinien für diesen &quot;aktuellen Pfad&quot;werden angezeigt.

* **Repository**

  : Wählt die Zugriffssteuerung auf Repository-Ebene aus. Beispiel: Wenn Sie die Berechtigung `jcr:namespaceManagement` festlegen, die nur für das Repository und nicht für einen Knoten relevant ist.

* **Prinzipal**

  Ein Prinzipal, der im Repository registriert ist.

  Sie können entweder die **Principal** oder klicken Sie auf das Symbol rechts neben dem Feld, um die **Prinzipal auswählen** Dialogfeld.

  Damit können Sie **Suche** für **Benutzer** oder **Gruppe**. Wählen Sie den erforderlichen Prinzipal aus der resultierenden Liste aus und klicken Sie auf **OK** , um den Wert wieder in das vorherige Dialogfeld zu übertragen.

![crx_access_control_selectprincipal](assets/crx_accesscontrol_selectprincipal.png)

>[!NOTE]
>
>Um die Verwaltung zu vereinfachen, empfiehlt Adobe, dass Sie Gruppenkonten Zugriffsrechte zuweisen, nicht einzelnen Benutzerkonten.
>
>Es ist einfacher, einige wenige Gruppen anstatt vieler Benutzerkonten zu verwalten.

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
   <td>Erstellen, ändern und entfernen Sie die Eigenschaften eines Knotens.</td>
  </tr>
  <tr>
   <td><code>jcr:namespaceManagement</code></td>
   <td>Namespace-Definitionen registrieren, deregistrieren und ändern.</td>
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
   <td>Registrieren Sie eine neue Berechtigung.</td>
  </tr>
 </tbody>
</table>

### Registrieren von neuen Berechtigungen {#registering-new-privileges}

Sie können auch neue Berechtigungen registrieren:

1. Wählen Sie in der Symbolleiste **Instrumente**, dann **Berechtigungen** , um die aktuell registrierten Berechtigungen anzuzeigen.

   ![ac_privileges](assets/ac_privileges.png)

1. Verwenden Sie die **Berechtigung registrieren** Symbol (**+**), damit Sie eine Berechtigung definieren können:

   ![ac_privilegeregister](assets/ac_privilegeregister.png)

1. Klicken Sie zum Speichern auf **OK**. Die Berechtigung steht jetzt zur Auswahl zur Verfügung.

### Hinzufügen von Zugriffssteuerungseinträgen {#adding-an-access-control-entry}

1. Wählen Sie die Ressource aus und öffnen Sie die Registerkarte **Zugriffssteuerung**.

1. Um neue **Richtlinien zur lokalen Zugriffssteuerung** hinzuzufügen, klicken Sie auf das **+**-Symbol rechts neben der Liste **Gültige Richtlinie für die Zugriffssteuerung**:

   ![crx_accesscontrol_applicable](assets/crx_accesscontrol_applicable.png)

1. Es wird ein neuer Eintrag unter **Richtlinien zur lokalen Zugriffssteuerung** angezeigt:

   ![crx_accesscontrol_newlocal](assets/crx_accesscontrol_newlocal.png)

1. Klicken Sie auf **+** -Symbol, damit Sie einen Eintrag hinzufügen können:

   ![crx_accesscontrol_addentry](assets/crx_accesscontrol_addentry.png)

   >[!NOTE]
   >
   >Derzeit ist es nur mithilfe einer Übergangslösung möglich, eine leere Zeichenfolge festzulegen.
   >
   >Dazu müssen Sie `""`.

1. Definieren Sie Ihre Zugriffssteuerungsrichtlinie und klicken Sie zum Speichern auf **OK**. Ihre neue Richtlinie lautet:

   * aufgeführt unter **Richtlinie zur lokalen Zugriffssteuerung**
   * Änderungen werden in der **Effektive Richtlinien zur Zugriffssteuerung**.

CRX überprüft Ihre Auswahl. Für einen bestimmten Prinzipal gibt es (höchstens) eine Ablehnungs- und eine Zulassungseingabe für einen bestimmten Knoten. Die Implementierung löscht immer redundante Einträge und stellt sicher, dass dieselbe Berechtigung nicht sowohl in den Zulassungs- als auch in den Ablehnungseinträgen aufgeführt wird.

### Sortieren von Richtlinien zur lokalen Zugriffssteuerung {#ordering-local-access-control-policies}

Die Reihenfolge in der Liste zeigt die Reihenfolge an, in der die Richtlinien angewendet werden.

1. In der Tabelle von **Richtlinien zur lokalen Zugriffssteuerung**, wählen Sie den gewünschten Eintrag aus und ziehen Sie ihn an die neue Position in der Tabelle.

   ![crx_accesscontrol_reorder](assets/crx_accesscontrol_reorder.png)

1. Die Änderungen werden in beiden Tabellen für die **Lokal** und **Effektive Richtlinien zur Zugriffssteuerung**.

### Entfernen von Richtlinien zur Zugriffssteuerung {#removing-an-access-control-policy}

1. In der Tabelle von **Richtlinien zur lokalen Zugriffssteuerung** klicken Sie auf das rote Symbol (-) rechts neben dem Eintrag.
1. Der Eintrag wird aus beiden Tabellen für die **Lokal** und **Effektive Richtlinien zur Zugriffssteuerung**.

### Testen von Richtlinien zur Zugriffssteuerung {#testing-an-access-control-policy}

1. Wählen Sie in der CRXDE Lite-Symbolleiste die Option **Instrumente**, dann **Zugriffskontrolle testen...**.
1. Oben rechts wird ein neues Dialogfeld geöffnet. Wählen Sie den **Pfad** und/oder den **Prinzipal** aus, den Sie testen möchten.
1. Klicken Sie auf **Testen**, um die Ergebnisse für Ihre Auswahl zu sehen:

   ![crx_accesscontrol_test](assets/crx_accesscontrol_test.png)
