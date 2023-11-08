---
title: Konfigurieren der SAML-Dienstanbietereinstellungen
seo-title: Configure SAML service provider settings
description: Sie können die Einstellungen des SAML-Dienstanbieters so konfigurieren, dass sich Benutzer über einen angegebenen Identitätsanbieter (IDP) von Drittanbietern bei AEM Formularen anmelden und authentifizieren können.
seo-description: You can configure SAML service provider settings to allow users to login and authenticate to AEM forms via a specified third-party identity provider (IDP).
uuid: 14c706ad-8b1c-4c03-9cd4-97424f2162bc
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 1169d0d1-cbfb-486b-acca-9b9de3d410dc
exl-id: dd302cfb-eae1-4189-aa7b-9f2533ebd164
source-git-commit: c4cd9a61a226ace2a72d60b5b7b7432de12cb873
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 25%

---

# Konfigurieren der SAML-Dienstanbietereinstellungen{#configure-saml-service-provider-settings}

Security Assertion Markup Language (SAML) ist eine der Optionen, die Sie beim Konfigurieren der Autorisierung für eine Unternehmens- oder Hybrid-Domain auswählen können. SAML wird hauptsächlich zum Unterstützen der einmaligen Anmeldung in mehreren Domains verwendet. Wenn SAML als Ihr Authentifizierungsanbieter konfiguriert ist, melden sich Benutzer an und authentifizieren sich über einen angegebenen Identitäts-Provider (IDP) AEM Formularen.

Eine Erläuterung von SAML finden Sie unter [Security Assertion Markup Language (SAML) V2.0 - Technische Übersicht](https://www.oasis-open.org/committees/download.php/20645/sstc-saml-tech-overview-2%200-draft-10.pdf).

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Konfiguration&quot;> &quot;SAML-Dienstanbietereinstellungen&quot;.
1. Geben Sie in das Feld &quot;Service Provider Entity ID&quot;eine eindeutige ID ein, die als Kennung für die Implementierung des AEM Forms-Dienstanbieters verwendet werden soll. Sie müssen diese eindeutige ID auch beim Konfigurieren Ihres Identitätsanbieters (IDP) (z. B. `um.lc.com` angeben.) Sie können außerdem die URL verwenden, die zum Zugreifen auf AEM Forms verwendet wird (z. B. `https://AEMformsserver`).
1. Geben Sie in das Feld &quot;Service Provider Base URL&quot;die Basis-URL für Ihren Forms-Server ein (z. B. `https://AEMformsserver:8080`).
1. (Optional) Führen Sie die folgenden Aufgaben aus, damit AEM Formulare signierte Authentifizierungsanfragen an den IDP senden können:

   * Verwenden Sie Trust Manager, um eine Berechtigung im PKCS #12-Format zu importieren, wobei &quot;Document Signing Credential&quot;als Trust Store-Typ ausgewählt ist. (Siehe [Lokale Berechtigungen verwalten](/help/forms/using/admin-help/local-credentials.md#managing-local-credentials).
   * Wählen Sie in der Liste &quot;Schlüsselalias für Dienstanbieterberechtigungen&quot;den Alias aus, den Sie der Berechtigung in Trust Store zugewiesen haben.
   * Klicken Sie auf Exportieren , um den URL-Inhalt in einer Datei zu speichern, und importieren Sie dann diese Datei in Ihren IDP.

1. (Optional) Wählen Sie in der Liste &quot;Service Provider Name ID Policy&quot;das Namensformat aus, das der IDP verwendet, um den Benutzer in einer SAML-Assertion zu identifizieren. Die Optionen sind Nicht angegeben, E-Mail und Windows Domain Qualified Name.

   >[!NOTE]
   >
   >Bei Namensformaten wird nicht zwischen Groß- und Kleinschreibung unterschieden.

1. (Optional) Wählen Sie Authentifizierungspflicht für lokale Benutzer aktivieren aus. Wenn diese Option ausgewählt ist, sehen Benutzer zwei Links:

   * eine Verknüpfung zur Anmeldeseite eines dritten SAML-Identitätsanbieters, wo sich Benutzer authentifizieren können, die zu einer Unternehmens-Domain gehören.
   * eine Verknüpfung zur AEM Forms-Anmeldeseite, wo sich Benutzer identifizieren können, die zu einer lokalen Domain gehören.

   Wenn diese Option nicht ausgewählt ist, werden die Benutzer direkt zur Anmeldeseite des dritten SAML-Identitätsanbieters geführt, wo sich Benutzer authentifizieren können, die zu einer Unternehmens-Domain gehören.

1. (Optional) Wählen Sie &quot;Artefaktbindung aktivieren&quot;, um die Unterstützung für die Artefaktbindung zu aktivieren. Standardmäßig wird die POST-Bindung mit SAML verwendet. Wenn Sie jedoch die Artefaktbindung konfiguriert haben, wählen Sie diese Option aus. Wenn diese Option ausgewählt ist, wird die tatsächliche Benutzerassertion nicht über die Browser-Anforderung weitergeleitet. Stattdessen wird ein Verweis auf die Assertion übergeben und die Assertion mithilfe eines Backend-Webdienstaufrufs abgerufen.
1. (Optional) Wählen Sie &quot;Redirect Binding aktivieren&quot;, um SAML-Bindungen zu unterstützen, die Umleitungen verwenden.
1. (Optional) Geben Sie unter &quot;Benutzerdefinierte Eigenschaften&quot;zusätzliche Eigenschaften an. Die zusätzlichen Eigenschaften sind Name=Wert-Paare, getrennt durch neue Zeilen.

   * Sie können AEM Formulare so konfigurieren, dass eine SAML-Bestätigung für einen Gültigkeitszeitraum ausgegeben wird, der dem Gültigkeitszeitraum einer Bestätigung eines Drittanbieters entspricht. Um das Zeitlimit für die SAML-Assertion eines Drittanbieters zu berücksichtigen, fügen Sie die folgende Zeile in den benutzerdefinierten Eigenschaften hinzu:

     `saml.sp.honour.idp.assertion.expiry=true`

   * Fügen Sie die folgende benutzerdefinierte Eigenschaft für die Verwendung von RelayState hinzu, um die URL zu bestimmen, an die der Benutzer nach erfolgreicher Authentifizierung weitergeleitet wird.

     `saml.sp.use.relaystate=true`

   * Fügen Sie die folgende benutzerdefinierte Eigenschaft hinzu, um die URL für die benutzerdefinierten Java Server Pages (JSP) zu konfigurieren, die zum Rendern der registrierten Liste von Identitätsanbietern verwendet wird. Wenn Sie keine benutzerdefinierte Webanwendung bereitgestellt haben, wird die Liste auf der standardmäßigen User Management-Seite gerendert.

   `saml.sp.discovery.url=/custom/custom.jsp`

1. Klicken Sie auf Speichern.
