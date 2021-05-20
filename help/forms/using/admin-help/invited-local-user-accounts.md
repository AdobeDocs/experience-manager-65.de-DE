---
title: Konten eingeladener und lokaler Benutzer verwalten
seo-title: Konten eingeladener und lokaler Benutzer verwalten
description: Unter Verwendung von Document Security können Sie nach eingeladenen und lokalen Benutzerkonten suchen, diese anzeigen, bearbeiten, sperren, entsperren und löschen.
seo-description: Unter Verwendung von Document Security können Sie nach eingeladenen und lokalen Benutzerkonten suchen, diese anzeigen, bearbeiten, sperren, entsperren und löschen.
uuid: 0d0c717a-6e6e-4e42-96eb-3a7166e215ab
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 65720eed-ab06-463f-9567-2fdc468b6219
feature: Dokumentensicherheit
exl-id: 23f71b34-a0cb-4664-bb8b-a60f33dc70d8
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1222'
ht-degree: 100%

---

# Konten eingeladener und lokaler Benutzer verwalten {#managing-invited-and-local-user-accounts}

Auf der Seite „Eingeladene und lokale Benutzer“ können Sie eingeladene und lokale Benutzer verwalten. Diese Seite wird nur angezeigt, wenn die folgenden Voraussetzungen erfüllt sind:

