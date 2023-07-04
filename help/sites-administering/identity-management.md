---
title: Identitäts-Management
seo-title: Identity Management
description: Erfahren Sie mehr über die Identitätsverwaltung in AEM.
seo-description: Learn about identity management in AEM.
uuid: d9b83cd7-c47a-41a5-baa4-bbf385d13bfd
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: 994a5751-7267-4a61-9bc7-01440a256c65
docset: aem65
exl-id: acb5b235-523e-4c01-9bd2-0cc2049f88e2
source-git-commit: 7803f1df1e05dc838cb458026f8dbd27de9cb924
workflow-type: tm+mt
source-wordcount: '1226'
ht-degree: 52%

---

# Identitäts-Management{#identity-management}

Einzelne Besucher Ihrer Website können nur identifiziert werden, wenn Sie ihnen die Möglichkeit geben, sich anzumelden. Es gibt verschiedene Gründe, warum Sie eine Anmeldefunktion bereitstellen möchten:

* Besuchende der [AEM Communities](/help/communities/overview.md)-Website müssen sich anmelden, um Inhalte an die Community posten zu können.
* [Geschlossene Benutzergruppen](/help/sites-administering/cug.md)

  Sie können den Zugang zu Ihrer Website (oder Abschnitten davon) ggf. auf bestimmte Besuchende beschränken.

* [Personalisierung](/help/sites-administering/personalization.md) ermöglicht Besuchenden die Konfiguration bestimmter Aspekte des Zugriffs auf Ihre Website.

