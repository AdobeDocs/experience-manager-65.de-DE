---
title: HSM-Berechtigungen verwalten
seo-title: HSM-Berechtigungen verwalten
description: Erfahren Sie, wie Sie HSM-Berechtigungen verwalten
seo-description: Erfahren Sie, wie Sie HSM-Berechtigungen verwalten
uuid: 30ddcd4a-f771-44d5-bdef-4826adcd0c44
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e5f17ba8-8aab-4449-811a-20ad33de1c6f
exl-id: facbeab2-de95-4778-894c-faa771d3391e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1313'
ht-degree: 99%

---

# HSM-Berechtigungen verwalten {#managing-hsm-credentials}

Auf der Seite „Trust Store-Verwaltung“ können Sie HSM-Berechtigungen (Hardware Security Module, Hardwaresicherheitsmodul) verwalten. Ein HSM ist ein PKCS#11-Gerät eines anderen Anbieters, mit dem Sie private Schlüssel sicher erzeugen und speichern können. Das HSM schützt den Zugriff auf die privaten Schlüssel und ihre Verwendung.

Die Clientsoftware ist für die Kommunikation mit dem HSM erforderlich. Die HSM-Clientsoftware muss auf demselben Computer wie AEM Forms installiert und konfiguriert werden.

AEM Forms Digital Signatures kann Berechtigungen verwenden, die in einem HSM gespeichert sind, um serverseitige digitale Signaturen anzuwenden. Befolgen Sie die Anweisungen in diesem Abschnitt, um einen Alias für jede HSM-Berechtigung zu erstellen, die Digital Signatures verwenden soll. Der Alias enthält alle vom HSM benötigten Parameter.

>[!NOTE]
>
>Nachdem Sie die HSM-Konfiguration geändert haben, müssen Sie den AEM Forms-Server neu starten.

## Alias für eine HSM-Berechtigung erstellen, wenn das HSM-Gerät online ist {#create-an-alias-for-an-hsm-credential-when-the-hsm-device-is-online}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „Trust Store-Verwaltung“ > „HSM-Berechtigungen“ und dann auf „Hinzufügen“.
1. Geben Sie in das Feld „Profilname“ eine Zeichenfolge zur Identifizierung des Alias ein. Dieser Wert wird als Eigenschaft für einige Digital Signatures-Vorgänge wie etwa das Signieren eines Signaturfelds verwendet.
1. Geben Sie in das Feld „PKCS11-Bibliothek“ den voll qualifizierten Pfad der HSM-Clientbibliothek auf dem Server ein. Beispiel: `c:\Program Files\LunaSA\cryptoki.dll`. In einer Clusterumgebung muss dieser Pfad für alle Server im Cluster identisch sein.
1. Klicken Sie auf „HSM-Verbindung testen“. Wenn AEM Forms eine Verbindung mit dem HSM-Gerät erstellen kann, wird eine Meldung angezeigt, dass das HSM verfügbar ist. Klicken Sie auf Weiter.
1. Verwenden Sie die Option „Tokenname“, „Steckplatz-ID“ oder „Steckplatzlistenindex“, um zu identifizieren, wo die Berechtigungen auf dem HSM gespeichert sind.

   * **Tokenname:** Entspricht dem Namen der HSM-Partition, die verwendet werden soll (z. B. HSMPART1).
   * **Steckplatz-ID:** Die Steckplatz-ID ist eine Steckplatzidentifizierung vom Typ „data type long“.
   * **Steckplatzlistenindex:** Wenn Sie die Option „Steckplatzlistenindex“ auswählen, stellen Sie die Steckplatzinfo auf eine Ganzzahl ein, die dem Steckplatz entspricht. Dies ist ein 0-basierter Index. Wenn daher der Client zuerst mit der Partition HSMPART1 registriert wird, wird auf HSMPART1 mit dem SlotListIndex-Wert 0 verwiesen.

1. Geben Sie in das Feld „Token-PIN“das für den Zugriff auf den HSM-Schlüssel benötigte Kennwort ein und klicken Sie auf „Weiter“.
1. Wählen Sie im Feld „Berechtigungen“ eine Berechtigung aus. Klicken Sie auf Speichern.

