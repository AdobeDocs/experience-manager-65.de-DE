---
title: Verwenden der Document Security-Web-Seiten
description: Erfahren Sie, wie Sie sich anmelden, auf den Document Security-Webseiten navigieren und diese verwenden können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Document Security
exl-id: caa31752-a02d-4d20-b7d9-c4aad5d0fae6
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '921'
ht-degree: 5%

---

# Verwenden der Document Security-Web-Seiten {#using-the-document-security-webpages}

Benutzer und Administratoren verwenden die Document Security-Webseiten zum Erstellen und Verwalten von Richtlinien, zum Verwalten richtliniengeschützter Dokumente und zum Überwachen von Ereignissen, die mit richtliniengeschützten Dokumenten verknüpft sind. Administratoren verwenden auch die Webseiten, um Richtliniensätze zu erstellen und Richtliniensatzkoordinatoren zu bestimmen, Standardeinstellungen für Document Security zu konfigurieren, die Registrierung und Konten eingeladener Benutzer zu verwalten sowie Server-, Richtlinien-, Benutzer- und dokumentbezogene Ereignisse zu überwachen und zu verwalten.

>[!NOTE]
>
>Sie können sich auch mit Ihrem Benutzeranmeldekonto über Acrobat und andere Clientanwendungen bei Document Security anmelden. (Siehe [Zugriff auf Document Security in Clientanwendungen einrichten](using-document-security-web-pages.md#setting-up-access-to-document-security-from-client-applications).

Zum Öffnen der Webseiten benötigen Sie einen Browser sowie die URL und Ihre Anmeldeinformationen für Document Security. Die URL für Benutzer unterscheidet sich von der URL für Administratoren.

Da Document Security die vorhandenen Ordner Ihres Unternehmens für Benutzerinformationen referenziert, können Ihre Document Security-Anmeldeinformationen mit den Informationen übereinstimmen, die Sie zum Anmelden in Ihrem Netzwerk und anderen Anwendungen verwenden. Informationen zu Ihrem Konto erhalten Sie von Ihrem Systemadministrator oder -administrator.

Damit Sie sich als Administrator anmelden können, müssen Sie die Administratorrolle zugewiesen haben. Sie können das standardmäßige Superadministrator-Konto verwenden, das während des Installationsprozesses erstellt wird.

## Bei den Webseiten anmelden {#log-in-to-the-web-pages}

Um sich über einen Browser bei den Webseiten anzumelden, benötigen Sie die Document Security-URL und ein Konto. Die URL für Benutzer unterscheidet sich von der URL für Administratoren. Administratoren können sich auch bei den Benutzerseiten anmelden, um Richtlinien zu erstellen.

Wenn Sie Zugriff auf mehr als eine Installation von Document Security haben, benötigen Sie die URL für die Instanz von Document Security, auf die Sie zugreifen möchten. Wenden Sie sich an Ihren Administrator, wenn Sie nicht über diese Informationen verfügen. Die Standard-URL für Benutzerseiten ist `https://[host]:[port]/edc`. In einigen Fällen ist die Portnummer möglicherweise nicht erforderlich. Fragen Sie Ihren Administrator nach Details.

Die Standard-URL für Administratoren lautet `https://[host]:[port]/adminui`.

Für Administratoren wird während der Installation ein standardmäßiges Superadministratorkonto erstellt. Sie können dieses Konto verwenden, um sich anzumelden, wenn Document Security zum ersten Mal installiert wird.

>[!NOTE]
>
>Sie können auch über Acrobat und andere Clientanwendungen auf die Webseiten zugreifen. Weitere Informationen finden Sie in der Hilfe zu Acrobat oder in der entsprechenden Hilfe zu Acrobat Reader DC-Erweiterungen .

1. Geben Sie die URL in Ihren Browser ein:

   Document Security-URL: `https://[host]:[port]/edc`

   oder Administration Console-URL: `https://[host]:[port]/adminui`

1. Geben Sie im Anmeldefenster Ihren Benutzernamen und Ihr Kennwort ein und klicken Sie auf &quot;OK&quot;.
1. Klicken Sie in Administration Console auf Dienste > Document Security.

>[!NOTE]
>
>Vermeiden Sie beim Arbeiten mit Webseiten die Verwendung von Browser-Schaltflächen wie der Zurück-, der Aktualisierungs- und der Zurück- und der Vorwärts-Taste, da diese Aktion zu unerwünschten Problemen bei der Datenerfassung und Datenanzeige führen kann.

## Navigieren auf den Webseiten {#navigating-the-web-pages}

Wenn Sie sich bei den Benutzer-Webseiten anmelden, sehen Sie Links zu den Benutzerseiten &quot;Richtlinien&quot;, &quot;Dokumente&quot;und &quot;Ereignisse&quot;.

Wenn Sie sich bei Administration Console anmelden und zur Document Security-Hauptseite navigieren, werden möglicherweise auch ein oder zwei weitere Links angezeigt: einer für die Seite &quot;Konfiguration&quot;und einer für die Seite &quot;Eingeladene und lokale Benutzer&quot;. Die Seite Eingeladene und lokale Benutzer wird nur angezeigt, wenn die Registrierung für eingeladene Benutzer aktiviert ist.

Verwenden Sie diese Links, um auf die verschiedenen Seiten zuzugreifen, auf denen Sie Richtlinien und richtliniengeschützte Dokumente erstellen und verwalten.

**Anzeigen einer Seite**

1. Klicken Sie auf den Namen der Seite, z. B. auf Richtlinien .

**Zurück zur vorherigen Seite**

1. Klicken Sie oben auf der Seite auf den Navigationslink der Seite, zu der Sie zurückkehren möchten.

**Datenliste auf einer Seite aktualisieren**

1. Klicken Sie auf der Hauptseite auf den Link zu der Seite, die Sie aktualisieren möchten.

>[!NOTE]
>
>Vermeiden Sie beim Arbeiten mit Webseiten die Verwendung von Browser-Schaltflächen wie der Zurück-, der Aktualisierungs- und der Zurück- und der Vorwärts-Taste, da diese Aktion zu unerwünschten Problemen bei der Datenerfassung und Datenanzeige führen kann.

## Zugriff auf Document Security in Clientanwendungen einrichten {#setting-up-access-to-document-security-from-client-applications}

Clientanwendungen müssen so eingerichtet sein, dass sie eine Verbindung zu Document Security herstellen, um Dokumente zu schützen, richtliniengeschützte Dokumente zu öffnen und eine Verbindung zu den Document Security-Webseiten herzustellen. Siehe *Hilfe zu Acrobat* oder *RightsManagementExtension-Hilfe* für Informationen zum Konfigurieren der Verbindung innerhalb der Clientanwendung.

Der Zugriff auf Document Security erfolgt über Secure Sockets Layer (SSL). Installieren Sie das Zertifikat der Website in Ihrem Zertifikatspeicher, damit Sie über die Clientanwendungen auf Document Security zugreifen können.

<!-- Fix broken link See Configuring SSL for information on SSL.-->

Diese Anweisungen gelten speziell für Internet Explorer. Sie können das Zertifikat jedoch mit einem beliebigen unterstützten Webbrowser installieren. Weitere Informationen finden Sie in der Hilfe für Ihren Browser.

**Installieren des Serverzertifikats mit Internet Explorer**

1. Öffnen Sie Ihren Webbrowser und geben Sie die Basis-URL für Document Security in das Feld &quot;Adresse&quot;ein. Geben Sie beispielsweise `https://[host]:[port]`. Ein Dialogfeld mit einer Sicherheitswarnung wird angezeigt.
1. Klicken Sie auf Zertifikat anzeigen , klicken Sie auf Zertifikat installieren und wählen Sie die Standardeinstellungen für die Installation aus. Das Zertifikat muss in den vertrauenswürdigen Stammzertifizierungsstellen installiert sein.
1. Schließen Sie die Browser-Sitzung.
1. Öffnen Sie ein anderes Browser-Fenster und geben Sie dieselbe URL in das Feld Adresse ein. Ein Dialogfeld mit Sicherheitswarnung sollte nicht angezeigt werden. Dieser Test bestätigt, dass das Zertifikat ordnungsgemäß installiert ist.

## Von den Webseiten abmelden {#log-out-of-the-web-pages}

Melden Sie sich ab, wenn Sie mit den Webseiten fertig sind, damit Sie Ihren Webbrowser sicher für andere Zwecke verwenden können. Abhängig davon, wie Document Security konfiguriert ist, müssen Sie möglicherweise den Browser schließen, um sich vollständig abzumelden.

1. Klicken Sie oben rechts auf der Seite auf Abmelden .
1. Wenn eine Meldung auf der Seite &quot;Abmelden&quot;angezeigt wird, schließen Sie das Browser-Fenster, um sich vollständig abzumelden. Andernfalls können Sie den Browser für andere Zwecke verwenden.
