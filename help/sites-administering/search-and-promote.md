---
title: Integration mit Adobe Search&Promote
description: Erfahren Sie, wie Sie eine Integration mit Adobe Search&Promote vornehmen können.
uuid: 7e9384d9-9e4f-4e00-a1c9-35547de6ceb8
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: aca444f6-418a-4c01-ae19-663b4e04fab9
docset: aem65
exl-id: 15f45978-a983-49a0-91cf-c7610fc37eef
source-git-commit: f4b7566abfa0a8dbb490baa0e849de6c355a3f06
workflow-type: tm+mt
source-wordcount: '882'
ht-degree: 33%

---

# Integration mit Adobe Search&amp;Promote{#integrating-with-adobe-search-promote}

Führen Sie zum Abrufen des Dienstes Adobe Search&amp;Promote von unserer Website die folgenden Aufgaben durch:

1. Geben Sie die URL der Cloud an.
1. Konfigurieren Sie die Verbindung mit dem Search&amp;Promote-Dienst.
1. Fügen Sie dem Sidekick Search&amp;Promote-Komponenten hinzu.
1. Verwenden Sie die Komponenten für die Bearbeitung des Inhalts. (Siehe [Hinzufügen von Search&amp;Promote-Funktionen zu einer Webseite](/help/sites-authoring/search-and-promote.md).)
1. Fügen Sie Ihren Seiten Banner hinzu. Bannerbilder reagieren auf Search&amp;Promote-Daten.
1. Generieren Sie eine Sitemap für den Search&amp;Promote-Dienst.

