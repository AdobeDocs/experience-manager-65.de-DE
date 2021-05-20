---
title: Richtlinien erstellen und verwalten
seo-title: Richtlinien erstellen und verwalten
description: Eine Richtlinie definiert einen Satz von Vertraulichkeitseinstellungen und Benutzern, die auf ein Dokument zugreifen dürfen, für das die Richtlinie gilt. Sie können verschiedene Arten von Richtlinien mit AEM Forms erstellen und verwalten.
seo-description: Eine Richtlinie definiert einen Satz von Vertraulichkeitseinstellungen und Benutzern, die auf ein Dokument zugreifen dürfen, für das die Richtlinie gilt. Sie können verschiedene Arten von Richtlinien mit AEM Forms erstellen und verwalten.
uuid: 72be06f3-3e90-495e-8425-72380d95704a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: fa054d30-c7dc-4b64-acf1-cbcbe8827df5
feature: Dokumentensicherheit
exl-id: 5e57451c-1a89-442c-8404-841e95d5ceff
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '4757'
ht-degree: 85%

---

# Richtlinien erstellen und verwalten {#creating-and-managing-policies}

Eine *Richtlinie* definiert einen Satz von Vertraulichkeitseinstellungen und Benutzern, die auf ein Dokument zugreifen dürfen, für das die Richtlinie gilt. Ein *Richtliniensatz* dient zum Gruppieren verschiedener Richtlinien mit einem gemeinsamen Zweck. Diese Richtliniensätze werden meist einer Teilmenge der Benutzer im System zur Verfügung gestellt. Einzelheiten zu den Richtlinien finden Sie unter [Informationen zu Richtlinien und richtliniengeschützte Dokumente](/help/forms/using/admin-help/document-security.md#policies-and-policy-protected-documents).

## Arten von Richtlinien {#types-of-policies}

Document Security bietet folgende Arten von Richtlinien.

**Persönliche Richtlinien**

Benutzer können eigene Richtlinien erstellen, kopieren, löschen und mit für eine bestimmte Situation geeigneten Einstellungen aktivieren. Nur die Person, die eine Richtlinie erstellt, und die Administratoren können auf diese persönliche Richtlinie zugreifen. Persönliche Richtlinien werden auf der Seite „Richtlinien“ auf der Registerkarte „Meine Richtlinien“ angezeigt.

Eingeladene Benutzer können ebenfalls persönliche Richtlinien erstellen, bearbeiten, kopieren und löschen, falls der Administrator diese Funktionalität aktiviert hat.

**Freigegebene Richtlinien**

Administratoren und Richtliniensatzkoordinatoren erstellen freigegebene Richtlinien basierend auf den Vertraulichkeitsanforderungen, die Ihr Unternehmen für verschiedene Typen von Dokumenten und Benutzern bestimmt hat. Freigegebene Richtlinien sind in Richtliniensätzen enthalten und stehen allen autorisierten Benutzern (Dokumentherausgebern, Richtliniensatzkoordinatoren und Dokumentempfängern) für einen bestimmten Richtliniensatz zur Verfügung. Administratoren und Richtliniensatzkoordinatoren können freigegebene Richtlinien aktivieren und deaktivieren. Freigegebene Richtlinien werden auf der Seite „Richtlinien“ auf der Registerkarte „Richtliniensätze“ in Richtliniensätzen angezeigt.

Wenn Sie Document Security zum ersten Mal installieren, enthält das Programm eine freigegebene Richtlinie mit dem Namen *Auf alle Prinzipale beschränken*. Wenn diese Richtlinie auf ein Dokument angewendet wird, kann jeder Benutzer, der sich bei Document Security anmelden kann, auf das Dokument zugreifen. Diese Richtlinie ist im Richtliniensatz *globaler Richtliniensatz* enthalten. In der Standardeinstellung ist diese Richtlinie deaktiviert. Sie können sie entsprechend den Anforderungen Ihrer Organisation aktivieren.

**Microsoft Outlook, automatisch generierte Richtlinien**

Acrobat ermöglicht Ihnen das Anwenden von Richtlinien auf Dokumente, die Sie aus Microsoft Outlook als E-Mail-Anlagen senden. In Outlook können Sie ein Dokument schützen, indem Sie eine vorhandene Richtlinie oder eine automatisch generierte Richtlinie verwenden, die von Acrobat mit Standardvertraulichkeitseinstellungen erzeugt und auf das Dokument angewendet wird, das an die E-Mail-Nachricht angehängt ist. (Weitere Informationen finden Sie in der *[Acrobat-Hilfe](https://help.adobe.com/en_US/acrobat/pro/using/index.html)*.)

>[!NOTE]
>
>Damit eine Richtlinie in Outlook verfügbar ist, müssen Sie die Richtlinie in Acrobat als Favorit festlegen. Alle anderen Richtlinien, einschließlich derer, dessen Herausgeber Sie sind, werden nicht in Outlook angezeigt.

## Wer kann Richtlinien und Richtliniensätze erstellen und verwalten?  {#who-can-create-and-manage-policies-and-policy-sets}

Wie Sie mit Richtlinien und Richtliniensätzen interagieren, hängt von Ihrer Rolle innerhalb des Unternehmens ab:

**Benutzer:** Benutzer können ihre persönlichen Richtlinien erstellen, bearbeiten und löschen. Eingeladene Benutzer können ebenfalls persönliche Richtlinien erstellen, falls der Administrator diese Funktionalität aktiviert hat.

**Richtliniensatzkoordinatoren:**  Richtliniensatzkoordinatoren können freigegebene Richtlinien in den Richtliniensätzen erstellen und verwalten, in denen sie als Koordinator benannt sind. Ein Richtliniensatzkoordinator ist in der Regel ein Spezialist im Unternehmen, der die Richtlinien in einem bestimmten Richtliniensatz am besten verwalten kann.

**Administratoren:** Administratoren können die persönlichen Richtlinien aller Benutzer bearbeiten. Sie können freigegebene Richtlinien erstellen. Sie können ebenfalls Richtliniensätze erstellen, bearbeiten und löschen und Richtliniensatzkoordinatoren angeben. 

Weitere Informationen zu den verschiedenen Document Security-Rollen finden Sie unter [Informationen zu Document Security-Benutzern](/help/forms/using/admin-help/document-security.md#about-document-security-users).

## Richtlinien erstellen und bearbeiten  {#creating-and-editing-policies}

Benutzer können ihre persönlichen Richtlinien für die eigene Verwendung erstellen oder bearbeiten. Administratoren und Richtliniensatzkoordinatoren können freigegebene Richtlinien für Ihr Unternehmen erstellen oder bearbeiten.

### Überlegungen zum Bearbeiten von Richtlinien  {#considerations-for-editing-policies}

Wenn Sie eine Richtlinie bearbeiten, wirken sich die Änderungen auf Dokumente aus, die gegenwärtig und künftig von der Richtlinie geschützt werden. Wenn Sie beispielsweise Empfänger aus einer Richtlinie entfernen, die gegenwärtig für ein Dokument gilt, können die Empfänger das Dokument nicht mehr öffnen.

Der Status des Dokuments bestimmt, wann die Änderung wirksam wird:

* Ist das Dokument online, werden Änderungen sofort übernommen, es sei denn, der Benutzer hat das Dokument geöffnet. In diesem Fall muss der Benutzer das Dokument schließen, damit die Änderungen in Kraft treten.
* Wenn ein Empfänger das Dokument offline verwendet (z. B. auf einem Laptop), werden die Änderungen bei der nächsten Onlineschaltung des Dokuments und Synchronisierung mit Document Security durch Öffnen eines beliebigen richtliniengeschützten Dokuments wirksam.

>[!NOTE]
>
>Richtlinien, die Acrobat automatisch für die Empfänger eines Dokuments generiert, das an eine E-Mail-Nachricht in Microsoft Outlook angehängt ist, werden nicht in der Richtlinienliste angezeigt. Sie können diese Richtlinien nur anzeigen, indem Sie die Seite „Dokumentdetails“ des dazugehörigen Dokuments öffnen.

Für die Bearbeitung von Richtlinien gelten diese Einschränkungen:

* Eingeladene Benutzer können nur Richtlinien bearbeiten, wenn der Administrator diese Funktionalität aktiviert hat. Wenn Sie keine Richtlinien bearbeiten dürfen, wird die Option „Bearbeiten“ nicht angezeigt.
* Richtliniensatzkoordinatoren können Richtlinien nur innerhalb von Richtliniensätzen bearbeiten, für die sie über die ordnungsgemäßen Berechtigungen verfügen. Diese Berechtigungen werden vom Hauptbenutzer oder Richtliniensatzadministrator auf der Document Security-Verwaltungsoberfläche festgelegt.
* Wenn die Richtlinie ein konfiguriertes Wasserzeichen hat, das der Administrator seit der Erstellung der Richtlinie gelöscht hat, wird dieses Wasserzeichen nicht mehr auf Dokumente angewendet, wenn Sie die Richtlinie bearbeiten und speichern. Gelöschte Wasserzeichen bleiben nur für vorhandene Richtlinien aktiviert, solange Sie die Richtlinie nicht bearbeiten. Wenn Sie die Richtlinie bearbeiten, müssen Sie zum Ersetzen des gelöschten Wasserzeichens ein anderes auswählen.
* Sie können keinen anonymen Zugriff auf ein Dokument gewähren, indem Sie die Richtlinie bearbeiten, die gegenwärtig gilt. Wenn Sie die Richtlinie bearbeiten, müssen die Benutzer sich dennoch anmelden, um auf das Dokument zuzugreifen. Um einen anonymen Zugriff auf dieses Dokument zu ermöglichen, müssen Sie zuerst die Richtlinie in der Clientanwendung entfernen und anschließend eine andere Richtlinie anwenden, die einen anonymen Zugriff zulässt.
* Eine Richtlinie, die Acrobat automatisch für die Empfänger eines Dokuments generiert, das an eine E-Mail-Nachricht in Microsoft Outlook angehängt ist, wird nicht in der Richtlinienliste angezeigt. Um auf diese Richtlinien zuzugreifen, suchen Sie das Dokument auf der Seite „Dokumente“, öffnen Sie die Seite „Dokumentdetails“ und klicken Sie auf den Richtliniennamen in der Liste der Dokumentdetails.

**Eine Richtlinie erstellen oder bearbeiten**

1. Klicken Sie auf der Document Security-Seite auf „Richtlinien“ und anschließend auf eine dieser Registerkarten:

   * Um eine persönliche Richtlinie zu erstellen, klicken Sie auf die Registerkarte „Meine Richtlinie“.
   * Um eine freigegebene Richtlinie zu erstellen oder zu bearbeiten (sofern Sie die Berechtigung dazu haben), klicken Sie auf die Registerkarte „Richtliniensätze“, anschließend auf den gewünschten Richtliniensatznamen und dann auf die Registerkarte „Richtlinien“.

1. Klicken Sie auf „Neu“ oder wählen Sie in der Liste die zu bearbeitende Richtlinie aus.
1. Geben Sie in das Feld „Name“ einen Namen ein, der die Richtlinie eindeutig bestimmt. Geben Sie in das Feld „Beschreibung“ den Zweck und Verwendungszeitpunkt der Richtlinie ein. Ist die Richtlinie in einem Richtliniensatz enthalten, wird der Name und die Beschreibung in der Richtlinienliste für alle angegebenen Benutzer angezeigt. Persönliche Richtlinien stehen nur dem jeweiligen Benutzer und den Administratoren zur Verfügung.

   Die folgenden Zeichen dürfen im Namen oder für die Beschreibung nicht verwendet werden:

   * Kleiner-als-Zeichen (&lt;)
   * Größer-als-Zeichen (>)
   * Kaufmännisches Und-Zeichen (&amp;)
   * Einfaches Anführungszeichen (&#39;)
   * Doppeltes Anführungszeichen (&quot;)
   * umgekehrter Schrägstrich (\)
   * Schrägstrich (/)

   Wenn Sie folgende Zeichen im Namen oder in der Beschreibung verwenden, werden diese in Leerzeichen konvertiert:

   * Wagenrücklauf (ASCII-Zeichen 13)
   * Zeilenvorschub (ASCII-Zeichen 10).

   >[!NOTE]
   >
   >Sie können Richtliniennamen erstellen, die erweiterte Zeichen enthalten. Bei einem Vergleich zwischen zwei derartigen Zeichenfolgen werden jedoch Zeichen mit und ohne Akzentzeichen, wie z. B. „e“ und „é“, als identisch bewertet. Beim Erstellen einer Richtlinie wird ein Vergleich durchgeführt, um zu überprüfen, ob bereits eine Richtlinie mit demselben Namen vorhanden ist. Der Vergleich kann nicht zwischen Namen unterscheiden, die sich nur durch Akzentzeichen unterscheiden. Es wird angenommen, dass die Richtlinie bereits zur Datenbank hinzugefügt wurde, sodass die neue nicht hinzugefügt wird.

1. Fügen Sie Benutzer und Gruppen zur Richtlinie hinzu und legen Sie entsprechende Berechtigungen fest. (Siehe [Benutzer und Gruppen](creating-policies.md#users-and-groups).)
1. Wählen Sie unter „Allgemeine Einstellungen“ die passenden Optionen aus: (Siehe [Allgemeine Einstellunen](creating-policies.md#general-settings).)
1. (Optional) Wählen Sie, falls zutreffend, einen externen Autorisierungsanbieter aus und legen Sie dessen Eigenschaften fest. Wenn Sie keinen externen Autorisierungsanbieter verwenden möchten, klicken Sie auf „Standardanbieter entfernen“.

   Der externe Autorisierungsanbieter dient zum Einrichten von Eigenschaften innerhalb der Richtlinie. Falls aktiviert, nutzt der externe Autorisierungsanbieter diese Informationen zum Auswerten der Richtlinie. Diese Eigenschaften werden vom Administrator und der Person konfiguriert, die die Software installiert.

1. Wählen Sie unter „Erweiterte Einstellungen“ die passenden Optionen aus. (Siehe [Erweiterte Einstellungen](creating-policies.md#advanced-settings).)
1. Wählen Sie unter „Unveränderliche erweiterte Einstellungen“ die passenden Optionen aus. (Siehe [Unveränderliche erweiterte Einstellungen](creating-policies.md#unchangeable-advanced-settings).)
1. Klicken Sie auf Speichern. Die Richtlinie wird in der Richtlinienliste angezeigt. Ein Symbol mit einem roten Kreis wird neben der neuen Richtlinie angezeigt, was bedeutet, dass sie noch deaktiviert ist.

   Um die Richtlinie den Benutzern zur Verfügung zu stellen, müssen Sie sie aktivieren. (Siehe [Freigegebene Richtlinien aktivieren oder deaktivieren](creating-policies.md#enable-or-disable-shared-policies).)

### Benutzer und Gruppen {#users-and-groups}

Geben Sie im Bereich „Benutzer und Gruppen“ die Benutzer an, die Zugriff auf Dokumente haben, die mit der Richtlinie geschützt sind. Für alle angegebenen Benutzer und Gruppen legen Sie auch die Berechtigungen zur Dokumentnutzung fest.

>[!NOTE]
>
>Der Dokumentherausgeber ist der Benutzer, der das Dokument mit der Richtlinie schützt. Dieser Benutzer wird stets standardmäßig in eine Richtlinie einbezogen und hat Vollzugriffsrechte, so auch zum Sperren des Dokumentzugriffs oder Wechseln der Richtlinie. Administratoren können jedoch die Zugriffsrechte des Dokumentherausgebers für freigegebene Richtlinien ändern. Beispielsweise kann der Administrator dem Dokumentherausgeber die Rechte zum Sperren des Dokumentzugriffs oder Wechseln der Richtlinie entziehen.

**Benutzer oder Gruppe hinzufügen:** Um einen Benutzer oder eine Gruppe von Benutzern hinzuzufügen, klicken Sie auf Benutzer oder Gruppe hinzufügen und dann auf Erweiterte Suche , um Benutzer oder Gruppen zu suchen. Zu Benutzern zählen firmeninterne sowie eingeladene Benutzer, die sich bei Document Security registriert haben. Wenn Sie diese Option auswählen, wird die Seite „Benutzer oder Gruppe hinzufügen“ angezeigt.

* Geben Sie in das Feld „Suchen“ den Namen oder die E-Mail-Adresse ein.
* Wählen Sie in der Liste „Verwendet“ den Suchparameter „Name“ oder „E-Mail“ aus.
* Wählen Sie in der Liste „Typ“ entweder „Benutzer“ oder „Gruppe“ aus.
* Wählen Sie in der Liste „In“ die zu durchsuchende Domäne aus und klicken Sie auf „Suchen“.
* Wenn die Ergebnisse zurückgegeben werden, wählen Sie den Benutzer oder die Gruppe, der/die hinzugefügt werden soll, aus und klicken Sie auf „Hinzufügen“.

>[!NOTE]
>
>Wenn Sie einen Namen eines eingeladenen Benutzers oder eine E-Mail-Adresse ordnungsgemäß eingeben, ohne dass ein Ergebnis zurückgegeben wird, wurde der Benutzer ggf. noch nicht registriert oder sein Konto gelöscht. Sie können versuchen, den Benutzer als eingeladenen Benutzer hinzuzufügen, oder wenden Sie sich an den Administrator.

**Neuen Benutzer einladen:** Um einen eingeladenen Benutzer hinzuzufügen, klicken Sie auf &quot;Neuen Benutzer einladen&quot;, geben Sie die E-Mail-Adresse des Benutzers in das angezeigte Feld ein und klicken Sie auf &quot;Einladen&quot;. Diese Option ist nur verfügbar, wenn der Administrator sie aktiviert hat. Wenn Sie einer Richtlinie neu eingeladene Benutzer hinzufügen, sendet Document Security eine Einladungs-E-Mail zur Registrierung, wenn die Benutzer nicht bereits zur Registrierung eingeladen wurden. Die Benutzer müssen auf den Link in der E-Mail klicken, um ein Konto zu erstellen, und das Konto anschließend aktivieren. 

Nach der Registrierung können eingeladene Benutzer richtliniengeschützte Dokumente nutzen, für die sie autorisiert sind. Abhängig von den Funktionen, die der Administrator aktiviert, sind externe Benutzer eventuell auch dazu berechtigt, Richtlinien auf Dokumente anzuwenden, Richtlinien zu erstellen, zu bearbeiten und zu löschen sowie weitere externe Benutzer zu Richtlinien hinzuzufügen.

**Anonymen Benutzer hinzufügen:** Um den anonymen Benutzerzugriff zuzulassen, klicken Sie auf &quot;Anonymen Benutzer hinzufügen&quot;. Diese Option ist nur verfügbar, wenn der Administrator den anonymen Benutzerzugriff für Document Security aktiviert hat. (Siehe Document Security-Server konfigurieren.) Diese Option erlaubt allen Benutzern die Verwendung eines von dieser Richtlinie geschützten Dokuments, auch wenn sie kein Document Security-Konto haben. Bei Aktivierung dieser Option können Sie dieser Richtlinie keine anderen Benutzertypen hinzufügen.

>[!NOTE]
>
>Wenn Sie den anonymen Zugriff auf ein richtliniengeschütztes Dokument zulassen möchten, für das dieser Zugriff momentan nicht möglich ist, müssen Sie die vorhandene Richtlinie entfernen und anschließend eine Richtlinie anwenden, die den anonymen Zugriff zulässt. Wenn Sie die vorhandene Richtlinie wechseln oder ändern, müssen sich die Benutzer dennoch anmelden, um auf das Dokument zuzugreifen.

#### Dokumentberechtigungen für Benutzer und Gruppen angeben  {#specify-the-document-permissions-for-users-and-groups}

Sie können Dokumentberechtigungen für einen Benutzer oder eine Gruppe gleichzeitig angeben. Sie können aber auch mehrere Benutzer und Gruppen in der Liste auswählen und ihre Berechtigungen mithilfe der Optionen in den Spaltenüberschriften ändern.

Standardmäßig verfügen alle richtliniengeschützten Dokumente über eine Berechtigung, die es dem Benutzer erlaubt, das Dokument online zu öffnen.

Die Registerkarten „Berechtigungen“ und „Optionen“ werden in Document Security angezeigt.

Diese Dokumentberechtigungen sind auf der Registerkarte „Berechtigungen“ verfügbar. Sie können diese Berechtigungen auf PDF-, PTC Pro/E- und Microsoft Office-Dateien anwenden.

**Drucken:** Erlaubt dem Benutzer das Drucken eines mit dieser Richtlinie geschützten Dokuments. Für Office- und Pro/E-Dateien können Sie das Kontrollkästchen „Drucken“ aktivieren, um Drucken zuzulassen, oder deaktivieren Sie es, um Drucken zu verhindern. Wenn Sie das Kontrollkästchen „Benutzerdefinierte Berechtigungen für PDF-Datei anzeigen“ aktivieren, können Sie aus folgenden Optionen auswählen:

**Nicht zulässig:** Benutzer darf die PDF-Datei nicht drucken.

**Zulässig:** Benutzer darf die PDF-Datei drucken.

**Geringe Auflösung. Nur:** Benutzer darf die PDF-Datei mit niedriger Auflösung drucken.

**Ändern:** Erlaubt dem Benutzer das Ändern eines mit dieser Richtlinie geschützten Dokuments. Für Office- und Pro/E-Dateien können Sie das Kontrollkästchen „Ändern“ aktivieren, um Änderungen zuzulassen, oder deaktivieren Sie es, um Änderungen zu verhindern. Wenn Sie das Kontrollkästchen „Benutzerdefinierte Berechtigungen für PDF-Datei anzeigen“ aktivieren, können Sie aus folgenden Optionen auswählen:

**Nicht zulässig:** Benutzer darf die PDF-Datei nicht ändern.

**Beliebig:** Benutzer können die PDF-Datei ändern.

**Zusammenarbeit:** Benutzer darf mit anderen mithilfe der Optionen für die Zusammenarbeit in Adobe Acrobat zusammenarbeiten. Mit dieser Berechtigung kann der Benutzer Formulardaten kopieren, auch wenn die Kopierberechtigung nicht ausdrücklich in der Richtlinie erteilt wurde.

**Seiten ändern:** Benutzer darf Seiten hinzufügen und entfernen und Inhalt in der PDF-Datei bearbeiten.

**Fill &amp; Sign:** Benutzer darf Formularfelder in der PDF-Datei ausfüllen und sie signieren.

**Kopieren:** Erlaubt dem Benutzer das Kopieren von Text aus einem Dokument, das mit dieser Richtlinie geschützt ist.

**Bildschirm-Reader:** Diese Berechtigung wird angezeigt, wenn Sie das Kontrollkästchen &quot;Benutzerdefinierte Berechtigungen für PDF anzeigen&quot;aktivieren. Wenn diese Option aktiviert ist, verfügt Adobe Acrobat über die Berechtigung zum Hinzufügen von temporären Tags zu der PDF-Datei, um die Lesbarkeit mit einer Bildschirmlesehilfe zu verbessern. 

Diese Dokumentberechtigungen sind auf der Registerkarte „Optionen“ verfügbar. Sie können diese Berechtigungen auf PDF-, PTC Pro/E- und Microsoft Office-Dateien anwenden:

**Offline:** Erlaubt dem Benutzer, ein mit dieser Richtlinie geschütztes Dokument offline anzuzeigen.

**Gültigkeit der Berechtigungen:** Wählen Sie &quot;Berechtigungen sind immer gültig&quot;aus oder legen Sie einen Gültigkeitszeitraum für Dokumentberechtigungen fest. Wenn Sie eine Gültigkeitsdauer auswählen, klicken Sie auf das Kalendersymbol und wählen Sie ein Datum aus. Verwenden Sie die Pfeiltasten, um eine Uhrzeit im 24-Stunden-Format auszuwählen.

Für freigegebene Richtlinien können Administratoren dem Dokumentherausgeber (dem Benutzer, der die Richtlinie auf ein Dokument anwendet) die folgenden Berechtigungen entziehen:

**Sperren:** Erlaubt dem Dokumentherausgeber, Dokumentzugriffsberechtigungen zu sperren.

**Switch:** Erlaubt dem Dokumentherausgeber, Richtlinienberechtigungen zu wechseln.

### Allgemeine Einstellungen {#general-settings}

Der Bereich „Allgemeine Einstellungen“ enthält folgende Einstellungen:

**Gültigkeitszeitraum:** Der Zeitraum, in dem autorisierte Empfänger auf das richtliniengeschützte Dokument zugreifen können. Sie können aus den folgenden Optionen für die Gültigkeitsdauer auswählen:

**Dokument ist nicht gültig nach:** Das Dokument ist für die angegebene Anzahl von Tagen ab dem Zeitpunkt, zu dem das Dokument gesichert wurde, zugänglich.

**Das Dokument ist nach diesem Datum nicht mehr gültig:**  Das Dokument ist ab dem Datum gültig, an dem die Richtlinie auf das Dokument angewendet wird, bis zum angegebenen Enddatum.

**Gültig von, bis:** Das Dokument ist für die angegebenen Daten gültig. Sie können, falls das Kalendersymbol angezeigt wird, ein Datum im Kalender auswählen.

**Dokument ist immer gültig:**  Der Gültigkeitszeitraum des Dokuments läuft nicht ab.

>[!NOTE]
>
>Der Gültigkeitszeitraum basiert auf der Zeitzone des Document Security-Systems und nicht auf der Zeitzone des lokalen Computers.

**Auditing:** Aktivieren oder deaktivieren Sie die Prüfung der Ereignisse, die mit einem richtliniengeschützten Dokument verknüpft sind. Document Security kann beispielsweise Ereignisse wie Versuche, ein Dokument zu öffnen, aufzeichnen. Geprüfte Ereignisse werden in der Liste auf der Seite „Ereignisse“ angezeigt. Wenn Sie diese Option nicht aktivieren, zeichnet Document Security keine Ereignisse für Dokumente auf, die der Richtlinie zugeordnet sind.

>[!NOTE]
>
>Der Administrator muss ferner auf der Konfigurationsseite „Prüfungs- und Datenschutzeinstellungen“ die Serverprüfung aktivieren, damit die Prüffunktion funktioniert.

**Erweiterte Nutzungsverfolgung:** Aktivieren oder deaktivieren Sie die erweiterte Nutzungsverfolgung. Document Security unterstützt die Verfolgung von Benutzerereignissen im Zusammenhang mit verschiedenen Vorgängen, die an einer PDF-Datei durchgeführt werden. Auf das Document Security-Objekt kann mithilfe eines Java-Skriptes zugegriffen werden. Beispiele für die Ereignisse, die von einem richtliniengeschützten PDF ausgelöst werden können, sind das Anklicken einer Schaltfläche, das Anzeigen einer Multimedia-Datei oder das Speichern einer Datei. Mit dem Document Security-Objekt können Sie auch Benutzerinformationen abrufen. Die Ereignisverfolgung kann über den Document Security-Server auf globaler oder auf Richtlinienebene aktiviert werden.

**Automatische Offline-Nutzungsdauer:** Die maximale Anzahl von Tagen, nach denen der Empfänger das richtliniengeschützte Dokument offline verwenden kann (ohne aktive Internet- oder Netzwerkverbindung). Nach Ablauf der Nutzungsdauer muss der Empfänger das Dokument erneut synchronisieren, um es weiter verwenden zu können.

### Externe Autorisierungsanbieter  {#external-authorization-providers}

Wählen Sie die externen Authentifizierungsanbieter aus, wenn bereits Anbieter konfiguriert sind. Verfügbare Anbieter werden aufgelistet.

### Authentifizierungseinstellungen {#authentication-settings}

Sie können die Authentifizierungseinstellungen überschreiben, die Sie auf dem Server konfiguriert haben, und die Authentifizierungsoptionen angeben, die für diese Richtlinie relevant sind. Wählen Sie „Globale Authentifizierungseinstellungen außer Kraft setzen“, und wählen Sie dann die Authentifizierungsoptionen, die für diese Richtlinie relevant sind. Die folgenden Authentifizierungsptionen sind verfügbar:

**Authentifizierung für Benutzernamen-Kennwort zulassen:** Wählen Sie diese Option, um Client-Anwendungen die Verwendung der Benutzername-/Kennwortauthentifizierung beim Herstellen einer Verbindung zum Server zu ermöglichen.

**Kerberos-Authentifizierung zulassen:** Wählen Sie diese Option, um Clientanwendungen zu aktivieren, die die Kerberos-Authentifizierung beim Herstellen einer Verbindung zum Server verwenden.

**Client-Zertifikatauthentifizierung zulassen:** Wählen Sie diese Option aus, um Clientanwendungen zu aktivieren, die die Zertifikatauthentifizierung beim Herstellen einer Verbindung zum Server verwenden.

**Erweiterte** Authentifizierung zulassenWählen Sie diese Option aus, um die erweiterte Authentifizierung zu aktivieren. Durch Auswahl dieser Option wird für Clientanwendungen die Verwendung der erweiterten Authentifizierung aktiviert. Mit erweiterter Authentifizierung können auf dem Document Security-Server angepasste Authentifizierungsprozesse und verschiedene Authentifizierungsoptionen konfiguriert werden.

Wenn Sie die globalen Authentifizierungseinstellungen überschreiben, können Sie die Authentifizierungsoptionen auswählen, die für diese Richtlinie relevant sind. Wenn Sie z. B. auf dem Server drei Authentifizierungsoptionen aktiviert haben (Benutzername und Kennwort, Client-Zertifikat und erweiterte Authentifizierung), dann können Sie diese globale Einstellung überschreiben und für diese Richtlinie nur erweiterte Authentifizierung auswählen. Sie müssen sicherstellen, dass die Authentifizierungsoption, die Sie hier auswählen, bereits auf dem Server konfiguriert ist. In diesem Beispiel können Sie Kerberos nicht als Authentifizierungsoption wählen, da sie nicht auf dem Server konfiguriert ist.

>[!NOTE]
>
>Erweiterte Authentifizierung wird auf Apple Mac OS X mit Adobe Acrobat ab Version 11.0.6 unterstützt.

### Erweiterte Einstellungen {#advanced-settings}

Der Bereich „Erweiterte Einstellungen“ enthält folgende Einstellungen:

**Dynamisches Wasserzeichen:** Wählen Sie ein Wasserzeichen aus, das dynamisch auf den Seiten eines Dokuments angezeigt werden soll (z. B. wenn ein Empfänger das Dokument druckt). Dynamische Wasserzeichen kennzeichnen ein Dokument eindeutig und sorgen so dafür, dass die Vertraulichkeit des Dokuments gewährleistet bleibt und Copyright-Verstöße verhindert werden. Der Administrator kann beispielsweise ein dynamisches Wasserzeichen konfigurieren, welches das aktuelle Datum oder den Namen oder die ID der Person anzeigt, die das Dokument verwendet, oder den Namen der Richtlinie, die zum Schutz des Dokuments verwendet wird. Ein Wasserzeichen kann auch einen benutzerdeinierten Text oder ein grafisches Element enthalten, wenn es entsprechend konfiguriert ist. Administratoren konfigurieren die Wasserzeichenoptionen und sowohl Administratoren als auch Benutzer können diese auf Richtlinien anwenden. 

(Siehe [Dynamische Wasserzeichen konfigurieren](/help/forms/using/admin-help/configuring-client-server-options.md#configure-dynamic-watermarks).) 

Wenn Sie eine Richtlinie bearbeiten und der Administrator ein konfiguriertes Wasserzeichen gelöscht hat, das Sie zuvor für diese Richtlinie ausgewählt haben, wird auf der Seite „Richtlinie bearbeiten“ ein Hinweis angezeigt. Wenn Sie in diesem Fall das bearbeitete Dokument speichern, müssen Sie ein neues Wasserzeichen auswählen, falls im Dokument ein Wasserzeichen angezeigt werden soll.

>[!NOTE]
>
>Bei Richtlinien, die einen anonymen Benutzerzugriff zulassen, werden der Benutzername und die ID eines anonymen Benutzers nicht als Wasserzeichen angezeigt, auch wenn Sie diesen Typ von Wasserzeichen auswählen.

**Use Only Certified Acrobat Plug-ins for PDF:** Wenn für eine Richtlinie ausgewählt, bedeutet diese Option, dass Acrobat 8.0 und höher beim Öffnen von mit der Richtlinie gesicherten Dokumenten im zertifizierten Modus ausgeführt werden muss. Wird Acrobat im zertifizierten Modus ausgeführt, werden keine Drittanbieter-Plug-Ins geladen.

Wählen Sie diese Option aus, wenn Sie befürchten, dass ein Dokumentempfänger ein Plug-In schreibt, das die Dokumentschutzmaßnahmen in Acrobat 8.0 oder höher umgehen könnte. Aktivieren Sie diese Option nicht, wenn die Dokumentempfänger in Acrobat Plug-Ins von Drittanbietern für die Interaktion mit Dokumenten verwenden müssen.

Diese Option aktiviert den zertifizierten Modus nur in Acrobat 8.0 oder höher. Für Acrobat 7.0 muss der Administrator den Zugriff deaktivieren. 

(Siehe [Document Security-Server konfigurieren](/help/forms/using/admin-help/configuring-client-server-options.md#configure-the-document-security-server).) 

Diese Option gilt nicht für Adobe Reader.

**Fehlermeldung &quot;Zugriff verweigert&quot;:**  Eine Meldung, die allen Benutzern angezeigt wird, die versuchen, ein richtliniengeschütztes Dokument ohne Berechtigung zu öffnen. Diese Meldung wird in Acrobat angezeigt. Clients, die diese Meldung nicht anzeigen können, zeigen die Standardmeldung an, dass der Zugriff verweigert wird.

### Unveränderliche erweiterte Einstellungen  {#unchangeable-advanced-settings}

Der Bereich „Unveränderliche erweiterte Einstellungen“ enthält folgende Einstellungen: Sie können diese Einstellungen nach dem Speichern der Richtlinie nicht mehr ändern.

**Verschlüsselungsalgorithmus und Schlüssellänge:** Werden zum Schutz Ihrer Dokumente verwendet. Sie können aus den folgenden Optionen auswählen:

* AES 128-Bit
* AES 256-Bit. Diese Option wird nur von Acrobat 9.0 und höher unterstützt. Zur Verwendung der AES 256-Verschlüsselung für PDF-Dateien laden Sie die Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy-Dateien herunter und installieren Sie sie. Diese Dateien ersetzen die Dateien local_policy.jar und US_export_policy.jar im Ordner [JAVE_HOME]/lib/security . Wenn Sie beispielsweise Sun JDK 1.6 verwenden, kopieren Sie die heruntergeladenen Dateien in den Ordner [dep root]/Java/jdk1.6.0_26/lib/security . Sie können diese Dateien von der Seite [Java SE Downloads](https://java.sun.com/javase/downloads/index.jsp) herunterladen.
* Keine Verschlüsselung. Diese Option wird gegenwärtig von Acrobat 9.0 und höher unterstützt. Bei Wahl dieser Option sind die Optionen von „Dokumenteinschränkung“ deaktiviert. Diese Option ist ggf. nützlich, wenn Sie Document Security für die Dokumentprüfung oder Versionskontrolle, nicht jedoch zum Verschlüsseln des Dokuments nutzen möchten.

**Dokumentbeschränkungen:** Wählen Sie die zu verschlüsselnden PDF-Dokumentkomponenten aus. Andere Clientanwendungen verschlüsseln das gesamte Dokument, jedoch keine verknüpften oder eingebetteten Dateien. Sie können aus den folgenden Optionen auswählen:

* Das gesamte Dokument, einschließlich Anlagen und Metadaten. *Metadata* sind Informationen zum Dokument und seinem Inhalt, die Sie im Dialogfeld „Eigenschaften“ oder im Acrobat-Menü „Erweitert“ anzeigen können. In Acrobat können Sie Dateien verschiedener Typen an PDF-Dokumente anhängen, z. B. Text-, Audio- und Videodateien.
* Das Dokument und seine Anlagen ohne Metadaten.
* Nur die Dokumentanlagen. Sie können die Anlagen einer PDF-Datei verschlüsseln, ohne den Dokumentinhalt zu verschlüsseln.

## Freigegebene Richtlinien aktivieren oder deaktivieren  {#enable-or-disable-shared-policies}

Um eine freigegebene Richtlinie zur Verfügung zu stellen, muss sie vom Administrator oder Richtliniensatzkoordinator aktiviert werden. Sie können neue Richtlinien bzw. zuvor deaktivierte Richtlinien aktivieren. Eine freigegebene Richtlinie, die Sie deaktivieren, gilt weiter für Dokumente, die durch diese Richtlinie geschützt werden.

Neben einer deaktivierten Richtlinie wird ein rotes X angezeigt.

>[!NOTE]
>
>Administratoren können persönliche Richtlinien nicht deaktivieren, Benutzer können ihre eigenen Richtlinien nicht aktivieren bzw. deaktivieren.

1. Klicken Sie auf der Document Security-Seite auf „Richtlinien“ und anschließend auf die Registerkarte „Richtliniensätze“.
1. Klicken Sie auf den Namen des gewünschten Richtliniensatzes und anschließend auf die Registerkarte „Richtlinien“.
1. Aktivieren Sie das Kontrollkästchen neben der gewünschten Richtlinie und klicken Sie entweder auf „Aktivieren“ oder „Deaktivieren“ und anschließend auf „OK“.

## Informationen zu Richtlinien anzeigen  {#view-information-about-a-policy}

Auf der Registerkarte „Meine Richtlinien“ können Sie nach persönlichen Richtlinien suchen.

Von Administratoren erstellte Richtlinien werden auf der Seite „Richtlinien“ auf der Registerkarte „Richtliniensätze“ mit Informationen zum Richtliniensatz (Name, Erstellungs-/Änderungsdatum, Beschreibung) angezeigt. Klicken Sie auf einen Richtliniensatznamen, um die Details anzuzeigen. Richtliniensatzkoordinatoren mit Berechtigung zum Verwalten von Richtlinien können innerhalb eines bestimmten Richtliniensatzes freigegebene Richtlinien erstellen.

Beim Erstellen oder Bearbeiten einer Richtlinie wird eine Seite angezeigt, auf der Sie Details wie den Richtliniennamen, Berechtigungsebenen, Vertraulichkeitseinstellungen und die in die Richtlinie einzubeziehenden Empfänger konfigurieren können.

Der Administrator kann die folgenden Vertraulichkeitseinstellungen für eine Richtlinie konfigurieren:

* Allgemeine Dokumentvertraulichkeitsoptionen, z. B. die Gültigkeits- und Offline-Nutzungsdauer
* Die autorisierten Benutzer sowie die Dokumenteinschränkungen und -berechtigungen für die einzelnen Benutzer
* Erweiterte Dokumentvertraulichkeitsoptionen wie dynamische Wasserzeichen und Dokumentverschlüsselung

Benutzer können die Richtlinien, die sie erstellt haben, und alle freigegebenen Richtlinien, auf die sie Zugriff haben, anzeigen. Administratoren können alle in Document Security vorhandenen freigegebenen und persönlichen Richtlinien anzeigen.

Sie können detaillierte Informationen zu einer Richtlinie in der Liste anzeigen, darunter die in die Richtlinie einbezogenen Benutzer und Gruppen sowie die für diese Benutzer definierten Vertraulichkeitseinstellungen.

>[!NOTE]
>
>Richtlinien, die Acrobat automatisch für die Empfänger eines Dokuments generiert, das an eine E-Mail-Nachricht in Microsoft Outlook angehängt ist, werden nicht in der Richtlinienliste angezeigt. Sie können diese Richtlinien nur anzeigen, indem Sie die Seite „Dokumentdetails“ des dazugehörigen Dokuments öffnen.

1. Klicken Sie auf der Document Security-Seite auf „Richtlinien“ und anschließend auf die Registerkarte „Meine Richtlinien“.
1. Geben Sie die Suchinformationen für die Suche nach persönlichen Richtlinien ein.
1. Wählen Sie die gewünschte Richtlinie in der Liste aus.
1. Auf der Seite „Richtliniendetails“ können Sie Einzelheiten zu der Richtlinie anzeigen, die Richtlinie bearbeiten oder Ereignisse, die mit der Richtlinie zusammenhängen, anzeigen.

## Nach Richtlinien suchen  {#search-for-policies}

Administratoren können nach freigegebenen Richtlinien und nach persönlichen Richtlinien, die von anderen erstellt wurden, suchen.

1. Um nach einer freigegebenen Richtlinie zu suchen, klicken Sie auf „Richtlinien“ und anschließend auf die Registerkarte „Richtliniensätze“. Wählen Sie einen Richtliniensatz in der Liste aus und klicken Sie auf die Registerkarte „Richtlinien“.

   Um nach einer persönlichen Richtlinie zu suchen, klicken Sie auf der Document Security-Seite auf „Richtlinien“ und anschließend auf die Registerkarte „Meine Richtlinien“.

1. Wählen Sie in der Liste „Suchen“ eine dieser Optionen aus:

   **Richtlinien-ID:** Die Identifikationsnummer der Richtlinie, die beim Erstellen der Richtlinie durch den Benutzer generiert wird. Sie müssen die genaue Richtlinien-ID eingeben.

   **Richtlinienname:** Der Name der Richtlinie. Sie können nach dem vollständigen Namen oder einem Teil des Richtliniennamens suchen.

1. Geben Sie in das Textfeld den entsprechenden Wert ein. Geben Sie bei Wahl von „Richtlinienname“ den gesuchten Richtliniennamen ein.
1. Wählen Sie in der Liste „Anzeigen“ die Anzahl der pro Seite anzuzeigenden Suchergebnisse aus und klicken Sie auf „Suchen“. Die Suchergebnisse werden angezeigt.
1. (Optional) Um Richtliniendetails anzuzeigen, klicken Sie auf die Richtlinie.

## Eine Richtlinie kopieren  {#copy-a-policy}

Sie können eine vorhandene Richtlinie kopieren und mit neuem Namen und neuer Beschreibung speichern. Durch Kopieren können neue Richtlinien unter Verwendung vorhandener Einstellungen effizient erstellt werden.

Externe Benutzer können nur Richtlinien kopieren, wenn der Administrator diese Funktionalität aktiviert hat. Wenn Sie keine Richtlinien erstellen dürfen, wird die Option „Kopieren“ nicht angezeigt.

1. Klicken Sie auf der Document Security-Seite auf „Richtlinien“ und anschließend auf die Registerkarte „Meine Richtlinie“.
1. Wählen Sie die gewünschte Richtlinie in der Liste aus.
1. Klicken Sie auf der Seite „Richtliniendetails“ auf „Kopieren“.
1. Geben Sie in das Feld „Neuer Richtlinienname“ den neuen Richtliniennamen ein. Sie können auch eine neue Beschreibung eingeben.

   Die folgenden Zeichen dürfen im Namen oder für die Beschreibung nicht verwendet werden:

   * Kleiner-als-Zeichen (&lt;)
   * Größer-als-Zeichen (>)
   * Kaufmännisches Und-Zeichen (&amp;)
   * Einfaches Anführungszeichen (&#39;)
   * Doppeltes Anführungszeichen (&quot;)
   * umgekehrter Schrägstrich (\)
   * Schrägstrich (/)

   Wenn Sie folgende Zeichen im Namen oder in der Beschreibung verwenden, werden diese in Leerzeichen konvertiert:

   * Wagenrücklauf (ASCII-Zeichen 13)
   * Zeilenvorschub (ASCII-Zeichen 10).

   >[!NOTE]
   >
   >Sie können Richtliniennamen erstellen, die erweiterte Zeichen enthalten. Bei einem Vergleich zwischen zwei derartigen Zeichenfolgen werden jedoch Zeichen mit und ohne Akzentzeichen, wie z. B. „e“ und „é“, als identisch bewertet. Beim Erstellen einer Richtlinie wird ein Vergleich durchgeführt, um zu überprüfen, ob bereits eine Richtlinie mit demselben Namen vorhanden ist. Der Vergleich kann nicht zwischen Namen unterscheiden, die sich nur durch Akzentzeichen unterscheiden. Es wird angenommen, dass die Richtlinie bereits zur Datenbank hinzugefügt wurde, sodass die neue nicht hinzugefügt wird.

1. Klicken Sie auf OK.

## Eine Richtlinie löschen  {#delete-a-policy}

Sie können selbst erstellte Richtlinien löschen. Administratoren können Richtlinien löschen, die beliebige Benutzer erstellt haben. Richtliniensatzkoordinatoren können Richtlinien aus ihren Richtliniensätzen löschen. Eine Richtlinie, die Sie löschen, gilt weiter für Dokumente, die durch diese Richtlinie geschützt werden. Sie können mehrere Richtlinien gleichzeitig löschen.

Eingeladene Benutzer können Richtlinien nur löschen, wenn der Administrator diese Funktionalität aktiviert hat. Wenn Sie keine Richtlinien löschen dürfen, wird die Option „Löschen“ nicht angezeigt.

1. Klicken Sie auf der Document Security-Seite auf „Richtlinien“.
1. Klicken Sie auf die Registerkarte „Meine Richtlinie“.
1. Um eine freigegebene Richtlinie zu löschen, klicken Sie auf die Registerkarte „Richtliniensätze“ und anschließend auf den gewünschten Richtliniensatznamen.
1. Aktivieren Sie das Kontrollkästchen neben der gewünschten Richtlinie und klicken Sie erst auf „Löschen“ und anschließend auf „OK“.

>[!NOTE]
>
>Richtlinien müssen in der Clientanwendung von Dokumenten entfernt werden. (Siehe Acrobat-Hilfe oder entsprechende Acrobat Reader DC Extensions-Hilfe.)

## Die Richtlinienliste sortieren  {#sort-the-policy-list}

Sie können die Richtlinienliste nach Spaltenüberschrift sortieren, um Richtlinien leichter zu finden. Ein Dreieckssymbol neben der Spaltenüberschrift gibt an, nach welcher Spalte gegenwärtig sortiert wird. Ein nach oben zeigendes Dreieck gibt eine aufsteigende Reihenfolge an. Ein nach unten zeigendes Dreieck gibt eine absteigende Reihenfolge an.

1. Klicken Sie auf der Document Security-Seite auf „Richtlinien“ und anschließend auf die Registerkarte „Richtliniensätze“.
1. Wählen Sie einen Richtliniensatz aus und klicken Sie auf die Registerkarte „Richtlinien“.
1. Klicken Sie auf die gewünschte Spaltenüberschrift.
1. Um die Sortierreihenfolge zu ändern, klicken Sie nochmals auf die Spaltenüberschrift.
