---
title: Verwalten der Konten eingeladener und lokaler Benutzer
description: Mithilfe der Dokumentensicherheit können Sie nach eingeladenen und lokalen Benutzerkonten suchen und diese anzeigen, bearbeiten, sperren, entsperren oder löschen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Document Security
exl-id: 23f71b34-a0cb-4664-bb8b-a60f33dc70d8
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '1196'
ht-degree: 100%

---

# Verwalten der Konten eingeladener und lokaler Benutzer {#managing-invited-and-local-user-accounts}

Auf der Seite „Eingeladene und lokale Benutzer“ können Sie eingeladene und lokale Benutzende verwalten. Diese Seite wird nur angezeigt, wenn die folgenden Voraussetzungen erfüllt sind:

* Sie sind Admin mit der in der Dokumentensicherheit zugewiesenen Rolle „Eingeladene und lokale Benutzer verwalten“ und „Administrationskonsolen-Benutzer“. (Siehe [Erstellen und Konfigurieren von Rollen](/help/forms/using/admin-help/creating-configuring-roles.md#creating-and-configuring-roles).)
* Die Registrierung für eingeladene Benutzende ist aktiviert. (Siehe [Konfigurieren der Registrierung für eingeladene Benutzende](/help/forms/using/admin-help/configuring-client-server-options.md#configuring-invited-user-registration).)

Die Seite „Eingeladene und lokale Benutzer“ enthält zwei Registerkarten, die Sie zum Suchen, Anzeigen, Bearbeiten, Sperren, Entsperren und Löschen von eingeladenen und lokalen Benutzerkonten verwenden können.

Sie können Registrierungs-E-Mails auch manuell an eingeladene Benutzende senden. Dies empfiehlt sich beispielsweise, wenn der von der E-Mail zugelassene Registrierungszeitraum abgelaufen ist und die Person sich nicht über die URL registrieren kann. In diesem Fall können Sie erneut eine Registrierungs-E-Mail an die eingeladene Person senden. Nachdem eingeladene Benutzende sich registriert und ihr Konto aktiviert haben, werden sie lokale Benutzende.

>[!NOTE]
>
>Eingeladene Benutzende können auch direkt über das LDAP-Verzeichnis hinzugefügt werden, auf das die Dokumentensicherheit verweist. Dies ist auch möglich, wenn Benutzende oder Admins beim Erstellen oder Bearbeiten einer Richtlinie eine neue Person einladen, wodurch eine Einladungs-E-Mail zur Registrierung ausgelöst wird. Benutzende können neue eingeladene Benutzende zu Richtlinien hinzufügen, wenn Sie auf der Seite „Registrierung für eingeladene Benutzer“ die Option „Registrierung für eingeladene Benutzer aktivieren“ aktivieren.

## Hinzufügen von eingeladenen Benutzenden {#add-an-invited-user}

Sie können ein oder mehrere eingeladene Benutzerkonten gleichzeitig zur Dokumentensicherheit hinzufügen. Um ein eingeladenes Benutzerkonto hinzuzufügen, benötigen Sie die E-Mail-Adresse der Person. Wenn Sie Benutzende hinzufügen, sendet die Dokumentensicherheit eine Registrierungs-E-Mail, die die Benutzenden zur Registrierung einlädt. 

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Eingeladene und lokale Benutzer“ und dann auf die Registerkarte „Neuen Benutzer einladen“.
1. Geben Sie die E-Mail-Adressen der Benutzenden ein, die Sie einladen möchten. Geben Sie mehrere Adressen in eine Zeile getrennt durch Kommas ein.

   Die Nachricht, die Sie beim Aktivieren der Registrierung für eingeladene Benutzende erstellt haben, wird an die Benutzenden gesendet. (Siehe [Konfigurieren der Registrierung für eingeladene Benutzende](/help/forms/using/admin-help/configuring-client-server-options.md#configuring-invited-user-registration).)

1. Klicken Sie auf OK.

## Anzeigen von Informationen zu lokalen Benutzenden {#view-information-about-a-local-user}

Sie können Informationen zu lokalen Benutzern (Name, E-Mail-Adresse, Firma, Registrierungsstatus und Domain) anzeigen.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Document Security“ > „Konfiguration“ > „Eingeladene und lokale Benutzer“ und dann auf die Registerkarte „Neuen Benutzer einladen“.
1. Klicken Sie auf die Registerkarte „Lokale Benutzer“ und auf der Seite „Lokale Benutzer verwalten“ auf die E-Mail-Adresse der Person, die Sie anzeigen möchten.

   Die Benutzerdetails werden angezeigt und Sie können das Kennwort der Person zurücksetzen und das Konto deaktivieren.

## Senden einer E-Mail an nicht registrierte externe Benutzende {#send-an-email-to-an-unregistered-external-user}

Wenn Sie eingeladene Benutzende hinzufügen, sendet die Dokumentensicherheit automatisch eine E-Mail mit einer Registrierungsaufforderung an die Benutzerin oder den Benutzer. Sie können auch manuell eine Registrierungs-E-Mail generieren, die an eingeladene Benutzende gesendet wird, die sich noch nicht registriert haben. Dies kann beispielsweise erforderlich sein, um eine neue Einladung zu senden, wenn die Registrierungs-E-Mail einer eingeladenen Person abläuft.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Document Security“ > „Eingeladene und lokale Benutzer“.
1. Aktivieren Sie in der Benutzerliste die Kontrollkästchen für die Personen, an die Sie eine Registrierungs-E-Mail senden möchten, und klicken Sie auf „E-Mail-Einladung erneut senden“.
1. Überprüfen Sie die Liste der ausgewählten Benutzenden und klicken Sie auf „OK“.

## Zurücksetzen des Kennworts lokaler Benutzender {#reset-a-local-user-password}

Sie können Kennwörter aktivierter eingeladener Benutzender zurücksetzen, die sich bei der Dokumentensicherheit registriert, aber ihr Kennwort vergessen haben. Wenn Sie ein Kennwort zurücksetzen, wird eine E-Mail mit einem neuen temporären Kennwort für die Person generiert.

Als Sie den Prozess zur Registrierung für eingeladene Benutzende aktiviert haben, wurde eine E-Mail-Nachricht erstellt, die an Benutzende mit der Aufforderung gesendet wird, ihre Kennwörter zurückzusetzen. (Siehe [Konfigurieren der Registrierung für eingeladene Benutzende](/help/forms/using/admin-help/configuring-client-server-options.md#configuring-invited-user-registration).)

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Document Security“ > „Eingeladene und lokale Benutzer“ und dann auf die Registerkarte „Lokale Benutzer“.
1. Wählen Sie in der Benutzerliste die gewünschte Person aus.
1. Klicken Sie auf der Seite „Lokale Benutzer verwalten“ auf „Kennwort zurücksetzen“ und dann auf „OK“. Eine E-Mail zum Zurücksetzen des Kennworts wird mit dem neuen Kennwort an die Person gesendet.

## Aktivieren oder Deaktivieren eines Benutzerkontos {#enable-or-disable-a-user-account}

Sie können lokale Benutzerkonten deaktivieren, wenn Sie eine Person vorübergehend an der Anmeldung bei der Dokumentensicherheit hindern möchten. Wenn Sie das Konto deaktivieren, kann die Person keine richtliniengeschützten Dokumente verwenden und auch keine Richtlinien erstellen oder anwenden.

Sie können ein deaktiviertes lokales Benutzerkonto wieder aktivieren. Sie können das Konto einer eingeladenen Person, die als registriert aufgelistet ist, nicht aktivieren. Der Status „registriert“ bedeutet, dass die eingeladene Person sich zwar registriert, ihr Konto aber noch nicht über den Hyperlink in der Aktivierungs-E-Mail aktiviert hat.

**Beschränken eines Benutzerkontos**

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Document Security“ > „Eingeladene und lokale Benutzer“ und dann auf die Registerkarte „Lokale Benutzer“.
1. Wählen Sie in der Benutzerliste die gewünschte Person aus.
1. Klicken Sie auf der Seite „Details für lokale Benutzer“ auf „Konto deaktivieren“.

**Reaktivieren eines Benutzerkontos**

1. Klicken Sie auf „Eingeladene und lokale Benutzer“ und dann auf die Registerkarte „Lokale Benutzer“.
1. Wählen Sie in der Benutzerliste die gewünschte Person aus.
1. Klicken Sie auf der Seite „Details für lokale Benutzer“ auf „Konto aktivieren“.

## Entfernen von Konten eingeladener Benutzender {#remove-an-invited-user-account}

Sie können die Konten eingeladener Benutzender aus der Dokumentensicherheit löschen. Sie müssen ein Konto ggf. löschen, wenn Benutzende ihre persönlichen E-Mail-Kontoinformationen ändern.

Wenn Sie ein Benutzerkonto löschen, können nur Sie oder andere Admins das Konto auf der Seite „Eingeladene Benutzer“ über die Option „Eingeladene Benutzer hinzufügen“ reaktivieren. Benutzende können das gelöschte Benutzerkonto zu keiner Richtlinie hinzufügen, und über diese Methode kann kein Einladungsvorgang eingeleitet werden.

>[!NOTE]
>
>Eingeladene Benutzende, die über die User Management-Schnittstelle von AEM Forms gelöscht wurden, können so lange nicht erneut eingeladen werden, bis sie erneut mit dem folgenden Verfahren gelöscht wurden.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Document Security“ > „Eingeladene und lokale Benutzer“ und dann auf die Registerkarte „Eingeladene Benutzer“.
1. Wählen Sie die Kontrollkästchen der Personen aus und klicken Sie auf „Löschen“ und anschließend auf „OK“.

## Suchen nach einem Konto für eingeladene Benutzende {#search-for-an-invited-user-account}

Sie können über eine E-Mail-Adresse nach Konten eingeladener Benutzender suchen.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Document Security“ > „Eingeladene und lokale Benutzer“.
1. Geben Sie in das Feld „E-Mail suchen“ die E-Mail-Adresse der Person ein und klicken Sie auf „Suchen“.

## Suchen nach einem lokalen Benutzerkonto {#search-for-a-local-user-account}

Sie können über die E-Mail-Adresse, den Namen oder die Domain eines Benutzers nach lokalen Benutzern suchen.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Document Security“ > „Eingeladene und lokale Benutzer“ und dann auf die Registerkarte „Lokale Benutzer“.
1. Geben Sie die Suchkriterien in das Feld „Suchen“ ein, wählen Sie „Name“ oder „E-Mail“ aus und klicken Sie auf „Suchen“.

## Entfernen eines lokalen Benutzerkontos {#remove-a-local-user-account}

Sie können lokale Benutzerkonten aus der Dokumentensicherheit löschen. Sie müssen Konten ggf. löschen, wenn Benutzende ihre persönlichen E-Mail-Kontoinformationen ändern.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Document Security“ > „Eingeladene und lokale Benutzer“ und dann auf die Registerkarte „Lokale Benutzer“.
1. Wählen Sie die Kontrollkästchen der Personen aus und klicken Sie auf „Löschen“ und anschließend auf „OK“.

## Sortieren der Benutzerliste {#sort-the-user-list}

Sie können Benutzende einfacher finden, indem Sie die Benutzerliste nach Spaltenüberschrift sortieren. Ein Dreieckssymbol neben der Spaltenüberschrift gibt an, nach welcher Spalte gegenwärtig sortiert wird:

* Ein nach oben zeigendes Dreieck gibt eine aufsteigende Reihenfolge an.
* Ein nach unten zeigendes Dreieck gibt eine absteigende Reihenfolge an.

   1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Document Security“ > „Eingeladene und lokale Benutzer“.
   1. Um eingeladene Benutzende zu sortieren, klicken Sie auf die Registerkarte „Eingeladene Benutzer“ und anschließend auf die gewünschte Spaltenüberschrift.
   1. Um lokale Benutzende zu sortieren, klicken Sie auf die Registerkarte „Lokale Benutzer“ und anschließend auf die gewünschte Spaltenüberschrift.
