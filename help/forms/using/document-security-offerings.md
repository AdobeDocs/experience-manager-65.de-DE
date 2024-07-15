---
title: Document Security-Angebote
description: Erfahren Sie mehr über die verschiedenen Tools und Funktionen von AEM Document Security
contentOwner: khsingh
geptopics: SG_AEMFORMS/categories/working_with_document_security
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Document Security
exl-id: d00ae232-b018-44e5-b04b-376d4cd9c6eb
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '1161'
ht-degree: 100%

---

# Document Security-Angebote{#document-security-offerings}

Adobe Experience Manager Forms Document Security stellt sicher, dass nur autorisierte Personen Ihre Dokumente verwenden können. Mithilfe von Document Security können Sie Informationen, die Sie in einem unterstützten Format gespeichert haben, sicher verteilen. Zu den unterstützten Dateiformaten gehören Adobe Portable Document Format (PDF) sowie Microsoft® Word-, Excel- und PowerPoint-Dateien.

Sie können Dokumente mithilfe von Richtlinien schützen. Die Vertraulichkeitseinstellungen, die Sie in einer Richtlinie angeben, bestimmen, wie ein Dokument, auf das Sie die Richtlinie anwenden, genutzt werden darf. Sie können beispielsweise angeben, ob Empfängerinnen und Empfänger Text drucken oder kopieren, Text bearbeiten oder geschützten Dokumenten Signaturen und Kommentare hinzufügen können.

Die Richtlinien werden zwar auf dem Document Security-Server gespeichert, Sie wenden sie jedoch über Ihre Client-Anwendung auf Dokumente an. Wenn Sie eine Richtlinie auf ein Dokument anwenden, schützen die in der Richtlinie angegebenen Vertraulichkeitseinstellungen die Informationen, die das Dokument enthält. Sie können das richtliniengeschützte Dokument an Empfängerinnen und Empfänger verteilen, die durch die Richtlinie autorisiert sind.

Die folgende Abbildung zeigt die typische Architektur für die Dokumentensicherheit in AEM Forms:

![Document Security - Empfohlene Architektur](do-not-localize/document_security_architecture.png)

## Document Security-Clients {#document-security-clients}

Document Security stellt verschiedene Clients bereit, um Dokumente zu schützen, geschützte Dokumente und Indexer anzuzeigen und zu bearbeiten, um die Volltextsuche in geschützten Dokumenten zu aktivieren. Sie können je nach Ihren Anforderungen und den benötigten Funktionen einen Client auswählen.

Der Document Security-Server ist die zentrale Komponente, über die Document Security Transaktionen wie z. B. die Authentifizierung von Benutzenden, die Richtlinienverwaltung in Echtzeit und das Anwenden von Vertraulichkeit ausführt. Der Server stellt außerdem ein zentrales Repository für Richtlinien, Auditdatensätze und andere zugehörige Informationen bereit.

Der Document Security-Server bietet eine Web-basierte Oberfläche (Web-Seite) zum Erstellen von Richtlinien, zum Verwalten richtliniengeschützter Dokumente und zum Überwachen von Ereignissen, die mit richtliniengeschützten Dokumenten verknüpft sind. Admins können auch globale Optionen wie Benutzerauthentifizierung, Auditing und Messaging für eingeladene Personen konfigurieren und Konten eingeladener Personen verwalten.

