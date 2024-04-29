---
title: Konfigurieren der Client- und Server-Optionen
description: Erfahren Sie, wie Sie die verschiedenen Client- und Server-Optionen konfigurieren können, z. B. Einstellungen zur Server-Konfiguration, Rollen für die Dokumentensicherheit und Ereignisprüfung.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Document Security
exl-id: fe132f13-5f9a-4c86-a385-0a0026c812e2
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '10266'
ht-degree: 100%

---

# Konfigurieren des Dokumentensicherheits-Servers {#configure-the-document-security-server}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Server-Konfiguration“.
1. Konfigurieren Sie die Einstellungen und klicken Sie auf „OK“.

## Einstellungen zur Server-Konfiguration {#server-configuration-settings}

**Basis-URL:** Die Document Security-Basis-URL, die den Servernamen und Port enthält. Durch Anfügen von Informationen an die Basis-URL werden Verbindungs-URLs erstellt. /edc/Main.do wird beispielsweise angefügt, um auf die Webseiten zuzugreifen. Diese URL ermöglicht Benutzern auch, auf Einladungen externer Benutzer zur Registrierung zu antworten.

Wenn Sie IPv6 verwenden, geben Sie die Basis-URL als den Computer-Namen oder den DNS-Namen ein. Wenn Sie eine numerische IP-Adresse verwenden, kann Acrobat richtliniengeschützte Dateien nicht öffnen. Verwenden Sie zudem eine HTTPS-URL (HTTP Secure) für Ihren Server.

>[!NOTE]
>
>Die Basis-URL ist in durch Richtlinien geschützte Dateien eingebettet. Sie wird von Client-Anwendungen verwendet, um sich wieder mit dem Server zu verbinden. Geschützte Dateien enthalten die Basis-URL auch dann weiter, wenn diese später geändert wird. Wenn Sie die Basis-URL ändern, müssen die Konfigurationsinformationen für alle sich mit dem Server verbindenden Clients geändert werden.

**Standardmäßiger Offline-Lease-Zeitraum:** Der standardmäßige Zeitraum, den ein Benutzer ein geschütztes Dokument offline nutzen darf. Diese Einstellung bestimmt den ursprünglichen Wert der Einstellung für die Automatische Offline-Nutzungsdauer, wenn Sie eine Richtlinie erstellen. (Siehe Richtlinien erstellen und bearbeiten.) Nach Ablauf der Nutzungsdauer muss der Empfänger das Dokument erneut synchronisieren, um es weiter verwenden zu können.

