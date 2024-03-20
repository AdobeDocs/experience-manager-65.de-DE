---
title: Konfigurieren von E-Mail-Endpunkten
description: Erfahren Sie, wie Sie E-Mail-Endpunkte konfigurieren. Mit E-Mail-Endpunkten können Sie einen Dienst aufrufen, indem Sie ein oder mehrere Dokumente an ein bestimmtes E-Mail-Konto senden.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 33583a12-4f20-4146-baa4-c9854e454bbf
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '3796'
ht-degree: 56%

---

# Konfigurieren von E-Mail-Endpunkten {#configuring-email-endpoints}

E-Mail-Endpunkte ermöglichen es Benutzern, einen Dienst aufzurufen, indem sie ein oder mehrere Dokumente (als E-Mail-Anhänge) an ein bestimmtes E-Mail-Konto senden. Der E-Mail-Posteingang dient als Sammelpunkt für die Anlagen. Der Dienst überwacht den Posteingang und verarbeitet die Anlagen. Die Ergebnisse der Konvertierung werden an den im -Endpunkt definierten Benutzer weitergeleitet.

Für einen E-Mail-Endpunkt können autorisierte Benutzer einen Prozess aufrufen, indem sie Dateien per E-Mail an das entsprechende Konto senden. Die Ergebnisse werden (standardmäßig) an den sendenden Benutzer oder an den in den Endpunkteinstellungen definierten Benutzer zurückgegeben.

Bevor Sie einen E-Mail-Endpunkt konfigurieren, erstellen Sie ein POP3- oder IMAP-E-Mail-Konto für die Verwendung durch den Endpunkt. Richten Sie für jeden Konvertierungstyp ein eigenes Konto ein. Beispielsweise kann ein PDF-Konto so konfiguriert werden, dass aus eingehenden Dateianlagen Standarddokumente generiert werden, und ein anderes Konto kann so konfiguriert werden, dass es sichere PDF-Dokumente generiert.

>[!NOTE]
>
>Jede E-Mail-Adresse darf nur einem E-Mail-Endpunkt zugeordnet sein. Sie können nicht mehrere E-Mail-Endpunkte für eine E-Mail-Adresse konfigurieren, selbst wenn die zusätzlichen E-Mail-Endpunkte deaktiviert sind.

Alle E-Mail-Endpunkte werden mit einem autorisierten Benutzernamen und Kennwort für den E-Mail-Posteingang konfiguriert, die beim Aufrufen des Dienstes erforderlich sind. Das E-Mail-Konto wird durch das E-Mail-Serversystem geschützt, auf dem es konfiguriert ist.

Wenn Benutzer Dokumente mit westeuropäischen Sprachzeichen in Datei- und Konvertierungspfadnamen senden, müssen Sie eine E-Mail-Anwendung einsetzen, welche die erforderlichen Kodierungstypen (Latin1 [ISO-8859-1], Westeuropäisch [Windows] oder UTF-8) unterstützt. Weitere Informationen finden Sie unter *Installieren und Bereitstellen von AEM* Dokument für Ihren Anwendungsserver.

