---
title: Erstellen und Hinzufügen von Vorlagen und Komponenten
seo-title: Erstellen und Hinzufügen von Vorlagen und Komponenten
description: Folgen Sie dieser Seite, um mehr über das Erstellen und Hinzufügen von Vorlagen und Komponenten zu Ihrer App zu erfahren. Die Seite verwendet die Geometrixx Unlimited-App als App, die eine App-Mustervorlage und Seitenvorlagen enthält.
seo-description: Folgen Sie dieser Seite, um mehr über das Erstellen und Hinzufügen von Vorlagen und Komponenten zu Ihrer App zu erfahren. Die Seite verwendet die Geometrixx Unlimited-App als App, die eine App-Mustervorlage und Seitenvorlagen enthält.
uuid: 3a93017c-8094-413f-a01c-9b72025a2b20
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
discoiquuid: ec4ada04-e429-4ad4-a060-2dccac847cf0
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '1198'
ht-degree: 2%

---


# Erstellen und Hinzufügen von Vorlagen und Komponenten {#creating-and-adding-templates-and-components}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

AEM Mobile On-Demand bietet eine vollständig konfigurierte App-Vorlage, eine Artikelvorlage und Artikelkomponenten.

Die We.Unlimited App ist eine Beispielvorlage, die die Shell einer vollständig konfigurierbaren und überschaubaren AEM Mobile On-Demand-Anwendung darstellt.

Durch Auswahl dieser Beispielvorlage beim Erstellen einer neuen App erhalten Sie ein AEM Mobile-Feature-Rich-Dashboard.

![chlimage_1-70](assets/chlimage_1-70.png)

>[!NOTE]
>
>Informationen zum Verwalten von Anwendungs- und mobilen App-Inhalten über das AEM Mobile Apps Control Center finden Sie im [AEM Mobile Application Dashboard](/help/mobile/mobile-apps-ondemand-application-dashboard.md).

## Erstellen von App-Vorlagen {#creating-app-templates}

Eine App-Vorlage wird zum Erstellen einer neuen App verwendet und dient als Sammlung von Seitenvorlagen und Komponenten, die eine Grundlage oder Grundlage einer App darstellen. Die Vorlage stempelt einige grundlegende Eigenschaften heraus, um die App auf die richtige Weise zu leiten. Im Allgemeinen erstellt ein Kunde nicht zu viele Apps.

App-Vorlagen bieten eine einfache Möglichkeit, vorhandene Designs zu nutzen, die von Entwicklern erstellt wurden und für die Erstellung neuer Apps in AEM verwendet werden.

Wenn Sie eine neue App erstellen, die auf der Vorlage einer anderen App basiert, erhalten Sie eine App mit einem Startpunkt, der der App entspricht, aus der sie erstellt wurde.

Schritte zum Erstellen einer neuen App basierend auf einer App-Vorlage:

1. Navigieren Sie zum AEM Mobile-App-Katalog: *&lt;server-url>/aem/apps.html/content/mobileapps*
1. Wählen Sie **Erstellen** —> **App** wie unten gezeigt

Nachdem Sie eine App mit dieser Vorlage erstellt haben, können Sie Ihrer App Artikel, Banner und Sammlungen hinzufügen. Informationen zum erneuten Besuch der Erstellung von Artikeln, Bannern und Sammlungen finden Sie unter [Content-Management-Aktionen](/help/mobile/mobile-apps-ondemand-manage-content-ondemand.md).

>[!NOTE]
>
>Alternativ können Sie auch eine App-Beispielvorlage auswählen, z. B. **We.Unlimited**, die Ihnen von einem AEM Entwickler zur Verfügung gestellt wird. Wenn Sie diese Mustervorlage für Ihre App verwenden, erhalten Sie einige Beispielartikel und Sammlungen, an denen Sie arbeiten können. Sie haben die Möglichkeit, die Mustervorlagen und Komponenten zu verwenden, die vorhandenen anzupassen oder neue zu erstellen.

