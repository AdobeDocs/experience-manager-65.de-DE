---
title: Verwalten der Konten eingeladener und lokaler Benutzer
description: Mit Document Security können Sie Konten eingeladener und lokaler Benutzer suchen, anzeigen, bearbeiten, sperren, entsperren und löschen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Document Security
exl-id: 23f71b34-a0cb-4664-bb8b-a60f33dc70d8
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '1196'
ht-degree: 4%

---

# Verwalten der Konten eingeladener und lokaler Benutzer {#managing-invited-and-local-user-accounts}

Verwenden Sie die Seite Eingeladene und lokale Benutzer , um eingeladene und lokale Benutzer zu verwalten. Diese Seite wird nur angezeigt, wenn die folgenden Anforderungen erfüllt sind:

* Sie sind ein Administrator, dem die Document Security-Rolle &quot;Eingeladene und lokale Benutzer verwalten&quot;und die Rolle &quot;Administration Console-Benutzer&quot;zugewiesen ist. (Siehe [Rollen erstellen und konfigurieren](/help/forms/using/admin-help/creating-configuring-roles.md#creating-and-configuring-roles).
* Die Registrierung eingeladener Benutzer ist aktiviert. (Siehe [Registrierung für eingeladene Benutzer konfigurieren](/help/forms/using/admin-help/configuring-client-server-options.md#configuring-invited-user-registration).

Die Seite Eingeladene und lokale Benutzer enthält zwei Registerkarten, mit denen Sie nach Konten eingeladener und lokaler Benutzer suchen, diese anzeigen, bearbeiten, sperren, entsperren und löschen können.

Sie können Registrierungs-E-Mails auch manuell an eingeladene Benutzer senden. Dies empfiehlt sich beispielsweise, wenn der von der E-Mail autorisierte Registrierungszeitraum endet und der Benutzer die URL nicht zur Registrierung verwenden kann. In diesem Fall können Sie eine Registrierungs-E-Mail an den eingeladenen Benutzer erneut senden. Wenn der eingeladene Benutzer das Konto registriert und aktiviert, wird er ein lokaler Benutzer.

>[!NOTE]
>
>Eingeladene Benutzer können auch direkt über den LDAP-Ordner hinzugefügt werden, auf den Document Security verweist. Dies ist auch der Fall, wenn ein Benutzer oder Administrator beim Erstellen oder Bearbeiten einer Richtlinie einen neuen Benutzer einlädt, wodurch eine Einladungs-E-Mail zur Registrierung initiiert wird. Benutzer können neue eingeladene Benutzer zu Richtlinien hinzufügen, wenn Sie die Option Registrierung für eingeladene Benutzer aktivieren auf der Seite Registrierung für eingeladene Benutzer aktivieren.

## Einen eingeladenen Benutzer hinzufügen {#add-an-invited-user}

Sie können Document Security gleichzeitig ein oder mehrere Konten eingeladener Benutzer hinzufügen. Um ein Konto für eingeladene Benutzer hinzuzufügen, benötigen Sie die E-Mail-Adresse des Benutzers. Wenn Sie einen Benutzer hinzufügen, sendet Document Security eine Registrierungs-E-Mail, in der der Benutzer zur Registrierung eingeladen wird.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Document Security&quot;> &quot;Eingeladene und lokale Benutzer&quot;und dann auf &quot;Neuen Benutzer einladen&quot;.
1. Geben Sie die E-Mail-Adressen der Benutzer ein, die Sie einladen möchten. Geben Sie mehrere Adressen in einer durch Kommas getrennten Zeile ein.

   Die Nachricht, die Sie beim Aktivieren der Registrierung für eingeladene Benutzer erstellt haben, wird an die Benutzer gesendet. (Siehe [Registrierung für eingeladene Benutzer konfigurieren](/help/forms/using/admin-help/configuring-client-server-options.md#configuring-invited-user-registration).

1. Klicken Sie auf OK.

## Informationen zu lokalen Benutzern anzeigen {#view-information-about-a-local-user}

Sie können Informationen zu lokalen Benutzern (Name, E-Mail-Adresse, Firma, Registrierungsstatus und Domain) anzeigen.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Document Security&quot;> &quot;Eingeladene und lokale Benutzer&quot;und dann auf &quot;Neuen Benutzer einladen&quot;.
1. Klicken Sie auf die Registerkarte Lokale Benutzer und anschließend auf der Seite Lokale Benutzer verwalten auf die E-Mail-Adresse des Benutzers, den Sie anzeigen möchten.

   Die Benutzerdetails werden angezeigt. Sie können das Kennwort des Benutzers zurücksetzen und das Konto deaktivieren.

## E-Mail an einen nicht registrierten externen Benutzer senden {#send-an-email-to-an-unregistered-external-user}

Wenn Sie einen eingeladenen Benutzer hinzufügen, sendet Document Security automatisch eine E-Mail-Registrierungsanfrage an den Benutzer. Sie können auch manuell eine Registrierungs-E-Mail generieren, die an einen eingeladenen Benutzer gesendet wird, der sich noch nicht registriert hat. Dies kann beispielsweise erforderlich sein, um eine neue Einladung zu senden, wenn die Registrierungs-E-Mail eines eingeladenen Benutzers abläuft.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Document Security&quot;> &quot;Eingeladene und lokale Benutzer&quot;.
1. Aktivieren Sie in der Benutzerliste das Kontrollkästchen für jeden Benutzer, an den eine Registrierungs-E-Mail gesendet werden soll, und klicken Sie dann auf Einladungs-E-Mail erneut senden .
1. Überprüfen Sie die Liste der ausgewählten Benutzer und klicken Sie auf OK.

## Kennwort eines lokalen Benutzers zurücksetzen {#reset-a-local-user-password}

Sie können Kennwörter für aktivierte eingeladene Benutzer zurücksetzen, die sich bei Document Security registriert, aber ihr Kennwort vergessen haben. Wenn Sie ein Kennwort zurücksetzen, wird eine E-Mail generiert, die ein neues temporäres Kennwort für den Benutzer enthält.

Wenn Sie den Registrierungsprozess für eingeladene Benutzer aktiviert haben, haben Sie eine E-Mail-Nachricht erstellt, die an Benutzer gesendet wird, die sie auffordern, ihre Kennwörter zurückzusetzen. (Siehe [Registrierung für eingeladene Benutzer konfigurieren](/help/forms/using/admin-help/configuring-client-server-options.md#configuring-invited-user-registration).

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Document Security&quot;> &quot;Eingeladene und lokale Benutzer&quot;und dann auf die Registerkarte &quot;Lokale Benutzer&quot;.
1. Wählen Sie in der Benutzerliste den entsprechenden Benutzer aus.
1. Klicken Sie auf der Seite &quot;Lokalen Benutzer verwalten&quot;auf Kennwort zurücksetzen und klicken Sie auf OK. Eine E-Mail zum Zurücksetzen des Kennworts, die das neue Kennwort enthält, wird an den Benutzer gesendet.

## Benutzerkonto aktivieren oder deaktivieren {#enable-or-disable-a-user-account}

Sie können lokale Benutzerkonten deaktivieren, um Benutzer vorübergehend daran zu hindern, sich bei Document Security anzumelden. Wenn Sie das Konto deaktivieren, kann der Benutzer keine richtliniengeschützten Dokumente verwenden oder Richtlinien erstellen oder anwenden.

Sie können ein lokales Benutzerkonto aktivieren, das derzeit deaktiviert ist. Sie können ein Konto für eingeladene Benutzer, das als registriert aufgeführt ist, nicht aktivieren. Der registrierte Status gibt an, dass der eingeladene Benutzer registriert, das Konto jedoch noch nicht über den Link in der Aktivierungs-E-Mail aktiviert wurde.

**Ein Benutzerkonto beschränken**

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Document Security&quot;> &quot;Eingeladene und lokale Benutzer&quot;und dann auf die Registerkarte &quot;Lokale Benutzer&quot;.
1. Wählen Sie in der Benutzerliste den entsprechenden Benutzer aus.
1. Klicken Sie auf der Seite &quot;Details für lokale Benutzer&quot;auf Konto deaktivieren .

**Benutzerkonto reaktivieren**

1. Klicken Sie auf Eingeladene und lokale Benutzer und dann auf die Registerkarte Lokale Benutzer .
1. Wählen Sie in der Benutzerliste den entsprechenden Benutzer aus.
1. Klicken Sie auf der Seite &quot;Details für lokale Benutzer&quot;auf Konto aktivieren .

## Ein Konto für eingeladene Benutzer entfernen {#remove-an-invited-user-account}

Sie können Konten eingeladener Benutzer aus Document Security löschen. Sie können beispielsweise ein Konto löschen, wenn ein Benutzer seine persönlichen E-Mail-Kontoinformationen ändert.

Wenn Sie ein Benutzerkonto löschen, können nur Sie oder ein anderer Administrator das Konto reaktivieren, indem Sie auf der Seite &quot;Eingeladene Benutzer&quot;die Option &quot;Eingeladenen Benutzer hinzufügen&quot;auswählen. Benutzer können das gelöschte Benutzerkonto nicht zu einer Richtlinie hinzufügen. Mit dieser Methode kann kein Einladungsprozess eingeleitet werden.

>[!NOTE]
>
>Eingeladene Benutzer, die über die Benutzeroberfläche für AEM Forms-Benutzerverwaltung gelöscht wurden, können erst wieder eingeladen werden, nachdem sie erneut mit dem folgenden Verfahren gelöscht wurden.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Document Security&quot;> &quot;Eingeladene und lokale Benutzer&quot;und dann auf die Registerkarte &quot;Eingeladene Benutzer&quot;.
1. Aktivieren Sie das Kontrollkästchen neben einem oder mehreren Benutzern und klicken Sie auf &quot;Löschen&quot;und anschließend auf &quot;OK&quot;.

## Nach einem Konto für eingeladene Benutzer suchen {#search-for-an-invited-user-account}

Sie können über eine E-Mail-Adresse nach Konten eingeladener Benutzer suchen.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Document Security&quot;> &quot;Eingeladene und lokale Benutzer&quot;.
1. Geben Sie in das Feld &quot;E-Mail suchen&quot;die E-Mail-Adresse des Benutzers ein und klicken Sie auf &quot;Suchen&quot;.

## Lokales Benutzerkonto suchen {#search-for-a-local-user-account}

Sie können über die E-Mail-Adresse, den Namen oder die Domain eines Benutzers nach lokalen Benutzern suchen.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Document Security&quot;> &quot;Eingeladene und lokale Benutzer&quot;und dann auf die Registerkarte &quot;Lokale Benutzer&quot;.
1. Geben Sie die Suchkriterien in das Feld &quot;Suchen&quot;ein, wählen Sie &quot;Name&quot;oder &quot;E-Mail&quot;und klicken Sie auf &quot;Suchen&quot;.

## Lokales Benutzerkonto entfernen {#remove-a-local-user-account}

Sie können lokale Benutzerkonten aus Document Security löschen. Sie können beispielsweise Konten löschen, wenn Benutzer ihre persönlichen E-Mail-Kontoinformationen ändern.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Document Security&quot;> &quot;Eingeladene und lokale Benutzer&quot;und dann auf die Registerkarte &quot;Lokale Benutzer&quot;.
1. Aktivieren Sie das Kontrollkästchen neben einem oder mehreren Benutzern und klicken Sie auf &quot;Löschen&quot;und anschließend auf &quot;OK&quot;.

## Sortieren der Benutzerliste {#sort-the-user-list}

Sie können Benutzer einfacher finden, indem Sie die Benutzerliste nach Spaltenüberschrift sortieren. Dreieckssymbole neben der Spaltenüberschrift geben an, welche Spalte derzeit zum Sortieren verwendet wird:

* Ein nach oben zeigendes Dreieck gibt eine aufsteigende Reihenfolge an.
* Ein nach unten zeigendes Dreieck gibt die absteigende Reihenfolge an.

   1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Document Security&quot;> &quot;Eingeladene und lokale Benutzer&quot;.
   1. Um eingeladene Benutzer zu sortieren, klicken Sie auf die Registerkarte Eingeladene Benutzer und dann auf die entsprechende Spaltenüberschrift.
   1. Um lokale Benutzer zu sortieren, klicken Sie auf die Registerkarte Lokale Benutzer und dann auf die gewünschte Spaltenüberschrift.