## Alias für eine HSM-Berechtigung erstellen, wenn das HSM-Gerät offline ist  {#create-an-alias-for-an-hsm-credential-when-the-hsm-device-is-offline}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „Trust Store-Verwaltung“ > „HSM-Berechtigungen“ und dann auf „Hinzufügen“.
1. Geben Sie in das Feld „Profilname“ eine Zeichenfolge zur Identifizierung des Alias ein. Dieser Wert wird als Eigenschaft für einige Digital Signatures-Vorgänge wie etwa das Signieren eines Signaturfelds verwendet.
1. Geben Sie in das Feld „PKCS11-Bibliothek“ den voll qualifizierten Pfad der HSM-Clientbibliothek auf dem Server ein. Beispiel: `c:\Program Files\LunaSA\cryptoki.dll`. In einer Clusterumgebung muss dieser Pfad für alle Server im Cluster identisch sein.
1. Aktivieren Sie das Kontrollkästchen „Offline Profilerstellung“. Klicken Sie auf Weiter.
1. Wählen Sie in der Liste „HSM-Gerät“ den Hersteller des HSM-Geräts aus, auf dem die Berechtigung gespeichert ist.
1. Wählen Sie in der Liste „Steckplatztyp“ den Eintrag „Steckplatz-ID“, „Steckplatzindex“ oder „Tokenname“ und geben Sie im Feld „Steckplatzinfo“ einen Wert an. AEM Forms stellt anhand dieser Einstellungen fest, wo die Berechtigungen auf dem HSM gespeichert sind.

   * **Tokenname:** Entspricht einem Partitionsnamen (z. B. HSMPART1).
   * **Steckplatz-ID:** Die Steckplatz-ID ist eine Ganzzahl, die dem Steckplatz entspricht, der wiederum einer Partition entspricht. Angenommen, der Client (Formularserver) hat sich zuerst bei der Partition HSMPART1 registriert. Damit wird für diesen Client Steckplatz 1 der Partition HSMPART1 zugeordnet. Da HSMPART1 die erste registrierte Partition ist, lautet die Steckplatz-ID 1 und Sie müssten als Steckplatzinfo ebenfalls 1 angeben.

      Die Steckplatz-ID wird für jeden Client einzeln festgelegt. Falls Sie einen zweiten Rechner bei einer anderen Partition registriert haben (z. B. HSMPART2 auf demselben HSM-Gerät), würde Steckplatz 1 für diesen Client mit der Partition HSMPART2 verknüpft.

   * **Steckplatzindex:** Wenn Sie die Option „Steckplatzindex“ auswählen, stellen Sie die Steckplatzinfo auf eine Ganzzahl ein, die dem Steckplatz entspricht. Dies ist ein 0-basierter Index, das heißt, wenn sich der Client zuerst bei der Partition HSMPART1 registriert hat, wird Steckplatz 1 für diesen Client der Partition HSMPART1 zugeordnet. Da HSMPART1 die erste registrierte Partition ist, hat „Steckplatzindex“ den Wert 0.

1. Wählen Sie eine dieser Optionen und geben Sie den Pfad an:

   * **Zertifikate**: (bei Verwendung von SHA 1 nicht erforderlich) Klicken Sie auf „Durchsuchen“ und suchen Sie den Pfad zu dem öffentlichen Schlüssel für die verwendete Berechtigung.
   * **Zertifikat SHA1:** (Bei Verwendung eines physischen Zertifikats nicht erforderlich) Geben Sie den SHA1-Wert (Thumbprint) der öffentlichen Schlüsseldatei (.cer) für die verwendete Berechtigung ein. Stellen Sie sicher, dass in dem SHA1-Wert keine Leerzeichen verwendet werden.

1. Geben Sie in das Feld „Kennwort“ das benötigte Kennwort für den Zugriff auf den HSM-Schlüssel für die angegebenen Steckplatzinformationen ein und klicken Sie dann auf „Speichern“.

## Eigenschaften von HSM-Berechtigungsaliassen anzeigen  {#view-hsm-credential-alias-properties}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „Trust Store-Verwaltung“ > „HSM-Berechtigungen“.
1. Klicken Sie zuerst auf den Aliasnamen des Berechtigungsalias, dessen Eigenschaften angezeigt werden sollen, und anschließend auf „OK“.

## Status einer HSM-Berechtigung überprüfen  {#check-the-status-of-an-hsm-credential}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „Trust Store-Verwaltung“ > „HSM-Berechtigungen“.
1. Aktivieren Sie das Kontrollkästchen neben der Berechtigung, die Sie überprüfen möchten, und klicken Sie auf „Status überprüfen“.

