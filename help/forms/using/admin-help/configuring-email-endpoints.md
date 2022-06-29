---
title: E-Mail-Endpunkte konfigurieren
seo-title: Configuring email endpoints
description: Erfahren Sie, wie Sie E-Mail-Endpunkte konfigurieren.
seo-description: Learn how to configure email endpoints.
uuid: d47bb45b-0e0e-43ca-9e25-e347d0e60206
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: dcf15c42-9ec6-4d1c-ad41-083aa0b8c7ae
exl-id: 33583a12-4f20-4146-baa4-c9854e454bbf
source-git-commit: 1cdd15800548362ccdd9e70847d9df8ce93ee06e
workflow-type: ht
source-wordcount: '3757'
ht-degree: 100%

---

# E-Mail-Endpunkte konfigurieren {#configuring-email-endpoints}

E-Mail-Endpunkte ermöglichen es einem Benutzer, einen Dienst durch Senden einer oder mehrerer Dokumente (als E-Mail-Anlage) an ein angegebenes E-Mail-Konto aufzurufen. Der E-Mail-Posteingang fungiert als Sammelpunkt für die Anlagen. Der Dienst überwacht den Posteingang und verarbeitet die Anlagen. Die Ergebnisse der Konvertierung werden an den Benutzer weitergeleitet, der im Endpunkt festgelegt ist.

Für einen E-Mail-Endpunkt können autorisierte Benutzer einen Prozess aufrufen, indem Dateien per E-Mail an das entsprechende Konto gesendet werden. Die Ergebnisse werden (standardmäßig) an den sendenden Benutzer oder den in den Endpunkteinstellungen angegebenen Benutzer zurückgegeben.

Bevor Sie einen E-Mail-Endpunkt konfigurieren, erstellen Sie ein POP3- oder IMAP-E-Mail-Konto, das mit dem Endpunkt verwendet werden soll. Richten Sie für jeden Konvertierungstyp ein eigenes Konto ein. Ein Konto kann beispielsweise zum Generieren standardmäßiger PDF-Dokumente aus eingehenden E-Mail-Anlagen konfiguriert werden, während ein anderes Konto zum Generieren geschützter PDF-Dokumente eingerichtet werden kann.

>[!NOTE]
>
>Jede E-Mail-Adresse darf nur einem E-Mail-Endpunkt zugeordnet sein. Es können nicht mehrere E-Mail-Endpunkte für eine einzelne E-Mail-Adresse konfiguriert werden, auch nicht, wenn die zusätzlichen E-Mail-Endpunkte deaktiviert sind.

Alle E-Mail-Endpunkte werden mit einem autorisierten Benutzernamen und Kennwort für den E-Mail-Posteingang konfiguriert. Diese Informationen müssen beim Aufrufen des Dienstes angegeben werden. Das E-Mail-Konto wird vom E-Mail-Serversystem geschützt, für das es konfiguriert ist.

Wenn Benutzer Dokumente mit westeuropäischen Sprachzeichen in Datei- und Konvertierungspfadnamen senden, müssen Sie eine E-Mail-Anwendung einsetzen, welche die erforderlichen Kodierungstypen (Latin1 [ISO-8859-1], Westeuropäisch [Windows] oder UTF-8) unterstützt. Weitere Informationen hierzu finden Sie im Dokument *Installieren und Bereitstellen von AEM Forms* für Ihren Anwendungsserver.

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

1. Geben Sie das Kennwort ein, wenn Sie dazu aufgefordert werden (für Java lautet das Standardkennwort `changeit`). In einer Meldung wird angezeigt, dass das Zertifikat erfolgreich importiert wurde.
1. Verwenden Sie Administration Console, um dem Dienst den E-Mail-Endpunkt hinzuzufügen.
1. Erstellen Sie den E-Mail-Endpunkt in Administration Console. Aktivieren Sie beim Konfigurieren der Endpunkteinstellungen „POP3/IMAP SSL Enabled“ für eingehende Nachrichten und „SMTP SSL Enabled“ für ausgehende Nachrichten und ändern Sie die Anschlusseigenschaften entsprechend.

