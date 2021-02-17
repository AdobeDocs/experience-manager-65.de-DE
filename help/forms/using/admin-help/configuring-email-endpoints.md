---
title: E-Mail-Endpunkte konfigurieren
seo-title: E-Mail-Endpunkte konfigurieren
description: Erfahren Sie, wie Sie E-Mail-Endpunkte konfigurieren.
seo-description: Erfahren Sie, wie Sie E-Mail-Endpunkte konfigurieren.
uuid: d47bb45b-0e0e-43ca-9e25-e347d0e60206
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: dcf15c42-9ec6-4d1c-ad41-083aa0b8c7ae
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f
workflow-type: tm+mt
source-wordcount: '3766'
ht-degree: 60%

---


# E-Mail-Endpunkte konfigurieren {#configuring-email-endpoints}

E-Mail-Endpunkte ermöglichen es einem Benutzer, einen Dienst durch Senden einer oder mehrerer Dokumente (als E-Mail-Anlage) an ein angegebenes E-Mail-Konto aufzurufen. Der E-Mail-Posteingang fungiert als Sammelpunkt für die Anlagen. Der Dienst überwacht den Posteingang und verarbeitet die Anlagen. Die Ergebnisse der Konvertierung werden an den Benutzer weitergeleitet, der im Endpunkt festgelegt ist.

Für einen E-Mail-Endpunkt können autorisierte Benutzer einen Prozess aufrufen, indem Dateien per E-Mail an das entsprechende Konto gesendet werden. Die Ergebnisse werden (standardmäßig) an den sendenden Benutzer oder den in den Endpunkteinstellungen angegebenen Benutzer zurückgegeben.

Bevor Sie einen E-Mail-Endpunkt konfigurieren, erstellen Sie ein POP3- oder IMAP-E-Mail-Konto, das mit dem Endpunkt verwendet werden soll. Richten Sie für jeden Konvertierungstyp ein eigenes Konto ein. Ein Konto kann beispielsweise zum Generieren standardmäßiger PDF-Dokumente aus eingehenden E-Mail-Anlagen konfiguriert werden, während ein anderes Konto zum Generieren geschützter PDF-Dokumente eingerichtet werden kann.

>[!NOTE]
>
>Jede E-Mail-Adresse darf nur einem E-Mail-Endpunkt zugeordnet sein. Es können nicht mehrere E-Mail-Endpunkte für eine einzelne E-Mail-Adresse konfiguriert werden, auch nicht, wenn die zusätzlichen E-Mail-Endpunkte deaktiviert sind.

Alle E-Mail-Endpunkte werden mit einem autorisierten Benutzernamen und Kennwort für den E-Mail-Posteingang konfiguriert. Diese Informationen müssen beim Aufrufen des Dienstes angegeben werden. Das E-Mail-Konto wird vom E-Mail-Serversystem geschützt, für das es konfiguriert ist.

Wenn Ihre Benutzer Dokumente mit westeuropäischen Sprachzeichen in Datei- und Konvertierungspfadnamen senden, müssen sie eine E-Mail-Anwendung verwenden, die die erforderlichen Kodierungstypen unterstützt (Latin1 [ISO-8859-1], Westeuropäisch [Windows] oder UTF-8). Weitere Informationen hierzu finden Sie im Dokument *Installieren und Bereitstellen von AEM Forms* für Ihren Anwendungsserver.

