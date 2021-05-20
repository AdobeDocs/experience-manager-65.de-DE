---
title: Ist Ihre Hybrid-App für AEM Mobile bereit?
seo-title: Ist Ihre Hybrid-App für AEM Mobile bereit?
description: Auf dieser Seite erfahren Sie mehr über Hrybrid-Apps. Eine App in AEM ist in der Regel in zwei Teile unterteilt. "Shell"und "Inhalt"sowie diese Seite bieten weitere Einblicke zu diesen Themen.
seo-description: Auf dieser Seite erfahren Sie mehr über Hrybrid-Apps. Eine App in AEM ist in der Regel in zwei Teile unterteilt. "Shell"und "Inhalt"sowie diese Seite bieten weitere Einblicke zu diesen Themen.
uuid: cbcce3fa-9100-46ea-9f24-931b42666709
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: b7fd7954-f2a5-402d-b259-e18b5a618be9
pagetitle: Is your hybrid app ready for AEM Mobile?
exl-id: 4625890c-2b76-4c78-88e8-23741bc09f5b
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '780'
ht-degree: 3%

---

# Ist Ihre Hybrid-App für AEM Mobile bereit?{#is-your-hybrid-app-ready-for-aem-mobile}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Sie haben Ihre Hybrid PhoneGap- oder Cordova-App in AEM importiert, was? Wahrscheinlich möchten Sie Ihrer App bearbeitbare Inhalte hinzufügen. Um diese Aufgabe zu erfüllen, benötigen Sie ein allgemeines Verständnis der Struktur einer AEM App. Eine App in AEM ist in der Regel in zwei Teile unterteilt. &quot;Shell&quot;und &quot;Inhalt&quot;. Die &quot;Shell&quot;umfasst die statischen Teile Ihrer App. wie die PhoneGap-Konfigurationsdateien, das App-Framework und die Navigationssteuerelemente. Der Inhalt des von Ihnen importierten Archivs wird als Teil der Shell gespeichert. Im Kontext dieses Dokuments ist die Shell der gesamte nicht AEM erstellte Inhalt Ihrer Hybrid PhoneGap-App, der vom App-Entwickler erstellt wurde.

Inhalt bezieht sich auf die Komponenten, Vorlagen und erstellten Seiten, die in AEM erstellt wurden, die vom AEM-Entwickler erstellt wurden. Inhalte werden entweder als Entwicklerinhalt oder als erstellten Inhalt kategorisiert. Komponenten, Designs und Seitenvorlagen gelten als Dev-Content, da sie von einem Entwickler erstellt wurden. author-content sind Seiten, die mit den Komponenten und Vorlagen erstellt wurden. Diese werden normalerweise von einem Designer oder Marketingexperten durchgeführt.

Das Hinzufügen von erstellten AEM zu Ihrer Hybrid-App erfordert eine Koordinierung zwischen dem App-Entwickler und dem AEM. überall in der App, wo Sie erstellten Inhalt hinzufügen möchten, muss der App-Entwickler diese Seiten in einer Struktur organisieren, die in AEM überlagert werden kann. Der App-Entwickler muss in der Lage sein, den AEM-Entwickler mit den Pfaden zu versorgen, zu denen die AEM erstellten Inhalte hinzugefügt werden sollen, und dann eine Platzhalterseite in der Hybrid-App bereitzustellen, die ersetzt wird, nachdem der AEM-Entwickler den Seiteninhalt erstellt hat.

Um das Befolgen der Erklärung zu vereinfachen, verwenden wir das AEM Marketing Cloud: AEM Mobile Hybrid-Referenz , um die Konzepte zu erläutern. Die Hybrid-Referenz-App besteht aus einer Begrüßungsseite mit einem Seitenmenü.

![chlimage_1-76](assets/chlimage_1-76.png)

In diesem Beispiel erstellen wir die Begrüßungsseite der Anwendung. Sehen Sie sich die Quelle [https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference/blob/master/hybrid-app/www/js/app.js#L75](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference/blob/master/hybrid-app/www/js/app.js#L75) an. Wir sehen, dass der App-Entwickler eine Begrüßungsseite definiert und eine Vorlage für die Seite bereitgestellt hat, die von der App gerendert wird. Hier müssen sich der App-Entwickler und AEM Entwickler koordinieren. Der Pfad zur Begrüßungsseitenvorlage in der Hybrid-Referenzanwendung ist als &quot;&#39;content/mobileapps/hybrid-reference-app/en/welcome.template.html&#39;&#39; definiert. Dieser Pfad ist äußerst wichtig, da der AEM-Entwickler seine Begrüßungsseite im AEM-Repository mit demselben Pfad erstellt.

![chlimage_1-77](assets/chlimage_1-77.png)

Es ist wichtig, dass die Hybrid-App und die AEM erstellten Inhalte denselben Pfad verwenden, da wir darauf angewiesen sind, Inhalte mithilfe der Inhaltssynchronisierung zu überlagern, um neue Seiten zur Hybrid-App hinzuzufügen. Wenn die Hybrid-App im Rahmen des Importvorgangs in AEM importiert wird, werden die Konfigurationen für die Inhaltssynchronisierung eingerichtet.

![chlimage_1-78](assets/chlimage_1-78.png)

Wenn Sie &quot;Quelle herunterladen&quot;aus dem App-Dashboard auswählen, werden diese ContentSync-Skripte ausgeführt, um ein Archiv Ihrer Hybrid-App zu assemblieren.

![chlimage_1-79](assets/chlimage_1-79.png)

ContentSync ruft zunächst die &quot;Shell&quot;der App ab, in der alle von der App entwickelten Inhalte der Hybrid-App gespeichert sind, und ruft dann den &quot;Inhalt&quot;der App ab. Wenn es jetzt Seiten in der &#39;Shell&#39; gibt, die denselben Pfad wie in &#39;content&#39; haben, werden die Seiten unter &#39;shell&#39; durch die Seiten unter &#39;content&#39; ersetzt. Anders ausgedrückt: Im Beispiel der Hybrid-Referenz-App wird die Seite, die Teil der Hybrid-Referenz-App war, überlagert, wenn Sie in AEM eine Seite erstellen, die denselben Pfad wie &quot;content/mobileapps/hybrid-reference-app/en/welcome.template.html&quot;hat, wenn ContentSync ausgeführt wird. Die Überlagerung wird von ContentSync übernommen, damit die Aktualisierungen der App mit AEM erstellten Inhalten nahtlos aussehen und keine Neuerstellung der App erfordern. Wenn Sie die App ausführen, wird die Begrüßungsseite daher wie folgt angezeigt:

![chlimage_1-80](assets/chlimage_1-80.png)