Die Spalte „Status“ gibt den aktuellen Status der Berechtigung an. Wenn es zu einem Fehler kommt, wird in der Spalte „Status“ in rotes X angezeigt. Bewegen Sie Ihre Maus über das X, um Quickinfos mit den Fehlerursachen anzuzeigen.

## Eigenschaften von HSM-Berechtigungsaliassen aktualisieren  {#update-hsm-credential-alias-properties}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „Trust Store-Verwaltung“ > „HSM-Berechtigungen“.
1. Klicken Sie auf den Aliasnamen des Berechtigungsalias.
1. Klicken Sie auf „Berechtigung aktualisieren“ und aktualisieren Sie die Einstellungen den Anforderungen entsprechend.

## Alle HSM-Verbindungen zurücksetzen  {#reset-all-hsm-connections}

Setzen Sie die offenen Verbindungen mit einem HSM-Gerät nach jeder Unterbrechung der Netzwerksitzung zwischen dem Formularserver und dem HSM-Gerät zurück. Unterbrechungen können beispielsweise aufgrund eines Netzwerkausfalls auftreten oder weil das HSM-Gerät für eine Softwareaktualisierung offline geschaltet wurde. Nach einer Unterbrechung sind die bestehenden Verbindungen nicht aktuell und alle Signierungsanfragen gegen diese Verbindungen schlagen fehl. Durch Verwenden der Option „Alle HSM-Verbindungen zurücksetzen“ werden die alten Verbindungen gelöscht.

1. Klicken Sie in Administration Console auf „Einstellungen“ > „Trust Store-Verwaltung“ > „HSM-Berechtigungen“.
1. Klicken Sie auf „Alle HSM-Verbindungen zurücksetzen“.

## HSM-Berechtigungsalias löschen  {#delete-an-hsm-credential-alias}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „Trust Store-Verwaltung“ > „HSM-Berechtigungen“.
1. Aktivieren Sie die Kontrollkästchen der zu löschenden HSM-Berechtigungen und klicken Sie erst auf „Löschen“ und anschließend auf „OK“.

## HSM-Remoteunterstützung konfigurieren  {#configure-remote-hsm-support}

AEM Forms verwendet einen webdienstbasierten IPC/RPC-Mechanismus. Über diesen Mechanismus kann AEM Forms ein auf einem Remotecomputer installiertes HSM verwenden. Um diese Funktion zu verwenden, installieren Sie den Webdienst auf dem Remotecomputer, auf dem das HSM installiert ist. Weitere Informationen finden Sie unter [Konfigurieren von HSM-Support für AEM Forms ES mit Sun JDK auf Windows 64-Bit-Plattform](https://kb2.adobe.com/cps/808/cpsid_80835.html).

Dieser Mechanismus unterstützt keine Online-Erstellung von HSM-Profilen oder Statusprüfungen. Allerdings gibt es zwei Möglichkeiten, HSM-Profile zu erstellen und Statusprüfungen auszuführen:

* Erstellen Sie eine AEM Forms-Clientberechtigung durch Übergabe des Zertifikats des Unterzeichners. Führen Sie die Schritte unter [Konfigurieren von HSM-Support für AEM Forms ES mit Sun JDK auf Windows 64-Bit-Plattform](https://kb2.adobe.com/cps/808/cpsid_80835.html) aus. Der Webdienst-Speicherort wird als Berechtigungseigenschaft übergeben. Offline-HSM-Profile, die entweder mit DER- oder SHA-1-Hexadezimal-Zertifikat erstellt wurden, werden ebenfalls unterstützt. Wenn Sie jedoch aus einer früheren Version von AEM Forms auf AEM Forms aktualisiert haben, nehmen Sie Clientänderungen vor, da die Berechtigung Zertifikats- und Webdienstinformationen enthielt.
* Der Speicherort des Webdienstes wird in Administration Console für den Signature-Dienst angegeben. (Siehe [Einstellungen des Signature-Dienstes](/help/forms/using/admin-help/configure-service-settings.md#signature-service-settings).) Hier enthielt der Client nur den Alias des HSM-Profils im Trust Store. Sie können diese Option nahtlos ohne Clientänderungen verwenden, auch wenn Sie aus einer früheren Version von AEM Forms auf AEM Forms aktualisiert haben. Diese Option unterstützt keine HSM-Profile, die ein SHA-1-Hexadezimal-Zertifikat verwenden.