Die Anmelde- (und Abmelde)-Funktion wird von einem [Konto mit einem **Profil**](#profiles-and-user-accounts) bereitgestellt, das zusätzliche Informationen über registrierte Besuchende (Benutzende) enthält. Die tatsächlichen Prozesse für die Registrierung und Autorisierung können abweichen:

* Selbstregistrierung über die Website

  Eine [Community-Website](/help/communities/sites-console.md) kann so konfiguriert werden, dass Besuchenden die Selbstregistrierung oder die Anmeldung mit ihrem Facebook- oder Twitter-Konto möglich ist.

* Antrag auf Registrierung über die Website

  Für eine geschlossene Benutzergruppe können Sie Besuchenden einen Antrag auf Registrierung gestatten, die Autorisierung jedoch mithilfe eines Workflows zwangsweise durchsetzen.

* Registrieren jedes Kontos über die Authoring-Umgebung

  Wenn Sie nur über eine geringe Anzahl von Profilen verfügen, die ohnehin autorisiert werden müssen, können Sie diese auch direkt registrieren.

Damit sich Besucher registrieren können, können eine Reihe von Komponenten und Formularen verwendet werden, um die erforderlichen Identifizierungsinformationen und dann die zusätzlichen (oft optionalen) Profilinformationen zu erfassen. Nachdem sie sich registriert haben, sollten sie auch in der Lage sein, die von ihnen übermittelten Details zu überprüfen und zu aktualisieren.

Zusätzliche Funktionen können konfiguriert oder entwickelt werden:

* Konfigurieren Sie alle erforderlichen Rückwärtsreplikationen.
* Benutzer können ihr Profil entfernen, indem sie ein Formular zusammen mit einem Workflow entwickeln.

>[!NOTE]
>
>Die im Profil angegebenen Informationen können auch verwendet werden, um dem Benutzer zielgerichtete Inhalte über [Segmente](/help/sites-administering/campaign-segmentation.md) und [Kampagnen](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md).

## Forms registrieren {#registration-forms}

A [Formular](/help/sites-authoring/default-components.md#form-component) kann verwendet werden, um die Registrierungsinformationen zu erfassen und dann das neue Konto und Profil zu generieren.

Benutzerinnen und Benutzer können beispielsweise mithilfe der folgenden Geometrixx-Seite ein neues Profil anfordern:
`http://localhost:4502/content/geometrixx-outdoors/en/user/register.html`

![registerform](assets/registerform.png)

Nach dem Übermitteln der Anfrage wird die Profilseite geöffnet. Auf dieser kann der Benutzer oder die Benutzerin persönliche Daten bereitstellen.

![profilepage](assets/profilepage.png)

Das neue Konto ist auch in der [Benutzerkonsole](/help/sites-administering/security.md) sichtbar.

## Anmeldung {#login}

Die Anmeldungskomponente kann verwendet werden, um die Anmeldeinformationen zu erfassen und den Anmeldeprozess zu aktivieren.

Sie stellt dem Besucher bzw. der Besucherin die Standardfelder **Benutzername** und **Kennwort** bereit, sowie ferner eine Schaltfläche **Anmelden** zum Aktivieren des Login-Verfahrens bei Eingabe der Anmeldedaten.

Benutzende können sich beispielsweise entweder anmelden oder mithilfe der Option **Anmelden** in der Geometrixx-Symbolleiste ein neues Konto erstellen, welches folgende Seite nutzt:

`http://localhost:4502/content/geometrixx-outdoors/en/user/sign-in.html`

![anmelden](assets/login.png)

## Abmelden {#logging-out}

Da es einen Anmeldemechanismus gibt, ist auch ein Abmeldemechanismus erforderlich. Dies ist als **Abmelden** in Geometrixx.

## Anzeigen und Aktualisieren eines Profils {#viewing-and-updating-a-profile}

Je nach Ihrem Registrierungsformular kann der Besucher registrierte Informationen in seinem Profil haben. Sie sollten in der Lage sein, dies zu einem späteren Zeitpunkt anzuzeigen und/oder zu aktualisieren. Dies kann mithilfe eines ähnlichen Formulars erfolgen, beispielsweise in Geometrixx:

```
http://localhost:4502/content/geometrixx-outdoors/en/user/profile.html
```

Um die Daten Ihres Profils einzusehen, klicken Sie in der oberen rechten Ecke einer beliebigen Seite auf **Mein Profil**; beispielsweise mit dem `admin`-Konto:
`http://localhost:4502/home/users/a/admin/profile.form.html/content/geometrixx-outdoors/en/user/profile.html.`

Sie können mit dem [ClientContext](/help/sites-administering/client-context.md) (in der Authoring-Umgebung und mit ausreichend Berechtigungen) ein anderes Profil anzeigen:

1. Öffnen Sie eine Seite; beispielsweise die Geometrixx-Seite:

   `http://localhost:4502/cf#/content/geometrixx/en.html`

1. Klicken **Mein Profil** in der oberen rechten Ecke. Sie sehen das Profil Ihres aktuellen Kontos. z. B. der Administrator.
1. Presse **control-alt-C** , um den Client-Kontext zu öffnen.
1. Klicken Sie oben links im ClientContext auf das **Profil laden** Schaltfläche.

   ![Schaltfläche &quot;Profil laden&quot;](do-not-localize/loadprofile.png)

1. Wählen Sie ein anderes Profil aus der Dropdown-Liste im Dialogfeld aus. Beispiel: **Alison Parker**.
1. Klicken Sie auf **OK**.
1. Klicken Sie erneut auf **Mein Profil**. Das Formular wird mit den Details von Alison aktualisiert.

   ![profilealison](assets/profilealison.png)

1. Sie können jetzt **Profil bearbeiten** oder **Kennwort ändern** um die Details zu aktualisieren.

## Hinzufügen von Feldern zur Profildefinition {#adding-fields-to-the-profile-definition}

Sie können der Profildefinition Felder hinzufügen. Beispielsweise zum Hinzufügen eines Felds „Lieblingsfarbe“ zum Geometrixx-Profil:

1. Navigieren Sie von der Websites-Konsole zu „Geometrixx Outdoors Site“ > „Deutsch“ > „Benutzer“ > „Mein Profil“.
1. Doppelklicken Sie auf die Seite **Mein Profil**, um sie zur Bearbeitung zu öffnen.
1. Erweitern Sie in der Registerkarte **Komponenten** des Sidekicks den Abschnitt **Formular**.
1. Ziehen Sie eine **Dropdown-Liste** aus dem Sidekick in das Formular, direkt unter das Feld **Info zu eigener Person**.
1. Doppelklicken Sie auf die Komponente **Dropdown-Liste**, um das Dialogfeld für die Konfiguration zu öffnen, und geben Sie Folgendes ein:

   * **Elementname** - `favoriteColor`
   * **Titel** - `Favorite Color`
   * **Elemente** – Fügen Sie mehrere Farben als Elemente hinzu

   Klicken Sie zum Speichern auf **OK**.

1. Schließen Sie die Seite. Kehren Sie zur **Websites-Konsole** zurück und aktivieren Sie die Seite „Mein Profil“.

   Bei der nächsten Ansicht eines Profils können Sie eine Lieblingsfarbe auswählen:

   ![aparkerfavcolour](assets/aparkerfavcolour.png)

   Das Feld wird unter dem Abschnitt **Profil** des relevanten Benutzerkontos gespeichert:

   ![aparkercrxdelite](assets/aparkercrxdelite.png)

## Profilstatus {#profile-states}

Es gibt eine Reihe von Nutzungsszenarien, bei denen es wichtig ist zu wissen, ob sich eine Benutzerin bzw. ein Benutzer (oder eher das Profil) in einem *bestimmten Status* befindet.

Dazu gehört das Definieren einer entsprechenden Eigenschaft im Benutzerprofil auf eine Weise, die:

* für den Benutzer sichtbar und zugänglich ist
* definiert zwei Status für jede Eigenschaft
* ermöglicht das Umschalten zwischen den beiden definierten Status

Dies geschieht mit:

* [Statusanbieter](#state-providers)

  Zum Verwalten der beiden Status einer speziellen Eigenschaft sowie der Übergänge zwischen beiden.

* [Workflows](#workflows)

  Zum Verwalten von statusbezogenen Aktionen.

Es können mehrere Status definiert werden; in Geometrixx umfassen diese beispielsweise:

* das Abonnieren (oder das Aufheben des Abonnements) von Benachrichtigungen zu Newslettern oder Kommentar-Threads
* Das Hinzufügen und Entfernen einer Verknüpfung zu einem Freund bzw. einer Freundin

### Statusanbieter {#state-providers}

Ein Statusanbieter verwaltet den aktuellen Status der betreffenden Eigenschaft zusammen mit den Übergängen zwischen den beiden möglichen Status.

Statusanbieter werden als Komponenten implementiert und können daher für Ihr Projekt angepasst werden. In Geometrixx umfassen diese Folgendes:

* Forum abonnieren/kündigen (Thema)
* Freund hinzufügen/entfernen

### Workflows {#workflows}

Statusanbieter verwalten eine Profileigenschaft und deren Status.

Es ist ein Workflow erforderlich, um die den Status betreffenden Aktionen zu implementieren. Beispiel: Beim Abonnieren von Benachrichtigungen handhabt der Workflow die tatsächliche Abonnementaktion; bei der Aufhebung des Benachrichtigungsabonnements handhabt der Workflow das Entfernen des Benutzers bzw. der Benutzerin von der Abonnementliste.

## Profile und Benutzerkonten {#profiles-and-user-accounts}

Profile werden im Content-Repository als Teil des [Benutzerkontos](/help/sites-administering/user-group-ac-admin.md) gespeichert.

Das Profil ist unter `/home/users/geometrixx` zu finden:

![chlimage_1-138](assets/chlimage_1-138.png)

Bei einer Standardinstallation (Autor oder Veröffentlichung) hat jeder Lesezugriff auf die gesamten Profilinformationen aller Benutzer. Jeder ist ein &quot;*Integrierte Gruppe, die automatisch alle vorhandenen Benutzer und Gruppen enthält. Die Mitgliederliste kann nicht bearbeitet werden*&quot;.

Diese Zugriffsberechtigungen werden durch die folgende Platzhalter-ACL definiert:

/home everyone allow jcr:read rep:glob = &#42;/profile&#42;

Dies ermöglicht Folgendes:

* Forum, Kommentare oder Blog-Beiträge zur Anzeige von Informationen (wie Symbol oder vollständiger Name) aus dem entsprechenden Profil
* Links zu Geometrixx-Profilseiten

Wenn dieser Zugriff für Ihre Installation nicht geeignet ist, können Sie diese Standardeinstellungen ändern.

Verwenden Sie dazu die Registerkarte **[Zugriffskontrolle](/help/sites-administering/user-group-ac-admin.md#access-right-management)**:

![aclmanager](assets/aclmanager.png)

## Profilkomponenten {#profile-components}

Es stehen auch verschiedene Profilkomponenten zur Definition der Profilanforderungen für Ihre Site zur Verfügung.

### Feld für die Kennwortüberprüfung {#checked-password-field}

Diese Komponente bietet Ihnen zwei Felder für:

* die Eingabe eines Kennworts
* eine Überprüfung, um sicherzustellen, dass das Kennwort korrekt eingegeben wurde.

Mit den Standardeinstellungen wird die Komponente wie folgt angezeigt:

![dc_profiles_checkedpassword](assets/dc_profiles_checkedpassword.png)

### Profil – Avatar-Foto {#profile-avatar-photo}

Diese Komponente bietet dem Benutzer einen Mechanismus zum Auswählen und Hochladen einer Avatar-Fotodatei.

![dc_profiles_avatarphoto](assets/dc_profiles_avatarphoto.png)

### Profil – Genauer Name {#profile-detailed-name}

Mit dieser Komponente kann der Benutzer einen detaillierten Namen eingeben.

![dc_profiles_detailedname](assets/dc_profiles_detailedname.png)

### Profil – Geschlecht {#profile-gender}

Mit dieser Komponente kann der Benutzer sein Geschlecht eingeben.

![dc_profiles_gender](assets/dc_profiles_gender.png)
