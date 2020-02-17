---
title: Ist Ihre Hybrid-App für AEM Mobile bereit?
seo-title: Ist Ihre Hybrid-App für AEM Mobile bereit?
description: Auf dieser Seite erfahren Sie mehr über Hrybrid-Apps. Eine App in AEM ist in der Regel in zwei Teile unterteilt. Die 'Shell' und 'content' und diese Seite bieten weitere Einblicke zu diesen Themen.
seo-description: Auf dieser Seite erfahren Sie mehr über Hrybrid-Apps. Eine App in AEM ist in der Regel in zwei Teile unterteilt. Die 'Shell' und 'content' und diese Seite bieten weitere Einblicke zu diesen Themen.
uuid: cbcce3fa-9100-46ea-9f24-931b42666709
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: b7fd7954-f2a5-402d-b259-e18b5a618be9
pagetitle: Is your hybrid app ready for AEM Mobile?
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Ist Ihre Hybrid-App für AEM Mobile bereit?{#is-your-hybrid-app-ready-for-aem-mobile}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Sie haben also Ihre Hybrid PhoneGap- oder Cordova-App in AEM importiert, was? Wahrscheinlich möchten Sie Ihrer App authentifizierbaren Inhalt hinzufügen. Für diese Aufgabe benötigen Sie ein allgemeines Verständnis der Struktur einer AEM-App. Eine App in AEM ist in der Regel in zwei Teile unterteilt. Die &#39;Shell&#39; und &#39;content&#39;. Die Shell umfasst die statischen Teile Ihrer App. wie die PhoneGap-Konfigurationsdateien, das App-Framework und die Navigationssteuerelemente. Der Inhalt des importierten Archivs wird als Teil der Shell gespeichert. Im Kontext dieses Dokuments ist die Shell der gesamte nicht von AEM erstellte Inhalt Ihrer Hybrid PhoneGap-App, der vom App-Entwickler erstellt wurde.

Inhalt bezieht sich auf die Komponenten, Vorlagen und erstellten Seiten, die in AEM erstellt wurden und von AEM Developer erstellt wurden. Inhalte werden entweder als Entwicklerinhalt oder als verfasster Inhalt kategorisiert. Komponenten, Entwürfe und Seitenvorlagen gelten als Dev-Content, da sie von einem Entwickler erstellt wurden. Autoreninhalt sind Seiten, die mit den Komponenten und Vorlagen erstellt wurden. Diese werden normalerweise von einem Designer oder Vermarkter durchgeführt.

Das Hinzufügen von erstellten AEM-Seiten zu Ihrer Hybrid-App erfordert die Koordination zwischen dem App-Entwickler und dem AEM-Entwickler. Überall in der App, wo Sie verfasste Inhalte hinzufügen möchten, muss der App-Entwickler diese Seiten in einer Struktur organisieren, die in AEM überlagert werden kann. Der App-Entwickler muss dem AEM-Entwickler die Pfade bereitstellen können, zu denen die AEM-erstellten Inhalte hinzugefügt werden sollen, und dann eine Platzhalterseite in der Hybrid-App bereitstellen, die ersetzt wird, nachdem der AEM-Entwickler den Seiteninhalt erstellt hat.

Um die Erklärung einfacher zu befolgen, verwenden wir die AEM Marketing Cloud: AEM Mobile Hybrid-Referenz, um die Konzepte zu erläutern. Die Hybrid-Referenz-App besteht aus einer Begrüßungsseite mit einem Seitenmenü.

![chlimage_1-76](assets/chlimage_1-76.png)

In diesem Beispiel erstellen wir die Begrüßungsseite des Antrags. Sehen Sie sich die Quelle [https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference/blob/master/hybrid-app/www/js/app.js#L75](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference/blob/master/hybrid-app/www/js/app.js#L75)an. Der App-Entwickler hat eine Begrüßungsseite definiert und eine Vorlage für die Seite bereitgestellt, die von der App gerendert wird. Hier müssen sich der App-Entwickler und AEM-Entwickler koordinieren. Der Pfad zur Vorlage der Begrüßungsseite in der Hybrid-Referenzanwendung ist als &quot;content/mobileapps/hybrid-reference-app/en/welcome.template.html&quot;definiert. Dieser Pfad ist äußerst wichtig, da der AEM-Entwickler seine Begrüßungsseite im AEM-Repository unter demselben Pfad erstellen wird.

![chlimage_1-77](assets/chlimage_1-77.png)

Es ist wichtig, dass die Hybrid-App und die von AEM erstellten Inhalte denselben Pfad verwenden, da wir darauf angewiesen sind, Inhalte mithilfe der Inhaltssynchronisierung zu überlagern, um der Hybrid-App neue Seiten hinzuzufügen. Wenn die Hybrid-App im Rahmen des Importvorgangs in AEM importiert wird, werden Inhaltssynchronisierungskonfigurationen eingerichtet.

![chlimage_1-78](assets/chlimage_1-78.png)

Wenn Sie &quot;Quelle herunterladen&quot;vom App-Dashboard ausführen, werden diese ContentSync-Skripten ausgeführt, um ein Archiv Ihrer Hybrid-App zusammenzustellen.

![chlimage_1-79](assets/chlimage_1-79.png)

ContentSync ruft zunächst die Shell der App ab, in der der gesamte von der App entwickelte Inhalt der Hybrid-App gespeichert wird, und ruft dann den Inhalt der App ab. Wenn es nun Seiten in der &#39;Shell&#39; gibt, die denselben Pfad wie in &#39;content&#39; haben, werden die Seiten unter &#39;shell&#39; durch die Seiten unter &#39;content&#39; ersetzt. Anders ausgedrückt: Wenn Sie im Beispiel für eine Hybrid-Referenz-App eine Seite in AEM erstellen, die denselben Pfad wie &quot;content/mobileapps/hybrid-reference-app/en/welcome.template.html&quot;hat, wenn ContentSync ausgeführt wird, wird die Seite, die Teil der Hybrid-Referenz-App war, mit dem Inhalt in AEM an diesem Speicherort überlagert. Die Überlagerung wird von ContentSync übernommen, damit die Updates für die App mit den von AEM erstellten Inhalten nahtlos aussehen und nicht neu erstellt werden müssen. Wenn Sie die App ausführen, wird die Begrüßungsseite wie folgt angezeigt:

![chlimage_1-80](assets/chlimage_1-80.png)
