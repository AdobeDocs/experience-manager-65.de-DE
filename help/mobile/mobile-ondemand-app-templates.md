---
title: Erstellen und Hinzufügen von Vorlagen und Komponenten
description: Auf dieser Seite erfahren Sie mehr über das Erstellen und Hinzufügen von Vorlagen und Komponenten zu Ihrer App. Die Seite verwendet die Geometrixx Unlimited-App als die App, die eine Beispiel-App-Vorlage und Seitenvorlagen enthält.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
exl-id: 5f050baa-fe10-4acc-ad32-de20793edc13
solution: Experience Manager
feature: Mobile
role: User
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '1130'
ht-degree: 1%

---

# Erstellen und Hinzufügen von Vorlagen und Komponenten {#creating-and-adding-templates-and-components}

{{ue-over-mobile}}

AEM Mobile On-Demand bietet eine vollständig konfigurierte App-Vorlage, eine Artikelvorlage und Artikelkomponenten.

Die We.Unlimited App ist eine Beispielvorlage, die die Shell einer vollständig konfigurierbaren und verwaltbaren AEM Mobile On-Demand-Anwendung darstellt.

Durch Auswahl dieser Beispielvorlage beim Erstellen einer App wird ein AEM Mobile-Dashboard mit umfangreichen Funktionen bereitgestellt.

![chlimage_1-70](assets/chlimage_1-70.png)

>[!NOTE]
>
>Informationen zum Verwalten Ihrer Mobile App und der Inhalte Ihrer Mobile App über das AEM Mobile Apps Control Center finden Sie unter [Dashboard der AEM Mobile App](/help/mobile/mobile-apps-ondemand-application-dashboard.md).

## Erstellen von App-Vorlagen {#creating-app-templates}

Eine App-Vorlage wird verwendet, um eine App zu erstellen, und dient als Sammlung von Seitenvorlagen und Komponenten, die eine Grundlinie oder Grundlage einer App darstellen. Die Vorlage streicht einige grundlegende Eigenschaften, um die App auf die entsprechende Weise zu führen. Im Allgemeinen würde ein Kunde nicht zu viele Apps insgesamt erstellen.

App-Vorlagen bieten eine einfache Möglichkeit, vorhandene Designs zu verwenden, die von Entwicklerinnen und Entwicklern erstellt wurden und für die Erstellung neuer Apps in AEM verwendet werden.

Wenn Sie eine App basierend auf der Vorlage einer anderen App erstellen, erhalten Sie eine App, deren Startpunkt repräsentativ für die App ist, aus der sie erstellt wurde.

Schritte zum Erstellen einer App basierend auf einer App-Vorlage:

1. Navigieren Sie zum AEM Mobile-App-Katalog: *&lt;server-url>/aem/apps.html/content/mobileapps*
1. Wählen Sie **Erstellen** > **Programm** wie unten dargestellt aus

Nachdem Sie eine App mit dieser Vorlage erstellt haben, können Sie Ihrer App Artikel, Banner und Sammlungen hinzufügen. Weitere Informationen zum erneuten Aufrufen, Erstellen von Artikeln, Bannern und Sammlungen finden Sie unter [Content-Management-Aktionen](/help/mobile/mobile-apps-ondemand-manage-content-ondemand.md).

>[!NOTE]
>
>Alternativ können Sie auch eine Beispiel-App-Vorlage auswählen, z. B. **We.Unlimited**-App, die Ihnen von einem AEM-Entwickler zur Verfügung gestellt wird. Wenn Sie diese Beispielvorlage für Ihre App verwenden, erhalten Sie einige Beispielartikel und Sammlungen, an denen Sie arbeiten können. Sie haben die Möglichkeit, die Beispielvorlagen und -komponenten zu verwenden, die vorhandenen Vorlagen anzupassen oder neue für Ihre App zu erstellen.