>[!NOTE]
>
>Wenn Sie Search&amp;Promote mit einer benutzerdefinierten Proxy-Konfiguration verwenden, müssen Sie beide HTTP-Client-Proxy-Konfigurationen konfigurieren, da einige Funktionen von Adobe Experience Manager die 3.x-APIs und andere die 4.x-APIs verwenden:
>
>* 3.x wird mit [https://localhost:4502/system/console/configMgr/com.day.commons.httpclient](https://localhost:4502/system/console/configMgr/com.day.commons.httpclient) konfiguriert.
>* 4.x ist mit [https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator) konfiguriert.

>



## Ändern der Search&amp;Promote-Dienst-URL {#changing-the-search-promote-service-url}

Die Standard-URL, die für den Search&amp;Promote-Dienst konfiguriert ist, lautet `https://searchandpromote.omniture.com/px/`. Verwenden Sie zur Verwendung eines anderen Diensts die OSGi-Konsole, um eine andere URL anzugeben.

1. Öffnen Sie die OSGi-Konsole und wählen Sie die Registerkarte **[!UICONTROL Konfiguration]** aus. ([https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr))
1. Wählen Sie das Element Day CQ Search&amp;Promote Configuration aus.
1. Geben Sie die URL in das Feld &quot;Remote Server URI&quot;ein und wählen Sie **[!UICONTROL Save]**.

## Verbindung zu Search&amp;Promote konfigurieren {#configuring-the-connection-to-search-promote}

Konfigurieren Sie eine oder mehrere Verbindungen mit Search&amp;Promote, sodass Ihre Webseiten mit dem Dienst interagieren können. Für die Verbindung benötigen Sie die Mitgliedsidentifikations- und Kontonummer Ihres Search&amp;Promote-Kontos.

1. Navigieren Sie in Experience Manager zu **[!UICONTROL Tools]** > **[!UICONTROL Bereitstellung]** > wählen Sie **[!UICONTROL Cloud Services]** aus.

   Wenn Sie sich auf einem lokalen Computer befinden, sieht die URL des Dashboards wie folgt aus:

   [https://localhost:4502/libs/cq/core/content/tools/cloudservices.html](https://localhost:4502/libs/cq/core/content/tools/cloudservices.html)

1. Wählen Sie auf der Seite &quot;Cloud Services&quot;den Link Adobe Search&amp;Promote oder das Symbol Search&amp;Promote aus.

1. Wenn Sie Adobe Search&amp;Promote zum ersten Mal konfigurieren, wählen Sie **[!UICONTROL Jetzt konfigurieren]** aus, um den Bereich Konfiguration erstellen zu öffnen.

   Um mehr über Search&amp;Promote zu erfahren, wählen Sie **[!UICONTROL Weitere Informationen]** aus.

   ![](assets/chlimage_1-59.png)

1. Geben Sie einen **[!UICONTROL Titel]** ein, der für Seitenautoren erkennbar ist, und geben Sie einen eindeutigen **[!UICONTROL Namen]** ein.
1. Wählen Sie **[!UICONTROL Erstellen]**.

   Darüber hinaus wird die neu erstellte Konfiguration unter **Verfügbare Konfigurationen** im **Cloud-Services-Dashboard** des Adobe Search&amp;Promote-Listenelements angezeigt.

   ![](assets/chlimage_1-60.png)

1. Fügen Sie den Feldern im Dialogfeld **[!UICONTROL Komponente bearbeiten]** Folgendes hinzu.

   * **Mitglieds-ID**
   * **Kontonummer**

   >[!NOTE]
   >
   >Um diese Informationen zu erhalten, müssen Sie sich zunächst bei ****
   >
   >[https://searchandpromote.omniture.com/center/](https://searchandpromote.omniture.com/center/)
   >
   >
   >mithilfe Ihrer gültigen Seach&amp;Promote-Zugriffsberechtigung (E-Mail/Kennwort) anmelden.
   >Dann müssen Sie Ihre URL in der Adressleiste Ihres Browsers betrachten, die ungefähr so aussehen sollte:
   >[](https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY)
   >
   >[https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY](https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY)
   >
   >**Dabei gilt:**
   >
   >    * **** XXXXXXXXXX entspricht Ihrer ** Mitglieds-ID**
   >    * **** spYYYYYYYYentspricht Ihrer  **Kontonummer**


1. Wählen Sie **[!UICONTROL Mit Search&amp;Promote]** verbinden.

   Wenn die Verbindungserfolgsmeldung angezeigt wird, wählen Sie **[!UICONTROL OK]** aus.

   (Nach dem Verbinden ändert sich der Schaltflächentext in &quot;Erneut mit Search&amp;Promote verbinden&quot;.)

1. Wählen Sie **[!UICONTROL OK]** aus. Die Seite &quot;Search&amp;Promote-Einstellungen&quot;wird für die von Ihnen erstellte Konfiguration angezeigt.

## Rechenzentrum konfigurieren {#configuring-the-data-center}

Wenn sich Ihr Search&amp;Promote in Asien oder Europa befindet, müssen Sie das standardmäßige Rechenzentrum so ändern, dass es auf das richtige Rechenzentrum verweist (das standardmäßige Rechenzentrum gilt für nordamerikanische Konten).

**Sie können das Datenzentrum wie folgt konfigurieren:**

1. Navigieren Sie zur Webkonsole unter `https://localhost:4502/system/console/configMgr/com.day.cq.searchpromote.impl.SearchPromoteServiceImpl` .

   ![](assets/chlimage_1-61.png)

1. Ändern Sie den URI je nach Standort des Servers in einen der folgenden:

   * Nordamerika: [https://center.atomz.com/px/](https://center.atomz.com/px/)
   * EMEA: [https://center.lon5.atomz.com/px/](https://center.lon5.atomz.com/px/)
   * APAC: [https://center.sin2.atomz.com/px/](https://center.sin2.atomz.com/px/)

1. Wählen Sie **[!UICONTROL Speichern]** aus.

## Fügen Sie dem Sidekick Search&amp;Promote-Komponenten hinzu {#adding-search-promote-components-to-sidekick}

Bearbeiten Sie im Designmodus eine **par**-Komponente, sodass sie die Search&amp;Promote-Komponenten im Sidekick zulässt. (In der Dokumentation zu den [Komponenten](/help/sites-developing/components.md#addinganewcomponenttotheparagraphsystemdesignmode) finden Sie weitere Informationen.)

Weitere Informationen zur Verwendung der Komponenten finden Sie unter [Hinzufügen von Search&amp;Promote-Funktionen zu einer Webseite](/help/sites-authoring/search-and-promote.md).)

## Geben Sie den Search&amp;Promote-Dienst an, den Ihre Seiten verwenden {#specifying-the-search-promote-service-that-your-pages-use}

Konfigurieren Sie Webseiten so, dass diese einen spezifischen Search&amp;Promote-Dienst verwenden. Search&amp;Promote-Komponenten verwenden automatisch den Dienst ihrer Hostseite.

Wenn Sie die Search&amp;Promote-Eigenschaften für eine Hostseite konfigurieren, übernehmen alle untergeordneten Seiten die Einstellungen. Bei Bedarf können Sie untergeordnete Seiten so konfigurieren, dass die geerbten Einstellungen überschrieben werden.

>[!NOTE]
>
>Die Dienstverbindung muss zuvor konfiguriert werden. (Siehe [Konfigurieren der Verbindung zu Search&amp;Promote](#connection).)

1. Öffnen Sie das Dialogfeld **[!UICONTROL Seiteneigenschaften]**. Klicken Sie beispielsweise auf der Seite &quot;Websites&quot;mit der rechten Maustaste auf die Seite und wählen Sie **[!UICONTROL Eigenschaften]** aus.
1. Wählen Sie die Registerkarte **[!UICONTROL Cloud-Services]** aus.
1. Um die Vererbung von Cloud Services-Konfigurationen von einer übergeordneten Seite zu deaktivieren, wählen Sie das Vorhängeschlosssymbol neben dem Vererbungspfad aus.

   ![](assets/sandpinheritpadlock.png)

1. Wählen Sie **[!UICONTROL Service]** hinzufügen.
1. Wählen Sie **[!UICONTROL Adobe Search&amp;Promote]** und dann **[!UICONTROL OK]** aus.
1. Wählen Sie die Verbindungskonfiguration für Ihr Search&amp;Promote-Konto aus und klicken Sie auf **OK**.

## Produkt-Feed {#product-feed}

Die Search&amp;Promote-Integration bietet folgende Möglichkeiten:

* Verwenden Sie die eCommerce-API unabhängig von der zugrunde liegenden Repository-Struktur und Commerce-Plattform.
* Verwenden Sie die Index Connector-Funktion von Search&amp;Promote, damit Sie einen Produkt-Feed im XML-Format haben können.
* Verwenden Sie die Fernsteuerungsfunktion von Search&amp;Promote, wenn Sie On-Demand- oder geplante Anfragen für den Produkt-Feed ausführen möchten.
* Feed-Generierung für verschiedene Search&amp;Promote-Konten, konfiguriert als Cloud Services-Konfigurationen.

Weitere Informationen finden Sie unter [Produkt-Feed](/help/sites-administering/product-feed.md).