Weitere Informationen zur Funktionsweise der Offline-Nutzung und Synchronisation finden Sie unter [Primer zum Konfigurieren der Offline-Nutzung und Synchronisation](https://blogs.adobe.com/security/2009/05/primer_on_configuring_offline.html).

**Standardmäßiger Offline-Synchronisierungs-Zeitraum:** Die maximale Zeit, die ein beliebiges Dokument offline verwendet werden kann, wenn es anfänglich geschützt ist.

**Client-Sitzungs-Timeout:** Der Zeitraum in Minuten, nach dem Document Security die Verbindung trennt, wenn ein über eine Clientanwendung angemeldeter Benutzer Document Security nicht verwendet.

**Anonymen Benutzerzugriff gestatten:** Aktivieren Sie diese Option, um das Erstellen von freigegebenen und persönlichen Richtlinien, die anonymen Benutzern das Öffnen richtliniengeschützter Dokumente erlauben, zuzulassen. (Benutzer ohne Konto können auf das Dokument zugreifen, sich jedoch nicht bei Document Security anmelden oder andere richtliniengeschützte Dokumente nutzen.)

**Zugriff auf Version 7-Clients deaktivieren:** Gibt an, ob Benutzer Acrobat oder Reader 7.0 verwenden können, um eine Verbindung zum Server herzustellen. Ist diese Option aktiviert, müssen Benutzende Acrobat bzw. Reader 8.0 oder höher verwenden, um Dokumentensicherheitsvorgänge für PDF-Dokumente durchzuführen. Falls Richtlinien erfordern, dass Acrobat bzw. Reader 8.0 oder höher zum Öffnen richtliniengeschützter Dokumente im zertifizierten Modus ausgeführt werden muss, sollten Sie den Zugriff auf Acrobat oder Reader 7 deaktivieren. (Siehe Die Dokumentberechtigungen für Benutzer und Gruppen angeben.)

**Offline-Zugriff pro Dokument zulassen** Wählen Sie diese Option, um den Offline-Zugriff pro Dokument anzugeben. Wenn diese Einstellung aktiviert ist, kann der Benutzer nur auf die Dokumente offline zugreifen, die er mindestens einmal online geöffnet hat.

**Benutzername-/Kennwort-Authentifizierung gestatten:** Aktivieren Sie diese Option, um zu bestimmen, ob Clientanwendungen beim Herstellen einer Serververbindung die Benutzername/Kennwort-Authentifizierung zulassen.

**Kerberos-Authentifizierung gestatten:** Aktivieren Sie diese Option, um zu bestimmen, ob Clientanwendungen beim Herstellen einer Serververbindung die Kerberos-Authentifizierung zulassen.

**Client-Zertifikat-Authentifizierung gestatten:** Aktivieren Sie diese Option, um zu bestimmen, ob Clientanwendungen beim Herstellen einer Serververbindung die Zertifikat-Authentifizierung zulassen.

**Erweiterte Authentifizierung gestatten** Wählen Sie diese Option, um erweiterte Authentifizierung zu aktivieren, und geben Sie dann die Startseiten-URL für die erweiterte Authentifizierung ein.

Wenn Sie diese Option auswählen, können Client-Anwendungen die erweiterte Authentifizierung verwenden. Mit der erweiterten Authentifizierung können auf dem AEM-Formular-Server angepasste Authentifizierungsprozesse und verschiedene Authentifizierungsoptionen konfiguriert werden. Beispielsweise können Benutzende die SAML-basierte Authentifizierung anstelle des AEM Forms-Benutzernamens/Kennworts von Acrobat- und Reader-Clients aus nutzen. Standardmäßig enthält die Landingpage-URL *localhost* als Server-Namen. Ersetzen Sie den Server-Namen durch einen vollständig qualifizierten Host-Namen. Der Host-Name in der Landingpage-URL wird automatisch mit der Basis-URL gefüllt, wenn die erweiterte Authentifizierung noch nicht aktiviert ist. Siehe [Hinzufügen des Anbieters für die erweiterte Authentifizierung](configuring-client-server-options.md#add-the-extended-authentication-provider).

***Hinweis **: Erweiterte Authentifizierung wird auf Apple Mac OS X mit Adobe Acrobat ab Version 11.0.6 unterstützt.*

**Bevorzugte HTML-Kontrollbreite für erweiterte Authentifizierung** Geben Sie die Breite des Dialogfelds für erweiterte Authentifizierung an, das in Acrobat zur Eingabe von Benutzeranmeldeinformationen geöffnet wird.

**Bevorzugte HTML-Steuerelementhöhe für erweiterte Authentifizierung** Geben Sie die Höhe des Dialogfelds für die erweiterte Authentifizierung an, das in Acrobat zur Eingabe von Benutzeranmeldeinformationen geöffnet wird.

***Hinweis **: Die Grenzen der Breite und Höhe für dieses Dialogfeld sind wie folgt:*

Breite: Minimum = 400, Maximum = 900

Höhe: Minimum = 450; Maximum = 800

**Zwischenspeichern von Client-Anmeldeinformationen gestatten:** Wählen Sie diese Option aus, um Benutzern zu erlauben, ihre Anmeldeinformationen (Benutzernamen und Kennwort) zwischenzuspeichern. Wenn die Anmeldeinformationen von Benutzenden zwischengespeichert werden, müssen sie sie beim Öffnen eines Dokuments oder beim Klicken auf die Schaltfläche „Aktualisieren“ auf der Seite „Sicherheitsrichtlinien verwalten“ in Adobe Acrobat nicht jedes Mal eingeben. Sie können die Anzahl der Tage angeben, nach deren Ablauf Benutzende die Anmeldeinformationen erneut eingeben müssen. Bei Festlegung auf 0 Tage werden die Anmeldeinformationen unbegrenzt zwischengespeichert.

## Konfigurieren von Document Security-Benutzenden und -Admins {#configuring-document-security-users-and-administrators}

### Zuweisen von Document Security-Rollen zu Admins {#assigning-document-security-roles-to-administrators}

Ihre AEM Forms-Umgebung enthält eine, einen oder mehrere Admins, die die entsprechenden Berechtigungen zum Erstellen von Benutzenden und Gruppen haben. Wenn Ihr Unternehmen Document Security verwendet, muss mindestens einer bzw. einem Admin auch das Recht zugewiesen sein, eingeladene und lokale Benutzende zu verwalten.

Die Admins müssen auch die Administrationskonsole-Benutzerrolle haben, um auf die Administrationskonsole zugreifen zu können. (Siehe [Erstellen und Konfigurieren von Rollen](/help/forms/using/admin-help/creating-configuring-roles.md#creating-and-configuring-roles).)

### Konfigurieren von sichtbaren Benutzenden und Gruppen {#configuring-visible-users-and-groups}

Um bei Suchen anhand von Benutzerrichtlinien Benutzer und Gruppen in ausgewählten Domains anzuzeigen, muss ein Superadministrator oder Richtliniensatzadministrator (in User Management erstellte) Domains auswählen und der Liste der sichtbaren Benutzer und Gruppen für jeden Richtliniensatz hinzufügen.

Diese Liste wird dem Richtliniensatzkoordinator angezeigt und dient zum Einschränken der Domains, die der Endbenutzer beim Auswählen von Benutzern oder Gruppen durchsuchen kann, die Richtlinien hinzugefügt werden sollen. Wird diese Aufgabe nicht durchgeführt, kann die Richtliniensatzkoordinatorin oder der Richtliniensatzkoordinator keine der Richtlinie hinzuzufügenden Benutzenden oder Gruppen finden. Für jeden Richtliniensatz kann es mehrere Richtliniensatzkoordinierende geben.

1. Richten Sie nach der Installation und Konfiguration der AEM Forms-Umgebung mit Document Security alle gewünschten Domains in User Management ein. <!-- Fix broken link (See Setting up and managing domains) -->

   ***Hinweis **: Das Erstellen von Domains muss vor dem Erstellen von Richtlinien erfolgen.*

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Document Management“ > „Richtlinien“ und dann auf die Registerkarte „Richtliniensätze“.
1. Wählen Sie den globalen Richtliniensatz aus und klicken Sie auf die Registerkarte „Sichtbare Benutzer und Gruppen“.
1. Klicken Sie auf „Domain(s) hinzufügen“ und fügen Sie den Anforderungen entsprechend vorhandene Domains hinzu.
1. Wechseln Sie zu „Dienste“ > „Document Security“ > „Meine Richtlinien“ und klicken Sie auf die Registerkarte „Sichtbare Benutzer und Gruppen“.
1. Klicken Sie auf „Domain(s) hinzufügen“ und fügen Sie den Anforderungen entsprechend vorhandene Domains hinzu.

## Hinzufügen des Anbieters für die erweiterte Authentifizierung {#add-the-extended-authentication-provider}

AEM Forms enthält eine Beispielkonfiguration, die Sie für Ihre Umgebung anpassen können. Führen Sie die folgenden Schritte durch:

>[!NOTE]
>
>Die erweiterte Authentifizierung wird auf Apple macOS mit Adobe Acrobat ab Version 11.0.6 unterstützt.

1. Mit der WAR-Beispieldatei können Sie dies bereitstellen. Informationen finden Sie in dem entsprechenden Installationshandbuch für Ihren Anwendungs-Server.
1. Vergewissern Sie sich, dass der Formular-Server einen voll qualifizierten Namen anstelle von IP-Adressen als Basis-URL hat und dass es sich um eine HTTPS-URL handelt. Siehe [Server-Konfigurationseinstellungen](configuring-client-server-options.md#server-configuration-settings).
1. Aktivieren Sie die erweiterte Authentifizierung über die Server-Konfigurationsseite. Siehe [Server-Konfigurationseinstellungen](configuring-client-server-options.md#server-configuration-settings).
1. Fügen Sie die erforderlichen SSO-Umleitungs-URLs in der User Management-Konfigurationsdatei hinzu. Siehe [Hinzufügen von SSO-Umleitungs-URLs für die erweiterte Authentifizierung](configuring-client-server-options.md#add-sso-redirect-urls-for-extended-authentication).

### Hinzufügen von SSO-Umleitungs-URLs für die erweiterte Authentifizierung {#add-sso-redirect-urls-for-extended-authentication}

Wenn die erweiterte Authentifizierung aktiviert ist, wird beim Öffnen eines richtliniengeschützten Dokuments in Acrobat XI oder Reader XI ein Dialogfeld für die Authentifizierung angezeigt. Dieses Dialogfeld lädt die HTML-Seite, die Sie als Startseiten-URL für erweiterte Authentifizierung in den Document Security-Server-Einstellungen angegeben haben. Siehe [Server-Konfigurationseinstellungen](configuring-client-server-options.md#server-configuration-settings).

>[!NOTE]
>
>Die erweiterte Authentifizierung wird auf Apple macOS mit Adobe Acrobat ab Version 11.0.6 unterstützt.

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Konfiguration“ > „Konfigurationsdateien importieren und exportieren“.
1. Klicken Sie auf „Exportieren“ und speichern Sie die Konfigurationsdatei auf Ihrer Festplatte.
1. Öffnen Sie die Datei in einem Editor und suchen Sie den Knoten „AllowedUrls“.
1. Fügen Sie im `AllowedUrls`-Knoten die folgenden Zeilen hinzu: `<entry key="sso-l" value="/ssoexample/login.jsp"/> <entry key="sso-s" value="/ssoexample"/> <entry key="sso-o" value="/ssoexample/logout.jsp"/>`

   ```xml
   <entry key="sso-l" value="/ssoexample/login.jsp"/>
   <entry key="sso-s" value="/ssoexample"/>
   <entry key="sso-o" value="/ssoexample/logout.jsp"/>
   ```

1. Speichern Sie die Datei und importieren Sie anschließend die aktualisierte Datei von der Seite „Manuelle Konfiguration“: Klicken Sie in der Administration-Console auf „Einstellungen“ > „User Management“ > „Konfiguration“ > „Konfigurationsdateien im- und exportieren“.

## Konfigurieren der Offline-Sicherheit {#configuring-offline-security}

Document Security bietet die Möglichkeit, richtliniengeschützte Dokumente offline, d. h. ohne eine Internet- oder Netzwerkverbindung zu nutzen. Für diese Möglichkeit ist es erforderlich, dass die Richtlinie den Offline-Zugriff zulässt, wie unter [Angeben der Dokumentberechtigungen für Benutzende und Gruppen](/help/forms/using/admin-help/creating-policies.md#specify-the-document-permissions-for-users-and-groups) beschrieben. Bevor ein Dokument mit einer solchen Richtlinie offline genutzt werden kann, müssen Empfangende das Dokument öffnen, während sie online sind, und den Offline-Zugriff aktivieren, indem sie bei Aufforderung auf „Ja“ klicken. Empfangende werden ggf. dazu aufgefordert, ihre Identität zu authentifizieren. Empfangende können anschließend Dokumente offline für die in der Richtlinie angegebene Offline-Nutzungsdauer verwenden.

Nach Ende der Offline-Nutzungsdauer müssen Empfangende das Dokument wieder mit Document Security synchronisieren, indem sie entweder ein Dokument online öffnen oder einen Acrobat-Befehl bzw. einen Acrobat Reader DC-Erweiterungen-Menübefehl zum Synchronisieren verwenden. (Siehe die *Acrobat-Hilfe* oder die entsprechende *Hilfe zu den Acrobat Reader DC-Erweiterungen*.)

Da Dokumente, die einen Offline-Zugriff zulassen, das Caching von Schlüsseldaten auf dem Computer erfordern, auf dem die Dateien offline gespeichert werden, kann die Datei Risiken ausgesetzt sein, wenn unbefugte Personen sich Zugang zu diesen Schlüsseldaten verschaffen können. Um dies zu verhindern, gibt es geplante und manuelle Rollover-Optionen, die Sie konfigurieren können, damit unbefugte Personen, die im Besitz des Schlüssels sind, keinen Zugriff auf das Dokument erhalten.

### Festlegen einer standardmäßigen Offline-Nutzungsdauer {#set-a-default-offline-lease-period}

Empfängerinnen und Empfänger richtliniengeschützter Dokumente können Dokumente für die Anzahl der in der Richtlinie angegebenen Tage offline verwenden. Nach einer einleitenden Synchronisierung des Dokuments mit der Dokumentensicherheit kann die Empfängerin oder der Empfänger das Dokument bis zum Ablauf der Offline-Nutzungsdauer offline verwenden. Nach Ablauf der Nutzungsdauer muss die Person das Dokument online schalten und sich anmelden, um eine Synchronisierung mit der Dokumentensicherheit durchzuführen und das Dokument weiter verwenden zu können.

Sie können eine standardmäßige Offline-Nutzungsdauer festlegen. Die Nutzungsdauer kann vom Standard abweichend geändert werden, wenn eine Person eine Richtlinie erstellt oder bearbeitet.

1. Klicken Sie auf der Seite für die Dokumentensicherheit auf „Konfiguration“ > „Server-Konfiguration“.
1. Geben Sie in das Feld „Standardmäßige Offline-Nutzungsdauer“ die Anzahl der für diesen Zeitraum gewünschten Tage ein.
1. Klicken Sie auf OK.

### Verwalten von Schlüssel-Rollovers {#manage-key-rollovers}

Die Dokumentensicherheit nutzt zum Schützen von Dokumenten Verschlüsselungsalgorithmen und Lizenzen. Beim Verschlüsseln eines Dokuments wird von der Dokumentensicherheit ein *DocKey* genannter Entschlüsselungsschlüssel generiert und verwaltet, der an die Client-Anwendung übergeben wird. Wenn die Richtlinie, die ein Dokument schützt, einen Offline-Zugriff zulässt, wird zudem ein *Hauptschlüssel* genannter Offline-Schlüssel für alle Benutzenden generiert, die Offline-Zugriff auf das Dokument haben.

>[!NOTE]
>
>Wenn noch kein Hauptschlüssel vorhanden ist, generiert die Dokumentensicherheit einen, um ein Dokument zu schützen.

Um ein richtliniengeschütztes Dokument offline zu öffnen, muss der Computer der Person über den entsprechenden Hauptschlüssel verfügen. Der Computer erhält den Hauptschlüssel, wenn die Person eine Synchronisierung mit der Dokumentensicherheit durchführt (d. h., ein geschütztes Dokument online öffnet). Wenn dieser Hauptschlüssel kompromittiert wurde, ist jedes Dokument gefährdet, auf das die Person offline Zugriff hat.

Eine Möglichkeit zum Eindämmen dieser Bedrohung für Offline-Dokumente besteht darin, den Offline-Zugriff auf besonders vertrauliche Dokumente zu vermeiden. Eine weitere Möglichkeit ist das regelmäßige Rollover der Hauptschlüssel. Wenn die Dokumentensicherheit auf den Schlüssel ein Rollover anwendet, kann mit vorhandenen Schlüsseln nicht mehr auf die richtliniengeschützten Dokumente zugegriffen werden. Wenn z. B. Unbefugte sich einen Hauptschlüssel von einem gestohlenen Laptop verschaffen, kann dieser Schlüssel nicht für den Zugriff auf geschützte Dokumente verwendet werden, nachdem ein Rollover erfolgt ist. Wenn Sie vermuten, dass ein bestimmter Hauptschlüssel kompromittiert wurde, können Sie manuell auf den Schlüssel ein Rollover anwenden.

Ein Schlüssel-Rollover betrifft jedoch alle Hauptschlüssel, nicht nur einen. Der Vorgang sorgt zudem für eine Verringerung der Skalierbarkeit des Systems, da Clients für den Offline-Zugriff mehr Schlüssel speichern müssen. Das Schlüssel-Rollover erfolgt standardmäßig alle 20 Tage. Es wird empfohlen, diesen Wert nicht auf weniger als 14 Tage festzulegen, da Benutzende sonst ggf. am Anzeigen von Offline-Dokumenten gehindert werden und die Systemleistung beeinträchtigt wird.

Im folgenden Beispiel ist Schlüssel1 der ältere der beiden Hauptschlüssel und Schlüssel2 ist der neuere. Wenn Sie zum ersten Mal auf die Schaltfläche „Schlüssel jetzt aktualisieren“ klicken, wird Schlüssel1 ungültig und ein neuer gültiger Hauptschlüssel (Schlüssel3) wird generiert. Die Benutzenden erhalten bei der Synchronisierung mit der Dokumentensicherheit Schlüssel3, in der Regel dann, wenn sie ein geschütztes Dokument online öffnen. Die Benutzenden müssen jedoch erst eine Synchronisierung mit der Dokumentensicherheit durchführen, wenn sie die in der Richtlinie angegebene maximale Offline-Nutzungsdauer erreicht haben. Nach dem ersten Schlüssel-Rollover können Offline-Benutzende Offline-Dokumente, einschließlich der durch Schlüssel3 geschützten Dokumente, noch so lange öffnen, bis sie die maximale Offline-Nutzungsdauer erreicht haben. Wenn Sie ein zweites Mal auf die Schaltfläche „Schlüssel jetzt aktualisieren“ klicken, wird Schlüssel2 ungültig und Schlüssel4 wird erstellt. Benutzende, die während der beiden Schlüsselaktualisierungen offline sind, können durch Schlüssel3 oder Schlüssel4 geschützte Dokumente erst wieder öffnen, nachdem sie eine Synchronisierung mit der Dokumentensicherheit ausgeführt haben.

**Ändern des Zeitintervalls für Schlüssel-Rollover**

Zum Schutz der Vertraulichkeit bei der Nutzung von Offline-Dokumenten bietet die Dokumentensicherheit eine automatische Schlüssel-Rollover-Option mit einem Standardzeitintervall von 20 Tagen. Sie können dieses Rollover-Intervall zwar ändern, es wird jedoch empfohlen, diesen Wert nicht auf weniger als 14 Tage festzulegen, da Benutzende sonst ggf. am Anzeigen von Offline-Dokumenten gehindert werden und die Systemleistung beeinträchtigt wird.

1. Klicken Sie auf der Seite für die Dokumentensicherheit auf „Konfiguration“ > „Schlüsselverwaltung“.
1. Geben Sie in das Feld „Zeitintervall für Schlüsselaktualisierungen“ die Anzahl der für diesen Zeitraum gewünschten Tage ein.
1. Klicken Sie auf OK.

**Manuelles Rollover der Hauptschlüssel**

Um die Vertraulichkeit von Offline-Dokumenten zu wahren, können Sie Hauptschlüssel manuell aktualisieren. Es ist ggf. erforderlich, einen Schlüssel manuell zu aktualisieren, etwa wenn sich eine unbefugte Person den Schlüssel von einem Computer verschafft hat, auf dem der Schlüssel für den Offline-Zugriff auf ein Dokument zwischengespeichert ist.

>[!NOTE]
>
>Vermeiden Sie zu häufige manuelle Aktualisierungen, da dadurch alle Hauptschlüssel und nicht nur einer aktualisiert werden, was Benutzende vorübergehend an der Offline-Anzeige neuer Dokumente hindern kann.

Die Hauptschlüssel müssen zweimal aktualisiert werden, bevor bereits vorhandene Schlüssel auf Client-Computern ihre Gültigkeit verlieren. Client-Computer, die über ungültig gemachte Hauptschlüssel verfügen, müssen eine erneute Synchronisierung mit dem Dienst für die Dokumentensicherheit ausführen, um die neuen Hauptschlüssel zu erhalten.

1. Klicken Sie auf der Seite für die Dokumentensicherheit auf „Konfiguration“ > „Schlüsselverwaltung“.
1. Klicken Sie auf „Schlüssel jetzt aktualisieren“ und dann auf „OK“.
1. Warten Sie ungefähr zehn Minuten.  Im Serverprotokoll wird die folgende Protokoll-Meldung angezeigt: `Done RightsManagement key rollover for`*N* `principals`. Dabei steht *N* für die Anzahl der Benutzenden im Dokumentensicherheitssystem.
1. Klicken Sie auf „Schlüssel jetzt aktualisieren“ und dann auf „OK“.
1. Warten Sie ungefähr zehn Minuten.

## Konfigurieren von Ereignis-Auditing- und Datenschutzeinstellungen {#configuring-event-auditing-and-privacy-settings}

Die Dokumentensicherheit kann Informationen zu Ereignissen im Zusammenhang mit dem Arbeiten mit richtliniengeschützten Dokumenten, Richtlinien, Admins und dem Server prüfen und aufzeichnen.  Sie können ein Ereignis-Auditing konfigurieren und die Typen zu prüfender Ereignisse angeben.  Um Ereignisse für ein bestimmtes Dokument zu prüfen, muss die Auditing-Option für die Richtlinie ebenfalls aktiviert sein.

Ist das Auditing aktiviert, können Sie Details zu geprüften Ereignissen auf der Seite „Ereignisse“ anzeigen.  Benutzende der Dokumentensicherheit können auch gezielt Ereignisse für die von ihnen selbst verwendeten oder erstellten richtliniengeschützten Dokumente anzeigen.

Sie können die folgenden zu prüfenden Ereignistypen auswählen:

* Ereignisse bei richtliniengeschützten Dokumenten, z. B. Versuche autorisierter bzw. nicht autorisierter Benutzender, Dokumente zu öffnen.
* Richtlinienereignisse wie das Erstellen, Ändern, Löschen, Aktivieren und Deaktivieren von Richtlinien.
* Benutzerereignisse, z. B. Einladungen und Registrierungen externer Benutzender, Aktivierung und Deaktivierung von Benutzerkonten, Änderungen von Benutzerkennwörtern und Aktualisierungen von Profilen.
* AEM Forms-Ereignisse, z. B. Nichtübereinstimmungen von Versionen, nicht verfügbare Verzeichnis-Server und Autorisierungsanbieter sowie Änderungen von Server-Konfigurationen

### Aktivieren oder Deaktivieren des Auditings von Ereignissen {#enable-or-disable-event-auditing}

Sie können das Auditing von Ereignissen im Zusammenhang mit dem Server, richtliniengeschützten Dokumenten, Richtlinien, Richtliniensätzen und Benutzenden aktivieren bzw. deaktivieren.  Wenn Sie das Ereignis-Auditing aktivieren, können Sie alle möglichen Ereignisse oder bestimmte Ereignisse in die Prüfung einbeziehen.

Wenn Sie das Server-Auditing aktivieren, können Sie die geprüften Ereignisse auf der Seite „Ereignisse“ anzeigen.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Prüfungs- und Datenschutzeinstellungen“.
1. Um das Server-Auditing zu konfigurieren, wählen Sie unter „Serverprüfung aktivieren“ entweder „Ja“ oder „Nein“ aus.
1. Führen Sie bei Wahl von „Ja“ unter jeder Ereigniskategorie eine der folgenden Aktionen aus, um die zu prüfenden Optionen auszuwählen:

   * Um alle Ereignisse in der Kategorie zu prüfen, wählen Sie „Alle“.
   * Um nur bestimmte Ereignisse zu prüfen, deaktivieren Sie „Alle“, und wählen Sie anschließend die Kontrollkästchen neben den zu prüfenden Ereignissen aus.

     (Siehe [Ereignis-Auditing-Optionen](configuring-client-server-options.md#event-auditing-options).)

1. Klicken Sie auf OK.

>[!NOTE]
>
>Verwenden Sie beim Arbeiten mit Web-Seiten nicht die Schaltflächen des Browsers (z. B. die Schaltfläche „Zurück“, die Schaltfläche „Aktualisieren“ oder die Pfeilschaltflächen „Zurück“ und „Vorwärts“), da dies zu unerwünschten Problemen bei der Erfassung und Anzeige von Daten führen kann.

### Aktivieren oder Deaktivieren von Datenschutzbenachrichtigungen {#enable-or-disable-privacy-notification}

Sie können eine Datenschutzbenachrichtigung aktivieren bzw. deaktivieren.  Beim Aktivieren der Datenschutzbenachrichtigung wird eine Meldung eingeblendet, wenn eine Empfängerin oder ein Empfänger versucht, ein richtliniengeschütztes Dokument zu öffnen.  Die Meldung informiert die Person, dass die Dokumentnutzung geprüft wird. Sie können auch eine URL angeben, auf die Benutzende zum Anzeigen einer Seite mit Datenschutzrichtlinien, falls vorhanden, klicken kann.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Prüfungs- und Datenschutzeinstellungen“.
1. Um die Datenschutzbenachrichtigung zu konfigurieren, wählen Sie unter „Datenschutzbestimmung aktivieren“ entweder „Ja“ oder „Nein“ aus.

   Wenn die an ein Dokument angehängte Richtlinie Zugriff durch anonyme Benutzende zulässt und wenn die Option „Datenschutzbestimmung aktivieren“ auf „Nein“ festgelegt ist, werden Benutzende nicht aufgefordert, sich anzumelden, und die Datenschutzbenachrichtigung wird nicht angezeigt.

   Wenn die an ein Dokument angehängte Richtlinie keinen Zugriff durch anonyme Benutzende zulässt, wird diesen die Datenschutzbenachrichtigung angezeigt.

1. Geben Sie, falls möglich, in das Feld „Datenschutz-URL“ die URL der Seite mit den Datenschutzrichtlinien ein.  Wenn das Feld „Datenschutz-URL“ leer gelassen wird, wird die Seite mit den Datenschutzeinstellungen von adobe.com angezeigt.
1. Klicken Sie auf OK.

>[!NOTE]
>
>Wenn Sie die Datenschutzhinweise deaktivieren, wird nicht gleichzeitig die Prüfung von Dokumentverwendung deaktiviert. Vorkonfigurierte Auditing-Aktionen und benutzerdefinierte Aktionen, die über erweitertes Nutzungs-Tracking unterstützt werden, können weiterhin Informationen zum Benutzerverhalten sammeln.

### Importieren eines benutzerdefinierten Auditing-Ereignistyps {#import-a-custom-audit-event-type}

Wenn Sie eine Anwendung mit aktivierter Dokumentensicherheit verwenden, die das Auditing zusätzlicher Ereignisse unterstützt, z. B. von für einen bestimmten Dateityp spezifischen Ereignissen, kann Ihnen ein Adobe-Partner benutzerdefinierte Audit-Ereignisse bereitstellen, die Sie in die Dokumentensicherheit importieren können. Wählen Sie diese Funktion nur aus, wenn Ihnen ein Adobe-Partner die benutzerspezifischen Ereignistypen bereitgestellt hat.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Ereignisverwaltung“.
1. Klicken Sie auf „Durchsuchen“, um zu der zu importierenden XML-Datei zu navigieren, und klicken Sie dann auf „Importieren“.
1. Beim Importieren werden auf dem Server vorhandene benutzerdefinierte Audit-Ereignistypen überschrieben, wenn identische Kombinationen aus Ereignis-Code und Namespace gefunden werden.
1. Klicken Sie auf OK.

### Löschen eines benutzerdefinierten Audit-Ereignistyps {#delete-a-custom-audit-event-type}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Ereignisverwaltung“.
1. Wählen Sie das Kontrollkästchen neben dem benutzerdefinierten Audit-Ereignistypen, den Sie löschen möchten, und klicken Sie auf „Löschen“.
1. Klicken Sie auf OK.

### Exportieren von Audit-Ereignissen {#export-audit-events}

Sie können Audit-Ereignisse zu Archivierungszwecken in eine Datei exportieren.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Ereignisverwaltung“.
1. Bearbeiten Sie unter „Audit-Ereignisse exportieren“ die Einstellungen wie gewünscht. Sie können Folgendes angeben:

   * das Mindestalter der zu exportierenden Audit-Ereignisse
   * die maximale Anzahl der Audit-Ereignisse, die eine Datei enthalten soll  Der Server erstellt eine oder mehrere Dateien auf Basis dieses Wertes.
   * der Ordner, in dem die Datei erstellt wird  Dieser Ordner befindet sich auf dem Formular-Server. Wenn der Ordnerpfad relativ ist, dann ist er relativ zum Stammverzeichnis für den Anwendungs-Server.
   * das für die Audit-Ereignisdateien zu verwendende Präfix
   * das Format der Datei, entweder eine CSV-Datei (Comma Separated Value, durch Komma getrennter Wert), die mit Microsoft Excel kompatibel ist, oder eine XML-Datei

1. Klicken Sie auf „Exportieren“. Wenn Sie den Export abbrechen möchten, klicken Sie auf „Export abbrechen“. Wenn eine andere Benutzerin oder ein anderer Benutzer einen Export geplant hat, steht die Schaltfläche „Export abbrechen“ nicht zur Verfügung, bis dieser Exportvorgang beendet ist. Die Schaltfläche „Export abbrechen“ steht nicht zur Verfügung, wenn eine andere Benutzerin oder ein anderer Benutzer einen Export geplant hat. Klicken Sie auf „Aktualisieren“, um zu überprüfen, ob ein geplanter Export- oder Löschvorgang gestartet oder beendet wurde.

### Löschen von Audit-Ereignissen {#delete-audit-events}

Sie können Audit-Ereignisse löschen, die älter als eine angegebene Anzahl von Tagen sind.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Ereignisverwaltung“.
1. Geben Sie unter „Prüfereignisse löschen“ die Anzahl der Tage im Feld „Prüfereignisse löschen an, die älter sind als“.
1. Klicken Sie auf Löschen. Klicken Sie auf „Exportieren“. Wenn Sie den Löschvorgang abbrechen möchten, klicken Sie auf „Löschvorgang abbrechen“. Wenn eine andere Benutzerin oder ein anderer Benutzer einen Löschvorgang geplant hat, steht die Schaltfläche „Löschvorgang abbrechen“ nicht zur Verfügung, bis dieser Export beendet ist. Die Schaltfläche „Löschvorgang abbrechen“ steht nicht zur Verfügung, wenn eine andere Benutzerin oder ein anderer Benutzer einen Export geplant hat. Klicken Sie auf „Aktualisieren“, um zu überprüfen, ob ein geplanter Löschvorgang gestartet oder beendet wurde.

### Ereignis-Auditing-Optionen {#event-auditing-options}

Sie können das Ereignis-Auditing aktivieren und deaktivieren und die zu prüfenden Ereignistypen angeben.

**Dokumentereignisse**

**Dokument anzeigen:** Ein Empfänger zeigt ein richtliniengeschütztes Dokument an.

**Dokument schließen:** Ein Empfänger schließt ein richtliniengeschütztes Dokument.

**Mit niedriger Auflösung drucken** Ein Empfänger druckt ein richtliniengeschütztes Dokument bei aktivierter Option für die niedrige Auflösung.

**Mit hoher Auflösung drucken** Ein Empfänger druckt ein richtliniengeschütztes Dokument bei aktivierter Option für die hohe Auflösung.

**Anmerkung zu Dokument hinzufügen:** Ein Empfänger fügt einem PDF-Dokument eine Anmerkung hinzu.

**Dokument sperren:** Ein Benutzer oder Administrator sperrt den Zugriff auf ein richtliniengeschütztes Dokument.

**Dokument entsperren:** Ein Benutzer oder Administrator reaktiviert den Zugriff auf ein richtliniengeschütztes Dokument.

**Formular ausfüllen:** Ein Empfänger gibt Informationen in ein Dokument ein, das ein ausfüllbares Formular ist.

**Richtlinie entfernen:** Ein Herausgeber entfernt eine Richtlinie vom Dokument, um den Schutz zu entfernen.

**Dokument-Sperr-URL ändern:** Ein Aufruf auf API-Ebene ändert eine Sperr-URL (die für den Zugriff auf ein neues Dokument, das ein gesperrtes Dokument ersetzt, angegebene URL).

**Dokument ändern:** Ein Empfänger ändert den Inhalt eines richtliniengeschützten Dokuments.

**Dokument unterschreiben:** Ein Empfänger signiert ein Dokument.

**Neues Dokument sichern:** Ein Benutzer wendet eine Richtlinie an, um ein Dokument zu schützen.

**Dokument-Richtlinie wechseln:** Ein Benutzer oder Administrator wechselt die für ein Dokument geltende Richtlinie.

**Dokument veröffentlichen als:** Ein neues Dokument, dessen Dokumentname und Lizenz mit einem vorhandenen Dokument identisch sind, wird auf dem Server registriert und die Dokumente haben keine hierarchische Beziehung. Dieses Ereignis kann mit dem AEM Forms-SDK ausgelöst werden.

**Dokument iterieren:** Ein neues Dokument, dessen Dokumentname und Lizenz mit einem vorhandenen Dokument identisch sind, wird auf dem Server registriert und die Dokumente haben eine hierarchische Beziehung. Dieses Ereignis kann mit dem AEM Forms-SDK ausgelöst werden.

**Richtlinienereignisse**

**Erstellte Richtlinie:** Ein Benutzer oder Administrator erstellt eine Richtlinie.

**Richtlinie aktiviert:** Ein Administrator stellt eine Richtlinie zur Verfügung.

**Geänderte Richtlinie:** Ein Benutzer oder Administrator ändert eine Richtlinie.

**Richtlinie deaktiviert:** Ein Administrator macht eine Richtlinie nicht verfügbar.

**Gelöschte Richtlinie:** Ein Benutzer oder Administrator löscht eine Richtlinie.

**Richtlinieneigentümer ändern:** Ein Aufruf auf API-Ebene ändert den Richtlinieneigentümer.

**Benutzerereignisse**

**Gelöschter Benutzer:** Ein Administrator löscht ein Benutzerkonto.

**Eingeladenen Benutzer registrieren:** Ein externer Benutzer registriert sich bei Document Security.

**Erfolgreicher Anmeldeversuch:** Erfolgreiche Anmeldeversuche von Administratoren und Benutzern.

**Eingeladene Benutzer:** Document Security lädt einen Benutzer zur Registrierung ein.

**Aktivierte Benutzer:** Externe Benutzer aktivieren ihre Konten über die URL in der Aktivierungs-E-Mail oder ein Administrator aktiviert ein Konto.

**Kennwort ändern:** Eingeladene Benutzer ändern ihr Kennwort oder ein Administrator setzt ein Kennwort eines lokalen Benutzers zurück.

**Fehlgeschlagener Anmeldeversuch:** Fehlgeschlagene Anmeldeversuche von Administratoren oder Benutzern.

**Deaktivierte Benutzer:** Ein Administrator deaktiviert ein lokales Benutzerkonto.

**Profil-Update:** Eingeladene Benutzer ändern ihren Namen, den Firmennamen und das Kennwort.

**Konto gesperrt:** Ein Administrator sperrt ein Konto.

**Richtliniensatzereignisse**

**Erstellter

Richtliniensatz:** Ein Administrator oder Richtliniensatzkoordinator erstellt einen Richtliniensatz.

**Gelöschter Richtliniensatz:** Ein Administrator oder Richtliniensatzkoordinator löscht einen Richtliniensatz.

**Geänderter Richtliniensatz:** Ein Administrator oder Richtliniensatzkoordinator ändert einen Richtliniensatz.

**Systemereignisse**

**Ordner

synchronisierung abgeschlossen:** Diese Informationen sind nicht auf der Seite Ereignisse verfügbar. Die aktuellen Informationen zur Ordnersynchronisierung, einschließlich des aktuellen Synchronisierungszustands und des Zeitpunktes der letzten Synchronisierung, werden auf der Seite „Domain-Verwaltung“ angezeigt. Um Zugriff auf die Domain-Verwaltung zu erhalten, klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.

**Offline-Zugriff für Client aktivieren:** Eine Person hat den Offline-Zugriff auf Dokumente aktiviert, die auf dem eigenen Computer gegen den Server geschützt sind.

**Synchronisierte Clientanwendung** Die Clientanwendung muss Informationen mit dem Server synchronisieren, um den Offline-Zugriff zuzulassen.

**Inkompatible Version:** Eine Version des AEM Forms-SDK, die nicht mit dem Server kompatibel ist, versuchte, eine Verbindung mit dem Server herzustellen.

**Informationen zur Ordnersynchronisierung:** Diese Informationen sind nicht auf der Seite Ereignisse verfügbar. Die aktuellen Informationen zur Ordnersynchronisierung, einschließlich des aktuellen Synchronisierungszustands und des Zeitpunktes der letzten Synchronisierung, werden auf der Seite „Domain-Verwaltung“ angezeigt. Um Zugriff auf die Domain-Verwaltung zu erhalten, klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.

**Änderungen an der Serverkonfiguration:** Änderungen an der Serverkonfiguration, die entweder über die Webseiten oder manuell durch Importieren einer „config.xml“-Datei erfolgen. Dazu zählen Änderungen der Basis-URL, Zeitüberschreitungseinstellungen für Sitzungen, Anmeldesperren, Verzeichniseinstellungen, Schlüsselaktualisierungen, SMTP-Server-Einstellungen für die externe Registrierung, Konfiguration von Wasserzeichen, Anzeigeoptionen usw.

## Konfigurieren der erweiterten Nutzungsverfolgung {#configuring-extended-usage-tracking}

Die Dokumentensicherheit kann mehrere benutzerdefinierte Ereignisse verfolgen, die für ein geschütztes Dokument durchgeführt werden. Sie können das Verfolgen von Ereignissen auf dem Dokumentensicherheits-Server auf globaler Ebene oder Richtlinienebene aktivieren. Sie können JavaScript einrichten, um dann die gewünschten Aktionen zu erfassen, die innerhalb des geschützten PDF-Dokuments ausgeführt werden, z. B. das Klicken auf eine Schaltfläche oder Speichern des Dokuments. Diese Nutzungsdaten werden als XML-Datei in Schlüssel-Wert-Paaren übermittelt, die Sie für die weitere Analyse verwenden können. Endbenutzende, die auf die geschützten Dokumente zugreifen, können diese Verfolgung über die Client-Anwendung zulassen oder ablehnen.

Wenn die Verfolgung auf globaler Ebene aktiviert ist, können Sie diese Einstellung auf Richtlinienebene überschreiben und sie für eine bestimmte Richtlinie deaktivieren. Das Überschreiben auf Richtlinienebene ist nicht möglich, wenn die Verfolgung auf globaler Ebene deaktiviert ist. Die Liste der verfolgten Ereignisse wird per Push automatisch an den Server gesendet, wenn die Ereigniszählung 25 erreicht oder wenn das Dokument geschlossen wird. Sie können Ihr Skript auch so konfigurieren, dass die Liste der Ereignisse entsprechend Ihren Anforderungen explizit per Push gesendet wird. Sie können die Ereignisverfolgung anpassen, indem Sie auf die Objekteigenschaften und Methoden der Dokumentensicherheit zugreifen.

Nachdem Sie die Verfolgung aktiviert haben, ist bei allen nachfolgend erstellten Richtlinien die Verfolgung standardmäßig aktiviert. Die Richtlinien, die erstellt wurden, bevor die Verfolgung auf dem Server aktiviert wurde, müssen manuell aktualisiert werden.

### Aktivieren oder Deaktivieren der erweiterten Nutzungsverfolgung {#enable-or-disable-extended-usage-tracking}

Bevor Sie beginnen, müssen Sie sicherstellen, dass das Server-Auditing aktiviert ist.  Unter [Konfigurieren von Ereignis-Auditing- und Datenschutzeinstellungen](configuring-client-server-options.md#configuring-event-auditing-and-privacy-settings) finden Sie weitere Informationen zum Auditing.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Prüfungs- und Datenschutzeinstellungen“.
1. Um das erweiterte Nutzungs-Tracking zu konfigurieren, wählen Sie unter „Verfolgung aktivieren“ „Ja“ oder „Nein“ aus.
1. Um die Option zum Zulassen der Sammlung von detaillierten Nutzungsdaten auf der Anmeldeseite zu konfigurieren, wählen Sie unter „Verfolgung standardmäßig aktivieren“ die Option „Ja“ oder „Nein“ aus.

Zum Anzeigen der verfolgten Ereignisse können Sie den Filter „Dokumentereignisse“ auf der Ereignisseite verwenden.  Die Ereignisse, die mithilfe von JavaScript verfolgt werden, werden als detailliertes Nutzungs-Tracking bezeichnet.  Unter [Ereignisse überwachen](/help/forms/using/admin-help/monitoring-events.md#monitoring-events) finden Sie weitere Informationen zu Ereignissen.

## Konfigurieren der Anzeigeeinstellungen für die Dokumentensicherheit {#configure-document-security-display-settings}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Anzeigeoptionen“.
1. Konfigurieren Sie die Einstellungen und klicken Sie auf „OK“.

### Anzeigeeinstellungen {#display-settings}

**Für Suchergebnisse anzuzeigende Zeilen:** Anzahl der Zeilen, die auf einer Seite angezeigt werden, wenn Suchvorgänge durchgeführt werden.

**Anpassen des Dialogfelds zur Client-Anmeldung**

Diese Einstellungen steuern den Text in der Anmeldeaufforderung, die angezeigt wird, wenn Sie sich über eine Client-Anwendung bei der Dokumentensicherheit anmelden.

**Begrüßungstext**: Der Text der Begrüßungsnachricht, z. B. „Bitte melden Sie sich mit Ihrem Benutzernamen und Kennwort an“. Der Begrüßungstext sollte Informationen dazu enthalten, wie die Anmeldung bei der Dokumentensicherheit erfolgen soll und wie Admins oder anderes Support-Personal in Ihrem Unternehmen kontaktiert werden können, falls Hilfe benötigt wird.  Externe Benutzende müssen ggf. Admins kontaktieren, wenn sie ihr Kennwort vergessen haben oder Hilfe bei der Registrierung oder Anmeldung benötigen. Die maximale Länge des Begrüßungstexts beträgt 512 Zeichen.

**Benutzernamentext:** Die Textbeschriftung für das Feld Benutzername.

**Kennworttext:** Die Textbeschriftung für das Feld „Kennwort“.

**Anpassung des Dialogfelds für die Client-Zertifikatauthentifizierung**

Diese Einstellungen steuern den im Dialogfeld für die Zertifikatauthentifizierung angezeigten Text.

**Text für 
„Authentifizierungstyp auswählen“:** Der Text, der angezeigt wird, um einen Benutzer zur Auswahl eines Authentifizierungstyps aufzufordern.

**Text für „Zertifikat auswählen“:** Der Text der angezeigt wird, um den Benutzer zum Auswählen eines Zertifikattyps aufzufordern.

**Fehlertext für „Zertifikate nicht verfügbar“:** Meldung mit bis zu 512 Zeichen, die angezeigt wird, wenn das ausgewählte Zertifikat nicht verfügbar ist.

**Client-Zertifikatanzeige anpassen**

**Nur Herausgeber von vertrauenswürdigen Berechtigungen anzeigen:** Wenn diese Option aktiviert ist, legt die Client-Anwendung dem Benutzer nur Zertifikate von Zertifizierungsstellen vor, die von AEM Forms laut Konfiguration als vertrauenswürdig eingestuft sind (siehe Verwalten von Zertifikaten und Berechtigungen.) Wenn diese Option nicht ausgewählt ist, wird der Person eine Liste aller Zertifikate angezeigt, die sich auf ihrem System befinden.

## Konfigurieren dynamischer Wasserzeichen {#configure-dynamic-watermarks}

Mit der Dokumentensicherheit können Sie die Standardeinstellungen für die dynamische Wasserzeichenoption konfigurieren, die Sie beim Erstellen von Richtlinien aktivieren können.  Ein *Wasserzeichen* ist eine Grafik, mit welcher der Text im Dokument überlagert wird. Es dient zum Tracking des Inhalts eines Dokuments und kann zum Ermitteln einer unzulässigen Nutzung von Inhalten beitragen.

Ein dynamisches Wasserzeichen kann entweder aus Text, der sich aus definierten Variablen wie Benutzer-ID und -Datum und benutzerdefiniertem Text zusammensetzt, oder aus Multimediainhalt in einer PDF-Datei bestehen.  Sie können Wasserzeichen mit mehreren Elementen konfigurieren, wobei für jedes Element eine eigene Position und Formatierung festgelegt wird.

Das Wasserzeichen kann nicht geändert werden und ist deshalb eine sichere Methode, um dafür zu sorgen, dass die Vertraulichkeit des Dokumentinhalts gewährleistet ist.  Dynamische Wasserzeichen sorgen auch dafür, dass ein Wasserzeichen genügend benutzerspezifische Informationen anzeigt, um eine weitere Verteilung des Dokuments einzudämmen.

Das in einer Richtlinie angegebene Wasserzeichen wird im richtliniengeschützten Dokument angezeigt, wenn eine Empfängerin oder ein Empfänger das Dokument anzeigt oder druckt.  Im Gegensatz zu dauerhaften Wasserzeichen wird ein dynamisches Wasserzeichen nie im Dokument gespeichert. Dies bietet die Flexibilität, die bei der Bereitstellung eines Dokuments in einer Intranet-Umgebung erforderlich ist, um sicherzustellen, dass die Anzeigeanwendung die Identität der spezifischen Person anzeigt. Wenn ein Dokument darüber hinaus mehrere Benutzende hat, ermöglicht die Verwendung eines dynamischen Wasserzeichens, dass Sie ein einzelnes Dokument anstatt mehrerer Versionen mit je einem unterschiedlichen Wasserzeichen verwenden können.  Das angezeigte Wasserzeichen gibt die Identität der aktuellen Person an.

Beachten Sie, dass sich dynamische Wasserzeichen von den Wasserzeichen unterscheiden, die Benutzende dem Dokument in Acrobat direkt hinzufügen können.  Dies bedeutet, dass ein richtliniengeschütztes Dokument zwei Wasserzeichen aufweisen kann.

### Überlegungen zum Erstellen von Wasserzeichen {#considerations-when-creating-watermarks}

Sie können dynamische Wasserzeichen mit mehreren Wasserzeichenelementen erstellen, wobei jedes Element entweder als Text oder als PDF-Datei angegeben wird.  Sie können einem Wasserzeichen bis zu fünf Elemente hinzufügen.

Wenn Sie ein textbasiertes Wasserzeichen auswählen, können Sie mehrere Elemente innerhalb des Wasserzeichens mit mehreren Texteinträgen angeben und die Position jedes Elements festlegen.  Ordnen Sie diesen Elementen aussagekräftige Namen zu, z. B. Kopf- und Fußzeilen.

Wenn Sie beispielsweise unterschiedlichen Text in Kopf- und Fußzeilen, an den Rändern und im gesamten Dokument als Wasserzeichen angeben möchten, erstellen Sie mehrere Wasserzeichenelemente und legen Sie ihre Position fest.  Wenn Sie möchten, dass die Benutzer-ID des Benutzers und das aktuelle Datum des Zugriffs auf das Dokument in der Kopfzeile, der Name der Richtlinie am rechten Rand und ein benutzerdefinierter Text wie „VERTRAULICH“ diagonal über dem Dokument erscheinen, definieren Sie separate Wasserzeichenelemente mit Text als Typ und legen dessen Formatierung und Positionierung fest. Wenn das Wasserzeichen auf ein Dokument angewendet wird, werden alle Elemente im Wasserzeichen gleichzeitig auf das Dokument angewendet, und zwar in der Reihenfolge, in der sie dem Wasserzeichen hinzugefügt werden.

In der Regel verwenden Sie PDF-basierte Wasserzeichen, damit grafische Inhalte wie Logos oder Sonderzeichen wie das Symbol für Copyright oder eingetragene Marken eingefügt werden können.

Sie können das Limit für die Anzahl von Wasserzeichenelementen und die PDF-Dateigröße ändern, indem Sie die Konfigurationsdatei für die Dokumentensicherheit ändern. Siehe [Ändern der Parameter der Wasserzeichenkonfiguration](configuring-client-server-options.md#change-the-watermark-configuration-parameters).

Beachten Sie beim Konfigurieren von Wasserzeichen Folgendes:

* Sie können kein kennwortgeschütztes PDF-Dokument als Wasserzeichenelement verwenden. Wenn das Wasserzeichen, das Sie erstellen, andere Elemente enthält, die nicht mit einem Kennwort geschützt sind, werden sie als Teil des Wasserzeichens angewendet.
* Sie können die maximale Größe der PDF-Datei ändern, die als Wasserzeichenelement verwendet werden soll. Allerdings beeinträchtigen große PDF-Dokumente, die als Wasserzeichen verwendet werden, die Leistung bei der Offline-Synchronisierung von Dokumenten, auf die diese Wasserzeichen angewendet wurden. Siehe [Ändern von Parametern der Wasserzeichenkonfiguration](configuring-client-server-options.md#change-the-watermark-configuration-parameters).
* Nur die erste Seite der ausgewählten PDF-Datei wird als Wasserzeichen verwendet. Stellen Sie sicher, dass die Informationen, die als Wasserzeichen angezeigt werden sollen, auf der ersten Seite verfügbar sind.
* Obwohl Sie die Skalierung des PDF-Dokuments angeben können, beachten Sie die Seitengröße und das Layout des PDF-Dokuments, wenn Sie dieses als Wasserzeichen in der Kopf- oder Fußzeile oder an den Rändern verwenden möchten.
* Wenn Sie den Schriftnamen angeben, achten Sie darauf, dass Sie den Namen richtig eingeben. AEM Forms ersetzt die von Ihnen angegebene Schrift, wenn sie auf dem Client-Computer, auf dem das Dokument geöffnet wird, nicht vorhanden ist.
* Wenn Sie Text als Wasserzeicheninhalt ausgewählt haben, können Sie für Seiten mit abweichender Breite nicht die Skalierungsoption „An Seite anpassen“ festlegen.
* Wenn Sie die Position der Wasserzeichenelemente angeben, stellen Sie sicher, dass nicht mehr als ein Element dieselbe Position hat. Wenn zwei Wasserzeichenelemente dieselbe Position haben, z. B. die Mittelposition, werden sie im Dokument als überlappend und in der Reihenfolge angezeigt, in der sie dem Wasserzeichen hinzugefügt wurden.
* Wenn Sie den Schriftgrad und -typ angeben, stellen Sie sicher, dass der Text in voller Länge auf der Seite sichtbar ist. Textinhalte werden in neue Zeilen weitergeführt, sodass der Wasserzeicheninhalt, der an den Rändern angezeigt werden soll, sich mit den Inhaltsbereichen auf den Seiten überlappen kann. Wenn das Dokument jedoch in Acrobat 9 geöffnet wird, wird der Text über die einzeilige Textzeile hinaus abgeschnitten.

### Einschränkungen bei dynamischen Wasserzeichen {#limitations-of-dynamic-watermarks}

Einige Client-Anwendungen unterstützen möglicherweise keine dynamischen Wasserzeichen. Weitere Informationen finden Sie in der entsprechenden Hilfe zu den Acrobat Reader DC-Erweiterungen. Darüber hinaus ist Folgendes zu den Versionen von Acrobat, die dynamische Wasserzeichen unterstützen, zu beachten:

* Sie können kein kennwortgeschütztes PDF-Dokument als Wasserzeichenelement verwenden.
* Acrobat- und Adobe Reader-Versionen (niedriger als Version 10) unterstützen folgende Wasserzeichenfunktionen nicht:

   * PDF-Wasserzeichen.
   * Mehrere Elemente im Wasserzeichen (Text/PDF).
   * Erweiterte Optionen wie Seitenbereich oder Anzeigeoptionen.
   * Textformatierungsoptionen wie die Angabe der Schrift, des Schriftnamens und der Schriftfarbe. Immerhin zeigen niedrigere Versionen von Acrobat und Reader den Textinhalt in der Standardschrift und -farbe an.

* Acrobat 9.0 und niedrigere Versionen: Acrobat 9.0 und niedrigere Versionen unterstützen keine Richtliniennamen in dynamischen Wasserzeichen. Wenn Acrobat 9.0 ein richtliniengeschütztes Dokument mit einem dynamischen Wasserzeichen öffnet, das einen Richtliniennamen oder andere dynamische Daten enthält, wird das Wasserzeichen ohne den Richtliniennamen angezeigt. Wenn das dynamische Wasserzeichen nur den Richtliniennamen enthält, zeigt Acrobat eine Fehlermeldung an.

### Hinzufügen einer Vorlage für dynamische Wasserzeichen {#add-a-dynamic-watermark-template}

Sie können Vorlagen für dynamische Wasserzeichen erstellen. Diese Vorlagen bleiben als Konfigurationsoption für Richtlinien verfügbar, die von Admins oder Benutzenden erstellt werden.

>[!NOTE]
>
>Die Konfigurationsinformationen dynamischer Wasserzeichen werden beim Exportieren einer Konfigurationsdatei nicht zusammen mit anderen Konfigurationsinformationen erfasst.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Wasserzeichen“.
1. Klicken Sie auf Neu.
1. Geben Sie in das Feld „Name“ einen Namen für das neue Wasserzeichen ein.

   ***Hinweis **: Einige Sonderzeichen können nicht in den Namen oder Beschreibungen von Wasserzeichen oder Wasserzeichenelementen verwendet werden. Weitere Informationen zu den Einschränkungen finden Sie unter [Überlegungen zum Bearbeiten von Richtlinien](/help/forms/using/admin-help/creating-policies.md#considerations-for-editing-policies).*

1. Geben Sie unter „Name“ neben dem Pluszeichen einen aussagekräftigen Namen für das Wasserzeichenelement ein, z. B. „Kopfzeile“. Fügen Sie dann eine neue Beschreibung hinzu. Anschließend klicken Sie auf das Pluszeichen, um die Optionen anzuzeigen.
1. Wählen Sie unter „Quelle“ den Typ des Wasserzeichens aus, entweder „Text“ oder „PDF“.
1. Wenn Sie „Text“ auswählen, gehen Sie wie folgt vor:

   * Wählen Sie die zu berücksichtigenden Wasserzeichentypen aus. Wenn Sie „Benutzerdefinierter Text“ auswählen, geben Sie in das Feld daneben den für das Wasserzeichen anzuzeigenden Text ein. Beachten Sie die Textlänge des Wasserzeichens.
   * Geben Sie die Eigenschaften für die Textformatierung wie Schriftartname, Schriftgröße und Vorder- sowie Hintergrundfarbe für den Textinhalt des Wasserzeichentextes an. Geben Sie die Vorder- und Hintergrundfarbe als Hexadezimalwerte an.

     ***Hinweis **: Wenn Sie die Skalierungsoption als „An Seite anpassen“ wählen, steht die Eigenschaft der Schriftgröße nicht zur Bearbeitung zur Verfügung.*

1. Wenn Sie „PDF“ für komplexe Wasserzeichen ausgewählt haben, klicken Sie neben der Option „Wasserzeichen-PDF auswählen“ auf **Durchsuchen**, um das PDF -Dokument auszuwählen, das als Wasserzeichen verwendet werden soll.

   ***Hinweis **: Verwenden Sie kein kennwortgeschütztes PDF-Dokument. Wenn Sie ein kennwortgeschütztes PDF als Wasserzeichenelement angeben, wird das Wasserzeichen nicht angewendet.*

1. Wählen Sie für „Als Hintergrund verwenden“ entweder „Ja“ oder „Nein“ aus.

   **Hinweis**: Derzeit wird das Wasserzeichen unabhängig von dieser Einstellung im Vordergrund angezeigt.

1. Um zu bestimmen, wo das Wasserzeichen im Dokument angezeigt werden soll, konfigurieren Sie die Optionen „Vertikale Ausrichtung“ und „Horizontale Ausrichtung“.
1. Wählen Sie entweder „An Seite anpassen“ oder „%“ aus, und geben Sie einen Prozentsatz in das Feld ein. Der Wert muss eine ganze Zahl sein, keine Dezimalzahl. Um die Größe des Wasserzeichens zu konfigurieren, können Sie einen Wert verwenden, der dem Prozentsatz der Seite entspricht, oder das Wasserzeichen so festlegen, dass es der Größe der Seite entspricht.
1. Geben Sie im Feld „Drehung“ die Gradzahl an, um die das Wasserzeichen gedreht werden soll. Der Bereich liegt zwischen -180 und 180. Verwenden Sie einen negativen Wert, um das Wasserzeichen gegen den Uhrzeigersinn zu drehen. Der Wert muss eine ganze Zahl sein, keine Dezimalzahl.
1. Geben Sie in das Feld „Deckkraft“ einen Prozentwert ein. Verwenden Sie eine ganze Zahl, keine Dezimalzahl.
1. Legen Sie unter „Erweiterte Optionen“ Folgendes fest:

   **Seitenbereichsoptionen**

   Legen Sie den Bereich der Seiten fest, auf dem das Wasserzeichen angezeigt werden soll. Geben Sie die Startseite als 1 und die Endseite als -1 ein, damit alle Seiten mit dem Wasserzeichen versehen werden.

   **Anzeigeoptionen**

   Wählen Sie aus, wo das Wasserzeichen angezeigt werden soll. Standardmäßig wird das Wasserzeichen sowohl auf der Softcopy (online) als auch auf der Hardcopy (Druck) angezeigt.

1. Klicken Sie unter „Wasserzeichenelemente“ auf **Neu**, um weitere Wasserzeichenelemente hinzuzufügen, falls erforderlich.
1. Klicken Sie auf OK.

### Bearbeiten einer Vorlage für dynamische Wasserzeichen {#edit-a-dynamic-watermark-template}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Wasserzeichen“.
1. Wählen Sie in der Liste das gewünschte Wasserzeichen aus.
1. Auf der Seite „Wasserzeichen bearbeiten“ können Sie die Einstellungen wie gewünscht verändern.
1. Klicken Sie auf OK.

### Löschen einer Vorlage für dynamische Wasserzeichen {#delete-a-dynamic-watermark-template}

Wenn Sie ein dynamisches Wasserzeichen löschen, kann es nicht mehr zu einer neuen Richtlinie hinzugefügt werden. Das Wasserzeichen bleibt jedoch bei bestehenden Richtlinien erhalten, die es gegenwärtig verwenden. Dokumente, die von der Richtlinie derzeit geschützt sind, zeigen das dynamische Wasserzeichen weiterhin an, bis Sie oder Benutzende die Richtlinie bearbeiten, die das gelöschte Wasserzeichen enthält. Nach Bearbeitung der Richtlinie wird das Wasserzeichen nicht mehr angewendet. Es wird die Meldung angezeigt, dass das vorhandene Wasserzeichen aus der Richtlinie gelöscht wurde und ein anderes ausgewählt werden kann, um es zu ersetzen.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Wasserzeichen“.
1. Aktivieren Sie das Kontrollkästchen neben dem entsprechenden Wasserzeichen und klicken Sie auf „Löschen“.
1. Klicken Sie auf OK.

## Konfigurieren der Registrierung für eingeladene Benutzende {#configuring-invited-user-registration}

Firmenexterne Benutzende können sich bei der Dokumentensicherheit registrieren. Eingeladene Benutzende, die sich registrieren und ihre Konten aktivieren, können sich bei der Dokumentensicherheit mit den Anmeldeinformationen (E-Mail-Adresse und Kennwort) anmelden, die sie bei der Registrierung angegeben haben. Registrierte, eingeladene Benutzende können richtliniengeschützte Dokumente verwenden, für die sie Berechtigungen haben.

Nach ihrer Aktivierung werden eingeladene Benutzende zu lokalen Benutzenden. Lokale Benutzende können im Bereich „Eingeladene und lokale Benutzer“ konfiguriert und verwaltet werden. (Siehe [Verwalten von Konten eingeladener und lokaler Benutzender](/help/forms/using/admin-help/invited-local-user-accounts.md#managing-invited-and-local-user-accounts).)

Je nachdem, welche Funktionen Sie für eingeladene Benutzende aktiviert haben, können diese die folgenden Dokumentensicherheits-Funktionen verwenden:

* Anwenden von Richtlinien auf Dokumente
* Erstellen von Richtlinien
* Hinzufügen eingeladener Benutzender zu Richtlinien 

Die Dokumentensicherheit generiert automatisch eine Einladungs-E-Mail zur Registrierung, wenn die folgenden Ereignisse eintreten, es sei denn, die Person befindet sich bereits im LDAP-Quellverzeichnis oder wurde schon zuvor zur Registrierung eingeladen:

* Vorhandene Benutzende fügen eine eingeladene Person zu einer Richtlinie hinzu.
* Admins fügen auf der Seite „Registrierung für eingeladene Benutzer“ das Konto einer eingeladenen Person hinzu.

Die Registrierungs-E-Mail enthält einen Link zu einer Registrierungsseite sowie Informationen zur Registrierung.  Nachdem sich die eingeladene Person registriert hat, sendet die Dokumentensicherheit eine Aktivierungs-E-Mail mit einem Link zu einer Aktivierungsseite.  Nach der Aktivierung bleibt das Konto gültig, bis Sie es deaktivieren oder löschen.

Wenn Sie die integrierte Registrierung aktivieren, geben Sie Ihren SMTP-Server, die Details der Registrierungs-E-Mail, die Zugriffsmöglichkeiten und den Text der E-Mail-Nachricht zum Zurücksetzen des Kennworts nur einmal an.  Bevor Sie die integrierte Registrierung aktivieren, stellen Sie sicher, dass Sie in der Benutzerverwaltung eine lokale Domäne erstellt und den entsprechenden Benutzenden und Gruppen in Ihrem Unternehmen die Rolle „Dokumentensicherheit – Benutzer einladen“ zugewiesen haben. (Siehe [Lokale Domain hinzufügen](/help/forms/using/admin-help/adding-domains.md#add-a-local-domain) und [Rollen erstellen und konfigurieren](/help/forms/using/admin-help/creating-configuring-roles.md#creating-and-configuring-roles).) Wenn Sie „Integrierte Registrierung“ nicht verwenden, müssen Sie über ein eigenes mit dem AEM Forms-SDK erstelltes Benutzerregistrierungssystem verfügen. Siehe die Hilfe zu „Entwickeln von SPIs für AEM-Formulare“ in [Programmieren mit AEM Forms](/help/forms/developing/introducing-java-api-soap-quick.md). Wenn Sie die integrierte Registrierung nicht verwenden, ist es ratsam, eine Meldung in der Aktivierungs-E-Mail sowie auf dem Client-Anmeldebildschirm zu konfigurieren, um Benutzende zu informieren, wie sie die Admins für ein neues Kennwort oder andere Informationen kontaktieren können.

**Aktivieren und Konfigurieren der Registrierung für eingeladene Benutzende**

Der Registrierungsprozess ist für eingeladene Benutzende standardmäßig deaktiviert.  Sie können für eingeladene Benutzende die Registrierung für die Dokumentensicherheit den Anforderungen entsprechend aktivieren oder deaktivieren.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Dokumentensicherheit“ > „Konfiguration“ > „Registrierung für eingeladene Benutzer“.
1. Wählen Sie „Registrierung für eingeladene Benutzer aktivieren“.
1. (Optional) Aktualisieren Sie die Einstellungen für die Registrierung eingeladener Benutzender den Anforderungen entsprechend:

   * [Externe Benutzer oder Benutzergruppen ein- oder ausschließen](configuring-client-server-options.md#exclude-or-include-an-external-user-or-group)
   * [Server- und Registrierungskontoparameter](configuring-client-server-options.md#server-and-registration-account-parameters)
   * [Einstellungen für die Einladungs-E-Mail zur Registrierung](configuring-client-server-options.md#registration-invitation-email-settings)
   * [Einstellungen für Aktivierungs-E-Mail](configuring-client-server-options.md#activation-email-settings)
   * [Eine E-Mail zum Zurücksetzen des Kennworts konfigurieren](configuring-client-server-options.md#configure-a-password-reset-email)

1. (Optional) Um die integrierte Registrierung zu verwenden, wählen Sie „Ja“ aus. Wenn Sie die integrierte Registrierung nicht aktivieren, müssen Sie ein eigenes Benutzerregistrierungssystem einrichten.
1. Klicken Sie auf OK.

### Ein- oder Ausschließen von externen Benutzern oder Benutzergruppen {#exclude-or-include-an-external-user-or-group}

Sie können die Registrierung bei der Dokumentensicherheit auf bestimmte externe Benutzende oder Benutzergruppen beschränken.  Diese Option ist hilfreich, wenn Sie beispielsweise einer bestimmten Benutzergruppe den Zugriff erlauben, jedoch bestimmte Gruppenmitglieder ausschließen möchten.

Die folgenden Einstellungen befinden sich im Bereich „Filter für E-Mail-Adressen“ auf der Seite „Registrierung für eingeladene Benutzer“.

**Ausschluss:** Geben Sie die E-Mail-Adresse eines Benutzers oder einer Gruppe ein, die Sie ausschließen möchten. Um mehrere Benutzende oder Gruppen auszuschließen, geben Sie jede E-Mail-Adresse in eine neue Zeile ein.  Um alle Benutzer, die zu einer bestimmten Domain gehören, auszuschließen, geben Sie einen Platzhalter und den Domain-Namen ein. Um beispielsweise alle Benutzer mit der Domain „example.com“ auszuschließen, geben Sie „*.example.com“ ein.

**Einbeziehung:** Geben Sie die E-Mail-Adresse eines Benutzers oder einer Gruppe ein, die Sie einbeziehen möchten. Um mehrere Benutzende oder Gruppen einzubeziehen, geben Sie jede E-Mail-Adresse in eine neue Zeile ein. Um alle Benutzer, die zu einer bestimmten Domäne gehören, einzubeziehen, geben Sie einen Platzhalter und den Domänennamen ein. Um beispielsweise alle Benutzer mit der Domain „example.com“ einzubeziehen, geben Sie „*.example.com“ ein.

### Server- und Registrierungskontoparameter {#server-and-registration-account-parameters}

Die folgenden Einstellungen befinden sich im Bereich „Allgemeine Einstellungen“ auf der Seite „Registrierung für eingeladene Benutzer“.

**SMTP-Host:** Der Host-Name des SMTP-Servers. Der SMTP-Server verwaltet die ausgehenden E-Mail-Nachrichten für die Registrierung und Aktivierung eingeladener Benutzender.

Falls für den SMTP-Host erforderlich, füllen Sie die Felder „Kontoname für den SMTP-Server“ und „Kennwort des Kontos für den SMTP-Server“ aus, um eine Verbindung mit dem SMTP-Server herzustellen.  Bei einigen Unternehmen ist dies nicht erforderlich.  Wenden Sie sich an Ihre Systemadmins, falls Sie Informationen benötigen.

**Socket-Klassenname des SMTP-Servers:** Socket-Klassenname für den SMTP-Server. Zum Beispiel javax.net.ssl.SSLSocketFactory.

**E-Mail-Content-Typ:** Akzeptierter MIME-Typ wie text/plain oder text/html.

**E-Mail-Kodierung:** Das zum Senden der E-Mail-Nachricht zu verwendende Kodierungsformat. Sie können jede beliebige Kodierung angeben, z. B. UTF-8 für Unicode oder ISO-8859-1 für Latein.  Die Standardeinstellung ist UTF-8.

**E-Mail-Adresse umleiten:** Wenn Sie eine E-Mail-Adresse für diese Einstellung angeben, werden alle neuen Einladungen an die angegebene Adresse gesendet. Diese Einstellung kann für Testzwecke sinnvoll sein.

**Lokale Domains verwenden:** Wählen Sie die entsprechende Domain aus. Stellen Sie bei einer Neuinstallation sicher, dass Sie die Domain in User Management erstellt haben. Bei einem Update kann eine externe Benutzer-Domain, die während des Updates erstellt wurde, verwendet werden.

**SSL für SMTP-Server verwenden:** Wählen Sie diese Option, um SSL für den SMTP-Server zu aktivieren.

**Anmelde-Link auf Registrierungsseite anzeigen:** Zeigt einen Anmelde-Link auf der Registrierungsseite für eingeladene Benutzer an.

**Aktivieren von Transport Layer Security (TLS) für den SMTP-Server**

1. Öffnen Sie die Administrationskonsole.

   Der Standardspeicherort der Administration-Console ist `https://<server>:<port>/adminui`.

1. Wechseln Sie zur Startseite > „Dienste“ > „Dokumentensicherheit“ > „Konfiguration“ > „Registrierung für eingeladene Benutzer“.
1. Geben Sie unter „Registrierung für eingeladene Benutzer“ alle Konfigurationseinstellungen an und klicken Sie auf „OK“.

   >[!NOTE]
   >
   >Wenn Sie Microsoft Office 365 als SMTP-Server zum Senden der Einladungen für eine Benutzerregistrierung verwenden, verwenden Sie die folgenden Einstellungen:
   >
   >**SMTP Host:** smtp.office365.com
   >**Port:** 587

1. Als Nächstes müssen Sie „config.xml“ aktualisieren. Weitere Informationen finden Sie unter [Konfiguration für die Aktivierung von SMTP für Transport Layer Security (TLS)](configuring-client-server-options.md#configuration-to-enable-smtp-for-transport-layer-security-tls).

>[!NOTE]
>
>Wenn Sie Änderungen an den Optionen für die Registrierung eingeladener Benutzer vornehmen, wird die Datei „config.xml“ überschrieben und TLS wird deaktiviert. Wenn Sie die Änderungen überschreiben, müssen Sie mithilfe des oben beschriebenen Schritts die TLS-Unterstützung für die Registrierung eingeladener Benutzender reaktivieren.

### Einstellungen für die Einladungs-E-Mail zur Registrierung {#registration-invitation-email-settings}

Die Dokumentensicherheit sendet automatisch eine Einladungs-E-Mail zur Registrierung, wenn Sie ein Konto für eine eingeladene Person erstellen oder wenn eine bestehende Person einer Richtlinie eine externe Empfängerin oder einen externen Empfänger hinzufügt, die bzw. der bislang weder registriert noch eingeladen wurde.  Die E-Mail enthält einen Link, über den die Empfängerin bzw. der Empfänger auf die Registrierungsseite zugreifen kann, um persönliche Kontoinformationen einschließlich Benutzername und Kennwort einzugeben.  Das Kennwort kann eine beliebige Kombination von acht Zeichen sein.

Wenn die Person ihr Konto aktiviert hat, wird sie eine lokale Benutzerin bzw. ein lokaler Benutzer.

Die folgenden Einstellungen befinden sich im Bereich „E-Mail-Konfiguration“ auf der Seite „Registrierung für eingeladene Benutzer“.

**Von:** Die E-Mail-Adresse, von der die Einladungs-E-Mail gesendet wird. Das Standardformat der „Von“-E-Mail-Adresse ist „postmaster@[Ihre_Installations-Domain].com“.

**Betreff:** Standardbetreff für die E-Mail-Nachricht mit der Einladung.

**Maximale Wartezeit:** Die Anzahl der Tage, nach denen die Registrierungseinladung abläuft, wenn sich der externe Benutzer nicht registriert. Der Standardwert ist 30 Tage.

**Nachricht:** Der Text, der im Textkörper der Nachricht angezeigt wird und den Benutzer zur Registrierung einlädt.

### Einstellungen für die Aktivierungs-E-Mail {#activation-email-settings}

Nach der Registrierung erhalten eingeladene Benutzende eine Aktivierungs-E-Mail von der Dokumentensicherheit.  Die Aktivierungs-E-Mail enthält einen Link zur Kontoaktivierungsseite, auf welcher Benutzende ihr Konto aktivieren können.  Nach der Aktivierung des Kontos können sich Benutzende bei der Dokumentensicherheit mit den Anmeldeinformationen (E-Mail-Adresse und Kennwort) anmelden, die sie bei der Registrierung angegeben haben.

Wenn die Person das Benutzerkonto aktiviert hat, wird sie eine lokale Benutzerin bzw. ein lokaler Benutzer.

Die folgenden Einstellungen befinden sich im Bereich „Konfiguration der Aktivierungs-E-Mail“ auf der Seite „Registrierung für eingeladene Benutzer“.

>[!NOTE]
>
>Es empfiehlt sich auch, eine Meldung auf dem Anmeldebildschirm zu konfigurieren, die externe Benutzende informiert, wie sie ihre Admins für ein neues Kennwort oder andere Informationen kontaktieren können.

**Von:** Die E-Mail-Adresse, von der die Aktivierungs-E-Mail gesendet wird. Diese E-Mail-Adresse empfängt Benachrichtigungen zu fehlgeschlagenen Übermittlungen vom E-Mail-Host der Person, die sich registriert, sowie Nachrichten, die als Antwort auf die Registrierungs-E-Mail gesendet werden. Das Standardformat der „Von“-E-Mail-Adresse ist „postmaster@[Ihre_Installations-Domain].com“.

**Betreff:** Standardbetreff für die Aktivierungs-E-Mail-Nachricht.

**Maximale Wartezeit:** Die Anzahl der Tage, nach denen die Aktivierungseinladung abläuft, wenn der Benutzer das Konto nicht aktiviert. Der Standardwert ist 30 Tage.

**Nachricht:** Der Text, der im Textkörper der Nachricht angezeigt wird und der angibt, dass das Benutzerkonto der Empfängerin bzw. des Empfängers aktiviert werden muss. Sie können nach Wunsch weitere Informationen hinzufügen, z. B. wie sich Admins kontaktieren lassen oder wie ein neues Kennwort bezogen werden kann.

### Konfigurieren einer E-Mail zum Zurücksetzen des Kennworts {#configure-a-password-reset-email}

Wenn Sie das Kennwort einer eingeladenen Person zurücksetzen müssen, wird eine Bestätigungs-E-Mail generiert, die die Person einlädt, ein neues Kennwort auszuwählen.  Es gibt keine Möglichkeit, das Kennwort einer Person zu ermitteln. Wurde es vergessen, müssen Sie es zurücksetzen.

Die folgenden Einstellungen befinden sich im Bereich „Konfiguration der E-Mail zum Zurücksetzen des Kennworts“ auf der Seite „Registrierung für eingeladene Benutzer“.

**Von:** Die E-Mail-Adresse, von der die E-Mail zum Zurücksetzen des Kennworts gesendet wird. Das Standardformat der „Von“-E-Mail-Adresse ist „postmaster@[Ihre_Installations-Domain].com“.

**Betreff:** Standardbetreff für die Nachricht zum Zurücksetzen.

**Nachricht:** Der Text, der im Textkörper der Nachricht angezeigt wird und der angibt, dass das Kennwort für externe Benutzende der Empfängerin bzw. des Empfängers zurückgesetzt wurde.

## Aktivieren von Benutzenden und Gruppen zum Erstellen von Richtlinien {#enable-users-and-groups-to-create-policies}

Die Seite „Konfiguration“ enthält einen Hyperlink zur Seite „Meine Richtlinien“. Dort können Sie angeben, welche Endbenutzenden eigene Richtlinien erstellen dürfen und welche Benutzenden und Gruppen in Suchergebnissen angezeigt werden. Die Seite „Meine Richtlinien“ hat zwei Registerkarten:

**Registerkarte „Richtlinien erstellen“:** Wird verwendet, um Benutzerberechtigungen zum Erstellen benutzerdefinierter Richtlinien zu konfigurieren.

**Registerkarte „Sichtbare Benutzer und Gruppen“:** Hier können Sie steuern, welche Benutzer und Gruppen in den Suchergebnissen der Benutzer sichtbar sind. Der Hauptbenutzer oder Richtliniensatzadministrator muss für jeden Richtliniensatz in User Management erstellte Domains auswählen und zum sichtbaren Benutzer bzw. zur sichtbaren Gruppe hinzufügen. Diese Liste wird dem Richtliniensatzkoordinator angezeigt und dient zum Eingrenzen der Domains, die der Richtliniensatzkoordinator beim Auswählen von Benutzern durchsuchen kann, die Richtlinien hinzugefügt werden sollen.

Bevor Sie Benutzenden die Berechtigung zum Erstellen benutzerdefinierter Richtlinien erteilen, denken Sie darüber nach, wie weit die Zugriffs- und Steuerungsmöglichkeiten der einzelnen Benutzenden gehen sollen. Prüfen Sie auch, welche Informationen zu Gruppen und Benutzenden angezeigt werden sollen, wenn sie in Suchergebnissen sichtbar sind.

### Angeben von Benutzenden und Gruppen mit Berechtigung zum Erstellen von Richtlinien {#specify-users-and-groups-who-can-create-policies}

Als Admin können Sie angeben, welche Benutzenden und Gruppen benutzerdefinierte Richtlinien erstellen dürfen. Diese Berechtigung kann auf Benutzer- und Gruppenebene erteilt werden. Die Suchfunktion durchsucht die Benutzerverwaltungsdatenbank nach Benutzenden und Gruppen.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Dokumentensicherheit“ > „Konfiguration“ > „Meine Richtlinien“.
1. Klicken Sie auf der Seite „Meine Richtlinien“ auf die Registerkarte „Richtlinien erstellen“ und dann auf „Benutzer und Gruppen hinzufügen“.
1. Geben Sie in das Feld „Suchen“ den Benutzernamen oder die E-Mail-Adresse der Person bzw. Gruppe ein, die Sie suchen. Wenn Sie diese Angaben nicht kennen, lassen Sie das Feld leer. Sie können einen Namen oder eine E-Mail-Adresse auch teilweise eingeben, wenn Ihnen beispielsweise nur die ersten beiden Buchstaben eines Benutzernamens bekannt sind.
1. Wählen Sie in der Liste „Verwendet“ die Suchparameter „Name“ oder „E-Mail“ aus.
1. Wählen Sie in der Liste „Typ“ den Eintrag „Gruppe“ oder „Benutzer“ aus, um die Suche einzugrenzen.
1. Wählen Sie in der Liste „In“ die zu durchsuchende Domain aus. Wenn Sie die Domain der Person oder Gruppe nicht kennen, wählen Sie „Alle Domains“ aus.
1. Geben Sie in der Liste „Anzeigen“ die Anzahl der pro Seite anzuzeigenden Suchergebnisse ein und klicken Sie auf „Suchen“.
1. Um Benutzende und Gruppen zu „Meine Richtlinien“ hinzuzufügen, aktivieren Sie die Kontrollkästchen der hinzuzufügenden Benutzenden und Gruppen.
1. Klicken Sie auf „Hinzufügen“ und dann auf „OK“.

Die ausgewählten Benutzenden und Gruppen dürfen nun benutzerdefinierte Richtlinien erstellen.

### Entfernen der Berechtigung zum Erstellen benutzerdefinierter Richtlinien für Benutzende oder Gruppen {#remove-the-create-custom-policies-permission-from-a-user-or-group}

1. Klicken Sie auf der Seite für die Dokumentensicherheit auf „Konfiguration“ > „Meine Richtlinien“.
1. Klicken Sie auf der Seite „Meine Richtlinien“ auf die Registerkarte „Richtlinien erstellen“. Benutzende und Gruppen mit der Berechtigung zum Erstellen benutzerdefinierter Richtlinien werden angezeigt.
1. Aktivieren Sie die Kontrollkästchen neben den Benutzenden und Gruppen, für die diese Berechtigung entfernt werden soll.
1. Klicken Sie auf „Löschen“ und anschließend auf „OK“.

### Angeben von Benutzenden und Gruppen, die in Suchvorgängen sichtbar sind {#specify-users-and-groups-that-are-visible-in-searches}

Wenn Benutzende ihre benutzerdefinierten Richtlinien verwalten, können sie Benutzende und Gruppen suchen, die ihren Richtlinien hinzugefügt werden sollen. Geben Sie die Domains an, aus denen Benutzende und Gruppen in diesen Suchergebnissen angezeigt werden sollen.

1. Klicken Sie auf der Seite für die Dokumentensicherheit auf „Konfiguration“ > „Meine Richtlinien“.
1. Klicken Sie auf der Seite „Meine Richtlinien“ auf die Registerkarte „Sichtbare Benutzer und Gruppen“.
1. Um die Benutzer und Gruppen in einer Domain sichtbar zu machen, klicken Sie auf „Domains hinzufügen“, wählen Sie die Domains aus und klicken Sie auf „Hinzufügen“. Aktivieren Sie zum Entfernen einer Domain das Kontrollkästchen neben dem Domain-Namen und klicken Sie auf „Löschen“.

## Manuelles Bearbeiten der Konfigurationsdatei für die Dokumentensicherheit {#manually-editing-the-document-security-configuration-file}

Sie können die Konfigurationsinformationen importieren und exportieren, die in der Dokumentensicherheits-Datenbank gespeichert sind. Sie sollten beispielsweise eine Sicherungskopie der Konfigurationsinformationen erstellen, wenn Sie von einer Staging- in eine Produktionsumgebung wechseln. Sie können auch die erweiterten Optionen bearbeiten, die nur durch Bearbeiten dieser Datei konfiguriert werden können.

Mithilfe der Konfigurationsdatei können Sie folgende Änderungen vornehmen:

[Anzeigen der CATIA-Berechtigungen beim Erstellen und Bearbeiten von Richtlinien](configuring-client-server-options.md#display-catia-permissions-when-creating-and-editing-policies)

[Angeben eines Zeitlimits für die Offline-Synchronisation](configuring-client-server-options.md#specify-a-timeout-period-for-offline-synchronization)

[Ablehnen von Document Security-Diensten für bestimmte Anwendungen](configuring-client-server-options.md#denying-document-security-services-for-specific-applications)

[Parameter der Wasserzeichenkonfiguration ändern](configuring-client-server-options.md#change-the-watermark-configuration-parameters)

[Externe Verknüpfungen deaktivieren](configuring-client-server-options.md#disabling-external-links)

>[!NOTE]
>
>Beim Importieren der Konfigurationsdatei wird Ihr System basierend auf den Informationen in der Datei neu konfiguriert.  Eine Ausnahme bilden die Konfigurationsinformationen dynamischer Wasserzeichen sowie Informationen über benutzerdefinierte Ereignisse, die nicht in der exportierten Konfigurationsdatei gespeichert werden.  Konfigurieren Sie diese Informationen manuell in Ihrem neuen System. Nur Systemadmins oder versierte IT-Fachleute, die mit Dokumentensicherheit und XML vertraut sind, sollten den Inhalt einer Konfigurationsdatei ändern (um beispielsweise eine fehlerhafte Einstellung neu zu konfigurieren oder Parameter für ein bestimmtes Unternehmensbereitstellungsszenario zu optimieren).

**Exportieren einer Konfigurationsdatei**

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Document Security 11“ > „Konfiguration“ > „Manuelle Konfiguration“.
1. Klicken Sie auf „Exportieren“ und speichern Sie die Konfigurationsdatei an einem anderen Speicherort.  Der Standarddateiname lautet „config.xml“.
1. Klicken Sie auf OK.
1. Bevor Sie Änderungen an der Konfigurationsdatei vornehmen, sollten Sie eine Sicherungskopie für den Fall erstellen, dass Sie den Ausgangszustand wiederherstellen müssen.

**Eine Konfigurationsdatei importieren**

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Document Security 11“ > „Konfiguration“ > „Manuelle Konfiguration“.
1. Klicken Sie auf „Durchsuchen“, um zur Konfigurationsdatei zu wechseln, und klicken Sie dann auf „Importieren“.  Sie können den Pfad nicht direkt in das Feld „Dateiname“ eingeben.
1. Klicken Sie auf OK.

### Angeben eines Zeitlimits für die Offline-Synchronisation {#specify-a-timeout-period-for-offline-synchronization}

Die Dokumentensicherheit ermöglicht Benutzenden das Öffnen und Verwenden geschützter Dokumente, wenn sie über keine Verbindung zum Dokumentensicherheits-Server verfügen.  Die Client-Anwendung der Person muss regelmäßig mit dem Server synchronisiert werden, damit die Dokumente für die Offline-Nutzung gültig bleiben.  Wenn die Person zum ersten Mal ein geschütztes Dokument öffnen möchte, wird sie gefragt, ob der Computer zum Ausführen der periodischen Client-Synchronisation autorisiert werden soll.

Die Synchronisation wird standardmäßig automatisch alle vier Stunden und nach Bedarf ausgeführt, wenn die Person eine Verbindung mit dem Document Security-Server hergestellt hat.  Wenn der Offline-Zeitraum für ein Dokument abläuft, während die Person offline ist, muss sie erneut eine Verbindung zum Server herstellen, damit die Client-Anwendung mit dem Server synchronisiert werden kann.

In der Document Security-Konfigurationsdatei können Sie das Standardzeitintervall der automatischen Hintergrundsynchronisation angeben.  Diese Einstellung fungiert als Standardzeitlimit für die Client-Anwendungen, es sei denn, der Client legt ausdrücklich seinen eigenen Zeitlimitwert fest.

1. Exportieren Sie die Document Security-Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Konfigurationsdatei für die Dokumentensicherheit](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)
1. Öffnen Sie die Konfigurationsdatei in einem Editor und suchen Sie den Knoten `PolicyServer`. Suchen Sie unter diesem Knoten den Knoten `ServerSettings`.
1. Fügen Sie im Knoten `ServerSettings` den folgenden Eintrag hinzu und speichern Sie anschließend die Datei:

   `<entry key="BackgroundSyncFrequency" value="`*Uhrzeit* `"/>`

   dabei ist *time* die Anzahl der Sekunden zwischen den automatischen Hintergrundsynchronisationen. Wenn Sie diesen Wert auf `0` festgelegt haben, wird immer eine Synchronisation ausgeführt. Der Standardwert ist `14400` Sekunden (alle vier Stunden).

1. Importieren Sie die Konfigurationsdatei.  (Siehe [Manuelles Bearbeiten der Konfigurationsdatei für die Dokumentensicherheit](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)

### Ablehnen von Document Security-Diensten für bestimmte Anwendungen {#denying-document-security-services-for-specific-applications}

Sie können die Dokumentensicherheit so konfigurieren, dass Dienste für Anwendungen, die bestimmte Kriterien erfüllen, abgelehnt werden.  Die Kriterien können ein einzelnes Attribut, z. B. einen Plattformnamen, oder mehrere Attributsätze angeben.  Mithilfe dieser Funktion können Sie die Anforderungen steuern, die die Dokumentensicherheit verarbeiten muss.  Im Folgenden finden Sie einige Anwendungen dieser Funktion:

* **Einkommensschutz:** Sie können den Zugriff auf Clientanwendungen, die Ihre Einkommenskonventionen nicht unterstützen, verweigern.
* **Anwendungskompatibilität:** Einige Anwendungen sind möglicherweise nicht mit den Richtlinien oder dem Verhalten Ihres Document Security-Servers kompatibel.

Wenn Client-Anwendungen versuchen, eine Verknüpfung mit der Dokumentensicherheit herzustellen, stellen sie Anwendungs-, Versions- und Plattforminformationen bereit.  Die Dokumentensicherheit vergleicht diese Informationen mit den Verweigerungseinstellungen, die es aus der Dokumentensicherheits-Konfigurationsdatei abruft.

Die Verweigerungseinstellungen können mehrere Verweigerungsbedingungen enthalten.  Wenn alle Attribute eines Satzes übereinstimmen, wird der anfordernden Anwendung der Zugriff auf die Dokumentensicherheits-Dienste verweigert.

Die Dienstblockaden-Funktion erfordert, dass Client-Anwendungen das Document Security C++ Client SDK ab Version 8.2 verwenden.  Die folgenden Adobe-Produkte stellen beim Anfordern von Dokumentensicherheits-Diensten Produktinformationen bereit:

* Adobe Acrobat 9.0 Professional/Acrobat 9.0 Standard und höher
* Adobe Reader 9.0 und höher
* Acrobat Reader DC-Erweiterungen für Microsoft Office ab Version 8.2

Client-Anwendungen verwenden die Client-API des Document Security C++ Client SDK, um Dienste von der Dokumentensicherheit anzufordern.  Die Client-API-Anforderungen enthalten Informationen über die Plattform und SDK-Version (vorkompiliert in die Client-API) sowie Produktinformationen, die aus der Client-Anwendung abgerufen wurden.

Client-Anwendungen oder Plug-ins unterstützen Produktinformationen bei ihrer Implementierung einer Rückruffunktion.  Die Anwendung stellt die folgenden Informationen bereit:

* Integrator-Name
* Integrator-Version
* Anwendungsfamilie
* Anwendungsname
* Anwendungsversion

Wenn bestimmte Informationen nicht verfügbar sind, bleibt das entsprechende Feld in der Client-Anwendung leer.

Einige Adobe-Anwendungen, darunter Acrobat, Adobe Reader und Acrobat Reader DC-Erweiterungen für Microsoft Office, enthalten Produktinformationen, die bei der Anforderung von Dokumentensicherheits-Diensten bereitgestellt werden.

**Acrobat und Adobe Reader**

Wenn Acrobat oder Adobe Reader einen Dienst von der Dokumentensicherheit anfordert, werden die folgenden Produktinformationen bereitgestellt:

* **Integrator:** Adobe Systems, Inc.
* **Integrator-Version:** 1.0
* **Anwendungsfamilie:** Acrobat
* **Anwendungsname:** Acrobat
* **Anwendungsversion:** 9.0.0

**Acrobat Reader DC-Erweiterungen für Microsoft Office**

Acrobat Reader DC-Erweiterungen für Microsoft Office ist ein Plug-in, das mit den Microsoft Office-Produkten Microsoft Word, Microsoft Excel und Microsoft PowerPoint verwendet wird.  Wenn es einen Dienst anfordert, stellt es die folgenden Informationen bereit:

* **Integrator:** Adobe Systems Incorporated
* **Integrator-Version:** 8.2
* **Anwendungsfamilie:** Acrobat Reader DC Extensions für Microsoft Office
* **Anwendungsname:** Microsoft Word, Microsoft Excel oder Microsoft PowerPoint
* **Anwendungsversion:** 2003 oder 2007

**Konfigurieren der Dokumentensicherheit zum Ablehnen von Diensten für bestimmte Anwendungen**

1. Exportieren Sie die Document Security-Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Konfigurationsdatei für die Dokumentensicherheit](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)
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

   Hierbei gilt:

   `SDKPlatforms` gibt die Plattform an, die als Host für die Clientanwendung dient. Mögliche Werte sind:

   * Microsoft Windows
   * Apple OS X
   * Sun Solaris
   * HP-UX

   `SDKVersions` gibt die Version der Document Security C++ Client-API an, die von der Clientanwendung verwendet wird. Beispiel: `"8.2"`.

   `APPFamilies` ist durch die Client-API definiert.

   `AppName` gibt den Namen der Clientanwendung an. Kommas werden als Trennzeichen für den Namen verwendet.  Um ein Komma in einen Namen einzufügen, ersetzen Sie es durch ein Backslash-Zeichen (\).  Zum Beispiel *Adobe Systems\, Inc.*.

   `AppVersions` gibt die Version der Clientanwendung an.

   `Integrators` gibt den Namen des Unternehmens oder der Gruppe, die das Plug-In oder die integrierte Anwendung entwickelt hat, an.

   `IntegratorVersions` ist die Version des Plug-Ins oder der integrierten Anwendung.

1. Fügen Sie für jeden weiteren Satz von Verweigerungsdaten ein weiteres *MyEntryName*-Element hinzu.
1. Speichern Sie die Konfigurationsdatei.
1. Importieren Sie die Konfigurationsdatei.  (Siehe [Manuelles Bearbeiten der Konfigurationsdatei für die Dokumentensicherheit](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)

**Beispiele**

In diesem Beispiel wird allen Windows-Clients der Zugriff verweigert.

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

In diesem Beispiel wird für „Meine Anwendung Version 3.0“ und „Meine andere Anwendung Version 2.0“ der Zugriff verweigert.  Unabhängig vom Grund für die Verweigerung wird dieselbe URL für die Verweigerungsinformationen verwendet.

```xml
 <node name="ClientVersionRules">
     <map>
         <entry key="infoURL" value="https://get.a.new/version.html"/>
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

In diesem Beispiel werden alle Anforderungen von einer Microsoft PowerPoint 2007- oder Microsoft PowerPoint 2010-Installation von Acrobat Reader DC-Erweiterungen für Microsoft Office abgelehnt.

```xml
 <node name="ClientVersionRules">
     <map>
         <entry key="infoURL" value="https://get.a.new/version.html"/>
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

### Ändern der Parameter der Wasserzeichenkonfiguration {#change-the-watermark-configuration-parameters}

Standardmäßig können Sie in einem Wasserzeichen maximal fünf Elemente angeben.  Die maximale Dateigröße des PDF-Dokuments, das Sie als Wasserzeichen verwenden möchten, ist auf 100 KB beschränkt.  Sie können diese Parameter in der Datei config.xml ändern.

***Hinweis **: Sie sollten diese Parameter mit Vorsicht ändern.*

1. Exportieren Sie die Document Security-Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Konfigurationsdatei für die Dokumentensicherheit](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)
1. Öffnen Sie die Konfigurationsdatei in einem Editor und suchen Sie den Knoten `ServerSettings`.
1. Fügen Sie im Knoten `ServerSettings` die folgenden Einträge hinzu und speichern Sie anschließend die Datei: `<entry key="maximumSizeOfWatermarkElement" value="max filesize in KB"/> <entry key="maximumWatermarkElementsPerWatermark" value="max elements"/>`

   Der erste Eintrag *max file size* ist die Maximalgröße der Datei (in KB) für ein Wasserzeichenelement. Der Standardwert ist 100 KB.

   Der zweite Eintrag *max elements* ist die Maximalanzahl der für ein Wasserzeichen zulässigen Elemente. Der Standardwert ist 5.

   ```xml
   <entry key="maximumSizeOfWatermarkElement" value="max filesize in KB"/>
   <entry key="maximumWatermarkElementsPerWatermark" value="max elements"/>
   ```

1. Importieren Sie die Konfigurationsdatei.  (Siehe [Manuelles Bearbeiten der Konfigurationsdatei für die Dokumentensicherheit](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)

### Deaktivieren von externen Verknüpfungen {#disabling-external-links}

Viele Benutzende der Dokumentensicherheithaben keinen Zugriff auf externe Verknüpfungen wie **www.adobe.com**, wenn sie die Rights Management-Benutzeroberflächen verwenden:

* `https://[host]:'port'/adminui`
* `https://[host]:'port'/edc`.

Die folgenden Änderungen an der Datei „config.xml“ deaktivieren alle externen Verknüpfungen in den Rights Management-Benutzeroberflächen.

1. Exportieren Sie die Document Security-Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Konfigurationsdatei für die Dokumentensicherheit](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)
1. Öffnen Sie die Konfigurationsdatei in einem Editor und suchen Sie den Knoten `DisplaySettings`.
1. Um alle externen Verknüpfungen zu deaktivieren, fügen Sie im Knoten `DisplaySettings` den folgenden Eintrag hinzu und speichern Sie anschließend die Datei: `<entry key="ExternalLinksAllowed" value="false"/>`

   ```xml
   <entry key="ExternalLinksAllowed" value="false"/>
   ```

1. Importieren Sie die Konfigurationsdatei.  (Siehe [Manuelles Bearbeiten der Konfigurationsdatei für die Dokumentensicherheit](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)

### Konfiguration für die Aktivierung von SMTP für Transport Layer Security (TLS) {#configuration-to-enable-smtp-for-transport-layer-security-tls}

Die folgenden Änderungen in „config.xml“ ermöglichen die TLS-Unterstützung für die Funktion „Registrierung für eingeladene Benutzer“.

1. Exportieren Sie die Document Security-Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Konfigurationsdatei für die Dokumentensicherheit](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)
1. Öffnen Sie die Konfigurationsdatei in einem Editor und suchen Sie den Knoten `DisplaySettings`.
1. Suchen Sie den folgenden Knoten: `<node name="ExternalUser">`

   ```xml
   <node name="ExternalUser">
   ```

1. Legen Sie für den Schlüssel `SmtpUseTls` unter dem Knoten `ExternalUser` den Wert **true** fest.
1. Legen Sie für den Schlüssel `SmtpUseSsl` unter dem Knoten `ExternalUser` den Wert **false** fest.
1. Speichern Sie die `config.xml`.
1. Importieren Sie die Konfigurationsdatei.  (Siehe [Manuelles Bearbeiten der Konfigurationsdatei für die Dokumentensicherheit](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)

### Deaktivieren der SOAP-Endpunkte für Document Security-Dokumente {#disable-soap-endpoints-for-document-security-documents}

Nehmen Sie die folgenden Änderungen in „config.xml“ vor, um SOAP-Endpunkte für Document Security-Dokumente zu deaktivieren.

1. Exportieren Sie die Document Security-Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Konfigurationsdatei für die Dokumentensicherheit](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)
1. Öffnen Sie die Konfigurationsdatei in einem Editor und suchen Sie den folgenden Knoten: `<node name="DRM">`

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

1. Speichern Sie die `config.xml`.
1. Importieren Sie die Konfigurationsdatei.  (Siehe [Manuelles Bearbeiten der Konfigurationsdatei für die Dokumentensicherheit](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)

### Erhöhen der Skalierbarkeit des Dokumentensicherheits-Servers {#increasingscalability}

Standardmäßig rufen die Dokumentensicherheits-Clients beim Synchronisieren von Dokumenten für die Offline-Nutzung zusammen mit den Informationen zum aktuellen Dokument Richtlinien, Lizenzen, Wasserzeichen und aktuelle Sperrinformationen für alle anderen Dokumente ab, auf die die Person Zugriff hat. Wenn diese Aktualisierungen und Informationen nicht mit dem Client synchronisiert werden, kann sich ein Dokument, das im Offline-Modus geöffnet ist, trotzdem mit den älteren Richtlinien, Wasserzeichen und Sperrinformationen öffnen lassen.

Sie können die Skalierbarkeit des Dokumentensicherheits-Servers erhöhen, indem Sie die Informationen einschränken, die an den Client gesendet werden. Die Reduzierung der Datenmenge, die an den Client gesendet werden, führen zu höherer Skalierbarkeit, kürzeren Antwortzeiten und besserer Leistung des Servers. Führen Sie zur Verbesserung der Skalierbarkeit folgende Schritte aus:

1. Exportieren Sie die Document Security-Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Konfigurationsdatei für die Dokumentensicherheit](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)
1. Öffnen Sie die Konfigurationsdatei in einem Editor und suchen Sie den Knoten ServerSettings.
1. Legen Sie im Knoten „ServerSettings“ den Wert der Eigentschaft `DisableGlobalOfflineSynchronizationData` auf `true` fest.

   `<entry key="DisableGlobalOfflineSynchronizationData" value="true"/>`

   Bei dem Wert „true“ sendet der Document Security-Server Informationen nur für das aktuelle Dokument und Informationen für die übrigen Dokumente (die übrigen Dokumente, auf die ein Benutzer Zugriff hat) werden nicht an den Client gesendet.

   >[!NOTE]
   >
   >Standardmäßig wird der Wert des `DisableGlobalOfflineSynchronizationData`- -Schlüssels auf `false` festgelegt.

1. Speichern und schließen Sie die Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Konfigurationsdatei für die Dokumentensicherheit](/help/forms/using/admin-help/configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)
