---
title: Verwalten von HSM-Berechtigungen
description: Erfahren Sie, wie Sie HSM-Berechtigungen verwalten. Sie können HSM auf der Seite "Trust Store-Verwaltung"verwalten. Sie können HSM-Komponenten anzeigen, überprüfen, aktualisieren, zurücksetzen und löschen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: facbeab2-de95-4778-894c-faa771d3391e
source-git-commit: fc2f26a69c208947c14e8c6036825bb217901481
workflow-type: tm+mt
source-wordcount: '1323'
ht-degree: 13%

---

# Verwalten von HSM-Berechtigungen {#managing-hsm-credentials}

Auf der Seite &quot;Trust Store-Verwaltung&quot;können Sie die HSM-Berechtigungen (Hardware Security Module) verwalten. Ein HSM ist ein PKCS#11-Gerät eines Drittanbieters, mit dem Sie private Schlüssel sicher generieren und speichern können. Das HSM schützt physisch den Zugriff auf und die Verwendung der privaten Schlüssel.

Die Clientsoftware ist für die Kommunikation mit dem HSM erforderlich. Die HSM-Clientsoftware muss auf demselben Computer installiert und konfiguriert werden wie AEM Formulare.

AEM Forms Digital Signatures kann auf einem HSM gespeicherte Berechtigungen verwenden, um serverseitige digitale Signaturen anzuwenden. Befolgen Sie die Anweisungen in diesem Abschnitt, um einen Alias für jede HSM-Berechtigung zu erstellen, die Digital Signatures verwenden soll. Der Alias enthält alle für HSM erforderlichen Parameter.

>[!NOTE]
>
>Nachdem Sie die HSM-Konfiguration geändert haben, starten Sie den AEM forms-Server neu.

## Alias für eine HSM-Berechtigung erstellen, wenn das HSM-Gerät online ist {#create-an-alias-for-an-hsm-credential-when-the-hsm-device-is-online}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;Trust Store-Verwaltung&quot;> &quot;HSM-Berechtigungen&quot;und dann auf &quot;Hinzufügen&quot;.
1. Geben Sie in das Feld &quot;Profilname&quot;eine Zeichenfolge ein, mit der der Alias identifiziert wird. Dieser Wert wird als Eigenschaft für einige Digital Signatures-Vorgänge wie den Vorgang &quot;Sign Signature Field&quot;verwendet.
1. Geben Sie in das Feld &quot;PKCS11 Library&quot;den vollständig qualifizierten Pfad Ihrer HSM-Client-Bibliothek auf dem Server ein. Beispiel: `c:\Program Files\LunaSA\cryptoki.dll`. In einer Clusterumgebung muss dieser Pfad für alle Server im Cluster identisch sein.
1. Klicken Sie auf HSM-Konnektivität testen . Wenn AEM Formulare eine Verbindung mit dem HSM-Gerät herstellen können, wird eine Meldung mit der Meldung angezeigt, dass das HSM verfügbar ist. Klicken Sie auf Weiter.
1. Verwenden Sie entweder den Token-Namen, die Steckplatz-ID oder den Steckplatzlistenindex, um zu ermitteln, wo die Anmeldeinformationen auf dem HSM gespeichert sind.

   * **Tokenname:** Entspricht dem Namen der HSM-Partition, die verwendet werden soll (z. B. HSMPART1).
   * **Steckplatz-ID:** Die Steckplatz-ID ist eine Steckplatzidentifizierung vom Typ „data type long“.
   * **Steckplatzlistenindex:** Wenn Sie die Option „Steckplatzlistenindex“ auswählen, stellen Sie die Steckplatzinfo auf eine Ganzzahl ein, die dem Steckplatz entspricht. Dies ist ein 0-basierter Index, d. h. wenn der Client zuerst bei der Partition HSMPART1 registriert ist, wird auf HSMPART1 mit dem SlotListIndex-Wert 0 verwiesen.

1. Geben Sie in das Feld &quot;Token-Pin&quot;das für den Zugriff auf den HSM-Schlüssel erforderliche Kennwort ein und klicken Sie auf &quot;Weiter&quot;.
1. Wählen Sie im Feld Anmeldedaten eine Berechtigung aus. Klicken Sie auf Speichern.

