---
title: Einführung in AEM Forms
description: Verwenden Sie dieses AEM 6.5-Handbuch, um digitale Formulare zu erstellen, zu verwalten, zu veröffentlichen und zu aktualisieren. Hier finden Sie Hilfe zur Installation, Aktualisierung und Konfiguration und erfahren, wie Sie adaptive Formulare erstellen können.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: introduction
docset: aem65
feature: Adaptive Forms
exl-id: e5533b4f-93b7-4ea9-a01d-fdf9528652c8
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 24523ac85b1ac455f4bdf32a0a725cb99e0de497
workflow-type: ht
source-wordcount: '950'
ht-degree: 100%

---

# Einführung in AEM Forms{#introduction-to-aem-forms}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/forms-overview/home.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

Informationen zu den neuesten Funktionen und Verbesserungen in AEM Forms finden Sie unter [Neue Funktionen in AEM Forms](../../forms/using/whats-new.md).

## Informationen zu AEM Forms {#about-aem-forms}

Adobe Experience Manager (AEM) ist eine benutzerfreundliche Lösung, mit der Sie komplexe digitale Formulare erstellen, verwalten, veröffentlichen und aktualisieren und dabei in Backend-Prozesse, Geschäftsregeln und Daten integrieren können.

Mit AEM Forms lassen sich Funktionen zum Erstellen, Verwalten und Veröffentlichen von Formularen mit Korrespondenzverwaltung, Dokumentensicherheit und integrierter Analyse zu einer griffigen End-to-End-Lösung kombinieren. AEM Forms wurde für die Verwendung sowohl über Web- als auch über Mobilkanäle konzipiert und kann effizient in Ihre Geschäftsprozesse integriert werden, sodass Sie Papierprozesse und Fehler reduzieren können, während Sie die Effizienz verbessern.

Bei großen Unternehmen werden Formulare häufig nur einmal erstellt und dann wiederverwendet, indem sie in ein Content-Management-System kopiert werden. Eine umfangreiche Datenbank mit Formularen aktuell zu halten und diese für Erkennungsfunktionen zugänglich zu machen, kann eine erhebliche Herausforderung darstellen.  AEM bietet ein anpassbares Formularportal, das Kundinnen und Kunden eine Suchfunktion und den Zugriff auf Formulare sowohl über Web-Kanäle als auch über mobile Kanäle ermöglicht.

AEM Forms bietet Tools zur Formularverwaltung, mit denen sich neben adaptiven Formularen auch XFA-Formulare, PDF-Formulare und zugehörige Elemente verwalten lassen. Weitere Informationen finden Sie in der [Einführung in das Verwalten von Formularen](../../forms/using/introduction-managing-forms.md).

>[!NOTE]
>
>Die Funktion „Adaptive Formulare“, verfügbar in [AEM 6.5 QuickStart](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html?lang=de), dient nur zu Kennenlern- und Evaluierungszwecken. Für die Verwendung in der Produktion muss eine gültige Lizenz für AEM Forms erworben werden, da für die Funktion „Adaptive Formulare“ eine Lizenzierung erforderlich ist.

![AEM Forms-Funktionen](do-not-localize/4th-draft-updated.gif)

### Schlüsselfunktionen {#key-capabilities}

Zusammenfassend lässt sich sagen, dass AEM Forms leistungsstarke Formularverwaltungsfunktionen wie die folgenden bietet, die manuelle Prozesse reduzieren und die Kundenzufriedenheit erhöhen.

* Ein zentralisiertes Formularportal zum Entwickeln und Bereitstellen von dynamischen Formularen, einschließlich PDF, HTML5 und adaptiver Formulare.
* Eine benutzerfreundliche grafische Benutzeroberfläche, mit der Benutzende im Geschäftsbereich Formulare mühelos importieren, verwalten, in der Vorschau anzeigen und veröffentlichen können.
* Ein responsives Formularverzeichnis mit leistungsstarken Suchfunktionen anhand von Schlüsselwörtern, Tags und Metadaten.
* Dynamische Erkennung des Geräts und Standorts einer Benutzerin oder eines Benutzers, um das Formular korrekt über Web- und mobile Kanäle wiederzugeben.
* Integration in Adobe Analytics, um Formularverwendungsmetriken effektiv zu messen.
* Integration in Adobe Document Cloud-eSign-Diensten oder Freihandskizzen zur elektronischen Verschlüsselung von Dokumenten mit vertraulichen Informationen.
* Automatisierte Formularveröffentlichungsfunktionen und die Möglichkeit, zeitnahe, personalisierte und konsistente Kommunikation über mehrere Kanäle bereitzustellen.

## AEM-Formulartypen {#aem-form-types}

Mit AEM Forms können Sie neue und vorhandene Formulare erweitern, um Folgendes zu erstellen:

* Pixel-genaue, paginierte HTML- und PDF-Formulare, die fast wie Papier aussehen, oder
* adaptive Formulare, die automatisch für das Gerät und den Browser einer Benutzerin oder eines Benutzers gerendert werden.

**PDF-Formulare**

PDF-Formulare können offline ausgefüllt und lokal gespeichert werden. Die Formulardaten werden dann gesendet, wenn Sie wieder online sind.  Sie können 2D-Barcodes verwenden, um Formulardaten zu erfassen, und digitale Signaturen verwenden, um die Authentizität für Benutzende zu validieren.

