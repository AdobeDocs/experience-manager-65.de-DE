---
title: Konfigurieren der Client- und Server-Optionen
description: Erfahren Sie, wie Sie die verschiedenen Client- und Serveroptionen konfigurieren können, z. B. Serverkonfigurationseinstellungen, Document Security-Rollen und Ereignisprüfungen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Document Security
exl-id: fe132f13-5f9a-4c86-a385-0a0026c812e2
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '10229'
ht-degree: 27%

---

# Document Security-Server konfigurieren {#configure-the-document-security-server}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Document Security&quot;> &quot;Konfiguration&quot;> &quot;Serverkonfiguration&quot;.
1. Konfigurieren Sie die Einstellungen und klicken Sie auf &quot;OK&quot;.

## Serverkonfigurationseinstellungen {#server-configuration-settings}

**Basis-URL:** Die Document Security-Basis-URL, die den Servernamen und Port enthält. Durch Anfügen von Informationen an die Basis-URL werden Verbindungs-URLs erstellt. /edc/Main.do wird beispielsweise angefügt, um auf die Webseiten zuzugreifen. Diese URL ermöglicht Benutzern auch, auf Einladungen externer Benutzer zur Registrierung zu antworten.

Wenn Sie IPv6 verwenden, geben Sie die Basis-URL als Computernamen oder den DNS-Namen ein. Wenn Sie eine numerische IP-Adresse verwenden, kann Acrobat keine richtliniengeschützten Dateien öffnen. Verwenden Sie außerdem die sichere HTTP-URL (HTTPS) für Ihren Server.

>[!NOTE]
>
>Die Basis-URL ist in richtliniengeschützte Dateien eingebettet. Clientanwendungen verwenden die Basis-URL, um eine Verbindung zum Server herzustellen. Geschützte Dateien enthalten weiterhin die Basis-URL, auch wenn sie später geändert werden. Wenn Sie die Basis-URL ändern, müssen die Konfigurationsinformationen für alle Verbindungs-Clients aktualisiert werden.

**Standardmäßiger Offline-Lease-Zeitraum:** Der standardmäßige Zeitraum, den ein Benutzer ein geschütztes Dokument offline nutzen darf. Diese Einstellung bestimmt den ursprünglichen Wert der Einstellung für die Automatische Offline-Nutzungsdauer, wenn Sie eine Richtlinie erstellen. (Siehe Richtlinien erstellen und bearbeiten.) Nach Ablauf der Nutzungsdauer muss der Empfänger das Dokument erneut synchronisieren, um es weiter verwenden zu können.