## Alias für eine HSM-Berechtigung erstellen, wenn das HSM-Gerät offline ist {#create-an-alias-for-an-hsm-credential-when-the-hsm-device-is-offline}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;Trust Store-Verwaltung&quot;> &quot;HSM-Berechtigungen&quot;und dann auf &quot;Hinzufügen&quot;.
1. Geben Sie in das Feld &quot;Profilname&quot;eine Zeichenfolge ein, mit der der Alias identifiziert wird. Dieser Wert wird als Eigenschaft für einige Digital Signatures-Vorgänge wie den Vorgang &quot;Sign Signature Field&quot;verwendet.
1. Geben Sie in das Feld &quot;PKCS11 Library&quot;den vollständig qualifizierten Pfad Ihrer HSM-Client-Bibliothek auf dem Server ein. Beispiel: `c:\Program Files\LunaSA\cryptoki.dll`. In einer Clusterumgebung muss dieser Pfad für alle Server im Cluster identisch sein.
1. Aktivieren Sie das Kontrollkästchen Offline-Profilerstellung . Klicken Sie auf Weiter.
1. Wählen Sie in der Liste HSM-Gerät den Hersteller des HSM-Geräts aus, auf dem die Berechtigung gespeichert ist.
1. Wählen Sie in der Liste &quot;Steckplatztyp&quot;die Option &quot;Steckplatz-ID&quot;, &quot;Steckplatzindex&quot;oder &quot;Token-Name&quot;aus und geben Sie im Feld &quot;Steckplatzinfo&quot;einen Wert an. AEM Formulare verwenden diese Einstellungen, um zu bestimmen, wo die Anmeldeinformationen auf dem HSM gespeichert werden.

   * **Tokenname:** Entspricht einem Partitionsnamen (z. B. HSMPART1).
   * **Steckplatz-ID:** Die Steckplatz-ID ist eine Ganzzahl, die dem Steckplatz entspricht, der wiederum einer Partition entspricht. Beispielsweise der Client (Formularserver), der zuerst bei der Partition HSMPART1 registriert ist. Dadurch wird Steckplatz 1 der Partition HSMPART1 für diesen Client zugeordnet. Da HSMPART1 die erste registrierte Partition ist, lautet die Steckplatz-ID 1 und Sie würden &quot;Steckplatzinfo&quot;auf 1 setzen.

     Die Steckplatz-ID wird Client für Client festgelegt. Wenn Sie einen zweiten Rechner bei einer anderen Partition registriert haben (z. B. HSMPART2 auf demselben HSM-Gerät), wird Steckplatz 1 für diesen Client mit der Partition HSMPART2 verknüpft.

   * **Steckplatzindex:** Wenn Sie die Option „Steckplatzindex“ auswählen, stellen Sie die Steckplatzinfo auf eine Ganzzahl ein, die dem Steckplatz entspricht. Dies ist ein 0-basierter Index, d. h. wenn der Client zuerst bei der Partition HSMPART1 registriert ist, wird Steckplatz 1 für diesen Client der Partition HSMPART1 zugeordnet. Da HSMPART1 die erste registrierte Partition ist, ist der Steckplatzindex 0.

1. Wählen Sie eine der folgenden Optionen aus und geben Sie den Pfad an:

   * **Zertifikate**: (bei Verwendung von SHA 1 nicht erforderlich) Klicken Sie auf „Durchsuchen“ und suchen Sie den Pfad zu dem öffentlichen Schlüssel für die verwendete Berechtigung.
   * **Zertifikat SHA1:** (Nicht erforderlich bei Verwendung eines physischen Zertifikats) Geben Sie den SHA1-Wert (Thumbprint) der öffentlichen Schlüsseldatei (.cer) für die verwendete Berechtigung ein. Stellen Sie sicher, dass im SHA1-Wert keine Leerzeichen verwendet werden.

1. Geben Sie in das Feld &quot;Kennwort&quot;das Kennwort ein, das für den Zugriff auf den HSM-Schlüssel für die angegebenen Steckplatzinformationen erforderlich ist, und klicken Sie auf &quot;Speichern&quot;.

## Eigenschaften von HSM-Berechtigungsalias anzeigen {#view-hsm-credential-alias-properties}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;Trust Store-Verwaltung&quot;> &quot;HSM-Berechtigungen&quot;.
1. Klicken Sie auf den Aliasnamen des Berechtigungsalias, um die Eigenschaften anzuzeigen, und klicken Sie dann auf &quot;OK&quot;.

## Überprüfen des Status einer HSM-Berechtigung {#check-the-status-of-an-hsm-credential}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;Trust Store-Verwaltung&quot;> &quot;HSM-Berechtigungen&quot;.
1. Aktivieren Sie das Kontrollkästchen neben den Berechtigungen, die Sie überprüfen möchten, und klicken Sie auf Status überprüfen .