>[!CAUTION]
>
>Festlegen ***Eigenschaft*** redirectTarget“
>
>Bei Verwendung einer der App-Vorlagen definiert der Entwickler den Inhalt des Programms. Der Entwickler muss jedoch wissen, wo die Anwendung im JCR erstellt wird, und den Wert der Eigenschaft ***redirectTarget*** kennen.
>
>Das ***redirectTarget*** wird im Rahmen des Vorgangs zum Erstellen einer App berechnet und versucht, einen Pfad aufzulösen, wenn eine redirectTarget-Eigenschaft als Teil der App-Vorlage verfügbar ist und der Wert des redirectTarget als relativ definiert ist. Wenn der Prozess „App erstellen“ einen relativen Wert für „redirectTarget“ in der App-Vorlage findet, wird der Wert an den aufgelösten Speicherort angehängt, an dem die App erstellt wurde.
>
>Wenn beispielsweise eine App-Vorlage ein ***redirectTarget*** mit dem Wert &quot;*language-masters/en*&quot; definiert und die App in &quot;*/content/mobileapps/fooApp*&quot; erstellt wurde, lautet der endgültige Wert für redirectTarget nach der Erstellung der App &quot;*/content/mobileapps/fooApp/language-masters/en*&quot;.
>

## Erstellen von Inhaltsvorlagen {#creating-content-templates}

Jeder Entitätstyp verfügt über zwei vordefinierte Vorlagen. Diese sind:

* **Standardvorlagen:** für die Inhaltserstellung mit entsprechenden Standardeigenschaften/-struktur verwendet
* **Importierte Vorlagen:** zum Importieren von Inhalten aus AEM Mobile mit entsprechenden Standardeigenschaften/-struktur verwendet

### Artikelvorlagen {#article-templates}

Der Artikel Unbegrenzt ist eine Beispielvorlage für ein typisches AEM Mobile On-Demand-Artikellayout.

1. Wählen **in „Artikel verwalten** die Option **+** aus, um einen Artikel zu erstellen. Sie können entweder einen **unbegrenzten Artikel** oder einen **Rich-Text-Artikel** auswählen. Die folgende Abbildung zeigt die Option, mit der Sie aus einer dieser beiden Artikelvorlagen auswählen können.

1. Klicken Sie **Weiter**, um Artikelmetadaten wie Artikelnamen/Titel, Beschreibung, Autor, Zusammenfassung, Abteilung, Miniaturbild, Artikelzugriff usw. zu definieren.
1. Klicken Sie **Weiter**, um die Eigenschaften der Anzeige auszufüllen.
1. Klicken Sie **Weiter**, um das Artikelbild oder das Social-Media-Bild einzugeben
1. Klicken Sie **Weiter**, um einen Sammlungslink für diesen neuen Artikel auszuwählen.
1. Klicken Sie **Weiter**, um die Details für die Freigabe in sozialen Netzwerken einzugeben.
1. Klicken Sie **Erstellen**, um die Erstellung eines Artikels anhand eines Beispiels abzuschließen. Klicken Sie entweder auf **Fertig** oder **Artikel bearbeiten** um die Eigenschaften dieses Artikels zu bearbeiten.

![chlimage_1-71](assets/chlimage_1-71.png)

### Hinzufügen von Komponenten zu Artikeln {#adding-components-to-article}

Nach der Erstellung kann ein Autor den Inhalt eines Artikels bearbeiten, indem er Komponenten wie Text und Bilder hinzufügt. Artikel sind eine Erweiterung von AEM-Seitenvorlagen.

Wählen Sie den zu bearbeitenden Artikel aus und klicken Sie dann auf **Bearbeiten**, um dem Artikel Komponenten hinzuzufügen.

![chlimage_1-72](assets/chlimage_1-72.png) ![chlimage_1-73](assets/chlimage_1-73.png)

Wählen Sie &#39;**+**&#39; im linken Bereich, um Komponenten zu Ihrem Artikel hinzuzufügen.

![chlimage_1-74](assets/chlimage_1-74.png)

### Erstellen von nativen Vorlagen {#creating-out-of-the-box-templates}