Der Server ist im AEM Forms Document Security-Add-On-Angebot enthalten. Sie können sich an das [Verkaufs-Team](https://business.adobe.com/request-consultation/experience-cloud.html?s_osc=70114000002JNwKAAW&amp;s_iid=70114000002JHs3AAG) von AEM Forms wenden, um das Document Security-Add-On zu erwerben.

### Schützen von Dokumenten {#protect-documents}

AEM Forms Document Security bietet verschiedene Tools zum Anwenden von Sicherheitsrichtlinien. Sie können je nach Anforderungen und Spezifikationen ein Tool auswählen.

![document-security-offerings](assets/document-security-offerings.png)

Sie können Document Security SDK, Adobe Acrobat, Document Security Extension für Microsoft® Office oder Portable Protection Library verwenden, um die Sicherheitsrichtlinien anzuwenden und nachzuverfolgen:

* **Document Security SDK:** Das SDK ist ein Client mit vielen Funktionen. Sie können das Document Security SDK verwenden, um auf Document Server-Funktionen zuzugreifen, richtliniengeschützte Dokumente zu öffnen und benutzerdefinierte Erweiterungen, Plug-ins oder Anwendungen zu entwickeln. Sie können beispielsweise Erweiterungen entwickeln, um benutzerdefinierte Dateiformate zu schützen oder das SDK in DLP-Lösungen (Data Loss Prevention) zu integrieren. Erweiterungen, Anwendungen und Plug-ins, die mit Document Security SDK entwickelt wurden, senden Dokumente an bestimmte AEM Forms-Server und die Richtlinien werden auf den Server angewendet. Der AEM Forms Document Security Client SDK (CSDK) kann die mit der Portable Protection Library (PPL) geschützten Dokumente nicht aufheben und umgekehrt.

  Das Document Security SDK ist für Java™ und C++ verfügbar. Java™ SDK ist in AEM Forms Document Security enthalten und wird bei der Bereitstellung von AEM Forms on JEE installiert. Kontaktieren Sie den [AEM Kundensupport](https://experienceleague.adobe.com/?lang=de&amp;support-solution=General&amp;support-tab=home#support), um das C++-SDK zu erhalten. Das C++-SDK kann mit Microsoft® Visual Studio 2013 kompiliert werden. Rufen Sie die [Document Security API-Dokumentation](https://help.adobe.com/de_DE/livecycle/11.0/Services/WS92d06802c76abadb76c48dfe12dbeb3e281-7ff0.2.html) auf, um mehr über die Funktionen des SDK zu erfahren.

* **Adobe Acrobat**: Sie können Adobe Acrobat verwenden, um Sicherheitsrichtlinien auf PDF-Dokumente anzuwenden, die mit gängigen Desktop-Anwendungen wie Microsoft® Office, Webbrowsern oder anderen Anwendungen, die den Druck im PDF-Format unterstützen, erstellt wurden.

  Sie können Adobe Acrobat von der [Adobe-Website](https://www.adobe.com/de/acrobat/free-trial-download.html) erwerben und herunterladen. Im Adobe Acrobat-Artikel [Sicherheitsrichtlinien für PDF-Dateien einrichten](https://helpx.adobe.com/de/acrobat/using/setting-security-policies-pdfs.html) finden Sie ausführliche Informationen zum Erstellen und Anwenden von Richtlinien in Adobe Acrobat.

* **Document Security Extension für Microsoft® Office**: Sie können die Document Security Extension für Microsoft® Office verwenden, um vordefinierte Richtlinien auf Ihre Microsoft® Office-Dateien in den Microsoft® Office-Programmen anzuwenden. Die Erweiterung stellt sicher, dass nur autorisierte Personen richtliniengeschützte Microsoft® Word-, Excel- und PowerPoint-Dateien verwenden können. Nur autorisierte Benutzende, die das Plug-in installiert haben, können die richtliniengeschützten Dateien verwenden.

  Die Document Security-Erweiterung ist als Plug-in für Microsoft® Office verfügbar. Wenden Sie sich an den [AEM Kunden-Support](https://helpx.adobe.com/de/marketing-cloud/contact-support.html), um die Erweiterung zu beziehen. Später können Sie die Hilfe zur [Document Security Extension für Microsoft® Office](https://experienceleague.adobe.com/docs/experience-manager-document-security/using/download-installer.html?lang=de) zum Installieren, Konfigurieren und zur Verwendung der Erweiterung verwenden.

* **Portable Protection Library:** Die PPL schützt ein Dokument lokal, ohne dass das Dokument an den AEM Forms-Server gesendet wird. Nur die Sicherheitsberechtigungen und Details der Schutzrichtlinie werden über das Netzwerk gesendet. Mit PPL können Sie auch den Zugriff auf die Richtlinienabfrage auf angemeldete Personen beschränken. Sie können Richtlinien mit dem Kontext der Person abrufen, der als AEM-Benutzerin oder -Benutzer angemeldet ist.

  Darüber hinaus verfügt das PPL über alle Funktionen des Document Security SDK. Sie können das Document Security SDK verwenden, um auf Document Server-Funktionen zuzugreifen, richtliniengeschützte Dokumente zu öffnen und benutzerdefinierte Erweiterungen, Plug-ins oder Anwendungen zu entwickeln. Die PPL kann den Schutz der mit dem AEM Forms Document Security Client SDK (CSDK) geschützten Dokumente nicht aufheben und umgekehrt.

  Die PPL ist für die Sprachen Java und C++ in 32-Bit- und 64-Bit-Versionen verfügbar.  Sie ist auch als OSGi-Bundle für AEM Forms unter OSGi verfügbar. Die C++-PPL kann mit Microsoft® Visual Studio 2013 kompiliert werden. Wenn Sie das AEM Forms Document Security-Add-on lizenziert haben, können Sie sich an das Support-Team für [AEM Forms Document Security](https://experienceleague.adobe.com/?lang=de&amp;support-solution=General&amp;support-tab=home#support) wenden, um die PPL zu beschaffen. Später können Sie die PPL-Hilfe (im Lieferumfang der Bibliothek enthalten) verwenden, um die PPL einzurichten und zu verwenden.

### Anzeigen oder Bearbeiten von geschützten Dokumenten {#view-or-edit-protected-documents}

* Für **PDF-Dokumente** können Sie Adobe Acrobat DC, Acrobat Reader und Acrobat Reader Mobile verwenden, um geschützte PDF-Dokumente anzuzeigen. Die meisten Benutzenden haben Acrobat Reader bereits auf ihren Geräten installiert, sodass sie keine zusätzliche Software benötigen, um geschützte Dokumente anzuzeigen. Sie können Acrobat Reader auch über die [Website zum Download von Acrobat Reader](https://get.adobe.com/de/reader/) herunterladen.

* Für **Microsoft® Office-Dokumente** benötigen Sie Microsoft® Office und die AEM Forms Document Security-Erweiterung für Microsoft® Office. Die Document Security-Erweiterung ist als Plug-in für Microsoft® Office verfügbar. Sie können die Erweiterung von der Adobe-Website herunterladen.

### Indexgeschützte Dokumente {#index-protected-documents}

Microsoft® Windows-Volltextsuchmaschinen (SharePoint Index Server) und Adobe Experience Manager (AEM) können Volltextsuchen für häufig verwendete Dokumentformate wie Textdateien, Microsoft® Office-Dokumente und PDF-Dokumente durchführen. Sie können Document Security-Indexer verwenden, um Volltext-Suchmaschinen für die Suche nach geschützten PDF-Dokumenten zu aktivieren:

* **iFilter-Indexer:** Sie können den iFilter-Indexer verwenden, um geschützte PDF-Dokumente zu indizieren und Microsoft® Windows-Volltextsuchmaschinen (Desktop Indexing Service und SharePoint Index Server) zu ermöglichen, geschützte PDF-Dokumente zu durchsuchen. Ausführlichere Informationen finden Sie unter [AEM SharePoint iFilter für geschützte Dokumente](assets/sharepoint-ifilter-doc-security.pdf).

* **AEM Forms Document Security-Impulszähler:** Sie können den AEM Document Security-Impulszähler verwenden, um geschützte PDF-Dokumente mit einem Index zu versehen und Adobe Experience Manager aktivieren, um geschützte PDF-Dokumente zu suchen. Die Indexer sind Teil des AEM Forms Document Security-Angebots. Diese sind in AEM Forms on JEE-Installationsprogrammen enthalten.
