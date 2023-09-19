---
title: Document Security-Angebote
description: Erfahren Sie mehr über verschiedene Tools und Funktionen von AEM Document Security.
contentOwner: khsingh
geptopics: SG_AEMFORMS/categories/working_with_document_security
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Document Security
exl-id: d00ae232-b018-44e5-b04b-376d4cd9c6eb
source-git-commit: 65c5a4442f17e6bc52deaa1588f535a05698083f
workflow-type: tm+mt
source-wordcount: '1216'
ht-degree: 24%

---

# Document Security-Angebote{#document-security-offerings}

Adobe Experience Manager Forms Document Security stellt sicher, dass nur autorisierte Benutzer Ihre Dokumente verwenden können. Mithilfe von Document Security können Sie Informationen, die Sie in einem unterstützten Format gespeichert haben, sicher verteilen. Zu den unterstützten Dateiformaten gehören Adobe Portable Document Format (PDF) sowie Microsoft® Word-, Excel- und PowerPoint-Dateien.

Sie können Dokumente mithilfe von Richtlinien schützen. Die Vertraulichkeitseinstellungen, die Sie in einer Richtlinie angeben, bestimmen, wie ein Dokument, auf das Sie die Richtlinie anwenden, genutzt werden darf. Sie können beispielsweise angeben, ob Empfängerinnen und Empfänger Text drucken oder kopieren, Text bearbeiten oder geschützten Dokumenten Signaturen und Kommentare hinzufügen können.

Die Richtlinien werden auf dem Document Security-Server gespeichert. Sie wenden die Richtlinien über Ihre Clientanwendung auf Dokumente an. Wenn Sie eine Richtlinie auf ein Dokument anwenden, schützen die in der Richtlinie angegebenen Vertraulichkeitseinstellungen die Informationen, die das Dokument enthält. Sie können das richtliniengeschützte Dokument an Empfängerinnen und Empfänger verteilen, die durch die Richtlinie autorisiert sind.

Die folgende Abbildung zeigt die typische Architektur für die Dokumentensicherheit in AEM Forms:

![Document Security - Empfohlene Architektur](do-not-localize/document_security_architecture.png)

## Document Security-Clients {#document-security-clients}

Document Security bietet verschiedene Clients zum Schützen von Dokumenten, zum Anzeigen und Bearbeiten geschützter Dokumente und Indexer, um die Volltextsuche in geschützten Dokumenten zu ermöglichen. Sie können einen Client auswählen, der auf Ihren Anforderungen und den Funktionen des Clients basiert.

Document Security Server ist die zentrale Komponente, über die Document Security Transaktionen wie die Benutzerauthentifizierung, die Echtzeit-Verwaltung von Richtlinien und die Anwendung von Vertraulichkeit durchführt. Der Server stellt außerdem ein zentrales Repository für Richtlinien, Auditdatensätze und andere zugehörige Informationen bereit.

Der Document Security-Server bietet eine webbasierte Oberfläche (Webseite) zum Erstellen von Richtlinien, zum Verwalten richtliniengeschützter Dokumente und zum Überwachen von Ereignissen, die mit richtliniengeschützten Dokumenten verknüpft sind. Admins können auch globale Optionen wie Benutzerauthentifizierung, Auditing und Messaging für eingeladene Benutzende konfigurieren und Konten eingeladener Benutzender verwalten.

