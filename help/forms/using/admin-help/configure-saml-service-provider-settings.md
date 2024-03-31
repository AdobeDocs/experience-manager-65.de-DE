---
title: Konfigurieren der SAML-Dienstanbietereinstellungen
description: Sie können die Einstellungen des SAML-Dienstanbieters so konfigurieren, dass sich Benutzer über einen angegebenen Identitäts-Provider (IDP) bei AEM Formularen anmelden und authentifizieren können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: dd302cfb-eae1-4189-aa7b-9f2533ebd164
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 77%

---

# Konfigurieren der SAML-Dienstanbietereinstellungen{#configure-saml-service-provider-settings}

Security Assertion Markup Language (SAML) ist eine der Optionen, die Sie beim Konfigurieren der Autorisierung für eine Unternehmens- oder Hybrid-Domain auswählen können. SAML wird hauptsächlich zum Unterstützen der einmaligen Anmeldung in mehreren Domains verwendet. Wenn SAML als Ihr Authentifizierungsanbieter konfiguriert ist, melden sich Benutzende bei AEM Forms an und authentifizieren sich über einen angegebenen Identitätsanbieter (IDP) von Drittanbietern.

Eine Erläuterung von SAML finden Sie unter [Security Assertion Markup Language (SAML) V2.0 Technische Übersicht](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0.html).

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Benutzerverwaltung“ > „Konfiguration“ > „SAML-Dienstanbietereinstellungen“.
1. Geben Sie in das Feld „Dienstanbieter-Entitäts-ID“ eine eindeutige ID als Kennung für die AEM Forms-Dienstanbieterimplementierung ein.  Sie müssen diese eindeutige ID auch beim Konfigurieren Ihres Identitätsanbieters (IDP) (z. B. `um.lc.com` angeben.) Sie können außerdem die URL verwenden, die zum Zugreifen auf AEM Forms verwendet wird (z. B. `https://AEMformsserver`).
1. Geben Sie in das Feld für die Dienstanbieter-Basis-URL die Basis-URL für Ihren Formular-Server ein (z. B. `https://AEMformsserver:8080`).
1. (Optional) Wenn Sie möchten, dass AEM Forms signierte Authentifizierungsanforderungen an den Identitätsanbieter sendet, führen Sie die folgenden Aufgaben aus:

   * Verwenden Sie Trust Manager, um eine Berechtigung im Format „PKCS #12“ mit der ausgewählten Option „Berechtigung für die Dokumentsignierung“ als Trust Store-Typ zu importieren.  (Siehe [Verwalten lokaler Berechtigungen](/help/forms/using/admin-help/local-credentials.md#managing-local-credentials).)
   * Wählen Sie in der Liste mit den Schlüsselaliassen für Dienstanbieterberechtigungen den Alias aus, den Sie der Berechtigung im Trust Store zugewiesen haben.
   * Klicken Sie auf Exportieren , um den URL-Inhalt in einer Datei zu speichern und diese Datei dann in Ihren IDP zu importieren.

1. (Optional) Wählen Sie in der Liste der ID-Richtlinie für Dienstanbieternamen das Namensformat aus, das der IDP zum Identifizieren der Person in einer SAML-Assertion verwendet.  Die Optionen lauten „Nicht angegeben“, „E-Mail“ und „Windows Domain Qualified Name“.

   >[!NOTE]
   >
   >Bei Namensformaten muss nicht auf Groß- und Kleinschreibung geachtet werden.

1. (Optional) Aktivieren Sie die Option „Authentifizierungs-Eingabeaufforderung für lokale Benutzer aktivieren“.  Wenn diese Option ausgewählt ist, sehen Benutzer zwei Links:

   * eine Verknüpfung zur Anmeldeseite eines dritten SAML-Identitätsanbieters, wo sich Benutzer authentifizieren können, die zu einer Unternehmens-Domain gehören.
   * eine Verknüpfung zur AEM Forms-Anmeldeseite, wo sich Benutzer identifizieren können, die zu einer lokalen Domain gehören.

   Wenn diese Option nicht ausgewählt ist, werden Benutzer direkt zur Anmeldeseite des dritten SAML-Identitätsanbieters geleitet, wo sich Benutzer authentifizieren können, die zu einer Unternehmensdomäne gehören.

1. (Optional) Wählen Sie „Artefakt-Bindung“, um die Unterstützung für die Artefakt-Bindung zu aktivieren.  Standardmäßig wird die POST-Bindung mit SAML verwendet.  Wenn Sie jedoch die Artefakt-Bindung konfiguriert haben, wählen Sie diese Option aus.  Wenn diese Option ausgewählt ist, wird die tatsächliche Benutzerassertion nicht durch die Browser-Anforderung weitergeleitet.  Stattdessen wird ein Verweis zu der Assertion weitergeleitet und die Assertion wird mithilfe eines Backend-Web-Dienstaufrufs abgerufen.
1. (Optional) Wählen Sie „Bindung umleiten“ aus, um SAML-Bindungen zu unterstützen, die Umleitungen verwenden.
1. (Optional) Geben Sie unter „Benutzerdefinierte Eigenschaften“ weitere Eigenschaften an.  Die zusätzlichen Eigenschaften sind durch neue Zeilen getrennte Name-Wert-Paare.

   * Sie können AEM Forms für die Ausgabe einer SAML-Bestätigung für eine Gültigkeitsdauer konfigurieren, die der Gültigkeitsdauer einer Assertion eines Drittanbieters entspricht.  Damit die Zeitüberschreitung der SAML-Bestätigung des Drittanbieters berücksichtigt wird, fügen Sie die folgende Zeile in den benutzerdefinierten Eigenschaften hinzu:

     `saml.sp.honour.idp.assertion.expiry=true`

   * Fügen Sie folgende benutzerdefinierte Eigenschaft für die Verwendung von RelayState hinzu, um die URL zu bestimmen, zu der Benutzende nach erfolgreicher Authentifizierung weitergeleitet werden.

     `saml.sp.use.relaystate=true`

   * Fügen Sie die folgende benutzerdefinierte Eigenschaft hinzu, damit Sie die URL für die benutzerdefinierten Java™ Server Pages (JSP) konfigurieren können, die zum Rendern der registrierten Liste von Identitätsanbietern verwendet wird. Wenn Sie keine benutzerdefinierte Webanwendung bereitgestellt haben, wird die Liste auf der standardmäßigen User Management-Seite gerendert.

   `saml.sp.discovery.url=/custom/custom.jsp`

1. Klicken Sie auf „Speichern“.