Weitere Informationen zur Funktionsweise der Offline-Nutzung und Synchronisation finden Sie unter [Primer zum Konfigurieren der Offline-Nutzung und Synchronisation](https://blogs.adobe.com/security/2009/05/primer_on_configuring_offline.html).

**Standardmäßiger Offline-Synchronisierungs-Zeitraum:** Die maximale Zeit, die ein beliebiges Dokument offline verwendet werden kann, wenn es anfänglich geschützt ist.

**Client-Sitzungs-Timeout:** Der Zeitraum in Minuten, nach dem Document Security die Verbindung trennt, wenn ein über eine Clientanwendung angemeldeter Benutzer Document Security nicht verwendet.

**Anonymen Benutzerzugriff gestatten:** Aktivieren Sie diese Option, um das Erstellen von freigegebenen und persönlichen Richtlinien, die anonymen Benutzern das Öffnen richtliniengeschützter Dokumente erlauben, zuzulassen. (Benutzer ohne Konto können auf das Dokument zugreifen, sich jedoch nicht bei Document Security anmelden oder andere richtliniengeschützte Dokumente nutzen.)

**Zugriff auf Version 7-Clients deaktivieren:** Gibt an, ob Benutzer Acrobat oder Reader 7.0 verwenden können, um eine Verbindung zum Server herzustellen. Wenn diese Option aktiviert ist, müssen Benutzer Acrobat oder Reader 8.0 und höher verwenden, um Document Security-Vorgänge auf PDF-Dokumenten abzuschließen. Wenn Richtlinien erfordern, dass Acrobat oder Reader 8.0 und höher beim Öffnen richtliniengeschützter Dokumente im zertifizierten Modus ausgeführt werden müssen, sollten Sie den Zugriff auf Acrobat oder Reader 7 deaktivieren. (Siehe Die Dokumentberechtigungen für Benutzer und Gruppen angeben.)

**Offline-Zugriff pro Dokument zulassen** Wählen Sie diese Option, um den Offline-Zugriff pro Dokument anzugeben. Wenn diese Einstellung aktiviert ist, kann der Benutzer nur auf die Dokumente offline zugreifen, die er mindestens einmal online geöffnet hat.

**Benutzername-/Kennwort-Authentifizierung gestatten:** Aktivieren Sie diese Option, um zu bestimmen, ob Clientanwendungen beim Herstellen einer Serververbindung die Benutzername/Kennwort-Authentifizierung zulassen.

**Kerberos-Authentifizierung gestatten:** Aktivieren Sie diese Option, um zu bestimmen, ob Clientanwendungen beim Herstellen einer Serververbindung die Kerberos-Authentifizierung zulassen.

**Client-Zertifikat-Authentifizierung gestatten:** Aktivieren Sie diese Option, um zu bestimmen, ob Clientanwendungen beim Herstellen einer Serververbindung die Zertifikat-Authentifizierung zulassen.

**Erweiterte Authentifizierung gestatten** Wählen Sie diese Option, um erweiterte Authentifizierung zu aktivieren, und geben Sie dann die Startseiten-URL für die erweiterte Authentifizierung ein.

Wenn Sie diese Option auswählen, können Clientanwendungen erweiterte Authentifizierung verwenden. Die erweiterte Authentifizierung bietet benutzerdefinierte Authentifizierungsprozesse und verschiedene Authentifizierungsoptionen, die auf dem AEM forms-Server konfiguriert sind. Beispielsweise können Benutzer jetzt die SAML-basierte Authentifizierung anstelle von Benutzername/Kennwort für AEM Formulare von Acrobat und Reader Client aus erleben. Standardmäßig enthält die Landingpage-URL *localhost* als Servernamen. Ersetzen Sie den Servernamen durch einen vollständig qualifizierten Hostnamen. Der Hostname in der Landingpage-URL wird automatisch aus der Basis-URL gefüllt, wenn die erweiterte Authentifizierung noch nicht aktiviert ist. Siehe [Erweiterten Authentifizierungsanbieter hinzufügen](configuring-client-server-options.md#add-the-extended-authentication-provider).

***Hinweis **: Erweiterte Authentifizierung wird auf Apple Mac OS X mit Adobe Acrobat ab Version 11.0.6 unterstützt.*

**Bevorzugte HTML-Kontrollbreite für erweiterte Authentifizierung** Geben Sie die Breite des Dialogfelds für erweiterte Authentifizierung an, das in Acrobat zur Eingabe von Benutzeranmeldeinformationen geöffnet wird.

**Bevorzugte HTML-Steuerelementhöhe für erweiterte Authentifizierung** Geben Sie die Höhe des Dialogfelds für die erweiterte Authentifizierung an, das in Acrobat zur Eingabe von Benutzeranmeldeinformationen geöffnet wird.

***Hinweis **: Die Grenzen der Breite und Höhe für dieses Dialogfeld sind wie folgt:*

Breite: Minimum = 400, Maximum = 900

Höhe: Minimum = 450; Maximum = 800

**Zwischenspeichern von Client-Anmeldeinformationen gestatten:** Wählen Sie diese Option aus, um Benutzern zu erlauben, ihre Anmeldeinformationen (Benutzernamen und Kennwort) zwischenzuspeichern. Wenn die Anmeldeinformationen von Benutzern zwischengespeichert werden, müssen sie ihre Anmeldeinformationen nicht jedes Mal eingeben, wenn sie ein Dokument öffnen, oder wenn sie in Adobe Acrobat auf der Seite &quot;Sicherheitsrichtlinien verwalten&quot;auf die Schaltfläche &quot;Aktualisieren&quot;klicken. Sie können die Anzahl der Tage angeben, bevor Benutzer ihre Anmeldeinformationen erneut angeben müssen. Wenn Sie die Anzahl der Tage auf 0 festlegen, können Anmeldeinformationen unbegrenzt zwischengespeichert werden.

## Document Security-Benutzer und -Administratoren konfigurieren {#configuring-document-security-users-and-administrators}

### Zuweisen von Document Security-Rollen zu Administratoren {#assigning-document-security-roles-to-administrators}

Ihre AEM Forms-Umgebung enthält einen oder mehrere Administratorbenutzer, die über die entsprechenden Berechtigungen zum Erstellen von Benutzern und Gruppen verfügen. Wenn Ihr Unternehmen Document Security verwendet, muss mindestens einem Administrator auch die Berechtigung zum Verwalten eingeladener und lokaler Benutzer zugewiesen werden.

Administratoren müssen außerdem über die Rolle &quot;Administration Console-Benutzer&quot;verfügen, um auf Administration Console zugreifen zu können. (Siehe [Rollen erstellen und konfigurieren](/help/forms/using/admin-help/creating-configuring-roles.md#creating-and-configuring-roles).

### Sichtbare Benutzer und Gruppen konfigurieren {#configuring-visible-users-and-groups}

Um bei Suchen anhand von Benutzerrichtlinien Benutzer und Gruppen in ausgewählten Domains anzuzeigen, muss ein Superadministrator oder Richtliniensatzadministrator (in User Management erstellte) Domains auswählen und der Liste der sichtbaren Benutzer und Gruppen für jeden Richtliniensatz hinzufügen.

Diese Liste wird dem Richtliniensatzkoordinator angezeigt und dient zum Einschränken der Domains, die der Endbenutzer beim Auswählen von Benutzern oder Gruppen durchsuchen kann, die Richtlinien hinzugefügt werden sollen. Wenn diese Aufgabe nicht ausgeführt wird, findet der Richtliniensatzkoordinator keine Benutzer oder Gruppen, die der Richtlinie hinzugefügt werden sollen. Für jeden Richtliniensatz kann es mehr als einen Richtliniensatzkoordinator geben.

1. Richten Sie nach der Installation und Konfiguration der AEM Forms-Umgebung mit Document Security alle gewünschten Domains in User Management ein. <!-- Fix broken link (See Setting up and managing domains) -->

   ***Hinweis **: Das Erstellen von Domains muss vor dem Erstellen von Richtlinien erfolgen.*

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Document Management&quot;> &quot;Richtlinien&quot;und dann auf die Registerkarte &quot;Richtliniensätze&quot;.
1. Wählen Sie den globalen Richtliniensatz aus und klicken Sie dann auf die Registerkarte &quot;Sichtbare Benutzer und Gruppen&quot;.
1. Klicken Sie auf „Domain(s) hinzufügen“ und fügen Sie den Anforderungen entsprechend vorhandene Domains hinzu.
1. Navigieren Sie zu Dienste > Document Security > Konfiguration > Meine Richtlinien und klicken Sie auf die Registerkarte Sichtbare Benutzer und Gruppen .
1. Klicken Sie auf „Domain(s) hinzufügen“ und fügen Sie den Anforderungen entsprechend vorhandene Domains hinzu.

## Erweiterten Authentifizierungsanbieter hinzufügen {#add-the-extended-authentication-provider}

AEM Forms bietet eine Beispielkonfiguration, die Sie für Ihre Umgebung anpassen können. Führen Sie die folgenden Schritte durch:

>[!NOTE]
>
>Erweiterte Authentifizierung wird unter Apple Mac OS X mit Adobe Acrobat-Version 11.0.6 und höher unterstützt.

1. Rufen Sie die WAR-Beispieldatei ab, um sie bereitzustellen. Weitere Informationen finden Sie im entsprechenden Installationshandbuch für Ihren Anwendungsserver.
1. Stellen Sie sicher, dass der Formularserver einen vollständig qualifizierten Namen anstelle von IP-Adressen als Basis-URL hat und dass es sich um eine HTTPS-URL handelt. Siehe [Serverkonfigurationseinstellungen](configuring-client-server-options.md#server-configuration-settings).
1. Aktivieren Sie auf der Seite &quot;Serverkonfiguration&quot;die erweiterte Authentifizierung. Siehe [Serverkonfigurationseinstellungen](configuring-client-server-options.md#server-configuration-settings).
1. Fügen Sie die erforderlichen SSO-Umleitungs-URLs in die User Management-Konfigurationsdatei ein. Siehe [SSO-Umleitungs-URLs für erweiterte Authentifizierung hinzufügen](configuring-client-server-options.md#add-sso-redirect-urls-for-extended-authentication).

### SSO-Umleitungs-URLs für erweiterte Authentifizierung hinzufügen {#add-sso-redirect-urls-for-extended-authentication}

Wenn die erweiterte Authentifizierung aktiviert ist, erhalten Benutzer, die ein richtliniengeschütztes Dokument in Acrobat XI oder Reader XI öffnen, ein Dialogfeld zur Authentifizierung. Dieses Dialogfeld lädt die HTML-Seite, die Sie als Landingpage für die erweiterte Authentifizierung in den Document Security-Servereinstellungen angegeben haben. Siehe [Serverkonfigurationseinstellungen](configuring-client-server-options.md#server-configuration-settings).

>[!NOTE]
>
>Erweiterte Authentifizierung wird unter Apple Mac OS X mit Adobe Acrobat-Version 11.0.6 und höher unterstützt.

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Konfiguration“ > „Konfigurationsdateien importieren und exportieren“.
1. Klicken Sie auf Exportieren und speichern Sie die Konfigurationsdatei auf Ihrer Festplatte.
1. Öffnen Sie die Datei in einem Editor und suchen Sie den Knoten AllowedUrls .
1. Fügen Sie im `AllowedUrls`-Knoten die folgenden Zeilen hinzu: `<entry key="sso-l" value="/ssoexample/login.jsp"/> <entry key="sso-s" value="/ssoexample"/> <entry key="sso-o" value="/ssoexample/logout.jsp"/>`

   ```xml
   <entry key="sso-l" value="/ssoexample/login.jsp"/>
   <entry key="sso-s" value="/ssoexample"/>
   <entry key="sso-o" value="/ssoexample/logout.jsp"/>
   ```

1. Speichern Sie die Datei und importieren Sie anschließend die aktualisierte Datei von der Seite „Manuelle Konfiguration“: Klicken Sie in der Administration-Console auf „Einstellungen“ > „User Management“ > „Konfiguration“ > „Konfigurationsdateien im- und exportieren“.

## Offline-Sicherheit konfigurieren {#configuring-offline-security}

Document Security bietet die Möglichkeit, richtliniengeschützte Dokumente offline ohne Internet- oder Netzwerkverbindung zu verwenden. Für diese Möglichkeit muss die Richtlinie den Offline-Zugriff zulassen, wie unter [Dokumentberechtigungen für Benutzer und Gruppen angeben](/help/forms/using/admin-help/creating-policies.md#specify-the-document-permissions-for-users-and-groups). Bevor ein Dokument mit einer solchen Richtlinie offline verwendet werden kann, muss der Empfänger das Dokument online öffnen und den Offline-Zugriff aktivieren, indem er bei Aufforderung auf Ja klickt. Der Empfänger kann auch aufgefordert werden, seine Identität zu authentifizieren. Der Empfänger kann dann Dokumente offline für die in der Richtlinie angegebene Offline-Nutzungsdauer verwenden.

Wenn die Offline-Nutzungsdauer endet, muss der Empfänger die Synchronisierung erneut mit Document Security synchronisieren, indem er entweder ein Dokument online öffnet oder einen Menübefehl für Acrobat- oder Acrobat Reader DC-Erweiterungen verwendet, um es zu synchronisieren. (Siehe *Hilfe zu Acrobat* oder *Hilfe zu Acrobat Reader DC-Erweiterungen*.

Da Dokumente, die den Offline-Zugriff zulassen, die Zwischenspeicherung von Schlüsselmaterial auf dem Computer erfordern, auf dem die Dateien offline gespeichert werden, kann die Datei möglicherweise beeinträchtigt werden, wenn ein nicht autorisierter Benutzer das Schlüsselmaterial abrufen kann. Um diese Möglichkeit auszugleichen, werden geplante und manuelle Schlüsselaktualisierungsoptionen bereitgestellt, die Sie konfigurieren können, um zu verhindern, dass eine nicht autorisierte Person den Schlüssel für den Zugriff auf das Dokument verwendet.

### Standardmäßige Offline-Nutzungsdauer festlegen {#set-a-default-offline-lease-period}

Empfänger richtliniengeschützter Dokumente können die Dokumente für die in der Richtlinie angegebene Anzahl von Tagen offline schalten. Nach der anfänglichen Synchronisierung des Dokuments mit Document Security kann der Empfänger es bis zum Ablauf der Offline-Nutzungsdauer offline verwenden. Nach Ablauf der Nutzungsdauer muss sich der Empfänger mit dem Dokument online anmelden und sich zur Synchronisierung mit Document Security anmelden, um das Dokument weiterhin verwenden zu können.

Sie können eine standardmäßige Offline-Nutzungsdauer konfigurieren. Die Nutzungsdauer kann von der Standardeinstellung geändert werden, wenn eine Richtlinie von einem Benutzer erstellt oder bearbeitet wird.

1. Klicken Sie auf der Document Security-Seite auf Konfiguration > Serverkonfiguration.
1. Geben Sie in das Feld &quot;Standardmäßige Offline-Nutzungsdauer&quot;die Anzahl der Tage für die Offline-Nutzungsdauer ein.
1. Klicken Sie auf OK.

### Verwalten von Schlüsselaktualisierungen {#manage-key-rollovers}

Document Security verwendet zum Schutz von Dokumenten Verschlüsselungsalgorithmen und Lizenzen. Beim Verschlüsseln eines Dokuments generiert und verwaltet Document Security einen Entschlüsselungsschlüssel, der als *DocKey* , dass sie an die Client-Anwendung übergeben wird. Wenn die Richtlinie, die ein Dokument schützt, den Offline-Zugriff zulässt, wird ein Offline-Schlüssel namens *Printschlüssel* wird auch für jeden Benutzer generiert, der Offline-Zugriff auf das Dokument hat.

>[!NOTE]
>
>Wenn kein Hauptschlüssel vorhanden ist, generiert Document Security einen zum Schützen eines Dokuments.

Um ein richtliniengeschütztes Dokument offline zu öffnen, muss der Computer des Benutzers über den entsprechenden Hauptschlüssel verfügen. Der Computer erhält den Hauptschlüssel, wenn der Benutzer eine Synchronisierung mit Document Security durchführt (ein geschütztes Dokument online öffnet). Wenn dieser Hauptschlüssel kompromittiert ist, kann auch jedes Dokument beeinträchtigt werden, auf das der Benutzer Offline-Zugriff hat.

Eine Möglichkeit, die Bedrohung für Offline-Dokumente zu verringern, besteht darin, zu verhindern, dass der Offline-Zugriff auf besonders vertrauliche Dokumente ermöglicht wird. Eine andere Methode besteht darin, die Hauptschlüssel regelmäßig zu aktualisieren. Wenn Document Security den Schlüssel umsetzt, können vorhandene Schlüssel nicht mehr auf die richtliniengeschützten Dokumente zugreifen. Wenn beispielsweise ein Täter einen Hauptschlüssel von einem gestohlenen Laptop erhält, kann dieser Schlüssel nicht für den Zugriff auf die Dokumente verwendet werden, die nach dem Rollover geschützt sind. Wenn Sie vermuten, dass ein bestimmter Hauptschlüssel beschädigt wurde, können Sie den Schlüssel manuell aktualisieren.

Beachten Sie jedoch auch, dass ein Schlüsselaktualisierung alle Hauptschlüssel betrifft, nicht nur einen. Außerdem wird die Skalierbarkeit des Systems verringert, da Clients mehr Schlüssel für den Offline-Zugriff speichern müssen. Die standardmäßige Schlüsselaktualisierungshäufigkeit beträgt 20 Tage. Es wird empfohlen, diesen Wert nicht auf weniger als 14 Tage festzulegen, da Personen möglicherweise daran gehindert werden, Offline-Dokumente anzuzeigen, und die Systemleistung möglicherweise beeinträchtigt ist.

Im folgenden Beispiel ist Schlüssel1 der ältere der beiden Hauptschlüssel und Schlüssel2 der neuere. Wenn Sie das erste Mal auf die Schaltfläche &quot;Schlüssel jetzt aktualisieren&quot;klicken, wird Schlüssel1 ungültig und ein neuer, gültiger Hauptschlüssel (Schlüssel3) wird generiert. Benutzer erhalten Schlüssel3, wenn sie mit Document Security synchronisieren, in der Regel durch Öffnen eines geschützten Dokuments online. Benutzer müssen jedoch erst mit Document Security synchronisieren, wenn sie die in einer Richtlinie angegebene maximale Offline-Nutzungsdauer erreicht haben. Nach der ersten Schlüsselaktualisierung können Benutzer, die offline bleiben, weiterhin Offline-Dokumente öffnen, einschließlich der durch Schlüssel3 geschützten Dokumente, bis sie die maximale Offline-Nutzungsdauer erreichen. Wenn Sie ein zweites Mal auf die Schaltfläche &quot;Schlüssel jetzt aktualisieren&quot;klicken, wird Schlüssel2 ungültig und Schlüssel4 wird erstellt. Benutzer, die während der beiden Schlüsselaktualisierungen offline sind, können mit Schlüssel3 oder Schlüssel4 geschützte Dokumente erst öffnen, wenn sie mit Document Security synchronisiert werden.

**Schlüsselaktualisierung ändern**

Aus Gründen der Vertraulichkeit bietet Document Security bei der Verwendung von Offline-Dokumenten eine automatische Schlüsselaktualisierungsoption mit einem standardmäßigen Zeitintervall von 20 Tagen. Sie können die Rollover-Häufigkeit ändern. Vermeiden Sie jedoch, den Wert auf unter 14 Tage festzulegen, da Personen möglicherweise daran gehindert werden, Offline-Dokumente anzuzeigen, und die Systemleistung möglicherweise beeinträchtigt ist.

1. Klicken Sie auf der Document Security-Seite auf Konfiguration > Schlüsselverwaltung.
1. Geben Sie in das Feld &quot;Zeitintervall für Schlüsselaktualisierung&quot;die Anzahl der Tage für den Rollover-Zeitraum ein.
1. Klicken Sie auf OK.

**Hauptschlüssel manuell aktualisieren**

Um die Vertraulichkeit von Offline-Dokumenten zu wahren, können Sie die Hauptschlüssel manuell aktualisieren. Es kann erforderlich sein, einen Schlüssel manuell zu aktualisieren (z. B. wenn der Schlüssel von einem Computer kompromittiert wird, auf dem er zwischengespeichert ist, um den Offline-Zugriff auf ein Dokument zu ermöglichen).

>[!NOTE]
>
>Vermeiden Sie häufig manuelles Rollover, da dadurch alle Hauptschlüssel aktualisiert werden, nicht nur einer, und Benutzer vorübergehend daran gehindert werden können, neue Dokumente offline anzuzeigen.

Die Hauptschlüssel müssen zweimal aktualisiert werden, bevor zuvor vorhandene Schlüssel auf Clientcomputern ungültig gemacht werden. Clientcomputer, die über ungültige Hauptschlüssel verfügen, müssen mit dem Document Security-Dienst neu synchronisieren, um die neuen Hauptschlüssel zu erhalten.

1. Klicken Sie auf der Document Security-Seite auf Konfiguration > Schlüsselverwaltung.
1. Klicken Sie auf Schlüssel jetzt aktualisieren und dann auf OK .
1. Warten Sie ungefähr 10 Minuten. Im Serverprotokoll wird die folgende Protokoll-Meldung angezeigt: `Done RightsManagement key rollover for`*N* `principals`. Wo *N* ist die Anzahl der Benutzer im Document Security-System.
1. Klicken Sie auf Schlüssel jetzt aktualisieren und dann auf OK .
1. Warten Sie ungefähr 10 Minuten.

## Ereignisprüfungs- und Datenschutzeinstellungen konfigurieren {#configuring-event-auditing-and-privacy-settings}

Document Security kann Informationen zu Ereignissen im Zusammenhang mit der Interaktion mit richtliniengeschützten Dokumenten, Richtlinien, Administratoren und dem Server prüfen und aufzeichnen. Sie können die Ereignisprüfung konfigurieren und die zu prüfenden Ereignistypen angeben. Um Ereignisse für ein bestimmtes Dokument zu prüfen, muss auch die Prüfoption für die Richtlinie aktiviert sein.

Wenn die Prüfung aktiviert ist, können Sie auf der Seite &quot;Ereignisse&quot;Details zu den geprüften Ereignissen anzeigen. Document Security-Benutzer können auch Ereignisse anzeigen, die sich speziell auf die von ihnen verwendeten oder erstellten richtliniengeschützten Dokumente beziehen.

Sie können die folgenden Ereignistypen für die Prüfung auswählen:

* Richtliniengeschützte Dokumentereignisse, beispielsweise Versuche autorisierter oder nicht autorisierter Benutzer, Dokumente zu öffnen
* Richtlinienereignisse wie das Erstellen, Ändern, Löschen, Aktivieren und Deaktivieren von Richtlinien
* Benutzerereignisse wie Einladungen und Registrierungen externer Benutzer, aktivierte und deaktivierte Benutzerkonten, Änderungen an Benutzerkennwörtern und Profilaktualisierungen
* AEM Forms-Ereignisse, z. B. nicht verfügbare Ordnerserver- und Autorisierungsanbieter sowie Serverkonfigurationsänderungen

### Ereignisprüfung aktivieren oder deaktivieren {#enable-or-disable-event-auditing}

Sie können die Prüfung von Ereignissen im Zusammenhang mit dem Server, richtliniengeschützten Dokumenten, Richtlinien, Richtliniensätzen und Benutzern aktivieren und deaktivieren. Wenn Sie die Ereignisprüfung aktivieren, können Sie alle möglichen Ereignisse prüfen oder bestimmte Ereignisse auswählen, die geprüft werden sollen.

Wenn Sie die Serverprüfung aktivieren, können Sie die geprüften Ereignisse auf der Seite &quot;Ereignisse&quot;anzeigen.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Document Security&quot;> &quot;Konfiguration&quot;> &quot;Audit and Privacy Settings&quot;.
1. Um die Serverprüfung zu konfigurieren, wählen Sie unter &quot;Serverprüfung aktivieren&quot;die Option &quot;Ja&quot;oder &quot;Nein&quot;aus.
1. Wenn Sie unter jeder Ereigniskategorie &quot;Ja&quot;ausgewählt haben, führen Sie einen der folgenden Schritte aus, um die zu prüfenden Optionen auszuwählen:

   * Um alle Ereignisse in der Kategorie zu prüfen, wählen Sie Alle aus.
   * Um nur bestimmte Ereignisse zu prüfen, deaktivieren Sie &quot;Alle&quot;und aktivieren Sie dann die Kontrollkästchen neben den Ereignissen, die Sie prüfen möchten.

     (Siehe [Ereignisprüfungsoptionen](configuring-client-server-options.md#event-auditing-options).

1. Klicken Sie auf OK.

>[!NOTE]
>
>Vermeiden Sie beim Arbeiten mit Webseiten die Verwendung von Browser-Schaltflächen wie der Zurück-, der Aktualisierungs- und der Zurück- oder der Vorwärts-Taste, da diese Aktion zu unerwünschten Problemen bei der Datenerfassung und Datenanzeige führen kann.

### Datenschutzbenachrichtigung aktivieren oder deaktivieren {#enable-or-disable-privacy-notification}

Sie können eine Datenschutzbenachrichtigung aktivieren und deaktivieren. Wenn Sie die Datenschutzbenachrichtigung aktivieren, wird eine Meldung angezeigt, wenn ein Empfänger versucht, ein richtliniengeschütztes Dokument zu öffnen. Der Hinweis informiert den Benutzer darüber, dass die Dokumentnutzung geprüft wird. Sie können auch eine URL angeben, die der Benutzer verwenden kann, um Ihre Seite mit den Datenschutzrichtlinien anzuzeigen, sofern eine verfügbar ist.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Document Security&quot;> &quot;Konfiguration&quot;> &quot;Audit and Privacy Settings&quot;.
1. Um die Datenschutzbenachrichtigung zu konfigurieren, wählen Sie unter Datenschutzbestimmung aktivieren die Option Ja oder Nein aus.

   Wenn die an ein Dokument angehängte Richtlinie den anonymen Benutzerzugriff zulässt und &quot;Datenschutzbestimmung aktivieren&quot;auf &quot;Nein&quot;gesetzt ist, wird der Benutzer nicht aufgefordert, sich anzumelden, und die Datenschutzbenachrichtigung wird nicht angezeigt.

   Wenn die an ein Dokument angehängte Richtlinie keinen anonymen Benutzerzugriff zulässt, wird dem Benutzer die Datenschutzbenachrichtigung angezeigt.

1. Falls zutreffend, geben Sie in das Feld &quot;Datenschutz-URL&quot;die URL zu Ihrer Datenschutzrichtlinien-Seite ein. Wenn das Feld Datenschutz-URL leer gelassen wird, wird die Datenschutzseite von adobe.com angezeigt.
1. Klicken Sie auf OK.

>[!NOTE]
>
>Wenn Sie die Datenschutzhinweise deaktivieren, wird nicht gleichzeitig die Prüfung von Dokumentverwendung deaktiviert. Vordefinierte Prüfaktionen und benutzerdefinierte Aktionen, die über erweitertes Nutzungsverfolgung unterstützt werden, können weiterhin Informationen zum Benutzerverhalten erfassen.

### Benutzerdefinierten Prüfereignistyp importieren {#import-a-custom-audit-event-type}

Wenn Sie eine Document Security-aktivierte Anwendung verwenden, die die Prüfung zusätzlicher Ereignisse unterstützt, z. B. von für einen bestimmten Dateityp spezifischen Ereignissen, kann Ihnen ein Adobe-Partner benutzerdefinierte Prüfereignisse bereitstellen, die Sie in Document Security importieren können. Verwenden Sie diese Funktion nur, wenn Sie von einem Adobe-Partner über benutzerdefinierte Ereignistypen verfügen.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Document Security&quot;> &quot;Konfiguration&quot;> &quot;Ereignisverwaltung&quot;.
1. Klicken Sie auf Durchsuchen , um zur zu importierenden XML-Datei zu gelangen, und klicken Sie auf Importieren.
1. Beim Import werden vorhandene benutzerdefinierte Prüfereignistypen auf dem Server überschrieben, wenn identische Ereigniscode- und Namespace-Kombinationen gefunden werden.
1. Klicken Sie auf OK.

### Löschen eines benutzerdefinierten Prüfereignistyps {#delete-a-custom-audit-event-type}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Document Security&quot;> &quot;Konfiguration&quot;> &quot;Ereignisverwaltung&quot;.
1. Aktivieren Sie das Kontrollkästchen neben dem benutzerdefinierten Prüfereignistyp, den Sie löschen möchten, und klicken Sie auf &quot;Löschen&quot;.
1. Klicken Sie auf OK.

### Exportieren von Prüfereignissen {#export-audit-events}

Sie können Prüfereignisse zu Archivierungszwecken in eine Datei exportieren.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Document Security&quot;> &quot;Konfiguration&quot;> &quot;Ereignisverwaltung&quot;.
1. Bearbeiten Sie die Einstellungen unter &quot;Prüfereignisse exportieren&quot;nach Bedarf. Sie können Folgendes angeben:

   * das Mindestalter der zu exportierenden Prüfereignisse
   * die maximale Anzahl von Prüfereignissen, die in eine Datei aufgenommen werden sollen. Der Server generiert eine oder mehrere Dateien, die auf diesem Wert basieren.
   * den Ordner, in dem die Datei erstellt wird. Dieser Ordner befindet sich auf dem Formularserver. Wenn der Ordnerpfad relativ ist, ist er relativ zum Stammordner des Anwendungsservers.
   * das Dateipräfix, das für die Prüfereignisdateien verwendet werden soll
   * das Dateiformat, entweder eine CSV-Datei (kommagetrennte Werte), die mit Microsoft Excel kompatibel ist, oder eine XML-Datei.

1. Klicken Sie auf Exportieren. Wenn Sie den Export abbrechen möchten, klicken Sie auf Export abbrechen . Wenn ein anderer Benutzer einen Export geplant hat, ist die Schaltfläche Export abbrechen nicht verfügbar, bis der Export abgeschlossen ist. Die Schaltfläche Export abbrechen ist nicht verfügbar, wenn ein anderer Benutzer einen Export geplant hat. Um zu überprüfen, ob ein geplanter Export- oder Löschvorgang gestartet oder beendet wurde, klicken Sie auf Aktualisieren .

### Löschen von Prüfereignissen {#delete-audit-events}

Sie können Prüfereignisse löschen, die älter als eine bestimmte Anzahl von Tagen sind.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Document Security&quot;> &quot;Konfiguration&quot;> &quot;Ereignisverwaltung&quot;.
1. Geben Sie unter &quot;Audit-Ereignisse löschen&quot;die Anzahl der Tage im Feld &quot;Audit-Ereignisse löschen, die älter sind als&quot;an.
1. Klicken Sie auf Löschen. Klicken Sie auf Exportieren. Wenn Sie den Löschvorgang abbrechen möchten, klicken Sie auf &quot;Löschvorgang abbrechen&quot;. Wenn ein anderer Benutzer einen Löschvorgang geplant hat, ist die Schaltfläche Löschvorgang abbrechen nicht verfügbar, bis der Export abgeschlossen ist. Die Schaltfläche Löschen abbrechen ist nicht verfügbar, wenn ein anderer Benutzer einen Export geplant hat. Um zu überprüfen, ob ein geplanter Löschvorgang gestartet oder beendet wurde, klicken Sie auf Aktualisieren .

### Ereignisprüfungsoptionen {#event-auditing-options}

Sie können die Ereignisprüfung aktivieren und deaktivieren und die zu prüfenden Ereignistypen angeben.

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

**URL für Dokumentsperrung ändern:** Ein Aufruf auf API-Ebene ändert die Sperrungs-URL, die für den Zugriff auf ein neues Dokument angegeben ist, das ein gesperrtes Dokument ersetzt.

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

**Client aktiviert Offline-Zugriff:** Ein Benutzer hat den Offline-Zugriff auf Dokumente aktiviert, die auf dem Computer des Benutzers gegen den Server gesichert sind.

**Synchronisierte Clientanwendung** Die Clientanwendung muss Informationen mit dem Server synchronisieren, um den Offline-Zugriff zuzulassen.

**Inkompatible Version:** Eine Version des AEM Forms-SDK, die nicht mit dem Server kompatibel ist, versuchte, eine Verbindung mit dem Server herzustellen.

**Informationen zur Ordnersynchronisierung:** Diese Informationen sind nicht auf der Seite Ereignisse verfügbar. Die aktuellen Informationen zur Ordnersynchronisierung, einschließlich des aktuellen Synchronisierungszustands und des Zeitpunktes der letzten Synchronisierung, werden auf der Seite „Domain-Verwaltung“ angezeigt. Um Zugriff auf die Domain-Verwaltung zu erhalten, klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.

**Änderungen an der Serverkonfiguration:** Änderungen an der Serverkonfiguration, die entweder über die Webseiten oder manuell durch Importieren einer „config.xml“-Datei erfolgen. Dazu gehören Änderungen an der Basis-URL, Sitzungszeitüberschreitungen, Anmeldeausfällen, Ordnereinstellungen, Schlüsselaktualisierungen, SMTP-Servereinstellungen für die externe Registrierung, Wasserzeichenkonfiguration, Anzeigeoptionen usw.

## Erweiterte Nutzungsverfolgung konfigurieren {#configuring-extended-usage-tracking}

Document Security kann verschiedene benutzerdefinierte Ereignisse verfolgen, die möglicherweise für ein geschütztes Dokument ausgeführt werden. Sie können die Verfolgung von Ereignissen vom Document Security-Server auf globaler Ebene oder auf Richtlinienebene aktivieren. Sie können dann ein JavaScript einrichten, um bestimmte Aktionen zu erfassen, die innerhalb des geschützten PDF-Dokuments ausgeführt werden, z. B. das Klicken auf eine Schaltfläche oder Speichern des Dokuments. Diese Nutzungsdaten werden als XML-Datei in Schlüssel-Wert-Paaren gesendet, die Sie für die weitere Analyse verwenden können. Endbenutzer, die auf die geschützten Dokumente zugreifen, können diese Verfolgung über die Clientanwendung zulassen oder ablehnen.

Wenn das Tracking auf globaler Ebene aktiviert ist, können Sie diese Einstellung auf Richtlinienebene überschreiben und sie für eine bestimmte Richtlinie deaktivieren. Das Überschreiben auf Richtlinienebene ist nicht möglich, wenn das Tracking auf globaler Ebene deaktiviert ist. Die Liste der getrackten Ereignisse wird automatisch an den Server gesendet, wenn die Ereignisanzahl 25 erreicht oder das Dokument geschlossen wird. Sie können Ihr Skript auch so konfigurieren, dass die Ereignisliste entsprechend Ihren Anforderungen explizit gepusht wird. Sie können die Ereignisverfolgung anpassen, indem Sie auf die Objekteigenschaften und -methoden von Document Security zugreifen.

Nachdem Sie die Verfolgung aktiviert haben, ist die Verfolgung für alle Richtlinien, die anschließend erstellt werden, standardmäßig aktiviert. Richtlinien, die erstellt wurden, bevor das Tracking auf dem Server aktiviert wurde, müssen manuell aktualisiert werden.

### Erweiterte Nutzungsverfolgung aktivieren oder deaktivieren {#enable-or-disable-extended-usage-tracking}

Bevor Sie beginnen, stellen Sie sicher, dass die Serverprüfung aktiviert ist. Siehe [Ereignisprüfungs- und Datenschutzeinstellungen konfigurieren](configuring-client-server-options.md#configuring-event-auditing-and-privacy-settings) für weitere Informationen zur Rechnungsprüfung.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Document Security&quot;> &quot;Konfiguration&quot;> &quot;Audit and Privacy Settings&quot;.
1. Um das erweiterte Nutzungsverfolgung zu konfigurieren, wählen Sie unter &quot;Tracking aktivieren&quot;die Option &quot;Ja&quot;oder &quot;Nein&quot;aus.
1. Um auf der Anmeldeseite das Kontrollkästchen Sammlung detaillierter Nutzungsdaten zulassen zu aktivieren, wählen Sie unter &quot;Tracking standardmäßig aktivieren&quot;die Option Ja oder Nein aus.

Um die verfolgten Ereignisse anzuzeigen, können Sie den Filter Dokumentereignisse auf der Seite Ereignisse verwenden. Die mit JavaScript verfolgten Ereignisse werden als detailliertes Nutzungsverfolgung bezeichnet. Siehe Abschnitt [Ereignisse überwachen](/help/forms/using/admin-help/monitoring-events.md#monitoring-events) für weitere Informationen zu Ereignissen.

## Anzeigeeinstellungen für Document Security konfigurieren {#configure-document-security-display-settings}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Document Security&quot;> &quot;Konfiguration&quot;> &quot;Anzeigeoptionen&quot;.
1. Konfigurieren Sie die Einstellungen und klicken Sie auf &quot;OK&quot;.

### Anzeigeeinstellungen {#display-settings}

**Für Suchergebnisse anzuzeigende Zeilen:** Anzahl der Zeilen, die auf einer Seite angezeigt werden, wenn Suchvorgänge durchgeführt werden.

**Dialogfeld für die Clientanmeldung anpassen**

Diese Einstellungen steuern den Text, der in der Anmeldeaufforderung angezeigt wird, die angezeigt wird, wenn sich ein Benutzer über eine Clientanwendung bei Document Security anmeldet.

**Begrüßungstext**: Der Text der Begrüßungsnachricht, z. B. „Bitte melden Sie sich mit Ihrem Benutzernamen und Kennwort an“. Der Begrüßungstext sollte Informationen dazu enthalten, wie Sie sich bei Document Security anmelden und wie Sie einen Administrator oder einen anderen Support-Mitarbeiter in Ihrem Unternehmen kontaktieren können, um Hilfe zu erhalten. Externe Benutzer müssen sich beispielsweise möglicherweise an einen Administrator wenden, wenn sie ihr Passwort vergessen haben oder Hilfe bei der Registrierung oder Anmeldung benötigen. Die maximale Länge des Begrüßungstextes beträgt 512 Zeichen.

**Benutzernamentext:** Die Textbeschriftung für das Feld Benutzername.

**Kennworttext:** Die Textbeschriftung für das Feld „Kennwort“.

**Dialogfeld für Client-Zertifikatauthentifizierung anpassen**

Diese Einstellungen steuern den Text, der im Dialogfeld für die Zertifikatauthentifizierung angezeigt wird.

**Text für 
„Authentifizierungstyp auswählen“:** Der Text, der angezeigt wird, um einen Benutzer zur Auswahl eines Authentifizierungstyps aufzufordern.

**Text für „Zertifikat auswählen“:** Der Text der angezeigt wird, um den Benutzer zum Auswählen eines Zertifikattyps aufzufordern.

**Fehlertext für „Zertifikate nicht verfügbar“:** Meldung mit bis zu 512 Zeichen, die angezeigt wird, wenn das ausgewählte Zertifikat nicht verfügbar ist.

**Client-Zertifikatanzeige anpassen**

**Nur Herausgeber von vertrauenswürdigen Berechtigungen anzeigen:** Wenn diese Option aktiviert ist, legt die Client-Anwendung dem Benutzer nur Zertifikate von Zertifizierungsstellen vor, die von AEM Forms laut Konfiguration als vertrauenswürdig eingestuft sind (siehe Verwalten von Zertifikaten und Berechtigungen.) Wenn diese Option nicht ausgewählt ist, wird dem Benutzer eine Liste aller Zertifikate auf dem System des Benutzers angezeigt.

## Dynamische Wasserzeichen konfigurieren {#configure-dynamic-watermarks}

Mit Document Security können Sie Standardeinstellungen für die Option für dynamische Wasserzeichen konfigurieren, die Sie beim Erstellen von Richtlinien anwenden können. A *Wasserzeichen* ist ein Bild, das über Text im Dokument überlagert wird. Dies ist nützlich für die Verfolgung des Inhalts eines Dokuments und kann dazu beitragen, die illegale Verwendung des Inhalts zu identifizieren.

Ein dynamisches Wasserzeichen kann entweder aus Text bestehen, der aus definierten Variablen wie Benutzer-ID und Datum und benutzerdefiniertem Text besteht, oder aus Rich-Content innerhalb einer PDF. Sie können Wasserzeichen mit mehreren Elementen konfigurieren, die jeweils eine eigene Positionierung und Formatierung aufweisen.

Wasserzeichen können nicht bearbeitet werden. Daher sind sie eine sicherere Methode, um die Vertraulichkeit des Dokumentinhalts zu gewährleisten. Dynamische Wasserzeichen stellen auch sicher, dass ein Wasserzeichen genügend benutzerspezifische Informationen anzeigt, um eine weitere Verteilung des Dokuments abzuwehren.

Das von einer Richtlinie angegebene Wasserzeichen wird im richtliniengeschützten Dokument angezeigt, wenn ein Empfänger das Dokument anzeigt oder druckt. Im Gegensatz zu dauerhaften Wasserzeichen wird ein dynamisches Wasserzeichen nie im Dokument gespeichert. Dies bietet die Flexibilität, die bei der Bereitstellung eines Dokuments in einer Intranetumgebung erforderlich ist, um sicherzustellen, dass die Anzeigeanwendung die Identität des spezifischen Benutzers anzeigt. Wenn ein Dokument mehrere Benutzer hat, bedeutet die Verwendung des dynamischen Wasserzeichens, dass Sie ein Dokument anstelle mehrerer Versionen mit jeweils einem anderen Wasserzeichen verwenden können. Das angezeigte Wasserzeichen spiegelt die Identität des aktuellen Benutzers wider.

Beachten Sie, dass sich dynamische Wasserzeichen von den Wasserzeichen unterscheiden, die Benutzer in Acrobat direkt zum Dokument hinzufügen können. Das Ergebnis ist, dass Sie in einem richtliniengeschützten Dokument zwei Wasserzeichen haben können.

### Überlegungen zum Erstellen von Wasserzeichen {#considerations-when-creating-watermarks}

Sie können dynamische Wasserzeichen mit mehreren Wasserzeichenelementen erstellen, wobei jedes Element als Text oder PDF angegeben ist. Sie können bis zu fünf Elemente in ein Wasserzeichen aufnehmen.

Wenn Sie ein textbasiertes Wasserzeichen auswählen, können Sie mehrere Elemente innerhalb des Wasserzeichens mit mehreren Texteinträgen angeben und die Position jedes Elements festlegen. Weisen Sie diesen Elementen aussagekräftige Namen zu, z. B. Kopf- und Fußzeile.

Wenn Sie beispielsweise unterschiedlichen Text in der Kopf- und Fußzeile, an den Rändern und im gesamten Dokument als Wasserzeichen angeben möchten, erstellen Sie mehrere Wasserzeichenelemente und geben Sie deren Position an. Wenn Sie möchten, dass die Benutzer-ID des Benutzers und das aktuelle Datum des Zugriffs auf das Dokument in der Kopfzeile, der Name der Richtlinie am rechten Rand und ein benutzerdefinierter Text wie „VERTRAULICH“ diagonal über dem Dokument erscheinen, definieren Sie separate Wasserzeichenelemente mit Text als Typ und legen dessen Formatierung und Positionierung fest. Wenn das Wasserzeichen auf ein Dokument angewendet wird, werden alle Elemente im Wasserzeichen gleichzeitig auf das Dokument angewendet, in der Reihenfolge, in der sie zum Wasserzeichen hinzugefügt werden.

In der Regel verwenden Sie PDF-basierte Wasserzeichen, um grafische Inhalte wie Logos oder Sonderzeichen wie Copyright oder eingetragene Marken einzuschließen.

Sie können die Grenzwerte für die Anzahl der Wasserzeichenelemente und die Dateigröße der PDF ändern, indem Sie die Document Security-Konfigurationsdatei ändern. Siehe [Parameter der Wasserzeichenkonfiguration ändern](configuring-client-server-options.md#change-the-watermark-configuration-parameters).

Beachten Sie beim Konfigurieren von Wasserzeichen Folgendes:

* Sie können kein kennwortgeschütztes PDF-Dokument als Wasserzeichenelement verwenden. Wenn das von Ihnen erstellte Wasserzeichen jedoch andere Elemente enthält, die nicht kennwortgeschützt sind, werden sie als Teil des Wasserzeichens angewendet.
* Sie können die maximale PDF-Dateigröße ändern, die Sie als Wasserzeichenelement verwenden möchten. Große PDF-Dokumente, die als Wasserzeichen verwendet werden, beeinträchtigen jedoch die Leistung bei der Offline-Synchronisation von Dokumenten, die mit solchen Wasserzeichen angewendet werden. Siehe [Parameter der Wasserzeichenkonfiguration ändern](configuring-client-server-options.md#change-the-watermark-configuration-parameters).
* Nur die erste Seite des ausgewählten PDF wird als Wasserzeichen verwendet. Stellen Sie sicher, dass die Informationen, die als Wasserzeichen angezeigt werden sollen, auf der ersten Seite selbst verfügbar sind.
* Obwohl Sie die Skalierung des PDF-Dokuments festlegen können, sollten Sie die Seitengröße und das Layout der PDF berücksichtigen, wenn Sie es als Wasserzeichen in der Kopf-, Fußzeile oder an den Rändern verwenden möchten.
* Geben Sie bei der Angabe des Schriftnamens den Namen richtig ein. AEM Formulare ersetzen die von Ihnen angegebene Schriftart, wenn sie nicht auf dem Clientcomputer vorhanden ist, auf dem das Dokument geöffnet wird.
* Wenn Sie Text als Wasserzeicheninhalt ausgewählt haben, funktioniert das Festlegen der Skalierungsoption als &quot;An Seite anpassen&quot;nicht für Seiten mit unterschiedlicher Breite.
* Wenn Sie die Positionierung der Wasserzeichenelemente festlegen, stellen Sie sicher, dass nicht mehr als ein Element dieselbe Position hat. Wenn zwei Wasserzeichenelemente dieselbe Position wie die Mitte haben, werden sie auf dem Dokument überlagert und in der Reihenfolge angezeigt, in der sie zum Wasserzeichen hinzugefügt wurden.
* Stellen Sie beim Festlegen der Schriftgröße und des Schrifttyps sicher, dass die Textlänge vollständig auf der Seite sichtbar ist. Textinhalte werden in neue Zeilen verschoben, sodass sich der Wasserzeicheninhalt, den Sie an den Rändern vorfinden möchten, möglicherweise mit den Inhaltsbereichen auf Seiten überschneidet. Wenn das Dokument jedoch in Acrobat 9 geöffnet wird, wird der Text über die einzelne Zeile hinaus abgeschnitten.

### Einschränkungen für dynamische Wasserzeichen {#limitations-of-dynamic-watermarks}

Einige Clientanwendungen unterstützen möglicherweise keine dynamischen Wasserzeichen. Weitere Informationen finden Sie in der entsprechenden Hilfe zu Acrobat Reader DC-Erweiterungen. Beachten Sie außerdem Folgendes zu den Versionen von Acrobat, die dynamische Wasserzeichen unterstützen:

* Sie können kein kennwortgeschütztes PDF-Dokument als Wasserzeichenelement verwenden.
* Acrobat- und Adobe Reader-Versionen vor 10 unterstützen die folgenden Wasserzeichenfunktionen nicht:

   * PDF-Wasserzeichen
   * Mehrere Elemente im Wasserzeichen (Text/PDF)
   * Erweiterte Optionen wie Seitenbereich oder Anzeigeoptionen
   * Textformatierungsoptionen wie angegebene Schriftart, Schriftname und Farbe. In früheren Versionen von Acrobat und Reader wird der Textinhalt jedoch in der Standardschrift und -farbe angezeigt.

* Acrobat 9.0 und frühere Versionen: Acrobat 9.0 und frühere Versionen unterstützen keine Richtliniennamen in dynamischen Wasserzeichen. Wenn Acrobat 9.0 ein richtliniengeschütztes Dokument mit einem dynamischen Wasserzeichen öffnet, das einen Richtliniennamen und andere dynamische Daten enthält, wird das Wasserzeichen ohne den Richtliniennamen angezeigt. Wenn das dynamische Wasserzeichen nur den Richtliniennamen enthält, zeigt Acrobat eine Fehlermeldung an

### Vorlage für dynamische Wasserzeichen hinzufügen {#add-a-dynamic-watermark-template}

Sie können Vorlagen für dynamische Wasserzeichen erstellen. Diese Vorlagen bleiben als Konfigurationsoption für Richtlinien verfügbar, die Administratoren oder Benutzer erstellen.

>[!NOTE]
>
>Konfigurationsinformationen dynamischer Wasserzeichen werden beim Exportieren einer Konfigurationsdatei nicht mit anderen Konfigurationsinformationen erfasst.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Document Security&quot;> &quot;Konfiguration&quot;> &quot;Wasserzeichen&quot;.
1. Klicken Sie auf Neu.
1. Geben Sie in das Feld &quot;Name&quot;einen Namen für das neue Wasserzeichen ein.

   ***Hinweis **: Einige Sonderzeichen können nicht in den Namen oder Beschreibungen von Wasserzeichen oder Wasserzeichenelementen verwendet werden. Siehe Einschränkungen unter [Überlegungen zum Bearbeiten von Richtlinien](/help/forms/using/admin-help/creating-policies.md#considerations-for-editing-policies).*

1. Geben Sie unter &quot;Name&quot;neben dem Pluszeichen einen aussagekräftigen Namen für das Wasserzeichenelement ein, z. B. &quot;Kopfzeile&quot;, fügen Sie eine Beschreibung hinzu und erweitern Sie das Pluszeichen, um die Optionen anzuzeigen.
1. Wählen Sie unter Quelle den Typ des Wasserzeichens entweder als Text oder als PDF aus.
1. Wenn Sie Text ausgewählt haben, gehen Sie wie folgt vor:

   * Wählen Sie die einzuschließenden Wasserzeichentypen aus. Wenn Sie &quot;Benutzerdefinierter Text&quot;auswählen, geben Sie in das angrenzende Feld den Text ein, der für das Wasserzeichen angezeigt werden soll. Beachten Sie die Textlänge, die als Wasserzeichen angezeigt wird.
   * Geben Sie die Eigenschaften für die Textformatierung wie Schriftart, Schriftgröße, Vordergrund- und Hintergrundfarbe für den Textinhalt des Wasserzeichentextes an. Geben Sie die Vordergrund- und Hintergrundfarbe als Hexadezimalwerte an.

     ***Hinweis **: Wenn Sie die Skalierungsoption als „An Seite anpassen“ wählen, steht die Eigenschaft der Schriftgröße nicht zur Bearbeitung zur Verfügung.*

1. Wenn Sie „PDF“ für komplexe Wasserzeichen ausgewählt haben, klicken Sie neben der Option „Wasserzeichen-PDF auswählen“ auf **Durchsuchen**, um das PDF -Dokument auszuwählen, das als Wasserzeichen verwendet werden soll.

   ***Hinweis **: Verwenden Sie kein kennwortgeschütztes PDF-Dokument. Wenn Sie ein kennwortgeschütztes PDF als Wasserzeichenelement angeben, wird das Wasserzeichen nicht angewendet.*

1. Wählen Sie unter Als Hintergrund verwenden entweder Ja oder Nein aus.

   **Hinweis**: Derzeit wird das Wasserzeichen unabhängig von dieser Einstellung im Vordergrund angezeigt.

1. Um zu steuern, wo das Wasserzeichen im Dokument angezeigt wird, konfigurieren Sie die Optionen Vertikale Ausrichtung und Horizontale Ausrichtung .
1. Wählen Sie entweder &quot;An Seite anpassen&quot;oder wählen Sie % aus und geben Sie einen Prozentsatz in das Feld ein. Der Wert muss eine ganze Zahl sein, kein Bruchteil. Um die Größe des Wasserzeichens zu konfigurieren, können Sie einen Wert verwenden, der dem Prozentsatz der Seite entspricht, oder das Wasserzeichen so einstellen, dass es der Größe der Seite entspricht.
1. Geben Sie in das Feld &quot;Drehung&quot;die Grad ein, um die das Wasserzeichen gedreht werden soll. Der Bereich liegt zwischen -180 und 180. Verwenden Sie einen negativen Wert, um das Wasserzeichen gegen den Uhrzeigersinn zu drehen. Der Wert muss eine ganze Zahl sein, kein Bruchteil.
1. Geben Sie in das Feld &quot;Deckkraft&quot;einen Prozentsatz ein. Verwenden Sie eine ganze Zahl, nicht einen Bruchteil.
1. Legen Sie unter Erweiterte Optionen Folgendes fest:

   **Seitenbereichsoptionen**

   Legen Sie den Seitenbereich fest, auf dem das Wasserzeichen angezeigt werden soll. Geben Sie die Startseite als 1 und die Endseite als -1 ein, damit alle Seiten mit dem Wasserzeichen markiert sind.

   **Anzeigeoptionen**

   Wählen Sie aus, wo das Wasserzeichen angezeigt werden soll. Standardmäßig wird das Wasserzeichen sowohl auf der Soft Copy (online) als auch auf der Festplatte (Druck) angezeigt.

1. Klicks **Neu** unter Wasserzeichenelemente , um bei Bedarf weitere Wasserzeichenelemente hinzuzufügen.
1. Klicken Sie auf OK.

### Vorlage für dynamische Wasserzeichen bearbeiten {#edit-a-dynamic-watermark-template}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Document Security&quot;> &quot;Konfiguration&quot;> &quot;Wasserzeichen&quot;.
1. Klicken Sie auf das entsprechende Wasserzeichen in der Liste.
1. Ändern Sie auf der Seite &quot;Wasserzeichen bearbeiten&quot;die Einstellungen nach Bedarf.
1. Klicken Sie auf OK.

### Vorlage für dynamische Wasserzeichen löschen {#delete-a-dynamic-watermark-template}

Wenn Sie ein dynamisches Wasserzeichen löschen, kann es nicht mehr zu einer neuen Richtlinie hinzugefügt werden. Das Wasserzeichen bleibt jedoch bei bestehenden Richtlinien erhalten, die es derzeit verwenden. Dokumente, die von der Richtlinie derzeit geschützt sind, zeigen das dynamische Wasserzeichen weiterhin an, bis Sie oder ein Benutzer die Richtlinie bearbeitet, die das gelöschte Wasserzeichen enthält. Nachdem die Richtlinie bearbeitet wurde, wird das Wasserzeichen nicht mehr angewendet. Es wird eine Meldung angezeigt, die angibt, dass das vorhandene Wasserzeichen in der Richtlinie gelöscht wird und der Benutzer ein anderes auswählen kann, um es zu ersetzen.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Document Security&quot;> &quot;Konfiguration&quot;> &quot;Wasserzeichen&quot;.
1. Aktivieren Sie das Kontrollkästchen neben dem entsprechenden Wasserzeichen und klicken Sie auf Löschen.
1. Klicken Sie auf OK.

## Registrierung für eingeladene Benutzer konfigurieren {#configuring-invited-user-registration}

Benutzer, die nicht zu Ihrer Organisation gehören, können sich bei Document Security registrieren. Eingeladene Benutzer, die sich registrieren und ihre Konten aktivieren, können sich bei Document Security anmelden, indem sie ihre E-Mail-Adresse und das Kennwort verwenden, die sie bei der Registrierung festgelegt haben. Registrierte eingeladene Benutzer können richtliniengeschützte Dokumente verwenden, für die sie Berechtigungen haben.

Wenn eingeladene Benutzer aktiviert werden, werden sie zu lokalen Benutzern. Lokale Benutzer können über den Bereich Eingeladene und lokale Benutzer konfiguriert und verwaltet werden. (Siehe [Konten eingeladener und lokaler Benutzer verwalten](/help/forms/using/admin-help/invited-local-user-accounts.md#managing-invited-and-local-user-accounts).

Abhängig von den Funktionen, die Sie für eingeladene Benutzer aktivieren, können diese auch die folgenden Document Security-Funktionen verwenden:

* Richtlinien auf Dokumente anwenden
* Erstellen von Richtlinien
* Eingeladene Benutzer zu Richtlinien hinzufügen

Document Security generiert automatisch eine Einladungs-E-Mail zur Registrierung, wenn die folgenden Ereignisse eintreten, es sei denn, der Benutzer befindet sich bereits im LDAP-Quellordner oder wurde zuvor zur Registrierung eingeladen:

* Ein bestehender Benutzer fügt einen eingeladenen Benutzer zu einer Richtlinie hinzu
* Ein Administrator fügt ein Konto für eingeladene Benutzer auf der Seite &quot;Registrierung für eingeladene Benutzer&quot;hinzu

Die Registrierungs-E-Mail enthält einen Link zu einer Registrierungsseite und Informationen zur Registrierung. Nachdem sich der eingeladene Benutzer registriert hat, sendet Document Security eine Aktivierungs-E-Mail mit einem Link zu einer Aktivierungsseite. Bei Aktivierung bleibt das Konto gültig, bis Sie es deaktivieren oder löschen.

Wenn Sie die integrierte Registrierung aktivieren, geben Sie Ihren SMTP-Server, die Details der Registrierungs-E-Mail, die Zugriffsfunktionen und die E-Mail-Informationen zum Zurücksetzen des Kennworts nur einmal an. Bevor Sie die integrierte Registrierung aktivieren, stellen Sie sicher, dass Sie in der Benutzerverwaltung eine lokale Domäne erstellt und den entsprechenden Benutzenden und Gruppen in Ihrem Unternehmen die Rolle „Dokumentensicherheit – Benutzer einladen“ zugewiesen haben. (Siehe [Lokale Domain hinzufügen](/help/forms/using/admin-help/adding-domains.md#add-a-local-domain) und [Rollen erstellen und konfigurieren](/help/forms/using/admin-help/creating-configuring-roles.md#creating-and-configuring-roles).) Wenn Sie „Integrierte Registrierung“ nicht verwenden, müssen Sie über ein eigenes mit dem AEM Forms-SDK erstelltes Benutzerregistrierungssystem verfügen. Siehe die Hilfe zu „Entwickeln von SPIs für AEM-Formulare“ in [Programmieren mit AEM Forms](/help/forms/developing/introducing-java-api-soap-quick.md). Wenn Sie die Option &quot;Integrierte Registrierung&quot;nicht verwenden, wird empfohlen, eine Nachricht in der Aktivierungs-E-Mail und auf dem Clientanmeldebildschirm zu konfigurieren, um Benutzer darüber zu informieren, wie der Administrator für ein neues Kennwort oder andere Informationen kontaktiert werden kann.

**Registrierung für eingeladene Benutzer aktivieren und konfigurieren**

Standardmäßig ist der Registrierungsprozess für eingeladene Benutzer deaktiviert. Sie können die Registrierung eingeladener Benutzer für Document Security bei Bedarf aktivieren und deaktivieren.

1. Klicken Sie in Administration Console auf Dienste > Document Security > Konfiguration > Registrierung für eingeladene Benutzer.
1. Wählen Sie Registrierung für eingeladene Benutzer aktivieren aus.
1. (Optional) Aktualisieren Sie die Einstellungen für die Registrierung eingeladener Benutzer nach Bedarf:

   * [Externe Benutzer oder Benutzergruppen ein- oder ausschließen](configuring-client-server-options.md#exclude-or-include-an-external-user-or-group)
   * [Server- und Registrierungskontoparameter](configuring-client-server-options.md#server-and-registration-account-parameters)
   * [Einstellungen für die Einladungs-E-Mail zur Registrierung](configuring-client-server-options.md#registration-invitation-email-settings)
   * [Einstellungen für Aktivierungs-E-Mail](configuring-client-server-options.md#activation-email-settings)
   * [Eine E-Mail zum Zurücksetzen des Kennworts konfigurieren](configuring-client-server-options.md#configure-a-password-reset-email)

1. (Optional) Wählen Sie unter &quot;Integrierte Registrierung&quot;die Option Ja aus, um diese Option zu aktivieren. Wenn Sie die integrierte Registrierung nicht aktivieren, müssen Sie ein eigenes Benutzerregistrierungssystem einrichten.
1. Klicken Sie auf OK.

### Ein- oder Ausschließen von externen Benutzern oder Benutzergruppen {#exclude-or-include-an-external-user-or-group}

Sie können die Registrierung mit Document Security für bestimmte externe Benutzer oder Benutzergruppen einschränken. Diese Option ist beispielsweise nützlich, um den Zugriff auf eine bestimmte Benutzergruppe zu ermöglichen, aber bestimmte Personen auszuschließen, die Teil der Gruppe sind.

Die folgenden Einstellungen befinden sich im Bereich Filter für E-Mail-Einschränkungen auf der Seite Registrierung für eingeladene Benutzer.

**Ausschluss:** Geben Sie die E-Mail-Adresse eines Benutzers oder einer Gruppe ein, die Sie ausschließen möchten. Um mehrere Benutzer oder Gruppen auszuschließen, geben Sie jede E-Mail-Adresse in eine neue Zeile ein. Um alle Benutzer, die zu einer bestimmten Domain gehören, auszuschließen, geben Sie einen Platzhalter und den Domain-Namen ein. Um beispielsweise alle Benutzer mit der Domain „example.com“ auszuschließen, geben Sie „*.example.com“ ein.

**Einbeziehung:** Geben Sie die E-Mail-Adresse eines Benutzers oder einer Gruppe ein, die Sie einbeziehen möchten. Um mehrere Benutzer oder Gruppen einzubeziehen, geben Sie jede E-Mail-Adresse in eine neue Zeile ein. Um alle Benutzer, die zu einer bestimmten Domäne gehören, einzubeziehen, geben Sie einen Platzhalter und den Domänennamen ein. Um beispielsweise alle Benutzer mit der Domain „example.com“ einzubeziehen, geben Sie „*.example.com“ ein.

### Server- und Registrierungskontoparameter {#server-and-registration-account-parameters}

Die folgenden Einstellungen befinden sich im Bereich &quot;Allgemeine Einstellungen&quot;auf der Seite &quot;Registrierung für eingeladene Benutzer&quot;.

**SMTP-Host:** Der Host-Name des SMTP-Servers. Der SMTP-Server verwaltet die ausgehenden E-Mail-Benachrichtigungen, um eingeladene Benutzerkonten zu registrieren und zu aktivieren.

Geben Sie bei Bedarf für Ihren SMTP-Host die erforderlichen Informationen in die Felder &quot;Kontoname des SMTP-Servers&quot;und &quot;Kennwort des SMTP-Servers&quot;ein, um eine Verbindung zum SMTP-Server herzustellen. Einige Unternehmen setzen diese Anforderung nicht um. Wenn Sie Informationen benötigen, wenden Sie sich an Ihren Systemadministrator.

**Socket-Klassenname des SMTP-Servers:** Socket-Klassenname für den SMTP-Server. Zum Beispiel javax.net.ssl.SSLSocketFactory.

**E-Mail-Content-Typ:** Akzeptierter MIME-Typ wie text/plain oder text/html.

**E-Mail-Kodierung:** Das zum Senden der E-Mail-Nachricht zu verwendende Kodierungsformat. Sie können eine beliebige Kodierung angeben, z. B. UTF-8 für Unicode oder ISO-8859-1 für Latein. Der Standardwert ist UTF-8.

**E-Mail-Adresse umleiten:** Wenn Sie eine E-Mail-Adresse für diese Einstellung angeben, werden alle neuen Einladungen an die angegebene Adresse gesendet. Diese Einstellung kann für Testzwecke sinnvoll sein.

**Lokale Domains verwenden:** Wählen Sie die entsprechende Domain aus. Stellen Sie bei einer Neuinstallation sicher, dass Sie die Domain in User Management erstellt haben. Bei einem Update kann eine externe Benutzer-Domain, die während des Updates erstellt wurde, verwendet werden.

**SSL für SMTP-Server verwenden:** Wählen Sie diese Option, um SSL für den SMTP-Server zu aktivieren.

**Anmelde-Link auf Registrierungsseite anzeigen:** Zeigt einen Anmelde-Link auf der Registrierungsseite für eingeladene Benutzer an.

**Aktivieren von Transport Layer Security (TLS) für den SMTP-Server**

1. Öffnen Sie die Administration Console.

   Der Standardspeicherort der Administration-Console ist `https://<server>:<port>/adminui`.

1. Navigieren Sie zu Startseite > Dienste > Document Security > Konfiguration > Registrierung für eingeladene Benutzer.
1. Geben Sie unter Registrierung für eingeladene Benutzer alle Konfigurationseinstellungen an und klicken Sie auf &quot;OK&quot;.

   >[!NOTE]
   >
   >Wenn Sie Microsoft Office 365 als SMTP-Server zum Senden der Einladungen für eine Benutzerregistrierung verwenden, verwenden Sie die folgenden Einstellungen:
   >
   >**SMTP Host:** smtp.office365.com
   >**Port:** 587

1. Als Nächstes müssen Sie „config.xml“ aktualisieren. Siehe [Konfiguration zum Aktivieren von SMTP für Transport Layer Security (TLS)](configuring-client-server-options.md#configuration-to-enable-smtp-for-transport-layer-security-tls)

>[!NOTE]
>
>Wenn Sie Änderungen an den Optionen für die Registrierung eingeladener Benutzer vornehmen, wird die Datei „config.xml“ überschrieben und TLS wird deaktiviert. Wenn Sie die Änderungen überschreiben, müssen Sie den obigen Schritt ausführen, um die TLS-Unterstützung für die Registrierung eingeladener Benutzer erneut zu aktivieren.

### Einstellungen für die Einladungs-E-Mail zur Registrierung {#registration-invitation-email-settings}

Document Security sendet automatisch eine Einladungs-E-Mail zur Registrierung, wenn Sie ein Konto für eingeladene Benutzer erstellen oder wenn ein bestehender Benutzer einen externen Empfänger hinzufügt, der sich noch nicht registriert hat oder zur Registrierung eingeladen wurde. Die E-Mail enthält einen Link, über den der Empfänger auf die Registrierungsseite zugreifen und persönliche Kontoinformationen wie Benutzername und Kennwort eingeben kann. Das Kennwort kann eine beliebige Kombination aus acht Zeichen sein.

Wenn der Empfänger das Konto aktiviert, wird der Benutzer zu einem lokalen Benutzer.

Die folgenden Einstellungen befinden sich im Bereich Konfiguration der Einladungs-E-Mail auf der Seite Registrierung für eingeladene Benutzer .

**Von:** Die E-Mail-Adresse, von der die Einladungs-E-Mail gesendet wird. Das Standardformat der „Von“-E-Mail-Adresse ist „postmaster@[Ihre_Installations-Domain].com“.

**Betreff:** Standardbetreff für die E-Mail-Nachricht mit der Einladung.

**Maximale Wartezeit:** Die Anzahl der Tage, nach denen die Registrierungseinladung abläuft, wenn sich der externe Benutzer nicht registriert. Der Standardwert ist 30 Tage.

**Nachricht:** Der Text, der im Textkörper der Nachricht angezeigt wird und den Benutzer zur Registrierung einlädt.

### Einstellungen für die Aktivierungs-E-Mail {#activation-email-settings}

Nachdem sich eingeladene Benutzer registriert haben, sendet Document Security eine Aktivierungs-E-Mail. Die Aktivierungs-E-Mail enthält einen Link zur Kontoaktivierungsseite, auf der die Benutzer ihr Konto aktivieren können. Wenn die Konten aktiviert werden, können sich Benutzer bei Document Security anmelden, indem sie ihre E-Mail-Adresse und das Kennwort verwenden, die sie bei der Registrierung erstellt haben.

Wenn der Empfänger das Benutzerkonto aktiviert, wird der Benutzer zu einem lokalen Benutzer.

Die folgenden Einstellungen befinden sich im Bereich Konfiguration der Aktivierungs-E-Mail auf der Seite Registrierung für eingeladene Benutzer .

>[!NOTE]
>
>Es wird außerdem empfohlen, eine Meldung auf dem Anmeldebildschirm zu konfigurieren, um externe Benutzer darüber zu informieren, wie sie ihren Administrator für ein neues Kennwort oder andere Informationen kontaktieren können.

**Von:** Die E-Mail-Adresse, von der die Aktivierungs-E-Mail gesendet wird. Diese E-Mail-Adresse erhält Benachrichtigungen zu fehlgeschlagenen Sendungen vom E-Mail-Host des Registranten sowie alle Nachrichten, die der Empfänger als Antwort auf die Registrierungs-E-Mail sendet. Das Standardformat der „Von“-E-Mail-Adresse ist „postmaster@[Ihre_Installations-Domain].com“.

**Betreff:** Standardbetreff für die Aktivierungs-E-Mail-Nachricht.

**Maximale Wartezeit:** Die Anzahl der Tage, nach denen die Aktivierungseinladung abläuft, wenn der Benutzer das Konto nicht aktiviert. Der Standardwert ist 30 Tage.

**Nachricht:** Der Text, der im Nachrichten-Textkörper angezeigt wird und der angibt, dass das Benutzerkonto des Empfängers aktiviert werden muss. Sie können auch Informationen angeben, wie Sie einen Administrator kontaktieren können, um ein neues Kennwort zu erhalten.

### Konfigurieren einer E-Mail zum Zurücksetzen des Kennworts {#configure-a-password-reset-email}

Wenn Sie das Kennwort eines eingeladenen Benutzers zurücksetzen müssen, wird eine Bestätigungs-E-Mail generiert, die den Benutzer zur Auswahl eines neuen Kennworts einlädt. Das Kennwort eines Benutzers kann nicht ermittelt werden. Wenn der Benutzer es vergisst, müssen Sie es zurücksetzen.

Die folgenden Einstellungen befinden sich im Bereich &quot;Kennwort-E-Mail zurücksetzen&quot;auf der Seite &quot;Registrierung für eingeladene Benutzer&quot;.

**Von:** Die E-Mail-Adresse, von der die E-Mail zum Zurücksetzen des Kennworts gesendet wird. Das Standardformat der „Von“-E-Mail-Adresse ist „postmaster@[Ihre_Installations-Domain].com“.

**Betreff:** Standardbetreff für die Nachricht zum Zurücksetzen.

**Nachricht:** Der Text, der im Textkörper der Nachricht angezeigt wird und der angibt, dass das externe Benutzerkennwort des Empfängers zurückgesetzt wurde.

## Benutzer und Gruppen zum Erstellen von Richtlinien aktivieren {#enable-users-and-groups-to-create-policies}

Die Seite &quot;Konfiguration&quot;enthält einen Link zur Seite &quot;Meine Richtlinien&quot;, auf der Sie angeben, welche Endbenutzer meine Richtlinien erstellen können und welche Benutzer und Gruppen in den Suchergebnissen sichtbar sind. Die Seite &quot;Meine Richtlinien&quot;verfügt über zwei Registerkarten:

**Registerkarte „Richtlinien erstellen“:** Wird verwendet, um Benutzerberechtigungen zum Erstellen benutzerdefinierter Richtlinien zu konfigurieren.

**Registerkarte „Sichtbare Benutzer und Gruppen“:** Hier können Sie steuern, welche Benutzer und Gruppen in den Suchergebnissen der Benutzer sichtbar sind. Der Hauptbenutzer oder Richtliniensatzadministrator muss für jeden Richtliniensatz in User Management erstellte Domains auswählen und zum sichtbaren Benutzer bzw. zur sichtbaren Gruppe hinzufügen. Diese Liste wird dem Richtliniensatzkoordinator angezeigt und dient zum Eingrenzen der Domains, die der Richtliniensatzkoordinator beim Auswählen von Benutzern durchsuchen kann, die Richtlinien hinzugefügt werden sollen.

Bevor Sie Benutzern Berechtigungen zum Erstellen benutzerdefinierter Richtlinien erteilen, sollten Sie wissen, wie viel Zugriff oder Kontrolle einzelne Benutzer haben sollen. Überlegen Sie außerdem, wie offen gelegt werden soll, wenn Benutzer und Gruppen für Suchvorgänge sichtbar gemacht werden sollen.

### Benutzer und Gruppen angeben, die Richtlinien erstellen können {#specify-users-and-groups-who-can-create-policies}

Geben Sie als Administrator an, welche Benutzer und Gruppen benutzerdefinierte Richtlinien erstellen können. Diese Berechtigung kann auf Benutzer- und Gruppenebene festgelegt werden. Die Suchfunktion durchsucht die User Management-Datenbank nach Benutzern und Gruppen.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Document Security&quot;> &quot;Konfiguration&quot;> &quot;Meine Richtlinien&quot;.
1. Klicken Sie auf der Seite Meine Richtlinien auf die Registerkarte Richtlinien erstellen und klicken Sie auf Benutzer und Gruppen hinzufügen .
1. Geben Sie in das Feld &quot;Suchen&quot;den Benutzernamen oder die E-Mail-Adresse des Benutzers oder der Gruppe ein, nach dem/der Sie suchen. Wenn Sie diese Informationen nicht haben, lassen Sie das Feld leer. Sie können auch einen Teilnamen oder eine E-Mail-Adresse eingeben, z. B. wenn Sie nur die ersten beiden Buchstaben eines Benutzernamens kennen.
1. Wählen Sie in der Liste Verwenden die Suchparameter Name oder E-Mail aus.
1. Wählen Sie in der Liste &quot;Typ&quot;die Option &quot;Gruppe&quot;oder &quot;Benutzer&quot;aus, um die Suche einzuschränken.
1. Wählen Sie in der Liste „In“ die zu durchsuchende Domain aus. Wenn Sie die Domäne des Benutzers oder der Gruppe nicht kennen, wählen Sie Alle Domänen aus.
1. Geben Sie in der Liste &quot;Anzeigen&quot;die Anzahl der pro Seite anzuzeigenden Suchergebnisse an und klicken Sie auf &quot;Suchen&quot;.
1. Um Benutzer und Gruppen zu &quot;Meine Richtlinien&quot;hinzuzufügen, aktivieren Sie das Kontrollkästchen der hinzuzufügenden Benutzer und Gruppen.
1. Klicken Sie auf Hinzufügen und dann auf OK.

Ihre ausgewählten Benutzer und Gruppen können jetzt benutzerdefinierte Richtlinien erstellen.

### Entfernen Sie die Berechtigung zum Erstellen benutzerdefinierter Richtlinien von einem Benutzer oder einer Gruppe {#remove-the-create-custom-policies-permission-from-a-user-or-group}

1. Klicken Sie auf der Document Security-Seite auf &quot;Konfiguration&quot;> &quot;Meine Richtlinien&quot;.
1. Klicken Sie auf der Seite Meine Richtlinien auf die Registerkarte Richtlinien erstellen . Benutzer und Gruppen mit der Berechtigung zum Erstellen benutzerdefinierter Richtlinien werden angezeigt.
1. Aktivieren Sie das Kontrollkästchen neben den Benutzern und Gruppen, die Sie aus dieser Berechtigung entfernen möchten.
1. Klicken Sie auf Löschen und dann auf OK.

### Festlegen von Benutzern und Gruppen, die in Suchvorgängen sichtbar sind {#specify-users-and-groups-that-are-visible-in-searches}

Wenn Benutzer ihre benutzerdefinierten Richtlinien verwalten, können sie nach Benutzern und Gruppen suchen, die zu ihren Richtlinien hinzugefügt werden sollen. Geben Sie die Domänen an, von denen aus Benutzer und Gruppen bei diesen Suchvorgängen sichtbar sind.

1. Klicken Sie auf der Document Security-Seite auf &quot;Konfiguration&quot;> &quot;Meine Richtlinien&quot;.
1. Klicken Sie auf der Seite Meine Richtlinien auf die Registerkarte Sichtbare Benutzer und Gruppen .
1. Um die Benutzer und Gruppen in einer Domain sichtbar zu machen, klicken Sie auf „Domains hinzufügen“, wählen Sie die Domains aus und klicken Sie auf „Hinzufügen“. Aktivieren Sie zum Entfernen einer Domain das Kontrollkästchen neben dem Domain-Namen und klicken Sie auf „Löschen“.

## Manuelles Bearbeiten der Document Security-Konfigurationsdatei {#manually-editing-the-document-security-configuration-file}

Sie können die in der Document Security-Datenbank gespeicherten Konfigurationsinformationen importieren und exportieren. Sie können beispielsweise eine Sicherungskopie der Konfigurationsinformationen erstellen, wenn Sie von einer Staging- in eine Produktionsumgebung wechseln. Alternativ können Sie erweiterte Optionen bearbeiten, die nur durch Bearbeiten dieser Datei konfiguriert werden können.

Sie können die folgenden Änderungen mithilfe der Konfigurationsdatei vornehmen:

[Anzeigen von CATIA-Berechtigungen beim Erstellen und Bearbeiten von Richtlinien](configuring-client-server-options.md#display-catia-permissions-when-creating-and-editing-policies)

[Zeitüberschreitungszeitraum für die Offline-Synchronisierung festlegen](configuring-client-server-options.md#specify-a-timeout-period-for-offline-synchronization)

[Ablehnen von Document Security-Diensten für bestimmte Anwendungen](configuring-client-server-options.md#denying-document-security-services-for-specific-applications)

[Parameter der Wasserzeichenkonfiguration ändern](configuring-client-server-options.md#change-the-watermark-configuration-parameters)

[Externe Verknüpfungen deaktivieren](configuring-client-server-options.md#disabling-external-links)

>[!NOTE]
>
>Beim Import der Konfigurationsdatei wird Ihr System basierend auf den Informationen in der Datei neu konfiguriert. Ausnahmen sind die Konfiguration dynamischer Wasserzeichen und benutzerdefinierte Ereignisinformationen, die nicht mit der exportierten Konfigurationsdatei gespeichert werden. Sie müssen diese Informationen manuell in Ihrem neuen System konfigurieren. Nur ein Systemadministrator oder ein Professional Services-Berater, der mit Document Security und XML vertraut ist, sollte den Inhalt einer Konfigurationsdatei ändern, z. B. um eine beschädigte Einstellung neu zu konfigurieren oder Parameter für ein bestimmtes Bereitstellungsszenario in einem Unternehmen anzupassen.

**Konfigurationsdatei exportieren**

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Document Security 11&quot;> &quot;Konfiguration&quot;> &quot;Manuelle Konfiguration&quot;.
1. Klicken Sie auf Exportieren und speichern Sie die Konfigurationsdatei an einem anderen Speicherort. Der Standarddateiname lautet &quot;config.xml&quot;.
1. Klicken Sie auf OK.
1. Bevor Sie die Konfigurationsdatei ändern, erstellen Sie eine Sicherungskopie, falls Sie sie wiederherstellen müssen.

**Eine Konfigurationsdatei importieren**

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Document Security 11&quot;> &quot;Konfiguration&quot;> &quot;Manuelle Konfiguration&quot;.
1. Klicken Sie auf Durchsuchen , um zur Konfigurationsdatei zu wechseln, und klicken Sie dann auf Importieren. Sie können den Pfad nicht direkt in das Feld Dateiname eingeben.
1. Klicken Sie auf OK.

### Zeitüberschreitungszeitraum für die Offline-Synchronisierung festlegen {#specify-a-timeout-period-for-offline-synchronization}

Document Security ermöglicht Benutzern das Öffnen und Verwenden geschützter Dokumente, wenn sie nicht mit dem Document Security-Server verbunden sind. Die Clientanwendung des Benutzers muss regelmäßig mit dem Server synchronisiert werden, damit Dokumente für die Offline-Verwendung gültig bleiben. Wenn Benutzer zum ersten Mal ein geschütztes Dokument öffnen, werden sie gefragt, ob ihr Computer zur Durchführung periodischer Clientsynchronisierungen autorisiert werden soll.

Standardmäßig erfolgt die Synchronisation automatisch alle vier Stunden und nach Bedarf, wenn ein Benutzer mit dem Document Security-Server verbunden ist. Wenn der Offline-Zeitraum für ein Dokument abläuft, während der Benutzer offline ist, muss der Benutzer erneut eine Verbindung zum Server herstellen, damit die Client-Anwendung mit dem Server synchronisiert werden kann.

In der Document Security-Konfigurationsdatei können Sie die Standardfrequenz der automatischen Hintergrundsynchronisierung festlegen. Diese Einstellung dient als standardmäßige Timeout-Zeit für Client-Anwendungen, es sei denn, der Client legt explizit einen eigenen Timeout-Wert fest.

1. Exportieren Sie die Document Security-Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).
1. Öffnen Sie die Konfigurationsdatei in einem Editor und suchen Sie den Knoten `PolicyServer`. Suchen Sie unter diesem Knoten den Knoten `ServerSettings`.
1. Fügen Sie im Knoten `ServerSettings` den folgenden Eintrag hinzu und speichern Sie anschließend die Datei:

   `<entry key="BackgroundSyncFrequency" value="`*Uhrzeit* `"/>`

   dabei ist *time* die Anzahl der Sekunden zwischen den automatischen Hintergrundsynchronisationen. Wenn Sie diesen Wert auf `0` festgelegt haben, wird immer eine Synchronisation ausgeführt. Der Standardwert ist `14400` Sekunden (alle vier Stunden).

1. Importieren Sie die Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).

### Ablehnen von Document Security-Diensten für bestimmte Anwendungen {#denying-document-security-services-for-specific-applications}

Sie können Document Security so konfigurieren, dass Dienste für Anwendungen, die bestimmte Kriterien erfüllen, verweigert werden. Die Kriterien können ein einzelnes Attribut, z. B. einen Plattformnamen, angeben oder mehrere Attributsätze angeben. Mit dieser Funktion können Sie die Anforderungen steuern, die Document Security verarbeiten muss. Im Folgenden finden Sie einige Anwendungen dieser Funktion:

* **Einkommensschutz:** Sie können den Zugriff auf Clientanwendungen, die Ihre Einkommenskonventionen nicht unterstützen, verweigern.
* **Anwendungskompatibilität:** Einige Anwendungen sind möglicherweise nicht mit den Richtlinien oder dem Verhalten Ihres Document Security-Servers kompatibel.

Wenn Clientanwendungen versuchen, eine Verknüpfung mit Document Security herzustellen, stellen sie Anwendungs-, Versions- und Plattforminformationen bereit. Document Security vergleicht diese Informationen mit den Verweigerungs-Einstellungen, die es aus der Document Security-Konfigurationsdatei erhält.

Die Verweigerungseinstellungen können mehrere Verweigerungsbedingungen enthalten. Wenn alle Attribute eines Sets übereinstimmen, wird der anfordernden Anwendung der Zugriff auf die Document Security-Dienste verweigert.

Die Funktion zur Dienstverweigerung erfordert, dass Clientanwendungen die Document Security C++ Client SDK-Version 8.2 oder höher verwenden. Die folgenden Adobe-Produkte stellen Produktinformationen bereit, wenn Document Security-Dienste angefordert werden:

* Adobe Acrobat 9.0 Professional/Acrobat 9.0 Standard und höher
* Adobe Reader 9.0 und höher
* Acrobat Reader DC-Erweiterungen für Microsoft Office 8.2 und höher

Clientanwendungen verwenden die Client-API aus dem Document Security C++ Client SDK, um Dienste von Document Security anzufordern. Die Client-API-Anfragen enthalten Informationen zur Plattform- und SDK-Version (vorkompiliert in die Client-API) sowie Produktinformationen, die von der Client-Anwendung abgerufen werden.

Client-Anwendungen oder Plug-ins liefern Produktinformationen bei ihrer Implementierung einer Callback-Funktion. Die Anwendung stellt die folgenden Informationen bereit:

* Integratorname
* Integrator-Version
* Anwendungsfamilie
* Anwendungsname
* Anwendungsversion

Wenn keine Informationen verfügbar sind, bleibt das entsprechende Feld in der Clientanwendung leer.

Einige Adobe-Anwendungen enthalten Produktinformationen beim Anfordern von Document Security-Diensten, einschließlich Acrobat-, Adobe Reader- und Acrobat Reader DC-Erweiterungen für Microsoft Office.

**Acrobat und Adobe Reader**

Wenn Acrobat oder Adobe Reader einen Dienst von Document Security anfordern, werden die folgenden Produktinformationen bereitgestellt:

* **Integrator:** Adobe Systems, Inc.
* **Integrator-Version:** 1.0
* **Anwendungsfamilie:** Acrobat
* **Anwendungsname:** Acrobat
* **Anwendungsversion:** 9.0.0

**Acrobat Reader DC Extensions für Microsoft Office**

Acrobat Reader DC Extensions für Microsoft Office ist ein Plug-in, das mit den Microsoft Office-Produkten Microsoft Word, Microsoft Excel und Microsoft PowerPoint verwendet wird. Wenn ein Dienst angefordert wird, stellt er die folgenden Informationen bereit:

* **Integrator:** Adobe Systems Incorporated
* **Integrator-Version:** 8.2
* **Anwendungsfamilie:** Acrobat Reader DC Extensions für Microsoft Office
* **Anwendungsname:** Microsoft Word, Microsoft Excel oder Microsoft PowerPoint
* **Anwendungsversion:** 2003 oder 2007

**Document Security zum Ablehnen von Diensten für bestimmte Anwendungen konfigurieren**

1. Exportieren Sie die Document Security-Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).
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
   * APPLE OS X
   * Sun Solaris
   * HP-UX

   `SDKVersions` gibt die Version der Document Security C++ Client-API an, die von der Clientanwendung verwendet wird. Beispiel: `"8.2"`.

   `APPFamilies` ist durch die Client-API definiert.

   `AppName` gibt den Namen der Clientanwendung an. Kommas werden als Trennzeichen für Namen verwendet. Um ein Komma in einen Namen einzufügen, maskieren Sie es mit einem umgekehrten Schrägstrich (\). Beispiel: *&quot;Adobe Systems\, Inc.&quot;*.

   `AppVersions` gibt die Version der Clientanwendung an.

   `Integrators` gibt den Namen des Unternehmens oder der Gruppe, die das Plug-In oder die integrierte Anwendung entwickelt hat, an.

   `IntegratorVersions` ist die Version des Plug-Ins oder der integrierten Anwendung.

1. Fügen Sie für jeden zusätzlichen Satz von Verweigerungsdaten einen weiteren hinzu. *MyEntryName* -Element.
1. Speichern Sie die Konfigurationsdatei.
1. Importieren Sie die Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).

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

In diesem Beispiel wird der Zugriff auf My Application Version 3.0 und My Other Application Version 2.0 verweigert. Dieselbe URL für Verweigerungsinformationen wird unabhängig vom Grund für die Verweigerung verwendet.

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

In diesem Beispiel werden alle Anforderungen einer Microsoft PowerPoint 2007- oder Microsoft PowerPoint 2010-Installation von Acrobat Reader DC-Erweiterungen für Microsoft Office verweigert.

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

Standardmäßig können Sie maximal fünf Elemente in einem Wasserzeichen angeben. Außerdem ist die maximale Dateigröße des PDF-Dokuments, das Sie als Wasserzeichen verwenden möchten, auf 100 KB beschränkt. Sie können diese Parameter in der Datei config.xml ändern.

***Hinweis **: Sie sollten diese Parameter mit Vorsicht ändern.*

1. Exportieren Sie die Document Security-Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).
1. Öffnen Sie die Konfigurationsdatei in einem Editor und suchen Sie den Knoten `ServerSettings`.
1. Fügen Sie im Knoten `ServerSettings` die folgenden Einträge hinzu und speichern Sie anschließend die Datei: `<entry key="maximumSizeOfWatermarkElement" value="max filesize in KB"/> <entry key="maximumWatermarkElementsPerWatermark" value="max elements"/>`

   Der erste Eintrag *max file size* ist die Maximalgröße der Datei (in KB) für ein Wasserzeichenelement. Der Standardwert ist 100 KB.

   den zweiten Eintrag, *max -Elemente* ist die maximale Anzahl von Elementen, die in einem Wasserzeichen zulässig ist. Der Standardwert ist 5.

   ```xml
   <entry key="maximumSizeOfWatermarkElement" value="max filesize in KB"/>
   <entry key="maximumWatermarkElementsPerWatermark" value="max elements"/>
   ```

1. Importieren Sie die Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).

### Deaktivieren von externen Verknüpfungen {#disabling-external-links}

Viele Document Security-Benutzer haben keinen Zugriff auf externe Links wie **www.adobe.com** während sie die Rights Management-Benutzeroberflächen verwenden:

* `https://[host]:'port'/adminui`
* `https://[host]:'port'/edc`.

Die folgenden Änderungen an der Datei &quot;config.xml&quot;deaktivieren alle externen Links über die Rights Management-Benutzeroberflächen.

1. Exportieren Sie die Document Security-Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).
1. Öffnen Sie die Konfigurationsdatei in einem Editor und suchen Sie den Knoten `DisplaySettings`.
1. Um alle externen Verknüpfungen zu deaktivieren, fügen Sie im Knoten `DisplaySettings` den folgenden Eintrag hinzu und speichern Sie anschließend die Datei: `<entry key="ExternalLinksAllowed" value="false"/>`

   ```xml
   <entry key="ExternalLinksAllowed" value="false"/>
   ```

1. Importieren Sie die Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).

### Konfiguration zum Aktivieren von SMTP für Transport Layer Security (TLS) {#configuration-to-enable-smtp-for-transport-layer-security-tls}

Die folgenden Änderungen an &quot;config.xml&quot;aktivieren die TLS-Unterstützung für die Funktion &quot;Registrierung für eingeladene Benutzer&quot;.

1. Exportieren Sie die Document Security-Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).
1. Öffnen Sie die Konfigurationsdatei in einem Editor und suchen Sie den Knoten `DisplaySettings`.
1. Suchen Sie den folgenden Knoten: `<node name="ExternalUser">`

   ```xml
   <node name="ExternalUser">
   ```

1. Legen Sie für den Schlüssel `SmtpUseTls` unter dem Knoten `ExternalUser` den Wert **true** fest.
1. Legen Sie für den Schlüssel `SmtpUseSsl` unter dem Knoten `ExternalUser` den Wert **false** fest.
1. Speichern Sie die `config.xml`.
1. Importieren Sie die Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).

### SOAP-Endpunkte für Document Security-Dokumente deaktivieren {#disable-soap-endpoints-for-document-security-documents}

Die folgenden Änderungen an der Datei &quot;config.xml&quot;, um SOAP-Endpunkte für Document Security-Dokumente zu deaktivieren.

1. Exportieren Sie die Document Security-Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).
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

1. Speichern Sie die `config.xml`.
1. Importieren Sie die Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).

### Erhöhen der Skalierbarkeit des Document Security-Servers {#increasingscalability}

Standardmäßig rufen die Document Security-Clients beim Synchronisieren eines Dokuments für die Offline-Verwendung zusammen mit den Informationen für das aktuelle Dokument Richtlinien, Wasserzeichen, Lizenzen und Sperren ab, um Informationen für alle anderen Dokumente zu aktualisieren, auf die der Benutzer Zugriff hat. Wenn diese Aktualisierungen und Informationen nicht mit dem Client synchronisiert werden, kann ein im Offlinemodus geöffnetes Dokument weiterhin mit älteren Richtlinien, Wasserzeichen und Sperrinformationen geöffnet werden.

Sie können die Skalierbarkeit des Document Security-Servers erhöhen, indem Sie die an den Client gesendeten Informationen einschränken. Die Reduzierung der an den Client gesendeten Informationen führt zu einer verbesserten Skalierbarkeit, kürzeren Reaktionszeiten und einer besseren Leistung des Servers. Führen Sie die folgenden Schritte aus, um die Skalierbarkeit zu erhöhen:

1. Exportieren Sie die Document Security-Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).
1. Öffnen Sie die Konfigurationsdatei in einem Editor und suchen Sie den Knoten ServerSettings.
1. Legen Sie im Knoten „ServerSettings“ den Wert der Eigentschaft `DisableGlobalOfflineSynchronizationData` auf `true` fest.

   `<entry key="DisableGlobalOfflineSynchronizationData" value="true"/>`

   Bei dem Wert „true“ sendet der Document Security-Server Informationen nur für das aktuelle Dokument und Informationen für die übrigen Dokumente (die übrigen Dokumente, auf die ein Benutzer Zugriff hat) werden nicht an den Client gesendet.

   >[!NOTE]
   >
   >Standardmäßig wird der Wert des `DisableGlobalOfflineSynchronizationData`- -Schlüssels auf `false` festgelegt.

1. Speichern und importieren Sie die Konfigurationsdatei. (Siehe [Manuelles Bearbeiten der Document Security-Konfigurationsdatei](/help/forms/using/admin-help/configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).
