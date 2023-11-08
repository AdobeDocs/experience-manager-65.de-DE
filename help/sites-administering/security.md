---
title: Benutzerverwaltung und Sicherheit
description: Erfahren Sie mehr über Benutzerverwaltung und Sicherheit in AEM.
uuid: 4512c0bf-71bf-4f64-99f6-f4fa5a61d572
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: e72da81b-4085-49b0-86c3-11ad48978a8a
docset: aem65
exl-id: 53d8c654-8017-4528-a44e-e362d8b59f82
feature: Security
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '5401'
ht-degree: 100%

---

# Benutzerverwaltung und Sicherheit{#user-administration-and-security}

In diesem Kapitel wird beschrieben, wie die Benutzerautorisierung konfiguriert und verwaltet wird. Außerdem werden die Grundlagen für die Funktionsweise von Authentifizierung und Autorisierung in AEM beschrieben.

## Benutzende und Gruppen in AEM {#users-and-groups-in-aem}

Dieser Abschnitt behandelt ausführlicher die verschiedenen Entitäten und verwandten Konzepte, um Sie beim Konfigurieren eines einfach zu handhabenden Benutzerverwaltungsansatzes zu unterstützen.

### Benutzer {#users}

Benutzende melden sich mit ihrem Konto bei AEM an. Jedes Benutzerkonto ist eindeutig und enthält die grundlegenden Kontodetails sowie die zugewiesenen Berechtigungen.

Benutzende sind häufig Mitglieder von Gruppen, was die Zuweisung dieser Berechtigungen und/oder Rechte vereinfacht.

### Gruppen {#groups}

Gruppen sind Sammlungen von Benutzenden, anderen Gruppen oder beidem. Diese Sammlungen werden alle als Mitglieder einer Gruppe bezeichnet.

Ihr Hauptzweck besteht darin, Verwaltungsvorgänge zu vereinfachen, indem die Anzahl der zu aktualisierenden Entitäten verringert wird, da eine Änderung an einer Gruppe auf alle Mitglieder der Gruppe angewendet wird. Gruppen spiegeln häufig Folgendes wider:

* Eine Rolle innerhalb der Anwendung, z. B. eine Person, die den Inhalt surfen darf, oder eine Person, die Inhalte hinzufügen darf.
* Ihre eigene Organisation, wobei Sie die Rollen erweitern können, um zwischen Mitwirkenden aus verschiedenen Abteilungen zu unterscheiden, wenn diese auf unterschiedliche Zweige in der Inhaltsstruktur beschränkt sind.

Deshalb sind Gruppen an sich meist stabil, während Benutzende häufiger wechseln.

Bei entsprechender Planung und einer sauberen Struktur kann die Verwendung von Gruppen Ihrer Struktur entsprechen, sodass Sie einen klaren Überblick haben und Ihnen ein effizienter Mechanismus für Aktualisierungen zur Verfügung steht.

### Integrierte Benutzende und Gruppen {#built-in-users-and-groups}

AEM WCM installiert mehrere Benutzende und Gruppen. Diese Sammlungen werden angezeigt, wenn Sie nach der Installation zum ersten Mal auf die Sicherheitskonsole zugreifen.

In der folgenden Tabelle finden Sie eine Aufstellung der einzelnen Elemente zusammen mit:

* einer kurzen Beschreibung;
* etwaigen Empfehlungen zu erforderlichen Änderungen.

*Ändern Sie alle Standardpasswörter* (sofern Sie nicht unter gewissen Bedingungen das gesamte Konto löschen).

<table>
 <tbody>
  <tr>
   <td>Benutzer-ID </td>
   <td>Typ</td>
   <td>Beschreibung</td>
   <td>Empfehlung</td>
  </tr>
  <tr>
   <td><p>admin</p> <p>Standardpasswort: admin</p> </td>
   <td>User</td>
   <td><p>Systemadministrationskonto mit vollen Zugriffsrechten.</p> <p>Dieses Konto wird für die Verbindung zwischen AEM WCM und CRX verwendet.</p> <p>Wenn Sie dieses Konto versehentlich löschen, wird es beim Neustart des Repositorys neu erstellt (bei Standardeinrichtung).</p> <p>Das Konto „admin“ ist eine Voraussetzung der AEM-Plattform. Folglich kann dieses Konto nicht gelöscht werden.</p> </td>
   <td><p>Adobe empfiehlt, das Standardpasswort für dieses Benutzerkonto zu ändern.</p> <p>Vorzugsweise sollte dies bei der Installation geschehen, es ist aber auch später möglich.</p> <p>Hinweis: Verwechseln Sie dieses Konto nicht mit dem Konto „admin“ der CQ Servlet Engine.</p> </td>
  </tr>
  <tr>
   <td><p>Anonym</p> <p> </p> </td>
   <td>User</td>
   <td><p>Besitzt die Standardrechte für nicht authentifizierten Zugriff auf eine Instanz. Dieses Konto verfügt standardmäßig über die Mindestzugriffsrechte.</p> <p>Wenn Sie dieses Konto versehentlich löschen, wird es beim Start neu erstellt. Das Konto kann zwar nicht dauerhaft gelöscht, aber deaktiviert werden.</p> </td>
   <td>Löschen oder deaktivieren Sie dieses Konto nicht, da dies die Funktionalität von Authoring-Instanzen beeinträchtigen kann. Wenn es Sicherheitsanforderungen gibt, die Sie dazu verpflichten, es zu löschen, stellen Sie sicher, dass Sie zuerst die Auswirkungen auf Ihre Systeme ordnungsgemäß testen.</td>
  </tr>
  <tr>
   <td><p>author</p> <p>Standardpasswort: author</p> </td>
   <td>User</td>
   <td><p>Ein Autorenkonto, das zu Schreibvorgängen unter „/content“ berechtigt ist. Umfasst Berechtigungen für Mitwirkende und Menschen, die surfen.</p> <p>Kann als Webmaster verwendet werden, da es Zugriff auf die gesamte „/content“-Baumstruktur hat.</p> <p>Bei diesem Konto handelt es sich nicht um einen integrierten Benutzer, sondern um einen weiteren Geometrixx-Demobenutzer</p> </td>
   <td><p>Adobe empfiehlt, entweder das Konto vollständig zu löschen oder das Standardpasswort zu ändern.</p> <p>Vorzugsweise sollte dies bei der Installation geschehen, es ist aber auch später möglich.</p> </td>
  </tr>
  <tr>
   <td>Administrierende</td>
   <td>Gruppe</td>
   <td><p>Gruppe, die allen Mitgliedern Admin-Rechte gewährt. Diese Gruppe darf nur von Admins bearbeitet werden.</p> <p>Hat vollständige Zugriffsrechte.</p> </td>
   <td>Auch wenn Sie für einen Knoten „Jedem verweigern“ einstellen, können die Admins immer noch auf den Knoten zugreifen</td>
  </tr>
  <tr>
   <td>content-authors</td>
   <td>Gruppe</td>
   <td><p>Gruppe, die für die Inhaltsbearbeitung verantwortlich ist. Es sind Berechtigungen zum Lesen, Ändern, Erstellen und Löschen erforderlich.</p> </td>
   <td>Sie können eigene „content-author“-Gruppen mit projektspezifischen Zugriffsrechten erstellen, sofern Sie Berechtigungen zum Lesen, Ändern, Erstellen und Löschen hinzufügen.</td>
  </tr>
  <tr>
   <td>contributor</td>
   <td>Gruppe</td>
   <td><p>Grundlegende Berechtigungen, die es Benutzenden erlauben, Inhalte zu schreiben (rein funktionsbezogen).</p> <p>Weist der „/content“-Struktur keine Berechtigungen zu. Muss für die einzelnen Gruppen oder Benutzenden zugewiesen werden.</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td>dam-users</td>
   <td>Gruppe</td>
   <td>Vordefinierte Referenzgruppe für typische Benutzende von AEM Assets. Mitglieder dieser Gruppe verfügen über die entsprechenden Berechtigungen, um das Hochladen/Freigeben von Assets und Sammlungen zu ermöglichen.</td>
   <td> </td>
  </tr>
  <tr>
   <td>everyone</td>
   <td>Gruppe</td>
   <td><p>Jeder und jede Benutzende in AEM ist ein Mitglied der Gruppe „everyone“, auch wenn diese Gruppe oder Mitgliedschaftsbeziehung nicht in allen Tools angezeigt wird.</p> <p>Diese Gruppe kann als Standardberechtigungen betrachtet werden, da sie verwendet werden kann, um Berechtigungen für alle anzuwenden, selbst für Benutzende, die in Zukunft erstellt werden.</p> </td>
   <td><p>Ändern oder löschen Sie diese Gruppe nicht.</p> <p>Eine Änderung dieses Kontos hat weitere Auswirkungen auf die Sicherheit.</p> </td>
  </tr>
  <tr>
   <td>tag-administrators</td>
   <td>Gruppe</td>
   <td>Gruppe, die zum Bearbeiten von Tags berechtigt ist.</td>
   <td> </td>
  </tr>
  <tr>
   <td>user-administrators</td>
   <td>Gruppe</td>
   <td>Gruppe, die zur Benutzerverwaltung autorisiert, also berechtigt, Benutzerinnen und Benutzer sowie Gruppen zu erstellen.</td>
   <td> </td>
  </tr>
  <tr>
   <td>workflow-editors</td>
   <td>Gruppe</td>
   <td>Gruppe, die zum Erstellen und Ändern von Workflow-Modellen berechtigt ist.</td>
   <td> </td>
  </tr>
  <tr>
   <td>workflow-users</td>
   <td>Gruppe</td>
   <td><p>Eine Person, die an einem Workflow beteiligt ist, muss Mitglied der Gruppe „workflow-users“ sein. Ermöglicht den Benutzenden vollen Zugriff auf: „/etc/workflow/instances“, damit sie die Workflow-Instanz aktualisieren können.</p> <p>Die Gruppe ist zwar Teil der Standardinstallation, Sie müssen jedoch Ihre Benutzenden manuell zur Gruppe hinzufügen.</p> </td>
  </tr>
 </tbody>
