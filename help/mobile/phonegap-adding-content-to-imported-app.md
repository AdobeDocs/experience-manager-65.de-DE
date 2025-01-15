---
title: Ist Ihre Hybrid-App bereit für AEM Mobile?
description: Informationen zu Hybrid-Apps. Eine App in Experience Manager ist normalerweise in zwei Teile unterteilt. Die „Shell“ und „Inhalt“ sowie diese Seite bieten weitere Einblicke in diese Themen.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
pagetitle: Is your hybrid app ready for AEM Mobile?
exl-id: 4625890c-2b76-4c78-88e8-23741bc09f5b
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 1%

---

# Ist Ihre Hybrid-App bereit für Adobe Experience Manager Mobile?{#is-your-hybrid-app-ready-for-aem-mobile}

{{ue-over-mobile}}

Sie haben also Ihre hybride PhoneGap- oder Cordova-App in AEM importiert, was nun? Wahrscheinlich möchten Sie bearbeitbare Inhalte zu Ihrer App hinzufügen. Um diese Aufgabe zu bewältigen, benötigen Sie allgemeine Kenntnisse über die Struktur einer AEM-App. Eine App in AEM ist in der Regel in zwei Teile unterteilt. Die „Shell“ und der „Inhalt“. Die „Shell“ umfasst die statischen Teile Ihrer App, z. B. die PhoneGap-Konfigurationsdateien, das App-Framework und die Navigationssteuerelemente. Der Inhalt des importierten Archivs wird als Teil der Shell gespeichert. Im Kontext dieses Dokuments ist die Shell der gesamte nicht von AEM erstellte Inhalt Ihrer hybriden PhoneGap-App, der vom App-Entwickler erstellt wurde.

Inhalte beziehen sich auf die Komponenten, Vorlagen und erstellten Seiten, die in AEM erstellt wurden, die von AEM Developer erstellt wurde. Inhalte werden entweder als Entwicklerinhalte oder als erstellte Inhalte kategorisiert. Komponenten, Designs und Seitenvorlagen gelten als Entwicklungsinhalte, da sie von einem Entwickler erstellt werden. Authoring-Inhalte sind Seiten, die mithilfe der Komponenten und Vorlagen erstellt wurden. Diese Seiten werden normalerweise von einer Designer oder einem Marketing-Experten erstellt.

Das Hinzufügen von erstellten AEM-Seiten zu Ihrer Hybrid-App erfordert die Koordinierung zwischen dem App-Entwickler und dem AEM-Entwickler. Überall in der App, wo Sie erstellten Inhalt hinzufügen möchten, muss der App-Entwickler diese Seiten in einer Struktur organisieren, die in Experience Manager überlagert werden kann. Der App-Entwickler muss in der Lage sein, dem Entwickler des Experience Managers die Pfade anzugeben, zu denen der von dem Experience Manager erstellte Inhalt hinzugefügt wird. Geben Sie dann in der Hybrid-App eine Platzhalterseite an, die ersetzt wird, nachdem der Experience Manager-Entwickler den Seiteninhalt erstellt hat.

Um die Erläuterung zu vereinfachen, wird die AEM-Experience Cloud verwendet: AEM Mobile Hybrid-Referenz zur Erläuterung der Konzepte. Die Hybrid-Referenz-App besteht aus einer Begrüßungsseite mit einem Seitenmenü.

![chlimage_1-76](assets/chlimage_1-76.png)

In diesem Beispiel wird die Begrüßungsseite des Programms verfasst. Überprüfung der Quelle [https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference/blob/master/hybrid-app/www/js/app.js#L75](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference/blob/master/hybrid-app/www/js/app.js#L75). Beachten Sie, dass der App-Entwickler eine Begrüßungsseite definiert und eine Vorlage für die Seite bereitgestellt hat, die von der App gerendert wird. Auf dieser Seite müssen sich der App-Entwickler und der AEM-Entwickler abstimmen. Der Pfad zur Vorlage für die Begrüßungsseite in der Hybrid-Referenz-App ist als &quot;content/mobileapps/hybrid-reference-app/en/welcome.template.html“ definiert. Dieser Pfad ist wichtig, da der AEM-Entwickler die Begrüßungsseite im AEM-Repository unter Verwendung desselben Pfads erstellt.

![chlimage_1-77](assets/chlimage_1-77.png)

Es ist wichtig, dass die Hybrid-App und die von der AEM erstellten Inhalte denselben Pfad verwenden, da dies auf der Möglichkeit beruht, Inhalte mithilfe der Inhaltssynchronisierung zu überlagern, um der Hybrid-App neue Seiten hinzuzufügen. Wenn die Hybrid-App im Rahmen des Importvorgangs in AEM importiert wird, werden Content Sync-Konfigurationen eingerichtet.

![chlimage_1-78](assets/chlimage_1-78.png)

Wenn Sie &quot;Source herunterladen“ über das App-Dashboard, werden diese ContentSync-Skripte ausgeführt, um ein Archiv Ihrer Hybrid-App zusammenzustellen.

![chlimage_1-79](assets/chlimage_1-79.png)

ContentSync ruft zunächst die „Shell“ der App ab, in der der gesamte von der App entwickelte Inhalt der Hybrid-App gespeichert wird. Anschließend ruft es den „Inhalt“ der App ab. Wenn es nun Seiten in der &#39;Shell&#39; gibt, die denselben Pfad wie in &#39;content&#39; haben, werden die Seiten unter &#39;shell&#39; durch die Seiten unter &#39;content&#39; ersetzt. Wenn also im Beispiel für die Hybrid-Referenz-App eine Seite in AEM erstellt wird, die denselben Pfad wie &quot;content/mobileapps/hybrid-reference-app/en/welcome.template.html“ hat, wird bei der Ausführung von ContentSync die Seite überlagert, die Teil der Hybrid-Referenz-App war. Es überlagert sie mit dem, was sich an diesem Speicherort in AEM befindet. Die Überlagerung wird von ContentSync übernommen, sodass für jemanden, der die App verwendet, die Aktualisierungen der App mit von AEM erstellten Inhalten nahtlos aussehen und keine Neuerstellung der App erforderlich ist. Wenn Sie die App ausführen, wird die Begrüßungsseite daher wie folgt angezeigt:

![chlimage_1-80](assets/chlimage_1-80.png)
