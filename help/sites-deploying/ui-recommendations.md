---
title: Empfehlungen für Kunden zur Benutzeroberfläche
seo-title: User Interface Recommendations for Customers
description: Eine Liste von Empfehlungen zu den klassischen und Touch-optimierten Benutzeroberflächen.
seo-description: A list of recommendations related to the classic and touch-optimized user interfaces.
uuid: 9ec2c9de-a79e-4f2c-a90f-b38ba9553e07
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 8f06d4b6-7d30-4ebc-9c6a-3bb8607a9be8
docset: aem65
exl-id: 7b71119a-ff58-47c0-aeef-a705ed8c40e0
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 46%

---

# Empfehlungen für Kunden zur Benutzeroberfläche{#user-interface-recommendations-for-customers}

Adobe Experience Manager verfügt über zwei Benutzeroberflächen: die einheitliche Experience Cloud-Benutzeroberfläche (auch als Touch-optimierte Benutzeroberfläche bezeichnet) und die klassische Benutzeroberfläche.

Dieses Dokument soll Kunden dabei helfen, die zu verwendende Benutzeroberfläche entsprechend ihrer Situation zu bestimmen.

Interessensgebiete:

* **Benutzeroberfläche (oder Standardbenutzeroberfläche)** Eine moderne Benutzeroberfläche, die in Version 5.6.0 als Technologievorschau eingeführt und in nachfolgenden Versionen erweitert wurde. Sie basiert auf dem einheitlichen Benutzererlebnis für Adobe Experience Cloud, das früher als Touch-optimierte Benutzeroberfläche oder Touch-Benutzeroberfläche bezeichnet wurde.

* **Klassische Benutzeroberfläche** Eine auf der ExtJS-Technologie basierende Benutzeroberfläche, die 2008 zusammen mit CQ 5.1 eingeführt wurde.

* **Seiten-Administrator** Funktionen zum Verwalten der Seitenhierarchie (Verschieben, Aktivieren, verwaltete Verweise) und Erstellen von neuen Seiten.

* **Seitenbearbeitung** Funktionen zum Hinzufügen von Inhalten zu einer Seite bzw. zum Bearbeiten des Seiteninhalts.

* **DAM-/Asset-Admin** Funktionen zum Verwalten digitaler Assets (einschließlich Bildern, Video, Dokumenten, Downloads).

* **ContextHub** Funktionen zum Aggregieren von Informationen über den Besucher und zum Verwenden derselben für verschiedene Zwecke. Stellt eine Benutzeroberfläche zum Simulieren von Personen bereit, die die Site besuchen. Ab AEM 6.2 ersetzt ContextHub die bisherige Technologie ClientContext.

## Allgemein {#general}

In den vergangenen Jahren hat Adobe alle Adobe Experience Cloud-Lösungen um eine einheitlichen Benutzeroberfläche erweitert. Benutzer der Experience Cloud-Lösungen profitieren so von einem konsistenten Erlebnis mit einem einheitlichen Verwendungsmuster für die Anwendungen. Mit jeder Version hat Adobe seine Benutzeroberfläche auf der Grundlage des Feedbacks von Kunden optimiert, die in den verschiedenen Lösungen arbeiten.

Die ursprüngliche Benutzeroberfläche für Adobe Experience Manager (früher CQ5), die 2008 eingeführt wurde und von Kunden mit den Versionen 5.0-5.6.1 verwendet wird, ist in AEM 6.5 enthalten. Dadurch wird sichergestellt, dass Kunden auf Version 6.5 aktualisieren und von einer aktualisierten Plattform mit neuen Funktionen profitieren können, während sie weiterhin dieselbe Benutzeroberfläche verwenden.

Adobe empfiehlt Kunden, den Umstieg auf die neue Benutzeroberfläche für 2018/19 zu planen. Dies kann entweder während der Aktualisierung auf 6.5 oder in separaten Projekten nach der Aktualisierung erfolgen, die die erforderlichen Anpassungen an den Dialogfeldern für Anpassungen und Komponenten enthalten.

Die klassische Benutzeroberfläche ist seit AEM 6.4 veraltet und Adobe hat nicht die Absicht, weitere Verbesserungen an der klassischen Benutzeroberfläche vorzunehmen. Beachten Sie, dass die klassische Benutzeroberfläche zwar veraltet ist, aber weiterhin umfassend unterstützt wird.

### Richtlinien und Empfehlungen {#rules-and-recommendations}

Im Folgenden finden Sie eine Liste der Empfehlungen von Product Management für Adobe Experience Manager 6.5:

<table>
 <tbody>
  <tr>
   <th>Mein Projekt...</th>
   <th>Empfehlungen</th>
  </tr>
  <tr>
   <td>Beginnt gerade mit der Verwendung von Adobe Experience Manager.</td>
   <td>Verwenden Sie die standardmäßige Benutzeroberfläche.</td>
  </tr>
  <tr>
   <td><p>Verwendet AEM eine Weile.</p> <p>Hat die vordefinierte Produktoberfläche verwendet und benutzerdefinierte Komponenten für die Sites entwickelt.<br /> </p> </td>
   <td>
    <ol>
     <li>Aktualisierung auf 6.5</li>
     <li>Verwenden Sie die Standard-Benutzeroberfläche für die Site-Verwaltung, Assets, ... usw.<br /> </li>
     <li>Konfigurieren Sie die Aktion "Seite bearbeiten", um den Seiten-Editor für die klassische Benutzeroberfläche zu öffnen. Siehe <a href="#selecting-your-ui">Auswählen der Benutzeroberfläche</a>.</li>
    </ol> <p>In einer zweiten Phase:</p>
    <ol>
     <li>Aktualisieren Sie Ihre Komponentendialogfelder, um das Coral 3-Dialogfeldformat zu verwenden. Adobe empfiehlt die Verwendung der <a href="/help/sites-developing/modernization-tools.md">AEM Modernisierungs-Tools</a> , um die Komponenten zu aktualisieren.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Hat eine Site erstellt, die die ClientContext mit Integrationen verwendet.<br /> </td>
   <td>
    <ol>
     <li>Aktualisierung auf 6.5</li>
     <li>Verwenden Sie die Standard-Benutzeroberfläche für die Site-Verwaltung, Assets, ... usw.</li>
     <li>Konfigurieren Sie die Aktion "Seite bearbeiten", um den Seiten-Editor für die klassische Benutzeroberfläche zu öffnen. Siehe <a href="#selecting-your-ui">Auswählen der Benutzeroberfläche</a>.</li>
    </ol> <p>In einer zweiten Phase:</p>
    <ol>
     <li>Aktualisieren Sie Ihre Komponentendialogfelder, um das Coral 3-Dialogfeldformat zu verwenden. Adobe empfiehlt die Verwendung der <a href="/help/sites-developing/modernization-tools.md">AEM Modernisierungs-Tools</a> , um die Komponenten zu aktualisieren.</li>
     <li>Konfigurieren Sie ContextHub (ersetzt ClientContext) und aktualisieren Sie die Seitenvorlagen für die Anwendung von ContextHub. Der ContextHub verfügt über einen Kompatibilitätsmodus, der das Laden benutzerdefinierter ClientContext-Stores ermöglicht.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><p>Verwendet seit vielen Jahren CQ/AEM.</p> <p>Hat die Produktoberfläche (z. B. Site Admin) erweitert und Komponenten mit umfangreichen Bearbeitungsdialogfeldern erstellt.</p> </td>
   <td><p>Aktualisierung auf 6.5 durchführen und die klassische Benutzeroberfläche als Standardbenutzeroberfläche zur Seitenbearbeitung für alle Benutzer konfigurieren. Siehe <a href="#selecting-your-ui">Auswählen der Benutzeroberfläche</a>.</p> <p>Starten Sie anschließend ein Projekt, um die Änderungen zu übernehmen und die Komponentendialogfelder im Coral 3-Format zu optimieren. Siehe <a href="#resources-to-help">Hilfe-Ressourcen</a>.<br /> </p> </td>
  </tr>
 </tbody>
</table>

### Häufig gestellte Fragen (FAQ) {#faq}

Siehe den Knowledge Base-Artikel . [Häufig gestellte Fragen zur Bearbeitung der Touch-optimierten Benutzeroberfläche](https://helpx.adobe.com/de/experience-manager/kb/index/touchui_faq.html), um Details anzuzeigen, einschließlich Informationen zum Zeitplan für die Einstellung der Verwendung der klassischen Benutzeroberfläche.

### Auswählen der Benutzeroberfläche {#selecting-your-ui}

Weitere Informationen zur erforderlichen Konfiguration Ihres Systems finden Sie unter [Festlegen der Benutzeroberfläche](/help/sites-authoring/select-ui.md).

### Status der Touch-optimierten Benutzeroberfläche {#touch-enabled-ui-status}

Weitere Informationen zu den Verbesserungen an der Touch-optimierten Benutzeroberfläche in AEM 6.5 finden Sie unter [Neue Funktionen](/help/release-notes/release-notes.md#what-s-new) in den Versionshinweisen.

Einen vollständigen Überblick finden Sie auf der Seite [Status der Funktionen der Touch-optimierten Benutzeroberfläche](/help/release-notes/touch-ui-features-status.md).

### Hilfe-Ressourcen {#resources-to-help}

Hintergrundinformationen zur grundlegenden Handhabung:

* [Authoring von Seiten](/help/sites-authoring/page-authoring.md).

Detaillierte Entwicklungsinformationen:

* [Architektur der Touch-optimierten Benutzeroberfläche](/help/sites-developing/touch-ui-concepts.md).
* Verwenden Sie die [AEM-Modernisierungs-Tools](/help/sites-developing/modernization-tools.md), um die Dialogfelder für die Komponentenbearbeitung von der klassischen Benutzeroberfläche in die Touch-optimierte Benutzeroberfläche zu konvertieren.

* [Struktur der Touch-optimierten Benutzeroberfläche](/help/sites-developing/touch-ui-structure.md).

* [Anpassen von Konsolen in der Touch-optimierten Benutzeroberfläche](/help/sites-developing/customizing-consoles-touch.md) (einschließlich Beispiel-Code).

* [Anpassen der Seitenbearbeitung in der Touch-optimierten Benutzeroberfläche](/help/sites-developing/customizing-page-authoring-touch.md) (einschließlich Beispiel-Code).

* [Dokumentation zur Granite-Benutzeroberfläche](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html)