**HTML-Formulare**

Browser-basierte HTML5-Formulare können sowohl auf Mobilgeräten als auch auf Desktop-Browsern angezeigt werden.  Sie können HTML-Formulare mithilfe von Freihandskizzen oder eSign-Diensten elektronisch signieren.

**Adaptive Formulare**

Adaptive Formulare können sich dynamisch an Benutzerantworten anpassen, indem Felder oder Abschnitte nach Bedarf hinzugefügt oder entfernt werden.  Mit AEM können Sie Adobe XML-Formularvorlagen verwenden, um adaptive Formulare zu erstellen.

### Unterstützte Funktionen {#supported-features}

Alle Formulartypen unterstützen die folgenden Funktionen:

* Dynamisches Layout
* Formularfeldvalidierung
* Kontextbezogene Hilfe
* Skripterstellung und Verarbeitung von XML-Daten
* Barrierefreiheits-Design und -prüfung
* Möglichkeit, Formulare auf Server-Seite zu speichern
* Unterstützung für Dateianhänge
* Integration in HTML Workspace zur Datenerfassung

## Offline-Datenerfassung {#offline-data-collection}

Wenn Formulardaten gesendet wurden, verbindet Adobe Experience Manager die Formulardaten mit vorhandenen Systemen, Geschäftsregeln und den gewünschten Personen.

AEM Forms umfasst Forms Workspace, eine Mobile App, die Ihre digitalen Geschäftsprozesse auf Mobilgeräte erweitert.  Mit Forms Workspace können Sie Daten auch dann erfassen und aufzeichnen, wenn Sie offline sind.  Forms Workspace nutzt die Funktionen Ihres Mobilgeräts und ermöglicht Ihnen das Erfassen von Fotos und Videos sowie das Erfassen von Daten wie Zeitstempeln und anderen Informationen. Wenn Sie das nächste Mal mit einem Netzwerk verbunden sind, können Sie dann die erfassten Daten synchronisieren.

Besonders für Menschen, die viel unterwegs sind, ist es nützlich, Daten offline zu erfassen und sie zu synchronisieren, wenn sie das nächste Mal online sind.  Dies verbessert die Produktivität und reduziert Fehler.

**Vorteile der Verwendung von Forms Workspace für die Offline-Datenerfassung**

* Benutzerfreundliche HTML-Workspace-Anwendung für Aufgabenzuweisung und -Tracking
* Workflow-Design-Umgebung mit Drag-and-Drop-Funktion
* Enterprise Content Management-(ECM-)Connectoren
* Unterstützung offener Standards, einschließlich XML und SOAP, um Formulardaten mit Unternehmenssystemen zu verbinden.
* Standardmäßig verfügbare HTML-Berichte, um Arbeitsrückstände, Warteschlangen und wichtige Leistungsindikatoren (KPIs) zu überwachen.
* Anpassbare Dashboards für Einblicke in Geschäftsvorgänge in Echtzeit
* API für die Verbindung mit Berichts-Tools von Drittanbietern

![Dritter Entwurf](do-not-localize/3rd-draft.gif)

## Personalisierte Kommunikation {#personalized-communication}

Eine wichtige Komponente für effizienten digitalen Self-Service ist die Kommunikation zeitnaher, personalisierter Informationen, auf die Benutzer von überall aus und mit jedem Gerät zugreifen können. Personalisierte und zeitnahe Kommunikation kann Konversionsraten und Benutzerzufriedenheit verbessern.

Mit AEM Forms können Benutzer interessante personalisierte Benutzererfahrungen schaffen, indem sie Dokumentvorlagen anpassen, Informationen aus Back-End-Prozessen integrieren und interaktive Komponenten aufnehmen. Eine intuitive Benutzeroberfläche hilft Benutzenden ohne technische Fachkenntnisse dabei, Geschäftsregeln zu entwickeln, die bestimmen, ob eine Kommunikation basierend auf einer Anforderung erstellt oder eine benutzergenerierte Antwort initiiert werden soll.

Personalisierte Dokumente wie Empfangsbestätigungen, Willkommens-Kits oder Anweisungen können einfach über mehrere Kanäle bereitgestellt werden.  Unternehmen können Traffic zu personalisierten Internet-Portalen steuern, was zu mehr Registrierungen oder Kauf von zusätzlichen Diensten führt.

**Wichtigste Funktionen**

* Korrespondenz-Authoring-Umgebung mit Unterstützung für Vorlagen, Inhaltsblöcke und Geschäftsregeln
* Dokumentkonvertierung und -assemblierung
* Unterstützung für bedarfsmäßige oder Batch-Dokumentzustellung über mehrere Kanäle, einschließlich Web, E-Mail und Papier
* Audit-Protokolle mit Änderungshistorie
* Unterstützung für digitale Signaturen zum Validieren der Inhaltsintegrität und der Identität der oder des Unterzeichnenden
* Document Security-Add-On für AEM Forms mit Funktionen für Verschlüsselung, Nutzungsrichtlinien, Tracking und Auditing

![Layout 2](do-not-localize/layout-02.png)

Optimierter Workflow für personalisierte Kommunikation

