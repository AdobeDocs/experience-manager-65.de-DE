---
title: Domänen hinzufügen
seo-title: Domänen hinzufügen
description: Erfahren Sie, wie Sie ein Unternehmen, eine lokale oder Hybriddomäne mithilfe der Einstellungen in Domain Management hinzufügen und allgmeine Gedanken zu Domänenamen und Ids.
seo-description: Erfahren Sie, wie Sie ein Unternehmen, eine lokale oder Hybriddomäne mithilfe der Einstellungen in Domain Management hinzufügen und allgmeine Gedanken zu Domänenamen und Ids.
uuid: 3ae1e5d4-ea5b-4e0b-be97-3957c3702d5f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: d4004ffe-c981-487d-b803-dc4492ae5998
exl-id: c708936d-7aa7-4b92-be2d-d97008f187d2
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '946'
ht-degree: 99%

---

# Domänen hinzufügen {#adding-domains}

## Eine Unternehmensdomäne hinzufügen {#add-an-enterprise-domain}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domänenverwaltung“.
1. Klicken Sie auf „Neue Unternehmensdomäne“.
1. Geben Sie in das Feld „ID“ einen eindeutigen Bezeichner für die Domäne und in das Feld „Name“ einen beschreibenden Namen für die Domäne ein. (Siehe [Wichtige Einstellungen für Domänennamen und IDs](adding-domains.md#important-considerations-for-domain-names-and-ids).)
1. Geben Sie an, ob die Kontosperrung aktiviert werden soll. (Siehe [Einstellungen für die Kontosperrung konfigurieren](/help/forms/using/admin-help/configure-account-locking-settings.md#configure-account-locking-settings).) Standardmäßig ist „Kontosperrung aktivieren“ ausgewählt.
1. Klicken Sie auf „Authentifizierung hinzufügen“ und wählen Sie in der Liste „Authentifizierungsanbieter“ einen der Authentifizierungsmethode Ihres Unternehmens entsprechenden Anbieter aus. Mögliche Werte sind LDAP, Kerberos, SAML oder ein benutzerdefinierter Authentifizierungsanbieter.

   Wenn Sie LDAP auswählen, können Sie den in Ihrer Ordnerkonfiguration angegebenen LDAP-Server verwenden. Sie können aber auch einen anderen LDAP-Server auswählen, der zur Authentifizierung verwendet werden soll. Wenn Sie einen anderen Server auswählen, müssen Ihre Benutzer auf beiden LDAP-Servern vorhanden sein.

1. Geben Sie weitere auf dieser Seite angeforderte Informationen ein. (Siehe [Authentifizierungseinstellungen](/help/forms/using/admin-help/configuring-authentication-providers.md#authentication-settings).)
1. Erstellen Sie einen Ordner oder ein benutzerdefiniertes Service Provider Interface (SPI). (Siehe [Ordner oder benutzerdefinierten SPIs hinzufügen](/help/forms/using/admin-help/configuring-directories.md#adding-directories-or-custom-spis).)
1. Klicken Sie auf „Fertig stellen“ und dann auf „OK“.

Nach dem Erstellen einer Unternehmensdomäne müssen Sie den Ordner manuell synchronisieren oder einen Trigger für die Synchronisierung erstellen, bevor User Management den Ordner verwenden kann. Danach können Sie einen Zeitplan für die Ordnersynchronisierung einrichten und bei Bedarf eine manuelle Synchronisierung durchführen. (Siehe [Ordner synchronisieren](/help/forms/using/admin-help/synchronizing-directories.md#synchronizing-directories).)

## Eine lokale Domäne hinzufügen {#add-a-local-domain}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domänenverwaltung“.
1. Klicken Sie auf „Neue lokale Domäne“.
1. Geben Sie in das Feld ID einen eindeutigen Bezeichner für die Domäne ein und in das Feld Name einen beschreibenden Namen für die Domäne. (Siehe [Wichtige Einstellungen für Domänennamen und IDs](adding-domains.md#important-considerations-for-domain-names-and-ids).)
1. Geben Sie an, ob die Kontosperrung aktiviert werden soll, und klicken Sie auf „OK“. (Siehe [Einstellungen für die Kontosperrung konfigurieren](/help/forms/using/admin-help/configure-account-locking-settings.md#configure-account-locking-settings).) Standardmäßig ist „Kontosperrung aktivieren“ ausgewählt.

## Hybriddomäne hinzufügen  {#add-a-hybrid-domain}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domänenverwaltung“.
1. Klicken Sie auf „Neue Hybriddomäne“.
1. Geben Sie in das Feld ID einen eindeutigen Bezeichner für die Domäne ein und in das Feld Name einen beschreibenden Namen für die Domäne. (Siehe [Wichtige Einstellungen für Domänennamen und IDs](adding-domains.md#important-considerations-for-domain-names-and-ids).)
1. Klicken Sie auf „Authentifizierung hinzufügen“ und wählen Sie in der Liste „Authentifizierungsanbieter“ einen der Authentifizierungsmethode Ihres Unternehmens entsprechenden Anbieter aus. Mögliche Werte sind LDAP, Kerberos, SAML oder ein benutzerdefinierter Authentifizierungsanbieter.
1. Geben Sie weitere auf dieser Seite angeforderte Informationen ein. (Siehe [Authentifizierungseinstellungen](/help/forms/using/admin-help/configuring-authentication-providers.md#authentication-settings).)
1. Klicken Sie auf „OK“ und dann erneut auf „OK“.

## Wichtige Einstellungen für Domänennamen und IDs  {#important-considerations-for-domain-names-and-ids}

Beachten Sie beim Auswählen eines Domänennamens und einer ID die folgenden Einstellungen:

### Allgemeine Überlegungen:{#general-considerations}

* Bei Nutzung anderer Datenbankanbieter als DB2 darf die Domänen-ID maximal 50 Byte umfassen. Wenn Sie Einzelbyte-Zeichen (ASCII) verwenden, beträgt die Grenze 50 Zeichen. Enthält der Domänenbezeichner Multibyte-Zeichen, verringert sich dieser Grenzwert. Wenn Sie beispielsweise eine Domäne erstellen, deren Bezeichner 3-Byte-Zeichen enthält, beträgt der Grenzwert 16 Zeichen. Das Erstellen von Domänen, deren Bezeichner 4-Byte-Zeichen enthalten, ist nicht möglich. Wenn Sie eine Domänen-ID erstellen, die diese Grenze überschreitet, versetzt dies AEM Forms in einen instabilen Zustand. Weitere Informationen zum Wiederherstellen des Systems aus diesem instabilen Zustand finden Sie unter [Eine Domäne, die erweiterte Zeichen oder Multibyte-Zeichen enthält, entfernen](adding-domains.md#remove-a-domain-that-contains-extended-or-multi-byte-characters) auf dieser Seite.
* Die Anzahl sowohl von Unternehmens- als auch von lokalen Domänen, die in AEM Forms erstellt werden können, ist von der Länge jeder einzelnen Domänen-ID abhängig. Wenn Sie eine Unternehmens- oder Hybriddomäne hinzufügen, aktualisiert User Management die Zeichenfolge „configInstance“ im „AuthProviders“-Knoten der AEM Forms-Konfigurationsdatei (config.xml). Die Zeichenfolge „configInstance“ enthält eine durch Doppelpunkt getrennte Liste der absoluten Pfade aller Domänen, die dem Autorisierungsanbieter zugeordnet sind. Diese Zeichenfolge ist auf 8192 Zeichen begrenzt. Wenn diese Grenze erreicht ist, können Sie keine zusätzlichen Domänen erstellen.

### Überlegungen bei der Verwendung von DB2  {#considerations-when-using-db2}

Bei Verwendung von DB2 als AEM Forms-Datenbank hängt die maximal zulässige Länge der Domänen-ID von dem verwendeten Zeichentyp ab:

* 100 Einzelbyte-Zeichen (ASCII) (z. B. in Englisch, Französisch oder Deutsch verwendete Zeichen)
* 50 Doppelbyte-Zeichen (z. B. in Chinesisch, Japanisch oder Koreanisch verwendete Zeichen)
* 25 Vierbyte-Zeichen (z. B. in traditionellem Chinesisch verwendete Zeichen)

### Überlegungen bei der Verwendung von MySQL  {#considerations-when-using-mysql}

Wenn Sie MySQL als AEM Forms-Datenbank verwenden, gelten die folgenden Einschränkungen:

* Für die Domänen-ID und den Domänennamen dürfen nur Einzelbyte-Zeichen (ASCII) verwendet werden. Wenn Sie erweiterte ASCII-Zeichen verwenden, befindet sich AEM Forms in einem instabilen Zustand und erzeugt möglicherweise eine Ausnahme, wenn Sie versuchen, die Domäne zu löschen. Weitere Informationen zum Wiederherstellen des Systems aus diesem instabilen Zustand finden Sie unter [Eine Domäne, die erweiterte Zeichen oder Multibyte-Zeichen enthält, entfernen](adding-domains.md#remove-a-domain-that-contains-extended-or-multi-byte-characters) auf dieser Seite.
* Sie können nicht zwei Domänen mit demselben Namen, aber unterschiedlicher Groß-/Kleinschreibung erstellen. Der Versuch, die Domäne *Adobe* zu erstellen, wenn die Domäne *adobe* bereits vorhanden ist, führt zu einer Fehlermeldung.
* User Management kann nicht zwischen zwei Domänennamen unterscheiden, die sich nur in der Verwendung erweiterter Zeichen unterscheiden. Wenn Sie beispielsweise eine Domäne namens *abcde* und eine namens *âbcdè* erstellen, gelten diese Namen als identisch.

### Eine Domäne, die erweiterte Zeichen oder Multibyte-Zeichen enthält, entfernen {#remove-a-domain-that-contains-extended-or-multi-byte-characters}

1. Exportieren Sie die Konfigurationsdatei, wie unter [Konfigurationsdatei importieren und exportieren](/help/forms/using/admin-help/importing-exporting-configuration-file.md#importing-and-exporting-the-configuration-file) beschrieben.
1. Öffnen Sie die Konfigurationsdatei und suchen Sie unter dem Knoten „Domänen“ den Knoten, dessen Namensattribut mit dem Namen der Domäne, die mit erweiterten Zeichen oder Multibyte-Zeichen erstellt wurde, übereinstimmt. Löschen Sie den gesamten Knoten für diese Domäne.
1. Suchen Sie in Ihrer Datenbank die Domäne in der Tabelle „edcprincipaldomainentity“:

   * Wählen Sie `*` aus edcprincipaldomainentity.
   * Suchen Sie den Domänennamen, der erweiterte Zeichen oder Multibyte-Zeichen enthält, und legen Sie den Status auf „OBSOLETE“ fest.

1. Importieren Sie die aktualisierte Konfigurationsdatei, wie unter [Konfigurationsdatei importieren und exportieren](/help/forms/using/admin-help/importing-exporting-configuration-file.md#importing-and-exporting-the-configuration-file) beschrieben.