Bevor Sie einen E-Mail-Endpunkt konfigurieren, konfigurieren Sie den E-Mail-Dienst. (Siehe [Einstellungen für Standard-E-Mail-Endpunkte konfigurieren](configuring-email-endpoints.md#configure-default-email-endpoint-settings).) Die Konfigurationsparameter des E-Mail-Dienstes haben zwei Verwendungszwecke:

* Das Konfigurieren von Attributen, die für alle E-Mail-Endpunkte gültig sind
* Das Bereitstellen von Standardwerten für alle E-Mail-Endpunkte

## SSL für einen E-Mail-Endpunkt konfigurieren {#configure-ssl-for-an-email-endpoint}

Sie können POP3, IMAP bzw. SMTP zum Verwenden von Secure Sockets Layer (SSL) für einen E-Mail-Endpunkt konfigurieren.

1. Aktivieren Sie auf dem E-Mail-Server gemäß der Dokumentation des Herstellers SSL für POP3, IMAP bzw. SMTP.
1. Exportieren Sie ein Clientzertifikat vom E-Mail-Server.
1. Verwenden Sie das Programm Keytool, um die Datei mit dem Clientzertifikat in den Java Virtual Machine-Zertifikatspeicher (JVM) des Anwendungsservers zu importieren. Das hierfür verwendete Verfahren ist von den JVM- und Clientinstallationspfaden abhängig.

   Beispiel: Wenn Sie eine standardmäßige Oracle WebLogic Server-Installation mit JDK 1.5.0 unter Microsoft Windows Server® 2003 verwenden, geben Sie an einer Eingabeaufforderung den folgenden Text ein:

   `keytool -import -file client_certificate -alias myalias -keystore BEA_HOME\jdk150_04\jre\security\cacerts`

1. Geben Sie bei Aufforderung das Kennwort ein. (Für Java lautet das Standardkennwort `changeit`.) In einer Meldung wird angezeigt, dass das Zertifikat erfolgreich importiert wurde.
1. Verwenden Sie Administration Console, um dem Dienst den E-Mail-Endpunkt hinzuzufügen.
1. Erstellen Sie den E-Mail-Endpunkt in Administration Console. Aktivieren Sie beim Konfigurieren der Endpunkteinstellungen „POP3/IMAP SSL Enabled“ für eingehende Nachrichten und „SMTP SSL Enabled“ für ausgehende Nachrichten und ändern Sie die Anschlusseigenschaften entsprechend.

>[!NOTE]
>
>Tipp: Falls beim Einsatz von SSL Probleme auftreten, verwenden Sie einen E-Mail-Client wie Microsoft Outlook, um zu prüfen, ob dieser bei Verwendung von SSL auf den E-Mail-Server zugreifen kann. Wenn der E-Mail-Client nicht auf den E-Mail-Server zugreifen kann, liegt das Problem entweder bei der Konfiguration des Zertifikats oder des E-Mail-Servers vor.

## Einstellungen für Standard-E-Mail-Endpunkte konfigurieren  {#configure-default-email-endpoint-settings}

Auf der Seite „Dienstverwaltung“ können Sie die Attribute konfigurieren, die für alle E-Mail-Endpunkte gültig sind, und Standardwerte für alle E-Mail-Endpunkte bereitstellen.

Damit der Arbeitsablauf für Formulare eingehende E-Mail-Nachrichten von Benutzern empfängt und verarbeitet, müssen Sie einen E-Mail-Endpunkt für den CompleteTask-Dienst erstellen. Für diesen E-Mail-Endpunkt sind, wie unter [E-Mail-Endpunkte für den CompleteTask-Dienst erstellen](configuring-email-endpoints.md#create-an-email-endpoint-for-the-complete-task-service) beschrieben, zusätzliche Einstellungen erforderlich.

### Standardwerte für E-Mail-Endpunkte ändern  {#change-the-default-values-for-email-endpoints}

1. Klicken Sie in Administration Console auf „Dienste“ > „Anwendungen und Dienste“ > „Dienstverwaltung“.
1. Klicken Sie auf der Seite „Dienstverwaltung“ auf „E-Mail: 1.0“ (die Komponenten-ID lautet „com.adobe.idp.dsc.provider.service.email.Email“).
1. Geben Sie auf der Registerkarte „Konfiguration“ die Einstellungen für Standard-E-Mail-Endpunkte an und klicken Sie auf „Speichern“.

### Einstellungen für Standard-E-Mail-Endpunkte  {#default-email-endpoint-settings}

**Cron-Ausdruck:** Der Cron-Ausdruck, der von Quarz zum Planen der Abfrage des Eingabeordners verwendet wird.

**Wiederholungsintervall:** Gibt an, wie oft die Ordnerabfrage wiederholt wird. Der Standardwert für das Wiederholungsintervall in Sekunden, wenn in der Endpunktkonfiguration kein Wert angegeben ist. Der Standardwert ist 10. Dieser Wert kann nicht kleiner als „10“ sein.

**Anzahl der Wiederholungen:** Gibt an, wie oft der Eingabeordner abgerufen wird. Der Standardwert für die Anzahl der Wiederholungen, der verwendet wird, wenn in der Endpunktkonfiguration kein Wert angegeben ist. Ein Wert von „-1“ bedeutet uneingeschränktes Überprüfen des Ordners („unendlich“). Der Standardwert ist -1.

**Verzögerung bei Beginn von Aufträgen:** Der Standardwert in Sekunden, bis der Beginn den Endpunkt überprüft. Der Standardwert ist 0.

**Stapelgröße:** Die Anzahl der E-Mails, die der Empfänger pro Überprüfung verarbeitet, um eine optimale Leistung zu erzielen. Der Wert „-1“ bedeutet alle E-Mails. Der Standardwert ist 2. 

**Asynchron:** Identifiziert den Aufruftyp als asynchron oder synchron. Transiente und synchrone Prozesse können nur synchron aufgerufen werden. Der Standardwert ist „asynchron“.

**Domänenmuster:** Das Domänennamenmuster, das zum Filtern eingehender E-Mails verwendet wird. Wenn beispielsweise adobe.com verwendet wird, werden nur E-Mails aus der Domäne „adobe.com“ verarbeitet, während E-Mails aus anderen Domänen ignoriert werden.

**Dateimuster:** Die Muster für eingehende Dateianlagen, die vom Anbieter akzeptiert werden. Dazu gehören Dateien mit bestimmten Erweiterungen (&amp;ast;.dat, &amp;ast;.xml), bestimmten Ausdrücken (Daten) und Composite-Dateien mit Namen und Erweiterung (.[d][aA]&#39;port&#39;). Der Standardwert ist &amp;ast;.&amp;ast;.

**Empfänger des Erfolgsauftrags:** Eine oder mehrere E-Mail-Adressen, die zum Senden von E-Mails verwendet werden, um erfolgreiche Aufträge anzuzeigen. Standardmäßig wird eine Benachrichtigung über erfolgreiche Aufträge immer an den Absender des Ausgangsauftrags gesendet. Es werden bis zu 100 Empfänger unterstützt. Zum Deaktivieren dieser Einstellung lassen Sie das Feld unausgefüllt.

**Empfänger des fehlgeschlagenen Auftrags:** Eine oder mehrere E-Mail-Adressen, die zum Senden von E-Mails zur Anzeige fehlgeschlagener Aufträge verwendet werden. Standardmäßig wird eine Benachrichtigung über fehlgeschlagene Aufträge immer an den Absender des Ausgangsauftrags gesendet. Es werden bis zu 100 Empfänger unterstützt. Zum Deaktivieren dieser Einstellung lassen Sie das Feld unausgefüllt.

**Posteingangshost:** Der Hostname oder die IP-Adresse des Posteingangs, die vom E-Mail-Anbieter überprüft werden soll.

**Posteingangsanschluss:** Die Anschlussnummer des Posteingangs, die vom E-Mail-Anbieter überprüft werden soll. Wenn der Wert 0 ist, wird der IMAP- oder POP3-Standardanschluss verwendet.

**Posteingangsprotokoll:** Das E-Mail-Protokoll, das vom E-Mail-Endpunkt zum Überprüfen des Posteingangs verwendet wird. Die Optionen sind IMAP und POP3. Der Hostmailserver des Posteingangs muss diese Protokolle unterstützen.

**Zeitlimit für Posteingang:** Gibt an, wie lange der Endpunkt wartet, bevor er beim Versuch, eine Verbindung zum Posteingang herzustellen, abgebrochen wird. Wenn vor Erreichen des Zeitlimitwertes keine Verbindung hergestellt werden konnte, wird der Posteingang nicht abgefragt.

**Posteingangsbenutzer:** Der für die Anmeldung beim E-Mail-Konto erforderliche Benutzername. In Abhängigkeit vom E-Mail-Server und der Konfiguration kann dies nur der Benutzernamenteil der E-Mail-Adresse oder die vollständige E-Mail-Adresse sein.

**Posteingangskennwort:** Das Kennwort für den Posteingangsbenutzer.

**SSL für POP3/IMAP aktiviert:** Wenn diese Option aktiviert ist, wird SSL aktiviert.

**SMTP-Host:** Der Hostname des E-Mail-Servers, mit dem der E-Mail-Anbieter Ergebnisse und Fehlermeldungen sendet. Zum Beispiel mail.corp.example.com.

**SMTP-Anschluss:** Der Anschluss, über den eine Verbindung zum E-Mail-Server hergestellt wird. Der Standardwert ist 25. 

**SMTP-Benutzer:** Das Benutzerkonto, das vom E-Mail-Anbieter verwendet werden soll, wenn E-Mail-Nachrichten zu Ergebnissen und Fehlern gesendet werden.

**SMTP-Kennwort:** Das Kennwort für das SMTP-Konto. Einige E-Mail-Server benötigen kein SMTP-Kennwort.

**Senden von:** Die E-Mail-Adresse (z. B. user@company.com), an die E-Mail-Benachrichtigungen zu Ergebnissen und Fehlern gesendet werden. Wenn Sie keinen Wert für „Senden von“ angeben, versucht der E-Mail-Server, die E-Mail-Adresse zu ermitteln, indem der für die Einstellung „SMTP-Benutzer“ festgelegte Wert mit einer auf dem E-Mail-Server konfigurierten Standarddomäne kombiniert wird. Wenn auf dem E-Mail-Server keine Standarddomäne konfiguriert ist und Sie keinen Wert für „Senden von“ angeben, können Fehler auftreten. Geben Sie daher einen Wert für die Einstellung „Senden von“ an, um sicherzustellen, dass die E-Mail-Nachrichten eine korrekte von-Adresse aufweisen.

**SSL für SMTP aktiviert:** Wenn diese Option aktiviert ist, wird SSL über SMTP aktiviert.

**Include The Original Email Body As An Attachment:** Standardmäßig wird beim Senden einer E-Mail an den Formularserver der Originaltext der Nachricht im Nachrichtentext eingefügt. Um den Text stattdessen als Anhang einzufügen, wählen Sie diese Option.

**Use The Original Subject Line for Result Emails:** Standardmäßig verwendet der Forms-Server beim Senden von Ergebnis-E-Mail-Nachrichten die in den Einstellungen Success Email Subject und Error Email Subject angegebenen Werte als Betreffzeile. Wenn Sie stattdessen dieselbe Betreffzeile wie in der ursprünglichen E-Mail, die an den Server gesendet wurde, verwenden möchten, wählen Sie diese Option.

**Success Email Subject:** Nachdem Sie eine E-Mail an einen E-Mail-Endpunkt an den Beginn gesendet oder einen Vorgang fortgesetzt haben, erhalten Sie eine E-Mail vom AEM forms-Server. Wenn Ihre E-Mail erfolgreich gesendet wird, erhalten Sie eine Erfolgs-E-Mail. Wenn das Senden Ihrer E-Mail fehlschlägt, erhalten Sie eine Fehler-E-Mail, die Sie über den Fehler informiert. Mit dieser Einstellung können Sie die Betreffzeile von Erfolgs-E-Mails, die an diesen Endpunkt gesendet werden, angeben.

**Erfolgs-E-Mail-Textkörper:** Hiermit können Sie den Haupttext der Erfolgs-E-Mail-Nachrichten angeben, die an diesen Endpunkt gesendet werden.

**Fehler-E-Mail-Betreff-Präfix:** Hiermit können Sie den Text angeben, der am Anfang der Betreffzeile der für diesen Endpunkt gesendeten Fehlermeldungen verwendet wird.

**Fehler-E-Mail-Betreff:** Ermöglicht die Angabe der Betreffzeile der für diesen Endpunkt gesendeten Fehler-E-Mail-Nachrichten. Dieser Text wird nach dem Präfix des Fehler-E-Mail-Betreffs angezeigt.

**Fehler-E-Mail-Textkörper:** Ermöglicht die Angabe der ersten Zeile im Textkörper der für diesen Endpunkt gesendeten Fehler-E-Mail-Nachrichten.

**E-Mail-Übersichtsinformationen:** Jede Erfolgs- oder Fehlermeldung enthält einen Abschnitt mit dem ursprünglichen E-Mail-Text, den Sie an den Formularserver gesendet haben. Diese Einstellung legt den Text fest, der oberhalb dieses Abschnitts angezeigt wird.

**Posteingang vor dem Erstellen/Aktualisieren dieses Endpunkts überprüfen:** Wenn diese Option aktiviert ist, prüft der Formularserver, ob Ihre SMTP/POP3-Einstellungen korrekt sind, bevor der Endpunkt erstellt wird. Wenn Sie auf „Hinzufügen“ klicken, wird angezeigt, ob das Posteingangskonto gültig ist. Wenn diese Option nicht ausgewählt ist, erstellt der AEM Forms-Server den Endpunkt, ohne den Posteingang zu überprüfen.

**Zeichensatzkodierung:** Das für die E-Mail-Nachricht zu verwendende Kodierungsformat. Der Standardwert ist UTF-8, der von den meisten Benutzern außerhalb von Japan benutzt wird. Benutzer in japanischen Umgebungen wählen eher ISO2022-JP.

**Fehlgeschlagener E-Mail-Versand-Ordner:** Gibt einen Ordner an, in dem Ergebnisse gespeichert werden, wenn der SMTP-E-Mail-Server nicht betriebsbereit ist.

## E-Mail-Endpunkteinstellungen {#email-endpoint-settings}

Mithilfe der folgenden Einstellungen können Sie einen E-Mail-Endpunkt konfigurieren.

**Name:** Eine obligatorische Einstellung, die den Endpunkt identifiziert. Der Name darf kein &lt;-Zeichen enthalten, weil dadurch die Anzeige des Namens in Workspace abgeschnitten wird. Wenn Sie eine URL als Name des Endpunktes angeben, vergewissern Sie sich, dass sie den in RFC1738 angegebenen Syntaxregeln entspricht.

**Beschreibung:** Eine Beschreibung des Endpunkts. Der Name darf kein &lt;-Zeichen enthalten, weil dadurch die Anzeige des Namens in Workspace abgeschnitten wird.

**Cron-Ausdruck:** Geben Sie einen Cron-Ausdruck ein, wenn die E-Mail mit einem Cron-Ausdruck geplant werden muss.

**Anzahl der Wiederholungen:** Gibt an, wie oft der E-Mail-Endpunkt den Ordner oder das Verzeichnis überprüft. Der Wert „-1“ bedeutet uneingeschränktes Überprüfen („unendlich“). Der Standardwert ist -1.

**Wiederholungsintervall:** Die Scanrate, mit der der Empfänger nach eingehenden Nachrichten sucht.

**Verzögern Sie den Beginn des Auftrags:** Die Wartezeit bis zum Scannen nach den Beginn der Planung.

**Stapelgröße:** Die Anzahl der E-Mails, die der Empfänger pro Überprüfung verarbeitet, um eine optimale Leistung zu erzielen. Der Wert „-1“ bedeutet alle E-Mails. Der Standardwert ist 2. 

**Benutzername:** Eine obligatorische Einstellung, bei der es sich um den Benutzernamen handelt, der beim Aufrufen eines E-Mail-Zielgruppe-Dienstes verwendet wird. Der Standardwert ist „SuperAdmin“.

**Domänenname:** Eine obligatorische Einstellung, bei der es sich um die Domäne des Benutzers handelt. Der Standardwert ist „DefaultDom“.

**Domänenmuster:** Gibt die Domänenmuster für eingehende E-Mails an, die vom Anbieter akzeptiert werden. Wenn beispielsweise „adobe.com“ verwendet wird, werden nur E-Mails aus der Domäne „adobe.com“ verarbeitet, während E-Mails aus anderen Domänen ignoriert werden.

**Dateimuster:** Gibt die Muster für eingehende Dateianlagen an, die vom Anbieter akzeptiert werden. Dazu gehören Dateien mit bestimmten Erweiterungen (&amp;ast;.dat, &amp;ast;.xml), bestimmten Ausdrücken (Daten) oder zusammengesetzten Namen in Name und Erweiterung (&amp;ast;..[d][aA]&#39;port&#39;).

**Empfänger des erfolgreichen Auftrags:** Eine E-Mail-Adresse, an die Benachrichtigungen über erfolgreiche Aufträge gesendet werden. Standardmäßig wird eine Benachrichtigung über erfolgreiche Aufträge immer an den Absender gesendet. Wenn Sie sender eingeben, werden E-Mail-Ergebnisse an den Absender gesendet. Es werden bis zu 100 Empfänger unterstützt. Geben Sie zusätzliche Empfänger mit durch Kommas (,) getrennte E-Mail-Adressen an.

Zum Deaktivieren dieser Einstellung lassen Sie sie unausgefüllt. Es kann Fälle geben, in denen Sie einen Prozess auslösen möchten, ohne ein Benachrichtigung per E-Mail zum Ergebnis erhalten zu wollen.

**Empfänger des fehlgeschlagenen Auftrags:** Eine E-Mail-Adresse, an die Benachrichtigungen über fehlgeschlagene Aufträge gesendet werden. Standardmäßig wird eine Benachrichtigung über Aufträge mit Fehlern immer an den Absender gesendet. Wenn Sie sender eingeben, werden E-Mail-Ergebnisse an den Absender gesendet. Es werden bis zu 100 Empfänger unterstützt. Geben Sie zusätzliche Empfänger mit durch Kommas (,) getrennte E-Mail-Adressen an.

Zum Deaktivieren dieser Einstellung lassen Sie sie unausgefüllt. Es kann Fälle geben, in denen Sie einen Prozess auslösen möchten, ohne ein Benachrichtigung per E-Mail zum Ergebnis erhalten zu wollen.

**Posteingangshost:** Der Hostname oder die IP-Adresse des Posteingangs, die vom E-Mail-Anbieter überprüft werden soll.

**Posteingangsanschluss:** Der Anschluss, den der E-Mail-Server verwendet. Der Standardwert ist für POP3 „110“ und für IMAP „143“. Ist SSL aktiviert, ist der Standardwert für POP3 „995“ und für IMAP „993“.

**Posteingangsprotokoll:** Das E-Mail-Protokoll, das vom E-Mail-Endpunkt zum Überprüfen des Posteingangs verwendet wird. Die Werte sind IMAP und POP3. Der Hostmailserver des Posteingangs muss diese Protokolle unterstützen.

**Zeitlimit für Posteingang:** Das Zeitlimit in Sekunden, das der E-Mail-Anbieter auf Posteingang-Antworten wartet.

**Posteingangsbenutzer:** Der Benutzername, der zum Anmelden beim E-Mail-Konto erforderlich ist. In Abhängigkeit vom E-Mail-Server und der Konfiguration kann dies nur der Benutzernamenteil der E-Mail-Adresse oder die vollständige E-Mail-Adresse sein.

**Posteingangskennwort:** Das Kennwort für den Posteingangsbenutzer.

**SSL für POP3/IMAP aktiviert:** Wählen Sie diese Einstellung, um den E-Mail-Anbieter zu zwingen, SSL zum Überprüfen des Posteingangs zu verwenden. Vergewissern Sie sich, dass Ihr E-Mail-Server SSL unterstützt.

**SMTP-Host:** Der Hostname des E-Mail-Servers, den der E-Mail-Anbieter zum Senden von Ergebnissen und Fehlermeldungen verwendet.

**SMTP-Anschluss:** Der Standardwert für den SMTP-Anschluss ist 25.

**SMTP-Benutzer:** Das Benutzerkonto, das vom E-Mail-Anbieter verwendet werden soll, wenn E-Mail-Benachrichtigungen zu Ergebnissen und Fehlern gesendet werden.

**SMTP-Kennwort:** Das Kennwort für das SMTP-Konto. Einige E-Mail-Server benötigen kein SMTP-Kennwort.

**Senden von:** Die E-Mail-Adresse (z. B. user@company.com), an die E-Mail-Benachrichtigungen zu Ergebnissen und Fehlern gesendet werden. Wenn Sie keinen Wert für „Senden von“ angeben, versucht der E-Mail-Server, die E-Mail-Adresse zu ermitteln, indem der für die Einstellung „SMTP-Benutzer“ festgelegte Wert mit einer auf dem E-Mail-Server konfigurierten Standarddomäne kombiniert wird. Wenn auf dem E-Mail-Server keine Standarddomäne konfiguriert ist und Sie keinen Wert für „Senden von“ angeben, können Fehler auftreten. Geben Sie daher einen Wert für die Einstellung „Senden von“ an, um sicherzustellen, dass die E-Mail-Nachrichten eine korrekte von-Adresse aufweisen.

**SSL für SMTP aktiviert:** Wählen Sie diese Einstellung, um den E-Mail-Anbieter zu zwingen, SSL zum Überprüfen des Posteingangs zu verwenden. Vergewissern Sie sich, dass Ihr E-Mail-Server SSL unterstützt.

**Fehlgeschlagener E-Mail-Versand-Ordner:** Gibt einen Ordner an, in dem Ergebnisse gespeichert werden, wenn der SMTP-E-Mail-Server nicht betriebsbereit ist.

**asynchron:** Wenn &quot;synchron&quot;festgelegt ist, werden alle Eingabedateien verarbeitet und eine einzige Antwort zurückgegeben. Bei Festlegung auf „asynchron“ wird für jedes verarbeitete Dokument eine Antwort gesendet.

Beispielsweise wird für einen Dienst ein E-Mail-Endpunkt erstellt, der ein einzelnes Word-Dokument akzeptiert und das Dokument als PDF-Datei zurückgibt. An den Posteingang des Endpunktes kann eine E-Mail gesendet werden, die mehrere (3) Word-Dokumente enthält. Wenn nach der Verarbeitung aller drei Dokumente der Endpunkt als „synchron“ konfiguriert wird, wird eine E-Mail-Antwort mit allen drei Dokumenten als Anlage gesendet. Ist der Endpunkt aber „asynchron“, wird nach der Konvertierung jedes Word-Dokuments in PDF eine E-Mail-Antwort gesendet. Das heißt also, dass drei E-Mails mit jeweils einem einzelnen PDF-Anhang gesendet werden.

Der Standardwert ist „asynchron“.

**Den ursprünglichen E-Mail-Text als Anhang einschließen:** Standardmäßig wird beim Senden einer E-Mail an den Formularserver der ursprüngliche Text der Nachricht im Nachrichtentext eingefügt. Um den Text stattdessen als Anhang einzufügen, wählen Sie diese Option.

**Verwenden Sie die ursprüngliche Betreffzeile für Ergebnis-E-Mails:** Standardmäßig verwendet der Forms-Server beim Senden von Ergebnis-E-Mail-Nachrichten die in den Einstellungen &quot;Success Email Subject&quot;und &quot;Error Email Subject&quot;angegebenen Werte als Betreffzeile. Wenn Sie stattdessen dieselbe Betreffzeile wie in der ursprünglichen E-Mail, die an den Server gesendet wurde, verwenden möchten, wählen Sie diese Option.

**Success Email Subject:** Nachdem Sie eine E-Mail an einen E-Mail-Endpunkt an den Beginn gesendet oder einen Vorgang fortgesetzt haben, erhalten Sie eine E-Mail vom AEM forms-Server. Wenn Ihre E-Mail erfolgreich gesendet wird, erhalten Sie eine Erfolgs-E-Mail. Wenn das Senden Ihrer E-Mail fehlschlägt, erhalten Sie eine Fehler-E-Mail, die Sie über den Fehler informiert. Mit dieser Einstellung können Sie die Betreffzeile von Erfolgs-E-Mails, die an diesen Endpunkt gesendet werden, angeben.

**Erfolgs-E-Mail-Textkörper:** Hiermit können Sie den Haupttext der Erfolgs-E-Mail-Nachrichten angeben, die an diesen Endpunkt gesendet werden.

**Fehler-E-Mail-Betreff-Präfix:** Hiermit können Sie den Text angeben, der am Anfang der Betreffzeile der für diesen Endpunkt gesendeten Fehlermeldungen verwendet wird.

**Fehler-E-Mail-Betreff:** Ermöglicht die Angabe der Betreffzeile der für diesen Endpunkt gesendeten Fehler-E-Mail-Nachrichten. Dieser Text wird nach dem Präfix des Fehler-E-Mail-Betreffs angezeigt.

**Fehler-E-Mail-Textkörper:** Ermöglicht die Angabe der ersten Zeile im Textkörper der für diesen Endpunkt gesendeten Fehler-E-Mail-Nachrichten.

**E-Mail-Übersichtsinformationen:** Jede Erfolgs- oder Fehlermeldung enthält einen Abschnitt mit dem ursprünglichen E-Mail-Text, den Sie an den Formularserver gesendet haben. Diese Einstellung legt den Text fest, der oberhalb dieses Abschnitts angezeigt wird.

**Validieren des Posteingangs vor dem Erstellen/Aktualisieren dieses Endpunkts:** Wenn diese Option ausgewählt ist, prüft der Formularserver, ob Ihre SMTP/POP3-Einstellungen korrekt sind, bevor der Endpunkt erstellt wird. Wenn Sie auf „Hinzufügen“ klicken, wird angezeigt, ob das Posteingangskonto gültig ist. Wenn diese Option nicht ausgewählt ist, erstellt der AEM Forms-Server den Endpunkt, ohne den Posteingang zu überprüfen.

**Vorgangsname:** Diese Einstellung ist obligatorisch. Eine Liste von Vorgängen, die dem E-Mail-Endpunkt zugewiesen werden können. Der Vorgang, den Sie hier auswählen, bestimmt, welche Felder in den Abschnitten „Zuordnungen von Eingabeparametern“ und „Zuordnungen von Ausgabeparametern“ angezeigt werden.

**Zuordnungen von Eingabeparametern:** Dient zum Konfigurieren der Eingabe, die für die Verarbeitung des Dienstes und Vorgangs erforderlich ist. Die beiden Eingabetypen sind „Literal“ und „Variable“.

**Literal:** Die E-Mail verwendet den Wert, der in das Feld eingegeben wird, wie er angezeigt wird.

**Variable:** Sie können eine Zeichenfolge aus dem E-Mail-Betreff, dem Text, der Kopfzeile oder der E-Mail-Adresse des Absenders zuordnen. Dazu verwenden Sie eines der folgenden Schlüsselwörter: %SUBJECT%, %BODY%, %HEADER% oder %SENDER%. Wenn Sie z. B. %SUBJECT%, angeben, wird der Inhalt des E-Mail-Betreffs als Eingabeparameter verwendet. Zum Auswählen von Anhängen geben Sie ein Dateimuster ein, das vom E-Mail-Endpunkt zum Auswählen der angehängten Dokumente verwendet werden kann. Wenn Sie beispielsweise &amp;ast;.pdf eingeben, werden alle angehängten Dokumente mit der Dateierweiterung .pdf ausgewählt. Eingabe &amp;ast; wählt angehängtes Dokument aus. Durch die Eingabe von example.pdf werden alle angehängten Dokumente namens „example.pdf“ ausgewählt.

**Zuordnungen von Ausgabeparametern:** Dient zum Konfigurieren der Ausgabe des Dienstes und Vorgangs. Die folgenden Zeichen in den Zuordnungswerten von Ausgabeparametern werden im Dateinamen des Anhangs erweitert:

**%** FRestellt den Dateinamen der Quelldatei dar (ohne Erweiterung).

**%** ERstellt die Erweiterung der Quelldatei dar.

Alle Vorkommen von \ (Backslash) werden durch %% ersetzt.

***Hinweis **: Wenn die Dienstanforderungsnachricht mehrere Dateianhänge enthält, können die Parameter „%F“ und „%E“ nicht für die Eigenschaft „Zuordnungen von Ausgabeparametern“ des Endpunkts verwendet werden. Wenn die Dienstantwort mehrere Dateianhänge zurückgibt, können Sie nicht denselben Dateinamen für mehr als eine Anlage angeben. Wenn Sie diese Empfehlungen nicht befolgen, werden die Namen für die zurückgegebenen Dateien vom aufgerufenen Dienst erstellt, und die Namen sind nicht vorhersehbar.*

Die folgenden Werte sind verfügbar:

**Einzelobjekt:** Der E-Mail-Anbieter hat nicht das Ziel des Quellordners; Ergebnisse werden als Anlagen zurückgegeben. Das Muster ist Result/%F.ps und gibt Result%%sourcefilename.ps als Dateinamenanhang zurück.

**Liste:** Das Muster lautet Result/%F/ und gibt Result%%sourcefilename%%file1 als Dateinamenanhang zurück.

**Zuordnung:** Das Muster lautet Result/%F/ und das Quellziel lautet Result%%sourcefilename%%file1 und Result%%sourcefilename%%file2. Wenn die Zuordnung mehr als ein Objekt enthält und das Muster Result/%F.ps ist, sind die Antwortdateianhänge Result%%Quelldateiname1.ps (Ausgabe 1) und Result%%Quelldateiname2.ps (Ausgabe 2).

## E-Mail-Endpunkt für den Complete Task-Dienst erstellen {#create-an-email-endpoint-for-the-complete-task-service}

Damit der Arbeitsablauf für Formulare eingehende E-Mail-Nachrichten von Benutzern empfängt und verarbeitet, müssen Sie einen E-Mail-Endpunkt für den CompleteTask-Dienst erstellen. 

1. Klicken Sie in Administration Console auf „Dienste“ > „Anwendungen und Dienste“ > „Dienstverwaltung“.
1. Klicken Sie auf der Seite „Dienstverwaltung“ auf den Dienst „Complete Task“.
1. Wählen Sie auf der Registerkarte „Endpunkte“ in der Dropdown-Liste „E-Mail“ aus und klicken Sie auf „Hinzufügen“.
1. Geben Sie in das Feld „Posteingangshost“ den Hostnamen oder die IP-Adresse des E-Mail-Servers ein.
1. Geben Sie in das Feld „Posteingangsbenutzer“ den Benutzernamen ein, der für die Anmeldung bei dem E-Mail-Konto, das Sie für die Verarbeitung von gesendeten Formularen erstellt haben, erforderlich ist. In Abhängigkeit vom E-Mail-Server und der Konfiguration kann dies nur der Benutzernamenteil der E-Mail-Adresse oder die vollständige E-Mail-Adresse sein.
1. Geben Sie in das Feld „Posteingangskennwort“ das Kennwort für den Posteingangsbenutzer ein.
1. Geben Sie in das Feld „SMTP-Host“ den Hostnamen oder die IP-Adresse des E-Mail-Servers ein, von dem aus der E-Mail-Anbieter Ergebnisse und Fehlermeldungen sendet.
1. Geben Sie in das Feld „SMTP-Benutzer“ das Benutzerkonto ein, das vom E-Mail-Anbieter verwendet werden soll, wenn ausgehende E-Mails mit Ergebnissen und Fehlermeldungen versendet werden. Dieses Benutzerkonto kann mit dem für Posteingangsbenutzer verwendeten Wert identisch sein.
1. Geben Sie in das Feld „SMTP-Kennwort“ das Kennwort für das SMTP-Konto ein.
1. Wählen Sie in der Liste „Vorgangsname“ den Eintrag „Invoke“.
1. Wählen Sie in der Liste &quot;attachmentMap&quot;die Option Variable und geben Sie im Feld daneben `*.*` ein. Hierdurch werden alle Anhänge eingehender E-Mails an eine Zuordnungsvariable (map) für den CompleteTask-Prozess gesendet.
1. Wählen Sie in der Liste mailBody die Variable und geben Sie im Feld daneben `%BODY%` ein.
1. Wählen Sie in der Liste mailFrom die Option Variable und geben Sie im Feld daneben `%SENDER%` ein. Hierdurch wird die Absenderadresse den CompleteTask-Prozessdaten zugeordnet.
1. Geben Sie in das Feld „Ergebnisse“ den Wert `results` ein. Hierdurch gibt der CompleteTask- oder Startprozess eine Ergebniszeichenfolge zurück.
1. Klicken Sie auf Hinzufügen.