* Wenn Sie ein Administrator sind, dem die Document Security-Rolle „Eingeladene und lokale Benutzer verwalten“ und „Administration Console-Benutzer“ zugewiesen wurde. (Siehe [Rollen erstellen und konfigurieren](/help/forms/using/admin-help/creating-configuring-roles.md#creating-and-configuring-roles).)
* Wenn die Registrierung für eingeladene Benutzer aktiviert ist. (Siehe [Registrierung für eingeladene Benutzer konfigurieren](/help/forms/using/admin-help/configuring-client-server-options.md#configuring-invited-user-registration).)

Die Seite „Eingeladene und lokale Benutzer“ enthält zwei Registerkarten, die Sie zum Suchen, Anzeigen, Bearbeiten, Sperren, Entsperren und Löschen von Konten eingeladener und lokaler Benutzer verwenden können.

Sie können auch Registrierungs-E-Mails manuell an eingeladene Benutzer senden. Dies ist z. B. erforderlich, wenn der von der E-Mail zugelassene Registrierungszeitraum abgelaufen ist und der Benutzer sich nicht über die URL registrieren kann. In diesem Fall können Sie erneut eine Registrierungs-E-Mail an den eingeladenen Benutzer senden. Nachdem ein eingeladener Benutzer sich registriert und sein Konto aktiviert hat, wird er ein lokaler Benutzer.

>[!NOTE]
>
>Eingeladene Benutzer können auch direkt über den LDAP-Ordner hinzugefügt werden, auf den Document Security verweist. Dies ist auch möglich, wenn ein Benutzer oder Administrator beim Erstellen oder Bearbeiten einer Richtlinie einen neuen Benutzer einlädt, wodurch eine Einladungs-E-Mail zur Registrierung ausgelöst wird. Benutzer können neue eingeladene Benutzer zu Richtlinien hinzufügen, wenn Sie auf der Seite „Registrierung für eingeladene Benutzer“ die Option „Registrierung für eingeladene Benutzer aktivieren“ aktivieren.

## Einen eingeladenen Benutzer hinzufügen {#add-an-invited-user}

Sie können Document Security ein oder mehrere Konten für eingeladene Benutzer gleichzeitig hinzufügen. Um das Konto eines eingeladenen Benutzers hinzuzufügen, benötigen Sie die E-Mail-Adresse des Benutzers. Wenn Sie einen Benutzer hinzufügen, sendet Document Security eine Registrierungs-E-Mail, die den Benutzer zur Registrierung einlädt.

1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Eingeladene und lokale Benutzer“ und dann auf die Registerkarte „Neuen Benutzer einladen“.
1. Geben Sie die E-Mail-Adressen der Benutzer ein, die Sie einladen möchten. Geben Sie mehrere Adressen in eine Zeile getrennt durch Kommas ein.

   Die Nachricht, die Sie beim Aktivieren der Registrierung für eingeladene Benutzer erstellt haben, wird an die Benutzer gesendet. (Siehe [Registrierung für eingeladene Benutzer konfigurieren](/help/forms/using/admin-help/configuring-client-server-options.md#configuring-invited-user-registration).)

1. Klicken Sie auf OK.

## Informationen zu lokalen Benutzern anzeigen  {#view-information-about-a-local-user}

Sie können Informationen zu lokalen Benutzern (Name, E-Mail-Adresse, Firma, Registrierungsstatus und Domäne) anzeigen.

1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Eingeladene und lokale Benutzer“ und dann auf die Registerkarte „Neuen Benutzer einladen“.
1. Klicken Sie auf die Registerkarte „Lokale Benutzer“ und auf der Seite „Lokale Benutzer verwalten“ auf die E-Mail-Adresse des Benutzers, den Sie anzeigen möchten.

   Die Benutzerdetails werden angezeigt und Sie können das Kennwort des Benutzers zurücksetzen und das Konto deaktivieren.

## Eine E-Mail an einen nicht registrierten externen Benutzer senden  {#send-an-email-to-an-unregistered-external-user}

Wenn Sie einen eingeladenen Benutzer hinzufügen, sendet Document Security automatisch eine E-Mail mit einer Registrierungsaufforderung an den Benutzer. Sie können eine Registrierungs-E-Mail auch manuell generieren, die an einen eingeladenen Benutzer gesendet wird, der sich noch nicht registriert hat. Dies kann z. B. erforderlich sein, um eine neue Einladung zu senden, wenn die Registrierungs-E-Mail eines eingeladenen Benutzers abgelaufen ist.

1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security“ > „Eingeladene und lokale Benutzer“.
1. Aktivieren Sie in der Benutzerliste die Kontrollkästchen der Benutzer, an die Sie eine Registrierungs-E-Mail senden möchten, und klicken Sie auf „E-Mail-Einladung erneut senden“.
1. Überprüfen Sie die Liste der ausgewählten Benutzer und klicken Sie auf „OK“.

## Kennwörter lokaler Benutzer zurücksetzen  {#reset-a-local-user-password}

Sie können Kennwörter aktivierter eingeladener Benutzer zurücksetzen, die sich bei Document Security registriert, aber ihr Kennwort vergessen haben. Wenn Sie ein Kennwort zurücksetzen, wird eine E-Mail mit einem neuen temporären Kennwort für den Benutzer generiert.

Wenn Sie den Prozess „Registrierung für eingeladene Benutzer“ aktiviert haben, wurde eine E-Mail-Nachricht erstellt, die an Benutzer mit der Aufforderung gesendet wird, ihre Kennwörter zurückzusetzen. (Siehe [Registrierung für eingeladene Benutzer konfigurieren](/help/forms/using/admin-help/configuring-client-server-options.md#configuring-invited-user-registration).)

1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security“ > „Eingeladene und lokale Benutzer“ und dann auf die Registerkarte „Lokale Benutzer“.
1. Wählen Sie in der Liste den gewünschten Benutzer aus.
1. Klicken Sie auf der Seite „Lokale Benutzer verwalten“ auf „Kennwort zurücksetzen“ und dann auf „OK“. Eine E-Mail zum Zurücksetzen des Kennworts wird mit dem neuen Kennwort an den Benutzer gesendet.

## Benutzerkonten aktivieren oder deaktivieren  {#enable-or-disable-a-user-account}

Sie können lokale Benutzerkonten deaktivieren, wenn Sie einen Benutzer vorübergehend an der Anmeldung bei Document Security hindern möchten. Wenn Sie das Konto deaktivieren, kann der Benutzer keine richtliniengeschützten Dokumente verwenden bzw. keine Richtlinien erstellen oder anwenden.

Sie können ein deaktiviertes lokales Benutzerkonto wieder aktivieren. Sie können das Konto eines eingeladenen Benutzers, der als registriert aufgelistet ist, nicht aktivieren. Der registrierte Status bedeutet, dass der eingeladene Benutzer sich zwar registriert, das Konto aber noch nicht über den Hyperlink in der Aktivierungs-E-Mail aktiviert hat.

**Ein Benutzerkonto beschränken**

1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security“ > „Eingeladene und lokale Benutzer“ und dann auf die Registerkarte „Lokale Benutzer“.
1. Wählen Sie in der Liste den gewünschten Benutzer aus.
1. Klicken Sie auf der Seite „Details für lokale Benutzer“ auf „Konto deaktivieren“.

**Ein Benutzerkonto reaktivieren**

1. Klicken Sie auf „Eingeladene und lokale Benutzer“ und dann auf die Registerkarte „Lokale Benutzer“.
1. Wählen Sie in der Liste den gewünschten Benutzer aus.
1. Klicken Sie auf der Seite „Details für lokale Benutzer“ auf „Konto aktivieren“.

## Das Konto eines eingeladenen Benutzers entfernen  {#remove-an-invited-user-account}

Sie können Konten eingeladener Benutzer aus Document Security löschen. Sie müssen ein Konto ggf. löschen, wenn Benutzer ihre persönlichen E-Mail-Kontoinformationen ändern.

Wenn Sie ein Benutzerkonto löschen, können nur Sie oder ein anderer Administrator das Konto auf der Seite „Eingeladene Benutzer“ über die Option „Eingeladenen Benutzer hinzufügen“ reaktivieren. Benutzer können das gelöschte Benutzerkonto keiner Richtlinie hinzufügen und über diese Methode kann kein Einladungsvorgang eingeleitet werden.

>[!NOTE]
>
>Eingeladene Benutzer, die über die AEM Forms User Management-Schnittstelle gelöscht wurden, können nicht erneut eingeladen werden, bis sie erneut mit dem folgenden Verfahren gelöscht wurden.

1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security“ > „Eingeladene und lokale Benutzer“ und dann auf die Registerkarte „Eingeladene Benutzer“.
1. Aktivieren Sie das Kontrollkästchen des Benutzers bzw. den Benutzern und klicken Sie auf „Löschen“ und anschließend auf „OK“.

## Nach einem Konto für eingeladene Benutzer suchen  {#search-for-an-invited-user-account}

Sie können über eine E-Mail-Adresse nach Konten eingeladener Benutzer suchen.

1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security“ > „Eingeladene und lokale Benutzer“.
1. Geben Sie in das Feld „E-Mail suchen“ die E-Mail-Adresse des Benutzers ein und klicken Sie auf „Suchen“.

## Nach einem Konto für lokale Benutzer suchen  {#search-for-a-local-user-account}

Sie können über die E-Mail-Adresse, den Namen oder die Domäne eines Benutzers nach lokalen Benutzern suchen.

1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security“ > „Eingeladene und lokale Benutzer“ und dann auf die Registerkarte „Lokale Benutzer“.
1. Geben Sie die Suchkriterien in das Feld „Suchen“ ein, wählen Sie „Name“ oder „E-Mail“ aus und klicken Sie auf „Suchen“.

## Ein lokales Benutzerkonto entfernen  {#remove-a-local-user-account}

Sie können Konten lokaler Benutzer aus Document Security löschen. Sie müssen Konten ggf. löschen, wenn Benutzer ihre persönlichen E-Mail-Kontoinformationen ändern.

1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security“ > „Eingeladene und lokale Benutzer“ und dann auf die Registerkarte „Lokale Benutzer“.
1. Aktivieren Sie das Kontrollkästchen des Benutzers bzw. den Benutzern und klicken Sie auf „Löschen“ und anschließend auf „OK“.

## Die Benutzerliste sortieren  {#sort-the-user-list}

Sie können Benutzer einfacher finden, indem Sie die Benutzerliste nach Spaltenüberschrift sortieren. Ein Dreieckssymbol neben der Spaltenüberschrift gibt an, nach welcher Spalte gegenwärtig sortiert wird:

* Ein nach oben zeigendes Dreieck gibt eine aufsteigende Reihenfolge an.
* Ein nach unten zeigendes Dreieck gibt eine absteigende Reihenfolge an.

   1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security“ > „Eingeladene und lokale Benutzer“.
   1. Um eingeladene Benutzer zu sortieren, klicken Sie auf die Registerkarte „Eingeladene Benutzer“ und anschließend auf die gewünschte Spaltenüberschrift.
   1. Um lokale Benutzer zu sortieren, klicken Sie auf die Registerkarte „Lokale Benutzer“ und anschließend auf die gewünschte Spaltenüberschrift.