Es gibt keine vordefinierten Artikelvorlagen. Es gibt jedoch eine Standardvorlage, die von benutzerdefinierten Vorlagen erweitert werden sollte. Weitere Informationen finden Sie unter Beispiel für eine Artikelvorlage [&#x200B; Geometrixx Unlimited-App](http://localhost:4502/crx/de/index.jsp#/apps/geometrixx-unlimited-app/templates/article).

Zu den wichtigsten Eigenschaften, die über die normalen Eigenschaften von AEM-Vorlagen hinausgehen, gehören:

***dps-resourceType=„dps:Article“***

Diese Eigenschaft stellt sicher, dass die AEM-Seite als AEM Mobile-Zielartikelseite erkannt wird.

Gemäß den AEM-Vorlagen können Sie dem Vorlagenknoten (jcr:content ***alle Standardeigenschaften oder untergeordneten*** hinzufügen.

### Banner- und Sammlungsvorlagen {#banner-and-collection-templates}

>[!CAUTION]
>
>Banner und Sammlungen enthalten keinen Inhalt, sodass ihre Erstellung benutzerdefinierte Vorlagen nicht unterstützt.

## Erstellen und Hinzufügen von Komponenten {#creating-and-adding-components}

Komponenten verwenden Widgets und ermöglichen den Zugriff darauf. Diese werden zum Rendern des Inhalts verwendet.

Im Code-Repository ist eine einfache Komponente enthalten, deren Quelle Sie in AEM finden. Anschließend kann es auch lokal in CRXDE Lite geöffnet werden.

>[!NOTE]
>
>Es gibt derzeit keine vordefinierten Komponenten, die für AEM Mobile bereitgestellt werden.
>

Sie können Komponenten zu Ihrer Seite hinzufügen. Jede Komponente kann in einer AEM Mobile-App verwendet werden, wird aber, wenn sie angewendet wird, möglicherweise nicht richtig gerendert.

Benutzerdefinierte Komponenten können jedoch ohne einen benutzerdefinierten Synchronisierungs-Handler für Exportinhalte, der in AEM gerendert wird, möglicherweise nicht korrekt exportiert und in AEM Mobile On-demand Services hochgeladen werden.

Sobald die Komponente zusammen mit einigen anderen Bausteinkomponenten bereits in einer AEM-Seite enthalten ist, können Sie der Seite eine weitere Komponente hinzufügen oder eine vorhandene bearbeiten.

**So fügen Sie der Seite eine weitere Komponente hinzu:**

1. Wählen Sie diese Seite aus und stellen Sie sicher, dass Sie sich im Bearbeitungsmodus befinden, indem Sie das Dropdown-Menü oben rechts in der Kopfzeile des Editors aufrufen
1. Blenden Sie den Seitenbereich mithilfe des Symbols ganz links in der Kopfzeile des Editors ein oder aus.
1. Wählen Sie die **Komponenten** aus
1. Ziehen Sie eine der verfügbaren Komponenten auf die Seite

![chlimage_1-75](assets/chlimage_1-75.png)

**So bearbeiten Sie eine vorhandene Komponente:**

1. Wählen Sie diese Seite aus und stellen Sie sicher, dass Sie sich im **Bearbeiten**-Modus befinden, und wählen Sie die Komponente aus
1. Wählen Sie das Schraubenschlüssel -Symbol aus, um die Komponente zu konfigurieren

>[!NOTE]
>
>Sie können eine Komponente in AEM erstellen und diese mit „Entwickeln [&#x200B; CRXDE Lite&quot; &#x200B;](/help/sites-developing/developing-with-crxde-lite.md). Nachdem Sie die vorhandene Komponente als Ihre Anforderungen angepasst haben, können Sie sie Ihrer Seite hinzufügen, indem Sie die Option **Bearbeiten** unter **Artikel verwalten** verwenden, wie in der folgenden Abbildung dargestellt.

>[!NOTE]
>
>Siehe [Best Practices für die Entwicklung von Vorlagen und Komponenten](/help/mobile/best-practices-aem-mobile.md) in AEM Mobile.

### Die nächsten Schritte {#the-next-steps}

* [Exportieren von Inhalten mit Inhaltseigenschaften](/help/mobile/on-demand-content-properties-exporting.md)
* [Mobile mit Inhaltssynchronisierung](/help/mobile/mobile-ondemand-contentsync.md)