Die Spalte Status gibt den aktuellen Status der Berechtigung an. Im Falle eines Fehlers wird in der Spalte Status ein rotes X angezeigt. Bewegen Sie den Mauszeiger über das X, um eine QuickInfo mit dem Grund für den Fehler anzuzeigen.

## Eigenschaften von HSM-Berechtigungsalias aktualisieren {#update-hsm-credential-alias-properties}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;Trust Store-Verwaltung&quot;> &quot;HSM-Berechtigungen&quot;.
1. Klicken Sie auf den Aliasnamen des Berechtigungsalias.
1. Klicken Sie auf Berechtigung aktualisieren und aktualisieren Sie die Einstellungen nach Bedarf.

## Alle HSM-Verbindungen zurücksetzen {#reset-all-hsm-connections}

Setzen Sie die offenen Verbindungen zu einem HSM-Gerät nach einer Unterbrechung der Netzwerksitzung zwischen dem Formularserver und dem HSM-Gerät zurück. Unterbrechungen können beispielsweise auftreten, wenn das Netzwerk ausfällt oder das HSM-Gerät für eine Softwareaktualisierung offline geschaltet wird. Nach einer Unterbrechung sind die vorhandenen Verbindungen veraltet und alle Signieranforderungen für diese Verbindungen schlagen fehl. Mit der Option Alle HSM-Verbindungen zurücksetzen werden die alten Verbindungen gelöscht.

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;Trust Store-Verwaltung&quot;> &quot;HSM-Berechtigungen&quot;.
1. Klicken Sie auf Alle HSM-Verbindungen zurücksetzen .

## HSM-Berechtigungsalias löschen {#delete-an-hsm-credential-alias}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;Trust Store-Verwaltung&quot;> &quot;HSM-Berechtigungen&quot;.
1. Aktivieren Sie die Kontrollkästchen der zu löschenden HSM-Berechtigungen und klicken Sie auf &quot;Löschen&quot;und anschließend auf &quot;OK&quot;.

## Remote HSM-Unterstützung konfigurieren {#configure-remote-hsm-support}

AEM Forms verwendet einen webdienstbasierten IPC/RPC-Mechanismus. Über diesen Mechanismus kann AEM Forms ein auf einem Remotecomputer installiertes HSM verwenden. Um diese Funktion zu verwenden, installieren Sie den Webdienst auf dem Remotecomputer, auf dem HSM installiert ist. Siehe [Konfigurieren von HSM-Unterstützung für AEM Forms ES mithilfe von Sun JDK auf Windows 64-Bit-Plattform](https://kb2.adobe.com/cps/808/cpsid_80835.html)für weitere Informationen.

Dieser Mechanismus unterstützt nicht die Online-Erstellung von HSM-Profilen oder Statusprüfungen. Es gibt jedoch zwei Möglichkeiten, HSM-Profile zu erstellen und Statusprüfungen durchzuführen:

* Erstellen Sie eine AEM forms-Client-Berechtigung, indem Sie sie an das Zertifikat des Unterzeichners übergeben. Führen Sie die Schritte unter [Konfigurieren von HSM-Unterstützung für AEM Forms ES mithilfe von Sun JDK auf Windows 64-Bit-Plattform](https://kb2.adobe.com/cps/808/cpsid_80835.html). Der Webdienstspeicherort wird als Eigenschaft &quot;Credential&quot;übergeben. Offline-HSM-Profile, die entweder mit Zertifikat der oder SHA-1-Hexadezimal-Zertifikat erstellt wurden, werden ebenfalls unterstützt. Wenn Sie jedoch von einer früheren Version AEM Formulars auf AEM Formulare aktualisiert haben, nehmen Sie Clientänderungen vor, da die Berechtigung Zertifikat- und Webdienstinformationen enthielt.
* Der Speicherort des Webdienstes wird in der Administration Console für den Signature-Dienst angegeben. (Siehe [Einstellungen des Signature-Dienstes](/help/forms/using/admin-help/configure-service-settings.md#signature-service-settings). Hier trug der Client nur den Alias des HSM-Profils im Trust Store. Sie können diese Option nahtlos ohne Client-Änderungen verwenden, auch wenn Sie von einer früheren Version AEM Formulars auf AEM Formulare aktualisiert haben. Diese Option unterstützt keine HSM-Profile, die das Zertifikat SHA-1 verwenden.
