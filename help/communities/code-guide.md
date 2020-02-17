---
title: 'Kodierungsrichtlinien '
seo-title: 'Kodierungsrichtlinien '
description: Richtlinien, Tipps und Tricks für Community-Entwickler
seo-description: Richtlinien, Tipps und Tricks für Community-Entwickler
uuid: 311ef4f7-7f2c-44c3-bcf2-f68713752623
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 244cd43c-a573-495d-b80c-b97ba9d19b75
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Kodierungsrichtlinien {#coding-guidelines}

## Richtlinien, Tipps und Tricks {#guidelines-tips-and-tricks}

Die Zusammenarbeit mit AEM Communities hat sich von der Abhängigkeit von Java Server Pages zu einer flexiblen Auswahl von Vorlagen für Skriptsprachen entwickelt, bei denen Geschäftslogik, Stil und Seiteninhalt voneinander unterscheiden.

Die SocialResourceProvider-API bietet weitere Flexibilität bei der Arbeit mit benutzergenerierten Inhalten (UGC), sodass Sie nicht mehr wissen müssen, welche [SRP](srp.md) -Option für die Bereitstellung ausgewählt wurde.

Im Folgenden finden Sie verschiedene Kodierungsrichtlinien und Best Practices für AEM Communities-Entwickler:

### Code{#code}

* [Zugriff auf UGC mit SRP](accessing-ugc-with-srp.md) - Wie vermeiden Sie das Schreiben einer Anwendung, die nur funktioniert, wenn UGC in JCR (JSRP) gespeichert wird.
* [SocialUtils Refactoring](socialutils.md) - Dienstprogrammmethoden für SRP, die SocialUtils ersetzen.
* [Benennungsregeln](naming-conventions.md) - Benennungskonventionen für benutzerdefinierte Java-Klassen.

### Skripten {#scripts}

* [Sideloading Communities Components](sideloading.md) - Anleitung zum dynamischen Hinzufügen einer Komponente nach dem Laden der Seite.
* [Rich Text Editor Essentials](rte.md) - Anleitung zum Anpassen der Rich-Text-Benutzeroberfläche, die Mitgliedern zum Posten von Inhalten zur Verfügung gestellt wird.

### IDE {#ide}

* [Verwenden von Maven for Communities](maven.md) - Anleitung zum Einbeziehen der Communities API-JARs.
* [SocialUtils Refactoring](socialutils.md) - Dienstprogrammmethoden für SRP, die SocialUtils ersetzen.

