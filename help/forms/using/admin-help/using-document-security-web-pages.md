---
title: Verwenden der Document Security-Webseiten
seo-title: Verwenden der Document Security-Webseiten
description: Erfahren Sie, wie Sie zu Document Security-Webseiten navigieren und sie verwenden und sich bei ihnen anmelden.
seo-description: Erfahren Sie, wie Sie zu Document Security-Webseiten navigieren und sie verwenden und sich bei ihnen anmelden.
uuid: b4863343-cda5-474a-a101-a20e39b1f8c7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 2878b145-e6c0-48d3-810c-3540de13c826
feature: Dokumentensicherheit
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 97%

---


# Verwenden der Document Security-Webseiten {#using-the-document-security-webpages}

Benutzer und Administratoren nutzen die Document Security-Webseiten zum Erstellen und Verwalten von Richtlinien, zum Verwalten richtliniengeschützter Dokumente und zum Überwachen von Ereignissen in Verbindung mit richtliniengeschützten Dokumenten. Administratoren nutzen Webseiten auch zum Erstellen von Richtliniensätzen und Zuweisen von Richtliniensatzkoordinatoren, zum Konfigurieren von Document Security-Standardeinstellungen, zum Verwalten der Registrierung und der Konten eingeladener Benutzer sowie zum Überwachen und Verwalten server-, richtlinien-, benutzer- und dokumentbezogener Ereignisse.

