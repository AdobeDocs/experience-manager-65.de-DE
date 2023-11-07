---
title: Erstellen und Verwalten von Richtlinien
seo-title: Creating and managing policies
description: Eine Richtlinie ist ein Satz von Vertraulichkeitseinstellungen und Benutzern, die auf ein Dokument zugreifen können, auf das die Richtlinie angewendet wird. Sie können verschiedene Arten von Richtlinien mit AEM Formularen erstellen und verwalten.
seo-description: A policy is a set of confidentiality settings and users who can access a document to which the policy is applied. You can create and manage various types of policies using AEM forms.
uuid: 72be06f3-3e90-495e-8425-72380d95704a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: fa054d30-c7dc-4b64-acf1-cbcbe8827df5
feature: Document Security
exl-id: 5e57451c-1a89-442c-8404-841e95d5ceff
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '4715'
ht-degree: 19%

---

# Erstellen und Verwalten von Richtlinien {#creating-and-managing-policies}

Eine *Richtlinie* definiert einen Satz von Vertraulichkeitseinstellungen sowie die Benutzenden, die auf ein Dokument zugreifen dürfen, für das die Richtlinie gilt. Ein *Richtliniensatz* dient zum Gruppieren verschiedener Richtlinien mit einem gemeinsamen Zweck. Diese Richtliniensätze werden dann einer Untergruppe von Benutzenden im System zur Verfügung gestellt. Weitere Informationen zu Richtlinien finden Sie unter [Richtlinien und richtliniengeschützte Dokumente](/help/forms/using/admin-help/document-security.md#policies-and-policy-protected-documents).

## Arten von Richtlinien {#types-of-policies}

Document Security bietet die folgenden Arten von Richtlinien.

**Persönliche Richtlinien**

Benutzer können eigene Richtlinien erstellen, bearbeiten, kopieren, löschen und mit Einstellungen anwenden, die für eine bestimmte Situation geeignet sind. Nur die Person, die eine Richtlinie erstellt, und die Administratoren können auf diese persönliche Richtlinie zugreifen. Persönliche Richtlinien werden auf der Registerkarte Meine Richtlinien auf der Seite Richtlinien angezeigt.

Eingeladene Benutzer können auch persönliche Richtlinien erstellen, bearbeiten, kopieren und löschen, wenn der Administrator diese Funktion aktiviert hat.

**Freigegebene Richtlinien**

Administratoren und Richtliniensatzkoordinatoren erstellen freigegebene Richtlinien basierend auf den Vertraulichkeitsanforderungen, die Ihr Unternehmen für verschiedene Arten von Dokumenten und Benutzern ermittelt. Freigegebene Richtlinien sind in Richtliniensätzen enthalten und stehen allen autorisierten Benutzern (Dokumentherausgebern, Richtliniensatzkoordinatoren und Dokumentempfängern) für einen bestimmten Richtliniensatz zur Verfügung. Administratoren und Richtliniensatzkoordinatoren können freigegebene Richtlinien aktivieren und deaktivieren. Freigegebene Richtlinien werden in Richtliniensätzen auf der Registerkarte &quot;Richtliniensätze&quot;der Seite &quot;Richtlinien&quot;angezeigt.

Wenn Sie Document Security zum ersten Mal installieren, enthält es eine freigegebene Richtlinie mit dem Namen *Auf alle Prinzipale beschränken*. Wenn diese Richtlinie auf ein Dokument angewendet wird, kann jeder Benutzer, der sich bei Document Security anmelden kann, auf das Dokument zugreifen. Diese Richtlinie befindet sich im Richtliniensatz namens *Globaler Richtliniensatz*. Standardmäßig ist diese Richtlinie nicht aktiviert. Sie können sie aktivieren, wenn sie den Anforderungen Ihres Unternehmens entspricht.

**Automatisch generierte Microsoft Outlook-Richtlinien**

Mit Acrobat können Sie Richtlinien auf Dokumente anwenden, die Sie in Microsoft Outlook als E-Mail-Anhänge senden. In Outlook können Sie ein Dokument schützen, indem Sie eine vorhandene Richtlinie verwenden oder eine automatisch generierte Richtlinie verwenden, die von Acrobat mit Standardvertraulichkeitseinstellungen generiert und auf das Dokument angewendet wird, das an eine E-Mail-Nachricht angehängt ist. (Weitere Informationen finden Sie in der *[Acrobat-Hilfe](https://help.adobe.com/de_DE/acrobat/pro/using/index.html)*.)

>[!NOTE]
>
>Damit eine Richtlinie in Outlook verfügbar ist, müssen Sie die Richtlinie in Acrobat als Favoriten festlegen. Alle anderen Richtlinien, einschließlich der Richtlinien, bei denen Sie Publisher sind, werden nicht in Outlook angezeigt.

## Wer kann Richtlinien und Richtliniensätze erstellen und verwalten {#who-can-create-and-manage-policies-and-policy-sets}

Wie Sie mit Richtlinien und Richtliniensätzen interagieren, hängt von Ihrer Rolle innerhalb des Unternehmens ab:

**Benutzer:** Benutzer können ihre persönlichen Richtlinien erstellen, bearbeiten und löschen. Eingeladene Benutzer können ebenfalls persönliche Richtlinien erstellen, falls der Administrator diese Funktionalität aktiviert hat.

**Richtliniensatzkoordinatoren:** Richtliniensatzkoordinatoren können freigegebene Richtlinien innerhalb von Richtliniensätzen, für die sie als Koordinator angegeben sind, erstellen und verwalten. Ein Richtliniensatzkoordinator ist in der Regel ein Spezialist im Unternehmen, der die Richtlinien in einem bestimmten Richtliniensatz am besten verwalten kann.

**Administratoren:** Administratoren können die persönlichen Richtlinien jedes Benutzers bearbeiten. Sie können freigegebene Richtlinien erstellen. Sie können auch Richtliniensätze erstellen, bearbeiten und löschen sowie Richtliniensatzkoordinatoren festlegen.

Weitere Informationen zu den verschiedenen Document Security-Rollen finden Sie unter [Über Document Security-Benutzer](/help/forms/using/admin-help/document-security.md#about-document-security-users).

## Richtlinien erstellen und bearbeiten {#creating-and-editing-policies}

Benutzer können persönliche Richtlinien für ihre eigene Verwendung erstellen oder bearbeiten. Administratoren und Richtliniensatzkoordinatoren können freigegebene Richtlinien für Ihr Unternehmen erstellen oder bearbeiten.

### Überlegungen zum Bearbeiten von Richtlinien {#considerations-for-editing-policies}

Wenn Sie eine Richtlinie bearbeiten, wirken sich die Änderungen auf Dokumente aus, die derzeit von der Richtlinie geschützt werden, sowie auf Dokumente, die anschließend von der Richtlinie geschützt werden. Wenn Sie beispielsweise Empfänger aus einer Richtlinie entfernen, die derzeit für ein Dokument gilt, können die Empfänger das Dokument nicht mehr öffnen.

Der Status des Dokuments bestimmt, wann die Änderung wirksam wird:

* Wenn das Dokument online ist, werden Änderungen sofort angewendet, es sei denn, der Benutzer hat das Dokument geöffnet. In diesem Fall muss der Benutzer das Dokument schließen, damit die Änderungen wirksam werden.
* Wenn ein Empfänger das Dokument offline verwendet (z. B. auf einem Laptop), werden die Änderungen wirksam, wenn der Empfänger das Dokument das nächste Mal online stellt und durch Öffnen eines beliebigen richtliniengeschützten Dokuments mit Document Security synchronisiert.

>[!NOTE]
>
>Richtlinien, die Acrobat automatisch für die Empfänger von Dokumenten generiert, die an E-Mail-Nachrichten in Microsoft Outlook angehängt sind, werden nicht in der Richtlinienliste angezeigt. Sie können diese Richtlinien nur anzeigen, indem Sie die Seite &quot;Dokumentdetails&quot;für das zugehörige Dokument öffnen.

Wenn Sie Richtlinien bearbeiten, gelten diese Einschränkungen:

* Eingeladene Benutzer können Richtlinien nur bearbeiten, wenn der Administrator diese Funktion aktiviert hat. Wenn Sie Richtlinien nicht bearbeiten können, ist die Option &quot;Bearbeiten&quot;nicht verfügbar.
* Richtliniensatzkoordinatoren können Richtlinien in Richtliniensätzen nur bearbeiten, wenn sie über die richtigen Berechtigungen verfügen. Der Hauptbenutzer oder Richtliniensatzadministrator legt diese Berechtigungen auf der Benutzeroberfläche des Document Security-Administrators fest.
* Wenn für die Richtlinie ein Wasserzeichen konfiguriert wurde, das der Administrator seit der Erstellung der Richtlinie gelöscht hat, wird dieses Wasserzeichen nicht mehr auf Dokumente angewendet, wenn Sie die Richtlinie bearbeiten und speichern. Gelöschte Wasserzeichen bleiben nur für vorhandene Richtlinien wirksam, solange Sie die Richtlinie nicht bearbeiten. Wenn Sie die Richtlinie bearbeiten, müssen Sie ein anderes Wasserzeichen auswählen, um das gelöschte Wasserzeichen zu ersetzen.
* Sie können keinen anonymen Zugriff auf ein Dokument gewähren, indem Sie die derzeit angewendete Richtlinie bearbeiten. Wenn Sie die Richtlinie bearbeiten, müssen sich die Benutzer dennoch anmelden, um auf das Dokument zugreifen zu können. Um anonymen Zugriff auf dieses Dokument zu gewähren, entfernen Sie zunächst die Richtlinie in der Clientanwendung und wenden Sie dann eine andere Richtlinie an, die den anonymen Zugriff zulässt.
* Richtlinien, die Acrobat automatisch für die Empfänger eines Dokuments generiert, das an eine E-Mail-Nachricht in Microsoft Outlook angehängt ist, werden nicht in der Richtlinienliste angezeigt. Um auf diese Richtlinie zuzugreifen, suchen Sie das Dokument auf der Seite &quot;Dokumente&quot;, öffnen Sie die Seite &quot;Dokumentdetails&quot;und klicken Sie auf den Richtliniennamen in der Liste der Dokumentdetails.

**Richtlinie erstellen oder bearbeiten**

1. Klicken Sie auf der Document Security-Seite auf Richtlinien und dann auf eine dieser Registerkarten:

   * Um eine persönliche Richtlinie zu erstellen oder zu bearbeiten, klicken Sie auf die Registerkarte Meine Richtlinie .
   * Um eine freigegebene Richtlinie zu erstellen oder zu bearbeiten, klicken Sie, falls Sie über entsprechende Berechtigungen verfügen, auf die Registerkarte Richtliniensätze , klicken Sie auf den entsprechenden Richtliniensatznamen und dann auf die Registerkarte Richtlinien .

1. Klicken Sie auf Neu oder wählen Sie in der Liste die Richtlinie aus, die Sie bearbeiten möchten.
1. Geben Sie in das Feld &quot;Name&quot;einen Namen ein, der die Richtlinie eindeutig identifiziert. Beschreiben Sie im Feld Beschreibung , was die Richtlinie tut und wann sie verwendet werden soll. Wenn sich die Richtlinie in einem Richtliniensatz befindet, werden der Name und die Beschreibung in der Richtlinienliste für alle angegebenen Benutzer angezeigt. Persönliche Richtlinien sind nur für Benutzer und Administratoren verfügbar.

   Die folgenden Zeichen dürfen im Namen oder in der Beschreibung nicht verwendet werden:

   * Kleiner-als-Zeichen (&lt;)
   * Größer-als-Zeichen (>)
   * kaufmännisches Und-Zeichen (&amp;)
   * Einfaches Anführungszeichen (&#39;)
   * Doppeltes Anführungszeichen (&quot;)
   * umgekehrter Schrägstrich (\)
   * Schrägstrich (/)

   Wenn Sie im Namen oder in der Beschreibung das folgende Zeichen verwenden, werden diese in Leerzeichen umgewandelt:

   * Wagenrücklauf (ASCII-Zeichen 13)
   * neue Zeile (ASCII-Zeichen 10).

   >[!NOTE]
   >
   >Sie können einen Richtliniennamen erstellen, der erweiterte Zeichen enthält. Wenn jedoch ein Vergleich zwischen zwei Zeichenfolgen durchgeführt wird, werden Zeichen mit und ohne Akzentzeichen wie &quot;e&quot;und &quot;é&quot;als identisch betrachtet. Wenn jemand eine Richtlinie erstellt, wird ein Vergleich durchgeführt, um zu überprüfen, ob bereits eine Richtlinie mit demselben Namen vorhanden ist. Der Vergleich kann nicht zwischen Namen unterscheiden, die mit Ausnahme von Akzentzeichen identisch sind. Es wird davon ausgegangen, dass die Richtlinie bereits zur Datenbank hinzugefügt und die neue nicht hinzugefügt wurde.

1. Fügen Sie der Richtlinie Benutzer und Gruppen hinzu und legen Sie die entsprechenden Berechtigungen fest. (Siehe [Benutzer und Gruppen](creating-policies.md#users-and-groups).
1. Wählen Sie unter &quot;Allgemeine Einstellungen&quot;die entsprechenden Optionen aus. (Siehe [Allgemeine Einstellungen](creating-policies.md#general-settings).
1. (Optional) Wählen Sie ggf. einen externen Autorisierungsanbieter aus und geben Sie dessen Eigenschaften an. Wenn Sie keinen externen Autorisierungsanbieter verwenden möchten, klicken Sie auf Standardanbieter entfernen.

   Ein externer Autorisierungsanbieter wird verwendet, um Eigenschaften innerhalb der Richtlinie einzurichten. Wenn diese ausgewählt sind, verwendet der externe Autorisierungsanbieter diese Informationen zur Bewertung der Richtlinie. Die verfügbaren Eigenschaften werden vom Administrator und von der Person konfiguriert, die die Software installiert.

1. Wählen Sie unter Erweiterte Einstellungen die entsprechenden Optionen aus. (Siehe [Erweiterte Einstellungen](creating-policies.md#advanced-settings).
1. Wählen Sie unter Unveränderliche erweiterte Einstellungen die entsprechenden Optionen aus. (Siehe [Unveränderliche erweiterte Einstellungen](creating-policies.md#unchangeable-advanced-settings).
1. Klicken Sie auf Speichern. Die Richtlinie wird in der Richtlinienliste angezeigt. Neben der neuen Richtlinie wird ein Symbol mit einem roten Kreis angezeigt, das angibt, dass sie noch deaktiviert ist.

   Um die Richtlinie Benutzern zur Verfügung zu stellen, aktivieren Sie sie. (Siehe [Freigegebene Richtlinien aktivieren oder deaktivieren](creating-policies.md#enable-or-disable-shared-policies).

### Benutzer und Gruppen  {#users-and-groups}

Geben Sie im Bereich Benutzer und Gruppen die Benutzer an, die Zugriff auf Dokumente haben, die durch die Richtlinie geschützt sind. Für jeden angegebenen Benutzer oder jede angegebene Gruppe legen Sie auch die Dokumentverwendungsberechtigungen fest.

>[!NOTE]
>
>Der Dokumentherausgeber ist der Benutzer, der das Dokument mit der Richtlinie schützt. Dieser Benutzer ist standardmäßig immer in eine Richtlinie mit vollen Zugriffsrechten eingeschlossen, einschließlich Sperren und Wechseln von Richtlinien. Administratoren können jedoch die Zugriffsberechtigungen des Dokumentherausgebers für freigegebene Richtlinien ändern. Beispielsweise kann der Administrator den Dokumentherausgeber daran hindern, den Dokumentzugriff zu sperren oder die Richtlinie zu wechseln.

**Benutzer oder Gruppe hinzufügen:** Um einen Benutzer oder eine Gruppe von Benutzern hinzuzufügen, klicken Sie auf „Benutzer oder Gruppe hinzufügen“ und anschließend auf „Erweiterte Suche“, um Benutzer oder Gruppen zu suchen. Zu den Benutzern gehören die internen Benutzer Ihrer Organisation und eingeladene Benutzer, die sich bei Document Security registriert haben. Wenn Sie diese Option auswählen, wird die Seite Benutzer oder Gruppe hinzufügen angezeigt:

* Geben Sie in das Feld &quot;Suchen&quot;den Benutzer- oder Gruppennamen oder die E-Mail-Adresse ein.
* Wählen Sie in der Liste &quot;Verwenden&quot;die Option Name oder E-Mail aus.
* Wählen Sie in der Liste Typ die Option Benutzer oder Gruppe aus.
* Wählen Sie in der Liste „In“ die zu durchsuchende Domain aus und klicken Sie auf „Suchen“.
* Wenn die Ergebnisse zurückgegeben werden, wählen Sie den hinzuzufügenden Benutzer oder die hinzuzufügende Gruppe aus und klicken Sie auf Hinzufügen.

>[!NOTE]
>
>Wenn Sie einen korrekten Namen eines eingeladenen Benutzers oder eine E-Mail-Adresse eingeben und kein Ergebnis zurückgegeben wird, hat sich der Benutzer möglicherweise noch nicht registriert oder das Konto kann gelöscht werden. Sie können versuchen, den Benutzer als eingeladenen Benutzer hinzuzufügen, oder sich an Ihren Administrator wenden.

**Neuen Benutzer einladen:** Um einen eingeladenen Benutzer hinzuzufügen, klicken Sie auf „Neuen Benutzer einladen“, geben Sie die E-Mail-Adresse des Benutzers in das Feld ein und klicken Sie auf „Einladen“. Diese Option ist nur verfügbar, wenn sie vom Administrator aktiviert wurde. Wenn Sie einer Richtlinie neue eingeladene Benutzer hinzufügen, sendet Document Security eine Einladungs-E-Mail zur Registrierung, wenn die Benutzer noch nicht zur Registrierung eingeladen wurden. Die Benutzer müssen den Link in der E-Mail verwenden, um ein Konto zu erstellen, und dann das Konto aktivieren.

Nach der Registrierung können eingeladene Benutzer richtliniengeschützte Dokumente verwenden, für die sie autorisiert sind. Abhängig von den Funktionen, die der Administrator aktiviert, sind externe Benutzer möglicherweise berechtigt, Richtlinien auf Dokumente anzuwenden, Richtlinien zu erstellen, zu bearbeiten und zu löschen und andere externe Benutzer zu Richtlinien hinzuzufügen.

**Anonymen Benutzer hinzufügen:** Um den anonymen Benutzerzugriff zuzulassen, klicken Sie auf „Anonymen Benutzer hinzufügen“. Diese Option ist nur verfügbar, wenn der Administrator den anonymen Benutzerzugriff für Document Security aktiviert hat. (Siehe Document Security-Server konfigurieren.) Mit dieser Option erhalten alle Benutzer Zugriff auf durch diese Richtlinie geschützte Dokumente, unabhängig davon, ob sie über ein Document Security-Konto verfügen. Wenn Sie diese Option auswählen, können Sie der Richtlinie keine anderen Typen von Benutzern hinzufügen.

>[!NOTE]
>
>Um den anonymen Zugriff auf ein richtliniengeschütztes Dokument zuzulassen, für das dieser Zugriff derzeit nicht möglich ist, entfernen Sie die vorhandene Richtlinie und wenden Sie dann eine Richtlinie an, die den anonymen Zugriff zulässt. Wenn Sie die vorhandene Richtlinie wechseln oder ändern, müssen sich die Benutzer dennoch anmelden, um auf das Dokument zuzugreifen.

#### Dokumentberechtigungen für Benutzer und Gruppen angeben {#specify-the-document-permissions-for-users-and-groups}

Sie können Dokumentberechtigungen für einen Benutzer oder eine Gruppe gleichzeitig angeben oder Sie können mehrere Benutzer und Gruppen aus der Liste auswählen und ihre Berechtigungen mithilfe der Optionen im Bereich der Spaltenüberschriften ändern.

Standardmäßig verfügen alle richtliniengeschützten Dokumente über eine Berechtigung, mit der Benutzer sie online öffnen können.

Die Registerkarte Berechtigungen und Optionen wird in Document Security angezeigt.

Diese Dokumentberechtigungen sind auf der Registerkarte Berechtigungen verfügbar. Sie können diese Berechtigungen auf PDF-, PTC Pro/E- und Microsoft Office-Dateien anwenden.

**Drucken:** Erlaubt dem Benutzer das Drucken eines durch diese Richtlinie geschützten Dokuments. Bei Office- und Pro/E-Dateien können Sie das Kontrollkästchen &quot;Drucken&quot;aktivieren, um das Drucken zuzulassen, oder deaktivieren Sie es, um das Drucken zu verhindern. Wenn Sie das Kontrollkästchen &quot;Benutzerdefinierte Berechtigungen für PDF anzeigen&quot;aktivieren, können Sie aus folgenden Optionen auswählen:

**Nicht zulässig:** Der Benutzer darf die PDF-Datei nicht drucken.

**Zugelassen:** Der Benutzer darf die PDF-Datei drucken.

**Nur niedrige Auflösung:** Der Benutzer darf die PDF-Datei in niedriger Auflösung drucken.

**Verändern:** Erlaubt dem Benutzer, ein durch diese Richtlinie geschütztes Dokument zu verändern. Bei Office- und Pro/E-Dateien können Sie das Kontrollkästchen Ändern aktivieren, um Änderungen zuzulassen, oder deaktivieren Sie es, um Änderungen zu verhindern. Wenn Sie das Kontrollkästchen &quot;Benutzerdefinierte Berechtigungen für PDF anzeigen&quot;aktivieren, können Sie aus folgenden Optionen auswählen:

**Nicht zulässig:** Der Benutzer darf die PDF-Datei nicht ändern.

**Beliebig:** Der Benutzer kann die PDF-Datei ändern.

**Zusammenarbeiten:** Benutzer darf mithilfe der Optionen „Zusammenarbeiten“ in Adobe Acrobat mit anderen zusammenarbeiten. Mit dieser Berechtigung kann der Benutzer Formulardaten kopieren, auch wenn die Kopierberechtigung nicht ausdrücklich in der Richtlinie erteilt wurde.

**Seiten ändern:** Der Benutzer darf Seiten hinzufügen und entfernen und den Inhalt der PDF-Datei bearbeiten.

**Ausfüllen und Signieren:** Der Benutzer darf Formularfelder in der PDF-Datei ausfüllen und die Datei signieren.

**Kopieren:** Erlaubt dem Benutzer das Kopieren eines durch diese Richtlinie geschützten Textes.

**Bildschirmlesehilfe:** Diese Berechtigung wird angezeigt, wenn Sie das Kontrollkästchen „Benutzerdefinierte Berechtigungen für PDF-Datei anzeigen“ aktivieren. Wenn diese Option aktiviert ist, ist Adobe Acrobat berechtigt, temporäre Tags zur PDF hinzuzufügen, um die Lesbarkeit mit einer Bildschirmlesehilfe zu verbessern.

Diese Dokumentberechtigungen sind auf der Registerkarte &quot;Optionen&quot;verfügbar. Sie können diese Berechtigungen auf PDF-, PTC Pro/E- und Microsoft Office-Dateien anwenden:

**Offline:** Erlaubt dem Benutzer die Offline-Anzeige eines durch diese Richtlinie geschützten Dokuments.

**Gültigkeit der Berechtigung:** Wählen Sie „Berechtigungen sind immer gültig“ aus oder legen Sie eine Gültigkeitsdauer für Dokumentberechtigungen fest. Wenn Sie einen Gültigkeitszeitraum auswählen, klicken Sie auf die Kalendersymbole, um ein Datum auszuwählen, und geben Sie mithilfe der Pfeile im 24-Stunden-Format die Uhrzeit an.

Für freigegebene Richtlinien können Administratoren die folgenden Berechtigungen für den Dokumentherausgeber deaktivieren (den Benutzer, der die Richtlinie auf ein Dokument anwendet):

**Sperren:** Erlaubt dem Herausgeber des Dokuments, die Dokumentzugriffsberechtigungen zu sperren.

**Wechseln:** Erlaubt dem Herausgeber des Dokuments, Richtlinienberechtigungen zu wechseln. 

### Allgemeine Einstellungen {#general-settings}

Der Bereich &quot;Allgemeine Einstellungen&quot;enthält die folgenden Einstellungen:

**Gültigkeitszeitraum:** Der Zeitraum, in dem autorisierte Empfänger auf das richtliniengeschützte Dokument zugreifen können. Sie können aus den folgenden Optionen für die Gültigkeitsdauer auswählen:

**Das Dokument ist nicht gültig nach:** Das Dokument ist für die angegebene Anzahl von Tagen ab dem Zeitpunkt der Sicherung des Dokuments zugänglich.

**Das Dokument ist nach diesem Datum nicht mehr gültig:** Das Dokument gilt ab dem Datum, an dem die Richtlinie auf das Dokument angewendet wird, bis zum angegebenen Enddatum.

**Gültig von, bis:** Das Dokument gilt während der von Ihnen angegebenen Daten gültig. Sie können, falls das Kalendersymbol angezeigt wird, ein Datum im Kalender auswählen.

**Dokument ist immer gültig:** Der Gültigkeitszeitraum des Dokuments läuft nicht ab.

>[!NOTE]
>
>Der Gültigkeitszeitraum basiert auf der Zeitzone des Document Security-Systems und nicht auf der Zeitzone des lokalen Computers.

**Prüfung:** Sie können die Prüfung auf Ereignisse im Zusammenhang mit einem richtliniengeschützten Dokument aktivieren oder deaktivieren. Document Security kann beispielsweise Ereignisse wie Versuche, ein Dokument zu öffnen, aufzeichnen. Geprüfte Ereignisse werden in der Liste auf der Seite &quot;Ereignisse&quot;angezeigt. Wenn Sie diese Option nicht auswählen, zeichnet Document Security keine Ereignisse für Dokumente auf, die mit der Richtlinie verknüpft sind.

>[!NOTE]
>
>Der Administrator muss außerdem die Serverprüfung auf der Konfigurationsseite &quot;Prüfungs- und Datenschutzeinstellungen&quot;aktivieren, damit die Prüffunktion funktioniert.

**Erweiterte Nutzungsverfolgung:** Aktivieren oder deaktivieren Sie die erweiterte Nutzungsverfolgung. Document Security unterstützt die Verfolgung von Benutzerereignissen, die mit verschiedenen Vorgängen verknüpft sind, die auf einer PDF-Datei ausgeführt werden. Auf das Document Security-Objekt kann mithilfe eines JavaScripts zugegriffen werden. Beispiele für Ereignisse, die von einer richtliniengeschützten PDF ausgelöst werden können, sind ein Schaltflächenklick, eine wiedergegebene Multimedia-Datei oder das Speichern einer Datei. Mit dem Document Security-Objekt können Sie auch Benutzerinformationen abrufen. Das Tracking von Ereignissen kann vom Document Security-Server auf globaler Ebene oder auf Richtlinienebene aktiviert werden.

**Automatische Offline-Nutzungsdauer:** Die maximale Anzahl von Tagen, die der Empfänger das richtliniengeschützte Dokument offline (ohne aktive Internet- oder Netzwerkverbindung) nutzen darf. Nach Ablauf der Nutzungsdauer muss der Empfänger das Dokument erneut synchronisieren, um es weiter verwenden zu können.

### Externe Autorisierungsanbieter {#external-authorization-providers}

Wählen Sie die externen Authentifizierungsanbieter aus, falls Sie bereits einen konfiguriert haben. Verfügbare Anbieter werden aufgelistet.

### Authentifizierungseinstellungen {#authentication-settings}

Sie können die Authentifizierungseinstellungen überschreiben, die Sie auf dem Server konfiguriert haben, und die für diese Richtlinie relevanten Authentifizierungsoptionen angeben. Wählen Sie Globale Authentifizierungseinstellungen überschreiben und dann die für diese Richtlinie relevanten Authentifizierungsoptionen. Die folgenden Authentifizierungsoptionen sind verfügbar:

**Benutzername/Kennwort-Authentifizierung zulassen:** Aktivieren Sie diese Option, um zu bestimmen, ob Client-Anwendungen beim Herstellen einer Server-Verbindung die Benutzername/Kennwort-Authentifizierung zulassen.

**Kerberos-Authentifizierung gestatten:** Aktivieren Sie diese Option, um zu bestimmen, ob Clientanwendungen beim Herstellen einer Serververbindung die Kerberos-Authentifizierung zulassen.

**Zertifikat-Authentifizierung zulassen:** Aktivieren Sie diese Option, um zu bestimmen, ob Client-Anwendungen beim Herstellen einer Server-Verbindung die Zertifikat-Authentifizierung zulassen.

**Erweiterte Authentifizierung zulassen** Wählen Sie diese Option aus, um die erweiterte Authentifizierung zu aktivieren. Wenn Sie diese Option auswählen, können Clientanwendungen erweiterte Authentifizierung verwenden. Die erweiterte Authentifizierung bietet benutzerdefinierte Authentifizierungsprozesse und verschiedene Authentifizierungsoptionen, die auf dem Document Security-Server konfiguriert sind.

Wenn Sie die globalen Authentifizierungseinstellungen überschreiben, können Sie die für diese Richtlinie relevanten Authentifizierungsoptionen auswählen. Wenn Sie beispielsweise drei Authentifizierungsoptionen (Benutzername und Kennwort, Client-Zertifikat und erweiterte Authentifizierung) auf dem Server aktiviert haben, können Sie diese globale Einstellung außer Kraft setzen und für diese Richtlinie nur erweiterte Authentifizierung auswählen. Sie müssen sicherstellen, dass die Authentifizierungsoption, die Sie hier auswählen, bereits auf dem Server konfiguriert ist. In diesem Beispiel können Sie Kerberos nicht als Authentifizierungsoption auswählen, da es nicht auf dem Server konfiguriert ist.

>[!NOTE]
>
>Erweiterte Authentifizierung wird unter Apple Mac OS X mit Adobe Acrobat-Version 11.0.6 und höher unterstützt.

### Erweiterte Einstellungen {#advanced-settings}

Der Bereich Erweiterte Einstellungen enthält die folgenden Einstellungen:

**Dynamisches Wasserzeichen:** Wählen Sie ein Wasserzeichen aus, das dynamisch auf den Seiten eines Dokuments angezeigt werden soll (z. B. wenn ein Empfänger das Dokument druckt). Dynamische Wasserzeichen kennzeichnen ein Dokument eindeutig, wodurch die Vertraulichkeit des Dokuments gewährleistet und Urheberrechtsverletzungen verhindert werden. Beispielsweise kann der Administrator ein dynamisches Wasserzeichen konfigurieren, das das aktuelle Datum, den Benutzernamen oder die Kennung der Person, die das Dokument verwendet, oder den Namen der Richtlinie anzeigt, die zum Schutz des Dokuments verwendet wird. Ein Wasserzeichen kann auch benutzerdefinierten Text oder Grafikelemente anzeigen, sofern konfiguriert. Administratoren konfigurieren die Wasserzeichenoptionen, und Administratoren und Benutzer können sie auf Richtlinien anwenden.

(Siehe [Dynamische Wasserzeichen konfigurieren](/help/forms/using/admin-help/configuring-client-server-options.md#configure-dynamic-watermarks).

Wenn Sie eine Richtlinie bearbeiten und der Administrator ein konfiguriertes Wasserzeichen gelöscht hat, das Sie zuvor für diese Richtlinie ausgewählt haben, wird auf der Seite Richtlinie bearbeiten ein Hinweis angezeigt. Wenn Sie in diesem Fall das bearbeitete Dokument speichern, wählen Sie ein neues Wasserzeichen aus, wenn eines im Dokument angezeigt werden soll.

>[!NOTE]
>
>Bei Richtlinien, die anonymen Benutzerzugriff bieten, werden der Benutzername und die Kennung eines anonymen Benutzers nicht als Wasserzeichen angezeigt, selbst wenn Sie diesen Typ von Wasserzeichen auswählen.

**Nur zertifizierte Acrobat-Plug-Ins für PDF-Datei verwenden:** Bei Auswahl dieser Option für eine Richtlinie wird festgelegt, dass Acrobat 8.0 und höher im zertifizierten Modus ausgeführt werden muss, wenn durch die Richtlinie geschützte Dokumente geöffnet werden. Wenn Acrobat im zertifizierten Modus ausgeführt wird, werden keine Plug-ins von Drittanbietern geladen.

Wählen Sie diese Option aus, wenn Sie befürchten, dass ein Dokumentempfänger ein Plug-in schreibt, das die Dokumentschutzmaßnahmen in Acrobat 8.0 und höher umgehen kann. Wählen Sie diese Option nicht aus, wenn Ihre Dokumentempfänger für die Interaktion mit Dokumenten Plug-ins von Drittanbietern in Acrobat verwenden müssen.

Diese Option aktiviert nur den zertifizierten Modus in Acrobat 8.0 oder höher. Der Administrator muss den Zugriff für Acrobat 7.0 deaktivieren.

(Siehe [Document Security-Server konfigurieren](/help/forms/using/admin-help/configuring-client-server-options.md#configure-the-document-security-server).

Diese Option gilt nicht für Adobe Reader.

**Fehlermeldung „Zugriff verweigert“:** Eine Meldung, die immer dann angezeigt wird, wenn jemand versucht, ein richtliniengeschütztes Dokument ohne Zugriffsberechtigung zu öffnen. Diese Meldung wird in Acrobat angezeigt. Clients, die diese Nachricht nicht anzeigen können, zeigen eine Standardmeldung an, die angibt, dass der Zugriff verweigert wurde.

### Unveränderliche erweiterte Einstellungen {#unchangeable-advanced-settings}

Der Bereich Unveränderliche erweiterte Einstellungen enthält die folgenden Einstellungen. Sie können diese Einstellungen nach dem Speichern der Richtlinie nicht mehr ändern.

**Verschlüsselungsalgorithmus und Schlüssellänge:** Dient zum Schutz Ihrer Dokumente. Sie können aus folgenden Optionen auswählen:

* AES 128-Bit
* AES 256-Bit. Diese Option wird nur von Acrobat 9.0 und höher unterstützt. Um die AES 256-Verschlüsselung für PDF-Dateien zu verwenden, rufen Sie die Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy-Dateien ab und installieren Sie sie. Diese Dateien ersetzen die Dateien „local_policy.jar“ und „US_export_policy.jar“ im Ordner „[JAVE_HOME] /lib/security“. Falls Sie beispielsweise Sun JDK 1.6 verwenden, kopieren Sie die heruntergeladenen Dateien in den Ordner „[dep-Stammordner]/Java/jdk1.6.0_26/lib/security“. Sie können diese Dateien von [Java SE-Downloads](https://java.sun.com/javase/downloads/index.jsp).
* Keine Verschlüsselung. Acrobat 9.0 und höher unterstützen diese Option derzeit. Wenn Sie diese Option auswählen, sind die Optionen für Dokumenteinschränkungen deaktiviert. Diese Option kann nützlich sein, wenn Sie Document Security für die Dokumentenprüfung oder Versionskontrolle verwenden, das Dokument jedoch nicht verschlüsseln möchten.

**Dokumenteinschränkungen:** Wählen Sie PDF-Dokumentkomponenten aus, die verschlüsselt werden sollen. Andere Clientanwendungen verschlüsseln das gesamte Dokument, jedoch keine verknüpften oder eingebetteten Dateien. Sie können aus folgenden Optionen auswählen:

* Das gesamte Dokument, einschließlich seiner Anlagen und Metadaten. *Metadaten* ist eine Information über das Dokument und seinen Inhalt, die Sie im Dialogfeld &quot;Dokumenteigenschaften&quot;oder im erweiterten Menü von Acrobat anzeigen können. In Acrobat können Sie Dateien unterschiedlicher Typen (z. B. Text-, Audio- und Videodateien) an PDF-Dokumente anhängen.
* Das Dokument und seine Anlagen, jedoch nicht die Metadaten.
* Nur die Dokumentanlagen. Sie können die Anlagen in einer PDF verschlüsseln, ohne den Dokumentinhalt zu verschlüsseln.

## Freigegebene Richtlinien aktivieren oder deaktivieren {#enable-or-disable-shared-policies}

Um eine freigegebene Richtlinie verfügbar zu machen, muss sie vom Administrator oder Richtliniensatzkoordinator aktiviert werden. Sie können neue Richtlinien oder zuvor deaktivierte Richtlinien aktivieren. Eine freigegebene Richtlinie, die Sie deaktivieren, wird weiterhin für Dokumente erzwungen, die mit dieser Richtlinie geschützt sind.

Neben einer deaktivierten Richtlinie wird ein rotes X angezeigt.

>[!NOTE]
>
>Administratoren können persönliche Richtlinien nicht deaktivieren und Benutzer können ihre eigenen Richtlinien nicht aktivieren und deaktivieren.

1. Klicken Sie auf der Document Security-Seite auf Richtlinien und dann auf die Registerkarte Richtliniensätze .
1. Klicken Sie auf den Namen des entsprechenden Richtliniensatzes und dann auf die Registerkarte Richtlinien .
1. Aktivieren Sie das Kontrollkästchen neben der entsprechenden Richtlinie, klicken Sie auf &quot;Aktivieren&quot;oder &quot;Deaktivieren&quot;und klicken Sie dann auf &quot;OK&quot;.

## Informationen zu Richtlinien anzeigen {#view-information-about-a-policy}

Auf der Registerkarte &quot;Meine Richtlinien&quot;können Sie nach persönlichen Richtlinien suchen.

Von Administratoren erstellte Richtliniensätze werden auf der Registerkarte &quot;Richtliniensätze&quot;der Seite &quot;Richtlinien&quot;mit Informationen zum Richtliniensatz aufgelistet, einschließlich dessen Namen, des Erstellungsdatums und der Änderung sowie einer Beschreibung. Klicken Sie auf einen Richtliniensatznamen, um dessen Details anzuzeigen. Richtliniensatzkoordinatoren mit Berechtigung zum Verwalten von Richtlinien können freigegebene Richtlinien in einem bestimmten Richtliniensatz erstellen.

Beim Erstellen oder Bearbeiten einer Richtlinie wird eine Seite angezeigt, auf der Sie Details wie Richtlinienname, Berechtigungsebenen, Vertraulichkeitseinstellungen und die in die Richtlinie einzubeziehenden Empfänger konfigurieren können.

Der Administrator kann die folgenden Vertraulichkeitseinstellungen für eine Richtlinie konfigurieren:

* Allgemeine Dokumentvertraulichkeitsoptionen, wie der Gültigkeitszeitraum des Dokuments und die Offline-Nutzungsdauer
* Die autorisierten Benutzer sowie die Dokumenteinschränkungen und -berechtigungen für jeden dieser Benutzer
* Erweiterte Dokumentvertraulichkeitsoptionen, einschließlich dynamischer Wasserzeichen und Dokumentverschlüsselung

Benutzer können die von ihnen erstellten Richtlinien und alle freigegebenen Richtlinien anzeigen, auf die sie Zugriff haben. Administratoren können alle freigegebenen und persönlichen Richtlinien anzeigen, die sich in Document Security befinden.

Sie können detailliertere Informationen zu einer Richtlinie anzeigen, die in der Liste angezeigt wird, einschließlich der in der Richtlinie enthaltenen Benutzer oder Gruppen und der für diese Benutzer festgelegten Vertraulichkeitseinstellungen.

>[!NOTE]
>
>Richtlinien, die Acrobat automatisch für die Empfänger von Dokumenten generiert, die an E-Mail-Nachrichten in Microsoft Outlook angehängt sind, werden nicht in der Richtlinienliste angezeigt. Sie können diese Richtlinien nur anzeigen, indem Sie die Seite &quot;Dokumentdetails&quot;für das zugehörige Dokument öffnen.

1. Klicken Sie auf der Document Security-Seite auf Richtlinien und dann auf die Registerkarte Meine Richtlinien .
1. Füllen Sie die Suchinformationen aus, um nach persönlichen Richtlinien zu suchen.
1. Wählen Sie die entsprechende Richtlinie aus der Liste aus.
1. Auf der Seite &quot;Richtliniendetails&quot;können Sie Details zur Richtlinie anzeigen, die Richtlinie bearbeiten oder Ereignisse im Zusammenhang mit der Richtlinie anzeigen.

## Suchen nach Richtlinien {#search-for-policies}

Administratoren können nach freigegebenen Richtlinien und persönlichen Richtlinien suchen, die von anderen Benutzern erstellt wurden.

1. Um nach einer freigegebenen Richtlinie zu suchen, klicken Sie auf &quot;Richtlinien&quot;und dann auf die Registerkarte &quot;Richtliniensätze&quot;. Klicken Sie auf einen Richtliniensatz in der Liste und dann auf die Registerkarte Richtlinien .

   Um nach einer persönlichen Richtlinie zu suchen, klicken Sie auf der Document Security-Seite auf &quot;Richtlinien&quot;und dann auf die Registerkarte &quot;Meine Richtlinien&quot;.

1. Wählen Sie in der Liste Suchen eine der folgenden Optionen aus:

   **Richtlinien-ID** Die Richtlinienidentifikationsnummer, die generiert wird, wenn ein Benutzer eine Richtlinie erstellt. Sie müssen die genaue Richtlinien-ID eingeben.

   **Richtlinienname:** Der Name der Richtlinie. Sie können nach einem Teil oder dem gesamten Richtliniennamen suchen.

1. Geben Sie in das Textfeld den entsprechenden Wert ein. Wenn Sie beispielsweise Richtlinienname ausgewählt haben, geben Sie den gesuchten Richtliniennamen ein.
1. Wählen Sie in der Liste &quot;Anzeigen&quot;die Anzahl der anzuzeigenden Ergebnisse aus und klicken Sie auf &quot;Suchen&quot;. Die Suchergebnisse werden angezeigt.
1. (Optional) Um Richtliniendetails anzuzeigen, klicken Sie auf die Richtlinie.

## Eine Richtlinie kopieren {#copy-a-policy}

Sie können eine vorhandene Richtlinie kopieren und mit einem neuen Namen und einer neuen Beschreibung speichern. Das Kopieren von Richtlinien ist eine effiziente Möglichkeit, neue Richtlinien mithilfe vorhandener Einstellungen zu erstellen.

Externe Benutzer können Richtlinien nur kopieren, wenn der Administrator diese Funktion aktiviert hat. Wenn Sie keine Richtlinien erstellen können, ist die Option Kopieren nicht verfügbar.

1. Klicken Sie auf der Document Security-Seite auf Richtlinien und dann auf die Registerkarte Meine Richtlinie .
1. Wählen Sie die entsprechende Richtlinie aus der Liste aus.
1. Klicken Sie auf der Seite &quot;Richtliniendetails&quot;auf Kopieren.
1. Geben Sie im Feld Neuer Richtlinienname den neuen Richtliniennamen ein. Geben Sie optional eine neue Beschreibung ein.

   Die folgenden Zeichen dürfen im Namen oder in der Beschreibung nicht verwendet werden:

   * Kleiner-als-Zeichen (&lt;)
   * Größer-als-Zeichen (>)
   * kaufmännisches Und-Zeichen (&amp;)
   * Einfaches Anführungszeichen (&#39;)
   * Doppeltes Anführungszeichen (&quot;)
   * umgekehrter Schrägstrich (\)
   * Schrägstrich (/)

   Wenn Sie im Namen oder in der Beschreibung das folgende Zeichen verwenden, werden diese in Leerzeichen umgewandelt:

   * Wagenrücklauf (ASCII-Zeichen 13)
   * neue Zeile (ASCII-Zeichen 10).

   >[!NOTE]
   >
   >Sie können einen Richtliniennamen erstellen, der erweiterte Zeichen enthält. Wenn jedoch ein Vergleich zwischen zwei Zeichenfolgen durchgeführt wird, werden Zeichen mit und ohne Akzentzeichen wie &quot;e&quot;und &quot;é&quot;als identisch betrachtet. Wenn jemand eine Richtlinie erstellt, wird ein Vergleich durchgeführt, um zu überprüfen, ob bereits eine Richtlinie mit demselben Namen vorhanden ist. Der Vergleich kann nicht zwischen Namen unterscheiden, die mit Ausnahme von Akzentzeichen identisch sind. Es wird davon ausgegangen, dass die Richtlinie bereits zur Datenbank hinzugefügt und die neue nicht hinzugefügt wurde.

1. Klicken Sie auf OK.

## Richtlinie löschen {#delete-a-policy}

Sie können von Ihnen erstellte Richtlinien löschen. Administratoren können Richtlinien löschen, die von jedem Benutzer erstellt wurden. Richtliniensatzkoordinatoren können Richtlinien in ihren Richtliniensätzen löschen. Eine Richtlinie, die Sie löschen, wird weiterhin für Dokumente erzwungen, die mit dieser Richtlinie geschützt sind. Sie können mehrere Richtlinien gleichzeitig löschen.

Eingeladene Benutzer können Richtlinien nur löschen, wenn der Administrator diese Funktion aktiviert hat. Wenn Sie Richtlinien nicht löschen können, ist die Löschoption nicht verfügbar.

1. Klicken Sie auf der Document Security-Seite auf Richtlinien .
1. Klicken Sie auf die Registerkarte Meine Richtlinie .
1. Um eine freigegebene Richtlinie zu löschen, klicken Sie auf die Registerkarte Richtliniensätze und dann auf den entsprechenden Richtliniensatznamen.
1. Aktivieren Sie das Kontrollkästchen neben der entsprechenden Richtlinie und klicken Sie auf &quot;Löschen&quot;und anschließend auf &quot;OK&quot;.

>[!NOTE]
>
>Sie müssen die Clientanwendung verwenden, um Richtlinien aus Dokumenten zu entfernen. (Siehe Acrobat-Hilfe oder die entsprechende Hilfe zu Acrobat Reader DC-Erweiterungen.)

## Richtlinienliste sortieren {#sort-the-policy-list}

Sie können die Richtlinienliste nach Spaltenüberschrift sortieren, um Richtlinien leichter zu finden. Ein Dreieckssymbol neben der Spaltenüberschrift gibt an, welche Spalte derzeit zum Sortieren verwendet wird. Ein nach oben zeigendes Dreieck gibt eine aufsteigende Reihenfolge an, während ein nach unten zeigendes Dreieck eine absteigende Reihenfolge angibt.

1. Klicken Sie auf der Document Security-Seite auf Richtlinien und dann auf die Registerkarte Richtliniensatz .
1. Wählen Sie einen Richtliniensatz aus und klicken Sie auf die Registerkarte Richtlinien .
1. Klicken Sie auf die entsprechende Spaltenüberschrift.
1. Um die Sortierreihenfolge zu ändern, klicken Sie erneut auf die Spalte.