Bevor Sie einen E-Mail-Endpunkt konfigurieren, konfigurieren Sie den E-Mail-Dienst. (Siehe [Standard-E-Mail-Endpunkteinstellungen konfigurieren](configuring-email-endpoints.md#configure-default-email-endpoint-settings). Die Konfigurationsparameter des E-Mail-Dienstes haben zwei Zwecke:

* So konfigurieren Sie Attribute, die für alle E-Mail-Endpunkte gelten
* So stellen Sie Standardwerte für alle E-Mail-Endpunkte bereit

## SSL für einen E-Mail-Endpunkt konfigurieren {#configure-ssl-for-an-email-endpoint}

Sie können POP3, IMAP oder SMTP so konfigurieren, dass Secure Sockets Layer (SSL) für einen E-Mail-Endpunkt verwendet wird.

1. Aktivieren Sie auf dem E-Mail-Server gemäß der Dokumentation des Herstellers SSL für POP3, IMAP oder SMTP.
1. Exportieren Sie ein Client-Zertifikat vom E-Mail-Server.
1. Verwenden Sie das Programm &quot;keytool&quot;, um die Datei mit dem Clientzertifikat in den JVM-Zertifikatspeicher (Java Virtual Machine) des Anwendungsservers zu importieren. Das Verfahren für diesen Schritt hängt von den JVM- und Client-Installationspfaden ab.

   Wenn Sie beispielsweise eine standardmäßige Oracle WebLogic Server-Installation mit JDK 1.5.0 unter Microsoft Windows Server® 2003 verwenden, geben Sie an einer Eingabeaufforderung den folgenden Text ein:

   `keytool -import -file client_certificate -alias myalias -keystore BEA_HOME\jdk150_04\jre\security\cacerts`

1. Geben Sie das Kennwort ein, wenn Sie dazu aufgefordert werden (für Java lautet das Standardkennwort `changeit`). Sie erhalten eine Meldung darüber, dass das Zertifikat erfolgreich importiert wurde.
1. Verwenden Sie Administration Console, um den E-Mail-Endpunkt zum Dienst hinzuzufügen.
1. Erstellen Sie den E-Mail-Endpunkt in Administration Console. Wählen Sie beim Konfigurieren der Endpunkteinstellungen &quot;POP3/IMAP SSL Enabled&quot;für eingehende Nachrichten und &quot;SMTP SSL Enabled&quot;für ausgehende Nachrichten und ändern Sie die Anschlusseigenschaften entsprechend.

>[!NOTE]
>
>Tipp: Wenn bei der Verwendung von SSL Probleme auftreten, verwenden Sie einen E-Mail-Client wie Microsoft Outlook, um zu überprüfen, ob dieser über SSL auf den E-Mail-Server zugreifen kann. Wenn der E-Mail-Client nicht auf den E-Mail-Server zugreifen kann, hängt das Problem mit der Konfiguration Ihres Zertifikats oder Ihres E-Mail-Servers zusammen.

## Standard-E-Mail-Endpunkteinstellungen konfigurieren {#configure-default-email-endpoint-settings}

Auf der Seite &quot;Dienstverwaltung&quot;können Sie Attribute konfigurieren, die für alle E-Mail-Endpunkte gelten, und Standardwerte für alle E-Mail-Endpunkte bereitstellen.

Damit der Arbeitsablauf für Formulare eingehende E-Mail-Nachrichten von Benutzern empfangen und verarbeiten kann, müssen Sie einen E-Mail-Endpunkt für den Complete Task-Dienst erstellen. Für diesen E-Mail-Endpunkt sind zusätzliche Einstellungen erforderlich, wie unter [E-Mail-Endpunkt für den Complete Task-Dienst erstellen](configuring-email-endpoints.md#create-an-email-endpoint-for-the-complete-task-service).

### Standardwerte für E-Mail-Endpunkte ändern {#change-the-default-values-for-email-endpoints}

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Anwendungen und Dienste“ > „Dienstverwaltung“.
1. Klicken Sie auf der Seite &quot;Dienstverwaltung&quot;auf E-Mail: 1.0 (die Komponenten-ID lautet com.adobe.idp.dsc.provider.service.email.Email).
1. Geben Sie auf der Registerkarte Konfiguration die standardmäßigen E-Mail-Endpunkteinstellungen an und klicken Sie auf Speichern .

### Standard-E-Mail-Endpunkteinstellungen {#default-email-endpoint-settings}

**Cron-Ausdruck:** Der Cron-Ausdruck, wie er von Quartz zur zeitlichen Planung des Abrufs des Eingabeordners verwendet wird.

**Wiederholungsintervall:** Die Häufigkeit, mit der der Ordner abgerufen wird. Der Standardwert für das Wiederholungsintervall in Sekunden, wenn in der Endpunktkonfiguration kein Wert angegeben ist. Der Standardwert ist 10. Dieser Wert kann nicht kleiner als „10“ sein.

**Anzahl der Wiederholungen:** Wie oft das Eingabeverzeichnis abgefragt wird. Der Standardwert für die Anzahl der Wiederholungen, der verwendet wird, wenn in der Endpunktkonfiguration kein Wert angegeben ist. Ein Wert von „-1“ bedeutet unbegrenztes Überprüfen des Ordners. Der Standardwert lautet -1.

**Start des Auftrags verzögern:** Der Standardwert in Sekunden für die Verzögerung, bevor der Auftrag beginnt, den Endpunkt zu überprüfen. Der Standardwert lautet 0.

**Batch-Größe:** Die Anzahl der E-Mails, die der Empfänger pro Überprüfung zur Optimierung der Leistung verarbeitet. Der Wert -1 zeigt alle E-Mails an. Der Standardwert lautet 2.

**Asynchron:** Gibt den Aufruftyp als asynchron oder synchron an. Transiente und synchrone Prozesse können nur synchron aufgerufen werden. Der Standardwert lautet „asynchron“.

**Domain-Muster:** Das Domain-Namensmuster, das zum Filtern eingehender E-Mails verwendet wird. Wenn beispielsweise adobe.com verwendet wird, werden nur E-Mails aus der Domain „adobe.com“ verarbeitet, während E-Mails aus anderen Domains ignoriert werden.

**Dateimuster:** Gibt die Muster für eingehende Dateianhänge an, die vom Anbieter akzeptiert werden. Hierzu gehören Dateien mit bestimmten Erweiterungen (&amp;ast;.dat, &amp;ast;.xml), Dateien mit bestimmten Namen (data) sowie Dateien mit zusammengesetzten Ausdrücken im Namen und in der Erweiterung (.[dD][aA]&#39;port&#39;). Der Standardwert lautet &amp;ast;.&amp;ast;.

**Empfänger erfolgreicher Aufträge:** Eine oder mehrere E-Mail-Adressen, an die Benachrichtigungen über erfolgreiche Aufträge per E-Mail gesendet werden. Standardmäßig wird eine erfolgreiche Auftragsnachricht immer an den Absender des ursprünglichen Auftrags gesendet. Es werden bis zu 100 Empfänger unterstützt. Um diese Einstellung zu deaktivieren, lassen Sie dieses Feld leer.

**Empfänger fehlgeschlagener Aufträge:** Eine oder mehrere E-Mail-Adressen, an die Benachrichtigungen über fehlgeschlagene Aufträge per E-Mail gesendet werden. Standardmäßig wird eine Benachrichtigung über fehlgeschlagene Aufträge immer an den Absender gesendet, der den ursprünglichen Auftrag gesendet hat. Es werden bis zu 100 Empfänger unterstützt. Um diese Einstellung zu deaktivieren, lassen Sie dieses Feld leer.

**Posteingang - Host:** Der Host-Name oder die IP-Adresse für den Posteingang, der/die vom E-Mail-Anbieter überprüft werden soll.

**Posteingang - Port:** Die Port-Nummer für den Posteingang, die vom E-Mail-Anbieter überprüft werden soll. Wenn der Wert 0 beträgt, wird der standardmäßige IMAP- oder POP3-Anschluss verwendet.

**Posteingang - Protokoll:** Das E-Mail-Protokoll, das vom E-Mail-Endpunkt zum Überprüfen des Posteingangs verwendet werden soll. Die Optionen sind IMAP oder POP3. Der Host-Mailserver des Posteingangs muss diese Protokolle unterstützen.

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

**Schließen Sie den ursprünglichen E-Mail-Hauptteil als Anhang ein:** Wenn Sie eine E-Mail an den Forms-Server senden, ist standardmäßig der ursprüngliche Nachrichtentext im Nachrichten-Textkörper enthalten. Wählen Sie diese Option, um den Text stattdessen als Anhang beizufügen.

**Ursprüngliche Betreffzeile für Ergebnis-E-Mails verwenden:** Standardmäßig verwendet der Formular-Server die Werte, die in den Einstellungen „Betreff für Erfolgs-E-Mails“ und „Betreff für Fehler-E-Mails“ als Betreffzeile angegeben wurden, wenn E-Mail-Nachrichten zu Ergebnissen gesendet werden. Wenn Sie stattdessen dieselbe Betreffzeile wie in der ursprünglichen E-Mail, die an den Server gesendet wurde, verwenden möchten, wählen Sie diese Option.

**Success Email Subject:** Nachdem Sie eine E-Mail an einen E-Mail-Endpunkt gesendet haben, um einen Prozess zu starten oder fortzusetzen, erhalten Sie eine E-Mail-Nachricht vom AEM Forms-Server. Wenn Ihre E-Mail erfolgreich ist, erhalten Sie eine Erfolgs-E-Mail. Wenn Ihre E-Mail fehlschlägt, erhalten Sie eine Fehler-E-Mail mit Informationen dazu, warum sie fehlgeschlagen ist. Mit dieser Einstellung können Sie die Betreffzeile von Erfolgs-E-Mails angeben, die an diesen Endpunkt gesendet werden.

**Nachricht für Erfolgs-E-Mails:** Mit dieser Option können Sie den Text der E-Mail-Nachrichten zu Erfolgen angeben, die an diesen Endpunkt gesendet werden.

**Betreffpräfix für Fehler-E-Mails:** Mit dieser Option können Sie den Text am Anfang der Betreffzeile von E-Mail-Nachrichten zu Fehlern angeben, die an diesen Endpunkt gesendet werden.

**Betreff für Fehler-E-Mails:** Mit dieser Option können Sie die Betreffzeile von E-Mail-Nachrichten zu Fehlern angeben, die an diesen Endpunkt gesendet werden. Dieser Text wird nach dem Präfix des Fehler-E-Mail-Betreffs angezeigt.

**Nachricht für Fehler-E-Mails:** Mit dieser Option können Sie die erste Zeile im Nachrichtentext von Fehler-E-Mails angeben, die an diesen Endpunkt gesendet werden.

**E-Mail-Zusammenfassungsinformationen:** Jede Erfolgs- oder Fehlermeldung enthält einen Abschnitt mit dem ursprünglichen E-Mail-Text, den Sie an den Forms-Server gesendet haben. Diese Einstellung legt den Text fest, der oberhalb dieses Abschnitts angezeigt wird.

**Validieren des Posteingangs vor dem Erstellen/Aktualisieren dieses Endpunkts:** Wenn diese Option aktiviert ist, prüft der Forms-Server, ob Ihre SMTP/POP3-Einstellungen korrekt sind, bevor der Endpunkt erstellt wird. Wenn Sie auf Hinzufügen klicken, wird eine Meldung angezeigt, die angibt, ob das Posteingangskonto gültig ist. Wenn diese Option nicht ausgewählt ist, erstellt der AEM Forms-Server den Endpunkt, ohne den Posteingang zu überprüfen.

**Zeichensatzkodierung:** Das für die E-Mail-Nachricht zu verwendende Kodierungsformat. Der Standardwert ist UTF-8, den die meisten Benutzer außerhalb Japans verwenden. Benutzer in japanischen Umgebungen können &quot;ISO2022-JP&quot;auswählen.

**Ordner für Fehler beim Senden von E-Mails:** Gibt einen Ordner an, in dem Ergebnisse gespeichert werden, falls der SMTP-Mail-Server nicht betriebsbereit ist.

## E-Mail-Endpunkteinstellungen {#email-endpoint-settings}

Verwenden Sie die folgenden Einstellungen, um einen E-Mail-Endpunkt zu konfigurieren.

**Name:** Eine obligatorische Angabe zum Identifizieren des Endpunktes. Der Name darf kein &lt;-Zeichen enthalten, weil dadurch die Anzeige des Namens in Workspace abgeschnitten wird. Wenn Sie eine URL als Name des Endpunktes angeben, vergewissern Sie sich, dass sie den in RFC1738 angegebenen Syntaxregeln entspricht.

**Beschreibung:** Eine Beschreibung des Endpunktes. Sie darf kein &lt;-Zeichen enthalten, weil dadurch die Anzeige der Beschreibung in Workspace abgeschnitten wird.

**Cron-Ausdruck:** Geben Sie einen Cron-Ausdruck ein, wenn die E-Mail mithilfe eines Cron-Ausdrucks geplant werden muss.

**Anzahl der Wiederholung:** Wie oft der E-Mail-Endpunkt den Ordner oder das Verzeichnis überprüft. Der Wert &quot;-1&quot;bedeutet uneingeschränktes Überprüfen. Der Standardwert ist -1.

**Wiederholungsintervall:** Die Überprüfungsrate, mit der der Empfänger den Ordner auf eingehende E-Mails prüft.

**Start des Auftrags verzögern:** Die Zeitspanne, die nach dem Start des Schedulers mit dem Scannen abgewartet wird.

**Batch-Größe:** Die Anzahl von E-Mails, die der Empfänger pro Überprüfung zur Optimierung der Leistung verarbeitet. Der Wert -1 zeigt alle E-Mails an. Der Standardwert ist 2.

**Benutzername:** (Obligatorische Einstellung) Der Benutzername, mit dem ein Ziel-Service aus einer E-Mail heraus aufgerufen wird. Der Standardwert lautet „SuperAdmin“.

**Domain-Name:** (Obligatorische Einstellung) Die Domain des Benutzers. Der Standardwert lautet „DefaultDom“.

**Domain-Muster:** Gibt die Domain-Muster für eingehende E-Mails an, die vom Anbieter akzeptiert werden. Wenn beispielsweise „adobe.com“ verwendet wird, werden nur E-Mails aus der Domain „adobe.com“ verarbeitet, während E-Mails aus anderen Domains ignoriert werden.

**Dateimuster:** Gibt das Muster für eingehende Dateianhänge an, die vom Anbieter akzeptiert werden. Dazu gehören Dateien mit bestimmten Erweiterungen (&amp;ast;.dat, &amp;ast;.xml), bestimmte Namen (Daten) oder zusammengesetzte Ausdrücke im Namen und in der Erweiterung (&amp;ast;.[dD][aA]&#39;port&#39;).

**Empfänger erfolgreicher Aufträge:** Eine E-Mail-Adresse, an die Benachrichtigungen über erfolgreiche Aufträge gesendet werden. Standardmäßig werden Benachrichtigungen über erfolgreiche Aufträge immer an den Absender gesendet. Wenn Sie „sender“ eingeben, werden E-Mail-Ergebnisse an den Absender gesendet. Es werden bis zu 100 Empfänger unterstützt. Geben Sie zusätzliche Empfänger mit E-Mail-Adressen, getrennt durch Kommas (,), an.

Um diese Einstellung zu deaktivieren, lassen Sie die Einstellung leer. In einigen Fällen möchten Sie einen Trigger durchführen und keine E-Mail-Benachrichtigung zum Ergebnis wünschen.

**Empfänger fehlgeschlagener Aufträge:** Eine E-Mail-Adresse, an die Benachrichtigungen über fehlgeschlagene Aufträge gesendet werden. Standardmäßig werden Benachrichtigungen über fehlgeschlagene Aufträge immer an den Absender gesendet. Wenn Sie „sender“ eingeben, werden E-Mail-Ergebnisse an den Absender gesendet. Es werden bis zu 100 Empfänger unterstützt. Geben Sie zusätzliche Empfänger mit E-Mail-Adressen, getrennt durch Kommas (,), an.

Um diese Einstellung zu deaktivieren, lassen Sie die Einstellung leer. In einigen Fällen möchten Sie einen Trigger durchführen und keine E-Mail-Benachrichtigung zum Ergebnis wünschen.

**Posteingang - Host:** Der Host-Name oder die IP-Adresse für den Posteingang, der/die vom E-Mail-Anbieter überprüft werden soll.

**Posteingang - Port:** Der Port, der vom E-Mail-Server verwendet wird. Der Standardwert ist für POP3 „110“ und für IMAP „143“. Wenn SSL aktiviert ist, lautet der Standardwert für POP3 „995“ und für IMAP „993“.

**Posteingang - Protokoll:** Das E-Mail-Protokoll, das vom E-Mail-Endpunkt zum Überprüfen des Posteingangs verwendet werden soll. Die Werte sind IMAP oder POP3. Der Host-Mailserver des Posteingangs muss diese Protokolle unterstützen.

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

**asynchron:** Bei Festlegung auf „synchron“ werden alle Eingabedokumente verarbeitet und eine einzige Antwort wird zurückgegeben. Wenn &quot;asynchron&quot;festgelegt ist, wird für jedes verarbeitete Dokument eine Antwort gesendet.

Beispielsweise wird ein E-Mail-Endpunkt für einen Dienst erstellt, der ein einzelnes Word-Dokument akzeptiert und dieses Dokument als PDF-Datei zurückgibt. Eine E-Mail kann an den Posteingang des Endpunkts gesendet werden, der mehrere (3) Word-Dokumente enthält. Wenn bei der Verarbeitung aller drei Dokumente der Endpunkt als synchron konfiguriert wird, wird eine einzige Antwort-E-Mail mit allen drei Dokumenten gesendet, die angehängt sind. Wenn der Endpunkt asynchron ist, wird eine Antwort-E-Mail gesendet, nachdem jedes Word-Dokument in PDF konvertiert wurde. Das Ergebnis sind drei E-Mails mit jeweils einem PDF-Anhang.

Der Standardwert ist „asynchron“.

**Fügen Sie den ursprünglichen E-Mail-Textkörper als Anhang hinzu:** Wenn Sie eine E-Mail an den Forms-Server senden, ist standardmäßig der ursprüngliche Nachrichtentext im Nachrichten-Textkörper enthalten. Um den Text stattdessen als Anhang beizufügen, wählen Sie diese Option.

**Ursprüngliche Betreffzeile für Ergebnis-E-Mails verwenden:** Standardmäßig verwendet der Formular-Server die Werte, die in den Einstellungen „Betreff für Erfolgs-E-Mails“ und „Betreff für Fehler-E-Mails“ als Betreffzeile angegeben wurden, wenn E-Mail-Nachrichten zu Ergebnissen gesendet werden. Wenn Sie stattdessen dieselbe Betreffzeile wie in der ursprünglichen E-Mail, die an den Server gesendet wurde, verwenden möchten, wählen Sie diese Option.

**Success Email Subject:** Nachdem Sie eine E-Mail an einen E-Mail-Endpunkt gesendet haben, um einen Prozess zu starten oder fortzusetzen, erhalten Sie eine E-Mail-Nachricht vom AEM Forms-Server. Wenn Ihre E-Mail erfolgreich ist, erhalten Sie eine Erfolgs-E-Mail. Wenn Ihre E-Mail fehlschlägt, erhalten Sie eine Fehler-E-Mail mit Informationen dazu, warum sie fehlgeschlagen ist. Mit dieser Einstellung können Sie die Betreffzeile von Erfolgs-E-Mails angeben, die an diesen Endpunkt gesendet werden.

**Nachricht für Erfolgs-E-Mails:** Mit dieser Option können Sie den Text der E-Mail-Nachrichten zu Erfolgen angeben, die an diesen Endpunkt gesendet werden.

**Betreffpräfix für Fehler-E-Mails:** Mit dieser Option können Sie den Text am Anfang der Betreffzeile von E-Mail-Nachrichten zu Fehlern angeben, die an diesen Endpunkt gesendet werden.

**Betreff für Fehler-E-Mails:** Mit dieser Option können Sie die Betreffzeile von E-Mail-Nachrichten zu Fehlern angeben, die an diesen Endpunkt gesendet werden. Dieser Text wird nach dem Präfix des Fehler-E-Mail-Betreffs angezeigt.

**Nachricht für Fehler-E-Mails:** Mit dieser Option können Sie die erste Zeile im Nachrichtentext von Fehler-E-Mails angeben, die an diesen Endpunkt gesendet werden.

**E-Mail-Zusammenfassungsinformationen:** Jede Erfolgs- oder Fehlermeldung enthält einen Abschnitt mit dem ursprünglichen E-Mail-Text, den Sie an den Forms-Server gesendet haben. Diese Einstellung legt den Text fest, der oberhalb dieses Abschnitts angezeigt wird.

**Validieren Sie den Posteingang, bevor Sie diesen Endpunkt erstellen/aktualisieren:** Wenn diese Option aktiviert ist, prüft der Forms-Server, ob Ihre SMTP/POP3-Einstellungen korrekt sind, bevor der Endpunkt erstellt wird. Wenn Sie auf Hinzufügen klicken, wird eine Meldung angezeigt, die angibt, ob das Posteingangskonto gültig ist. Wenn diese Option nicht ausgewählt ist, erstellt der AEM Forms-Server den Endpunkt, ohne den Posteingang zu überprüfen.

**Vorgangsname:** Diese Einstellung ist obligatorisch. Eine Liste von Vorgängen, die dem E-Mail-Endpunkt zugewiesen werden können. Der hier ausgewählte Vorgang bestimmt, welche Felder in den Abschnitten &quot;Zuordnungen von Eingabeparametern&quot;und &quot;Zuordnungen von Ausgabeparametern&quot;angezeigt werden.

**Zuordnungen von Eingabeparametern:** Dient zur Konfiguration der Eingabe, die für die Verarbeitung des Service und der Operation erforderlich ist. Die beiden Eingabetypen sind „Literal“ und „Variable“.

**Wörtlich:** Die E-Mail verwendet den Wert, der in das Feld eingegeben wird, so wie er angezeigt wird.

**Variable:** Sie können eine Zeichenfolge aus dem E-Mail-Betreff, dem Textkörper, der Kopfzeile oder der E-Mail-Adresse des Absenders zuordnen. Verwenden Sie dazu einen der folgenden Suchbegriffe: %SUBJECT%, %BODY%, %HEADER% oder %SENDER%. Wenn Sie beispielsweise %SUBJECT% verwenden, wird der Inhalt des E-Mail-Betreffs als Eingabeparameter verwendet. Um Anlagen abzurufen, geben Sie ein Dateimuster ein, mit dem der E-Mail-Endpunkt die angehängten Dokumente auswählen kann. Durch die Eingabe von „*.pdf“ werden beispielsweise alle angehängten Dokumente mit einer PDF-Dateinamenerweiterung ausgewählt. Die Eingabe von „&amp;ast;“ wählt ein angehängtes Dokument aus. Durch die Eingabe von „beispiel.pdf“ werden alle angehängten Dokumente namens „beispiel.pdf“ ausgewählt.

**Zuordnungen von Ausgabeparametern:** Wird zum Konfigurieren der Ausgabe des Dienstes und Vorgangs verwendet. Die folgenden Zeichen in den Zuordnungswerten von Ausgabeparametern werden im Dateinamen des Anhangs erweitert:

**%F** Stellt den Dateinamen der Quelldatei dar (ohne eine Erweiterung).

**%E** Steht für die Erweiterung der Quelldatei.

Alle Vorkommen von \ (Backslash) werden durch %% ersetzt.

***Hinweis **: Wenn die Service-Anforderungsnachricht mehrere Dateianhänge enthält, können die Parameter „%F“ und „%E“ nicht für die Eigenschaft „Zuordnungen von Ausgabeparametern“ des Endpunkts verwendet werden. Wenn die Dienstantwort mehrere Dateianhänge zurückgibt, können Sie nicht denselben Dateinamen für mehr als eine Anlage angeben. Wenn Sie diesen Empfehlungen nicht folgen, erstellt der aufgerufene Dienst die Namen für die zurückgegebenen Dateien und die Namen sind nicht vorhersehbar.*

Die folgenden Werte sind verfügbar:

**Einzelnes Objekt:** Das Quellordnerziel ist beim E-Mail-Anbieter nicht vorhanden. Ergebnisse werden als Anhänge zurückgegeben. Das Muster ist „Result/%F.ps“ und gibt „Result%%Quelldateiname.ps“ als Dateinamenanhang zurück.

**Liste:** Das Muster ist „Result/%F/“ und gibt „Result%%Quelldateiname%%file1“ als Dateinamenanhang zurück.

**Zuordnung:** Das Muster ist „Result/%F/“ und das Quellziel ist „Result%%Quelldateiname%%file1“ and „Result%%Quelldateiname%%file2“. Wenn die Zuordnung mehr als ein Objekt enthält und das Muster „Result/%F.ps“ ist, sind die Antwortdateianhänge „Result%%Quelldateiname1.ps“ (Ausgabe 1) und „Result%%Quelldateiname2.ps“ (Ausgabe 2).

## E-Mail-Endpunkt für den Complete Task-Dienst erstellen {#create-an-email-endpoint-for-the-complete-task-service}

Damit der Arbeitsablauf für Formulare eingehende E-Mail-Nachrichten von Benutzern empfangen und verarbeiten kann, müssen Sie einen E-Mail-Endpunkt für den Complete Task-Dienst erstellen.

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Anwendungen und Dienste“ > „Dienstverwaltung“.
1. Klicken Sie auf der Seite &quot;Dienstverwaltung&quot;auf den Dienst &quot;Aufgabe abschließen&quot;.
1. Wählen Sie auf der Registerkarte Endpunkte die Option E-Mail aus der Dropdown-Liste aus und klicken Sie auf Hinzufügen.
1. Geben Sie in das Feld &quot;Posteingangshost&quot;den Hostnamen oder die IP-Adresse des E-Mail-Servers ein.
1. Geben Sie im Feld &quot;Posteingangsbenutzer&quot;den Benutzernamen ein, der erforderlich ist, um sich bei dem E-Mail-Konto anzumelden, das Sie für die Verarbeitung von Formularübermittlungen erstellt haben. Je nach E-Mail-Server und Konfiguration kann dieser Name nur der Benutzernamenteil der E-Mail-Adresse oder die vollständige E-Mail-Adresse sein.
1. Geben Sie in das Feld &quot;Posteingangskennwort&quot;das Kennwort für den Posteingangsbenutzer ein.
1. Geben Sie in das Feld SMTP Host den Hostnamen oder die IP-Adresse des E-Mail-Servers ein, von dem aus der E-Mail-Anbieter Ergebnisse und Fehlermeldungen sendet.
1. Geben Sie im Feld &quot;SMTP User&quot;das Benutzerkonto ein, das der E-Mail-Anbieter verwenden soll, wenn er E-Mails mit Ergebnissen und Fehlern sendet. Dieses Benutzerkonto kann mit dem für Posteingangsbenutzer verwendeten Wert übereinstimmen.
1. Geben Sie in das Feld SMTP Password das Kennwort für das SMTP-Konto ein.
1. Wählen Sie in der Liste &quot;Vorgangsname&quot;die Option invoke aus.
1. Wählen Sie in der Liste „attachmentMap“ den Eintrag „Variable“ und geben Sie in das angrenzende Feld `*.*` ein. Hierdurch werden alle Anhänge eingehender E-Mails an eine Zuordnungsvariable für den Prozess „Aufgabe fertig stellen“ gesendet.
1. Wählen Sie in der Liste „mailBody“ den Eintrag „Variable“ und geben Sie in das angrenzende Feld `%BODY%` ein.
1. Wählen Sie in der Liste „mailFrom“ den Eintrag „Variable“ und geben Sie in das angrenzende Feld `%SENDER%` ein. Hierdurch wird die Absenderadresse den Daten des Prozesses „Aufgabe fertig stellen“ zugeordnet.
1. Geben Sie in das Ergebnisfeld `results` ein. Dadurch gibt der Complete Task- oder Start-Prozess eine Ergebniszeichenfolge zurück.
1. Klicken Sie auf „Hinzufügen“.