>[!NOTE]
>
>Sie können sich auch mit Ihrem Benutzeranmeldekonto über Acrobat und andere Clientanwendungen bei Document Security anmelden. (Siehe [Zugriff auf Document Security in Clientanwendungen einrichten](using-document-security-web-pages.md#setting-up-access-to-document-security-from-client-applications).)

Zum Öffnen der Webseiten benötigen Sie einen Browser sowie die URL und Ihre Anmeldeinformationen für Document Security. Die URL für Benutzer unterscheidet sich von der für Administratoren.

Da Document Security die vorhandenen Ordner Ihres Unternehmens für Benutzerinformationen nutzt, können die Document Security-Anmeldeinformationen mit den Informationen übereinstimmen, mit denen Sie sich am Netzwerk und anderen Anwendungen anmelden. Informationen zu Ihrem Konto erhalten Sie vom Systemadministrator bzw. Administrator.

Um sich als Administrator anmelden zu können, muss Ihnen die Rolle „Administrator“ zugewiesen worden sein. Sie können das standardmäßige Superadministratorkonto verwenden, das während der Installation angelegt wird.

## Anmelden an den Webseiten {#log-in-to-the-web-pages}

Zum Anmelden bei den Webseiten über einen Browser benötigen Sie die Document Security-URL sowie ein Konto. Die URL für Benutzer unterscheidet sich von der für Administratoren. Administratoren können sich auch an den Benutzerseiten anmelden, um Richtlinien zu erstellen.

Wenn Sie Zugriff auf mehrere Document Security-Installationen haben, benötigen Sie die URL der Instanz von Document Security, auf die Sie zugreifen möchten. Befragen Sie den Administrator, sollten Sie diese Informationen nicht haben. Die Standard-URL für die Benutzerseiten ist `https://[host]:[port]/edc`. In einigen Fällen ist die Anschlussnummer möglicherweise nicht erforderlich. Fragen Sie Ihren Administrator nach Details.

Die Standard-URL für Administratoren ist `https://[host]:[port]/adminui`.

Für Administratoren wird ein standardmäßiges Superadministratorkonto während der Installation angelegt. Sie können sich mit diesem Konto anmelden, nachdem Document Security erstmals installiert wurde.

>[!NOTE]
>
>Sie können auch in Acrobat und anderen Clientanwendungen auf die Webseiten zugreifen. Weitere Informationen finden Sie in der Acrobat-Hilfe oder der entsprechenden Acrobat Reader DC Extensions-Hilfe.

1. Geben Sie die URL in den Browser ein.

   Dokument-Sicherheits-URL: `https://[host]:[port]/edc`

   oder URL der Administrationskonsole: `https://[host]:[port]/adminui`

1. Geben Sie im Anmeldefenster Ihren Benutzernamen und Ihr Kennwort ein und klicken Sie auf „OK“.
1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security“.

>[!NOTE]
>
>Verwenden Sie beim Arbeiten mit Webseiten nicht die Schaltflächen im Browser (z. B. die Schaltfläche „Zurück“, die Schaltfläche „Aktualisieren“ oder die Pfeilschaltflächen „Zurück“ und „Vorwärts“), da dies zu unerwünschten Problemen bei der Erfassung und Anzeige von Daten führen kann.

## Auf den Webseiten navigieren  {#navigating-the-web-pages}

Wenn Sie sich an den Benutzerwebseiten anmelden, werden Hyperlinks zu den Benutzerseiten „Richtlinien“, „Dokumente“ und „Ereignisse“ angezeigt.

Wenn Sie sich bei Administration Console anmelden und zur Document Security-Hauptseite wechseln, werden ggf. ein oder zwei zusätzliche Hyperlinks angezeigt, und zwar einer zur Seite „Konfiguration“ und einer zur Seite „Eingeladene und lokale Benutzer“. Die Seite „Eingeladene und lokale Benutzer“ wird nur angezeigt, wenn die Registrierung für eingeladene Benutzer aktiviert ist.

Über diese Links greifen Sie auf die verschiedenen Seiten zu, auf denen Sie Richtlinien und richtliniengeschützte Dokumente erstellen und verwalten können.

**Eine Seite anzeigen**

1. Klicken Sie auf den Namen der Seite, z. B. Richtlinien.

**Zur vorherigen Seite zurückgelangen**

1. Klicken Sie oben auf der Seite auf den Navigations-Hyperlink der Seite, zu der Sie zurückkehren möchten.

**Die Datenanzeige auf einer Seite aktualisieren**

1. Klicken Sie auf der Hauptseite auf den Link zu der Seite, die Sie aktualisieren möchten.

>[!NOTE]
>
>Verwenden Sie beim Arbeiten mit Webseiten nicht die Schaltflächen im Browser (z. B. die Schaltfläche „Zurück“, die Schaltfläche „Aktualisieren“ oder die Pfeilschaltflächen „Zurück“ und „Vorwärts“), da dies zu unerwünschten Problemen bei der Erfassung und Anzeige von Daten führen kann.

## Zugriff auf Document Security in Clientanwendungen einrichten  {#setting-up-access-to-document-security-from-client-applications}

Clientanwendungen müssen so eingerichtet werden, dass sie eine Verbindung mit Document Security herstellen, um Dokumente zu schützen, richtliniengeschützte Dokumente öffnen und die Verbindung mit den Document Security-Webseiten herzustellen. Einzelheiten zum Konfigurieren der Verbindung in der Client-Anwendung finden Sie in der *Acrobat-Hilfe* oder der entsprechenden *RightsManagementExtension-Hilfe*.

Der Zugriff auf Document Security erfolgt über SSL (Secure Sockets Layer). Sie müssen das Zertifikat der Website in Ihrem Zertifikatspeicher installieren, damit Sie über die Clientanwendungen auf Document Security zugreifen können.

<!-- Fix broken link See Configuring SSL for information on SSL.-->

Diese Anweisungen gelten für Internet Explorer. Sie können das Zertifikat jedoch auch mithilfe eines anderen unterstützten Browsers installieren. Weitere Informationen finden Sie in der Dokumentation zum jeweiligen Browser.

**In Internet Explorer das Serverzertifikat installieren**

1. Öffnen Sie den Browser und geben Sie die Basis-URL für Document Security in das Feld „Adresse“ ein. Geben Sie beispielsweise `https://[host]:[port]`. Ein Dialogfeld mit einer Sicherheitswarnung wird angezeigt.
1. Klicken Sie auf „Zertifikat anzeigen“ und anschließend auf „Zertifikat installieren“ und übernehmen Sie die Standardeinstellungen für die Installation. Das Zertifikat muss in der „Vertrauenswürdigen Stammzertifizierungsstelle“ installiert sein.
1. Schließen Sie die Browsersitzung.
1. Öffnen Sie ein weiteres Browser-Fenster und geben Sie die Basis-URL in das Feld „Adresse“ ein. Ein Dialogfeld mit einer Sicherheitswarnung sollte nicht angezeigt werden. Dieser Test bestätigt, dass das Zertifikat ordnungsgemäß installiert wurde.

## Von den Webseiten abmelden  {#log-out-of-the-web-pages}

Melden Sie sich ab, wenn Sie die Aufgaben auf den Webseiten erledigt haben, damit Sie den Browser sicher für andere Zwecke verwenden können. Je nach Konfiguration von Document Security müssen Sie den Browser schließen, um sich vollständig abzumelden.

1. Klicken Sie oben rechts auf der Seite auf „Abmelden“.
1. Wenn eine Meldung auf der Seite „Abmelden“ angezeigt wird, schließen Sie das Browserfenster, um sich vollständig abzumelden. Ansonsten können Sie den Browser für andere Zwecke weiter verwenden.

