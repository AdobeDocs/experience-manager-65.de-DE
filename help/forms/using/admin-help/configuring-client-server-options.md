---
title: Client- und Serveroptionen konfigurieren
seo-title: Client- und Serveroptionen konfigurieren
description: Erfahren Sie, wie Sie die verschiedenen Client- und Serveroptionen konfigurieren können, z. B. Einstellungen zur Serverkonfiguration, Document Security-Rollen und Ereignisrevidierung.
seo-description: Erfahren Sie, wie Sie die verschiedenen Client- und Serveroptionen konfigurieren können, z. B. Einstellungen zur Serverkonfiguration, Document Security-Rollen und Ereignisrevidierung.
uuid: 1f9f9886-726e-4fad-9ff8-0ff11eef653e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 0f069fbc-10c2-403e-9419-5e9920035d75
feature: Document Security
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '10275'
ht-degree: 85%

---


# Document Security-Server konfigurieren {#configure-the-document-security-server}

1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Serverkonfiguration“.
1. Konfigurieren Sie die Einstellungen und klicken Sie auf „OK“.

## Einstellungen zur Serverkonfiguration {#server-configuration-settings}

**Basis-URL:** Die Basis-Dokument-Sicherheits-URL, die den Servernamen und Anschluss enthält. Durch Anfügen von Informationen an die Basis-URL werden Verbindungs-URLs erstellt. /edc/Main.do wird beispielsweise angefügt, um auf die Webseiten zuzugreifen. Diese URL ermöglicht Benutzern auch , auf Einladungen externer Benutzer zur Registrierung zu antworten.

Wenn Sie IPv6 verwenden, geben Sie die Basis-URL als Computernamen oder den DNS-Namen ein. Wenn Sie eine numerische IP-Adresse verwenden, kann Acrobat die richtliniengeschützten Dateien nicht öffnen. Verwenden Sie auch die sichere HTTP-URL (HTTPS) für Ihren Server.

>[!NOTE]
>
>Die Basis-URL ist in durch Richtlinien geschützte Dateien eingebettet. Sie wird von Clientanwendungen verwendet, um sich wieder mit dem Server zu verbinden. Geschützte Dateien enthalten die Basis-URL auch dann weiter, wenn diese später geändert wird. Wenn Sie die Basis-URL ändern, müssen die Konfigurationsinformationen für alle sich mit dem Server verbindenden Clients geändert werden.

**Standardmäßige Offline-Nutzungsdauer:** Die Standarddauer, die ein Benutzer offline ein geschütztes Dokument verwenden kann. Diese Einstellung bestimmt den ursprünglichen Wert der Einstellung für die Automatische Offline-Nutzungsdauer, wenn Sie eine Richtlinie erstellen. (Siehe Richtlinien erstellen und bearbeiten.) Nach Ablauf der Nutzungsdauer muss der Empfänger das Dokument erneut synchronisieren, um es weiter verwenden zu können.

