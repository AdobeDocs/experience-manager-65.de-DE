---
title: Verwenden der Document Security-Web-Seiten
description: Erfahren Sie, wie Sie zu Dokumentensicherheits-Web-Seiten navigieren, sie verwenden und sich bei ihnen anmelden können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Document Security
exl-id: caa31752-a02d-4d20-b7d9-c4aad5d0fae6
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '921'
ht-degree: 100%

---

# Verwenden der Document Security-Web-Seiten {#using-the-document-security-webpages}

Benutzende und Admins nutzen die Dokumentensicherheits-Web-Seiten zum Erstellen und Verwalten von Richtlinien, zum Verwalten richtliniengeschützter Dokumente und zum Überwachen von Ereignissen in Verbindung mit richtliniengeschützten Dokumenten.  Admins nutzen Webseiten auch zum Erstellen von Richtliniensätzen und Zuweisen von Richtliniensatzkoordinatorinnen bzw. -koordinatoren, zum Konfigurieren von Dokumentensicherheits-Standardeinstellungen, zum Verwalten der Registrierung eingeladener Benutzender und deren Konten sowie zum Überwachen und Verwalten von Server-, Richtlinien-, Benutzer- und Dokumenten-bezogenen Ereignissen.

>[!NOTE]
>
>Sie können sich auch mit Ihrem Benutzeranmeldekonto über Acrobat und andere Clientanwendungen bei Document Security anmelden. (Siehe [Einrichten des Zugriffs auf die Dokumentensicherheit in Client-Anwendungen](using-document-security-web-pages.md#setting-up-access-to-document-security-from-client-applications).)

Zum Öffnen der Web-Seiten benötigen Sie einen Browser sowie die URL und Ihre Anmeldeinformationen für die Dokumentensicherheit.  Die URL für Benutzende unterscheidet sich von der für Admins.

Da die Dokumentensicherheit die vorhandenen Verzeichnisse Ihres Unternehmens für Benutzerinformationen nutzt, können die Dokumentensicherheits-Anmeldeinformationen mit den Informationen übereinstimmen, mit denen Sie sich am Netzwerk und anderen Anwendungen anmelden.  Informationen zu Ihrem Konto erhalten Sie von Ihren Systemadmins oder Admins.

Um sich als Admin anmelden zu können, muss Ihnen die Rolle „Administrator“ zugewiesen worden sein.  Sie können das standardmäßige Superadministratorkonto verwenden, das während der Installation angelegt wird.

## Anmelden bei den Web-Seiten {#log-in-to-the-web-pages}

Zum Anmelden bei den Web-Seiten über einen Browser benötigen Sie die Dokumentensicherheits-URL sowie ein Konto.  Die URL für Benutzende unterscheidet sich von der für Admins. Admins können sich auch bei den Benutzerseiten anmelden, um Richtlinien zu erstellen.

Wenn Sie Zugriff auf mehrere Dokumentensicherheits-Installationen haben, benötigen Sie die URL der Instanz der Dokumentensicherheit, auf die Sie zugreifen möchten.  Wenden Sie sich an ihre Admins, falls Sie diese Informationen nicht haben.  Die Standard-URL für Benutzerseiten ist `https://[host]:[port]/edc`. In einigen Fällen ist die Port-Nummer möglicherweise nicht erforderlich.  Fragen Sie Ihre Admins nach Details.

Die Standard-URL für Administratoren lautet `https://[host]:[port]/adminui`.

Für Admins wird während der Installation ein standardmäßiges Superadministratorkonto angelegt.  Sie können sich mit diesem Konto anmelden, nachdem die Dokumentensicherheit erstmals installiert wurde.

>[!NOTE]
>
>Sie können auch in Acrobat und anderen Client-Anwendungen auf die Web-Seiten zugreifen.  Weitere Informationen finden Sie in der Acrobat-Hilfe oder der entsprechenden Hilfe zu den Acrobat Reader DC Erweiterungen.

1. Geben Sie die URL in den Browser ein.

   Document Security-URL: `https://[host]:[port]/edc`

   oder Administration Console-URL: `https://[host]:[port]/adminui`

1. Geben Sie im Anmeldefenster Ihren Benutzernamen und Ihr Kennwort ein und klicken Sie auf „OK“.
1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Dokumentensicherheit“.

>[!NOTE]
>
>Verwenden Sie beim Arbeiten mit Web-Seiten nicht die Schaltflächen des Browsers (z. B. die Schaltfläche „Zurück“, die Schaltfläche „Aktualisieren“ oder die Pfeilschaltflächen „Zurück“ und „Vorwärts“), da dies zu unerwünschten Problemen bei der Erfassung und Anzeige von Daten führen kann.

## Navigieren auf den Web-Seiten {#navigating-the-web-pages}

Wenn Sie sich bei den Benutzer-Web-Seiten anmelden, werden Links zu den Benutzerseiten „Richtlinien“, „Dokumente“ und „Ereignisse“ angezeigt.

Wenn Sie sich bei der Administrationskonsole anmelden und zur Dokumentensicherheits-Hauptseite wechseln, werden ggf. ein oder zwei zusätzliche Links angezeigt, und zwar einer zur Seite „Konfiguration“ und einer zur Seite „Eingeladene und lokale Benutzer“.  Die Seite „Eingeladene und lokale Benutzer“ wird nur angezeigt, wenn die Registrierung für eingeladene Benutzende aktiviert ist.

Über diese Links greifen Sie auf die verschiedenen Seiten zu, auf denen Sie Richtlinien und richtliniengeschützte Dokumente erstellen und verwalten können.

**Anzeigen einer Seite**

1. Klicken Sie auf den Namen der Seite, z. B. „Richtlinien“.

**Zurückkehren zur vorherigen Seite**

1. Klicken Sie oben auf der Seite auf den Navigations-Link der Seite, zu der Sie zurückkehren möchten.

**Aktualisieren der Datenanzeige auf einer Seite**

1. Klicken Sie auf der Hauptseite auf den Link zu der Seite, die Sie aktualisieren möchten.

>[!NOTE]
>
>Verwenden Sie beim Arbeiten mit Web-Seiten nicht die Schaltflächen des Browsers (z. B. die Schaltfläche „Zurück“, die Schaltfläche „Aktualisieren“ oder die Pfeilschaltflächen „Zurück“ und „Vorwärts“), da dies zu unerwünschten Problemen bei der Erfassung und Anzeige von Daten führen kann.

## Einrichten des Zugriffs auf die Dokumentensicherheit in Client-Anwendungen {#setting-up-access-to-document-security-from-client-applications}

Client-Anwendungen müssen so eingerichtet werden, dass sie eine Verbindung mit der Dokumentensicherheit herstellen, um Dokumente zu schützen, richtliniengeschützte Dokumente öffnen zu und die Verbindung mit den Dokumentensicherheits-Web-Seiten herzustellen.  Einzelheiten zum Konfigurieren der Verbindung in der Client-Anwendung finden Sie in der *Acrobat-Hilfe* oder der entsprechenden *RightsManagementExtension-Hilfe*.

Der Zugriff auf die Dokumentensicherheit erfolgt über SSL (Secure Sockets Layer).  Installieren Sie das Zertifikat der Website in Ihrem Zertifikatsspeicher, damit Sie über die Client-Anwendungen auf die Dokumentensicherheit zugreifen können.

<!-- Fix broken link See Configuring SSL for information on SSL.-->

Diese Anweisungen gelten für Internet Explorer. Sie können das Zertifikat jedoch auch mithilfe eines anderen unterstützten Webbrowsers installieren. Weitere Informationen finden Sie in der Hilfe für Ihren Browser.

**Installieren des Server-Zertifikats mit Internet Explorer**

1. Öffnen Sie den Webbrowser und geben Sie die Basis-URL für die Dokumentensicherheit in das Adressfeld ein. Geben Sie beispielsweise `https://[host]:[port]`. Es wird ein Dialogfeld mit einer Sicherheitswarnung angezeigt.
1. Klicken Sie auf „Zertifikat anzeigen“ und anschließend auf „Zertifikat installieren“ und übernehmen Sie die Standardeinstellungen für die Installation. Das Zertifikat muss unter „Vertrauenswürdige Stammzertifizierungsstellen“ installiert werden.
1. Schließen Sie die Browser-Sitzung.
1. Öffnen Sie ein weiteres Browser-Fenster und geben Sie dieselbe URL in das Adressfeld ein. Es sollte kein Dialogfeld mit einer Sicherheitswarnung angezeigt werden. Dieser Test bestätigt, dass das Zertifikat ordnungsgemäß installiert wurde.

## Abmelden von den Web-Seiten {#log-out-of-the-web-pages}

Melden Sie sich ab, wenn Sie Ihre Aufgaben auf den Web-Seiten erledigt haben, damit Sie den Webbrowser sicher für andere Zwecke verwenden können. Je nach Konfiguration der Dokumentensicherheit müssen Sie ggf. den Browser schließen, um sich vollständig abzumelden.

1. Klicken Sie oben rechts auf der Seite auf „Abmelden“.
1. Wenn eine Meldung auf der Seite „Abmelden“ angezeigt wird, schließen Sie das Browser-Fenster, um sich vollständig abzumelden. Ansonsten können Sie den Browser direkt für andere Zwecke weiterverwenden.
