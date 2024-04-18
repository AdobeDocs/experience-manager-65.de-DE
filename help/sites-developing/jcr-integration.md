---
title: JCR-Integration
description: Hier finden Sie Tipps zur Integration in Adobe Experience Manager auf JCR-Ebene.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: 170474c1-c7f4-446c-bda4-84768d44a078
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 100%

---

# JCR-Integration{#jcr-integration}

## Ziehen Sie die Sling-Ressourcen-API der JCR-API vor {#prefer-the-sling-resource-api-to-jcr-api}

Die Sling-API arbeitet auf einem höheren, abstrakteren Niveau als die JCR-API. Dadurch kann Ihr Code wiederverwendbar und unabhängig vom zugrunde liegenden Speicher sein. Dies erleichtert ggf. das Einbinden externer virtueller Daten über den ResourceProvider-Mechanismus.

## Vermeiden Sie Abfragen, wo immer es möglich ist {#avoid-queries-wherever-possible}

Es ist immer schneller, das Repository zu durchsuchen, um Daten abzurufen, als eine Abfrage auszuführen. Es gibt Fälle, in denen Abfragen erforderlich sind, z. B. eine Endbenutzerabfrage oder die Suche nach strukturiertem Inhalt aus dem gesamten Repository, aber in allen anderen Fällen wird es bevorzugt, zu den erforderlichen Knoten zu navigieren. In der Render-Logik, z. B. in Navigationskomponenten, einer „Liste der letzten Elemente“, Anzahl von Elementen usw., sollten Abfragen grundsätzlich vermieden werden. In diesen Fällen ist es besser, durch die Hierarchie zu gehen oder das Ergebnis vorab zwischenzuspeichern, damit es direkt beim Rendern verwendet werden kann.

## Schränken Sie den Umfang der JCR-Beobachtung ein {#restrict-the-scope-of-jcr-observation}

Beim Lauschen auf Ereignisse im Repository ist es wichtig, den Umfang so weit wie möglich einzuschränken. Zum Beispiel ist es viel besser, `/etc/mycompany` auf ein Ereignis zu überwachen als `/etc`. Lauschen Sie niemals auf Ereignisse am Repository-Stamm. Stellen Sie außerdem sicher, dass die Callback-Methoden so schnell wie möglich ausgeführt werden, wenn für sie nichts zu tun ist.

## Beseitigen Sie den JCR-Administratorzugriff {#eliminate-use-of-jcr-admin-access}

Ab AEM 6 ist die Anmeldung als Admin veraltet, da eine Verwaltungssitzung von ResourceResolverFactory abgerufen wird. Stattdessen sollten Dienstkonten für die Back-Office-Vorgänge erstellt werden, die diese Art des Zugriffs erfordern, und mit der ResourceResolverFactory kann ein ResourceResolver für dieses Konto abgerufen werden.
