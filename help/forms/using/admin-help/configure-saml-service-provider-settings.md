---
title: SAML-Dienstanbietereinstellungen konfigurieren
seo-title: Configure SAML service provider settings
description: Wenn SAML-Service als Ihr Authentifizierungsanbieter konfiguriert ist, melden sich die Benutzer bei AEM Forms an und authentifizieren sich über einen angegebenen Identitätsanbieter (IDP) von Drittanbietern.
seo-description: You can configure SAML service provider settings to allow users to login and authenticate to AEM forms via a specified third-party identity provider (IDP).
uuid: 14c706ad-8b1c-4c03-9cd4-97424f2162bc
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 1169d0d1-cbfb-486b-acca-9b9de3d410dc
exl-id: dd302cfb-eae1-4189-aa7b-9f2533ebd164
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '599'
ht-degree: 100%

---

# SAML-Dienstanbietereinstellungen konfigurieren{#configure-saml-service-provider-settings}

Security Assertion Markup Language (SAML) ist eine der Optionen, die Sie beim Konfigurieren der Autorisierung für eine Unternehmens- oder Hybrid-Domain auswählen können. SAML wird hauptsächlich zum Unterstützen der einmaligen Anmeldung in mehreren Domains verwendet. Wenn SAML als Ihr Authentifizierungsanbieter konfiguriert ist, melden sich die Benutzer bei AEM Forms an und authentifizieren sich über einen angegebenen Identitätsanbieter (IDP) von Drittanbietern.

Eine Erläuterung von SAML finden Sie unter [Security Assertion Markup Language (SAML) V2.0 Technische Übersicht](https://www.oasis-open.org/committees/download.php/20645/sstc-saml-tech-overview-2%200-draft-10.pdf).

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Konfiguration“ > „SAML-Dienstanbietereinstellungen“.
1. Geben Sie in das Feld „Dienstanbieter-Entitäts-ID“ eine eindeutige ID als Bezeichner für die AEM Forms-Dienstanbieterimplementierung ein. Sie müssen diese eindeutige ID auch beim Konfigurieren Ihres Identitätsanbieters (IDP) (z. B. `um.lc.com` angeben.) Sie können außerdem die URL verwenden, die zum Zugreifen auf AEM Forms verwendet wird (z. B. `https://AEMformsserver`).
1. Geben Sie in das Feld für die Dienstanbieter-Basis-URL die Basis-URL für Ihren AEM Forms-Server ein (z. B. `https://AEMformsserver:8080`).
1. (Optional) Wenn Sie möchten, dass AEM Forms signierte Authentifizierungsanforderungen an den Identitätsanbieter sendet, führen Sie die folgenden Aufgaben aus:

   * Verwenden Sie Trust Manager, um eine Berechtigung im „PKCS #12“-Format mit der ausgewählten Option „Berechtigung für die Dokumentsignierung“ als Trust Store-Typ zu importieren. (Siehe [Lokale Berechtigungen verwalten](/help/forms/using/admin-help/local-credentials.md#managing-local-credentials).)
   * Wählen Sie in der Liste mit den Schlüsselalias für Dienstanbieterberechtigungen den Alias aus, den Sie der Berechtigung in Trust Store zugewiesen haben.
   * Klicken Sie auf „Exportieren“, um den URL-Inhalt in einer Datei zu speichern, und importieren Sie anschließend diese Datei in Ihren IDP.

1. (Optional) Wählen Sie in der Liste der ID-Richtlinie für Dienstanbieternamen das Namensformat aus, das der IDP zum Identifizieren des Benutzers in einer SAML-Assertion verwendet. Die Optionen lauten „Nicht angegeben“, „E-Mail“ und „Windows Domain Qualified Name“.

   >[!NOTE]
   >
   >Bei Namensformaten muss nicht auf Groß- und Kleinschreibung geachtet werden.

1. (Optional) Aktivieren Sie die Option „Authentifizierungs-Eingabeaufforderung für lokale Benutzer aktivieren“. Wenn diese Option ausgewählt ist, werden den Benutzern zwei Verknüpfungen angezeigt:

   * eine Verknüpfung zur Anmeldeseite eines dritten SAML-Identitätsanbieters, wo sich Benutzer authentifizieren können, die zu einer Unternehmens-Domain gehören.
   * eine Verknüpfung zur AEM Forms-Anmeldeseite, wo sich Benutzer identifizieren können, die zu einer lokalen Domain gehören.

   Wenn diese Option nicht ausgewählt ist, werden die Benutzer direkt zur Anmeldeseite des dritten SAML-Identitätsanbieters geführt, wo sich Benutzer authentifizieren können, die zu einer Unternehmens-Domain gehören.

1. (Optional) Wählen Sie „Artefakt-Bindung“, um die Unterstützung für die Artefakt-Bindung zu aktivieren. Standardmäßig wird POST-Bindung mit SAML verwendet. Wenn Sie jedoch Artefakt-Bindung konfiguriert haben, wählen Sie diese Option aus. Wenn diese Option ausgewählt ist, wird die tatsächliche Benutzerassertion nicht durch die Browseranforderung weitergeleitet. Stattdessen wird ein Verweis zu der Assertion weitergeleitet und die Assertion wird mithilfe eines Backend-Webdienstaufrufs abgerufen.
1. (Optional) Wählen Sie „Bindung umleiten“ aus, um SAML-Bindungen, die Umleitungen verwenden, zu unterstützen.
1. (Optional) Geben Sie unter „Custom Properties“ weitere Eigenschaften an. Die zusätzlichen Eigenschaften lauten Name=Wert, Paare durch neue Zeilen getrennt.

   * Sie können AEM Forms für die Ausgabe einer SAML-Bestätigung für eine Gültigkeitsdauer konfigurieren, die der Gültigkeitsdauer einer Bestätigung eines Drittanbieters entspricht. Damit die Zeitüberschreitung der SAML-Bestätigung des Drittanbieters berücksichtigt wird, fügen Sie die folgende Zeile in den benutzerdefinierten Eigenschaften hinzu:

      `saml.sp.honour.idp.assertion.expiry=true`

   * Fügen Sie folgende benutzerdefinierte Eigenschaft für die Verwendung von RelayState hinzu, um die URL zu ermitteln, zu der der Benutzer nach erfolgreicher Authentifizierung weitergeleitet wird.

      `saml.sp.use.relaystate=true`

   * Fügen Sie folgende benutzerdefinierte Eigenschaft zum Konfigurieren der URL für die benutzerdefinierten Java Serverseiten (JSP) hinzu, die zur Wiedergabe der registrierten Liste von Identitätsanbietern verwendet wird. Wenn Sie keine benutzerdefinierte Webanwendung bereitgestellt haben, wird die standardmäßige User Management-Seite verwendet, um die Liste wiederzugeben.

   `saml.sp.discovery.url=/custom/custom.jsp`

1. Klicken Sie auf Speichern.
