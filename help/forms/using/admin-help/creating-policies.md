---
title: Erstellen und Verwalten von Richtlinien
description: Eine Richtlinie definiert einen Satz von Vertraulichkeitseinstellungen und Benutzenden, die auf ein Dokument zugreifen dürfen, für das die Richtlinie gilt. Sie können mit AEM Forms verschiedene Arten von Richtlinien erstellen und verwalten.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Document Security
exl-id: 5e57451c-1a89-442c-8404-841e95d5ceff
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '4713'
ht-degree: 100%

---

# Erstellen und Verwalten von Richtlinien {#creating-and-managing-policies}

Eine *Richtlinie* definiert einen Satz von Vertraulichkeitseinstellungen sowie die Benutzenden, die auf ein Dokument zugreifen dürfen, für das die Richtlinie gilt. Ein *Richtliniensatz* dient zum Gruppieren verschiedener Richtlinien mit einem gemeinsamen Zweck. Diese Richtliniensätze werden dann einer Untergruppe von Benutzenden im System zur Verfügung gestellt. Einzelheiten zu den Richtlinien finden Sie unter [Richtlinien und richtliniengeschützte Dokumente](/help/forms/using/admin-help/document-security.md#policies-and-policy-protected-documents).

## Arten von Richtlinien {#types-of-policies}

Die Dokumentensicherheit bietet folgende Arten von Richtlinien.

**Persönliche Richtlinien**

Benutzende können eigene Richtlinien erstellen, bearbeiten, kopieren, löschen und mit für eine bestimmte Situation geeigneten Einstellungen anwenden. Nur die Person, die eine Richtlinie erstellt hat, und Admins können auf diese persönliche Richtlinie zugreifen. Persönliche Richtlinien werden auf der Seite „Richtlinien“ auf der Registerkarte „Meine Richtlinien“ angezeigt.

Eingeladene Benutzende können ebenfalls persönliche Richtlinien erstellen, bearbeiten, kopieren und löschen, falls die Admins diese Funktionalität aktiviert haben.

**Freigegebene Richtlinien**

Admins sowie Personen, die Richtliniensätze koordinieren, erstellen freigegebene Richtlinien basierend auf den Vertraulichkeitsanforderungen, die Ihr Unternehmen für verschiedene Typen von Dokumenten und Benutzenden bestimmt hat. Freigegebene Richtlinien sind in Richtliniensätzen enthalten und stehen allen autorisierten Benutzenden (die entweder Dokumente veröffentlichen, Richtliniensätze koordinieren oder Dokumente empfangen) für einen bestimmten Richtliniensatz zur Verfügung. Admins sowie Personen, die Richtliniensätze koordinieren, können freigegebene Richtlinien aktivieren und deaktivieren. Freigegebene Richtlinien werden auf der Seite „Richtlinien“ auf der Registerkarte „Richtliniensätze“ in Richtliniensätzen angezeigt.

Wenn Sie die Dokumentensicherheit zum ersten Mal installieren, enthält das Programm eine freigegebene Richtlinie mit dem Namen *Auf alle Prinzipale beschränken*. Wenn diese Richtlinie auf ein Dokument angewendet wird, können Benutzende, die sich bei der Dokumentensicherheit anmelden, auf das Dokument zugreifen. Diese Richtlinie ist im Richtliniensatz namens *globaler Richtliniensatz* enthalten. In der Standardeinstellung ist diese Richtlinie deaktiviert. Sie können sie entsprechend den Anforderungen Ihres Unternehmens aktivieren.

**Von Microsoft® Outlook automatisch generierte Richtlinien**

Acrobat ermöglicht Ihnen das Anwenden von Richtlinien auf Dokumente, die Sie mit Microsoft® Outlook als E-Mail-Anhänge senden. In Outlook können Sie ein Dokument mithilfe einer vorhandenen Richtlinie schützen. Sie können auch eine automatisch generierte Richtlinie verwenden, die von Acrobat mit Standardvertraulichkeitseinstellungen generiert und auf das Dokument angewendet wird, das an die E-Mail-Nachricht angehängt ist. (Weitere Informationen finden Sie in der *[Acrobat-Hilfe](https://help.adobe.com/de_DE/acrobat/pro/using/index.html)*.)

>[!NOTE]
>
>Damit eine Richtlinie in Outlook verfügbar ist, müssen Sie die Richtlinie in Acrobat als Favorit festlegen. Alle anderen Richtlinien, einschließlich derer, dessen Publisher Sie sind, werden nicht in Outlook angezeigt.

## Wer kann Richtlinien und Richtliniensätze erstellen und verwalten? {#who-can-create-and-manage-policies-and-policy-sets}

Wie Sie mit Richtlinien und Richtliniensätzen interagieren, hängt von Ihrer Rolle innerhalb des Unternehmens ab:

**Benutzer:** Benutzer können ihre persönlichen Richtlinien erstellen, bearbeiten und löschen. Eingeladene Benutzer können ebenfalls persönliche Richtlinien erstellen, falls der Administrator diese Funktionalität aktiviert hat.

**Richtliniensatzkoordinatoren:** Richtliniensatzkoordinatoren können freigegebene Richtlinien innerhalb von Richtliniensätzen, für die sie als Koordinator angegeben sind, erstellen und verwalten. Ein Richtliniensatzkoordinator ist in der Regel ein Spezialist im Unternehmen, der die Richtlinien in einem bestimmten Richtliniensatz am besten verwalten kann.

**Admins:** Admins können die persönlichen Richtlinien von Benutzenden bearbeiten. Sie können freigegebene Richtlinien erstellen. Sie können ebenfalls Richtliniensätze erstellen, bearbeiten und löschen sowie Koordinatorinnen und Koordinatoren für Richtliniensätze angeben.

Weitere Informationen zu den verschiedenen Dokumentensicherheits-Rollen finden Sie unter [Informationen zu Document Security-Benutzenden](/help/forms/using/admin-help/document-security.md#about-document-security-users).

## Erstellen und Bearbeiten von Richtlinien {#creating-and-editing-policies}

Benutzende können ihre persönlichen Richtlinien für die eigene Verwendung erstellen oder bearbeiten. Admins sowie Personen, die Richtliniensätze koordinieren, können freigegebene Richtlinien für Ihr Unternehmen erstellen oder bearbeiten.

### Überlegungen zum Bearbeiten von Richtlinien {#considerations-for-editing-policies}

Wenn Sie eine Richtlinie bearbeiten, wirken sich die Änderungen auf Dokumente aus, die gegenwärtig und künftig durch die Richtlinie geschützt werden. Wenn Sie beispielsweise Empfängerinnen und Empfänger aus einer Richtlinie entfernen, die gegenwärtig für ein Dokument gilt, können diese Empfängerinnen und Empfänger das Dokument nicht mehr öffnen.

Der Status des Dokuments bestimmt, wann die Änderung wirksam wird:

* Ist das Dokument online, werden Änderungen sofort übernommen, es sei denn, die Benutzerin bzw. der Benutzer hat das Dokument geöffnet. In diesem Fall muss die Person das Dokument schließen, damit die Änderungen in Kraft treten.
* Wenn eine Empfängerin bzw. ein Empfänger das Dokument offline verwendet (z. B. auf einem Laptop), werden die Änderungen wirksam, sobald die Person das Dokument das nächste Mal online stellt. Anschließend wird die Synchronisierung mit der Dokumentensicherheit durch Öffnen eines beliebigen richtliniengeschützten Dokuments durchgeführt.

>[!NOTE]
>
>Richtlinien, die Acrobat automatisch für die Empfängerinnen und Empfänger von Dokumenten generiert, die an E-Mail-Nachrichten in Microsoft® Outlook angehängt sind, erscheinen nicht in der Richtlinienliste. Sie können diese Richtlinien nur anzeigen, indem Sie die Seite „Dokument-Details“ des dazugehörigen Dokuments öffnen.

Wenn Sie Richtlinien bearbeiten, gelten die folgenden Einschränkungen:

* Eingeladene Benutzerinnen und Benutzer können Richtlinien nur bearbeiten, wenn die Admins diese Funktionalität aktiviert haben. Wenn jemand keine Richtlinien bearbeiten darf, wird die Option „Bearbeiten“ nicht angezeigt.
* Richtliniensatz-Koordinatorinnen und -Koordinatoren können Richtlinien in Richtliniensätzen nur bearbeiten, wenn sie über die richtigen Berechtigungen verfügen. Die Superuser oder die Admins von Richtliniensätzen legen diese Berechtigungen in der Administrator-Oberfläche der Dokumentensicherheit fest.
* Wenn für die Richtlinie ein Wasserzeichen konfiguriert wurde, das die Admins seit der Erstellung der Richtlinie gelöscht haben, wird dieses Wasserzeichen nicht mehr auf Dokumente angewendet, wenn Sie die Richtlinie bearbeiten und speichern. Gelöschte Wasserzeichen bleiben nur für vorhandene Richtlinien wirksam, solange Sie die Richtlinie nicht bearbeiten. Wenn Sie die Richtlinie bearbeiten, müssen Sie ein anderes Wasserzeichen auswählen, um das gelöschte Wasserzeichen zu ersetzen.
* Sie können keinen anonymen Zugriff auf ein Dokument gewähren, indem Sie die angewendete Richtlinie bearbeiten. Wenn Sie die Richtlinie bearbeiten, müssen sich die Benutzenden dennoch anmelden, um auf das Dokument zugreifen zu können. Um anonymen Zugriff auf dieses Dokument zu gewähren, entfernen Sie zunächst die Richtlinie in der Client-Anwendung und wenden Sie dann eine andere Richtlinie an, die einen anonymen Zugriff zulässt.
* Richtlinien, die Acrobat automatisch für die Empfängerinnen und Empfänger eines Dokuments generiert, das an eine E-Mail-Nachricht in Microsoft Outlook angehängt ist, werden nicht in der Richtlinienliste angezeigt. Um auf diese Richtlinien zuzugreifen, suchen Sie das Dokument auf der Seite „Dokumente“, öffnen Sie die Seite „Dokumentdetails“ und klicken Sie auf den Richtliniennamen in der Liste der Dokumentdetails.

**Erstellen oder Bearbeiten einer Richtlinie**

1. Klicken Sie auf der Dokumentensicherheits-Seite auf „Richtlinien“ und anschließend auf eine der folgenden Registerkarten:

   * Um eine persönliche Richtlinie zu erstellen, klicken Sie auf die Registerkarte „Meine Richtlinien“.
   * Um eine freigegebene Richtlinie zu erstellen oder zu bearbeiten (sofern Sie die Berechtigung dazu haben), klicken Sie auf die Registerkarte „Richtliniensätze“, anschließend auf den gewünschten Richtliniensatznamen und dann auf die Registerkarte „Richtlinien“.

1. Klicken Sie auf „Neu“ oder wählen Sie in der Liste die zu bearbeitende Richtlinie aus.
1. Geben Sie in das Feld „Name“ einen Namen ein, der die Richtlinie eindeutig bestimmt. Geben Sie im Feld „Beschreibung“ an, was die Richtlinie bewirkt und wann sie zu verwenden ist. Wenn sich die Richtlinie in einem Richtliniensatz befindet, werden der Name und die Beschreibung in der Richtlinienliste für alle angegebenen Benutzenden angezeigt. Persönliche Richtlinien sind nur für Benutzende und Admins verfügbar.

   Die folgenden Zeichen dürfen im Namen oder in der Beschreibung nicht verwendet werden:

   * Kleiner-als-Zeichen (&lt;)
   * Größer-als-Zeichen (>)
   * Kaufmännisches Und-Zeichen (&amp;)
   * Einfaches Anführungszeichen (&#39;)
   * Doppeltes Anführungszeichen (&quot;)
   * umgekehrter Schrägstrich (\)
   * Schrägstrich (/)

   Wenn Sie folgende Zeichen im Namen oder in der Beschreibung verwenden, werden diese in Leerzeichen konvertiert:

   * Zeilenumbruch (ASCII-Zeichen 13)
   * Zeilenvorschub (ASCII-Zeichen 10).

   >[!NOTE]
   >
   >Sie können Richtliniennamen erstellen, die erweiterte Zeichen enthalten. Bei einem Vergleich zwischen zwei derartigen Zeichenfolgen werden jedoch Zeichen mit und ohne Akzentzeichen, wie z. B. „e“ und „é“, als identisch bewertet. Wenn jemand eine Richtlinie erstellt, wird ein Vergleich durchgeführt, um zu überprüfen, ob eine Richtlinie mit demselben Namen vorhanden ist. Der Vergleich kann nicht zwischen Namen unterscheiden, die sich nur durch Akzentzeichen unterscheiden. Es wird dann angenommen, dass die Richtlinie bereits zur Datenbank hinzugefügt wurde, sodass die neue nicht hinzugefügt wird.

1. Fügen Sie Benutzende und Gruppen zur Richtlinie hinzu und legen Sie entsprechende Berechtigungen fest. (Siehe [Erstellen von Benutzenden und Gruppen](creating-policies.md#users-and-groups).)
1. Wählen Sie unter „Allgemeine Einstellungen“ die passenden Optionen aus: (Siehe [Allgemeine Einstellungen](creating-policies.md#general-settings).)
1. (Optional) Wählen Sie ggf. einen externen Autorisierungsanbieter aus und geben Sie dessen Eigenschaften an. Wenn Sie keinen externen Autorisierungsanbieter verwenden möchten, klicken Sie auf „Standardanbieter entfernen“.

   Der externe Autorisierungsanbieter dient zum Einrichten von Eigenschaften innerhalb der Richtlinie. Falls aktiviert, nutzt der externe Autorisierungsanbieter diese Informationen zum Auswerten der Richtlinie. Diese Eigenschaften werden von den Admins und der Person konfiguriert, die die Software installiert.

1. Wählen Sie unter „Erweiterte Einstellungen“ die passenden Optionen aus. (Siehe [Erweiterte Einstellungen](creating-policies.md#advanced-settings).)
1. Wählen Sie unter „Unveränderliche erweiterte Einstellungen“ die passenden Optionen aus. (Siehe [Unveränderliche erweiterte Einstellungen](creating-policies.md#unchangeable-advanced-settings).)
1. Klicken Sie auf Speichern. Die Richtlinie wird in der Richtlinienliste angezeigt. Ein Symbol mit einem roten Kreis wird neben der neuen Richtlinie angezeigt. Das bedeutet, dass sie noch deaktiviert ist.

   Um die Richtlinie den Benutzenden zur Verfügung zu stellen, müssen Sie sie aktivieren. (Siehe [Freigegebene Richtlinien aktivieren oder deaktivieren](creating-policies.md#enable-or-disable-shared-policies).)

### Benutzer und Gruppen  {#users-and-groups}

Geben Sie im Bereich „Benutzer und Gruppen“ die Personen an, die Zugriff auf Dokumente haben, die mit der Richtlinie geschützt sind. Legen Sie für alle angegebenen Personen und Gruppen auch die Berechtigungen zur Dokumentnutzung fest.

>[!NOTE]
>
>Der Herausgeberin bzw. der Herausgeber des Dokuments ist die Person, die das Dokument mit der Richtlinie schützt. Diese Person wird stets standardmäßig in eine Richtlinie einbezogen und hat Vollzugriffsrechte, so auch zum Sperren des Dokumentzugriffs oder Wechseln der Richtlinie. Admins können jedoch die Zugriffsrechte der Herausgeberin bzw. des Herausgebers des Dokuments für freigegebene Richtlinien ändern. Beispielsweise können Admins der Herausgeberin bzw. dem Herausgeber des Dokuments die Rechte zum Sperren des Dokumentzugriffs oder Wechseln der Richtlinie entziehen.

**Benutzer oder Gruppe hinzufügen:** Um eine Person oder eine Gruppe von Personen hinzuzufügen, klicken Sie auf „Benutzer oder Gruppe hinzufügen“ und anschließend auf „Erweiterte Suche“, um Personen oder Gruppen zu suchen. Zu den Benutzenden zählen firmeninterne Personen sowie eingeladene Benutzende, die sich bei der Dokumentensicherheit registriert haben. Wenn Sie diese Option auswählen, wird die Seite „Benutzer oder Gruppe hinzufügen“ angezeigt:

* Geben Sie in das Feld „Suchen“ den Namen oder die E-Mail-Adresse der Person oder Gruppe ein.
* Wählen Sie in der Liste „Verwenden von“ den Suchparameter „Name“ oder „E-Mail“ aus.
* Wählen Sie in der Liste „Typ“ entweder „Benutzer“ oder „Gruppe“ aus.
* Wählen Sie in der Liste „In“ die zu durchsuchende Domain aus und klicken Sie auf „Suchen“.
* Wenn die Ergebnisse zurückgegeben werden, wählen Sie die Person oder Gruppe aus, die hinzugefügt werden soll, und klicken Sie auf „Hinzufügen“.

>[!NOTE]
>
>Wenn Sie den Namen oder die E-Mail-Adresse einer eingeladenen Person ordnungsgemäß eingeben, ohne dass ein Ergebnis zurückgegeben wird, wurde ggf. die Person noch nicht registriert oder das zugehörige Konto gelöscht. Sie können versuchen, die Person als eingeladene Person hinzuzufügen, oder wenden Sie sich an die Admins.

**Neuen Benutzer einladen:** Um eine eingeladene Person hinzuzufügen, klicken Sie auf „Neuen Benutzer einladen“, geben Sie die E-Mail-Adresse der Person in das Feld ein und klicken Sie auf „Einladen“. Diese Option ist nur verfügbar, wenn die oder der Admin sie aktiviert hat. Wenn Sie einer Richtlinie neu eingeladene Personen hinzufügen, sendet die Dokumentensicherheit eine Einladungs-E-Mail zur Registrierung, falls die Personen nicht bereits zur Registrierung eingeladen wurden. Die Personen müssen auf den Link in der E-Mail klicken, um ein Konto zu erstellen, und das Konto anschließend aktivieren.

Nach der Registrierung können eingeladene Personen richtliniengeschützte Dokumente nutzen, für die sie autorisiert sind. Abhängig von den Funktionen, die von den Admins aktiviert werden, sind externe Benutzende eventuell auch dazu berechtigt, Richtlinien auf Dokumente anzuwenden, Richtlinien zu erstellen, zu bearbeiten und zu löschen sowie weitere externe Benutzende zu Richtlinien hinzuzufügen.

**Anonymen Benutzer hinzufügen:** Um den anonymen Benutzerzugriff zuzulassen, klicken Sie auf „Anonymen Benutzer hinzufügen“. Diese Option ist nur verfügbar, wenn der Administrator den anonymen Benutzerzugriff für Document Security aktiviert hat. (Siehe Document Security-Server konfigurieren.) Diese Option erlaubt allen Benutzenden den Zugriff auf von dieser Richtlinie geschützte Dokumente, auch wenn sie kein Konto für die Dokumentensicherheit haben. Bei Aktivierung dieser Option können Sie dieser Richtlinie keine anderen Benutzertypen hinzufügen.

>[!NOTE]
>
>Wenn Sie den anonymen Zugriff auf ein richtliniengeschütztes Dokument zulassen möchten, für das dieser Zugriff momentan nicht möglich ist, müssen Sie die vorhandene Richtlinie entfernen und anschließend eine Richtlinie anwenden, die einen anonymen Zugriff zulässt. Wenn Sie die vorhandene Richtlinie wechseln oder ändern, müssen sich die Benutzenden dennoch anmelden, um auf das Dokument zuzugreifen.

#### Angeben von Dokumentberechtigungen für Personen und Gruppen {#specify-the-document-permissions-for-users-and-groups}

Sie können Dokumentberechtigungen für eine Person oder eine Gruppe gleichzeitig angeben. Sie können aber auch mehrere Personen und Gruppen in der Liste auswählen und ihre Berechtigungen mithilfe der Optionen in den Spaltenüberschriften ändern.

Standardmäßig verfügen alle richtliniengeschützten Dokumente über eine Berechtigung, die es Benutzenden erlaubt, das Dokument online zu öffnen.

Die Registerkarten „Berechtigungen“ und „Optionen“ werden in Document Security angezeigt.

Diese Dokumentberechtigungen sind auf der Registerkarte „Berechtigungen“ verfügbar. Sie können diese Berechtigungen auf PDF-, PTC Pro/E- und Microsoft Office-Dateien anwenden.

**Drucken:** Erlaubt dem Benutzer das Drucken eines durch diese Richtlinie geschützten Dokuments. Für Office- und Pro/E-Dateien können Sie das Kontrollkästchen „Drucken“ aktivieren, um Drucken zuzulassen, oder es deaktivieren, um das Drucken zu verhindern. Wenn Sie das Kontrollkästchen „Benutzerdefinierte Berechtigungen für PDF anzeigen“ aktivieren, können Sie aus folgenden Optionen auswählen:

**Nicht zulässig:** Der Benutzer darf die PDF-Datei nicht drucken.

**Zugelassen:** Der Benutzer darf die PDF-Datei drucken.

**Nur niedrige Auflösung:** Der Benutzer darf die PDF-Datei in niedriger Auflösung drucken.

**Verändern:** Erlaubt dem Benutzer, ein durch diese Richtlinie geschütztes Dokument zu verändern. Für Office- und Pro/E-Dateien können Sie das Kontrollkästchen „Ändern“ aktivieren, um Änderungen zuzulassen, oder es deaktivieren, um Änderungen zu verhindern. Wenn Sie das Kontrollkästchen „Benutzerdefinierte Berechtigungen für PDF anzeigen“ aktivieren, können Sie aus folgenden Optionen auswählen:

**Nicht zulässig:** Der Benutzer darf die PDF-Datei nicht ändern.

**Beliebig:** Der Benutzer kann die PDF-Datei ändern.

**Zusammenarbeiten:** Benutzer darf mithilfe der Optionen „Zusammenarbeiten“ in Adobe Acrobat mit anderen zusammenarbeiten. Mit dieser Berechtigung kann der Benutzer Formulardaten kopieren, auch wenn die Kopierberechtigung nicht ausdrücklich in der Richtlinie erteilt wurde.

**Seiten ändern:** Der Benutzer darf Seiten hinzufügen und entfernen und den Inhalt der PDF-Datei bearbeiten.

**Ausfüllen und Signieren:** Der Benutzer darf Formularfelder in der PDF-Datei ausfüllen und die Datei signieren.

**Kopieren:** Erlaubt dem Benutzer das Kopieren eines durch diese Richtlinie geschützten Textes.

**Bildschirmlesehilfe:** Diese Berechtigung wird angezeigt, wenn Sie das Kontrollkästchen „Benutzerdefinierte Berechtigungen für PDF-Datei anzeigen“ aktivieren. Wenn diese Option augewählt ist, verfügt Adobe Acrobat über die Berechtigung zum Hinzufügen von temporären Tags zu der PDF-Datei, um die Lesbarkeit mit einer Bildschirmlesehilfe zu verbessern.

Diese Dokumentberechtigungen sind auf der Registerkarte „Optionen“ verfügbar. Sie können diese Berechtigungen auf PDF-, PTC Pro/E- und Microsoft Office-Dateien anwenden:

**Offline:** Erlaubt dem Benutzer die Offline-Anzeige eines durch diese Richtlinie geschützten Dokuments.

**Gültigkeit der Berechtigung:** Wählen Sie „Berechtigungen sind immer gültig“ aus oder legen Sie eine Gültigkeitsdauer für Dokumentberechtigungen fest. Wenn Sie eine Gültigkeitsdauer auswählen, klicken Sie auf das Kalendersymbol und wählen Sie ein Datum aus. Verwenden Sie die Pfeiltasten, um eine Uhrzeit im 24-Stunden-Format auszuwählen.

Für freigegebene Richtlinien können Admins dem Dokument-Publisher (der Person, die die Richtlinie auf ein Dokument anwendet) die folgenden Berechtigungen entziehen:

**Sperren:** Erlaubt dem Herausgeber des Dokuments, die Dokumentzugriffsberechtigungen zu sperren.

**Wechseln:** Erlaubt dem Herausgeber des Dokuments, Richtlinienberechtigungen zu wechseln. 

### Allgemeine Einstellungen {#general-settings}

Der Bereich „Allgemeine Einstellungen“ enthält folgende Einstellungen:

**Gültigkeitszeitraum:** Der Zeitraum, in dem autorisierte Empfänger auf das richtliniengeschützte Dokument zugreifen können. Sie können aus den folgenden Optionen für die Gültigkeitsdauer auswählen:

**Das Dokument ist nicht gültig nach:** Das Dokument ist für die angegebene Anzahl von Tagen ab dem Zeitpunkt der Sicherung des Dokuments zugänglich.

**Das Dokument ist nach diesem Datum nicht mehr gültig:** Das Dokument gilt ab dem Datum, an dem die Richtlinie auf das Dokument angewendet wird, bis zum angegebenen Enddatum.

**Gültig von, bis:** Das Dokument gilt während der von Ihnen angegebenen Daten gültig. Sie können, falls das Kalendersymbol angezeigt wird, ein Datum im Kalender auswählen.

**Dokument ist immer gültig:** Der Gültigkeitszeitraum des Dokuments läuft nicht ab.

>[!NOTE]
>
>Der Gültigkeitszeitraum basiert auf der Zeitzone des Document Security-Systems und nicht auf der Zeitzone des lokalen Computers.

**Prüfung:** Sie können die Prüfung auf Ereignisse im Zusammenhang mit einem richtliniengeschützten Dokument aktivieren oder deaktivieren. Die Dokumentensicherheit kann beispielsweise Ereignisse wie Versuche, ein Dokument zu öffnen, aufzeichnen. Geprüfte Ereignisse werden in der Liste auf der Seite „Ereignisse“ angezeigt. Wenn Sie diese Option nicht aktivieren, zeichnet die Dokumentensicherheit keine Ereignisse für Dokumente auf, die der Richtlinie zugeordnet sind.

>[!NOTE]
>
>Admins müssen ferner auf der Konfigurationsseite „Auditing- und Datenschutzeinstellungen“ das Server-Auditing aktivieren, damit die Auditing-Funktion funktioniert.

**Erweiterte Nutzungsverfolgung:** Aktivieren oder deaktivieren Sie die erweiterte Nutzungsverfolgung. Die Dokumentensicherheit unterstützt das Tracking von Benutzerereignissen, die mit verschiedenen Vorgängen verknüpft sind, die mit einer PDF-Datei ausgeführt werden. Auf das Document Security-Objekt kann mithilfe eines Java-Skriptes zugegriffen werden. Beispiele für die Ereignisse, die von einem richtliniengeschützten PDF ausgelöst werden können, sind das Anklicken einer Schaltfläche, das Anzeigen einer Multimedia-Datei oder das Speichern einer Datei. Mit dem Document Security-Objekt können Sie auch Benutzerinformationen abrufen. Das Tracking von Ereignissen kann über den Document Security-Server auf globaler oder auf Richtlinienebene aktiviert werden.

**Automatische Offline-Nutzungsdauer:** Die maximale Anzahl von Tagen, die der Empfänger das richtliniengeschützte Dokument offline (ohne aktive Internet- oder Netzwerkverbindung) nutzen darf. Nach Ablauf der Nutzungsdauer muss der Empfänger das Dokument erneut synchronisieren, um es weiter verwenden zu können.

### Externe Authentifizierungsanbieter {#external-authorization-providers}

Wählen Sie die externen Authentifizierungsanbieter aus, wenn bereits Anbieter konfiguriert sind. Verfügbare Anbieter werden aufgelistet.

### Authentifizierungseinstellungen {#authentication-settings}

Sie können die Authentifizierungseinstellungen überschreiben, die Sie auf dem Server konfiguriert haben, und die für diese Richtlinie relevanten Authentifizierungsoptionen angeben. Wählen Sie „Globale Authentifizierungseinstellungen überschreiben“, und wählen Sie dann die Authentifizierungsoptionen, die für diese Richtlinie relevant sind. Die folgenden Authentifizierungsptionen sind verfügbar:

**Benutzername/Kennwort-Authentifizierung zulassen:** Wählen Sie diese Option, wenn Sie möchten, dass Client-Anwendungen bei der Verbindung mit dem Server eine Benutzername/Kennwort-Authentifizierung verwenden.

**Kerberos-Authentifizierung zulassen:** Wählen Sie diese Option, wenn Sie Client-Anwendungen die Verwendung der Kerberos-Authentifizierung bei der Verbindung mit dem Server ermöglichen möchten.

**Client-Zertifikat-Authentifizierung zulassen:** Wählen Sie diese Option, wenn Sie es Client-Anwendungen ermöglichen möchten, bei der Verbindung mit dem Server eine Zertifikat-Authentifizierung zu verwenden.

**Erweiterte Authentifizierung zulassen** Wählen Sie diese Option aus, um die erweiterte Authentifizierung zu aktivieren. Wenn Sie diese Option auswählen, können Client-Anwendungen die erweiterte Authentifizierung verwenden. Die erweiterte Authentifizierung bietet benutzerdefinierte Authentifizierungsprozesse und verschiedene Authentifizierungsoptionen, die auf dem Document Security-Server konfiguriert sind.

Wenn Sie die globalen Authentifizierungseinstellungen überschreiben, können Sie die für diese Richtlinie relevanten Authentifizierungsoptionen auswählen. Wenn Sie beispielsweise drei Authentifizierungsoptionen (Benutzername und Kennwort, Client-Zertifikat und erweiterte Authentifizierung) auf dem Server aktiviert haben, können Sie diese globale Einstellung überschreiben und für diese Richtlinie nur die erweiterte Authentifizierung auswählen. Stellen Sie sicher, dass die Authentifizierungsoption, die Sie hier auswählen, bereits auf dem Server konfiguriert ist. In diesem Beispiel können Sie Kerberos nicht als Authentifizierungsoption wählen, da es nicht auf dem Server konfiguriert ist.

>[!NOTE]
>
>Die erweiterte Authentifizierung wird auf Apple macOS mit Adobe Acrobat ab Version 11.0.6 unterstützt.

### Erweiterte Einstellungen {#advanced-settings}

Der Bereich „Erweiterte Einstellungen“ enthält folgende Einstellungen:

**Dynamisches Wasserzeichen:** Wählen Sie ein Wasserzeichen aus, das dynamisch auf den Seiten eines Dokuments angezeigt werden soll (z. B. wenn ein Empfänger das Dokument druckt). Dynamische Wasserzeichen kennzeichnen ein Dokument eindeutig, wodurch die Vertraulichkeit des Dokuments gewährleistet und Urheberrechtsverletzungen verhindert werden. Beispielsweise können Admins ein dynamisches Wasserzeichen konfigurieren, das das aktuelle Datum, den Benutzernamen oder die Kennung der Person anzeigt, die das Dokument verwendet. Oder der Name der Richtlinie, die zum Schutz des Dokuments verwendet wird. Ein Wasserzeichen kann auch benutzerdefinierten Text oder Grafikelemente anzeigen, sofern konfiguriert. Admins konfigurieren die Wasserzeichenoptionen, und andere Admins und Benutzende können sie auf Richtlinien anwenden.

(Siehe [Konfigurieren von dynamischen Wasserzeichen](/help/forms/using/admin-help/configuring-client-server-options.md#configure-dynamic-watermarks).)

Wenn Sie eine Richtlinie bearbeiten und die Admins ein konfiguriertes Wasserzeichen gelöscht haben, das Sie zuvor für diese Richtlinie ausgewählt haben, wird auf der Seite „Richtlinie bearbeiten“ ein Hinweis angezeigt. Wenn Sie in diesem Fall das bearbeitete Dokument speichern, wählen Sie ein neues Wasserzeichen aus, wenn eines im Dokument angezeigt werden soll.

>[!NOTE]
>
>Bei Richtlinien, die anonymen Benutzerzugriff bieten, werden der Benutzername und die Kennung von anonymen Benutzenden nicht als Wasserzeichen angezeigt, selbst wenn Sie diesen Typ von Wasserzeichen auswählen.

**Nur zertifizierte Acrobat-Plug-Ins für PDF-Datei verwenden:** Bei Auswahl dieser Option für eine Richtlinie wird festgelegt, dass Acrobat 8.0 und höher im zertifizierten Modus ausgeführt werden muss, wenn durch die Richtlinie geschützte Dokumente geöffnet werden. Wenn Acrobat im zertifizierten Modus ausgeführt wird, werden keine Plug-ins von Drittanbietern geladen.

Wählen Sie diese Option aus, wenn Sie befürchten, dass Empfängerinnen oder Empfänger von Dokumenten ein Plug-in schreiben könnten, das die Dokumentschutzmaßnahmen in Acrobat 8.0 und höher umgehen kann. Wählen Sie diese Option nicht aus, wenn die Empfängerinnen oder Empfänger Ihrer Dokumente für die Interaktion mit Dokumenten Plug-ins von Drittanbietern in Acrobat verwenden müssen.

Diese Option aktiviert nur den zertifizierten Modus in Acrobat 8.0 oder höher. Die Admins müssen den Zugriff für Acrobat 7.0 deaktivieren.

(Siehe [Konfigurieren des Dokumentensicherheits-Servers](/help/forms/using/admin-help/configuring-client-server-options.md#configure-the-document-security-server).)

Diese Option gilt nicht für Adobe Reader.

**Fehlermeldung „Zugriff verweigert“:** Eine Meldung, die immer dann angezeigt wird, wenn jemand versucht, ein richtliniengeschütztes Dokument ohne Zugriffsberechtigung zu öffnen. Diese Meldung wird in Acrobat angezeigt. Clients, die diese Meldung nicht anzeigen können, zeigen die Standardmeldung an, dass der Zugriff verweigert wird.

### Unveränderliche erweiterte Einstellungen {#unchangeable-advanced-settings}

Der Bereich „Unveränderliche erweiterte Einstellungen“ enthält folgende Einstellungen: Sie können diese Einstellungen nach dem Speichern der Richtlinie nicht mehr ändern.

**Verschlüsselungsalgorithmus und Schlüssellänge:** Dient zum Schutz Ihrer Dokumente. Sie können zwischen den folgenden Optionen wählen:

* AES 128 Bit
* AES 256 Bit. Diese Option wird nur von Acrobat 9.0 und höher unterstützt. Um die AES-256-Verschlüsselung für PDF-Dateien zu verwenden, müssen Sie die Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy-Dateien beziehen und installieren. Diese Dateien ersetzen die Dateien „local_policy.jar“ und „US_export_policy.jar“ im Ordner „[JAVE_HOME] /lib/security“. Falls Sie beispielsweise Sun JDK 1.6 verwenden, kopieren Sie die heruntergeladenen Dateien in den Ordner „[dep-Stammordner]/Java/jdk1.6.0_26/lib/security“. Sie können diese Dateien von [Java SE-Downloads](https://java.sun.com/javase/downloads/index.jsp) herunterladen.
* Keine Verschlüsselung. Diese Option wird gegenwärtig von Acrobat 9.0 und höher unterstützt. Wenn Sie diese Option auswählen, sind die Optionen für Dokumenteinschränkungen deaktiviert. Diese Option kann nützlich sein, wenn Sie die Dokumentensicherheit für die Dokumentenprüfung oder Versionskontrolle verwenden, das Dokument jedoch nicht verschlüsseln möchten.

**Dokumenteinschränkungen:** Wählen Sie PDF-Dokumentkomponenten aus, die verschlüsselt werden sollen. Andere Client-Anwendungen verschlüsseln das gesamte Dokument, jedoch keine verknüpften oder eingebetteten Dateien. Sie können zwischen den folgenden Optionen wählen:

* Das gesamte Dokument, einschließlich seiner Anlagen und Metadaten. *Metadaten* sind Informationen zum Dokument und seinem Inhalt, die Sie im Dialogfeld „Eigenschaften“ oder im Acrobat-Menü „Erweitert“ anzeigen können. In Acrobat können Sie Dateien unterschiedlicher Typen (z. B. Text-, Audio- und Videodateien) an PDF-Dokumente anhängen.
* Das Dokument und seine Anlagen, jedoch nicht die Metadaten.
* Nur die Dokumentanlagen. Sie können die Anlagen in einer PDF-Datei verschlüsseln, ohne den Dokumentinhalt zu verschlüsseln.

## Aktivieren oder Deaktivieren von freigegebenen Richtlinien {#enable-or-disable-shared-policies}

Um eine freigegebene Richtlinie verfügbar zu machen, muss sie von Admins oder Richtliniensatz-Koordinatorinnen bzw. -Koordinatoren aktiviert werden. Sie können neue Richtlinien oder zuvor deaktivierte Richtlinien aktivieren. Eine freigegebene Richtlinie, die Sie deaktivieren, wird weiterhin für Dokumente erzwungen, die mit dieser Richtlinie geschützt sind.

Neben einer deaktivierten Richtlinie wird ein rotes X angezeigt.

>[!NOTE]
>
>Admins können persönliche Richtlinien nicht deaktivieren, und Benutzende können ihre eigenen Richtlinien weder aktivieren noch deaktivieren.

1. Klicken Sie auf der Dokumentensicherheits-Seite auf „Richtlinien“ und anschließend auf die Registerkarte „Richtliniensätze“.
1. Klicken Sie auf den Namen des gewünschten Richtliniensatzes und anschließend auf die Registerkarte „Richtlinien“.
1. Aktivieren Sie das Kontrollkästchen neben der gewünschten Richtlinie und klicken Sie entweder auf „Aktivieren“ oder „Deaktivieren“ und anschließend auf „OK“.

## Anzeigen von Informationen zu Richtlinien {#view-information-about-a-policy}

Auf der Registerkarte „Meine Richtlinien“ können Sie nach persönlichen Richtlinien suchen.

Von Admins erstellte Richtliniensätze werden auf der Registerkarte „Richtliniensätze“ der Richtlinien-Seite aufgeführt. Sie enthalten Informationen über den Richtliniensatz, einschließlich seines Namens, des Erstellungsdatums und der Änderung sowie eine Beschreibung. Klicken Sie auf einen Richtliniensatznamen, damit Sie dessen Details anzeigen können. Richtliniensatzkoordinatoren mit Berechtigung zum Verwalten von Richtlinien können freigegebene Richtlinien in einem bestimmten Richtliniensatz erstellen.

Beim Erstellen oder Bearbeiten einer Richtlinie wird eine Seite angezeigt, auf der Sie den Richtliniennamen, die Berechtigungsebenen, die Vertraulichkeitseinstellungen und die in die Richtlinie einzubeziehenden Empfängerinnen und Empfänger konfigurieren können.

Admins können die folgenden Vertraulichkeitseinstellungen für eine Richtlinie konfigurieren:

* Allgemeine Dokumentvertraulichkeitsoptionen, wie der Gültigkeitszeitraum des Dokuments und die Offline-Nutzungsdauer
* Die autorisierten Benutzenden sowie die Dokumenteinschränkungen und -berechtigungen für jede dieser Personen
* Erweiterte Dokumentvertraulichkeitsoptionen, einschließlich dynamischer Wasserzeichen und Dokumentverschlüsselung

Benutzende können die von ihnen erstellten Richtlinien und alle freigegebenen Richtlinien anzeigen, auf die sie Zugriff haben. Admins können alle freigegebenen und persönlichen Richtlinien anzeigen, die sich in der Dokumentensicherheit befinden.

Sie können detailliertere Informationen zu einer Richtlinie anzeigen, die in der Liste angezeigt wird, einschließlich der in der Richtlinie enthaltenen Personen oder Gruppen und der für diese Personen festgelegten Vertraulichkeitseinstellungen.

>[!NOTE]
>
>Richtlinien, die Acrobat automatisch für die Empfängerinnen und Empfänger von Dokumenten generiert, die an E-Mail-Nachrichten in Microsoft Outlook angehängt sind, werden nicht in der Richtlinienliste angezeigt. Sie können diese Richtlinien nur anzeigen, indem Sie die Seite „Dokument-Details“ des dazugehörigen Dokuments öffnen.

1. Klicken Sie auf der Dokumentensicherheits-Seite auf „Richtlinien“ und anschließend auf die Registerkarte „Meine Richtlinien“.
1. Füllen Sie die Suchinformationen aus, damit Sie nach persönlichen Richtlinien suchen können.
1. Wählen Sie die gewünschte Richtlinie in der Liste aus.
1. Auf der Seite „Richtlinien-Details“ können Sie Einzelheiten zu der Richtlinie anzeigen, die Richtlinie bearbeiten oder Ereignisse anzeigen, die mit der Richtlinie zusammenhängen.

## Suchen nach Richtlinien {#search-for-policies}

Admins können nach freigegebenen Richtlinien und persönlichen Richtlinien suchen, die von anderen Benutzenden erstellt wurden.

1. Um nach einer freigegebenen Richtlinie zu suchen, klicken Sie auf „Richtlinien“ und anschließend auf die Registerkarte „Richtliniensätze“. Wählen Sie einen Richtliniensatz in der Liste aus und klicken Sie auf die Registerkarte „Richtlinien“.

   Um nach einer persönlichen Richtlinie zu suchen, klicken Sie auf der Dokumentensicherheits-Seite auf „Richtlinien“ und anschließend auf die Registerkarte „Meine Richtlinien“.

1. Wählen Sie in der Suchliste eine dieser Optionen aus:

   **Richtlinien-ID** Die Richtlinienidentifikationsnummer, die generiert wird, wenn ein Benutzer eine Richtlinie erstellt. Geben Sie die genaue Richtlinien-ID ein.

   **Richtlinienname:** Der Name der Richtlinie. Sie können nach einem Teil des Richtliniennamens oder nach dem vollständigen Namen suchen.

1. Geben Sie in das Textfeld den entsprechenden Wert ein. Wenn Sie „Richtlinienname“ ausgewählt haben, geben Sie den gesuchten Richtliniennamen ein.
1. Wählen Sie in der Liste „Anzeigen“ die Anzahl der anzuzeigenden Ergebnisse aus und klicken Sie auf „Suchen“. Die Suchergebnisse werden angezeigt.
1. (Optional) Um Richtliniendetails anzuzeigen, klicken Sie auf die Richtlinie.

## Kopieren einer Richtlinie {#copy-a-policy}

Sie können eine vorhandene Richtlinie kopieren und mit neuem Namen und neuer Beschreibung speichern. Durch Kopieren können Richtlinien mit den vorhandenen Einstellungen effizient erstellt werden.

Externe Benutzende können Richtlinien nur kopieren, wenn die Admins diese Funktionalität aktiviert haben. Wenn Sie keine Richtlinien erstellen dürfen, ist die Option „Kopieren“ nicht verfügbar.

1. Klicken Sie auf der Dokumentensicherheits-Seite auf „Richtlinien“ und anschließend auf die Registerkarte „Meine Richtlinie“.
1. Wählen Sie die gewünschte Richtlinie in der Liste aus.
1. Klicken Sie auf der Seite „Richtliniendetails“ auf „Kopieren“.
1. Geben Sie in das Feld „Neuer Name für die Richtlinie“ den neuen Richtliniennamen ein. Sie können auch eine neue Beschreibung eingeben.

   Die folgenden Zeichen dürfen im Namen oder in der Beschreibung nicht verwendet werden:

   * Kleiner-als-Zeichen (&lt;)
   * Größer-als-Zeichen (>)
   * Kaufmännisches Und-Zeichen (&amp;)
   * Einfaches Anführungszeichen (&#39;)
   * Doppeltes Anführungszeichen (&quot;)
   * umgekehrter Schrägstrich (\)
   * Schrägstrich (/)

   Wenn Sie folgende Zeichen im Namen oder in der Beschreibung verwenden, werden diese in Leerzeichen konvertiert:

   * Zeilenumbruch (ASCII-Zeichen 13)
   * Zeilenvorschub (ASCII-Zeichen 10).

   >[!NOTE]
   >
   >Sie können Richtliniennamen erstellen, die erweiterte Zeichen enthalten. Bei einem Vergleich zwischen zwei derartigen Zeichenfolgen werden jedoch Zeichen mit und ohne Akzentzeichen, wie z. B. „e“ und „é“, als identisch bewertet. Wenn jemand eine Richtlinie erstellt, wird ein Vergleich durchgeführt, um zu überprüfen, ob eine Richtlinie mit demselben Namen vorhanden ist. Der Vergleich kann nicht zwischen Namen unterscheiden, die sich nur durch Akzentzeichen unterscheiden. Es wird dann angenommen, dass die Richtlinie bereits zur Datenbank hinzugefügt wurde, sodass die neue nicht hinzugefügt wird.

1. Klicken Sie auf OK.

## Löschen einer Richtlinie {#delete-a-policy}

Sie können von Ihnen selbst erstellte Richtlinien löschen. Admins können Richtlinien löschen, die von beliebigen Benutzenden erstellt wurden. Richtliniensatz-Koordinatorinnen und -Koordinatoren können Richtlinien aus ihren Richtliniensätzen löschen. Eine Richtlinie, die Sie löschen, gilt weiter für Dokumente, die durch diese Richtlinie geschützt werden. Sie können mehrere Richtlinien gleichzeitig löschen.

Eingeladene Benutzende können Richtlinien nur löschen, wenn die Admins diese Funktionalität aktiviert haben. Wenn Sie keine Richtlinien löschen dürfen, ist die Option „Löschen“ nicht verfügbar.

1. Klicken Sie auf der Dokumentensicherheits-Seite auf „Richtlinien“.
1. Klicken Sie auf die Registerkarte „Meine Richtlinien“.
1. Um eine freigegebene Richtlinie zu löschen, klicken Sie auf die Registerkarte „Richtliniensätze“ und anschließend auf den gewünschten Richtliniensatznamen.
1. Aktivieren Sie das Kontrollkästchen neben der gewünschten Richtlinie und klicken Sie erst auf „Löschen“ und anschließend auf „OK“.

>[!NOTE]
>
>Verwenden Sie die Client-Anwendung, um Richtlinien von Dokumenten zu entfernen. (Siehe die Hilfe für Acrobat oder die entsprechende Hilfe zu den Acrobat Reader DC-Erweiterungen.)

## Sortieren der Richtlinienliste {#sort-the-policy-list}

Sie können die Richtlinienliste nach der Spaltenüberschrift sortieren, um Richtlinien leichter zu finden. Ein Dreiecksymbol neben der Spaltenüberschrift gibt an, nach welcher Spalte gegenwärtig sortiert wird. Ein nach oben zeigendes Dreieck gibt eine aufsteigende Reihenfolge an, ein nach unten zeigendes Dreieck gibt eine absteigende Reihenfolge an.

1. Klicken Sie auf der Dokumentensicherheits-Seite auf „Richtlinien“ und anschließend auf die Registerkarte „Richtliniensätze“.
1. Wählen Sie einen Richtliniensatz aus und klicken Sie auf die Registerkarte „Richtlinien“.
1. Klicken Sie auf die gewünschte Spaltenüberschrift.
1. Um die Sortierreihenfolge zu ändern, klicken Sie nochmals auf die Spaltenüberschrift.
