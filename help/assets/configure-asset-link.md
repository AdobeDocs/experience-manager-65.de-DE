---
title: Konfigurieren von Experience Manager Assets für Adobe Asset Link
description: Konfigurieren Sie Experience Manager Assets für die Verwendung mit der Adobe Asset Link-Erweiterung für Creative Cloud-Anwendungen.
contentOwner: Vishabh Gupta
role: Admin
feature: Asset Management
exl-id: 3a9b44d4-1756-4ad5-91df-df8d53e82193
source-git-commit: 84b16dd1a60f731b568dd87ef89699875cb86596
workflow-type: ht
source-wordcount: '3149'
ht-degree: 100%

---

# Konfigurieren von Experience Manager Assets für Adobe Asset Link {#adobe-asset-link}

[Adobe Asset Link (AAL)](https://www.adobe.com/de/creativecloud/business/enterprise/adobe-asset-link.html) optimiert die Zusammenarbeit zwischen Kreativen und Marketern bei der Inhaltserstellung. Damit wird Adobe Experience Manager Assets mit den Creative Cloud-Desktop-Programmen Adobe InDesign, Adobe Photoshop und Adobe Illustrator verbunden. Über das Adobe Asset-Link-Bedienfeld können Kreative auf in AEM Assets gespeicherte Inhalte zugreifen und diese bearbeiten, ohne die Kreativprogramme zu verlassen, mit denen sie am besten vertraut sind.

Implementieren Sie die folgenden Aufgaben, um Experience Manager Assets für die Verwendung mit Asset Link zu konfigurieren. Verwenden Sie das Experience Manager-Admini-Konto, um die Konfiguration durchzuführen:

1. Installieren Sie die Pakete nach Bedarf. Details finden Sie unter [Voraussetzungen](#prerequisites).

1. Konfigurieren Sie Experience Manager entweder [manuell](#manual-configuration) oder mithilfe eines [Pakets](#configure-using-package).

1. Um lizenzierte Creative Cloud-Benutzer zu Benutzern von Experience Manager zuzuordnen, verwalten Sie dies über die [Benutzerzugriffssteuerung](#user-access).

1. Erstellen Sie einen [benutzerdefinierten Abfrageindex](#create-custom-index), konfigurieren Sie [FPO-Ausgabedarstellungen](/help/assets/configure-fpo-renditions.md) für InDesign, konfigurieren Sie die [Adobe Stock-Integration](/help/assets/aem-assets-adobe-stock.md) und konfigurieren Sie die [visuelle oder Ähnlichkeitssuche](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/search-assets.html?lang=de#configvisualsearch).

## Voraussetzungen und Unterstützung für verschiedene Funktionen {#prerequisites}

Installieren Sie unbedingt das entsprechende Service Pack und das Paket, das Sie benötigen. Beachten Sie die folgenden Anforderungen für jede Experience Manager-Version und für spezifische Funktionen.

| Asset-Funktion | Experience Manager-Version und Support-Anforderungen |
|--- |--- |
| Asset Link funktioniert standardmäßig | Experience Manager 6.5 und 6.5.2 oder höher. </br> Experience Manager 6.4.4 und 6.4.6 oder höher. </br> Adobe empfiehlt, vor der Verwendung von AAL die neueste Version des [Experience Manager Service Pack (SP)](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html?lang=de) zu installieren. |
| Asset Link funktioniert nach der Installation eines Pakets | Installieren Sie für Experience Manager 6.4.0 bis 6.4.3 das Paket [adobe-asset-link-support](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/featurepack/adobe-asset-link-support). |
| Adobe Stock-Integration | Experience Manager 6.4.2 oder höher |
| Visuelle oder Ähnlichkeitssuche | Experience Manager 6.5.0 oder höher |


## Konfigurieren von Experience Manager mithilfe des Konfigurationspakets {#configure-using-package}

Adobe empfiehlt die Installation des Konfigurationspakets [adobe-asset-link-config](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/product/assets/adobe-asset-link-config) zur Automatisierung der meisten Konfigurationsaufgaben, gefolgt von einigen manuellen Aufgaben. Alternativ können Sie [manuell konfigurieren](#manual-configuration).

>[!CAUTION]
>
>Wenn Ihre Experience Manager-Instanz für die Benutzeranmeldung mit Adobe IMS-Konten konfiguriert ist, verwenden Sie nicht das Konfigurationspaket. Stattdessen müssen Sie Ihre Experience Manager-Instanz [manuell konfigurieren](#manual-configuration).

1. Um den Package Manager in der Experience Manager-Web-Benutzeroberfläche zu öffnen, greifen Sie auf **[!UICONTROL Tools]** > **[!UICONTROL Implementierung]** > **[!UICONTROL Package Share]** zu. Installieren Sie das Paket `adobe-asset-link-config`.

1. Öffnen Sie **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**. Suchen Sie die Konfiguration für **[!UICONTROL Adobe Granite OAuth IMS Provider]** und klicken Sie darauf, um sie zu bearbeiten.

   Legen Sie die folgenden Eigenschaften fest und speichern Sie die Änderungen.

   * [!UICONTROL Gruppenzuordnungen]: Dies können Sie leer lassen, falls gewünscht. Weitere Informationen finden Sie unter [Gruppenzuordnung](#group-mapping).
   * [!UICONTROL Organisation]: Geben Sie die Organisations-ID ein, die Sie in der Adobe Admin Console verwenden. Weitere Informationen zu Organisations-IDs finden Sie unter [Benutzergruppe erstellen](https://helpx.adobe.com/de/enterprise/using/create-aal-user-group.html).

1. Suchen Sie die Konfiguration für **[!UICONTROL Adobe Granite Bearer Authentication Handler]** und klicken Sie darauf, um sie zu bearbeiten.

   Fügen Sie **[!UICONTROL InDesignAem2]**-Client-IDs zur Konfigurationseigenschaft **[!UICONTROL Zulässige OAuth-Client-IDs]** hinzu.


## Manuelles Konfigurieren von Experience Manager {#manual-configuration}

Konfigurieren Sie Experience Manager manuell, wenn Sie kein Konfigurationspaket verwenden möchten oder wenn Ihre Experience Manager-Bereitstellung so konfiguriert ist, dass die Benutzeranmeldung mit Adobe IMS-Konten unterstützt wird.

So konfigurieren Sie Experience Manager manuell:

1. Um auf den Konfigurations-Manager zuzugreifen, gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**. Wählen Sie **[!UICONTROL OSGi]** > **[!UICONTROL Konfiguration]** aus dem Menü oben.

1. Suchen Sie die Konfiguration **[!UICONTROL Adobe Granite OAuth IMS Provider]** und klicken Sie darauf, um sie zu bearbeiten.

   Legen Sie die folgende Konfiguration fest und klicken Sie auf **[!UICONTROL Speichern]**.

   * [!UICONTROL Autorisierungsendpunkt]: ` https://ims-na1.adobelogin.com/ims/authorize/v1`
   * [!UICONTROL Token-Endpunkt]: ` https://ims-na1.adobelogin.com/ims/token/v1`
   * [!UICONTROL Profil-Endpunkt]: ` https://ims-na1.adobelogin.com/ims/profile/v1`
   * [!UICONTROL Validierungs-URL]: ` https://ims-na1.adobelogin.com/ims/validate_token/v1`
   * [!UICONTROL Organisation]: Festgelegt auf die Organisations-ID im [Adobe Admin Console](https://adminconsole.adobe.com/).
   * [!UICONTROL Gruppenzuordnungen]: Lassen Sie das Feld leer, es sei denn, Sie haben einen Sonderfall. Weitere Informationen finden Sie unter [Gruppenzuordnung](#group-mapping).

1. Suchen Sie die Konfiguration für **[!UICONTROL Adobe Granite Bearer Authentication Handler]** und klicken Sie darauf, um sie zu bearbeiten.

   Fügen Sie die folgenden Client-IDs zur Konfigurationseigenschaft **[!UICONTROL Zulässige OAuth-Client-IDs]** hinzu: `InDesignAem2, cc-europa-desktop_0_1, cc-europa-desktop_1_0, cc-europa-desktop_2_0, cc-europa-desktop_3_0, cc-europa-desktop_4_0, cc-europa-desktop_5_0, cc-europa-desktop_6_0, cc-europa-desktop_7_0, cc-europa-desktop_8_0, cc-europa-desktop_9_0, and cc-europa-desktop_10_0`.

   Um jede `Client ID` hinzuzufügen, klicken Sie auf `+`. Klicken Sie auf **[!UICONTROL Speichern]**, nachdem Sie alle IDs hinzugefügt haben.

1. Überprüfen Sie in der Konfiguration von **[!UICONTROL Adobe Granite OAuth Application and Provider]** die vorhandenen **[!UICONTROL Adobe Granite OAuth Authentication Handler]**-Instanzen. Wenn Sie eine Instanz mit einem `Config ID`-Wert von `ims` finden, verwenden Sie diese für die Anweisungen in diesem Verfahren. Klicken Sie andernfalls auf `+`, um eine Konfigurationsinstanz zu erstellen. Legen Sie die folgenden Eigenschaftswerte fest und klicken Sie auf **[!UICONTROL Speichern]**.

   * [!UICONTROL Client-ID]: Nicht ändern
   * [!UICONTROL Client-Geheimnis]: Nicht ändern
   * [!UICONTROL Konfigurations-ID]: ` ims`
   * [!UICONTROL Umfang]: `AdobeID, OpenID, read_organizations` (Andere Werte können sich auch in der Konfiguration befinden)
   * [!UICONTROL Anbieter-ID]: ` ims`
   * [!UICONTROL Benutzer erstellen]: ` Checked`
   * [!UICONTROL Benutzer-ID-Eigenschaft]: `Email` für die neu erstellte Konfiguration. Andernfalls bleibt es unverändert.

1. Suchen Sie die Konfiguration für **[!UICONTROL Apache Jackrabbit Oak Standard Sync Handler]** mit dem **[!UICONTROL Sync Handler-Namen]** `ims` und klicken Sie darauf, um sie zu bearbeiten.

   Legen Sie die folgenden Konfigurationseigenschaften fest und klicken Sie auf **[!UICONTROL Speichern]**.

   * [!UICONTROL User Expiration Time and User Membership Expiration]: Zeit in Minuten, gefolgt von einem „m“ ohne Leerzeichen. Beispiel: `15m` für 15 Minuten. Weitere Informationen finden Sie unter [Gruppenzuordnung](#group-mapping).
   * [!UICONTROL Automatische Benutzermitgliedschaft]: Nicht ändern
   * [!UICONTROL Dynamische Benutzermitgliedschaft]: ` Deslect`

1. Suchen Sie die Konfiguration für **[!UICONTROL Adobe Granite OAuth Authentication Handler]** und klicken Sie darauf, um sie zu bearbeiten. Klicken Sie, ohne Änderungen vorzunehmen, auf **[!UICONTROL Speichern]**.

1. Um die relative Priorität des Bearer-Authentication-Handlers anzupassen, gehen Sie in CRXDE zu `/apps/system/config`. Suchen Sie `com.adobe.granite.auth.oauth.impl.BearerAuthenticationHandler.config` und öffnen Sie die Konfiguration. Fügen Sie am Ende `service.ranking=I"-10"` hinzu. Speichern Sie die Änderungen.

   >[!NOTE]
   >
   >Für jede mit einem Bearer-Token authentifizierte Anfrage fallen drei Aufrufe an Adobe IMS, die Benutzersynchronisierung und die Erstellung eines Anmelde-Tokens in Experience Manager an. Um diesen Mehraufwand zu vermeiden, erfasst Adobe Asset Link das Anmelde-Token, das in der Antwort von Experience Manager zurückgegeben wird, und sendet es mit nachfolgenden Anfragen. Damit dieser Prozess funktioniert, muss die relative Priorität des Bearer-Authentifizierungs-Handlers angepasst werden.

1. (Optional) Wenn die Experience Manager-Benutzer Großbuchstaben oder gemischte Groß- und Kleinschreibung in ihren E-Mail-IDs verwenden, wählen Sie in den **[!UICONTROL Adobe Granite ACP Platform Configs]** in der Experience Manager-Web-Konsole die Option **[!UICONTROL Sperrung der Benutzer in Kleinbuchstaben ändern]**.

## Zusätzliche Konfiguration nach der Migration zu Geschäftsprofilen {#configure-migration-activity}

Adobe Asset Link-Benutzer können eine Verbindung zu Experience Manager herstellen, um die IMS-Anmeldung über die primäre Creative Cloud für Enterprise (CCE)-Organisation zu ermöglichen. Experience Manager verwendet die Client-IDs, um die zulässige IMS-Organisation zu identifizieren. Nach der Migration zu Geschäftsprofilen ist es erforderlich, die Client-ID und den geheimen Schlüssel für die IMS-Organisation in Experience Manager für den Bearer-Authentifizierungs-Handler zu konfigurieren. Weitere Informationen zu Geschäftsprofilen finden Sie unter [Einführung in Adobe-Profile](https://helpx.adobe.com/de/enterprise/kb/introducing-adobe-profiles.html).

Eine zusätzliche Konfiguration ist nur erforderlich, wenn Sie verschiedene Adobe IMS-Organisationen für Experience Manager und Creative Cloud for Enterprise (CCE) verwenden und zwischen diesen beiden Organisationen eine Vertrauensbeziehung zwischen diesen beiden Organisationen hergestellt wird.

>[!NOTE]
>
>* Die Fehlerbehebung für Geschäftsprofile finden Sie in Experience Manager 6.5.11.0.
>* Die vorhandene Konfiguration funktioniert weiterhin, wenn Sie dieselbe Adobe IMS-Organisation mit Experience Manager und CCE verwenden.



**Voraussetzungen**

1. Eine betriebsbereite Experience Manager-Instanz mit für AAL konfigurierter Bearer-Authentifizierung.
1. Installieren Sie das folgende Paket (Service Pack 11) auf Ihrer Experience Manager 6.5-Instanz.

   [Experience Manager 6.5.11.0 herunterladen](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.11.zip)

1. Wenden Sie sich an den [!UICONTROL Kunden-Support], um die Client-ID und den geheimen Schlüssel für die Bearer-Authentifizierung Ihrer IMS-Organisation zu erhalten.

Im Folgenden finden Sie die zusätzlichen Konfigurationen, die nach der Migration zu Geschäftsprofilen erforderlich sind:

1. Legen Sie in **[!UICONTROL Adobe Granite OAuth IMS Configuration Provider]** (`com.adobe.granite.auth.ims.impl.ImsConfigProviderImpl`) Folgendes fest:

   * OAuth-Konfigurations-ID (`oauth.configmanager.ims.configid`): `ims` (Überprüfen Sie einmal, ob es möglicherweise bereits konfiguriert ist)

   * IMS-Eigentümerentität (`ims.owningEntity`): Ihre IMS-Organisations-ID

   ![IMS-Konfigurations-ID](assets/bearer-authentication1.png)

1. Öffnen Sie die Konfiguration für den **[!UICONTROL Bearer-Authentifizierungs-Handler]** und fügen Sie die Client-ID hinzu, die sie vom [!UICONTROL Kunden-Support] erhalten haben, zur Liste der **[!UICONTROL Zulässigen OAuth-Client-IDs]** hinzu.

   ![Hinzufügen der Client-ID](assets/add-clientid-bearer-auth.png)

1. Öffnen Sie die Konfiguration für **[!UICONTROL Adobe Granite OAuth Application and Provider]** und fügen Sie die **[!UICONTROL Client-ID]** und das **[!UICONTROL Client-Geheimnis]** (Geheimer Schlüssel) hinzu, die Sie vom kunden-Support erhalten haben.

   Stellen Sie sicher, dass das Feld **[!UICONTROL Konfigurations-ID]** (`oauth.config.id`) den gleichen Wert enthält wie im Feld **[!UICONTROL OAuth-Konfigurations-ID]** (`oauth.configmanager.ims.configid`) weiter oben angegeben.

   ![Überprüfen der Client-ID](assets/clientid-secretkey.png)

1. Öffnen Sie die Konfiguration für **[!UICONTROL Adobe Granite IMS Cluster Exchange Token Preprocessor]** und legen Sie sie auf `enable` fest.

## Verwalten der Benutzerzugriffssteuerung {#user-access}

In diesem Abschnitt wird beschrieben, wie Sie Benutzer und deren Zugriff auf das Experience Manager-Repository verwalten.

### Gruppenzuordnung {#group-mapping}

Die Gruppenzuordnung legt fest, wie die Gruppen in Experience Manager den Gruppen in Adobe IMS entsprechen. Dies spielt eine wichtige Rolle bei der Erteilung von Zugriffsberechtigungen für Adobe Asset Link-Benutzer auf Experience Manager Assets.

Bei Verwendung mit Adobe Asset Link delegiert Experience Manager Benutzerverwaltungsfunktionen an Adobe IMS. Es werden automatisch Benutzer und Gruppen erstellt, die den Benutzern und Gruppen in Adobe IMS entsprechen. Darüber hinaus werden Benutzer, Gruppen und Gruppenmitgliedschaften in Experience Manager mit denen in Adobe IMS synchronisiert, damit sie übereinstimmen.

Angenommen, Adobe Asset Link-Benutzer sind Mitglieder der Adobe IMS-Gruppe assetlink-users. In diesem Fall wird eine synchronisierte Gruppe mit dem Namen assetlink-users in Experience Manager erstellt, wenn ein Benutzer dieser Adobe IMS-Gruppe zum ersten Mal eine Verbindung zu Adobe Asset Link herstellt. Jeder neue Benutzer in der Adobe IMS-Gruppe wird in Experience Manager dieser entsprechenden Gruppe hinzugefügt, wenn er zum ersten Mal über Adobe Asset Link eine Verbindung zu Experience Manager herstellt.

Gruppen in Experience Manager, die Gruppen in Adobe IMS entsprechen und mit diesen synchronisiert sind, können direkt Zugriff erhalten oder indem sie zu Mitgliedern einer anderen Gruppe gemacht werden. Im Folgenden finden Sie ein Beispiel dafür, wie Berechtigungen verwaltet werden können.

![Beispiele für Gruppen](assets/group-examples.png)

Die folgenden Regeln gelten für Gruppenzuordnungen in Experience Manager:

* Stellen Sie sicher, dass die Eigenschaft **[!UICONTROL Gruppenzuordnungen]** in der Konfiguration für **[!UICONTROL Adobe Granite OAuth IMS Provider]** leer ist.
* Die Zugehörigkeit zu einer Adobe Asset Link-Benutzergruppe wird geprüft, wenn sich der Benutzer authentifiziert und die Zeitspanne, die in der Eigenschaft **[!UICONTROL Benutzerablaufzeit]** in der Konfiguration für **[!UICONTROL Apache Jackrabbit Oak Default Sync Handler]** angegeben ist, verstrichen ist. Derzeit können Benutzer in Experience Manager Gruppen hinzugefügt und aus ihnen entfernt werden, um sie mit den in Adobe IMS vorhandenen zu synchronisieren.
* Vermeiden Sie Konflikte mit Gruppennamen. Stellen Sie sicher, dass sich die Namen für in Adobe IMS erstellte Experience Manager-Benutzergruppen (zur Benutzerverwaltung) von denen aller Systemgruppennamen unterscheiden.

   Stellen Sie beispielsweise sicher, dass sie sich von der Gruppe `dam-users` und den vom Experience Manager-Admin erstellten Gruppen unterscheiden.

   Eine Adobe IMS-Gruppe, deren Name mit dem Namen einer Experience Manager-Systemgruppe oder einer manuell erstellten Gruppe kollidiert, wird nicht zur Steuerung von Benutzerberechtigungen verwendet.
* Wenn ein Adobe IMS-Benutzer eine Verbindung zu einer Experience Manager-Instanz herstellt, bei der der Name des Benutzers mit einem zuvor erstellten Experience Manager-Benutzer kollidiert, erhält der Adobe IMS-Benutzer einen anderen Namen, dem Zahlen hinzugefügt werden, um ihn eindeutig zu machen.

**Erstmaliges Einrichten der Zugriffssteuerung**

Benutzer, die eine Verbindung über Adobe Asset Link herstellen, können Assets nur dann anzeigen und mit ihnen interagieren, wenn sie die erforderliche Berechtigung erhalten haben. Im obigen Abschnitt über die [Gruppenzuordnung](#group-mapping) wird erläutert, wie Benutzergruppen in Experience Manager erstellt werden, die den Benutzergruppen in Ihrer Organisation in Adobe IMS entsprechen und mit diesen synchronisiert werden. Es wird empfohlen, dass die Experience Manager-Admins diese Gruppen verwenden, um die Zugriffssteuerung für Adobe Asset Link-Benutzer zu verwalten.

Für jede Experience Manager-Gruppe, die mit einer Adobe IMS-Gruppe synchronisiert wird (die für die Verwaltung der Benutzerzugriffssteuerung verwendet wird) müssen Sie Folgendes tun:

1. Stellen Sie sicher, dass die Gruppe über ein Mitglied verfügt, das für eine Erstverbindung über Adobe Asset Link verwendet werden kann.
1. Verwenden Sie diesen Benutzer, um sich bei Adobe Asset Link anzumelden und eine Verbindung zu Experience Manager herzustellen. Es wird erwartet, dass diese Verbindung fehlschlägt.
1. Suchen Sie in Experience Manager die Gruppe, die der Gruppe in Adobe IMS entspricht, und gewähren Sie ihr die gewünschte Zugriffssteuerung. Zum Beispiel wird die neue Gruppe ein Mitglied der Gruppe dam-users.
1. Schließen Sie Adobe Asset Link und starten Sie das Creative Cloud-Programm neu.
1. Um sicherzustellen, dass der Benutzer den erwarteten Zugriff hat, öffnen Sie Adobe Asset Link erneut.

Sobald diese Schritte durchgeführt wurden, können andere Benutzer in derselben Gruppe beim ersten Versuch eine Verbindung zu Experience Manager mit Adobe Asset Link herstellen. Sie haben automatisch dieselben Berechtigungen wie die anderen Benutzer in der Gruppe.

## Verwalten von Experience Manager-Benutzern für Adobe Asset Link {#manage-users}

Adobe Asset Link-Benutzer können eine Verbindung zu Experience Manager herstellen, wenn sie bei ihrer Creative Cloud-Anwendung angemeldet sind. Diese Authentifizierung verwendet die Adobe IMS-Technologie und erstellt Benutzerinformationen in Experience Manager, falls diese nicht vorhanden sind. Es ist üblich, dass Experience Manager-Unternehmenskunden ihre Benutzer über einen externen Identitätsanbieter verwalten, der mit Experience Manager integriert ist. Zu den Identitätsanbietern gehören Adobe IMS und andere Produkte, die die Protokolle SAML und LDAP verwenden. Alternativ können Benutzer in Experience Manager lokal erstellt und verwaltet werden.

Benutzer, die über Adobe Asset Link eine Verbindung zu Experience Manager herstellen, haben keinen Konflikt mit bestehenden Benutzerinformationen, die in Experience Manager bei einer früheren direkten Anmeldung gespeichert wurden, wenn:

* Alle Benutzernamen, die für die direkte Anmeldung bei Experience Manager verwendet werden, sich von den Benutzernamen, die in Adobe IMS für die Anmeldung bei Creative Cloud verwendet werden, unterscheiden.
* Adobe IMS als Identitätsanbieter für die direkte Anmeldung bei Experience Manager verwendet wird.
* Benutzer über Adobe Asset Link eine Verbindung zu Experience Manager herstellen, bevor sie sich mit demselben Konto direkt bei Experience Manager anmelden.


Andererseits müssen die Benutzerinformationen, die als Ergebnis der direkten Experience Manager-Anmeldung erstellt wurden, in den folgenden Szenarien aktualisiert werden, damit sie mit Adobe Asset Link funktionieren:

* Der gleiche Benutzername, z. B. die E-Mail-Adresse des Benutzers, wird sowohl für das Konto in Creative Cloud, das Adobe IMS verwendet, als auch für das Konto bei einem externen Identitätsanbieter, der nicht Adobe IMS ist, verwendet.
* Der gleiche Benutzername wird sowohl für das Konto in Creative Cloud als auch für ein lokales Experience Manager-Konto verwendet.
* Bei den Creative Cloud-Konten in Adobe IMS handelt es sich um Federated IDs, die von demselben externen Identitätsanbieter bereitgestellt werden, der auch in Experience Manager für die direkte Anmeldung integriert ist.

Die durch diese Szenarien erstellten Benutzer verfügen nicht über eine Eigenschaft, die für Benutzer erforderlich ist, die mit Adobe IMS synchronisiert werden.

So aktualisieren Sie diese Benutzer in Experience Manager, damit sie mit Asset Link arbeiten können:

1. Suchen Sie in der Experience Manager-Webkonsole die Konfiguration für **[!UICONTROL Apache Jackrabbit Oak External PrincipalConfiguration]** und klicken Sie darauf, um sie zu bearbeiten. Deaktivieren Sie das Kontrollkästchen **[!UICONTROL Externer Identitätsschutz]** und klicken Sie auf **[!UICONTROL Speichern]**.
1. Um auf die Benutzeroberfläche für das User Management in Experience Manager zuzugreifen, gehenn Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]**. Wählen Sie den Benutzer aus, den Sie aktualisieren möchten, und notieren Sie sich dann das Ende des URL-Pfads Ihres Browsers für diesen Benutzer, beginnend mit `/home/users`. Alternativ können Sie auch in CRXDE nach dem Benutzernamen suchen. Ein Beispiel für einen Benutzerpfad: `/home/users/x/xTac082TDh-guJzzG7WM`.
1. Navigieren Sie in CRXDE zum Benutzerpfad, wählen Sie den Benutzerknoten aus und zeigen Sie die Eigenschaften des Knotens an, indem Sie die Registerkarte **[!UICONTROL Eigenschaften]** im unteren mittleren Bereich auswählen. Dieser Knoten hat einen `jcr:primaryType`-Eigenschaftswert von `rep:User`.
1. Geben Sie am unteren Rand des Registerkartenbereichs **[!UICONTROL Eigenschaften]** einen Wert für den `Name` von `rep:externalId` ein, einen Wert für den `Type` von `String` und einen Wert für den `Value` von `rep:authorizableId`;`ims`, wobei `rep:authorizableId` der Wert der `rep:authorizableId`-Eigenschaft des Knotens ist. (Ein Semikolon ohne Leerzeichen wird verwendet, um den Wert `rep:authorizableId` vom Wert `ims` zu trennen.)
1. Klicken Sie auf der rechten Seite Ihres neuen Eintrags auf **[!UICONTROL Hinzufügen]** und klicken Sie auf **[!UICONTROL Alle speichern]**.
1. Wiederholen Sie die Schritte 2 bis 5 für alle anderen Benutzer, die Sie aktualisieren möchten, damit sie mit Adobe Asset Link arbeiten können.
1. Suchen Sie in der Experience Manager-Webkonsole die Konfiguration für **[!UICONTROL Apache Jackrabbit Oak External PrincipalConfiguration]** und klicken Sie darauf, um sie zu bearbeiten. Deaktivieren Sie das Kontrollkästchen **[!UICONTROL Externer Identitätsschutz]** und klicken Sie auf **[!UICONTROL Speichern]**.

>[!NOTE]
>
>Wenn die Services nicht innerhalb weniger Minuten wiederhergestellt werden, starten Sie Experience Manager neu, um erfolgreiche Authentifizierungen zu ermöglichen.

Nach dieser Änderung kann ein aktualisierter Experience Manager-Benutzer eine Verbindung mit Adobe Asset Link herstellen und weiterhin die Methode der direkten Anmeldung bei Experience Manager verwenden, die vor dem Update verwendet wurde. Bei erfolgreicher Authentifizierung mit Adobe IMS werden die Benutzerprofilinformationen von Experience Manager mit dem Benutzerprofil in Adobe IMS synchronisiert.

Es gibt eine Methode, mit der eine Massenmigration von mehreren Experience Manager-Benutzern durchgeführt werden kann, damit diese mit Adobe Asset Link arbeiten können. Wenden Sie sich an den Adobe-Kunden-Support, um weitere Informationen und Unterstützung bei der Aktivierung dieser Option zu erhalten.

Als Alternative zu diesen Schritten kann einem Adobe Asset Link-Benutzer unter bestimmten Umständen ein schneller Zugriff auf Experience Manager gewährt werden. In solchen Fällen werden die bereits vorhandenen Benutzerinformationen mit Experience Manager User Management oder Experience Manager CRXDE gefunden und gelöscht, bevor sie mit Adobe Asset Link verbunden werden. Nach der Verbindung werden in Experience Manager neue Benutzerinformationen erstellt. Verwenden Sie diesen Ansatz nur, wenn Sie sicher sind, dass es keine wichtigen Daten gibt, die als untergeordneter Knoten des Benutzerknotens hinzugefügt werden. Diese zusätzlichen Daten sind alle Knoten, die dem Benutzerknoten untergeordnet sind, außer den Knoten `tokens`, `preferences`, `profile`, `profiles`, `profiles/public` und `rep:policy/*`.

## Automatischer Start des Workflows zur bedingten Verarbeitung von Assets {#auto-start-workflow}

In Experience Manager 6.4 und Experience Manager 6.5 können Admins Workflows konfigurieren, um Assets auf der Grundlage vordefinierter Bedingungen automatisch auszuführen und zu verarbeiten.

Die Konfiguration ist beispielsweise für Fachanwender und Marketingexperten nützlich, um einen benutzerdefinierten Workflow für einige bestimmte Ordner zu erstellen. So können z. B. alle Assets aus dem Fotoshooting einer Agentur mit einem Wasserzeichen versehen werden, oder alle von einem Freiberufler hochgeladenen Assets können verarbeitet werden, um bestimmte Ausgabedarstellungen zu erstellen.

Weitere Informationen auch zur Konfiguration von Experience Manager finden Sie unter [Automatisches Ausführen von Workflows für Assets](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/assets-workflow.html?lang=de#auto-execute-workflow-on-some-assets).


## Erstellen eines benutzerdefinierten Index in Experience Manager 6.4.x-Versionen {#create-custom-index}

Experience Manager enthält Indizes, die für Abfragen verwendet werden. Erstellen Sie den folgenden benutzerdefinierten Index für die angegebene Version. Experience Manager 6.5.0 enthält diesen Index standardmäßig. Adobe Asset Link benötigt diesen Index, um festzustellen, welche Assets ein Benutzer ausgecheckt hat.

1. Suchen Sie in CRXDE den Knoten `/oak:index`. Erstellen Sie einen Knoten mit dem Namen `cqDrivelock` und legen Sie seinen `Type` auf `oak:QueryIndexDefinition` fest.

1. Fügen Sie dem neuen Knoten die folgenden Eigenschaften hinzu und speichern Sie die Änderungen:

   * `Name: type; Type: string; Value: property`

   * `Name: propertyNames; Type: Name[] (click the "Multi" button); Value: cq:drivelock`


## Konfigurieren der visuellen oder Ähnlichkeitssuche {#configure-visual-similarity-search}

Mit der Funktion „Visuelle Suche“ können Sie über das Adobe Asset Link-Bedienfeld im AEM Assets-Repository nach visuell ähnlichen Assets suchen. Diese Funktion ist ab Version 6.5.0 verfügbar, und es werden nur die indizierten Assets durchsucht. Weitere Informationen finden Sie unter [Konfigurieren der visuellen Suche](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/search-assets.html?lang=de#configvisualsearch).

## Erzeugen von FPO (For Placement Only)-Ausgabedarstellungen (also nur für die Platzierung) für Adobe InDesign {#fpo-renditions}

Experience Manager bietet Ausgabeversionen, die nur für die Platzierung (FPO) verwendet werden. Diese FPO-Ausgabedarstellungen haben eine kleine Dateigröße, weisen aber dasselbe Seitenverhältnis auf. Wenn für ein Asset keine FPO-Ausgabedarstellung verfügbar ist, verwendet Adobe InDesign stattdessen das Original-Asset. Dieser Fallback-Mechanismus stellt sicher, dass der kreative Workflow ohne Unterbrechung fortgesetzt wird. Weitere Informationen finden Sie unter [Erzeugen von FPO-Ausgabedarstellungen](/help/assets/configure-fpo-renditions.md).


## Integrieren mit Adobe Stock {#adobe-stock-integration}

Organisationen integrieren ihre Adobe Stock-Konten mit Experience Manager Assets. Dies hilft Marketingexperten dabei, lizenzierte, hochwertige und lizenzfreie Fotos, Vektoren, Illustrationen, Videos, Vorlagen und 3D-Assets für ihre Kreativ- und Marketingprojekte verfügbar zu machen. Kreativprofis können diese Assets über das Bedienfeld „Asset-Link“ verwenden.

Informationen zur Integration mit Adobe Stock finden Sie unter [Adobe Stock-Assets in Experience Manager Assets](/help/assets/aem-assets-adobe-stock.md). Für die Integration mit Adobe Stock ist Experience Manager 6.4.2 oder höher erforderlich.


## Fehlerbehebung bei Problemen im Zusammenhang mit Experience Manager {#troubleshoot}


Wenn Sie Probleme bei der Konfiguration oder Verwendung von Adobe Asset Link haben, versuchen Sie Folgendes:

* Vergewissern Sie sich, dass Ihre Implementierung die Voraussetzungen erfüllt. Stellen Sie insbesondere sicher, dass die entsprechenden Feature Packs oder Pakete installiert sind.
* Wenden Sie sich an den Partner oder Systemintegrator Ihrer Organisation.
* Wenn sich Ihre Creative Cloud-Benutzer nicht bei den ausgecheckten Assets verifizieren können, überprüfen Sie die Groß-/Kleinschreibung der Domain-Namen in den E-Mail-IDs. Zur Behebung siehe [Manuelle Konfiguration](#manual-configuration).
* Weitere Informationen finden Sie unter [Fehlerbehebung bei Asset Link](https://helpx.adobe.com/de/enterprise/kb/asset-link-troubleshooting.html).


>[!MORELIKETHIS]
>
>* [Über Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html)
>* [Verwenden von Asset Link in der Creative Cloud-Desktop-Anwendung und Verwalten von Assets](https://helpx.adobe.com/de/enterprise/using/manage-assets-using-adobe-asset-link.html)
>* [Konfigurieren von Adobe Experience Manager Assets as a Cloud Service](https://helpx.adobe.com/de/enterprise/using/configure-aem-assets-for-asset-link.html).

