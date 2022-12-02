---
title: Repository-Neustrukturierung in AEM 6.5
seo-title: Repository Restructuring in AEM 6.5
description: Informieren Sie sich über die Grundlagen und die Logik hinter der Repository-Neustrukturierung in AEM 6.5
seo-description: Learn about the basics and reasoning behind the repository restructuring in AEM 6.5
uuid: e9cd3e88-e352-44a8-9b97-69488d3267cb
contentOwner: chaikels
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: fc879b0b-823b-4bdc-aaa6-36f53a33fb22
feature: Upgrading
exl-id: 2572aa8d-2a3a-4e5b-ae5f-07e1017ea0f4
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '534'
ht-degree: 100%

---

# Repository-Neustrukturierung in AEM 6.5{#repository-restructuring-in-aem}

## Einführung {#introduction}

In Versionen vor AEM 6.4 wurde Kunden-Code teilweise in JCR-Bereichen bereitgestellt, die bei Aktualisierungen geändert werden konnten. Aus diesem Grund war es üblich, dass formale AEM-Versionen benutzerdefinierten Code, Konfigurationen oder Inhalte überschrieben haben. Darüber hinaus kam es vor, dass durch Kunden vorgenommene Änderungen den AEM-Produktcode oder AEM-Inhalte überschrieben und dadurch die Produktfunktionen beeinträchtigten.

Durch klare Abgrenzungshierarchien für AEM-Produkt-Code und Kunden-Code können diese Konflikte vermieden werden.

Aus diesem Grund wird ab AEM 6.4 und in zukünftigen Versionen der Inhalt aus „/etc“ in andere Ordner im Repository verschoben und es gibt Richtlinien dafür, welcher Inhalt wo gespeichert wird. Dabei kommen die folgenden Regeln zur Anwendung:

* AEM-Produkt-Code wird immer im Ordner „/libs“ abgelegt, der nicht durch benutzerdefinierten Code überschrieben werden darf.
* Benutzerdefinierter Code sollte in „/apps“, „/content“ und „/conf“ gespeichert werden.

## Auswirkungen auf Aktualisierungen auf 6.5 {#impact-on-upgrades}

Beim Aktualisieren auf AEM 6.5 wird eine große Teilmenge des Inhalts unter „/etc“ in andere Ordner im Repository dupliziert. Diese neuen Speicherorte sind die bevorzugten Stellen, an denen der Inhalt referenziert wird. Allerdings ist die Aktualisierung auf AEM 6.5 abwärtskompatibel mit den früheren Speicherorten im Ordner „/etc“, sodass der AEM-Code in den meisten Fällen weiterhin auf die alten Speicherorte verweist, bis Änderungen im Programm eines Kunden aktiv –- und in vielen Fällen manuell – vorgenommen werden. Hinsichtlich des Zeitrahmens gibt es zwei Kategorien von Änderungen:

* Mit der Aktualisierung auf 6.5: Einige der Neustrukturierungsänderungen für „/etc“ sind nicht abwärtskompatibel und entsprechend sollten Änderungen im Rahmen der Aktualisierung auf AEM 6.5 geplant und umgesetzt werden.
* Vor der zukünftigen Aktualisierung: Die überwiegende Mehrheit der Neustrukturierungsänderungen für „/etc“ kann auf einen späteren Zeitpunkt nach der Aktualisierung verschoben werden. Wie bereits erwähnt, verweist der AEM 6.5-Code weiterhin auf die alten Speicherorte, bis die Änderungen im Rahmen einer Kundenfreigabe implementiert werden. Es gibt zwar keinen erforderlichen Zeitrahmen für die Änderungen, es wird jedoch empfohlen, sie vor der zukünftigen Aktualisierung durchzuführen, da zukünftige Funktionen davon abhängen können, dass die neuen Speicherorte referenziert werden. Auch verweist die Dokumentation für eine bestimmte Funktion standardmäßig auf die neuen Speicherorte, weswegen die Verwendung alter Speicherorte verwirrend sein könnte.

### Leitfaden für die Neustrukturierung {#restructuring-guidance}

Bei der Planung einer Aktualisierung auf AEM 6.5 sollten die folgenden Seiten zur Abschätzung des Arbeitsaufwands herangezogen werden:

* [Repository-Neustrukturierung für alle AEM-Lösungen](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md)
* [Repository-Neustrukturierung für AEM Sites](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md)
* [Repository-Neustrukturierung für AEM Assets](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md)
* [Repository-Neustrukturierung für AEM Assets Dynamic Media](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-5.md)
* [Repository-Neustrukturierung für AEM Forms](/help/sites-deploying/forms-repository-restructuring-in-aem-6-5.md)
* [Repository-Neustrukturierung für AEM Communities](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md)
* [Repository-Neustrukturierung für AEM Commerce](/help/sites-deploying/ecommerce-repository-restructuring-in-aem-6-5.md)

Jede Seite enthält zwei Bereiche entsprechend der Dringlichkeit der erforderlichen Änderungen. Alle Punkte im Abschnitt „Mit der Aktualisierung auf 6.5“ sollten im Rahmen des AEM 6.5-Aktualisierungsprojekts behandelt werden. Alles, was unter „Vor der zukünftigen Aktualisierung“ steht, kann optional auf nach der Aktualisierung verschoben werden.

Jeder Eintrag auf der Seite enthält ein Feld „Leitfaden für die Neustrukturierung“, in dem die empfohlene technische Strategie für die Ausrichtung an dem neuen 6.5-Repository-Modell beschrieben wird, sodass die neuen Speicherorte für Inhalte referenziert werden, die sich zuvor im Ordner „/etc“ befanden. Ein zusätzliches Feld „Hinweise“ bietet zusätzlichen nützlichen Kontext.