>[!CAUTION]
>
>Festlegen der Eigenschaft ***redirectTarget***
>
>Bei Verwendung einer der App-Vorlagen definiert der Entwickler den Inhalt der Anwendung. Der Entwickler muss jedoch wissen, wo die Anwendung in der jcr-Eigenschaft erstellt wird, und den Wert der ***redirectTarget***-Eigenschaft.
>
>Das ***redirectTarget*** wird als Teil des Erstellungsvorgangs der App berechnet und versucht, einen Pfad aufzulösen, wenn eine redirectTarget-Eigenschaft als Teil der App-Vorlage verfügbar ist und der Wert von redirectTarget als relativ definiert ist. Wenn der Vorgang zum Erstellen einer App einen relativen Wert für &quot;redirectTarget&quot;in der App-Vorlage findet, wird der Wert an den aufgelösten Speicherort angehängt, an dem die App erstellt wurde.
>
>Wenn beispielsweise eine App-Vorlage ein ***redirectTarget*** mit dem Wert &quot;*language-master/en*&quot;definiert und die App unter &quot;*/content/mobileapps/fooApp*&quot;erstellt wurde, lautet der endgültige Wert für redirectTarget nach Erstellung der App &quot;*&quot;.>/content/mobileapps/fooApp/language-masters/de*&quot;.


## Erstellen von Inhaltsvorlagen {#creating-content-templates}

Jeder Entitätstyp verfügt über zwei vordefinierte Vorlagen. Diese sind:

* **Standardvorlagen:für die Inhaltserstellung mit entsprechenden Standardeigenschaften/-struktur** verwenden
* **Importierte Vorlagen:** Wird zum Importieren von Inhalten aus AEM Mobile mit entsprechenden Standardeigenschaften/-struktur verwendet

### Artikelvorlagen {#article-templates}

Der Artikel &quot;Unbegrenzt&quot;ist eine Beispielvorlage, die ein typisches AEM Mobile On-Demand-Artikellayout darstellt.

1. Klicken Sie auf **+** in **Artikel verwalten**, um einen neuen Artikel zu erstellen. Sie können entweder einen **Unbeschränkten Artikel** oder einen **Rich Text-Artikel** auswählen. Die folgende Abbildung zeigt die Option, mit der Sie aus einer dieser beiden Artikelvorlagen wählen können.

1. Klicken Sie auf **Weiter**, um Artikelmetadaten wie Artikelname/Titel, Beschreibung, Autor, Zusammenfassung, Abteilung, Miniaturbild, Zugriff auf Artikel usw. zu definieren.
1. Klicken Sie auf **Weiter**, um die Anzeigeneigenschaften auszufüllen.
1. Klicken Sie auf **Weiter**, um das Artikelbild oder das Social Media-Bild einzugeben.
1. Klicken Sie auf **Weiter**, um einen Sammlungslink zu diesem neuen Artikel auszuwählen.
1. Klicken Sie auf **Weiter**, um die Details für Social Sharing einzugeben.
1. Klicken Sie auf **Erstellen**, um den Vorgang zum Erstellen eines Artikels mithilfe des Beispiels abzuschließen. Sie können entweder auf **Fertig** oder **Artikel bearbeiten** klicken, um die Eigenschaften dieses Artikels zu bearbeiten.

![chlimage_1-71](assets/chlimage_1-71.png)

### Hinzufügen von Komponenten zu Artikel {#adding-components-to-article}

Nach der Erstellung kann ein Autor den Inhalt eines Artikels bearbeiten, indem er Komponenten wie Text und Bilder hinzufügt. Artikel sind eine Erweiterung AEM Seitenvorlagen.

Wählen Sie einen Artikel aus, den Sie bearbeiten möchten, und klicken Sie auf **Bearbeiten**, um dem Artikel Komponenten hinzuzufügen.

![chlimage_1-72](assets/chlimage_1-72.png) ![chlimage_1-73](assets/chlimage_1-73.png)

Wählen Sie im linken Bereich &quot;**+**&quot;aus, um Komponenten zu Ihrem Artikel hinzuzufügen.

![chlimage_1-74](assets/chlimage_1-74.png)

### Erstellen von vordefinierten Vorlagen {#creating-out-of-the-box-templates}

