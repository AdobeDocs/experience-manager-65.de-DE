---
title: ContextHub-Diagnosen
seo-title: ContextHub Diagnostics
description: ContextHub bietet eine Diagnoseseite, auf der Sie einen Überblick über das ContextHub-Framework erhalten.
seo-description: ContextHub provides a diagnostics page where you can see an overview of the ContextHub framework
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
exl-id: b833c28b-76c6-42a2-b690-3e81ddf91bc2
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 58%

---

# ContextHub-Diagnosen {#contexthub-diagnostics}

ContextHub bietet eine Diagnoseseite, auf der Sie einen Überblick über das ContextHub-Framework erhalten. Um die Seite zu öffnen, gehen Sie zur `contexthub.diagnostics.html`-Seite Ihrer AEM-Autorenrinstanz, z. B.:

`http://<host>:<port>/conf/<tenant>/settings/cloudsettings/default/contexthub.diagnostics.html`

Auf der Seite &quot;ContextHub-Diagnose&quot;finden Sie Informationen zu den erstellten Stores und Benutzeroberflächenmodulen, den geladenen Client-Bibliotheksordnern und Links zu nützlichen Seiten.

>[!NOTE]
>
>Damit Diagnoseinformationen zurückgegeben werden können, muss der Debug-Modus aktiviert sein, da andernfalls die Diagnoseseite leer ist. Siehe [dieses Dokuments](ch-configuring.md#debugging-contexthub) für Details zum Aktivieren des Debug-Modus.

>[!NOTE]
>
>Für ContextHub-Konfigurationen, die sich noch unter ihren alten Pfaden befinden, befindet sich die Diagnoseseite unter `http://<host>:<port>/libs/settings/cloudsettings/legacy/contexthub.diagnostics.html`.

## Stores {#stores}

Der Abschnitt „Stores“ listet alle ContextHub-Stores auf, die konfiguriert wurden. Jedes Element in der Liste besteht aus folgenden Informationen:

* **Title:** Der [Store-Typ](/help/sites-developing/ch-samplestores.md), auf dem der Store basiert.
* **path:** Der Pfad zum Repository-Knoten, der die Konfiguration enthält.
* **resourceType:** Der Pfad des Repository-Knotens, in dem der Speichertyp definiert ist.
* **clientlibs:** Die Kategorien der geladenen Client-Bibliotheken, die den Store-Typ implementieren.

## Modules {#modules}

Der Abschnitt „Modules“ listet alle ContextHub Benutzeroberflächenmodule auf, die konfiguriert wurden. Jedes Element in der Liste besteht aus folgenden Informationen:

* **Title:** Der [Benutzeroberflächenmodultyp](/help/sites-developing/ch-samplemodules.md), auf dem das Benutzeroberflächenmodul basiert.
* **path:** Der Pfad zum Repository-Knoten, der die Konfiguration enthält.
* **resourceType:** Der Pfad des Repository-Knotens, in dem der UI-Modultyp definiert ist.
* **clientlibs:** Die Kategorien der geladenen Client-Bibliotheken, die den UI-Modultyp implementieren.

## Clientlibs {#clientlibs}

Der Abschnitt „Clientlibs“ listet alle Ordner der Client-Bibliothek auf, die ContextHub geladen hat. Die Client-Bibliotheken werden kategorisiert:

* **kernel.js:** Client-Bibliotheken, die das ContextHub-Framework, die Segment-Engine und Storetypen implementieren.
* **ui.js:** Client-Bibliotheken, die die ContextHub-Benutzeroberfläche und Benutzeroberflächenmodultypen implementieren.
* **style.css:** CSS-Dateien, die aus Client-Bibliotheken geladen werden.

## URLs {#urls}

Der Abschnitt „URLs“ enthält Links zu ContextHub-Features:

* **Konfigurationseditor:** Öffnet die [ContextHub-Konfigurationsseite](ch-configuring.md), wo Sie Stores, Benutzeroberflächenmodi und Benutzeroberflächenmodule konfigurieren können.

* **Konfiguration von ContextHub-Modulen:** Öffnet die Datei /etc/cloudsettings/default/contexthub.config.kernel.js , die die JavaScript-Objektdarstellung der ContextHub-Store-Konfigurationen enthält.
* **Konfiguration der ContextHub-Benutzeroberfläche:** Öffnet die Datei /etc/cloudsettings/default/contexthub.config.ui.js , die die JavaScript-Objektdarstellung der Konfigurationen des ContextHub-UI-Modus enthält.
* **kernel.js:** Öffnet die Datei /etc/cloudsettings/default/contexthub.kernel.js, die den Quell-Code der Client-Bibliotheken enthält, welche das ContextHub-Framework, die Segment-Engine und die Speichertypen implementieren.
* **ui.js:** Öffnet die Datei /etc/cloudsettings/default/ contexthub.ui.js, die den Quell-Code der Client-Bibliotheken enthält, welche die ContextHub-Benutzeroberfläche und Benutzeroberflächenmodultypen implementieren.
* **style.css:** Öffnet die Datei /etc/cloudsettings/default/contexthub.styles.css, die die CSS-Stile für die ContextHub-Benutzeroberfläche und Benutzeroberflächenmodule enthält.