</table>

## Berechtigungen in AEM {#permissions-in-aem}

AEM nutzt ACLs (Access Control Lists, Zugriffssteuerungslisten), um zu ermitteln, welche Aktionen eine Benutzerin, ein Benutzer oder eine Gruppe wo durchführen kann.

### Berechtigungen und ACLs {#permissions-and-acls}

Berechtigungen definieren, wer welche Aktionen für eine Ressource ausführen kann. Berechtigungen sind das Ergebnis einer Bewertung der [Zugriffssteuerung](#access-control-lists-and-how-they-are-evaluated).

Sie können die für bestimmte Benutzende erteilten/abgelehnten Berechtigungen durch Aktivieren oder Deaktivieren der Kontrollkästchen für die einzelnen AEM-[Aktionen](security.md#actions) ändern. Ein Häkchen bedeutet, dass eine Aktion erlaubt ist. Kein Häkchen bedeutet, dass eine Aktion abgelehnt wird.

Die Stelle, an der sich das Häkchen im Raster befindet, zeigt zudem an, welche Berechtigungen Benutzende in welchen AEM-Bereichen (also Pfaden) haben.

### Aktionen {#actions}

Aktionen können auf einer Seite (Ressource) ausgeführt werden. Für jede Seite in der Hierarchie können Sie festlegen, welche Aktion Benutzende auf dieser Seite ausführen dürfen. Mithilfe von [Berechtigungen](#permissions-and-acls) können Sie eine Aktion zulassen oder ablehnen.

<table>
 <tbody>
  <tr>
   <td><strong>Aktion </strong></td>
   <td><strong>Beschreibung </strong></td>
  </tr>
  <tr>
   <td>Lesen</td>
   <td>Benutzende dürfen die Seite und alle untergeordneten Seiten lesen.</td>
  </tr>
  <tr>
   <td>Ändern</td>
   <td><p>Benutzende können:</p>
    <ul>
     <li>vorhandenen Inhalt auf der Seite und auf untergeordneten Seiten ändern.</li>
     <li>Absätze auf der Seite oder auf einer untergeordneten Seite erstellen.</li>
    </ul> <p>Auf JCR-Ebene können Benutzende eine Ressource bearbeiten, indem sie ihre Eigenschaften, Sperr- und Versionierungsvorgänge sowie nt-Änderungen bearbeiten. Außerdem verfügen sie über volle Schreibrechte für Knoten, die einen untergeordneten jcr:content-Knoten definieren. Zum Beispiel: cq:Page, nt:file, cq:Asset.</p> </td>
  </tr>
  <tr>
   <td>Erstellen</td>
   <td><p>Benutzende können:</p>
    <ul>
     <li>eine neue Seite oder untergeordnete Seite erstellen.</li>
    </ul> <p>Wenn <strong>Verändern</strong> abgelehnt wird, werden die Unterstrukturen unterhalb von jcr:content ausgeschlossen, da die Erstellung von jcr:content und seiner untergeordneten Knoten als Seitenänderung betrachtet wird. Dies gilt nur für die Knoten, die einen untergeordneten jcr:content-Knoten definieren.</p> </td>
  </tr>
  <tr>
   <td>Löschen</td>
   <td><p>Benutzende können:</p>
    <ul>
     <li>vorhandene Absätze von der Seite oder einer untergeordneten Seite löschen.</li>
     <li>eine Seite oder untergeordnete Seite löschen.</li>
    </ul> <p>Wenn <strong>Verändern</strong> abgelehnt wird, werden die Unterstrukturen unterhalb von jcr:content ausgeschlossen, da das Entfernen von jcr:content und seiner Unterknoten als Seitenänderung betrachtet wird. Dies gilt nur für die Knoten, die einen untergeordneten jcr:content-Knoten definieren.</p> </td>
  </tr>
  <tr>
   <td>ACL lesen</td>
   <td>Benutzende können die Zugriffssteuerungsliste der Seite oder untergeordneten Seiten lesen.</td>
  </tr>
  <tr>
   <td>ACL bearbeiten</td>
   <td>Benutzende können die Zugriffssteuerungsliste der Seite oder untergeordneter Seiten ändern.</td>
  </tr>
  <tr>
   <td>Replizieren</td>
   <td>Benutzende können Inhalte in einer anderen Umgebung replizieren (z. B. in der Publishing-Umgebung). Die Berechtigung gilt auch für untergeordnete Seiten.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>AEM generiert automatisch Benutzergruppen für die Rollenzuweisung (Inhaber, Bearbeiter, Betrachter) in [Sammlungen](/help/assets/manage-collections.md). Das manuelle Hinzufügen von ACLs für solche Gruppen kann jedoch Sicherheitslücken in AEM verursachen. Adobe empfiehlt, das manuelle Hinzufügen von ACLs zu vermeiden.

### Zugriffssteuerungslisten und deren Bewertung {#access-control-lists-and-how-they-are-evaluated}

AEM WCM verwendet Zugriffssteuerungslisten (ACLs), um die Berechtigungen zu organisieren, die auf die verschiedenen Seiten angewendet werden.

Zugriffssteuerungslisten bestehen aus den individuellen Berechtigungen und werden verwendet, um die Reihenfolge zu bestimmen, in der diese Berechtigungen angewendet werden. Die Liste wird entsprechend der Hierarchie der betroffenen Seiten gebildet. Diese Liste wird dann von unten nach oben gescannt, bis die erste geeignete Berechtigung zur Anwendung auf eine Seite gefunden wird.

>[!NOTE]
>
>Es gibt ACLs, die in den Beispielen enthalten sind. Es wird empfohlen, dass Sie überprüfen und bestimmen, was für Ihre Anwendungen geeignet ist. Um sich die inbegriffenen ACLs anzusehen, gehen Sie zu **CRXDE** und wählen Sie die Registerkarte **Zugriffssteuerung** für die folgenden Knoten aus:
>
>* `/etc/cloudservices`
>* `/home/users/we-retail`
>
>Ihre benutzerdefinierte Anwendung kann den Zugriff für andere Beziehungen festlegen, z. B.:
>
>* `*/social/relationships/friend/*`
>* oder `*/social/relationships/pending-following/*`.
>
>Wenn Sie bestimmte ACLs für Communities erstellen, können Mitgliedern, die diesen Communities beitreten, zusätzliche Berechtigungen erteilt werden. Wenn beispielsweise Benutzende den Communitys unter `/content/we-retail/us/en/community` beitreten

### Berechtigungsstatus {#permission-states}

>[!NOTE]
>
>Für CQ 5.3-Benutzende:
>
>Im Gegensatz zu vorherigen CQ-Versionen sollten die Rechte **Erstellen** und **Löschen** nicht mehr erteilt werden, wenn jemand nur Seiten ändern darf. Gewähren Sie stattdessen die Aktion **Ändern** nur, wenn Sie möchten, dass Benutzende Komponenten auf bestehenden Seiten erstellen, ändern oder löschen können.
>
>Aus Gründen der Abwärtskompatibilität berücksichtigen die Tests für Aktionen nicht die Sonderbehandlung von Knoten, die **jcr:content** definieren.

| **Aktion** | **Beschreibung** |
|---|---|
| Zulassen (Häkchen) | AEM WCM ermöglicht es Benutzenden, die Aktion auf dieser Seite oder auf untergeordneten Seiten durchzuführen. |
| Verweigern (kein Häkchen) | AEM WCM gestattet es Benutzenden nicht, die Aktion auf dieser Seite oder auf untergeordneten Seiten durchzuführen. |

Die Berechtigungen gelten auch für untergeordnete Seiten.

Wenn eine Berechtigung nicht vom übergeordneten Knoten vererbt wird, aber mindestens einen lokalen Eintrag dafür hat, werden die folgenden Symbole an das Kontrollkästchen angehängt. Ein lokaler Eintrag ist ein Eintrag, der in der CRX 2.2-Benutzeroberfläche erstellt wird. (Platzhalter-ACLs können derzeit nur in CRX erstellt werden.)

Für eine Aktion unter einem bestimmten Pfad:

<table>
 <tbody>
  <tr>
   <td>* (Sternchen)</td>
   <td>Es gibt mindestens einen lokalen Eintrag (entweder effektiv oder ineffektiv). Diese Platzhalter-ACLs werden in CRX definiert.</td>
  </tr>
  <tr>
   <td>! (Ausrufezeichen)</td>
   <td>Es gibt mindestens einen Eintrag, der derzeit nicht effektiv ist.</td>
  </tr>
 </tbody>
</table>

Wenn Sie den Mauszeiger über das Sternchen oder Ausrufezeichen bewegen, liefert eine QuickInfo weitere Details zu den deklarierten Einträgen. Die QuickInfo ist in zwei Teile unterteilt:

<table>
 <tbody>
  <tr>
   <td>Oberer Teil</td>
   <td><p>Listet die effektiven Einträge auf.</p> </td>
  </tr>
  <tr>
   <td>Unterer Teil</td>
   <td>Listet die ineffektiven Einträge auf, die sich an anderer Stelle der Struktur auswirken können (wie durch ein spezielles Attribut im entsprechenden Zugriffssteuerungseintrag angegeben, das den Umfang des Eintrags einschränkt). Dies kann auch ein Eintrag sein, dessen Wirkung von einem anderen Eintrag, der unter dem angegebenen Pfad oder in einem Vorgängerknoten definiert wurde, aufgehoben wurde.</td>
  </tr>
 </tbody>
</table>

![chlimage_1-112](assets/chlimage_1-112.png)

>[!NOTE]
>
>Wenn für eine Seite keine Berechtigungen definiert sind, werden alle Aktionen verweigert.

Im Folgenden finden Sie Empfehlungen zur Verwaltung von Zugriffssteuerungslisten:

* Weisen Sie Benutzenden keine Berechtigungen direkt zu. Weisen Sie diese nur Gruppen zu.

  Dies vereinfacht die Wartung, da die Anzahl der Gruppen deutlich kleiner ist als die Anzahl der Benutzenden und damit weniger Schwankungen ausgesetzt ist.

* Wenn Sie möchten, dass eine Gruppe/Person nur in der Lage sein soll, Seiten zu ändern, dürfen Sie keine Rechte zum Erstellen oder Ablehnen gewähren. Gewähren Sie in diesem Fall ausschließlich Änderungs- und Leseberechtigungen.
* Setzen Sie „Ablehnen“ sparsam ein. Verwenden Sie, soweit möglich, nur „Zulassen“.

  Die Verwendung von „Ablehnen“ kann unerwartete Folgen haben, wenn die Berechtigungen in einer anderen Reihenfolge als der erwarteten angewendet werden. Ist eine Person Mitglied in mehr als einer Gruppe, kann die Anweisung „Ablehnen“ einer Gruppe die Anweisung „Zulassen“ einer anderen Gruppe aufheben und umgekehrt. Es ist schwierig, einen Überblick zu behalten, wenn so etwas passiert, und es kann leicht zu unvorhergesehenen Ergebnissen führen. Durch Zuweisung von „Zulassen“ lassen sich solche Konflikte hingegen ausschließen.

  Adobe empfiehlt, „Zulassen“ statt „Ablehnen“ zu verwenden. Siehe [Best Practices](#best-practices).

Bevor Sie eine der Berechtigungen ändern, sollten Sie wissen, wie sie funktionieren und miteinander in Beziehung stehen. Informationen darüber, wie AEM WCM [Zugriffsrechte bewertet](/help/sites-administering/user-group-ac-admin.md#how-access-rights-are-evaluated), sowie Beispiele zum Einrichten von Zugriffssteuerungslisten finden Sie in der CRX-Dokumentation.

### Berechtigungen {#permissions}

Durch Berechtigungen erhalten Benutzende und Gruppen Zugriff auf AEM-Funktionen von AEM-Seiten.

Berechtigungen werden pfadweise durch Ein-/Ausblenden der Knoten durchsucht. Außerdem können Sie die Vererbung von Berechtigungen bis zum Stammknoten nachverfolgen.

Um Berechtigungen zuzulassen oder abzulehnen, aktivieren bzw. deaktivieren Sie die entsprechenden Kontrollkästchen.

![cqsecuritypermissionstab](assets/cqsecuritypermissionstab.png)

### Anzeigen detaillierter Berechtigungsinformationen {#viewing-detailed-permission-information}

Zusammen mit der Rasteransicht bietet AEM eine detaillierte Ansicht der Berechtigungen für ausgewählte Benutzende/Gruppen unter einem bestimmten Pfad. Die Detailansicht enthält zusätzliche Informationen.

Neben der Anzeige von Informationen können Sie auch aktuelle Benutzende oder die aktuelle Gruppe aus einer Gruppe ein- oder ausschließen. Siehe [Hinzufügen von Benutzenden oder Gruppen beim Hinzufügen von Berechtigungen](#adding-users-or-groups-while-adding-permissions). Hier durchgeführte Änderungen werden sofort im oberen Abschnitt der Detailansicht wiedergegeben.

Zum Aufrufen der Detailansicht klicken Sie für beliebige Gruppen/Benutzende und Pfad auf der Registerkarte **Berechtigungen** auf **Details**.

![permissiondetails](assets/permissiondetails.png)

Die Details werden in zwei voneinander getrennten Bereichen angezeigt:

<table>
 <tbody>
  <tr>
   <td>Oberer Teil</td>
   <td><p>Wiederholt die Informationen, die Sie im Strukturraster sehen. Ein Symbol zeigt für jede Aktion an, ob sie zulässig oder verweigert ist:</p>
    <ul>
     <li>Kein Symbol = kein deklarierter Eintrag</li>
     <li>(Häkchen) = deklarierte Aktion (zulässig)</li>
     <li>(-) = deklarierte Aktion (verweigert)</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Unterer Teil</td>
   <td><p>Zeigt das Raster der Benutzenden bzw. Gruppen an, das folgende Funktionen hat:</p>
    <ul>
     <li>Deklariert einen Eintrag für den angegebenen Pfad UND</li>
     <li>ist die angegebene Autorisierung ODER ist eine Gruppe</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### Stellvertretendes Agieren für andere Benutzende {#impersonating-another-user}

Mit der Funktion [Stellvertretend agieren](/help/sites-authoring/user-properties.md#user-settings) können Benutzende im Auftrag anderer Benutzender arbeiten.

Das heißt, ein Benutzerkonto kann andere Konten angeben, die mit seinem Konto arbeiten können. Wenn beispielsweise Person B stellvertretend für Person A agieren darf, kann Person B mit den vollständigen Kontodetails von Person A agieren.

Mit dieser Funktion können Stellvertreter-Konten Aufgaben so erledigen, als ob sie das Konto benutzen würden, für das sie sich ausgeben. Zum Beispiel bei Abwesenheit oder kurzfristiger Lastverteilung.

>[!NOTE]
>
>Um stellvertretend für Benutzende ohne Adminrechte arbeiten zu können, muss die stellvertretende Person (im obigen Fall Person B) über LESE-Berechtigungen im Pfad `/home/users` verfügen.
>
>Siehe [Berechtigungen in AEM](/help/sites-administering/security.md#permissions-in-aem).

>[!CAUTION]
>
>Wenn ein Konto stellvertretend für ein anderes Konto agiert, ist dies nur schwer zu erkennen. Im Auditprotokoll wird zwar ein Eintrag eingefügt, wann die Stellvertretung beginnt und endet. Die anderen Protokolldateien (wie das Zugriffsprotokoll) enthalten jedoch keine Informationen darüber, dass Ereignisse stellvertretend ausgeführt wurden. Wenn also Person B stellvertretend für Person A agiert, sehen alle Ereignisse so aus, als ob Person A sie ausgeführt hätte.

>[!CAUTION]
>
>Wird stellvertretend für andere Benutzende agiert, ist es möglich, eine Seite zu sperren. Eine auf diese Weise gesperrte Seite kann nur von der Person, für die stellvertretend agiert wurde, oder von einer Person mit Administratorrechten entsperrt werden.
>
>Seiten können nicht entsperrt werden, indem man sich als die Person ausgibt, der die Seite gesperrt hat.

### Best Practices {#best-practices}

Im Folgenden werden Best Practices für die Arbeit mit Berechtigungen und Rechten beschrieben:

| Regel | Grund |
|--- |--- |
| *Benutzergruppen* | Vermeiden Sie es, Zugriffsrechte einzelnen Benutzenden zuzuweisen. Für diesen Ratschlag gibt es mehrere Gründe:<ul><li>Da es viel mehr Benutzende als Gruppen gibt, vereinfachen Gruppen die Struktur.</li><li>Gruppen bieten Ihnen einen Überblick über alle Konten.</li> <li>Die Vererbung bei Gruppen ist einfacher.</li><li>Benutzer wechseln häufiger. Gruppen sind auf Langfristigkeit ausgelegt.</li></ul> |
| *Zulassen statt verweigern* | Verwenden Sie immer Anweisungen vom Typ „Zulassen“, um die Rechte einer Gruppe festzulegen (sofern möglich). Vermeiden Sie Anweisungen vom Typ „Ablehnen“. Gruppen werden der Reihe nach bewertet. Diese Reihenfolge kann je nach Benutzenden unterschiedlich definiert sein. Mit anderen Worten: Sie haben womöglich nur wenig Kontrolle über die Reihenfolge, in der die Anweisungen implementiert und bewertet werden. Wenn Sie ausschließlich Anweisungen vom Typ „Zulassen“ verwenden, spielt die Reihenfolge keine Rolle. |
| *Einfach halten* | Es lohnt sich, etwas Zeit und Überlegung in die Konfiguration einer neuen Installation zu investieren. Die Anwendung einer klaren Struktur vereinfacht die laufende Pflege und Verwaltung und stellt sicher, dass sowohl Ihre jetzigen Kolleginnen und Kollegen als auch Ihre zukünftigen Nachfolgenden leicht verstehen können, was implementiert wird. |
| *Test* | Verwenden Sie zum Üben eine Testinstallation, um sicherzustellen, dass Sie die Beziehungen zwischen den verschiedenen Benutzenden sowie Gruppen verstehen. |
| *Standardbenutzende/Gruppen* | Aktualisieren Sie die Standardbenutzenden und -gruppen immer sofort nach der Installation, um Sicherheitsprobleme zu vermeiden. |

## Verwalten von Benutzenden und Gruppen {#managing-users-and-groups}

Zu den Benutzenden gehören Personen, die das System verwenden, und Fremdsystemen, die Anforderungen an das System stellen.

Eine Gruppe beinhaltet mehrere Benutzende.

Beide können über die Funktion „Benutzerverwaltung“ in der Sicherheitskonsole konfiguriert werden.

### Zugriff auf die Benutzerverwaltung über die Sicherheitskonsole {#accessing-user-administration-with-the-security-console}

Sie können über die Sicherheitskonsole auf alle Benutzenden, Gruppen und zugehörigen Berechtigungen zugreifen. Alle in diesem Abschnitt beschriebenen Verfahren werden in diesem Fenster durchgeführt.

Führen Sie einen der folgenden Schritte aus, um auf AEM WCM-Sicherheit zuzugreifen:

* Klicken Sie im Begrüßungsbildschirm oder in verschiedenen anderen Bereichen in AEM auf das Sicherheitssymbol:

![Registerkarte „AEM-WCM-Sicherheit“](do-not-localize/wcmtoolbar.png)

* Navigieren Sie direkt zu `https://<server>:<port>/useradmin`. Achten Sie darauf, sich als Admin bei AEM anzumelden.

Es wird folgendes Fenster angezeigt:

![cqsecuritypage](assets/cqsecuritypage.png)

In der linken Struktur werden alle Benutzenden und Gruppen aufgelistet, die sich derzeit im System befinden. Sie können die anzuzeigenden Spalten auswählen, den Inhalt der Spalten sortieren und die Anzeigereihenfolge der Spalten ändern, indem Sie die Spaltenüberschrift an eine neue Position ziehen.

![cqsecuritycolumncontext](assets/cqsecuritycolumncontext.png)

Über die Registerkarten können Sie auf verschiedene Konfigurationen zugreifen:

<!-- ??? in table below. -->

| Registerkarte | Beschreibung |
|--- |--- |
| Filterfeld | Ein Mechanismus zum Filtern der aufgelisteten Benutzenden, Gruppen oder beides. Siehe [Filtern von Benutzenden und Gruppen](#filtering-users-and-groups). |
| Benutzende ausblenden | Ein Umschalter, der alle aufgelisteten Einzelpersonen ausblendet, sodass nur Gruppen verbleiben. Siehe [Ausblenden von Benutzenden und Gruppen](#hiding-users-and-groups). |
| Gruppen ausblenden | Ein Umschalter, mit dem alle aufgelisteten Gruppen ausgeblendet werden, sodass nur Einzelpersonen verbleiben. Siehe [Ausblenden von Benutzenden und Gruppen](#hiding-users-and-groups). |
| Bearbeiten | Ein Menü, über das Sie Benutzende oder Gruppen erstellen und löschen sowie aktivieren und deaktivieren können. Siehe [Erstellen von Benutzenden und Gruppen](#creating-users-and-groups) und [Löschen von Benutzenden und Gruppen](#deleting-users-and-groups). |
| Eigenschaften | Listet Informationen über Benutzenden oder eine Gruppe auf, z. B. E-Mail-Adresse, Beschreibung und Namen. Außerdem können Sie das Passwort einer Benutzerin oder eines Benutzers ändern. Siehe [Erstellen von Benutzenden und Gruppen](#creating-users-and-groups), [Ändern von Benutzer- und Gruppeneigenschaften](#modifying-user-and-group-properties) und [Ändern von Benutzerkennwörtern](#changing-a-user-password). |
| Gruppen | Listet alle Gruppen auf, denen die/der ausgewählte Benutzende oder die ausgewählte Gruppe angehört. Sie können die/den ausgewählte(n) Benutzenden oder die ausgewählte Gruppe zusätzlichen Gruppen zuweisen oder aus Gruppen entfernen. Siehe [Gruppen](#adding-users-or-groups-to-a-group). |
| Mitglieder | Nur für Gruppen verfügbar. Es werden nur die Mitglieder einer bestimmten Gruppe aufgeführt. Siehe [Mitglieder](#members-adding-users-or-groups-to-a-group). |
| Berechtigungen | Sie können Benutzenden oder Gruppen Berechtigungen zuweisen. Hiermit können Sie Folgendes steuern:<ul><li>Berechtigungen für bestimmte Seiten/Knoten. Siehe [Festlegen von Zugriffsberechtigungen](#setting-permissions). </li><li>Berechtigungen zum Erstellen und Löschen von Seiten und zum Ändern der Hierarchie. Sie können [Berechtigungen zuweisen](#settingprivileges), z. B. Hierarchieänderung, mit denen Sie Seiten erstellen und löschen können.</li><li>Berechtigungen im Zusammenhang mit [Replikationsberechtigungen](#setting-replication-privileges) (normalerweise von der Autoren- zur Veröffentlichungsinstanz) anhand eines Pfads.</li></ul> |
| Stellvertretender | Ermöglicht es anderen Benutzenden, die Identität des Kontos zu übernehmen. Dies ist nützlich, wenn ein/e Benutzende stellvertretend für andere agieren soll. Siehe [Stellvertretendes Agieren für Benutzende](#impersonating-another-user). |
| Voreinstellungen | Legt [Voreinstellungen für die Gruppe oder Benutzende](#setting-user-and-group-preferences) fest, etwa Sprachvoreinstellungen. |

### Filtern von Benutzenden und Gruppen {#filtering-users-and-groups}

Sie können die Liste durch Eingabe eines Filterausdrucks filtern, der alle nicht dem Ausdruck entsprechenden Benutzende und Gruppen ausblendet. Sie können Benutzende sowie Gruppen auch über die Schaltflächen [„Benutzende ausblenden“ und „Gruppen ausblenden“](#hiding-users-and-groups) ausblenden.

So filtern Sie Benutzende oder Gruppen:

1. Geben Sie in der linken Strukturliste Ihren Filterausdruck in das bereitgestellte Feld ein. Wenn Sie zum Beispiel **admin** eingeben, werden alle Benutzenden und Gruppen angezeigt, die diese Zeichenfolge enthalten.
1. Klicken Sie auf die Lupe, um die Liste zu filtern.

   ![cqsecurityfilter](assets/cqsecurityfilter.png)

1. Klicken Sie auf **x**, um alle Filter zu entfernen.

### Ausblenden von Benutzenden und Gruppen {#hiding-users-and-groups}

Das Ausblenden von Benutzenden oder Gruppen ist eine weitere Möglichkeit, die Liste aller Benutzenden und Gruppen in einem System zu filtern. Es gibt zwei Umschaltmechanismen. Wenn Sie auf „Benutzer ausblenden“ klicken, werden alle Einzelpersonen ausgeblendet, und wenn Sie auf „Gruppen ausblenden“ klicken, werden alle Gruppen ausgeblendet (Sie können nicht gleichzeitig alle Einzelpersonen und Gruppen ausblenden). Informationen zum Filtern der Liste mithilfe eines Filterausdrucks finden Sie unter [Filtern von Benutzenden und Gruppen](#filtering-users-and-groups).

So blenden Sie Benutzende und Gruppen aus:

1. Klicken Sie in der Konsole **Sicherheit** auf **Benutzer ausblenden** oder **Gruppen ausblenden**. Die ausgewählte Schaltfläche wird hervorgehoben.

   ![cqsecurityhideusers](assets/cqsecurityhideusers.png)

1. Damit die Benutzenden bzw. Gruppen wieder angezeigt werden, klicken Sie erneut auf die entsprechende Schaltfläche.

### Erstellen von Benutzenden und Gruppen {#creating-users-and-groups}

So erstellen Sie eine Benutzerin bzw. einen Benutzer oder eine Gruppe:

1. Klicken Sie in der Strukturliste der **Sicherheitskonsole** auf **Bearbeiten** und dann entweder auf **Benutzende erstellen** oder **Gruppe erstellen**.

   ![cqseruityeditcontextmenu](assets/cqseruityeditcontextmenu.png)

1. Geben Sie die erforderlichen Details ein, je nachdem, ob Sie eine Benutzerin bzw. einen Benutzer oder eine Gruppe erstellen.

   * Bei Auswahl von **Benutzer erstellen** geben Sie die Anmeldungskennung, den Vor- und Nachnamen, die E-Mail-Adresse und ein Passwort ein. Standardmäßig erstellt AEM einen Pfad basierend auf dem ersten Buchstaben des Nachnamens. Sie können aber auch einen anderen Pfad festlegen.

   ![createuserdialog](assets/createuserdialog.png)

   * Bei Auswahl von **Gruppe erstellen** geben Sie eine Gruppenkennung und eine optionale Beschreibung ein.

   ![creategroupdialog](assets/creategroupdialog.png)

1. Klicken Sie auf **Erstellen**. Die von Ihnen erstellte Einzelperson bzw. Gruppe wird in der Strukturliste angezeigt.

### Löschen von Benutzenden und Gruppen {#deleting-users-and-groups}

So löschen Sie Benutzende oder eine Gruppe:

1. Wählen Sie in der **Sicherheitskonsole** die zu löschende Person bzw. Gruppe aus. Wenn mehrere Elemente gelöscht werden sollen, wählen Sie diese durch Klicken bei gedrückter Umschalt- oder Strg-Taste aus.
1. Klicken Sie auf **Bearbeiten** und wählen Sie dann „Löschen“. AEM WCM fragt, ob Sie die Person bzw. Gruppe löschen möchten.
1. Klicken Sie auf **OK** zum Bestätigen oder auf „Abbrechen“.

### Ändern von Benutzer- und Gruppeneigenschaften {#modifying-user-and-group-properties}

So ändern Sie Benutzer- und Gruppeneigenschaften:

1. Doppelklicken Sie in der **Sicherheitskonsole** auf den Namen der/des zu ändernden Benutzenden bzw. der zu ändernden Gruppe.

1. Klicken Sie auf die Registerkarte **Eigenschaften**, nehmen Sie die erforderlichen Änderungen vor und klicken Sie auf **Speichern**.

   ![cqsecurityuserprops](assets/cqsecurityuserprops.png)

>[!NOTE]
>
>Der Pfad der/des Benutzenden wird unten in den Benutzereigenschaften angezeigt. Er ist unveränderbar.

### Ändern von Benutzerkennwörtern {#changing-a-user-password}

Gehen Sie wie folgt vor, um das Passwort einer/eines Benutzenden zu ändern.

>[!NOTE]
>
>Das Admin-Passwort kann nicht über die Sicherheitskonsole geändert werden. Um das Passwort für das Admin-Konto zu ändern, verwenden Sie die unter „Granite-Vorgänge“ bereitgestellte [Benutzerkonsole](/help/sites-administering/granite-user-group-admin.md#changing-the-password-for-an-existing-user).
>
>Wenn Sie AEM Forms on JEE verwenden, verwenden Sie nicht die folgenden Anweisungen, um das Passwort zu ändern, sondern die Admin Console von AEM Forms on JEE (/adminui).

1. Doppelklicken Sie in der **Sicherheitskonsole** auf den Namen der/des Benutzenden, deren bzw. dessen Passwort geändert werden soll.
1. Klicken Sie auf die Registerkarte **Eigenschaften** (sofern noch nicht aktiv).
1. Klicken Sie auf **Kennwort festlegen**. Daraufhin wird das Fenster „Kennwort festlegen“ geöffnet, in dem Sie das Kennwort ändern können.

   ![cqsecurityuserpassword](assets/cqsecurityuserpassword.png)

1. Geben Sie das neue Passwort zweimal ein. Da es nicht als Klartext angezeigt wird, dient diese Aktion der Bestätigung, und wenn die Eingaben nicht übereinstimmen, zeigt das System einen Fehler an.
1. Klicken Sie auf **Festlegen**, um das neue Passwort für das Konto zu aktivieren.

### Hinzufügen von Benutzenden oder Gruppen zu einer Gruppe {#adding-users-or-groups-to-a-group}

AEM bietet drei verschiedene Möglichkeiten, Benutzende oder Gruppen zu einer vorhandenen Gruppe hinzuzufügen:

* Wenn Sie sich in der Gruppe befinden, können Sie Mitglieder hinzufügen (entweder Benutzende oder Gruppen).
* Über das Mitgliederprofil können Sie Mitglieder zu Gruppen hinzufügen.
* Wenn Sie an Berechtigungen arbeiten, können Sie Mitglieder zu Gruppen hinzufügen.

### Gruppen – Hinzufügen von Benutzenden oder Gruppen zu einer Gruppe {#groups-adding-users-or-groups-to-a-group}

Auf der Registerkarte **Gruppen** wird angezeigt, zu welchen Gruppen das aktuelle Konto gehört. Sie können damit das ausgewählte Konto zu einer Gruppe hinzufügen:

1. Doppelklicken Sie auf den Namen des Kontos (Einzelperson oder Gruppe), das Sie einer Gruppe zuweisen möchten.
1. Klicken Sie auf die Registerkarte **Gruppen**. Es wird eine Liste der Gruppen angezeigt, zu denen das Konto bereits gehört.
1. Klicken Sie in der Strukturliste auf den Namen der Gruppe, die Sie dem Konto hinzufügen möchten, und ziehen Sie sie in den Bereich **Gruppen**. (Wenn Sie mehrere Benutzende hinzufügen möchten, klicken Sie bei gedrückter Umschalt- oder Strg-Taste auf die entsprechenden Namen und ziehen Sie sie erst dann.)

   ![cqsecurityaddusertogroup](assets/cqsecurityaddusertogroup.png)

1. Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

### Mitglieder – Hinzufügen von Benutzenden oder Gruppen zu einer Gruppe {#members-adding-users-or-groups-to-a-group}

Auf der Registerkarte **Mitglieder**, die nur für Gruppen verwendet werden kann, wird angezeigt, welche Benutzenden und Gruppen zur aktuellen Gruppe gehören. Sie können damit Konten zu einer Gruppe hinzufügen:

1. Doppelklicken Sie auf den Namen der Gruppe, der Sie Mitglieder hinzufügen möchten.
1. Klicken Sie auf die Registerkarte **Mitglieder**. Es wird eine Liste der Mitglieder angezeigt, die bereits zu dieser Gruppe gehören.
1. Klicken Sie in der Strukturliste auf den Namen des Mitglieds, das der Gruppe hinzugefügt werden soll, und ziehen Sie das Mitglied in den Bereich **Mitglieder**. (Wenn Sie mehrere Benutzende hinzufügen möchten, klicken Sie bei gedrückter Umschalt- oder Strg-Taste auf die entsprechenden Namen und ziehen Sie sie erst dann.)

   ![cqsecurityadduserasmember](assets/cqsecurityadduserasmember.png)

1. Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

### Hinzufügen von Benutzenden oder Gruppen beim Hinzufügen von Berechtigungen {#adding-users-or-groups-while-adding-permissions}

So fügen Sie einer Gruppe unter einem bestimmten Pfad Mitglieder hinzu:

1. Doppelklicken Sie auf den Namen der Gruppen oder Benutzenden, denen Benutzende hinzugefügt werden sollen.

1. Klicken Sie auf die Registerkarte **Berechtigungen**.

1. Navigieren Sie zu dem Pfad, dem Berechtigungen hinzugefügt werden sollen, und klicken Sie auf **Details**. Im unteren Abschnitt des Detailfensters finden Sie Informationen darüber, wer Berechtigungen für diese Seite besitzt.

   ![chlimage_1-113](assets/chlimage_1-113.png)

1. Markieren Sie in der Spalte **Mitglied** das Kontrollkästchen bei den Mitgliedern, denen Sie für diesen Pfad Berechtigungen gewähren möchten. Deaktivieren Sie das Kontrollkästchen bei den Mitgliedern, denen Sie Berechtigungen entziehen möchten. In der Zelle, die Sie geändert haben, wird ein rotes Dreieck angezeigt.
1. Klicken Sie auf **OK**, um die Änderungen zu speichern.

### Entfernen von Benutzenden oder Gruppen aus Gruppen {#removing-users-or-groups-from-groups}

AEM bietet drei Möglichkeiten, Benutzende oder Gruppen aus einer Gruppe zu entfernen:

* Wenn Sie sich im Gruppenprofil befinden, können Sie Mitglieder (Benutzende oder Gruppen) entfernen.
* Wenn Sie sich im Mitgliederprofil befinden, können Sie Mitglieder aus Gruppen entfernen.
* Wenn Sie an Berechtigungen arbeiten, können Sie Mitglieder aus Gruppen entfernen.

### Gruppen – Entfernen von Benutzenden oder Gruppen aus Gruppen {#groups-removing-users-or-groups-from-groups}

So entfernen Sie ein Benutzer- oder Gruppenkonto aus einer Gruppe:

1. Doppelklicken Sie auf den Namen der Gruppe oder des Benutzerkontos, die bzw. das aus einer Gruppe entfernt werden soll.
1. Klicken Sie auf die Registerkarte **Gruppen**. Sie sehen, zu welchen Gruppen das ausgewählte Konto gehört.
1. Klicken Sie im Bereich **Gruppen** auf den Namen der Person oder Gruppe, die Sie aus der Gruppe entfernen möchten, und klicken Sie auf **Entfernen**. (Wenn mehrere Konten entfernt werden sollen, klicken Sie bei gedrückter Umschalt- oder Strg-Taste auf die entsprechenden Namen und dann auf **Entfernen**.)

   ![cqsecurityremoveuserfromgrp](assets/cqsecurityremoveuserfromgrp.png)

1. Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

### Mitglieder – Entfernen von Benutzenden oder Gruppen aus Gruppen {#members-removing-users-or-groups-from-groups}

So entfernen Sie Konten aus einer Gruppe:

1. Doppelklicken Sie auf den Namen der Gruppe, aus der Sie Mitglieder entfernen möchten.
1. Klicken Sie auf die Registerkarte **Mitglieder**. Es wird eine Liste der Mitglieder angezeigt, die bereits zu dieser Gruppe gehören.
1. Klicken Sie im Fensterbereich **Mitglieder** auf den Namen des Mitglieds, das Sie aus der Gruppe entfernen möchten, und klicken Sie auf **Entfernen**. (Wenn Sie mehrere Benutzende entfernen möchten, klicken Sie bei gedrückter Umschalttaste oder bei gedrückter Strg-Taste auf diese Namen und erst dann auf **Entfernen**).

   ![cqsecurityremovemember](assets/cqsecurityremovemember.png)

1. Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

### Entfernen von Benutzenden oder Gruppen beim Hinzufügen von Berechtigungen {#removing-users-or-groups-while-adding-permissions}

So entfernen Sie Mitglieder aus einer Gruppe unter einem bestimmten Pfad:

1. Doppelklicken Sie auf den Namen der Gruppen oder der Benutzenden, für die Benutzende entfernt werden sollen.

1. Klicken Sie auf die Registerkarte **Berechtigungen**.

1. Navigieren Sie zu dem Pfad, dem Sie die Berechtigungen entziehen möchten, und klicken Sie auf **Details**. Im unteren Abschnitt des Detailfensters finden Sie Informationen darüber, wer Berechtigungen für diese Seite besitzt.

   ![chlimage_1-114](assets/chlimage_1-114.png)

1. Markieren Sie in der Spalte **Mitglied** das Kontrollkästchen bei den Mitgliedern, denen Sie für diesen Pfad Berechtigungen gewähren möchten. Deaktivieren Sie das Kontrollkästchen bei den Mitgliedern, denen Sie Berechtigungen entziehen möchten. In der Zelle, die Sie geändert haben, wird ein rotes Dreieck angezeigt.
1. Klicken Sie auf **OK**, um die Änderungen zu speichern.

### Benutzersynchronisierung {#user-synchronization}

Wenn es sich bei der Bereitstellung um eine [Veröffentlichungsfarm](/help/sites-deploying/recommended-deploys.md#tarmk-farm) handelt, müssen Benutzende sowie Gruppen auf allen Veröffentlichungsknoten synchronisiert werden.

Informationen zur Benutzersynchronisierung und deren Aktivierung finden Sie unter [Benutzersynchronisierung](/help/sites-administering/sync.md).

## Verwalten von Berechtigungen {#managing-permissions}

>[!NOTE]
>
>Adobe hat eine neue Hauptansicht für die Berechtigungsverwaltung eingeführt, die auf einer Touch-optimierten Benutzeroberfläche basiert. Weitere Informationen zu ihrer Verwendung finden Sie [auf dieser Seite](/help/sites-administering/touch-ui-principal-view.md).

Dieser Abschnitt beschreibt, wie Berechtigungen, darunter auch die zur Replikation, festgelegt werden.

### Festlegen von Berechtigungen {#setting-permissions}

Berechtigungen erlauben es Benutzenden, bestimmte Aktionen auf Ressourcen in bestimmten Pfaden durchzuführen. Dazu gehört auch das Erstellen oder Löschen von Seiten.

So fügen Sie Berechtigungen hinzu bzw. ändern oder löschen diese:

1. Doppelklicken Sie in der **Sicherheitskonsole** auf den Namen der/des Benutzenden bzw. der Gruppe, für den bzw. die Berechtigungen festgelegt werden sollen, oder [suchen Sie nach Knoten](#searching-for-nodes).

1. Klicken Sie auf die Registerkarte **Berechtigungen**.

   ![cquserpermissions](assets/cquserpermissions.png)

1. Aktivieren Sie im Strukturraster das entsprechende Kontrollkästchen, um zuzulassen, dass die ausgewählte Benutzerin, der ausgewählte Benutzer oder die ausgewählte Gruppe eine Aktion durchführen kann, oder deaktivieren Sie das entsprechende Kontrollkästchen, um dies abzulehnen. Um weitere Informationen zu erhalten, klicken Sie auf **Details**.

1. Klicken Sie abschließend auf **Speichern**.

### Festlegen von Replikationsberechtigungen {#setting-replication-privileges}

Die Replikationsberechtigung bezeichnet das Recht zur Veröffentlichung von Inhalten. Sie kann für Gruppen und Benutzende festgelegt werden.

>[!NOTE]
>
>* Sämtliche auf eine Gruppe angewendeten Replikationsrechte gelten für alle Benutzenden dieser Gruppe.
>* Die Replikationsberechtigungen einer Einzelperson haben Vorrang vor den Replikationsberechtigungen einer Gruppe.
>* Die Replikationsberechtigungen „Zulassen“ haben Vorrang vor den Replikationsberechtigungen „Ablehnen“. Weitere Informationen finden Sie unter [Berechtigungen in AEM](#permissions-in-aem).
>

So legen Sie Replikationsberechtigungen fest:

1. Wählen Sie die Einzelperson oder Gruppe aus der Liste aus, doppelklicken Sie zum Öffnen und klicken Sie auf **Berechtigungen**.
1. Navigieren Sie im Raster zu dem Pfad, unter dem die/der Benutzende Replikationsberechtigungen besitzen soll, oder [suchen Sie nach Knoten.](#searching-for-nodes)

1. Aktivieren Sie in der Spalte **Replizieren** im ausgewählten Pfad das Kontrollkästchen, um eine Replikationsberechtigung für diese Benutzerin, diesen Benutzer oder diese Gruppe hinzuzufügen, oder deaktivieren Sie das Kontrollkästchen, um die Replikationsberechtigung aufzuheben. In AEM wird ein rotes Dreieck dort angezeigt, wo Sie Änderungen vorgenommen, aber noch nicht gespeichert haben.

   ![cquserreplicatepermissions](assets/cquserreplicatepermissions.png)

1. Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

### Suchen nach Knoten {#searching-for-nodes}

Beim Hinzufügen oder Entfernen von Berechtigungen können Sie Knoten durchsuchen oder nach Knoten suchen.

Es gibt zwei verschiedene Typen von Pfadsuchvorgängen:

* Pfadsuche – Wenn die Suchzeichenfolge mit „/“ beginnt, wird nach den direkt untergeordneten Knoten des angegebenen Pfads gesucht:

![cqsecuritypathsearch](assets/cqsecuritypathsearch.png)

Im Suchfeld stehen Ihnen folgende Möglichkeiten zur Verfügung:

| Aktion | Funktion |
|--- |--- |
| Nach-rechts-Taste | Wählt einen Unterknoten im Suchergebnis aus |
| Nach-unten-Taste | Startet die Suche erneut. |
| Eingabetaste | Wählt einen Unterknoten aus und lädt ihn in das Strukturraster. |

* Volltextsuche – Wenn die Suchzeichenfolge nicht mit „/“ beginnt, wird eine Volltextsuche in allen Knoten unter dem Pfad /content ausgeführt.

![cqsecurityfulltextsearch](assets/cqsecurityfulltextsearch.png)

So führen Sie eine Pfad- oder Volltextsuche durch:

1. Wählen Sie in der Sicherheitskonsole eine Benutzerin, einen Benutzer oder eine Gruppe aus und klicken Sie dann auf die Registerkarte **Berechtigungen**.

1. Geben Sie einen Suchbegriff in das Suchfeld ein.

### Stellvertretendes Agieren für Benutzende {#impersonating-users}

Sie können eine oder mehrere Personen angeben, die stellvertretend für die aktuelle Person agieren dürfen. Diese Fähigkeit bedeutet, dass diese ihre Kontoeinstellungen auf die der aktuellen Person umstellen und im Namen dieser Person handeln können.

Seien Sie beim Verwenden dieser Funktion vorsichtig, da sie es Benutzenden ermöglicht, Aktionen durchzuführen, zu denen sie selbst nicht berechtigt sind. Wenn Benutzende für eine andere Person stellvertretend agieren, werden sie benachrichtigt, dass sie nicht mit dem eigenen Profil angemeldet sind.

Es gibt verschiedene Szenarien, in denen Sie diese Funktion verwenden können, darunter:

* Wenn Sie nicht im Büro sind, können Sie während Ihrer Abwesenheit eine andere Person stellvertretend agieren lassen. Mithilfe dieser Funktion können Sie sicherstellen, dass eine andere Person über Ihre Zugriffsrechte verfügt und Sie weder ein Benutzerprofil ändern noch Ihr Passwort herausgeben müssen.
* Sie können die Funktion zum Debuggen verwenden, Zum Beispiel, um zu sehen, wie die Website für Benutzende mit eingeschränkten Zugriffsrechten aussieht. Wenn eine Person technische Probleme meldet, können Sie außerdem stellvertretend für diese Person agieren, um das Problem zu diagnostizieren und zu beheben.

So agieren Sie stellvertretend für vorhandene Benutzende:

1. Wählen Sie in der Strukturliste den Namen der Person aus, der andere Benutzende zum stellvertretenden Agieren zugewiesen werden sollen. Doppelklicken Sie zum Öffnen darauf.
1. Klicken Sie auf die Registerkarte **Darsteller**.
1. Klicken Sie auf die Person, der stellvertretend für die ausgewählte Person agieren soll. Ziehen Sie die Person (die stellvertretend agieren wird) aus der Liste in den Bereich „Darsteller“. Der Name wird in der Liste angezeigt.

   ![chlimage_1-115](assets/chlimage_1-115.png)

1. Klicken Sie auf **Speichern**.

### Festlegen von Benutzer- und Gruppeneinstellungen {#setting-user-and-group-preferences}

So legen Sie Benutzer- und Gruppenvoreinstellungen fest, einschließlich Voreinstellungen für die Sprache, Fensterverwaltung und Symbolleiste:

1. Wählen Sie in der linken Struktur die Person bzw. Gruppe aus, deren Voreinstellungen geändert werden sollen. Um mehrere Personen oder Gruppen auszuwählen, klicken Sie bei gedrückter Strg- oder Umschalttaste.
1. Klicken Sie auf die Registerkarte **Voreinstellungen**.

   ![cqsecurityPreferences](assets/cqsecuritypreferences.png)

1. Nehmen Sie nach Bedarf Änderungen an den Gruppen- oder Benutzereinstellungen vor und klicken Sie abschließend auf **Speichern**.

### Einrichten von Benutzenden oder Admins mit der Berechtigung zum Verwalten anderer Benutzender {#setting-users-or-administrators-to-have-the-privilege-to-manage-other-users}

So richten Sie Benutzende oder Admins mit Berechtigungen zum Löschen/Aktivieren/Deaktivieren anderer Benutzenden ein:

1. Fügen Sie die Person, die zum Verwalten anderer Benutzender berechtigt werden soll, der Administratorgruppe hinzu und speichern Sie Ihre Änderungen.

   ![cqsecurityaddmembertoadmin](assets/cqsecurityaddmembertoadmin.png)

1. Navigieren Sie auf der Registerkarte **Berechtigungen** der Benutzerin oder des Benutzers zu „/“ und aktivieren Sie in der Spalte „Replizieren“ das Kontrollkästchen zum Zulassen einer Replikation unter „/“. Klicken Sie dann auf **Speichern**.

   ![cqsecurityreplicatepermissions](assets/cqsecurityreplicatepermissions.png)

   Die ausgewählte Person kann jetzt Benutzende deaktivieren, aktivieren, löschen und erstellen.

### Erweitern von Berechtigungen auf Projektebene {#extending-privileges-on-a-project-level}

Wenn Sie planen, anwendungsspezifische Berechtigungen zu implementieren, wird in den folgenden Informationen beschrieben, was Sie wissen müssen, um eine benutzerdefinierte Berechtigung zu implementieren, und wie Sie sie in CQ durchsetzen können:

Die Berechtigung zum Ändern der Hierarchie wird von einer Kombination von jcr-Berechtigungen abgedeckt. Die Replikationsberechtigung **crx:replicate** wird mit anderen Berechtigungen im jcr-Repository gespeichert/evaluiert. Sie wird jedoch nicht auf jcr-Ebene durchgesetzt.

Die Definition und Registrierung benutzerdefinierter Berechtigungen sind ab Version 2.4 offizieller Bestandteil der [Jackrabbit-API](https://jackrabbit.apache.org/oak/docs/security/privilege.html) (siehe auch [JCR-2887](https://issues.apache.org/jira/browse/JCR-2887)). Die weitere Verwendung wird über die JCR-Zugriffssteuerungsverwaltung abgedeckt, wie in [JSR 283](https://jcp.org/en/jsr/detail?id=283) (Abschnitt 16) definiert. Außerdem definiert die Jackrabbit-API verschiedene Erweiterungen.

Der Mechanismus zur Berechtigungsregistrierung befindet sich auf der Benutzeroberfläche unter **Repository Configuration**.

Die Registrierung neuer (benutzerdefinierter) Berechtigungen ist selbst durch eine integrierte Berechtigung geschützt, die auf Repository-Ebene erteilt werden muss. In JCR: Übergeben von „null“ als Parameter „absPath“ in der ac-mgt-API; für Details siehe „jsr 333“. Standardmäßig wird diese Berechtigung dem Profil **admin** und allen Mitgliedern der Administratorgruppe erteilt.

>[!NOTE]
>
>Zwar erfolgen im Rahmen der Implementierung sowohl die Validierung als auch die Bewertung der benutzerdefinierten Berechtigungen, durchgesetzt werden sie jedoch nur in Form von Aggregaten integrierter Berechtigungen.