Es gibt keine vordefinierten Artikelvorlagen. Es gibt jedoch eine Standardvorlage, die benutzerdefinierte Vorlagen erweitern sollten. Weitere Informationen finden Sie unter [Artikelvorlagenbeispiel für die Geometrixx Unlimited-App](http://localhost:4502/crx/de/index.jsp#/apps/geometrixx-unlimited-app/templates/article).

Zu den wichtigsten Eigenschaften, die über die normale AEM hinaus erforderlich sind, gehören:

***dps-resourceType=&quot;dps:Article&quot;***

Diese Eigenschaft stellt sicher, dass die AEM Seite als eine auf AEM Mobile ausgerichtete Artikelseite erkannt wird.

Gemäß AEM Vorlagen können Sie alle Standardeigenschaften oder untergeordneten Knoten der Vorlage ***jcr:content*** hinzufügen.

### Banner- und Sammlungsvorlagen {#banner-and-collection-templates}

>[!CAUTION]
>
>Banner und Sammlungen verfügen nicht über Inhalt, sodass ihre Erstellung keine benutzerdefinierten Vorlagen unterstützt.

## Erstellen und Hinzufügen von Komponenten {#creating-and-adding-components}

Komponenten verwenden Widgets und erlauben den Zugriff darauf. Diese werden zum Rendern des Inhalts verwendet.

Eine einfache Komponente ist im Code-Repository enthalten, dessen Quelle in AEM gefunden werden kann. Anschließend kann es auch lokal in CRXDE Lite geöffnet werden.

>[!NOTE]
>
>Für AEM Mobile sind derzeit keine vordefinierten Komponenten verfügbar.


Sie können Komponenten zu Ihrer Seite hinzufügen. Jede Komponente kann in einer AEM Mobile-App verwendet werden, wird jedoch bei Anwendung möglicherweise nicht ordnungsgemäß gerendert.

Benutzerdefinierte Komponenten können jedoch nicht ordnungsgemäß exportieren und nach AEM Mobile On-demand Services hochladen, ohne dass ein benutzerdefinierter Exportinhalt-Synchronisierungs-Handler zur Wiedergabe in AEM ausgeführt wird.

Nachdem die Komponente zusammen mit einigen anderen Bausteinkomponenten bereits in eine AEM Seite eingefügt wurde, können Sie der Seite eine weitere Komponente hinzufügen oder eine vorhandene bearbeiten.

**So fügen Sie der Seite eine weitere Komponente hinzu:**

1. Wählen Sie diese Seite aus und stellen Sie sicher, dass Sie sich im Bearbeitungsmodus befinden, über das Dropdown oben rechts in der Kopfzeile des Editors
1. Schalten Sie das Seitenbedienfeld mit dem Symbol ganz links in der Kopfzeile des Editors ein/aus
1. Wählen Sie die Registerkarte **Komponenten**
1. Ziehen Sie eine der verfügbaren Komponenten per Drag &amp; Drop auf die Seite

![chlimage_1-75](assets/chlimage_1-75.png)

**So bearbeiten Sie eine vorhandene Komponente:**

1. Wählen Sie diese Seite aus und stellen Sie sicher, dass Sie sich im Modus **Bearbeiten** befinden, und wählen Sie die Komponente aus.
1. Tippen Sie auf das Schraubenschlüsselsymbol, um die Komponente zu konfigurieren.

>[!NOTE]
>
>Sie können eine Komponente in AEM erstellen und dasselbe anpassen, indem Sie [Entwickeln mit CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) verwenden. Nachdem Sie die vorhandene Komponente Ihren Anforderungen entsprechend angepasst haben, können Sie sie Ihrer Seite mit der Option **Bearbeiten** unter **Artikel verwalten** hinzufügen, wie in der Abbildung oben dargestellt.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Best Practices für die Entwicklung von Vorlagen und Komponenten](/help/mobile/best-practices-aem-mobile.md) in AEM Mobile.

### Die nächsten Schritte {#the-next-steps}

* [Verwenden von Inhaltseigenschaften zum Exportieren von Inhalten](/help/mobile/on-demand-content-properties-exporting.md)
* [Mobil mit Inhaltssynchronisierung](/help/mobile/mobile-ondemand-contentsync.md)