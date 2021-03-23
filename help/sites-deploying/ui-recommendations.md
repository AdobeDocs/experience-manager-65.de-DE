---
title: Empfehlungen für Kunden zur Benutzeroberfläche
seo-title: Empfehlungen für Kunden zur Benutzeroberfläche
description: Eine Liste mit Empfehlungen zur klassischen und Touch-optimierten Benutzeroberfläche.
seo-description: Eine Liste mit Empfehlungen zur klassischen und Touch-optimierten Benutzeroberfläche.
uuid: 9ec2c9de-a79e-4f2c-a90f-b38ba9553e07
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 8f06d4b6-7d30-4ebc-9c6a-3bb8607a9be8
docset: aem65
translation-type: tm+mt
source-git-commit: 7035c19a109ff67655ee0419aa37d1723e2189cc
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 93%

---


# Empfehlungen für Kunden zur Benutzeroberfläche{#user-interface-recommendations-for-customers}

Adobe Experience Manager verfügt über zwei Benutzeroberflächen- Die einheitliche Experience-Cloud Benutzeroberfläche (auch als Touch-optimierte Benutzeroberfläche bekannt) und die klassische Benutzeroberfläche.

Dieses Dokument soll Kunden bei der Auswahl der richtigen Benutzeroberfläche für ihre Anforderungen helfen.

Verwendete Begriffe:

* **Benutzeroberfläche (oder Standardbenutzeroberfläche)** Eine moderne Benutzeroberfläche, die in Version 5.6.0 als Technologievorschau eingeführt und in nachfolgenden Versionen erweitert wurde. Sie basiert auf dem einheitlichen Benutzererlebnis für Adobe Experience Cloud, das früher als Touch-optimierte Benutzeroberfläche oder Touch-Benutzeroberfläche bezeichnet wurde.

* **Klassische Benutzeroberfläche** Eine auf der ExtJS-Technologie basierende Benutzeroberfläche, die 2008 zusammen mit CQ 5.1 eingeführt wurde.

* **Seiten-Administrator** Funktionen zum Verwalten der Seitenhierarchie (Verschieben, Aktivieren, verwaltete Verweise) und Erstellen von neuen Seiten.

* **Seitenbearbeitung** Funktionen zum Hinzufügen von Inhalten zu einer Seite bzw. zum Bearbeiten des Seiteninhalts.

* **DAM-/Asset-Admin** Funktionen zum Verwalten digitaler Assets (einschließlich Bildern, Video, Dokumenten, Downloads).

* **ContextHub** Funktionen zum Aggregieren von Informationen über den Besucher und zum Verwenden derselben für verschiedene Zwecke. Stellt eine Benutzeroberfläche zum Simulieren von Personen bereit, die die Site besuchen. Ab AEM 6.2 ersetzt ContextHub die bisherige Technologie ClientContext.

## Allgemein {#general}

In den vergangenen Jahren hat Adobe alle Adobe Experience Cloud-Lösungen um eine einheitlichen Benutzeroberfläche erweitert. Benutzer der Experience Cloud-Lösungen profitieren so von einem konsistenten Erlebnis mit einem einheitlichen Verwendungsmuster für die Anwendungen. In jeder neuen Version wurde die Adobe-Benutzeroberfläche auf der Grundlage von Kundenanregungen zu den verschiedenen Lösungen verbessert.

Die ursprüngliche Benutzeroberfläche von Adobe Experience Manager (zuvor als CQ5 bekannt), die 2008 eingeführt und von Kunden mit den Versionen 5.0–5.6.1 verwendet wurde, ist in AEM 6.5 verfügbar. So wird sichergestellt, dass Kunden eine Aktualisierung auf Version 6.5 durchführen und von einer aktualisierten Plattform mit neuen Funktionen profitieren können, während sie gleichzeitig dieselbe Benutzeroberfläche weiterverwenden.

Adobe empfiehlt Kunden, den Umstieg auf die neue Benutzeroberfläche für 2018/19 zu planen. Dies ist entweder im Rahmen einer Aktualisierung auf Version 6.5 möglich oder im Rahmen separater Projekte nach der Aktualisierung, bei der die notwendige Anpassung des Dialogfelds und die Änderung der Dialogkomponenten vorgenommen werden müssen.

Die klassische Benutzeroberfläche ist seit AEM 6.4 veraltet und Adobe hat nicht die Absicht, weitere Verbesserungen an der klassischen Benutzeroberfläche vorzunehmen. Beachten Sie, dass die klassische Benutzeroberfläche zwar veraltet ist, aber weiterhin umfassend unterstützt wird.

### Richtlinien und Empfehlungen {#rules-and-recommendations}

Nachfolgend finden Sie eine Liste mit Empfehlungen der Produktmanagement-Abteilung für Adobe Experience Manager 6.5:

<table>
 <tbody>
  <tr>
   <th>Mein Projekt...</th>
   <th>Empfehlungen</th>
  </tr>
  <tr>
   <td>Beginnt gerade mit der Verwendung von Adobe Experience Manager.</td>
   <td>Standardbenutzeroberfläche verwenden.</td>
  </tr>
  <tr>
   <td><p>Verwendet seit einiger Zeit AEM.</p> <p>Hat die vorkonfigurierte Produktbenutzeroberfläche verwendet und benutzerdefinierte Komponenten für die Sites entwickelt.<br /> </p> </td>
   <td>
    <ol>
     <li>Aktualisierung auf 6.5.</li>
     <li>Standardbenutzeroberfläche für Site-Verwaltung, Assets, usw. usw.<br /> </li>
     <li>Aktion „Seite bearbeiten“ konfigurieren, um den Seiteneditor der klassischen Benutzeroberfläche zu öffnen. Siehe <a href="#selecting-your-ui">Festlegen der Benutzeroberfläche</a>.</li>
    </ol> <p>Anschließend:</p>
    <ol>
     <li>Komponentendialoge aktualisieren, um das Coral 3-Dialogformat zu verwenden. Adobe empfiehlt, die Komponenten mit den <a href="/help/sites-developing/modernization-tools.md">AEM Moderationstools</a> zu aktualisieren.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Es wurde eine Website erstellt, die die ClientContext-Komponente mit Integrationen verwendet.<br /> </td>
   <td>
    <ol>
     <li>Aktualisierung auf 6.5.</li>
     <li>Standardbenutzeroberfläche für Site-Verwaltung, Assets, usw. usw.</li>
     <li>Aktion „Seite bearbeiten“ konfigurieren, um den Seiteneditor der klassischen Benutzeroberfläche zu öffnen. Siehe <a href="#selecting-your-ui">Festlegen der Benutzeroberfläche</a>.</li>
    </ol> <p>Anschließend:</p>
    <ol>
     <li>Komponentendialoge aktualisieren, um das Coral 3-Dialogformat zu verwenden. Adobe empfiehlt, die Komponenten mit den <a href="/help/sites-developing/modernization-tools.md">AEM Moderationstools</a> zu aktualisieren.</li>
     <li>Konfigurieren Sie ContextHub (ersetzt ClientContext) und aktualisieren Sie die Seitenvorlagen für die Anwendung von ContextHub. Hinweis: ContextHub verfügt über einen Kompatibilitätsmodus, mit dem benutzerdefinierter ClientContext-Speicher geladen werden kann.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><p>Verwendet CQ/AEM seit vielen Jahren.</p> <p>Hat die Produktbenutzeroberfläche (z. B. Website-Verwaltung) erweitert und Komponenten mit umfangreichen Dialogfeldern zum Bearbeiten erstellt.</p> </td>
   <td><p>Aktualisierung auf 6.5 durchführen und die klassische Benutzeroberfläche als Standardbenutzeroberfläche zur Seitenbearbeitung für alle Benutzer konfigurieren. Siehe <a href="#selecting-your-ui">Festlegen der Benutzeroberfläche</a>.</p> <p>Starten Sie anschließend ein Projekt, um die Änderungen zu übernehmen und die Komponentendialogfelder im Coral 3-Format zu optimieren. Siehe <a href="#resources-to-help">Hilfe-Ressourcen</a>.<br /> </p> </td>
  </tr>
 </tbody>
</table>

### Häufig gestellte Fragen (FAQ){#faq}

Weitere Einzelheiten finden Sie im Knowledge Base-Artikel [Seitenbearbeitung mit der Touch-optimierten Benutzeroberfläche – Häufig gestellte Fragen (FAQ)](https://helpx.adobe.com/experience-manager/kb/index/touchui_faq.html), darunter Informationen zur geplanten Entfernung der klassischen Benutzeroberfläche.

### Festlegen der Benutzeroberfläche {#selecting-your-ui}

Weitere Informationen zur erforderlichen Konfiguration Ihres Systems finden Sie unter [Festlegen der Benutzeroberfläche](/help/sites-authoring/select-ui.md).

### Status der Funktionen der Touch-fähigen Benutzeroberfläche {#touch-enabled-ui-status}

Einzelheiten zu den Verbesserungen an der Touch-optimierten Benutzeroberfläche in AEM 6.5 finden Sie in den Versionshinweisen unter [Neue Funktionen](/help/release-notes/release-notes.md#what-s-new).

Einen vollständigen Überblick finden Sie auf der Seite [Status der Funktionen der Touch-optimierten Benutzeroberfläche](/help/release-notes/touch-ui-features-status.md).

### Hilfe-Ressourcen {#resources-to-help}

Für Hintergrundinformationen über den grundsätzlichen Umgang:

* [Bearbeiten von Seiten (Authoring)](/help/sites-authoring/page-authoring.md)

Für detaillierte Entwicklungsinformationen:

* [Design der Touch-optimierten Benutzeroberfläche](/help/sites-developing/touch-ui-concepts.md).
* Verwenden Sie die [AEM Moderationstools](/help/sites-developing/modernization-tools.md), um Dialogfelder zum Bearbeiten von Komponenten aus der klassischen Benutzeroberfläche in die touchfähige Benutzeroberfläche zu konvertieren.

* [Struktur der Touch-optimierten Benutzeroberfläche](/help/sites-developing/touch-ui-structure.md).

* [Anpassen von Konsolen in der Touch-optimierten Benutzeroberfläche](/help/sites-developing/customizing-consoles-touch.md) (einschließlich Beispielcode).

* [Anpassen der Seitenbearbeitung in der Touch-optimierten Benutzeroberfläche](/help/sites-developing/customizing-page-authoring-touch.md) (einschließlich Beispielcode).

* [AEM GEM Session zur Anpassung in der Touch-optimierten Benutzeroberfläche](https://docs.adobe.com/content/ddc/en/gems/user-interface-customization-for-aem-6.html)
* [Dokumentation zur Granite-Benutzeroberfläche](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html)