Weitere Informationen zur Funktionsweise der Offline-Nutzung und Synchronisation finden Sie unter [Primer zum Konfigurieren der Offline-Nutzung und Synchronisation](https://blogs.adobe.com/security/2009/05/primer_on_configuring_offline.html).

**Standardmäßige Offline-Synchronisierungszeit:** Die maximale Zeit, die ein Dokument offline verwendet werden kann, wenn es ursprünglich geschützt ist.

**Client-Sitzungszeitlimit:** Die Zeitspanne in Minuten, nach der Dokument Security die Verbindung trennt, wenn ein Benutzer, der über eine Clientanwendung angemeldet ist, nicht mit Dokument Security interagiert.

**Zugriff auf anonyme Benutzer zulassen:** Wählen Sie diese Option, um freigegebene und persönliche Richtlinien zu erstellen, die anonymen Benutzern das Öffnen richtliniengeschützter Dokumente ermöglichen. (Benutzer ohne Konto können auf das Dokument zugreifen, sich jedoch nicht bei Document Security anmelden oder andere richtliniengeschützte Dokumente nutzen.)

**Zugriff auf Version 7-Clients deaktivieren:** Gibt an, ob Benutzer mit Acrobat oder Reader 7.0 eine Verbindung zum Server herstellen können. Ist diese Option aktiviert, müssen Benutzer Acrobat oder Reader 8.0 oder höher verwenden, um Document Security-Vorgänge für PDF-Dokumente durchzuführen. Falls Richtlinien erfordern, dass Acrobat oder Reader 8.0 oder höher zum Öffnen richtliniengeschützter Dokumente im zertifizierten Modus ausgeführt werden muss, müssen Sie den Zugriff auf Acobat oder Reader 7 deaktivieren. (Siehe Die Dokumentberechtigungen für Benutzer und Gruppen angeben.)

**Offline-Zugriff pro** Dokument zulassenWählen Sie diese Option, um den Offline-Zugriff pro Dokument festzulegen. Wenn diese Einstellung aktiviert ist, kann der Benutzer nur auf die Dokumente offline zugreifen, die er mindestens einmal online geöffnet hat.

**Authentifizierung mit Benutzername und Kennwort zulassen:** Wählen Sie diese Option, damit Clientanwendungen beim Herstellen einer Serververbindung die Authentifizierung mit Benutzername und Kennwort verwenden können.

**Kerberos-Authentifizierung zulassen:** Wählen Sie diese Option, damit Clientanwendungen beim Herstellen einer Verbindung mit dem Server die Kerberos-Authentifizierung verwenden können.

**Client-Zertifikatauthentifizierung zulassen:** Wählen Sie diese Option, damit Clientanwendungen beim Herstellen einer Verbindung mit dem Server die Zertifikatauthentifizierung verwenden können.

**Erweiterte** Authentifizierung zulassenWählen Sie aus, um die erweiterte Authentifizierung zu aktivieren, und geben Sie dann die Landing-URL der erweiterten Authentifizierung ein.

Durch Auswahl dieser Option werden Clientanwendungen für die Verwendung der erweiterten Authentifizierung aktiviert. Mit erweiterter Authentifizierung können auf dem AEM Forms-Server angepasste Authentifizierungsprozesse und verschiedene Authentifizierungsoptionen konfiguriert werden. Beispielsweise können Benutzer die SAML-basierte Authentifizierung anstelle des AEM Forms-Benutzernamens/Kennworts von Acrobat- und Reader-Clients aus nutzen. Standardmäßig enthält die Startseiten-URL „*localhost*“ als den Servernamen. Ersetzen Sie den Servernamen durch einen voll qualifizierten Hostnamen. Der Hostname in der Startseiten-URL wird automatisch mit der Basis-URL gefüllt, wenn die erweiterte Authentifizierung noch nicht aktiviert ist. Siehe [Erweiterten Authentifizierungsanbieter hinzufügen](configuring-client-server-options.md#add-the-extended-authentication-provider). 

***Hinweis **: Erweiterte Authentifizierung wird auf Apple Mac OS X mit Adobe Acrobat ab Version 11.0.6 unterstützt.*

**Bevorzugte HTML-Steuerelementbreite für erweiterte** AuthentifizierungGeben Sie die Breite des Dialogfelds für erweiterte Authentifizierung an, das in Acrobat zur Eingabe von Benutzeranmeldeinformationen geöffnet wird.

**Bevorzugte Höhe des HTML-Steuerelements für erweiterte** AuthentifizierungGeben Sie die Höhe des Dialogfelds für erweiterte Authentifizierung an, das in Acrobat zur Eingabe der Benutzeranmeldeinformationen geöffnet wird.

***Hinweis **: Die Breite und Höhe dieses Dialogfelds sind wie folgt begrenzt:*
Breite: Minimum = 400, Maximum = 900

Höhe: Minimum = 450; Maximum = 800

**Zwischenspeichern von Clientberechtigungen aktivieren:** Wählen Sie diese Option, damit Benutzer ihre Anmeldeinformationen (Benutzername und Kennwort) zwischenspeichern können. Wenn die Anmeldeinformationen von Benutzern zwischengespeichert werden, müssen sie sie beim Öffnen eines Dokument oder beim Klicken auf die Schaltfläche „Aktualisieren“ auf der Seite „Sicherheitsrichtlinien verwalten“ in Adobe Acrobat nicht immer eingeben. Sie können die Anzahl der Tage angeben, nach deren Ablauf die Benutzer die Anmeldeinformationen erneut eingeben müssen. Bei Festlegung auf 0 Tage werden die Anmeldeinformationen unbegrenzt zwischengespeichert.

## Konfigurieren von Document Security-Benutzern und -Administratoren {#configuring-document-security-users-and-administrators}

### Zuweisen von Document Security-Rollen zu Administratoren {#assigning-document-security-roles-to-administrators}

Ihre AEM Forms-Umgebung enthält einen oder mehrere Administratorbenutzer, die die entsprechenden Berechtigungen zum Erstellen von Benutzern und Gruppen haben. Wenn Ihr Unternehmen Document Security verwendet, muss mindestens einem Administrator auch das Recht zugewiesen sein, eingeladene und lokale Benutzer zu verwalten.

Die Administratoren müssen auch die Administration Console-Benutzerrolle haben, um auf Administration Console zugreifen zu können. (Siehe [Rollen erstellen und konfigurieren](/help/forms/using/admin-help/creating-configuring-roles.md#creating-and-configuring-roles).)

### Sichtbare Benutzer und Gruppen konfigurieren  {#configuring-visible-users-and-groups}

Um bei Suchen anhand von Benutzerrichtlinien Benutzer und Gruppen in ausgewählten Domänen anzuzeigen, muss ein Superadministrator oder Richtliniensatzadministrator (in User Management erstellte) Domänen auswählen und der Liste der sichtbaren Benutzer und Gruppen für jeden Richtliniensatz hinzufügen.

Diese Liste wird dem Richtliniensatzkoordinator angezeigt und dient zum Einschränken der Domänen, die der Endbenutzer beim Auswählen von Benutzern oder Gruppen durchsuchen kann, die Richtlinien hinzugefügt werden sollen. Wird dieser Schritt nicht durchgeführt, kann der Richtliniensatzkoordinator keine der Richtlinie hinzuzufügenden Benutzer oder Gruppen finden. Es kann mehrere Richtliniensatzkoordinatoren für einen Richtliniensatz geben.

1. Richten Sie nach der Installation und Konfiguration der AEM Forms-Umgebung mit Document Security alle gewünschten Domänen in User Management ein. <!-- Fix broken link (See Setting up and managing domains) -->

   ***Hinweis **: Das Erstellen von Domänen muss vor dem Erstellen von Richtlinien erfolgen.*

1. Klicken Sie in Administration Console auf „Dienste“ > „Document Management“ > „Richtlinien“ und dann auf die Registerkarte „Richtliniensätze“.
1. Wählen Sie den globalen Richtliniensatz aus und klicken Sie auf die Registerkarte „Sichtbare Benutzer und Gruppen“.
1. Klicken Sie auf „Domäne(n) hinzufügen“ und fügen Sie den Anforderungen entsprechend vorhandene Domänen hinzu.
1. Wechseln Sie zu „Dienste“ > „Document Security“ > „Meine Richtlinien“ und klicken Sie auf die Registerkarte „Sichtbare Benutzer und Gruppen“.
1. Klicken Sie auf „Domäne(n) hinzufügen“ und fügen Sie den Anforderungen entsprechend vorhandene Domänen hinzu.

## Erweiterten Authentifizierungsanbieter hinzufügen  {#add-the-extended-authentication-provider}

AEM Forms enthält eine Beispielkonfiguration, die Sie für Ihre Umgebung anpassen können. Führen Sie die folgenden Schritte durch:

>[!NOTE]
>
>Erweiterte Authentifizierung wird auf Apple Mac OS X mit Adobe Acrobat ab Version 11.0.6 unterstützt.

1. Mit der WAR-Beispieldatei können Sie diese Konfiguration bereitstellen. Anweisungen finden Sie in dem entsprechenden Installationshandbuch für Ihren Anwendungsserver.
1. Vergewissern Sie sich, dass der Formularserver einen voll qualifizierten Namen anstelle von IP-Adressen als Basis-URL hat und dass es sich um eine HTTPS-URL handelt. Siehe [Serverkonfigurationseinstellungen](configuring-client-server-options.md#server-configuration-settings).
1. Aktivieren Sie die erweiterte Authentifizierung über die Serverkonfigurationsseite. Siehe [Serverkonfigurationseinstellungen](configuring-client-server-options.md#server-configuration-settings).
1. Fügen Sie die erforderliche SSO-Umleitungs-URL in der User Management-Konfigurationsdatei hinzu. Siehe [SSO-Umleitungs-URLs für erweiterte Authentifizierung hinzufügen](configuring-client-server-options.md#add-sso-redirect-urls-for-extended-authentication).

### Umleitungs-URLs für erweiterte Authentifizierung hinzufügen  {#add-sso-redirect-urls-for-extended-authentication}

Wenn die erweiterte Authentifizierung aktiviert ist, wird beim Öffnen eines richtliniengeschützten Dokuments in Acrobat XI oder Reader XI ein Dialogfeld für die Authentifizierung angezeigt. Dieses Dialogfeld lädt die HTML-Seite, die Sie als Startseiten-URL für erweiterte Authentifizierung in den Document Security-Servereinstellungen angegeben haben. Siehe [Serverkonfigurationseinstellungen](configuring-client-server-options.md#server-configuration-settings).

>[!NOTE]
>
>Erweiterte Authentifizierung wird auf Apple Mac OS X mit Adobe Acrobat ab Version 11.0.6 unterstützt.

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Konfiguration“ > „Konfigurationsdateien importieren und exportieren“.
1. Klicken Sie auf „Exportieren“ und speichern Sie die Konfigurationsdatei auf Ihrer Festplatte.
1. Öffnen Sie die Datei in einem Editor und suchen Sie den Knoten „AllowedUrls“.
1. Fügen Sie im `AllowedUrls`-Knoten die folgenden Zeilen hinzu: `<entry key="sso-l" value="/ssoexample/login.jsp"/> <entry key="sso-s" value="/ssoexample"/> <entry key="sso-o" value="/ssoexample/logout.jsp"/>`

   ```xml
   <entry key="sso-l" value="/ssoexample/login.jsp"/>
   <entry key="sso-s" value="/ssoexample"/>
   <entry key="sso-o" value="/ssoexample/logout.jsp"/>
   ```

1. Speichern Sie die Datei und importieren Sie dann die aktualisierte Datei von der Seite &quot;Manuelle Konfiguration&quot;: Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Konfiguration&quot;> &quot;Konfigurationsdateien importieren und exportieren&quot;.

## Offline-Sicherheit konfigurieren {#configuring-offline-security}

Document Security bietet die Möglichkeit, richtliniengeschützte Dokumente offline, d. h. ohne eine Internet- oder Netzwerkverbindung, zu nutzen. Für diese Möglichkeit ist es erforderlich, dass die Richtlinie den Offline-Zugriff zulässt, wie unter [Die Dokumentberechtigungen für Benutzer und Gruppen angeben](/help/forms/using/admin-help/creating-policies.md#specify-the-document-permissions-for-users-and-groups) beschrieben. Bevor ein Dokument mit einer solchen Richtlinie offline genutzt werden kann, muss der Empfänger das Dokument bei bestehender Internet-/Netzwerkverbindung öffnen und den Offline-Zugriff aktivieren, indem bei Aufforderung auf „Ja“ geklickt wird. Der Empfänger wird ggf. dazu aufgefordert, seine Identität zu authentifizieren. Der Empfänger kann anschließend Dokumente offline für die in der Richtlinie angegebenen Offline-Nutzungsdauer verwenden.

Nach Ende der Offline-Nutzungsdauer muss der Empfänger das Dokument wieder mit Document Security synchronisieren, indem er entweder ein Dokument online öffnet oder einen Acrobat-Befehl oder einen Acrobat Reader DC Extensions-Menübefehl zum Synchronisieren verwendet. (Siehe *Acrobat-Hilfe* oder entsprechende *Acrobat Reader DC Extensions-Hilfe*.)

Da Dokumente, die einen Offline-Zugriff zulassen, die Zwischenspeicherung von Schlüsseldaten auf dem Computer erfordern, auf dem die Dateien offline gespeichert werden, kann die Datei Risiken ausgesetzt sein, wenn ein nicht befugter Benutzer sich die Schlüsseldaten verschafft. Um dies zu verhindern, können Schlüssel gemäß einem Zeitplan oder manuell aktualisiert werden, damit nicht autorisierte Personen im Besitz des Schlüssels keinen Zugriff auf das Dokument erhalten.

### Eine standardmäßige Offline-Nutzungsdauer festlegen  {#set-a-default-offline-lease-period}

Empfänger richtliniengeschützter Dokumente können Dokumente für die Anzahl der in der Richtlinie angegebenen Tage offline schalten. Nach einer einleitenden Synchronisierung des Dokuments mit Document Security kann der Empfänger das Dokument bis zum Ablauf der Offline-Nutzungsdauer offline verwenden. Nach Ablauf der Nutzungsdauer muss der Empfänger das Dokument online schalten und sich anmelden, um mit Document Security zu synchronisieren, damit er das Dokument weiter verwenden kann.

Sie können eine standardmäßige Offline-Nutzungsdauer festlegen. Die Nutzungsdauer kann vom Standard abweichend geändert werden, wenn ein Benutzer eine Richtlinie erstellt oder bearbeitet.

1. Klicken Sie auf der Document Security-Seite auf „Konfiguration“ > „Serverkonfiguration“.
1. Geben Sie in das Feld Standardmäßige Offline-Nutzungsdauer die Anzahl der für diesen Zeitraum gewünschten Tage ein.
1. Klicken Sie auf OK.

### Schlüsselaktualisierungen verwalten  {#manage-key-rollovers}

Document Security nutzt zum Schützen von Dokumenten Verschlüsselungsalgorithmen und Lizenzen. Beim Verschlüsseln eines Dokuments wird von Document Security ein *DocKey* genannter Entschlüsselungsschlüssel generiert und verwaltet, der an die Clientanwendung übergeben wird. Wenn die Richtlinie zum Schutz eines Dokuments einen Offline-Zugriff zulässt, wird zudem ein *Hauptschlüssel* genannter Offline-Schlüssel für jeden Benutzer generiert, der Offline-Zugriff auf das Dokument hat.

>[!NOTE]
>
>Wenn noch kein Hauptschlüssel vorhanden ist, generiert Document Security einen, um ein Dokument zu schützen.

Um ein richtliniengeschütztes Dokument offline zu öffnen, muss der Computer des Benutzers über den entsprechenden Hauptschlüssel verfügen. Der Computer empfängt den Hauptschlüssel, wenn der Benutzer eine Synchronisierung mit Document Security durchführt (d. h. ein geschütztes Dokument online öffnet). Wenn dieser Hauptschlüssel nicht mehr geheim ist, kann der Inhalt von Dokumenten, auf die der Benutzer offline Zugriff hat, offen gelegt werden.

Eine Möglichkeit der Eindämmung dieser Bedrohung von Offline-Dokumenten besteht darin, den Offline-Zugriff auf besonders vertrauliche Dokumente zu vermeiden. Eine weitere Möglichkeit ist die regelmäßige Aktualisierung der Hauptschlüssel. Wenn Document Security den Schlüssel aktualisiert, kann mit vorhandenen Schlüsseln nicht mehr auf die richtliniengeschützten Dokumente zugegriffen werden. Wenn ein nicht autorisierter Benutzer sich einen Hauptschlüssel von einem gestohlenen Laptop verschafft, kann dieser Schlüssel nicht für den Zugriff auf das geschützte Dokument verwendet werden, nachdem eine Aktualisierung erfolgt ist. Wenn Sie vermuten, dass ein bestimmter Hauptschlüssel nicht mehr geheim ist, können Sie den Schlüssel manuell aktualisieren.

Sie sollten sich dessen bewusst sein, dass eine Schlüsselaktualisierung alle Hauptschlüssel und nicht nur einen betrifft. Der Vorgang sorgt zudem für eine Verringerung der Skalierbarkeit des Systems, da Clients für den Offline-Zugriff mehr Schlüssel speichern müssen. Die Schlüsselaktualisierung erfolgt standardmäßig alle 20 Tage. Es wird empfohlen, diesen Wert nicht auf weniger als 14 Tage festzulegen, da Benutzer sonst ggf. am Anzeigen von Offline-Dokumenten gehindert werden und die Systemleistung beeinträchtigt wird.

Im folgenden Beispiel ist Schlüssel1 der ältere der beiden Hauptschlüssel und Schlüssel2 ist der neuere. Wenn Sie zum ersten Mal auf die Schaltfläche „Schlüssel jetzt aktualisieren“ klicken, wird Schlüssel1 ungültig und ein neuer gültiger Hauptschlüssel (Schlüssel3) wird generiert. Die Benutzer erhalten bei der Synchronisierung mit Document Security in der Regel dann Schlüssel3, wenn ein geschütztes Dokument online geöffnet wird. Die Benutzer müssen jedoch erst mit Document Security synchronisieren, wenn sie die in der Richtlinie angegebene maximale Offline-Nutzungsdauer erreicht haben. Nach der ersten Schlüsselaktualisierung können Offline-Benutzer Offline-Dokumente, einschließlich der durch Schlüssel3 geschützten Dokumente, so lange öffnen, bis sie die maximale Offline-Nutzungsdauer erreicht haben. Wenn Sie ein zweites Mal auf die Schaltfläche „Schlüssel jetzt aktualisieren“ klicken, wird Schlüssel2 ungültig und Schlüssel4 wird erstellt. Benutzer, die während der beiden Schlüsselaktualisierungen offline sind, können durch Schlüssel3 oder Schlüssel4 geschützte Dokumente erst wieder öffnen, wenn sie eine Synchronisierung mit Document Security ausgeführt haben.

**Zeitintervall der Schlüsselaktualisierung ändern**

Zum Schutz der Vertraulichkeit bei der Nutzung von Offline-Dokumenten bietet Document Security eine automatische Schlüsselaktualisierungsoption mit einem Standardzeitintervall von 20 Tagen. Sie können dieses Aktualisierungsintervall ändern. Es wird jedoch empfohlen, diesen Wert nicht auf weniger als 14 Tage festzulegen, da Benutzer sonst ggf. am Anzeigen von Offline-Dokumenten gehindert werden und die Systemleistung beeinträchtigt wird.

1. Klicken Sie auf der Document Security-Seite auf „Konfiguration“ > „Schlüsselverwaltung“.
1. Geben Sie in das Feld „Zeitintervall für Schlüsselaktualisierungen“ die Anzahl der für diesen Zeitraum gewünschten Tage ein.
1. Klicken Sie auf OK.

**Hauptschlüssel manuell aktualisieren**

Um die Vertraulichkeit von Offline-Dokumenten zu wahren, können Sie Hauptschlüssel manuell aktualisieren. Es ist ggf. erforderlich, einen Schlüssel manuell zu aktualisieren, wenn sich ein nicht autorisierter Benutzer den Schlüssel von einem Computer verschafft hat, auf dem der Schlüssel zum Ermöglichen des Offline-Zugriffs auf ein Dokument zwischengespeichert ist.

>[!NOTE]
>
>Vermeiden Sie zu häufige manuelle Aktualisierungen, da dadurch alle Hauptschlüssel und nicht nur einer aktualisiert werden, was Benutzer vorübergehend an der Offline-Anzeige neuer Dokumente hindern kann.

Die Hauptschlüssel müssen zweimal aktualisiert werden, bevor bereits vorhandene Schlüssel auf Client-Computern ihre Gültigkeit verlieren. Client-Computer, die über ungültige Hauptschlüssel verfügen, müssen eine erneute Synchronisierung mit dem Document Security-Dienst ausführen, um die neuen Hauptschlüssel zu erhalten.

1. Klicken Sie auf der Document Security-Seite auf „Konfiguration“ > „Schlüsselverwaltung“.
1. Klicken Sie auf „Schlüssel jetzt aktualisieren“ und dann auf „OK“.
1. Warten Sie ungefähr zehn Minuten. Die folgende Protokollmeldung wird im Serverprotokoll angezeigt: `Done RightsManagement key rollover for`*N* `principals` Dabei steht *N* für die Anzahl der Benutzer im Document Security-System.
1. Klicken Sie auf „Schlüssel jetzt aktualisieren“ und dann auf „OK“.
1. Warten Sie ungefähr zehn Minuten.

## Ereignisprüfungs- und Datenschutzeinstellungen konfigurieren  {#configuring-event-auditing-and-privacy-settings}

Document Security kann Informationen zu Ereignissen im Zusammenhang mit dem Arbeiten mit richtliniengeschützten Dokumenten, Richtlinien, Administratoren und dem Server prüfen und aufzeichnen. Sie können eine Ereignisprüfung konfigurieren und die Typen zu prüfender Ereignisse angeben. Um Ereignisse für ein bestimmtes Dokument zu prüfen, muss die Prüfoption für die Richtlinie ebenfalls aktiviert sein.

Ist die Prüfung aktiviert, können Sie Details zu geprüften Ereignissen auf der Seite „Ereignisse“ anzeigen. Document Security-Benutzer können auch gezielt Ereignisse für die von ihnen selbst verwendeten oder erstellten richtliniengeschützten Dokumente anzeigen.

Sie können die folgenden zu prüfenden Ereignistypen auswählen:

* Ereignisse bei richtliniengeschützten Dokumenten, z. B. Versuche autorisierter bzw. nicht autorisierter Benutzer, Dokumente zu öffnen
* Richtlinienereignisse wie das Erstellen, Ändern, Löschen, Aktivieren und Deaktivieren von Richtlinien
* Benutzerereignisse, z. B. Einladungen und Registrierungen externer Benutzer, Aktivierung und Deaktivierung von Benutzerkonten, Änderungen von Benutzerkennwörtern und Aktualisierungen von Profilen
* AEM Forms-Ereignisse, z. B. Nichtübereinstimmungen von Versionen, nicht verfügbare Ordnerserver und Autorisierungsanbieter und Änderungen von Serverkonfigurationen

### Ereignisprüfung aktivieren oder deaktivieren  {#enable-or-disable-event-auditing}

Sie können die Prüfung von Ereignissen im Zusammenhang mit dem Server, richtliniengeschützten Dokumenten, Richtlinien, Richtliniensätzen und Benutzern aktivieren bzw. deaktivieren. Wenn Sie die Ereignisprüfung aktivieren, können Sie alle möglichen Ereignisse oder bestimmte Ereignisse in die Prüfung einbeziehen.

Wenn Sie die Serverprüfung aktivieren, können Sie die geprüften Ereignisse auf der Seite „Ereignisse“ anzeigen.

1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Prüfungs- und Datenschutzeinstellungen“.
1. Um die Serverprüfung zu konfigurieren wählen Sie unter „Serverprüfung aktivieren“ entweder „Ja“ oder „Nein“ aus.
1. Führen Sie bei Wahl von „Ja“ unter jeder Ereigniskategorie einen der folgenden Schritte aus, um zu die prüfenden Optionen auszuwählen:

   * Um alle Ereignisse in der Kategorie zu prüfen, wählen Sie „Alle“.
   * Um nur bestimmte Ereignisse zu prüfen, deaktivieren Sie „Alle“, und aktivieren Sie anschließend die Kontrollkästchen neben den zu prüfenden Ereignissen.

      (Siehe [Ereignisprüfungsoptionen](configuring-client-server-options.md#event-auditing-options).)

1. Klicken Sie auf OK.

>[!NOTE]
>
>Verwenden Sie beim Arbeiten mit Webseiten nicht die Schaltflächen im Browser (z. B. die Schaltfläche „Zurück“, die Schaltfläche „Aktualisieren“ oder die Pfeilschaltflächen „Zurück“ und „Vorwärts“), da dies zu unerwünschten Problemen bei der Erfassung und Anzeige von Daten führen kann.

### Datenschutzbenachrichtigung aktivieren oder deaktivieren  {#enable-or-disable-privacy-notification}

Sie können eine Datenschutzbenachrichtigung aktivieren bzw. deaktivieren. Beim Aktivieren der Datenschutzbenachrichtigung wird eine Meldung eingeblendet, wenn ein Empfänger versucht, ein richtliniengeschütztes Dokument zu öffnen. Die Meldung informiert den Benutzer, dass die Dokumentnutzung geprüft wird. Sie können auch eine URL angeben, auf die der Benutzer zum Anzeigen einer Seite mit Datenschutzrichtlinien, falls vorhanden, klicken kann.

1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Prüfungs- und Datenschutzeinstellungen“.
1. Um die Datenschutzbenachrichtigung zu konfigurieren, wählen Sie unter „Datenschutzbestimmung aktivieren“ entweder „Ja“ oder „Nein“ aus.

   Wenn die an ein Dokument angehängte Richtlinie Zugriff durch anonyme Benutzer zulässt und wenn die Option „Datenschutzbestimmung aktivieren“ auf „Nein“ festgelegt ist, wird der Benutzer nicht aufgefordert, sich anzumelden, und die Datenschutzbenachrichtigung wird nicht angezeigt.

   Wenn die an ein Dokument angehängte Richtlinie keinen Zugriff durch anonyme Benutzer zulässt, wird diesem die Datenschutzbenachrichtigung angezeigt.

1. Geben Sie, falls möglich, in das Feld „Datenschutz-URL“ die URL der Seite mit den Datenschutzrichtlinien ein. Wenn das Feld „Datenschutz-URL“ leer gelassen wird, wird die Seite mit den Datenschutzeinstellungen von adobe.com angezeigt.
1. Klicken Sie auf OK.

>[!NOTE]
>
>Wenn Sie die Datenschutzhinweise deaktivieren, wird nicht gleichzeitig die Prüfung von Dokumentverwendung deaktiviert. Vordefinierte Prüfaktionen und benutzerdefinierte Aktionen, die über erweiterte Nutzungsverfolgung unterstützt werden, können weiterhin Informationen zum Benutzerverhalten sammeln.

### Einen benutzerdefinierten Prüfereignistyp importieren  {#import-a-custom-audit-event-type}

Wenn Sie mit einer Document Security-fähigen Anwendung arbeiten, die die Prüfung zusätzlicher Ereignisse unterstützt, z. B. von für einen bestimmten Dateityp spezifischen Ereignissen, kann Ihnen ein Adobe-Partner die spezifischen Prüfungsereignisse bereitstellen, die Sie in Document Security importieren können. Wählen Sie diese Funktion nur, wenn Ihnen ein Adobe-Partner die spezifischen Prüfungsereignisse bereitgestellt hat.

1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Ereignisverwaltung“.
1. Klicken Sie auf Durchsuchen, um zu der zu importierenden XML-Datei zu wechseln, und klicken Sie dann auf Importieren.
1. Beim Importieren werden auf dem Server vorhandene benutzerdefinierte Prüfereignistypen überschrieben, wenn identische Kombinationen aus Ereigniscode und Namespace gefunden werden.
1. Klicken Sie auf OK.

### Benutzerdefinierten Prüfereignistyp löschen  {#delete-a-custom-audit-event-type}

1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Ereignisverwaltung“.
1. Aktivieren Sie das Kontrollkästchen neben dem benutzerdefinierten Prüfereignistypen, den Sie löschen möchten, und klicken Sie auf „Löschen“.
1. Klicken Sie auf OK.

### Prüfereignisse exportieren  {#export-audit-events}

Sie können Prüfereignisse zu Archivierungszwecken in eine Datei exportieren.

1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Ereignisverwaltung“.
1. Bearbeiten Sie unter „Prüfereignisse exportieren“ die Einstellungen den Anforderungen entsprechend. Sie können Folgendes angeben:

   * das Mindestalter der zu exportierenden Prüfereignisse;
   * die maximale Anzahl der Prüfereignisse, die eine Datei enthalten soll. Der Server erstellt auf der Basis dieses Wertes eine oder mehrere Dateien.
   * der Ordner, in dem die Datei erstellt wird. Dieser Ordner befindet sich auf dem Formularserver. Wenn der Ordnerpfad relativ ist, dann ist er relativ zum Stammordner für den Anwendungsserver.
   * das für die Prüfereignisdateien zu verwendende Präfix;
   * das Format der Datei, entweder eine CSV-Datei (Comma Separated Value, durch Komma getrennter Wert), die mit Microsoft Excel kompatibel ist, oder eine XML-Datei.

1. Klicken Sie auf „Exportieren“. Wenn Sie den Export abbrechen möchten, klicken Sie auf „Export abbrechen“. Wenn ein anderer Benutzer einen Export geplant hat, steht die Schaltfläche „Export abbrechen“ nicht zur Verfügung, bis der Löschvorgang beendet ist. Die Schaltfläche „Export abbrechen“ steht nicht zur Verfügung, wenn ein anderer Benutzer einen Löschvorgang geplant hat. Klicken Sie zum Überprüfen, ob ein geplanter Export- oder Löschvorgang gestartet oder beendet wurde, auf „Aktualisieren“.

### Prüfereignisse löschen  {#delete-audit-events}

Sie können Prüfereignisse, die älter als eine angegebene Anzahl von Tagen sind, löschen.

1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Ereignisverwaltung“.
1. Geben Sie unter „Prüfereignisse löschen“ die Anzahl der Tage im Feld „Prüfereignisse löschen, die älter sind als“ an.
1. Klicken Sie auf Löschen. Klicken Sie auf „Exportieren“. Wenn Sie den Löschvorgang abbrechen möchten, klicken Sie auf „Löschvorgang abbrechen“. Wenn ein anderer Benutzer einen Löschvorgang geplant hat, steht die Schaltfläche „Löschvorgang abbrechen“ nicht zur Verfügung, bis der Export beendet ist. Die Schaltfläche „Löschvorgang abbrechen“ steht nicht zur Verfügung, wenn ein anderer Benutzer einen Export geplant hat. Klicken Sie zum Überprüfen, ob ein geplanter Löschvorgang gestartet oder beendet wurde, auf „Aktualisieren“.

### Ereignisprüfungsoptionen  {#event-auditing-options}

Sie können die Ereignisprüfung aktivieren und deaktivieren und die zu prüfenden Ereignistypen angeben.

**Dokumentereignisse**

**Ansicht Dokument:** Ein Empfänger Ansicht ein richtliniengeschütztes Dokument.

**Dokument schließen:** Ein Empfänger schließt ein richtliniengeschütztes Dokument.

**Drucken mit niedriger** AuflösungEin Empfänger druckt ein richtliniengeschütztes Dokument mit der angegebenen Option für die niedrige Auflösung.

**Drucken mit hoher Auflösung:** Ein Empfänger druckt ein richtliniengeschütztes Dokument mit der angegebenen Option für die hohe Auflösung.

**hinzufügen Anmerkung zu Dokument:** Ein Empfänger fügt einem PDF-Dokument eine Anmerkung hinzu.

**Dokument sperren:** Ein Benutzer oder Administrator sperrt den Zugriff auf ein richtliniengeschütztes Dokument.

**Aufhebung der Sperre:** Ein Benutzer oder Administrator installiert den Zugriff auf ein richtliniengeschütztes Dokument erneut.

**Ausfüllen von Formularen:** Ein Empfänger gibt Informationen in ein PDF-Dokument ein, das ein ausfüllbares Formular ist.

**Richtlinie entfernt:** Ein Herausgeber entfernt eine Richtlinie aus einem Dokument, um den Sicherheitsschutz zu entfernen.

**URL der Sperrung des Dokuments ändern:** Ein Aufruf auf API-Ebene ändert die Sperr-URL, die angegeben wird, um auf ein neues Dokument zuzugreifen, das ein gesperrtes Dokument ersetzt.

**Dokument ändern:** Ein Empfänger ändert den Inhalt eines richtliniengeschützten Dokuments.

**Dokument unterschreiben:** Ein Empfänger signiert ein Dokument.

**Neues Dokument sichern:** Ein Benutzer wendet eine Richtlinie zum Schutz eines Dokuments an.

**Richtlinie auf Dokument wechseln:** Ein Benutzer oder Administrator schaltet die an ein Dokument angeschlossene Richtlinie.

**Dokument veröffentlichen als:** Ein neues Dokument, dessen documentName und Lizenz mit einem vorhandenen Dokument identisch sind, wird auf dem Server registriert und die Dokumente haben keine Beziehung zwischen über- und untergeordnet. Dieses Ereignis kann mit dem AEM Forms-SDK ausgelöst werden.

**Iterate-Dokument:** Ein neues Dokument, dessen documentName und Lizenz mit einem vorhandenen Dokument identisch sind, wird auf dem Server registriert und die Dokumente haben eine übergeordnete/untergeordnete Beziehung. Dieses Ereignis kann mit dem AEM Forms-SDK ausgelöst werden.

**Richtlinienereignisse**

**Erstellte Richtlinie:** Ein Benutzer oder Administrator erstellt eine Richtlinie.

**Richtlinie aktiviert:** Ein Administrator stellt eine Richtlinie zur Verfügung.

**Geänderte Richtlinie:** Ein Benutzer oder Administrator ändert eine Richtlinie.

**Richtlinie deaktiviert:** Ein Administrator macht eine Richtlinie nicht verfügbar.

**Gelöschte Richtlinie:** Ein Benutzer oder Administrator löscht eine Richtlinie.

**Richtlinieneigentümer ändern:** Ein Aufruf auf API-Ebene ändert den Richtlinieneigentümer.

**Benutzerereignisse**

**Gelöschter Benutzer:** Ein Administrator löscht ein Benutzerkonto.

**Eingeladene Benutzer registrieren:** Ein externer Benutzer registriert sich bei Dokument Security.

**Erfolgreiche Anmeldung:** Erfolgreiche Anmeldeversuche von Administratoren oder Benutzern.

**Eingeladene Benutzer:** Dokument Security lädt einen Benutzer zur Registrierung ein.

**Aktivierte Benutzer:** Externe Benutzer aktivieren ihre Konten über die URL in der Aktivierungen-E-Mail oder ein Administrator aktiviert ein Konto.

**Kennwort ändern:** Eingeladene Benutzer ändern ihr Kennwort oder ein Administrator setzt ein Kennwort für einen lokalen Benutzer zurück.

**Fehlgeschlagene Anmeldung:** Fehlgeschlagene Anmeldeversuche von Administratoren oder Benutzern.

**Benutzer deaktiviert:** Ein Administrator deaktiviert ein lokales Benutzerkonto.

**Profil-Aktualisierung:** Eingeladene Benutzer ändern ihren Namen, ihren Firmennamen und ihr Passwort.

**Konto gesperrt:** Ein Administrator sperrt ein Konto.

**Richtliniensatzereignisse**

**Erstellter Richtliniensatz:** Ein Administrator oder Richtliniensatzkoordinator erstellt einen Richtliniensatz.

**Gelöschter Richtliniensatz:** Ein Administrator oder Richtliniensatzkoordinator löscht einen Richtliniensatz.

**Geänderter Richtliniensatz:** Ein Administrator oder Richtliniensatzkoordinator ändert einen Richtliniensatz.

**Systemereignisse**

**Ordnersynchronisierung abgeschlossen:** Diese Informationen sind auf der Seite &quot;Ereignisse&quot;nicht verfügbar. Die aktuellen Informationen zur Ordnersynchronisierung, einschließlich des aktuellen Synchronisierungszustands und des Zeitpunktes der letzten Synchronisierung, werden auf der Seite „Domänenverwaltung“ angezeigt. Um Zugriff auf die Domänenverwaltung zu erhalten, klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domänenverwaltung“.

**Offline-Zugriff für Client aktivieren:** Ein Benutzer hat den Offline-Zugriff auf Dokumente aktiviert, die auf dem Benutzercomputer gegen den Server geschützt sind.

**Die synchronisierte** ClientClient-Anwendung muss Informationen mit dem Server synchronisieren, um Offline-Zugriff zu ermöglichen.

**Versionskonflikt:** Eine Version des AEM Forms SDK, die nicht mit dem Server kompatibel ist, versuchte eine Verbindung mit dem Server herzustellen.

**Informationen zur Ordnersynchronisierung:** Diese Informationen stehen auf der Seite &quot;Ereignisse&quot;nicht zur Verfügung. Die aktuellen Informationen zur Ordnersynchronisierung, einschließlich des aktuellen Synchronisierungszustands und des Zeitpunktes der letzten Synchronisierung, werden auf der Seite „Domänenverwaltung“ angezeigt. Um Zugriff auf die Domänenverwaltung zu erhalten, klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domänenverwaltung“.

**Änderung der Serverkonfiguration:** Änderungen an der Serverkonfiguration, die entweder über die Webseiten oder manuell durch Importieren einer Datei &quot;config.xml&quot;vorgenommen werden. Dazu zählen Änderungen der Basis-URL, Sitzungszeitlimits, Anmeldesperren, Ordnereinstellungen, Schlüsselaktualisierungen, SMTP-Servereinstellungen für die externe Registrierung, der Konfiguration von Wasserzeichen, Anzeigeoptionen usw.

## Erweiterte Nutzungsverfolgung konfigurieren  {#configuring-extended-usage-tracking}

Document Security kann mehrere benutzerdefinierte Ereignisse verfolgen, die an einem geschützten Dokument durchgeführt werden. Sie können das Verfolgen von Ereignissen auf dem Document Security-Server auf globaler Ebene oder auf einer Richtlinienebene aktivieren. Sie können JavaScript einrichten, um dann die gewünschten Aktionen zu erfassen, die innerhalb des geschützten PDF-Dokuments ausgeführt werden, wie das Klicken auf eine Schaltfläche oder Speichern des Dokuments. Diese Nutzungsdaten werden als XML-Datei in Schlüssel/Wert-Paaren übermittelt, die Sie für die weitere Analyse verwenden können. Benutzer, die auf die geschützten Dokumente zugreifen, können diese Verfolgung über die Clientanwendung zulassen oder ablehnen.

Wenn die Verfolgung auf globaler Ebene aktiviert ist, können Sie diese Einstellung auf der Richtlinienebene überschreiben und sie für eine bestimmte Richtlinien deaktivieren. Das Überschreiben auf Richtlinienebene ist nicht möglich, wenn die Verfolgung auf globaler Ebene deaktiviert ist. Die Liste der verfolgten Ereignissen wird automatisch an den Server gesendet, wenn die Vorgangszählung 25 erreicht, oder wenn das Dokument geschlossen wird. Sie können Ihr Skript auch so konfigurieren, dass die Liste der Ereignisse entsprechend Ihren Anforderungen explizit gesendet wird. Sie können die Ereignisverfolgung anpassen, indem Sie auf die Document Security-Objekteigenschaften und -methoden zugreifen.

Nachdem Sie die Verfolgung aktiviert haben, ist bei allen nachfolgend erstellten Richtlinien die Verfolgung standardmäßig aktiviert. Die Richtlinien, die erstellt wurden, bevor die Verfolgung auf dem Server aktiviert wurde, müssen manuell aktualisiert werden.

### Erweiterte Nutzungsverfolgung aktivieren oder deaktivieren  {#enable-or-disable-extended-usage-tracking}

Bevor Sie beginnen, müssen Sie sicherstellen, dass die Serverprüfung aktiviert ist. Unter [Ereignisprüfungs- und Datenschutzeinstellungen konfigurieren](configuring-client-server-options.md#configuring-event-auditing-and-privacy-settings) finden Sie weitere Informationen zur Prüfung.

1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Prüfungs- und Datenschutzeinstellungen“.
1. Um die erweiterte Nutzungsverfolgung von konfigurieren, wählen Sie unter „Verfolgung aktivieren“ „Ja“ oder „Nein“ aus.
1. Um die Option zum Zulassen der Sammlung von detaillierten Nutzungsdaten auf der Anmeldeseite zu konfigurieren, wählen Sie unter „Verfolgung standardmäßig aktivieren“ die Option „Ja“ oder „Nein“ aus.

Zum Anzeigen der verfolgten Ereignisse können Sie den Filter „Dokumentereignisse“ auf der Ereignisseite verwenden. Die Ereignisse, die mithilfe von JavaScript verfolgt werden, werden als detaillierte Nutzungsverfolgung bezeichnet. Unter [Ereignisse überwachen](/help/forms/using/admin-help/monitoring-events.md#monitoring-events) finden Sie weitere Informationen zu Ereignissen.

## Document Security-Anzeigeeinstellungen konfigurieren  {#configure-document-security-display-settings}

1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Anzeigeoptionen“.
1. Konfigurieren Sie die Einstellungen und klicken Sie auf „OK“.

### Anzeigeeinstellungen {#display-settings}

**Zeilen, die für Suchergebnisse angezeigt werden sollen:** Anzahl der Zeilen, die auf einer Seite angezeigt werden, wenn Suchvorgänge durchgeführt werden.

**Dialogfeld zur Client-Anmeldung anpassen**

Diese Einstellungen steuern den Text in der Anmeldeaufforderung, die angezeigt wird, wenn sich ein Benutzer über eine Clientanwendung bei Document Security anmeldet.

**Begrüßungstext:** Der Begrüßungstext, z. B. &quot;Bitte melden Sie sich mit Ihrem Benutzernamen und Kennwort an&quot;. Der Begrüßungstext sollte Informationen dazu enthalten, wie die Anmeldung bei Document Security erfolgen soll und wie ein Administrator oder anderer Support-Mitarbeiter in Ihrem Unternehmen kontaktiert werden kann, falls Hilfe benötigt wird. Externe Benutzer müssen ggf. einen Administrator kontaktieren, wenn sie ihr Kennwort vergessen haben oder Hilfe bei der Registrierung oder Anmeldung benötigen. Die maximale Länge des Begrüßungstexts ist 512 Zeichen.

**Benutzernamentext:** Die Textbeschriftung für das Feld &quot;Benutzername&quot;.

**Kennworttext:** Die Textbeschriftung für das Kennwortfeld.

**Anpassung des Dialogfelds für die Clientzertifikatauthentifizierung**

Diese Einstellungen steuern den im Dialogfeld für die Zertifikatauthentifizierung angezeigten Text.

**Wählen Sie &quot;Authentifizierungstyp&quot;:** Der Text, der angezeigt wird, um einen Benutzer zur Auswahl eines Authentifizierungstyps anzuweisen.

**Wählen Sie &quot;Zertifikattext&quot;:** Der Text, der angezeigt wird, um einen Benutzer zur Auswahl eines Zertifikattyps anzuweisen.

**Fehlertext &quot;Zertifikate nicht verfügbar&quot;:** Meldung mit bis zu 512 Zeichen, die angezeigt wird, wenn das ausgewählte Zertifikat nicht verfügbar ist.

**Client-Zertifikatanzeige anpassen**

**Aussteller von vertrauenswürdigen Berechtigungen nur anzeigen:** Wenn diese Option aktiviert ist, stellt die Clientanwendung dem Benutzer nur Zertifikate von Ausstellern zur Verfügung, denen AEM Formulare vertraut (siehe Verwalten von Zertifikaten und Berechtigungen). Wenn diese Option nicht ausgewählt ist, wird dem Benutzer eine Liste aller Zertifikate, die sich auf dem System des Benutzers befinden, vorgelegt.

## Dynamische Wasserzeichen konfigurieren  {#configure-dynamic-watermarks}

Mit Document Security können Sie die Standardeinstellungen für die dynamische Wasserzeichenoption konfigurieren, die Sie beim Erstellen von Richtlinien aktivieren können. Ein *Wasserzeichen* ist eine Grafik, mit welcher der Text im Dokument überlagert wird. Es dient zum Nachverfolgen des Inhalts eines Dokuments und kann zur Ermittlung einer unzulässigen Nutzung von Inhalten beitragen.

Ein dynamisches Wasserzeichen kann entweder aus Text, der aus definierten Variablen wie Benutzer-ID und -Datum und benutzerdefiniertem Text besteht, oder aus Multimediainhalt in einer PDF-Datei bestehen. Sie können Wasserzeichen mit mehreren Elementen konfigurieren, wobei für jedes Element eine eigene Position und Formatierung festgelegt wird.

Das Wasserzeichen kann nicht geändert werden und ist deshalb eine sichere Methode, um dafür zu sorgen, dass die Vertraulichkeit des Dokumentinhalts gewährleistet ist. Dynamische Wasserzeichen sorgen auch dafür, dass ein Wasserzeichen genügend benutzerspezifische Informationen anzeigt, um eine weitere Verteilung des Dokuments einzudämmen.

Das in einer Richtlinie angegebene Wasserzeichen wird im richtliniengeschützten Dokument angezeigt, wenn ein Empfänger das Dokument anzeigt oder druckt. Im Gegensatz zu dauerhaften Wasserzeichen wird ein dynamisches Wasserzeichen nicht im Dokument gespeichert. Dies ermöglicht die notwendige Flexibilität beim Bereitstellen eines Dokuments in einer Intranetumgebung, um sicherzustellen, dass die ID des spezifischen Benutzers von der anzeigenden Anwendung angezeigt wird. Wenn ein Dokument darüber hinaus mehrere Benutzer hat, ermöglicht die Verwendung eines dynamischen Wasserzeichens, dass Sie ein einzelnes Dokument anstatt mehrere Versionen mit je einem unterschiedlichen Wasserzeichen verwenden können. Das angezeigte Wasserzeichen gibt die Identität des aktuellen Benutzers an.

Beachten Sie, dass sich dynamische Wasserzeichen von den Wasserzeichen unterscheiden, die Benutzer dem Dokument in Acrobat direkt hinzufügen können. Dies bedeutet, dass ein richtliniengeschütztes Dokument zwei Wasserzeichen aufweisen kann.

### Überlegungen zum Erstellen von Wasserzeichen  {#considerations-when-creating-watermarks}

Sie können dynamische Wasserzeichen mit mehreren Wasserzeichenelementen erstellen, wobei jedes Element entweder als Text- oder PDF-Datei angegeben wird. Sie können einem Wasserzeichen bis zu fünf Elemente hinzufügen.

Wenn Sie ein textbasiertes Wasserzeichen auswählen, können Sie mehrere Elemente innerhalb des Wasserzeichens mit mehreren Texteinträgen angeben und die Position jedes Elements festlegen. Ordnen Sie diesen Elementen aussagekräftige Namen zu, z. B. Kopf- und Fußzeilen usw.

Wenn Sie beispielsweise unterschiedlichen Text in Kopf- und Fußzeilen, an den Rändern und im gesamten Dokument als Wasserzeichen angeben möchten, erstellen Sie mehrere Wasserzeichenelemente und legen Sie ihre Position fest. Wenn Sie möchten, dass die ID des Benutzers und das aktuelle Datum des Zugriffs auf das Dokument in der Kopfzeile, der Richtlinienname am rechten Rand und der benutzerdefinierte Text VERTRAULICH diagonal über das gesamte Dokument angezeigt werden, definieren Sie separate Wasserzeichenelemente des Typs „Text“ und geben Sie jeweils die Formatierung und Position an. Wenn das Wasserzeichen auf ein Dokument angewendet wird, werden alle Elemente im Wasserzeichen gleichzeitig auf das Dokument angewendet, und zwar in der Reihenfolge, in der sie dem Wasserzeichen hinzugefügt werden.

In der Regel verwenden Sie PDF-basierte Wasserzeichen, damit grafische Inhalte wie Logos oder Sonderzeichen wie Copyright oder eingetragene Marke eingefügt werden können.

Sie können die Anzahl von Wasserzeichenelementen und die PDF-Dateigröße ändern, indem Sie die Document Security-Konfigurationsdatei ändern. Siehe [Parameter der Wasserzeichenkonfiguration ändern](configuring-client-server-options.md#change-the-watermark-configuration-parameters).

Beachten Sie beim Konfigurieren von Wasserzeichen Folgendes:

* Sie können ein kennwortgeschütztes PDF-Dokument nicht als das Wasserzeichenelement verwenden. Wenn das Wasserzeichen, das Sie erstellen, andere Elemente enthält, die nicht mit einem Kennwort geschützt sind, werden sie als Teil des Wasserzeichens angewendet.
* Sie können die maximale PDF-Dateigröße ändern, die Sie als Wasserzeichenelement verwenden möchten. Allerdings beeinträchtigen große PDF-Dokumente, die als Wasserzeichen verwendet werden, die Leistung bei der Offlinesynchronisation von Dokumenten, auf die diese Wasserzeichen angewendet wurden. Siehe [Parameter der Wasserzeichenkonfiguration ändern](configuring-client-server-options.md#change-the-watermark-configuration-parameters).
* Nur die erste Seite der ausgewählten PDF-Datei wird als Wasserzeichen verwendet. Stellen Sie sicher, dass die Informationen, die als Wasserzeichen angezeigt werden sollen, auf der ersten Seite verfügbar sind.
* Obwohl Sie die Skalierung des PDF-Dokuments angeben können, beachten Sie die Seitengröße und das Layout des PDF-Dokuments, wenn Sie dieses als Wasserzeichen in der Kopf- oder Fußzeile oder an den Rändern verwenden möchten.
* Wenn Sie den Namen der Schriftart angeben, achten Sie darauf, dass Sie den Namen richtig eingeben. AEM Forms ersetzt die von Ihnen angegebene Schriftart, wenn sie auf dem Client-Computer, auf dem das Dokument geöffnet wird, nicht vorhanden ist.
* Wenn Sie Text als Wasserzeicheninhalt ausgewählt haben, können Sie für Seiten mit abweichender Breite nicht die Skalierungsoption „An Seite anpassen“ festlegen.
* Wenn Sie die Position der Wasserzeichenelemente angeben, stellen Sie sicher, dass nicht mehr als ein Element dieselbe Position hat. Wenn zwei Wasserzeichenelemente dieselbe Position haben, z. B. die Mittelposition, werden sie im Dokument als überlappend und in der Reihenfolge, in der sie dem Wasserzeichen hinzugefügt wurden, angezeigt.
* Wenn Sie den Schriftgrad und -typ angeben, stellen Sie sicher, dass der Text in voller Länge auf der Seite sichtbar ist. Textinhalte werden in neue Zeilen weitergeführt, sodass der Wasserzeicheninhalt, der an den Rändern angezeigt werden soll, mit den Inhaltsbereichen auf den Seiten überlappen kann. Wenn das Dokument jedoch in Acrobat 9 geöffnet wird, wird der Text über die einzeilige Textzeile hinaus abgeschnitten.

### Einschränkungen bei dynamischen Wasserzeichen  {#limitations-of-dynamic-watermarks}

Einige Clientanwendungen unterstützen möglicherweise keine dynamischen Wasserzeichen. Weitere Informationen finden Sie in der entsprechenden Acrobat Reader DC-Extensions-Hilfe. Darüber hinaus ist Folgendes zu den Versionen von Acrobat, die dynamische Wasserzeichen unterstützen, zu beachten:

* Sie können ein kennwortgeschütztes PDF-Dokument nicht als das Wasserzeichenelement verwenden.
* Acrobat- und Adobe Reader-Versionen (niedriger als Version 10) unterstützen folgende Wasserzeichen nicht:

   * PDF-Wasserzeichen
   * Mehrere Elemente im Wasserzeichen (Text/PDF)
   * Erweiterte Optionen wie Bereich von Seiten oder Anzeigeoptionen
   * Textformatierungsoptionen wie Angabe von Schriftart, -name und -farbe. Allerdings zeigen niedrigere Versionen von Acrobat und Reader den Textinhalt in der Standardschrift und -farbe an.

* Acrobat 9.0 und niedrigere Versionen: Acrobat 9.0 und niedrigere Versionen unterstützen keine Richtliniennamen in dynamischen Wasserzeichen. Wenn Acrobat 9.0 ein richtliniengeschütztes Dokument mit einem dynamischen Wasserzeichen öffnet, das einen Richtliniennamen oder andere dynamische Daten enthält, wird das Wasserzeichen ohne den Richtliniennamen angezeigt. Wenn das dynamische Wasserzeichen nur den Richtliniennamen enthält, zeigt Acrobat eine Fehlermeldung an

### Eine Vorlage für dynamische Wasserzeichen hinzufügen  {#add-a-dynamic-watermark-template}

Sie können Vorlagen für dynamische Wasserzeichen anlegen. Diese Vorlagen stehen als Konfigurationsoption für Richtlinien zur Verfügung, die von Administratoren oder Benutzern erstellt werden.

>[!NOTE]
>
>Die Konfigurationsinformationen dynamischer Wasserzeichen werden beim Exportieren einer Konfigurationsdatei nicht zusammen mit anderen Konfigurationsinformationen erfasst.

1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Wasserzeichen“.
1. Klicken Sie auf Neu.
1. Geben Sie in das Feld „Name“ einen Namen für das neue Wasserzeichen ein.

   ***Hinweis **: Einige Sonderzeichen können nicht in den Namen oder Beschreibungen von Wasserzeichen oder Wasserzeichenelementen verwendet werden. Weitere Informationen finden Sie unter [Überlegungen zum Bearbeiten von Richtlinien](/help/forms/using/admin-help/creating-policies.md#considerations-for-editing-policies).*

1. Geben Sie unter „Name“ neben dem Pluszeichen einen aussagekräftigen Namen für das Wasserzeichenelement ein, z. B. „Kopfzeile“. Fügen Sie dann eine neue Beschreibung hinzu. Anschließend klicken Sie auf das Pluszeichen, um die Optionen anzuzeigen.
1. Wählen Sie unter „Quelle“ den Typ des Wasserzeichens, entweder „Text“ oder „PDF“.
1. Wenn Sie „Text“wählen, gehen Sie wie folgt vor:

   * Wählen Sie die zu berücksichtigenden Wasserzeichentypen. Wenn Sie „Benutzerdefinierter Text“ auswählen, geben Sie in das Feld daneben den für das Wasserzeichen anzuzeigenden Text ein. Beachten Sie die Textlänge des Wasserzeichens.
   * Geben Sie die Eigenschaften der Textformatierung wie Schriftartname und -größe sowie Vordergrund- und Hintergrundfarbe für den Textinhalt des Wasserzeichentexts an. Geben Sie die Vordergrund- und die Hintergrundfarbe als Hexadezimalwertwerte an.

      ***Hinweis **: Wenn Sie die Skalierungsoption als „An Seite anpassen“ wählen, steht die Eigenschaft der Schriftgröße nicht zur Bearbeitung zur Verfügung.*

1. Wenn Sie „PDF“ für komplexe Wasserzeichen ausgewählt haben, klicken Sie neben der Option „Wasserzeichen-PDF auswählen“ auf **Durchsuchen**, um das PDF -Dokument auszuwählen, das als Wasserzeichen verwendet werden soll.

   ***Hinweis **: Verwenden Sie kein kennwortgeschütztes PDF-Dokument. Wenn Sie ein kennwortgeschütztes PDF als Wasserzeichenelement angeben, wird das Wasserzeichen nicht angewendet.*

1. Wählen Sie für „Als Hintergrund verwenden“ entweder „Ja“ oder „Nein“ aus.

   **Hinweis**: Derzeit wird das Wasserzeichen unabhängig von dieser Einstellung im Vordergrund angezeigt.

1. Um zu bestimmen, wo das Wasserzeichen im Dokument angezeigt werden soll, legen Sie „Vertikale Ausrichtung“ und „Horizontale Ausrichtung“ fest.
1. Wählen Sie entweder „An Seite anpassen“ oder „%“ aus, und geben Sie einen Prozentsatz in das Feld ein. Der Wert muss eine ganze Zahl und darf keine Bruchzahl sein. Um die Wasserzeichengröße zu bestimmen, können Sie einen Wert auswählen, welcher einem Prozentsatz der Seitegröße entspricht, oder das Wasserzeichen so festlegen, dass es sich an die Seitengröße anpasst.
1. Geben Sie im Feld „Drehung“ die Gradzahl an, um die das Wasserzeichen gedreht werden soll. Der Bereich reicht von -180 bis +180. Um das Wasserzeichen gegen den Uhrzeigersinn zu drehen, geben Sie einen negativen Wert ein. Der Wert muss eine ganze Zahl und darf keine Bruchzahl sein.
1. Geben Sie in das Feld „Deckkraft“ einen Prozentwert ein. Der Wert muss eine ganze Zahl und darf keine Bruchzahl sein.
1. Unter „Erweiterte Optionen“ stellen Sie folgende Optionen ein:

   **Seitenbereich-Optionen**

   Legen Sie den Seitenbereich fest, in dem das Wasserzeichen angezeigt werden soll. Geben Sie die Startseite als 1 und die Endseite als -1 ein, damit alle Seiten mit dem Wasserzeichen versehen werden.

   **Anzeigeoptionen**

   Wählen Sie die Stelle, an der das Wasserzeichen angezeigt werden soll. Standardmäßig wird das Wasserzeichen sowohl in der Bildschirmausgabe (Online) als auch in der Ausgabe (Druck) angezeigt.

1. Klicken Sie unter „Wasserzeichenelemente“ auf **Neu**, um weitere Wasserzeichenelemente hinzuzufügen (falls erforderlich).
1. Klicken Sie auf OK.

### Eine Vorlage für dynamische Wasserzeichen bearbeiten  {#edit-a-dynamic-watermark-template}

1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Wasserzeichen“.
1. Wählen Sie das gewünschte Wasserzeichen in der Liste aus.
1. Auf der Seite „Wasserzeichen bearbeiten“ können Sie die Einstellungen ändern.
1. Klicken Sie auf OK.

### Eine Vorlage für dynamische Wasserzeichen löschen  {#delete-a-dynamic-watermark-template}

Wenn Sie ein dynamisches Wasserzeichen löschen, kann es einer neuen Richtlinie nicht mehr hinzugefügt werden. Das Wasserzeichen bleibt jedoch für vorhandene Richtlinien erhalten, die es gegenwärtig verwenden. Auf Dokumenten, die gegenwärtig von der Richtlinie geschützt sind, wird das dynamische Wasserzeichen weiter angezeigt, bis die Richtlinie, die das gelöschte Wasserzeichen enthält, von Ihnen oder einem anderen Benutzer bearbeitet wird. Nach Bearbeitung der Richtlinie wird das Wasserzeichen nicht mehr angewendet. Es wird die Meldung angezeigt, dass das vorhandene Wasserzeichen aus der Richtlinie gelöscht wurde und ein anderes ausgewählt werden kann, um es zu ersetzen.

1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Wasserzeichen“.
1. Aktivieren Sie das Kontrollkästchen neben dem gewünschten Wasserzeichen und klicken Sie auf „Löschen“.
1. Klicken Sie auf OK.

## Registrierung für eingeladene Benutzer konfigurieren  {#configuring-invited-user-registration}

Firmenexterne Benutzer können sich bei Document Security registrieren. Eingeladene Benutzer, die sich registrieren und ihre Konten aktivieren, können sich bei Document Security mit den Anmeldeinformationen (E-Mail-Adresse und Kennwort) anmelden, die sie bei der Registrierung angegeben haben. Registrierte eingeladene Benutzer können richtliniengeschützte Dokumente nutzen, für die sie Berechtigungen haben.

Nach ihrer Aktivierung werden eingeladene Benutzer zu lokalen Benutzern. Lokale Benutzer können im Bereich „Eingeladene und lokale Benutzer“ konfiguriert und verwaltet werden. (Siehe [Konten eingeladener und lokaler Benutzer verwalten](/help/forms/using/admin-help/invited-local-user-accounts.md#managing-invited-and-local-user-accounts).)

Je nachdem, welche Funktionen Sie für eingeladene Benutzer aktiviert haben, können diese die folgenden Document Security-Funktionen verwenden:

* Richtlinien auf Dokumente anwenden
* Erstellen von Richtlinien
* Eingeladene Benutzer zu Richtlinien hinzufügen

Document Security generiert automatisch eine Einladungs-E-Mail zur Registrierung, wenn die folgenden Ereignisse eintreten, sofern der Benutzer nicht bereits im LDAP-Quellordner enthalten ist und noch nicht zur Registrierung eingeladen wurde:

* Ein vorhandener Benutzer fügt einer Richtlinie einen eingeladen Benutzer hinzu.
* Ein Administrator fügt auf der Seite „Registrierung für eingeladene Benutzer“ das Konto eines eingeladenen Benutzers hinzu.

Die Registrierungs-E-Mail enthält einen Hyperlink zu einer Registrierungsseite sowie Informationen zur Registrierung. Nachdem sich der eingeladene Benutzer registriert hat, sendet Document Security eine Aktivierungs-E-Mail mit einem Link zu einer Aktivierungsseite. Nach der Aktivierung bleibt das Konto gültig, bis es deaktiviert oder gelöscht wird.

Durch Aktivieren von „Integrierte Registrierung“ geben Sie den SMTP-Server, die Details der Registrierungs-E-Mail, die Zugriffsmöglichkeiten und den Text der E-Mail-Nachricht zum Zurücksetzen des Kennworts nur einmal an. Stellen Sie vor der Aktivierung der Option „Integrierte Registrierung“ sicher, dass Sie in User Management eine lokale Domäne erstellt und den entsprechenden Benutzern und Gruppen im Unternehmen die Rolle „Document Security – Benutzer einladen“ zugewiesen haben. (Siehe [Lokale Domäne hinzufügen](/help/forms/using/admin-help/adding-domains.md#add-a-local-domain) und [Rollen erstellen und konfigurieren](/help/forms/using/admin-help/creating-configuring-roles.md#creating-and-configuring-roles).) Wenn Sie „Integrierte Registrierung“ nicht verwenden, müssen Sie über ein eigenes mit dem AEM Forms-SDK erstelltes Benutzerregistrierungssystem verfügen. Weitere Informationen finden Sie in der LiveCycle-SDK-Hilfe unter „Entwickeln von SPIs für AEM Forms“ in [ deProgrammieren mit AEM Forms. ](https://www.adobe.com/go/learn-aemforms-programming-63) Wenn Sie die Option „Integrierte Registrierung“ nicht verwenden, ist es ratsam, eine Meldung in der Aktivierungs-E-Mail sowie auf dem Clientanmeldebildschirm zu konfigurieren, um die Benutzer zu informieren, wie sie den Administrator für ein neues Kennwort oder andere Informationen kontaktieren können.

**Registrierung für eingeladene Benutzer aktivieren und deaktivieren**

Standardmäßig ist der Registrierungsprozess für eingeladene Benutzer deaktiviert. Sie können die Registrierung für eingeladene Benutzer für Document Security den Anforderungen entsprechend aktivieren oder deaktivieren.

1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Registrierung für eingeladene Benutzer.
1. Aktivieren Sie „Registrierung für eingeladene Benutzer aktivieren“.
1. (Optional) Aktualisieren Sie die Einstellungen für die Registrierung eingeladener Benutzer den Anforderungen entsprechend:

   * [Externe Benutzer oder Benutzergruppen ein- oder ausschließen](configuring-client-server-options.md#exclude-or-include-an-external-user-or-group)
   * [Server- und Registrierungskontoparameter](configuring-client-server-options.md#server-and-registration-account-parameters)
   * [Einstellungen für die Einladungs-E-Mail zur Registrierung](configuring-client-server-options.md#registration-invitation-email-settings)
   * [Einstellungen für Aktivierungs-E-Mail](configuring-client-server-options.md#activation-email-settings)
   * [Eine E-Mail zum Zurücksetzen des Kennworts konfigurieren](configuring-client-server-options.md#configure-a-password-reset-email)

1. (Optional) Um „Integrierte Registrierung“ zu verwenden, wählen Sie „Ja“ aus. Wenn Sie „Integrierte Registrierung“ nicht aktivieren, müssen Sie ein eigenes Benutzerregistrierungssystem einrichten.
1. Klicken Sie auf OK.

### Externe Benutzer oder Benutzergruppen ein- oder ausschließen  {#exclude-or-include-an-external-user-or-group}

Sie können die Registrierung bei Document Security auf bestimmte Benutzer oder Benutzergruppen beschränken. Diese Option ist hilfreich, wenn Sie beispielsweise einer bestimmten Benutzergruppe den Zugriff erlauben, jedoch bestimmte Gruppenmitglieder ausschließen möchten.

Die folgenden Einstellungen befinden sich im Bereich „Filter für E-Mail-Adressen“ auf der Seite „Registrierung für eingeladene Benutzer“.

**Ausschluss:** Geben Sie die E-Mail-Adresse eines Benutzers oder einer Gruppe ein, die ausgeschlossen werden soll. Um mehrere Benutzer oder Gruppen auszuschließen, geben Sie jede E-Mail-Adresse in eine neue Zeile ein. Um alle Benutzer, die zu einer bestimmten Domäne gehören, auszuschließen, geben Sie einen Platzhalter und den Domänennamen ein. Um beispielsweise alle Benutzer in der Domäne &quot;example.com&quot;auszuschließen, geben Sie &amp;ast;.example.com ein.

**Aufnahme:** Geben Sie die E-Mail-Adresse eines Benutzers oder einer Gruppe ein, die einbezogen werden soll. Um mehrere Benutzer oder Gruppen einzubeziehen, geben Sie jede E-Mail-Adresse in eine neue Zeile ein. Um alle Benutzer, die zu einer bestimmten Domäne gehören, einzubeziehen, geben Sie einen Platzhalter und den Domänennamen ein. Um beispielsweise alle Benutzer in der Domäne &quot;example.com&quot;einzubeziehen, geben Sie &amp;ast;.example.com ein.

### Server- und Registrierungskontoparameter {#server-and-registration-account-parameters}

Die folgenden Einstellungen befinden sich im Bereich „Allgemeine Einstellungen“ auf der Seite „Registrierung für eingeladene Benutzer“.

**SMTP-Host:** Der Hostname des SMTP-Servers. Der SMTP-Server verwaltet die ausgehenden E-Mail-Nachrichten für die Registrierung und Aktivierung eingeladener Benutzer.

Falls für den SMTP-Host erforderlich, füllen Sie die Felder „Kontoname für den SMTP-Server“ und „Kennwort des Kontos für den SMTP-Server“ aus, um eine Verbindung mit dem SMTP-Server herzustellen. Bei einige Unternehmen ist dies nicht erforderlich. Befragen Sie den Systemadministrator, falls Sie Informationen benötigen.

**Name der Socket-Klasse des SMTP-Servers:Name der** Socket-Klasse für den SMTP-Server. Zum Beispiel javax.net.ssl.SSLSocketFactory.

**E-Mail-Inhaltstyp:** Akzeptierter MIME-Typ wie text/plain oder text/html.

**E-Mail-Kodierung:** Kodierformat für das Senden von E-Mail-Nachrichten. Sie können jede beliebige Kodierung angeben, z. B. UTF-8 für Unicode oder ISO-8859-1 für Latein. Die Standardeinstellung ist UTF-8.

**E-Mail-Adresse umleiten:** Wenn Sie für diese Einstellung eine E-Mail-Adresse angeben, wird jede neue Einladung an die angegebene Adresse gesendet. Diese Einstellung kann für Testzwecke sinnvoll sein.

**Lokale Domänen verwenden:** Wählen Sie die gewünschte Domäne aus. Stellen Sie bei einer Neuinstallation sicher, dass Sie die Domäne in User Management erstellt haben. Bei einem Update kann eine externe Benutzerdomäne, die während des Updates erstellt wurde, verwendet werden.

**SSL für SMTP-Server verwenden:** Wählen Sie diese Option, um SSL für den SMTP-Server zu aktivieren.

**Link zum Anmelden auf der Registrierungsseite anzeigen:** Zeigt einen Link zum Anmelden auf der Registrierungsseite an, der für eingeladene Benutzer angezeigt wird.

**Aktivieren von Transport Layer Security (TLS) für den SMTP-Server**

1. Öffnen Sie Administration Console.

   Der Standardspeicherort der Administrationskonsole ist `https://<server>:<port>/adminui`.

1. Wechseln Sie zu „Startseite“ > „Dienste“ > „Document Security “ > „Konfiguration“ > „Registrierung für eingeladene Benutzer“.
1. Geben Sie für „Registrierung für eingeladene Benutzer“ alle Konfigurationseinstellungen an und klicken Sie auf „OK“.

   >[!NOTE]
   >
   >Wenn Sie Microsoft Office 365 als SMTP-Server zum Senden der Einladungen für eine Benutzerregistrierung verwenden, verwenden Sie die folgenden Einstellungen:
   >
   >**SMTP-Host:** smtp.office365.com
   >**Port:** 587

1. Als Nächstes müssen Sie „config.xml“ aktualisieren. Weitere Informationen finden Sie unter [Konfiguration für die Aktivierung von SMTP für Transport Layer Security (TLS)](configuring-client-server-options.md#configuration-to-enable-smtp-for-transport-layer-security-tls).

>[!NOTE]
>
>Wenn Sie Änderungen an den Optionen für die Registrierung eingeladener Benutzer vornehmen, wird die Datei „config.xml“ überschrieben und TLS wird deaktiviert. Wenn Sie die Änderungen überschreiben, müssen Sie mithilfe des oben beschriebenen Schritts die TLS-Unterstützung für die Registrierung eingeladener Benutzer reaktivieren.

### Einstellungen für die Einladungs-E-Mail zur Registrierung  {#registration-invitation-email-settings}

Document Security sendet automatisch eine Einladungs-E-Mail zur Registrierung, wenn Sie ein Konto für einen eingeladenen Benutzers erstellen oder ein bestehender Benutzer einer Richtlinie einen externen Empfänger hinzufügt, der bislang weder registriert noch eingeladen wurde. Die E-Mail enthält einen Hyperlink, über den der Empfänger auf die Registrierungsseite zugreifen kann, um persönliche Kontoinformationen einschließlich Benutzername und Kennwort einzugeben. Das Kennwort kann eine beliebige Kombination von acht Zeichen sein.

Wenn der Empfänger sein Konto aktiviert hat, wird er ein lokaler Benutzer.

Die folgenden Einstellungen befinden sich im Bereich „E-Mail-Konfiguration“ auf der Seite „Registrierung für eingeladene Benutzer“.

**Von:** Die E-Mail-Adresse, von der die Einladungs-E-Mail gesendet wird. Das Standardformat der E-Mail-Adresse &quot;Von&quot;ist &quot;postmaster@[your_installation_domain].com&quot;.

**Betreff:** Standardbetreff für die Einladungs-E-Mail-Nachricht.

**Timeout:** Die Anzahl der Tage, nach denen die Registrierungseinladung abläuft, wenn sich der externe Benutzer nicht registriert. Der Standardwert ist 30 Tage .

**Nachricht:** Der Text, der im Nachrichtentext angezeigt wird und den Benutzer zur Registrierung einlädt.

### Einstellungen für Aktivierungs-E-Mail {#activation-email-settings}

Nach der Registrierung erhalten eingeladene Benutzer eine Aktivierungs-E-Mail von Document Security. Die Aktivierungs-E-Mail enthält einen Link zur Kontoaktivierungsseite, auf welcher der Benutzer sein Konto aktivieren kann. Nach der Aktivierung des Kontos können sich die Benutzer bei Document Security mit den Anmeldeinformationen (E-Mail-Adresse und Kennwort) anmelden, die sie bei der Registrierung angegeben haben.

Wenn der Empfänger das Benutzerkonto aktiviert hat, wird er ein lokaler Benutzer.

Die folgenden Einstellungen befinden sich im Bereich „Konfiguration der Aktivierungs-E-Mail“ auf der Seite „Registrierung für eingeladene Benutzer“.

>[!NOTE]
>
>Es empfiehlt sich auch, eine Meldung auf dem Anmeldebildschirm zu konfigurieren, die externe Benutzer informiert, wie der Administrator für ein neues Kennwort oder andere Informationen kontaktiert werden kann.

**Von:** Die E-Mail-Adresse, von der die Aktivierung-E-Mail gesendet wird. Diese E-Mail-Adresse empfängt Benachrichtigungen zu fehlgeschlagenen Übermittlungen vom E-Mail-Host des Registrierenden sowie Nachrichten, die der Empfänger als Antwort auf die Registrierungs-E-Mail sendet. Das Standardformat der E-Mail-Adresse &quot;Von&quot;ist &quot;postmaster@[your_installation_domain].com&quot;.

**Betreff:** Standardbetreff für die Aktivierung-E-Mail-Nachricht.

**Timeout:** Die Anzahl der Tage, nach denen die Einladung zur Aktivierung abläuft, wenn der Benutzer das Konto nicht aktiviert. Der Standardwert ist 30 Tage .

**Nachricht:** Der Text, der im Textkörper der Nachricht angezeigt wird und der angibt, dass das Benutzerkonto des Empfängers aktiviert werden muss. Sie können nach Wunsch weitere Informationen hinzufügen, z. B. wie der Administrator kontaktiert und ein neues Kennwort bezogen werden kann.

### Eine E-Mail zum Zurücksetzen des Kennworts konfigurieren  {#configure-a-password-reset-email}

Wenn Sie das Kennwort eines eingeladenen Benutzers zurücksetzen müssen, wird eine Bestätigungs-E-Mail generiert, die den Benutzer einlädt, ein neues Kennwort auszuwählen. Es gibt keine Möglichkeit, das Kennwort eines Benutzers zu ermitteln. Hat es der Benutzer vergessen, müssen Sie es zurücksetzen.

Die folgenden Einstellungen befinden sich im Bereich „Konfiguration der E-Mail zum Zurücksetzen des Kennworts“ auf der Seite „Registrierung für eingeladene Benutzer“.

**Von:** Die E-Mail-Adresse, von der die E-Mail zum Zurücksetzen des Kennworts gesendet wird. Das Standardformat der E-Mail-Adresse &quot;Von&quot;ist &quot;postmaster@[your_installation_domain].com&quot;.

**Betreff:** Standardbetreff für die E-Mail-Nachricht zum Zurücksetzen.

**Nachricht:** Der Text, der im Textkörper der Nachricht angezeigt wird und die Meldung enthält, dass das Kennwort des externen Empfängers zurückgesetzt wurde.

## Benutzer und Gruppen zum Erstellen von Richtlinien aktivieren {#enable-users-and-groups-to-create-policies}

Die Seite „Konfiguration“ enthält einen Hyperlink zur Seite „Meine Richtlinien“, auf der Sie angeben können, welche Endbenutzer eigene Richtlinien erstellen dürfen und welche Benutzer und Gruppen in Suchergebnissen angezeigt werden. Die Seite „Meine Richtlinien“ hat zwei Registerkarten:

**Richtlinien erstellen, Registerkarte:** Zum Konfigurieren von Benutzerberechtigungen zum Erstellen benutzerdefinierter Richtlinien.

**Sichtbare Benutzer und Gruppen, Registerkarte:** Mit dieser Option können Sie steuern, welche Benutzer und Gruppen in den Suchergebnissen der Benutzer sichtbar sind. Der Hauptbenutzer oder Richtliniensatzadministrator muss für jeden Richtliniensatz in User Management erstellte Domänen auswählen und zum sichtbaren Benutzer bzw. zur sichtbaren Gruppe hinzufügen. Diese Liste wird dem Richtliniensatzkoordinator angezeigt und dient zum Eingrenzen der Domänen, die der Richtliniensatzkoordinator beim Auswählen von Benutzern durchsuchen kann, die Richtlinien hinzugefügt werden sollen.

Bevor Sie Benutzern die Berechtigung zum Erstellen benutzerdefinierter Richtlinien erteilen, sollten Sie prüfen, welchen Zugriffs- oder Steuerungsgrad die einzelnen Benutzer haben sollen. Prüfen Sie auch, welche Informationen zu Gruppen und Benutzern angezeigt werden sollen, wenn sie in Suchergebnissen angezeigt werden.

### Benutzer und Gruppen mit Berechtigung zum Erstellen von Richtlinien angeben  {#specify-users-and-groups-who-can-create-policies}

Als Administrator können Sie angeben, welche Benutzer und Gruppen benutzerdefinierte Richtlinien erstellen dürfen. Diese Berechtigung kann auf Benutzer- und Gruppenebene erteilt werden. Die Suchfunktion durchsucht die User Management-Datenbank nach Benutzern und Gruppen.

1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Meine Richtlinien“.
1. Klicken Sie auf der Seite „Meine Richtlinien“ auf die Registerkarte „Richtlinien erstellen“ und dann auf „Benutzer und Gruppen hinzufügen“.
1. Geben Sie in das Feld „Suchen“ den Namen des Benutzers oder die E-Mail-Adresse des Benutzers bzw. der Gruppe ein, den/die Sie suchen. Wenn Sie diese Angaben nicht kennen, lassen Sie das Feld leer. Sie können einen Namen oder eine E-Mail-Adresse auch teilweise eingeben, wenn Ihnen beispielsweise nur die ersten beiden Buchstaben eines Benutzernamens bekannt sind.
1. Wählen Sie in der Liste „Verwendet“ die Suchparameter „Name“ oder „E-Mail“ aus.
1. Wählen Sie in der Liste „Typ“ den Eintrag „Gruppe“ oder „Benutzer“ aus, um die Suche einzugrenzen.
1. Wählen Sie in der Liste „In“ die zu durchsuchende Domäne aus. Wenn Sie die Domäne des Benutzers oder der Gruppe nicht kennen, wählen Sie „Alle Domänen“ aus.
1. Geben Sie in der Liste „Anzeigen“ die Anzahl der pro Seite anzuzeigenden Suchergebnisse ein und klicken Sie auf „Suchen“.
1. Um Benutzer und Gruppen zu „Meine Richtlinien“ hinzuzufügen, aktivieren Sie die Kontrollkästchen der hinzuzufügenden Benutzer und Gruppen.
1. Klicken Sie auf „Hinzufügen“ und dann auf „OK“.

Die ausgewählten Benutzer und Gruppen dürfen nun benutzerdefinierte Richtlinien erstellen.

### Die Berechtigung zum Erstellen benutzerdefinierter Richtlinien für Benutzer oder Gruppen entfernen  {#remove-the-create-custom-policies-permission-from-a-user-or-group}

1. Klicken Sie auf der Document Security-Seite auf „Konfiguration“ > „Meine Richtlinien“.
1. Klicken Sie auf der Seite „Meine Richtlinien“ auf die Registerkarte „Richtlinien erstellen“. Benutzer und Gruppen mit der Berechtigung zum Erstellen benutzerdefinierter Richtlinien werden angezeigt.
1. Aktivieren Sie die Kontrollkästchen neben den Benutzern und Gruppen, die Sie aus dieser Berechtigung entfernen möchten.
1. Klicken Sie auf „Löschen“ und dann auf „OK“.

### Benutzer und Gruppen, die in Suchergebnissen sichtbar sind, angeben  {#specify-users-and-groups-that-are-visible-in-searches}

Wenn Benutzer ihre benutzerdefinierten Richtlinien verwalten, können sie Benutzer und Gruppen suchen, die sie ihren Richtlinien hinzufügen möchten. Sie müssen die Domänen angeben, aus denen Benutzer und Gruppen in diesen Suchergebnissen angezeigt werden sollen.

1. Klicken Sie auf der Document Security-Seite auf „Konfiguration“ > „Meine Richtlinien“.
1. Klicken Sie auf der Seite „Meine Richtlinien“ auf die Registerkarte „Sichtbare Benutzer und Gruppen“.
1. Um die Benutzer und Gruppen in einer Domäne sichtbar zu machen, klicken Sie auf „Domänen hinzufügen“, wählen Sie die Domänen aus und klicken Sie auf „Hinzufügen“. Aktivieren Sie zum Entfernen einer Domäne das Kontrollkästchen neben dem Domänennamen und klicken Sie auf „Löschen“.

## Manuelles Bearbeiten der Document Security-Konfigurationsdatei  {#manually-editing-the-document-security-configuration-file}

Sie können die Konfigurationsinformationen im- und exportieren, die in der Document Security-Datenbank gespeichert sind. Sie sollten beispielsweise eine Sicherungskopie der Konfigurationsinformationen erstellen, wenn Sie von einer Test- und zu einer Produktionsumgebung wechseln. Sie können auch erweiterte Optionen bearbeiten, die nur durch Bearbeiten dieser Datei konfiguriert werden können.

Mithilfe der Konfigurationsdatei können Sie folgende Änderungen vornehmen:

[CATIA-Berechtigungen beim Erstellen und Bearbeiten von Richtlinien anzeigen](configuring-client-server-options.md#display-catia-permissions-when-creating-and-editing-policies)

[Ein Zeitlimit für die Offline-Synchronisation angeben](configuring-client-server-options.md#specify-a-timeout-period-for-offline-synchronization)

[Ablehnen von Document Security-Diensten für bestimmte Anwendungen](configuring-client-server-options.md#denying-document-security-services-for-specific-applications)

[Parameter der Wasserzeichenkonfiguration ändern](configuring-client-server-options.md#change-the-watermark-configuration-parameters)

[Externe Verknüpfungen deaktivieren](configuring-client-server-options.md#disabling-external-links)

>[!NOTE]
>
>Beim Importieren der Konfigurationsdatei wird Ihr System basierend auf den Informationen in der Datei neu konfiguriert. Eine Ausnahme bilden die Konfigurationsinformationen dynamischer Wasserzeichen sowie Informationen über benutzerdefinierte Ereignisse, die nicht in der exportierten Konfigurationsdatei gespeichert werden. Sie müssen diese Informationen im neuen System manuell konfigurieren. Nur ein Systemadministrator oder versierter IT-Berater, der mit Document Security und XML vertraut ist, sollte den Inhalt einer Konfigurationsdatei ändern (um beispielsweise eine fehlerhafte Einstellung neu zu konfigurieren oder Parameter für ein bestimmtes Unternehmensbereitstellungsszenario zu optimieren).

**Eine Konfigurationsdatei exportieren**

1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security 11“ > „Konfiguration“ > „Manuelle Konfiguration“.
1. Klicken Sie auf „Exportieren“ und speichern Sie die Konfiguration an einem anderen Speicherort. Der Standarddateiname lautet „config.xml“.
1. Klicken Sie auf OK.
1. Bevor Sie Änderungen an der Konfigurationsdatei vornehmen, erstellen Sie eine Sicherungskopie für den Fall, dass Sie den Ausgangszustand wiederherstellen müssen.

**Eine Konfigurationsdatei importieren**

1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security 11“ > „Konfiguration“ > „Manuelle Konfiguration“.
1. Klicken Sie auf Durchsuchen, um zur Konfigurationsdatei zu wechseln, und klicken Sie dann auf Importieren. Sie können den Pfad nicht direkt in das Feld „Dateiname“ eingeben.
1. Klicken Sie auf OK.

### Ein Zeitlimit für die Offline-Synchronisation angeben  {#specify-a-timeout-period-for-offline-synchronization}

Document Security ermöglicht Benutzern das Öffnen und Verwenden geschützter Dokumente, wenn sie über keine Verbindung zum Document Security-Server verfügen. Die Clientanwendung des Benutzers muss regelmäßig mit dem Server synchronisiert werden, damit die Dokumente für die Offline-Nutzung gültig bleiben. Wenn der Benutzer zum ersten Mal ein geschütztes Dokument öffnen möchte, wird er gefragt, ob der Computer zum Ausführen periodischer Clientsynchronisation autorisiert werden soll.

Standardmäßig wird die Synchronisation automatisch alle vier Stunden und nach Bedarf ausgeführt, wenn der Benutzer eine Verbindung mit dem Document Security-Server hergestellt hat. Wenn der Offline-Zeitraum für ein Dokument abläuft, während der Benutzer offline ist, muss der Benutzer erneut eine Verbindung zum Server herstellen, damit die Clientanwendung mit dem Server synchronisiert werden kann.

In der Document Security-Konfigurationsdatei können Sie das Standardzeitintervall der automatischen Hintergrundsynchronisation angeben. Diese Einstellung fungiert als Standardzeitlimit für die Clientanwendungen, es sei denn, der Client legt ausdrücklich seinen eigenen Zeitlimitwert fest.

1. Exportieren Sie die Document Security-Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)
1. Öffnen Sie die Konfigurationsdatei in einem Editor und suchen Sie den Knoten `PolicyServer`. Suchen Sie unter diesem Knoten den Knoten `ServerSettings`.
1. Fügen Sie im Knoten `ServerSettings` den folgenden Eintrag hinzu und speichern Sie anschließend die Datei:

   `<entry key="BackgroundSyncFrequency" value="`*Uhrzeit* `"/>`

   dabei ist *time* die Anzahl der Sekunden zwischen den automatischen Hintergrundsynchronisationen. Wenn Sie diesen Wert auf `0` festgelegt haben, wird immer eine Synchronisation ausgeführt. Der Standardwert ist `14400` Sekunden (alle vier Stunden).

1. Importieren Sie eine Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)

### Ablehnen von Document Security-Diensten für bestimmte Anwendungen  {#denying-document-security-services-for-specific-applications}

Sie können Document Security so konfigurieren, dass Dienste für Anwendungen, die bestimmte Kriterien erfüllen, abgelehnt werden. Die Kriterien können ein einzelnes Attribut, z. B. einen Plattformnamen, oder mehrere Attributsätze angeben. Mithilfe dieser Funktion können Sie die Anforderungen steuern, die Document Security verarbeiten muss. Im Folgenden finden Sie einige Anwendungen dieser Funktion:

* **Einkommensschutz:** Sie können den Zugriff auf Clientanwendungen, die Ihre Einkommenskonventionen nicht unterstützen, verweigern.
* **Anwendungskompatibilität:** Einige Anwendungen sind möglicherweise nicht mit den Richtlinien oder dem Verhalten Ihres Document Security-Servers kompatibel.

Wenn Clientanwendungen versuchen, eine Verknüpfung mit Document Security herzustellen, stellen sie Anwendungs-, Versions- und Plattforminformationen bereit. Document Security vergleicht diese Informationen mit den Verweigerungs-Einstellungen, die aus der Document Security-Konfigurationsdatei abruft.

Die Verweigerungs-Einstellungen können mehrere Verweigerungsbedingungen enthalten. Wenn alle Attribute eines Satzes übereinstimmen, wird der anfordernden Anwendung der Zugriff auf die Document Security-Dienste verweigert.

Die Dienstblockaden-Funktion erfordert, dass Clientanwendungen die Document Security C++ Client SDK ab Version 8.2 verwenden. Die folgenden Adobe-Produkte stellen beim Anfordern von Document Security-Diensten Produktinformationen bereit:

* Adobe Acrobat 9.0 Professional/Acrobat 9.0 Standard und höher
* Adobe Reader 9.0 und höher
* Acrobat Reader DC Extensions für Microsoft Office ab Version 8.2

Clientanwendungen verwenden die Client-API des Document Security C++ Client SDK, um Dienste von Document Security anzufordern. Die Client-API-Anforderungen enthalten Informationen über die Plattform und SDK-Version (vorkompiliert in die Client-API) sowie Produktinformationen, die aus der Clientanwendung abgerufen wurden.

Clientanwendungen oder Plug-Ins unterstützen Produktinformationen bei ihrer Implementierung einer Rückruffunktion. Die Anwendung stellt die folgenden Informationen bereit:

* Integrator-Name
* Integrator-Version
* Anwendungsfamilie
* Anwendungsname
* Anwendungsversion

Wenn Informationen nicht verfügbar sind, bleibt das entsprechende Feld in der Clientanwendung leer.

Einige Adobe-Anwendungen, darunter Acrobat, Adobe Reader und Acrobat Reader DC Extensions für Microsoft Office, enthalten Produktinformationen ein, die bereitgestellt werden, wenn Document Security-Dienste angefordert werden.

**Acrobat und Adobe Reader**

Wenn Acrobat oder Adobe Reader einen Dienst von Document Security anfordert, werden die folgenden Produktinformationen bereitgestellt:

* **Integrator:** Adobe Systems, Inc.
* **Integrator-Version:** 1.0
* **Anwendungsfamilie:** Acrobat
* **Anwendungsname:** Acrobat
* **Anwendungsversion:** 9.0.0

**Acrobat Reader DC Extensions für Microsoft Office**

Acrobat Reader DC Extensions für Microsoft Office ist ein Plug-In, das mit den Microsoft Office-Produkten Microsoft Word, Microsoft Excel und Microsoft PowerPoint verwendet wird. Wenn es einen Dienst anfordert, stellt es die folgenden Informationen bereit:

* **Integrator:** Adobe Systems Incorporated
* **Integrator-Version:** 8.2
* **Anwendungsfamilie:** Acrobat Reader DC Extensions für Microsoft Office
* **Anwendungsname:** Microsoft Word, Microsoft Excel oder Microsoft PowerPoint
* **Anwendungsversion:** 2003 oder 2007

**Document Security zum Ablehnen von Diensten für bestimmte Anwendungen konfigurieren**

1. Exportieren Sie die Document Security-Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)
1. Öffnen Sie die Konfigurationsdatei in einem Editor und suchen Sie den Knoten `PolicyServer`. Fügen Sie einen `ClientVersionRules`-Knoten als unmittelbar untergeordneten Knoten des `PolicyServer`-Knotens hinzu, wenn noch kein solcher Knoten vorhanden ist.

   ```xml
    <node name="ClientVersionRules">
        <map>
            <entry key="infoURL" value="URL"/>
        </map>
        <node name="Denials">
            <map/>
            <node name="MyEntryName">
                <map>
                    <entry key="SDKPlatforms" value="platforms"/>
                    <entry key="SDKVersions" value="versions"/>
                    <entry key="AppFamilies" value="families"/>
                    <entry key="AppNames" value="names"/>
                    <entry key="AppVersions" value="versions"/>
                    <entry key="Integrators" value="integrators"/>
                    <entry key="IntegratorVersions" value="versions"/>
                </map>
            </node>
            <node name="MyOtherEntryName"
                <map>
                    [...]
                </map>
            </node>
            [...]
        </node>
    </node>
   ```

   hierbei gilt:

   `SDKPlatforms` gibt die Plattform an, die als Host für die Clientanwendung dient.  Mögliche Werte sind:

   * Microsoft Windows
   * Apple OS X
   * Sun Solaris
   * HP-UX

   `SDKVersions` gibt die Version der Document Security C++ Client-API an, die von der Clientanwendung verwendet wird. Beispiel: `"8.2"`.

   `APPFamilies` ist durch die Client-API definiert.

   `AppName` gibt den Namen der Clientanwendung an.  Kommas werden als Trennzeichen für den Namen verwendet. Um ein Komma in einen Namen einzufügen, ersetzen Sie es durch ein Backslash (\)-Zeichen. Zum Beispiel *Adobe Systems\, Inc.*

   `AppVersions` gibt die Version der Clientanwendung an.

   `Integrators` gibt den Namen des Unternehmens oder der Gruppe, die das Plug-In oder die integrierte Anwendung entwickelt hat, an.

   `IntegratorVersions` ist die Version des Plug-Ins oder der integrierten Anwendung.

1. Fügen Sie für jeden weiteren Satz von Verweigerungsdaten ein weiteres *MyEntryName*-Element hinzu.
1. Speichern Sie die Konfigurationsdatei.
1. Importieren Sie eine Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)

**Beispiele**

In diesem Beispiel wird allen Windows Clients der Zugriff verweigert.

```xml
 <node name="ClientVersionRules">
     <map>
         <entry key="infoURL" value="https://www.dont.use/windows.html"/>
     </map>
     <node name="Denials">
         <map/>
         <node name="Entry_1">
             <map>
                 <entry key="SDKPlatforms" value="Microsoft Windows"/>
             </map>
         </node>
     </node>
 </node>
```

In diesem Beispiel wird „Meine Anwendung Version 3.0“ und „Meine andere Anwendung Version 2.0“ der Zugriff verweigert. Dieselbe URL für die Verweigerungsinformationen wird unabhängig vom Grund für die Verweigerung verwendet.

```xml
 <node name="ClientVersionRules">
     <map>
         <entry key="infoURL" value=”https://get.a.new/version.html”/>
     </map>
     <node name="Denials">
         <map/>
         <node name="FirstDenialSettings">
             <map>
                 <entry key="AppNames" value="My Application"/>
                 <entry key="AppVersions" value="3.0"/>
             </map>
         </node>
         <node name="SecondDenialSettings">
             <map>
                 <entry key="AppNames" value="My Other Application"/>
                 <entry key="AppVersions" value="2.0"/>
             </map>
         </node>
     </node>
 </node>
```

In diesem Beispiel werden alle Anforderungen von einer Microsoft PowerPoint 2007- oder Microsoft PowerPoint 2010-Installation von Acrobat Reader DC Extensions für Microsoft Office abgelehnt.

```xml
 <node name="ClientVersionRules">
     <map>
         <entry key="infoURL" value=”https://get.a.new/version.html”/>
     </map>
     <node name="Denials">
         <map/>
         <node name="Entry_1">
             <map>
                 <entry key="AppFamilies" value=
     "document security Extension for Microsoft Office"/>
                 <entry key="AppNames" value= "Microsoft PowerPoint"/>
                 <entry key="AppVersions" value="2007,2010"/>
             </map>
         </node>
     </node>
 </node
```

### Parameter der Wasserzeichenkonfiguration ändern  {#change-the-watermark-configuration-parameters}

Standardmäßig können Sie maximal fünf Elemente in einem Wasserzeichen angeben. Die maximale Dateigröße des PDF-Dokuments, das Sie als Wasserzeichen verwenden möchten, ist auf 100 KB beschränkt ist. Sie können diese Parameter in der config.xml-Datei ändern.

***Hinweis **: Sie sollten diese Parameter mit Vorsicht ändern.*

1. Exportieren Sie die Document Security-Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)
1. Öffnen Sie die Konfigurationsdatei in einem Editor und suchen Sie den Knoten `ServerSettings`.
1. Fügen Sie im Knoten `ServerSettings` die folgenden Einträge hinzu und speichern Sie anschließend die Datei: `<entry key="maximumSizeOfWatermarkElement" value="max filesize in KB"/> <entry key="maximumWatermarkElementsPerWatermark" value="max elements"/>`

   Der erste Eintrag *max file size* ist die Maximalgröße der Datei (in KB) für ein Wasserzeichenelement. Der Standardwert ist 100 KB.

   Der zweite Eintrag *max elements* ist die Maximalanzahl von Elementen für ein Wasserzeichen. Der Standardwert ist 5.

   ```xml
   <entry key="maximumSizeOfWatermarkElement" value="max filesize in KB"/>
   <entry key="maximumWatermarkElementsPerWatermark" value="max elements"/>
   ```

1. Importieren Sie eine Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)

### Externe Verknüpfungen deaktivieren  {#disabling-external-links}

Viele Document Security-Benutzer haben keinen Zugriff auf externe Verknüpfungen wie **www.adobe.com**, wenn sie die Rights Management-Benutzeroberflächen verwenden:

* `https://[host]:'port'/adminui`
* `https://[host]:'port'/edc`.

Die folgenden Änderungen an der Datei „config.xml“ deaktivieren alle externen Verknüpfungen in den Rights Management-Benutzeroberflächen.

1. Exportieren Sie die Document Security-Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)
1. Öffnen Sie die Konfigurationsdatei in einem Editor und suchen Sie den Knoten `DisplaySettings`.
1. Um alle externen Verknüpfungen zu deaktivieren, fügen Sie im Knoten `DisplaySettings` den folgenden Eintrag hinzu und speichern Sie anschließend die Datei: `<entry key="ExternalLinksAllowed" value="false"/>`

   ```xml
   <entry key="ExternalLinksAllowed" value="false"/>
   ```

1. Importieren Sie eine Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)

### Konfiguration für die Aktivierung von SMTP für Transport Layer Security (TLS)  {#configuration-to-enable-smtp-for-transport-layer-security-tls}

Die folgenden Änderungen in „config.xml“ ermöglichen die TLS-Unterstützung für die Funktion „Registrierung für eingeladene Benutzer“.

1. Exportieren Sie die Document Security-Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)
1. Öffnen Sie die Konfigurationsdatei in einem Editor und suchen Sie den Knoten `DisplaySettings`.
1. Suchen Sie den folgenden Knoten: `<node name="ExternalUser">`

   ```xml
   <node name="ExternalUser">
   ```

1. Legen Sie für den Schlüssel `SmtpUseTls` unter dem Knoten `ExternalUser` den Wert **true** fest.
1. Legen Sie für den Schlüssel `SmtpUseSsl` unter dem Knoten `ExternalUser` den Wert **false** fest.
1. Speichern Sie `config.xml`.
1. Importieren Sie eine Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)

### SOAP-Endpunkte für Document Security-Dokumente deaktivieren  {#disable-soap-endpoints-for-document-security-documents}

Nehmen Sie die folgenden Änderungen in „config.xml“ vor, um SOAP-Endpunkte für Document Security-Dokumente zu deaktivieren.

1. Exportieren Sie die Document Security-Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)
1. Öffnen Sie die Konfigurationsdatei in einem Editor und suchen Sie den folgenden Knoten:  `<node name="DRM">`

   ```xml
   <node name="DRM">
   ```

1. Suchen Sie im DRM-Knoten den `entry`-Knoten:

   `<entry key="AllowUnencryptedVoucher" value="true"/>`

1. Um SOAP-Endpunkte für Document Security-Dokumente zu deaktivieren, ändern Sie den Wert des Attributs „value“ in **false**.

   ```xml
   <node name="DRM">
       <map>
           <entry key="AllowUnencryptedVoucher" value="false"/>
       </map>
   </node>
   ```

1. Speichern Sie `config.xml`.
1. Importieren Sie eine Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)

### Erhöhen der Skalierbarkeit des Document Security-Servers  {#increasingscalability}

Standardmäßig beim Synchronisieren von Dokumenten für die Offline-Nutzung zusammen mit den Informationen zum aktuellen Dokument, rufen die Dokument-Sicherheits-Clients standardmäßig Richtlinien, Lizenzen, Wasserzeichen und Rücknahme-Updateinformation für alle anderen Dokumente, auf den der Benutzer Zugriff hat, auf. Wenn diese Updates und Informationen nicht mit dem Client synchronisiert werden, öffnet sich ein Dokument, das im Offlinemodus geöffnet ist, noch mit den alten Richtlinien Wasserzeichen und Sperrinformationen.

Sie können die Skalierbarkeit des Document Security-Servers erhöhen, indem Sie die Informationen, die an den Client gesendet werden, einschränken. Die Reduzierung der Datenmenge, die an den Client gesendet werden, führen zu verbesserter Skalierbarkeit, reduzierter Reaktionsfähigkeit und besserer Leistung des Servers. Führen Sie zur Verbesserung der Skalierbarkeit folgende Schritte durch:

1. Exportieren Sie die Document Security-Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)
1. Öffnen Sie die Konfigurationsdatei in einem Editor und suchen Sie den Knoten ServerSettings.
1. Legen Sie im Knoten ServerSettings den Wert der Eigenschaft `DisableGlobalOfflineSynchronizationData`auf `true` fest.

   `<entry key="DisableGlobalOfflineSynchronizationData" value="true"/>`

   Bei dem Wert „true“ sendet der Document Security-Server Informationen nur für das aktuelle Dokument und Informationen für die übrigen Dokumente (die übrigen Dokumente, auf die ein Benutzer Zugriff hat) werden nicht an den Client gesendet.

   >[!NOTE]
   >
   >Standardmäßig wird der Wert des `DisableGlobalOfflineSynchronizationData`- -Schlüssels auf `false` festgelegt.

1. Speichern und schließen Sie die Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](/help/forms/using/admin-help/configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)

