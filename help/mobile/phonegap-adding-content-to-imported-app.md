---
title: Ist Ihre Hybrid-App für AEM Mobile bereit?
description: Erfahren Sie mehr über hybride Apps. Eine App im Experience Manager ist in der Regel in zwei Teile unterteilt. "Shell"und "Inhalt"sowie diese Seite bieten weitere Einblicke zu diesen Themen.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
pagetitle: Is your hybrid app ready for AEM Mobile?
exl-id: 4625890c-2b76-4c78-88e8-23741bc09f5b
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 4%

---

# Ist Ihre Hybrid-App für Adobe Experience Manager Mobile bereit?{#is-your-hybrid-app-ready-for-aem-mobile}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Sie haben Ihre Hybrid PhoneGap- oder Cordova-App in AEM importiert, was? Wahrscheinlich möchten Sie Ihrer App bearbeitbare Inhalte hinzufügen. Um diese Aufgabe zu erfüllen, benötigen Sie ein allgemeines Verständnis der Struktur einer AEM App. Eine App in AEM ist in der Regel in zwei Teile unterteilt. &quot;Shell&quot;und &quot;Inhalt&quot;. Die &quot;Shell&quot;umfasst die statischen Teile Ihrer App, z. B. die PhoneGap-Konfigurationsdateien, das App-Framework und die Navigationssteuerelemente. Der Inhalt des von Ihnen importierten Archivs wird als Teil der Shell gespeichert. Im Kontext dieses Dokuments ist die Shell der gesamte nicht AEM erstellte Inhalt Ihrer Hybrid PhoneGap-App, der vom App-Entwickler erstellt wurde.

Inhalt bezieht sich auf die Komponenten, Vorlagen und erstellten Seiten, die in AEM erstellt wurden, die vom AEM-Entwickler erstellt wurden. Inhalte werden entweder als Entwicklerinhalt oder als erstellten Inhalt kategorisiert. Komponenten, Designs und Seitenvorlagen gelten als Dev-Content, da sie von einem Entwickler erstellt wurden. Autoreninhalte sind Seiten, die mit den Komponenten und Vorlagen erstellt wurden. Diese Seiten werden normalerweise von einem Designer oder Marketingexperten erstellt.

Das Hinzufügen von erstellten AEM zu Ihrer Hybrid-App erfordert eine Koordinierung zwischen dem App-Entwickler und dem AEM. überall in der App, wo Sie erstellten Inhalt hinzufügen möchten, muss der App-Entwickler diese Seiten in einer Struktur organisieren, die in Experience Manager überlagert werden kann. Der App-Entwickler muss in der Lage sein, dem Experience Manager-Entwickler die Pfade zur Verfügung zu stellen, zu denen der Experience Manager-Autoreninhalt hinzugefügt wird. Geben Sie dann eine Platzhalterseite in der Hybrid-App an, die ersetzt wird, nachdem der Experience Manager-Entwickler den Seiteninhalt erstellt hat.

Um die Erläuterung leichter zu befolgen, wird die AEM Experience Cloud verwendet: AEM Mobile Hybrid-Referenz zur Erläuterung der Konzepte. Die Hybrid-Referenz-App besteht aus einer Begrüßungsseite mit einem Seitenmenü.

![chlimage_1-76](assets/chlimage_1-76.png)

In diesem Beispiel wird die Begrüßungsseite der Anwendung erstellt. Betrachten der Quelle [https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference/blob/master/hybrid-app/www/js/app.js#L75](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference/blob/master/hybrid-app/www/js/app.js#L75). Beachten Sie, dass der App-Entwickler eine Begrüßungsseite definiert und eine Vorlage für die Seite bereitgestellt hat, die von der App gerendert wird. Auf dieser Seite müssen sich der App-Entwickler und AEM Entwickler koordinieren. Der Pfad zur Vorlage für die Begrüßungsseite in der Hybrid-Referenz-App ist als &quot;&#39;content/mobileapps/hybrid-reference-app/en/welcome.template.html&#39;&#39; definiert. Dieser Pfad ist wichtig, da der AEM-Entwickler seine Begrüßungsseite im AEM-Repository mit demselben Pfad erstellt.

![chlimage_1-77](assets/chlimage_1-77.png)

Es ist wichtig, dass die Hybrid-App und die AEM erstellten Inhalte denselben Pfad verwenden, da sie darauf angewiesen sind, Inhalte mithilfe der Inhaltssynchronisierung zu überlagern, um neue Seiten zur Hybrid-App hinzuzufügen. Wenn die Hybrid-App in AEM importiert wird, werden im Rahmen des Importvorgangs Konfigurationen für die Inhaltssynchronisierung eingerichtet.

![chlimage_1-78](assets/chlimage_1-78.png)

Wenn Sie &quot;Quelle herunterladen&quot;aus dem App-Dashboard auswählen, werden diese ContentSync-Skripte ausgeführt, um ein Archiv Ihrer Hybrid-App zu assemblieren.

![chlimage_1-79](assets/chlimage_1-79.png)

ContentSync ruft zunächst die &quot;Shell&quot;der App ab, in der alle von der App entwickelten Inhalte der Hybrid-App gespeichert sind. Anschließend wird der &quot;Inhalt&quot;der App abgerufen. Wenn es nun Seiten in der &#39;Shell&#39; gibt, die denselben Pfad wie in &#39;content&#39; haben, werden die Seiten unter &#39;shell&#39; durch die Seiten unter &#39;content&#39; ersetzt. Wenn also im Beispiel der Hybrid-Referenz-App eine Seite in AEM erstellt wird, die denselben Pfad wie &quot;content/mobileapps/hybrid-reference-app/en/welcome.template.html&quot;hat, überlagert ContentSync die Seite, die Teil der Hybrid-Referenz-App war. Er überlagert ihn mit dem, was sich an AEM Stelle befindet. Die Überlagerung wird von ContentSync übernommen. Daher sehen die Aktualisierungen der App mit AEM erstellten Inhalten nahtlos aus und erfordern keine Neuerstellung der App. Wenn Sie die App ausführen, wird daher die Begrüßungsseite wie folgt angezeigt:

![chlimage_1-80](assets/chlimage_1-80.png)
