---
title: Empfehlungen für Kunden zur Benutzeroberfläche
description: Eine Liste mit Empfehlungen zur klassischen und zur Touch-optimierten Benutzeroberfläche.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
docset: aem65
exl-id: 7b71119a-ff58-47c0-aeef-a705ed8c40e0
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '788'
ht-degree: 100%

---

# Empfehlungen für Kunden zur Benutzeroberfläche{#user-interface-recommendations-for-customers}

Adobe Experience Manager verfügt über zwei Benutzeroberflächen: die einheitliche Experience Cloud-Benutzeroberfläche (auch als Touch-optimierte Benutzeroberfläche bekannt) und die klassische Benutzeroberfläche.

Dieses Dokument soll Kundinnen und Kunden bei der Auswahl der richtigen Benutzeroberfläche für ihre Anforderungen helfen.

Verwendete Begriffe:

* **Benutzeroberfläche (oder Standardbenutzeroberfläche)** Eine moderne Benutzeroberfläche, die in Version 5.6.0 als Technologievorschau eingeführt und in nachfolgenden Versionen erweitert wurde. Sie basiert auf dem einheitlichen Benutzererlebnis für Adobe Experience Cloud, das früher als Touch-optimierte Benutzeroberfläche oder Touch-Benutzeroberfläche bezeichnet wurde.

* **Klassische Benutzeroberfläche** Eine auf der ExtJS-Technologie basierende Benutzeroberfläche, die 2008 zusammen mit CQ 5.1 eingeführt wurde.

* **Seiten-Administrator** Funktionen zum Verwalten der Seitenhierarchie (Verschieben, Aktivieren, verwaltete Verweise) und Erstellen von neuen Seiten.

* **Seitenbearbeitung** Funktionen zum Hinzufügen von Inhalten zu einer Seite bzw. zum Bearbeiten des Seiteninhalts.

* **DAM-/Asset-Admin** Funktionen zum Verwalten digitaler Assets (einschließlich Bildern, Video, Dokumenten, Downloads).

* **ContextHub** Funktionen zum Aggregieren von Informationen über den Besucher und zum Verwenden derselben für verschiedene Zwecke. Stellt eine Benutzeroberfläche zum Simulieren von Personen bereit, die die Site besuchen. Ab AEM 6.2 ersetzt ContextHub die bisherige Technologie ClientContext.

## Allgemein {#general}

In den vergangenen Jahren hat Adobe alle Adobe Experience Cloud-Lösungen um eine einheitlichen Benutzeroberfläche erweitert. Benutzer der Experience Cloud-Lösungen profitieren so von einem konsistenten Erlebnis mit einem einheitlichen Verwendungsmuster für die Anwendungen. In jeder neuen Version wurde die Benutzeroberfläche von Adobe auf Basis von Kunden-Feedback zu den verschiedenen Lösungen verbessert.

Die ursprüngliche Benutzeroberfläche von Adobe Experience Manager (zuvor als CQ5 bekannt), die 2008 eingeführt und von Kundinnen und Kunden mit den Versionen 5.0 bis 5.6.1 verwendet wurde, ist in AEM 6.5 verfügbar. So wird sichergestellt, dass Kundinnen und Kunden eine Aktualisierung auf die Version 6.5 durchführen und von einer aktualisierten Plattform mit neuen Funktionen profitieren können, während sie gleichzeitig dieselbe Benutzeroberfläche weiterverwenden.

Adobe empfiehlt Kunden, den Umstieg auf die neue Benutzeroberfläche für 2018/19 zu planen. Dies ist entweder im Rahmen einer Aktualisierung auf Version 6.5 möglich oder im Rahmen separater Projekte nach der Aktualisierung, bei der die notwendige Anpassung des Dialogfelds und die Änderung der Dialogkomponenten vorgenommen werden müssen.

Die klassische Benutzeroberfläche ist seit AEM 6.4 veraltet und Adobe hat nicht die Absicht, weitere Verbesserungen an der klassischen Benutzeroberfläche vorzunehmen. Beachten Sie, dass die klassische Benutzeroberfläche zwar veraltet ist, aber weiterhin umfassend unterstützt wird.

### Richtlinien und Empfehlungen {#rules-and-recommendations}

Nachfolgend finden Sie eine Liste mit Empfehlungen der Produkt-Management-Abteilung für Adobe Experience Manager 6.5:

<table>
 <tbody>
  <tr>
   <th>Situation</th>
   <th>Empfehlungen</th>
  </tr>
  <tr>
   <td>Ich habe gerade erst begonnen, Adobe Experience Manager für mein Projekt zu verwenden.</td>
   <td>Verwenden Sie die Standardbenutzeroberfläche.</td>
  </tr>
  <tr>
   <td><p>Ich verwende AEM bereits seit einiger Zeit für mein Projekt.</p> <p>Für mein Projekt wird die vorkonfigurierte Produktbenutzeroberfläche genutzt, bei Entwicklung benutzerdefinierter Komponenten für die Sites.<br /> </p> </td>
   <td>
    <ol>
     <li>Aktualisieren Sie auf 6.5.</li>
     <li>Verwenden Sie die Standardbenutzeroberfläche für die Site-Administration, Assets, usw.<br /> </li>
     <li>Konfigurieren Sie die Aktion „Seite bearbeiten“, um den Seiteneditor der klassischen Benutzeroberfläche zu öffnen. Siehe <a href="#selecting-your-ui">Auswahl der Benutzeroberfläche</a>.</li>
    </ol> <p>Anschließend:</p>
    <ol>
     <li>Aktualisieren Sie Ihre Komponentendialogfelder, um das Coral 3-Dialogfeldformat zu verwenden. Adobe empfiehlt, die <a href="/help/sites-developing/modernization-tools.md">AEM-Modernisierungs-Tools</a> zu nutzen, um die Komponenten zu aktualisieren.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Für mein Projekt wurde eine Site erstellt, die die ClientContext-Komponente mit Integrationen verwendet.<br /> </td>
   <td>
    <ol>
     <li>Aktualisieren Sie auf 6.5.</li>
     <li>Verwenden Sie die Standardbenutzeroberfläche für die Site-Administration, Assets, usw.</li>
     <li>Konfigurieren Sie die Aktion „Seite bearbeiten“, um den Seiteneditor der klassischen Benutzeroberfläche zu öffnen. Siehe <a href="#selecting-your-ui">Auswahl der Benutzeroberfläche</a>.</li>
    </ol> <p>Anschließend:</p>
    <ol>
     <li>Aktualisieren Sie Ihre Komponentendialogfelder, um das Coral 3-Dialogfeldformat zu verwenden. Adobe empfiehlt, die <a href="/help/sites-developing/modernization-tools.md">AEM-Modernisierungs-Tools</a> zu nutzen, um die Komponenten zu aktualisieren.</li>
     <li>Konfigurieren Sie ContextHub (ersetzt ClientContext) und aktualisieren Sie die Seitenvorlagen für die Anwendung von ContextHub. ContextHub verfügt über einen Kompatibilitätsmodus, mit dem benutzerdefinierte ClientContext-Stores geladen werden können.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><p>Verwendet CQ/AEM seit vielen Jahren.</p> <p>Hat die Produktbenutzeroberfläche (z. B. Website-Verwaltung) erweitert und Komponenten mit umfangreichen Dialogfeldern zum Bearbeiten erstellt.</p> </td>
   <td><p>Aktualisierung auf 6.5 durchführen und die klassische Benutzeroberfläche als Standardbenutzeroberfläche zur Seitenbearbeitung für alle Benutzer konfigurieren. Siehe <a href="#selecting-your-ui">Festlegen der Benutzeroberfläche</a>.</p> <p>Starten Sie anschließend ein Projekt, um die Änderungen zu übernehmen und die Komponentendialogfelder im Coral 3-Format zu optimieren. Siehe <a href="#resources-to-help">Hilfreiche Ressourcen</a>.<br /> </p> </td>
  </tr>
 </tbody>
</table>

### Häufig gestellte Fragen (FAQ) {#faq}

Weitere Einzelheiten finden Sie im Knowledgebase-Artikel [Seitenbearbeitung mit der Touch-optimierten Benutzeroberfläche – Häufig gestellte Fragen (FAQ)](https://helpx.adobe.com/de/experience-manager/kb/index/touchui_faq.html), inklusive Informationen zur geplanten Entfernung der klassischen Benutzeroberfläche.

### Festlegen der Benutzeroberfläche {#selecting-your-ui}

Weitere Informationen zur erforderlichen Konfiguration Ihres Systems finden Sie unter [Festlegen der Benutzeroberfläche](/help/sites-authoring/select-ui.md).

### Status der Funktionen der Touch-optimierten Benutzeroberfläche {#touch-enabled-ui-status}

Einzelheiten zu den Verbesserungen an der Touch-optimierten Benutzeroberfläche in AEM 6.5 finden Sie in den Versionshinweisen unter [Neue Funktionen](/help/release-notes/release-notes.md#what-s-new).

Einen vollständigen Überblick finden Sie auf der Seite [Status der Funktionen der Touch-optimierten Benutzeroberfläche](/help/release-notes/touch-ui-features-status.md).

### Hilfreiche Ressourcen {#resources-to-help}

Hintergrundinformationen zur grundlegenden Bearbeitung:

* [Authoring-Seiten](/help/sites-authoring/page-authoring.md).

Für detaillierte Entwicklungsinformationen:

* [Design der Touch-optimierten Benutzeroberfläche](/help/sites-developing/touch-ui-concepts.md).
* Verwenden Sie die [AEM-Modernisierungs-Tools](/help/sites-developing/modernization-tools.md), um die Dialogfelder für die Komponentenbearbeitung von der klassischen Benutzeroberfläche in die Touch-optimierte Benutzeroberfläche zu konvertieren.

* [Struktur der Touch-optimierten Benutzeroberfläche](/help/sites-developing/touch-ui-structure.md).

* [Anpassen von Konsolen in der Touch-optimierten Benutzeroberfläche](/help/sites-developing/customizing-consoles-touch.md) (einschließlich Beispiel-Code).

* [Anpassen der Seitenbearbeitung in der Touch-optimierten Benutzeroberfläche](/help/sites-developing/customizing-page-authoring-touch.md) (einschließlich Beispiel-Code).

* [Dokumentation zur Granite-Benutzeroberfläche](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html)