Der Server ist im AEM Forms Document Security-Add-On-Angebot enthalten. Sie können AEM Forms kontaktieren [Vertriebsteam](https://business.adobe.com/request-consultation/experience-cloud.html?s_osc=70114000002JNwKAAW&amp;s_iid=70114000002JHs3AAG) , um das Document Security-Add-on zu erwerben.

### Protect-Dokumente {#protect-documents}

AEM Forms Document Security bietet verschiedene Tools zum Anwenden von Sicherheitsrichtlinien. Sie können ein Tool gemäß Ihren Anforderungen und Spezifikationen auswählen.

![document-security-offerings](assets/document-security-offerings.png)

Sie können Document Security SDK, Adobe Acrobat, Document Security Extension for Microsoft® Office oder Portable Protection Library verwenden, um die Sicherheitsrichtlinien anzuwenden und zu verfolgen:

* **Document Security SDK:** Das SDK ist ein Client mit vielen Funktionen. Sie können das Document Security SDK verwenden, um auf die Document Server-Funktionalität zuzugreifen, richtliniengeschützte Dokumente zu öffnen und benutzerdefinierte Erweiterungen, Plug-ins oder Anwendungen zu entwickeln. Sie können beispielsweise Erweiterungen entwickeln, um benutzerdefinierte Dateiformate zu schützen oder das SDK in DLP-Lösungen (Data Loss Prevention) zu integrieren. Erweiterungen, Anwendungen und Plug-ins, die mithilfe des Document Security SDK entwickelt wurden, um Dokumente an den vorgesehenen AEM Forms-Server zu senden, und die Richtlinien werden auf den Server angewendet. Das AEM Forms Document Security Client SDK (CSDK) kann den Schutz der mit der Portable Protection Library (PPL) geschützten Dokumente nicht aufheben und umgekehrt.

  Das Document Security SDK ist sowohl für Java™ als auch für C++ verfügbar. Java™ SDK ist im AEM Forms Document Security-Angebot enthalten und wird bei der Bereitstellung von AEM Forms on JEE installiert. Kontakt [AEM Kundensupport](https://experienceleague.adobe.com/?lang=de&amp;support-solution=General&amp;support-tab=home#support) , um das C++-SDK zu erhalten. Das C++ SDK kann mit Microsoft® Visual Studio 2013 kompiliert werden. Besuchen Sie die [Dokumentation zur Document Security API](https://help.adobe.com/de_DE/livecycle/11.0/Services/WS92d06802c76abadb76c48dfe12dbeb3e281-7ff0.2.html) Site, auf der Sie die Funktionen des SDK lernen und verwenden können.

* **Adobe Acrobat:** Sie können Adobe Acrobat verwenden, um Sicherheitsrichtlinien auf PDF-Dokumente anzuwenden, die mit gängigen Desktop-Applikationen wie Microsoft® Office, Webbrowsern oder beliebigen Applikationen erstellt wurden, die das Drucken im PDF-Format unterstützen.

  Sie können Adobe Acrobat über das [Adobe-Website](https://www.adobe.com/acrobat/free-trial-download.html). Im Adobe Acrobat-Artikel [Sicherheitsrichtlinien für PDF-Dateien einrichten](https://helpx.adobe.com/acrobat/using/setting-security-policies-pdfs.html) finden Sie ausführliche Informationen zum Erstellen und Anwenden von Richtlinien in Adobe Acrobat.

* **Document Security Extension for Microsoft® Office**: Sie können die Document Security Extension for Microsoft® Office verwenden, um vordefinierte Richtlinien auf Ihre Microsoft® Office-Dateien in den Microsoft® Office-Programmen anzuwenden. Die Erweiterung stellt sicher, dass nur autorisierte Personen richtliniengeschützte Microsoft® Word-, Excel- und PowerPoint-Dateien verwenden können. Nur autorisierte Benutzer, die das Plug-in installiert haben, können die richtliniengeschützten Dateien verwenden.

  Die Document Security-Erweiterung ist als Microsoft® Office-Plug-in verfügbar. Kontakt [AEM Kundensupport](https://helpx.adobe.com/de/marketing-cloud/contact-support.html) , um die Erweiterung zu erhalten. Später können Sie [Document Security Extension for Microsoft® Office](https://experienceleague.adobe.com/docs/experience-manager-document-security/using/download-installer.html?lang=de) Hilfe zum Installieren, Konfigurieren und Verwenden der Erweiterung.

* **Portable Protection Library:** Die PPL schützt ein Dokument lokal, ohne es an den AEM Forms-Server zu senden. Nur Sicherheitsberechtigungen und Richtliniendetails werden über das Netzwerk übertragen. Mit PPL können Sie außerdem den Richtlinienabfragezugriff auf nur angemeldete Benutzer beschränken. Sie können Richtlinien mit dem Kontext des Benutzers abrufen, der als AEM-Benutzer angemeldet ist.

  Zusammen mit den oben genannten Funktionen verfügt die PPL über alle Funktionen des Document Security SDK. Sie können das Document Security SDK verwenden, um auf die Document Server-Funktionalität zuzugreifen, richtliniengeschützte Dokumente zu öffnen und benutzerdefinierte Erweiterungen, Plug-ins oder Anwendungen zu entwickeln. Die PPL kann den Schutz der mit dem AEM Forms Document Security Client SDK (CSDK) geschützten Dokumente nicht aufheben und umgekehrt.

  Die PPL ist für Java™- und C++-Sprachen in 32-Bit- und 64-Bit-Versionen verfügbar. Sie ist auch als OSGi-Bundle für AEM Forms unter OSGi verfügbar. Die C++ PPL kann mit Microsoft® Visual Studio 2013 kompiliert werden. Wenn Sie das AEM Forms Document Security-Add-on lizenziert haben, können Sie sich an den [AEM Forms Document Security](https://experienceleague.adobe.com/?lang=de&amp;support-solution=General&amp;support-tab=home#support) Support-Team für die Beschaffung der PPL. Später können Sie die PPL-Hilfe (im Paket mit der Bibliothek) verwenden, um die PPL einzurichten und zu verwenden.

### Anzeigen oder Bearbeiten geschützter Dokumente {#view-or-edit-protected-documents}

* Für **PDF-Dokumente** können Sie Adobe Acrobat DC, Acrobat Reader und Acrobat Reader Mobile verwenden, um geschützte PDF-Dokumente anzuzeigen. Die meisten Benutzer haben Acrobat Reader bereits auf ihren Geräten installiert, sodass sie keine zusätzliche Software benötigen, um geschützte Dokumente anzuzeigen. Sie können die Acrobat Reader auch über die [Acrobat Reader-Download-Website](https://get.adobe.com/de/reader/).

* Für **Microsoft® Office-Dokumente** benötigen Sie Microsoft® Office und AEM Forms Document Security Extension for Microsoft® Office. Die Document Security-Erweiterung ist als Microsoft® Office-Plug-in verfügbar. Sie können die Erweiterung von der Adobe-Website herunterladen.

### Indexgeschützte Dokumente {#index-protected-documents}

Microsoft® Windows-Volltextsuchmaschinen (SharePoint Index Server) und Adobe Experience Manager (AEM) können Volltextsuchen für häufig verwendete Dokumentformate wie Textdateien, Microsoft® Office-Dokumente und PDF-Dokumente durchführen. Sie können Document Security-Indexer verwenden, um Volltext-Suchmaschinen für die Suche nach geschützten PDF-Dokumenten zu aktivieren:

* **iFilter-Indexer:** Sie können den iFilter-Indexer verwenden, um geschützte PDF-Dokumente zu indizieren und Microsoft® Windows-Volltextsuchmaschinen (Desktop Indexing Service und SharePoint Index server) zu aktivieren, um geschützte PDF-Dokumente zu durchsuchen. Detaillierte Informationen finden Sie unter [AEM SharePoint IFilter für geschützte Dokumente](assets/sharepoint-ifilter-doc-security.pdf).

* **AEM Forms Document Security-Impulszähler:** Sie können den AEM Document Security-Impulszähler verwenden, um geschützte PDF-Dokumente mt einem Index zu versehen und die Adobe Experience Manager aktivieren, um geschützte PDF-Dokumente zu suchen. Die Indexer sind Teil des AEM Forms Document Security-Angebots. Diese sind in AEM Forms in JEE-Installationsprogrammen enthalten.