>[!NOTE]
>
>Tipp: Falls beim Einsatz von SSL Probleme auftreten, verwenden Sie einen E-Mail-Client wie Microsoft Outlook, um zu prüfen, ob dieser bei Verwendung von SSL auf den E-Mail-Server zugreifen kann. Wenn der E-Mail-Client nicht auf den E-Mail-Server zugreifen kann, liegt das Problem entweder bei der Konfiguration des Zertifikats oder des E-Mail-Servers vor.

## Einstellungen für Standard-E-Mail-Endpunkte konfigurieren {#configure-default-email-endpoint-settings}

Auf der Seite „Dienstverwaltung“ können Sie die Attribute konfigurieren, die für alle E-Mail-Endpunkte gültig sind, und Standardwerte für alle E-Mail-Endpunkte bereitstellen.

Damit der Arbeitsablauf für Formulare eingehende E-Mail-Nachrichten von Benutzern empfängt und verarbeitet, müssen Sie einen E-Mail-Endpunkt für den CompleteTask-Dienst erstellen. Für diesen E-Mail-Endpunkt sind, wie unter [E-Mail-Endpunkte für den CompleteTask-Dienst erstellen](configuring-email-endpoints.md#create-an-email-endpoint-for-the-complete-task-service) beschrieben, zusätzliche Einstellungen erforderlich.

### Standardwerte für E-Mail-Endpunkte ändern {#change-the-default-values-for-email-endpoints}

1. Klicken Sie in Administration Console auf „Dienste“ > „Anwendungen und Dienste“ > „Dienstverwaltung“.
1. Klicken Sie auf der Seite „Dienstverwaltung“ auf „E-Mail: 1.0“ (die Komponenten-ID lautet „com.adobe.idp.dsc.provider.service.email.Email“).
1. Geben Sie auf der Registerkarte „Konfiguration“ die Einstellungen für Standard-E-Mail-Endpunkte an und klicken Sie auf „Speichern“.

### Einstellungen für Standard-E-Mail-Endpunkte {#default-email-endpoint-settings}

**Cron-Ausdruck:** Der Cron-Ausdruck, wie er von Quartz zur zeitlichen Planung des Abrufs des Eingabeordners verwendet wird.

**Wiederholungsintervall:** Die Häufigkeit, mit der der Ordner abgerufen wird. Der Standardwert für das Wiederholungsintervall in Sekunden, wenn in der Endpunktkonfiguration kein Wert angegeben ist. Der Standardwert ist 10. Dieser Wert kann nicht kleiner als „10“ sein.

**Anzahl der Wiederholungen:** Wie oft das Eingabeverzeichnis abgefragt wird. Der Standardwert für die Anzahl der Wiederholungen, der verwendet wird, wenn in der Endpunktkonfiguration kein Wert angegeben ist. Ein Wert von „-1“ bedeutet uneingeschränktes Überprüfen des Ordners („unendlich“). Der Standardwert lautet -1.

**Start des Auftrags verzögern:** Der Standardwert in Sekunden für die Verzögerung, bevor der Auftrag beginnt, den Endpunkt zu überprüfen. Der Standardwert lautet 0.

**Batch-Größe:** Die Anzahl der E-Mails, die der Empfänger pro Überprüfung zur Optimierung der Leistung verarbeitet. Der Wert „-1“ bedeutet alle E-Mails. Der Standardwert lautet 2.

**Asynchron:** Gibt den Aufruftyp als asynchron oder synchron an. Transiente und synchrone Prozesse können nur synchron aufgerufen werden. Der Standardwert lautet „asynchron“.

**Domain-Muster:** Das Domain-Namensmuster, das zum Filtern eingehender E-Mails verwendet wird. Wenn beispielsweise adobe.com verwendet wird, werden nur E-Mails aus der Domain „adobe.com“ verarbeitet, während E-Mails aus anderen Domains ignoriert werden.

**Dateimuster:** Gibt die Muster für eingehende Dateianhänge an, die vom Anbieter akzeptiert werden. Hierzu gehören Dateien mit bestimmten Erweiterungen (&amp;ast;.dat, &amp;ast;.xml), Dateien mit bestimmten Namen (data) sowie Dateien mit zusammengesetzten Ausdrücken im Namen und in der Erweiterung (.[dD][aA]&#39;port&#39;). Der Standardwert lautet &amp;ast;.&amp;ast;.

**Empfänger erfolgreicher Aufträge:** Eine oder mehrere E-Mail-Adressen, an die Benachrichtigungen über erfolgreiche Aufträge per E-Mail gesendet werden. Standardmäßig wird eine Benachrichtigung über erfolgreiche Aufträge immer an den Absender des Ausgangsauftrags gesendet. Es werden bis zu 100 Empfänger unterstützt. Zum Deaktivieren dieser Einstellung lassen Sie das Feld unausgefüllt.

**Empfänger fehlgeschlagener Aufträge:** Eine oder mehrere E-Mail-Adressen, an die Benachrichtigungen über fehlgeschlagene Aufträge per E-Mail gesendet werden. Standardmäßig wird eine Benachrichtigung über fehlgeschlagene Aufträge immer an den Absender des Ausgangsauftrags gesendet. Es werden bis zu 100 Empfänger unterstützt. Zum Deaktivieren dieser Einstellung lassen Sie das Feld unausgefüllt.

**Posteingang - Host:** Der Host-Name oder die IP-Adresse für den Posteingang, der/die vom E-Mail-Anbieter überprüft werden soll.

**Posteingang - Port:** Die Port-Nummer für den Posteingang, die vom E-Mail-Anbieter überprüft werden soll. Wenn der Wert 0 ist, wird der IMAP- oder POP3-Standard-Port verwendet.

**Posteingang - Protokoll:** Das E-Mail-Protokoll, das vom E-Mail-Endpunkt zum Überprüfen des Posteingangs verwendet werden soll. Die Optionen sind IMAP und POP3. Der Hostmailserver des Posteingangs muss diese Protokolle unterstützen.

**Posteingang - Zeitüberschreitung:** Gibt den Zeitraum an, den der Endpunkt beim Herstellen einer Verbindung mit dem Posteingang wartet, bevor der Vorgang abgebrochen wird. Wenn vor Erreichen des Zeitüberschreitungswerts keine Verbindung hergestellt werden konnte, wird der Posteingang nicht abgefragt.

**Posteingang - Benutzer:** Der Benutzername, der zum Anmelden beim E-Mail-Konto erforderlich ist. Je nach E-Mail-Server und Konfiguration kann dies nur der in der E-Mail-Adresse enthaltene Benutzername oder die vollständige E-Mail-Adresse sein.

**Posteingang - Kennwort:** Das Kennwort für den Posteingangsbenutzer.

**POP3/IMAP SSL aktiviert:** Durch Auswahl diese Option wird SSL aktiviert.

**SMTP-Host:** Der Host-Name des E-Mail-Servers, den der E-Mail-Anbieter zum Senden von Ergebnissen und Fehlermeldungen verwendet. Beispiel: mail.example.com.

**SMTP-Port**: Der Port, über den die Verbindung zum Mail-Server hergestellt wird. Der Standardwert ist 25.

**SMTP-Benutzer:** Das Benutzerkonto, das vom E-Mail-Anbieter zum Senden ausgehender E-Mails mit Ergebnissen und Fehlermeldungen verwendet werden soll.

**SMTP-Kennwort:** Das Kennwort für das SMTP-Konto. Einige E-Mail-Server benötigen kein SMTP-Kennwort.

**Senden von:** Die E-Mail-Adresse (z. B. benutzer@firma.com), die zum Senden von E-Mail-Benachrichtigungen zu Ergebnissen und Fehlern verwendet wird. Wenn Sie keinen Wert für „Senden von“ angeben, versucht der E-Mail-Server, die E-Mail-Adresse zu ermitteln, indem der für die Einstellung „SMTP-Benutzer“ festgelegte Wert mit einer auf dem E-Mail-Server konfigurierten Standard-Domain kombiniert wird. Wenn auf dem E-Mail-Server keine Standard-Domain konfiguriert ist und Sie keinen Wert für „Senden von“ angeben, können Fehler auftreten. Geben Sie daher einen Wert für die Einstellung „Senden von“ an, um sicherzustellen, dass die E-Mail-Nachrichten eine korrekte Absenderadresse haben.

**SMTP SSL aktiviert:** Durch Auswahl dieser Option wird SSL über SMTP aktiviert.

**Ursprüngliche E-Mail-Nachricht als Anhang aufnehmen:** Wenn Sie eine E-Mail an den Formular-Server senden, wird standardmäßig der ursprüngliche Text der Nachricht in das Textfeld der E-Mail eingefügt. Wählen Sie diese Option, um den Text stattdessen als Anhang beizufügen.

**Ursprüngliche Betreffzeile für Ergebnis-E-Mails verwenden:** Standardmäßig verwendet der Formular-Server die Werte, die in den Einstellungen „Betreff für Erfolgs-E-Mails“ und „Betreff für Fehler-E-Mails“ als Betreffzeile angegeben wurden, wenn E-Mail-Nachrichten zu Ergebnissen gesendet werden. Wenn Sie stattdessen dieselbe Betreffzeile wie in der ursprünglichen E-Mail, die an den Server gesendet wurde, verwenden möchten, wählen Sie diese Option.

**Betreff für Erfolgs-E-Mails:** Nachdem Sie eine E-Mail an einen E-Mail-Endpunkt gesendet haben, um einen Prozess zu beginnen oder fortzusetzen, erhalten Sie vom AEM Forms-Server eine E-Mail-Nachricht mit einer Antwort. Wenn Ihre E-Mail erfolgreich gesendet wird, erhalten Sie eine Erfolgs-E-Mail. Wenn das Senden Ihrer E-Mail fehlschlägt, erhalten Sie eine Fehler-E-Mail, die Sie über den Fehler informiert. Mit dieser Einstellung können Sie die Betreffzeile von Erfolgs-E-Mails, die an diesen Endpunkt gesendet werden, angeben.

**Nachricht für Erfolgs-E-Mails:** Mit dieser Option können Sie den Text der E-Mail-Nachrichten zu Erfolgen angeben, die an diesen Endpunkt gesendet werden.

**Betreffpräfix für Fehler-E-Mails:** Mit dieser Option können Sie den Text am Anfang der Betreffzeile von E-Mail-Nachrichten zu Fehlern angeben, die an diesen Endpunkt gesendet werden.

**Betreff für Fehler-E-Mails:** Mit dieser Option können Sie die Betreffzeile von E-Mail-Nachrichten zu Fehlern angeben, die an diesen Endpunkt gesendet werden. Dieser Text wird nach dem Präfix des Fehler-E-Mail-Betreffs angezeigt.

**Nachricht für Fehler-E-Mails:** Mit dieser Option können Sie die erste Zeile im Nachrichtentext von Fehler-E-Mails angeben, die an diesen Endpunkt gesendet werden.

**E-Mail-Zusammenfassungsinfo:** Jede Erfolgs- oder Fehlernachricht enthält einen Abschnitt mit dem ursprünglichen E-Mail-Text, den Sie an den Formular-Server gesendet haben. Diese Einstellung legt den Text fest, der oberhalb dieses Abschnitts angezeigt wird.

**Posteingang validieren, bevor dieser Endpunkt erstellt/aktualisiert wird:** Wenn diese Option ausgewählt ist, prüft der Formular-Server, ob Ihre SMTP/POP3-Einstellungen korrekt sind, bevor der Endpunkt erstellt wird. Wenn Sie auf „Hinzufügen“ klicken, wird angezeigt, ob das Posteingangskonto gültig ist. Wenn diese Option nicht ausgewählt ist, erstellt der AEM Forms-Server den Endpunkt, ohne den Posteingang zu überprüfen.

**Zeichensatzkodierung:** Das für die E-Mail-Nachricht zu verwendende Kodierungsformat. Der Standardwert ist UTF-8, der von den meisten Benutzern außerhalb von Japan benutzt wird. Benutzer in japanischen Umgebungen wählen eher ISO2022-JP.

**Ordner für Fehler beim Senden von E-Mails:** Gibt einen Ordner an, in dem Ergebnisse gespeichert werden, falls der SMTP-Mail-Server nicht betriebsbereit ist.

## E-Mail-Endpunkteinstellungen {#email-endpoint-settings}

Mithilfe der folgenden Einstellungen können Sie einen E-Mail-Endpunkt konfigurieren.

**Name:** Eine obligatorische Angabe zum Identifizieren des Endpunktes. Der Name darf kein &lt;-Zeichen enthalten, weil dadurch die Anzeige des Namens in Workspace abgeschnitten wird. Wenn Sie eine URL als Name des Endpunktes angeben, vergewissern Sie sich, dass sie den in RFC1738 angegebenen Syntaxregeln entspricht.

**Beschreibung:** Eine Beschreibung des Endpunktes. Sie darf kein &lt;-Zeichen enthalten, weil dadurch die Anzeige der Beschreibung in Workspace abgeschnitten wird.

**Cron-Ausdruck:** Geben Sie einen Cron-Ausdruck ein, wenn die E-Mail mithilfe eines Cron-Ausdrucks geplant werden muss.

**Anzahl der Wiederholung:** Wie oft der E-Mail-Endpunkt den Ordner oder das Verzeichnis überprüft. Der Wert „-1“ bedeutet uneingeschränktes Überprüfen („unendlich“). Der Standardwert ist -1.

**Wiederholungsintervall:** Die Überprüfungsrate, mit der der Empfänger den Ordner auf eingehende E-Mails prüft.

**Start des Auftrags verzögern:** Die Zeitspanne, die nach dem Start des Schedulers mit dem Scannen abgewartet wird.

**Batch-Größe:** Die Anzahl von E-Mails, die der Empfänger pro Überprüfung zur Optimierung der Leistung verarbeitet. Der Wert „-1“ bedeutet alle E-Mails. Der Standardwert ist 2.

**Benutzername:** (Obligatorische Einstellung) Der Benutzername, mit dem ein Ziel-Service aus einer E-Mail heraus aufgerufen wird. Der Standardwert lautet „SuperAdmin“.

**Domain-Name:** (Obligatorische Einstellung) Die Domain des Benutzers. Der Standardwert lautet „DefaultDom“.

**Domain-Muster:** Gibt die Domain-Muster für eingehende E-Mails an, die vom Anbieter akzeptiert werden. Wenn beispielsweise „adobe.com“ verwendet wird, werden nur E-Mails aus der Domain „adobe.com“ verarbeitet, während E-Mails aus anderen Domains ignoriert werden.

**Dateimuster:** Gibt das Muster für eingehende Dateianhänge an, die vom Anbieter akzeptiert werden. Dazu gehören Dateien mit bestimmten Erweiterungen (&amp;ast;.dat, &amp;ast;.xml), bestimmte Namen (Daten) oder zusammengesetzte Ausdrücke im Namen und in der Erweiterung (&amp;ast;.[dD][aA]&#39;port&#39;).

**Empfänger erfolgreicher Aufträge:** Eine E-Mail-Adresse, an die Benachrichtigungen über erfolgreiche Aufträge gesendet werden. Standardmäßig werden Benachrichtigungen über erfolgreiche Aufträge immer an den Absender gesendet. Wenn Sie „sender“ eingeben, werden E-Mail-Ergebnisse an den Absender gesendet. Es werden bis zu 100 Empfänger unterstützt. Geben Sie zusätzliche Empfänger mit durch Kommas (,) getrennte E-Mail-Adressen an.

Zum Deaktivieren dieser Einstellung lassen Sie sie unausgefüllt. Es kann Fälle geben, in denen Sie einen Prozess auslösen möchten, ohne ein Benachrichtigung per E-Mail zum Ergebnis erhalten zu wollen.

**Empfänger fehlgeschlagener Aufträge:** Eine E-Mail-Adresse, an die Benachrichtigungen über fehlgeschlagene Aufträge gesendet werden. Standardmäßig werden Benachrichtigungen über fehlgeschlagene Aufträge immer an den Absender gesendet. Wenn Sie „sender“ eingeben, werden E-Mail-Ergebnisse an den Absender gesendet. Es werden bis zu 100 Empfänger unterstützt. Geben Sie zusätzliche Empfänger mit durch Kommas (,) getrennte E-Mail-Adressen an.

Zum Deaktivieren dieser Einstellung lassen Sie sie unausgefüllt. Es kann Fälle geben, in denen Sie einen Prozess auslösen möchten, ohne ein Benachrichtigung per E-Mail zum Ergebnis erhalten zu wollen.

**Posteingang - Host:** Der Host-Name oder die IP-Adresse für den Posteingang, der/die vom E-Mail-Anbieter überprüft werden soll.

**Posteingang - Port:** Der Port, der vom E-Mail-Server verwendet wird. Der Standardwert ist für POP3 „110“ und für IMAP „143“. Wenn SSL aktiviert ist, lautet der Standardwert für POP3 „995“ und für IMAP „993“.

**Posteingang - Protokoll:** Das E-Mail-Protokoll, das vom E-Mail-Endpunkt zum Überprüfen des Posteingangs verwendet werden soll. Die Werte sind IMAP und POP3. Der Hostmailserver des Posteingangs muss diese Protokolle unterstützen.

**Posteingang - Zeitüberschreitung:** Das Zeitlimit in Sekunden, das der E-Mail-Anbieter auf Antworten des Posteingangs warten soll.

**Posteingang - Benutzer:** Der Benutzername, der zum Anmelden beim E-Mail-Konto erforderlich ist. Je nach E-Mail-Server und Konfiguration kann dies nur der in der E-Mail-Adresse enthaltene Benutzername oder die vollständige E-Mail-Adresse sein.

**Posteingang - Kennwort:** Das Kennwort für den Posteingangsbenutzer.

**POP3/IMAP SSL aktiviert:** Aktivieren Sie diese Einstellung, um den E-Mail-Anbieter zu zwingen, bei der Überprüfung des Posteingangs SSL zu verwenden. Vergewissern Sie sich, dass Ihr E-Mail-Server SSL unterstützt.

**SMTP-Host:** Der Host-Name des E-Mail-Servers, den der E-Mail-Anbieter zum Senden von Ergebnissen und Fehlermeldungen verwendet.

**SMTP-Port:** Der Standardwert für den SMTP-Anschluss ist 25.

**SMTP-Benutzer:** Das Benutzerkonto, das vom E-Mail-Anbieter zum Senden ausgehender E-Mail-Benachrichtigungen mit Ergebnissen und Fehlermeldungen verwendet werden soll.

**SMTP-Kennwort:** Das Kennwort für das SMTP-Konto. Einige E-Mail-Server benötigen kein SMTP-Kennwort.

**Senden von:** Die E-Mail-Adresse (z. B. benutzer@firma.com), die zum Senden von E-Mail-Benachrichtigungen zu Ergebnissen und Fehlern verwendet wird. Wenn Sie keinen Wert für „Senden von“ angeben, versucht der E-Mail-Server, die E-Mail-Adresse zu ermitteln, indem der für die Einstellung „SMTP-Benutzer“ festgelegte Wert mit einer auf dem E-Mail-Server konfigurierten Standard-Domain kombiniert wird. Wenn auf dem E-Mail-Server keine Standard-Domain konfiguriert ist und Sie keinen Wert für „Senden von“ angeben, können Fehler auftreten. Geben Sie daher einen Wert für die Einstellung „Senden von“ an, um sicherzustellen, dass die E-Mail-Nachrichten eine korrekte Absenderadresse haben.

**SMTP SSL aktiviert:** Aktivieren Sie diese Einstellung, um den E-Mail-Anbieter zu zwingen, bei der Überprüfung des Posteingangs SSL zu verwenden. Vergewissern Sie sich, dass Ihr E-Mail-Server SSL unterstützt.

**Ordner für Fehler beim Senden von E-Mails:** Gibt einen Ordner an, in dem Ergebnisse gespeichert werden, falls der SMTP-Mail-Server nicht betriebsbereit ist.

**asynchron:** Bei Festlegung auf „synchron“ werden alle Eingabedokumente verarbeitet und eine einzige Antwort wird zurückgegeben. Bei Festlegung auf „asynchron“ wird für jedes verarbeitete Dokument eine Antwort gesendet.

Beispielsweise wird für einen Dienst ein E-Mail-Endpunkt erstellt, der ein einzelnes Word-Dokument akzeptiert und das Dokument als PDF-Datei zurückgibt. An den Posteingang des Endpunktes kann eine E-Mail gesendet werden, die mehrere (3) Word-Dokumente enthält. Wenn nach der Verarbeitung aller drei Dokumente der Endpunkt als „synchron“ konfiguriert wird, wird eine E-Mail-Antwort mit allen drei Dokumenten als Anlage gesendet. Ist der Endpunkt aber „asynchron“, wird nach der Konvertierung jedes Word-Dokuments in PDF eine E-Mail-Antwort gesendet. Das heißt also, dass drei E-Mails mit jeweils einem einzelnen PDF-Anhang gesendet werden.

Der Standardwert ist „asynchron“.

**Ursprüngliche E-Mail-Nachricht als Anhang aufnehmen:** Wenn Sie eine E-Mail an den Formular-Sserver senden, wird standardmäßig der ursprüngliche Text der Nachricht in das Textfeld der E-Mail eingefügt. Um den Text stattdessen als Anhang beizufügen, wählen Sie diese Option.

**Ursprüngliche Betreffzeile für Ergebnis-E-Mails verwenden:** Standardmäßig verwendet der Formular-Server die Werte, die in den Einstellungen „Betreff für Erfolgs-E-Mails“ und „Betreff für Fehler-E-Mails“ als Betreffzeile angegeben wurden, wenn E-Mail-Nachrichten zu Ergebnissen gesendet werden. Wenn Sie stattdessen dieselbe Betreffzeile wie in der ursprünglichen E-Mail, die an den Server gesendet wurde, verwenden möchten, wählen Sie diese Option.

**Betreff für Erfolgs-E-Mails:** Nachdem Sie eine E-Mail an einen E-Mail-Endpunkt gesendet haben, um einen Prozess zu beginnen oder fortzusetzen, erhalten Sie vom AEM Forms-Server eine E-Mail mit einer Antwort. Wenn Ihre E-Mail erfolgreich gesendet wird, erhalten Sie eine Erfolgs-E-Mail. Wenn das Senden Ihrer E-Mail fehlschlägt, erhalten Sie eine Fehler-E-Mail, die Sie über den Fehler informiert. Mit dieser Einstellung können Sie die Betreffzeile von Erfolgs-E-Mails, die an diesen Endpunkt gesendet werden, angeben.

**Text für Erfolgs-E-Mails:** Ermöglicht es Ihnen, den Text der Erfolgs-E-Mails anzugeben, die für diesen Endpunkt gesendet werden.

**Betreffpräfix für Fehler-E-Mails:** Ermöglicht es Ihnen, den Text festzulegen, der am Anfang der Betreffzeile von Fehler-E-Mails verwendet wird, die für diesen Endpunkt gesendet werden.

**Betreff für Fehler-E-Mails:** Ermöglicht es Ihnen, die Betreffzeile der für diesen Endpunkt gesendeten Fehler-E-Mail-Nachrichten anzugeben. Dieser Text wird nach dem Betreffpräfix der Fehler-E-Mails angezeigt.

**Text für Fehler-E-Mails:** Ermöglicht es Ihnen, die erste Zeile des Textes von Fehler-E-Mails anzugeben, die für diesen Endpunkt gesendet werden.

**E-Mail-Übersichtsinfo:** Jede Erfolgs- oder Fehlermeldung enthält einen Abschnitt mit dem ursprünglichen E-Mail-Text, den Sie an den Formular-Server gesendet haben. Diese Einstellung legt den Text fest, der oberhalb dieses Abschnitts angezeigt wird.

**Posteingang prüfen, bevor dieser Endpunkt erstellt/aktualisiert wird:** Wenn diese Option ausgewählt ist, prüft der Formular-Server, ob Ihre SMTP/POP3-Einstellungen korrekt sind, bevor der Endpunkt erstellt wird. Wenn Sie auf „Hinzufügen“ klicken, wird angezeigt, ob das Posteingangskonto gültig ist. Wenn diese Option nicht ausgewählt ist, erstellt der AEM Forms-Server den Endpunkt, ohne den Posteingang zu überprüfen.

**Vorgangsname:** Diese Einstellung ist obligatorisch. Eine Liste von Vorgängen, die dem E-Mail-Endpunkt zugewiesen werden können. Der Vorgang, den Sie hier auswählen, bestimmt, welche Felder in den Abschnitten „Zuordnungen von Eingabeparametern“ und „Zuordnungen von Ausgabeparametern“ angezeigt werden.

**Zuordnungen von Eingabeparametern:** Dient zur Konfiguration der Eingabe, die für die Verarbeitung des Service und der Operation erforderlich ist. Die beiden Eingabetypen sind „Literal“ und „Variable“.

**Wörtlich:** Die E-Mail verwendet den Wert, der in das Feld eingegeben wird, so wie er angezeigt wird.

**Variable:** Sie können eine Zeichenfolge aus dem E-Mail-Betreff, dem Textkörper, der Kopfzeile oder der E-Mail-Adresse des Absenders zuordnen. Dazu verwenden Sie eines der folgenden Schlüsselwörter: %SUBJECT%, %BODY%, %HEADER% oder %SENDER%. Wenn Sie z. B. %SUBJECT%, angeben, wird der Inhalt des E-Mail-Betreffs als Eingabeparameter verwendet. Zum Auswählen von Anhängen geben Sie ein Dateimuster ein, das vom E-Mail-Endpunkt zum Auswählen der angehängten Dokumente verwendet werden kann. Durch die Eingabe von „*.pdf“ werden beispielsweise alle angehängten Dokumente mit einer PDF-Dateinamenerweiterung ausgewählt. Die Eingabe von „&amp;ast;“ wählt ein angehängtes Dokument aus. Durch die Eingabe von „beispiel.pdf“ werden alle angehängten Dokumente namens „beispiel.pdf“ ausgewählt.

**Zuordnungen von Ausgabeparametern:** Wird zum Konfigurieren der Ausgabe des Dienstes und Vorgangs verwendet. Die folgenden Zeichen in den Zuordnungswerten von Ausgabeparametern werden im Dateinamen des Anhangs erweitert:

**%F** Stellt den Dateinamen der Quelldatei dar (ohne eine Erweiterung).

**%E** Steht für die Erweiterung der Quelldatei.

Alle Vorkommen von \ (Backslash) werden durch %% ersetzt.

***Hinweis **: Wenn die Service-Anforderungsnachricht mehrere Dateianhänge enthält, können die Parameter „%F“ und „%E“ nicht für die Eigenschaft „Zuordnungen von Ausgabeparametern“ des Endpunkts verwendet werden. Wenn die Dienstantwort mehrere Dateianhänge zurückgibt, können Sie nicht denselben Dateinamen für mehr als eine Anlage angeben. Wenn Sie diese Empfehlungen nicht befolgen, werden die Namen für die zurückgegebenen Dateien vom aufgerufenen Dienst erstellt, und die Namen sind nicht vorhersehbar.*

Die folgenden Werte sind verfügbar:

**Einzelnes Objekt:** Das Quellordnerziel ist beim E-Mail-Anbieter nicht vorhanden. Ergebnisse werden als Anhänge zurückgegeben. Das Muster ist „Result/%F.ps“ und gibt „Result%%Quelldateiname.ps“ als Dateinamenanhang zurück.

**Liste:** Das Muster ist „Result/%F/“ und gibt „Result%%Quelldateiname%%file1“ als Dateinamenanhang zurück.

**Zuordnung:** Das Muster ist „Result/%F/“ und das Quellziel ist „Result%%Quelldateiname%%file1“ and „Result%%Quelldateiname%%file2“. Wenn die Zuordnung mehr als ein Objekt enthält und das Muster „Result/%F.ps“ ist, sind die Antwortdateianhänge „Result%%Quelldateiname1.ps“ (Ausgabe 1) und „Result%%Quelldateiname2.ps“ (Ausgabe 2).

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
1. Wählen Sie in der Liste „attachmentMap“ den Eintrag „Variable“ und geben Sie in das angrenzende Feld `*.*` ein. Hierdurch werden alle Anhänge eingehender E-Mails an eine Zuordnungsvariable für den Prozess „Aufgabe fertig stellen“ gesendet.
1. Wählen Sie in der Liste „mailBody“ den Eintrag „Variable“ und geben Sie in das angrenzende Feld `%BODY%` ein.
1. Wählen Sie in der Liste „mailFrom“ den Eintrag „Variable“ und geben Sie in das angrenzende Feld `%SENDER%` ein. Hierdurch wird die Absenderadresse den Daten des Prozesses „Aufgabe fertig stellen“ zugeordnet.
1. Geben Sie in das Ergebnisfeld `results` ein. Hierdurch gibt der CompleteTask- oder Startprozess eine Ergebniszeichenfolge zurück.
1. Klicken Sie auf „Hinzufügen“.
