---
title: Analyse mit externen Anbietern
description: Erfahren Sie, wie Sie Ihre eigene Instanz von generischen Analytics-Snippets konfigurieren, um eine neue Dienstkonfiguration zu definieren.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
exl-id: 9bf818f9-6e33-4557-b2e4-b0d4900f2a05
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 26%

---


# Analyse mit externen Anbietern {#analytics-with-external-providers}

Analysen können Ihnen wichtige und interessante Informationen darüber liefern, wie Ihre Website verwendet wird.

Verschiedene vordefinierte Konfigurationen stehen Ihnen zur Integration in den entsprechenden Dienst zur Verfügung, zum Beispiel:

* [Adobe Analytics](/help/sites-administering/adobeanalytics.md)
* [Adobe Target](/help/sites-administering/target.md)

Sie können auch Ihre eigene Instanz der **Allgemeine Analytics-Snippets** , um eine neue Dienstkonfiguration zu definieren.

Die Informationen werden dann von kleinen Codeausschnitten erfasst, die zu den Webseiten hinzugefügt werden. Beispiel:

>[!CAUTION]
>
>Skripte nicht einschließen in `script` Tags.

```
var _gaq = _gaq || [];
_gaq.push(['_setAccount', 'UA-XXXXX-X']);
_gaq.push(['_trackPageview']);

(function() {
    var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;
    ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'https://www') + '.google-analytics.com/ga.js';
    var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s);
})();
```

Diese Snippets ermöglichen die Erfassung von Daten und die Erstellung von Berichten. Die tatsächlichen erfassten Daten hängen vom Provider und dem tatsächlich verwendeten Codeausschnitt ab. Zu den Beispielstatistiken gehören:

* wie viele Besucher im Laufe der Zeit
* wie viele Seiten besucht wurden
* verwendete Suchbegriffe
* Landingpages

>[!CAUTION]
>
>Die Demosite &quot;Geometrixx-Outdoors&quot;ist so konfiguriert, dass die in den Seiteneigenschaften angegebenen Attribute an den HTML-Quellcode angehängt werden (direkt über dem `</html>` end -Tag) in der entsprechenden `js` Skript.
>
>Wenn Ihre `/apps` nicht von der standardmäßigen Seitenkomponente übernehmen ( `/libs/foundation/components/page`) müssen Sie (oder Ihre Entwickler) sicherstellen, dass die entsprechenden `js` -Skripte enthalten sind, z. B. durch `cq/cloudserviceconfigs/components/servicescomponents`oder einen ähnlichen Mechanismus verwenden.
>
>Ohne diese Funktion funktioniert keiner der Dienste (generisch, Analytics, Target usw.).

## Erstellen eines Dienstes mit einem generischen Snippet {#creating-a-new-service-with-a-generic-snippet}

Für die Grundkonfiguration:

1. Öffnen Sie die **Tools-Konsole**.
1. Erweitern Sie im linken Bereich die **Cloud Service-Konfigurationen**.
1. Doppelklicken **Generisches Analytics-Snippet** , um die Seite zu öffnen:

   ![Generisches Analyse-Snippet](assets/analytics_genericoverview.png)

1. Klicken Sie auf + , um eine neue Konfiguration über das Dialogfeld hinzuzufügen. Weisen Sie mindestens einen Namen zu, z. B. Google Analytics:

   ![Erstellen einer Konfiguration](assets/analytics_addconfig.png)

1. Klicks **Erstellen**, wird das Dialogfeld &quot;Snippet&quot;sofort geöffnet. Fügen Sie das entsprechende JavaScript-Snippet in das Feld ein:

   ![Bearbeiten der Komponente](assets/analytics_snippet.png)

1. Klicken Sie zum Speichern auf **OK**.

## Verwenden des neuen Dienstes auf Seiten {#using-your-new-service-on-pages}

Nachdem Sie die Dienstkonfiguration erstellt haben, müssen Sie jetzt die erforderlichen Seiten konfigurieren, um sie zu verwenden:

1. Navigieren Sie zu der Seite.
1. Öffnen Sie die **Seiteneigenschaften** im Sidekick und wählen Sie dann die Registerkarte **Cloud-Services** aus.
1. Klicks **Dienst hinzufügen** und wählen Sie dann den gewünschten Dienst aus. Beispiel: die **Generisches Analytics-Snippet**:

   ![Hinzufügen eines Cloud-Service](assets/analytics_selectservice.png)

1. Klicken Sie zum Speichern auf **OK**.
1. Sie kehren zum **Cloud Service** Registerkarte. Der Dienst **Generisches Analyse-Snippet** wird nun mit der Meldung `Configuration reference missing` angezeigt. Verwenden Sie die Dropdown-Liste, um Ihre spezifische Dienstinstanz auszuwählen. Beispiel: Google-analytics:

   ![Hinzufügen der Cloud Service-Konfiguration](assets/analytics_selectspecificservice.png)

1. Klicken Sie zum Speichern auf **OK**.

   Das Snippet kann jetzt angezeigt werden, wenn Sie die Seitenquelle für die Seite anzeigen.

   Nach Ablauf einer gewissen Zeit können Sie die gesammelten Statistiken anzeigen.

   >[!NOTE]
   >
   >Wenn die Konfiguration an eine Seite mit untergeordneten Seiten angehängt wird, wird der Dienst von diesen ebenfalls übernommen.
