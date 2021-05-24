---
title: Entwicklungspraktiken
seo-title: Entwicklungspraktiken
description: Best Practices für die Entwicklung in AEM
seo-description: Best Practices für die Entwicklung in AEM
uuid: 27a75f7f-6e2c-4113-9e9f-c5013a4594c2
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 8b0297a1-d922-410f-9aaf-3a6b87e11dc0
exl-id: 65b2029e-03c9-4df4-8579-2b15dbee1035
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 100%

---

# Entwicklungspraktiken{#development-practices}

## Arbeit anhand einer Definition von „Fertig“{#work-according-to-a-definition-of-done}

Jedes Team hat ein eigenes Verständnis davon, was „fertig“ bedeutet, aber es ist wichtig, eines zu haben und sicherzustellen, dass eine Story die definierten Kriterien erfüllt, bevor sie akzeptiert wird.

Einige häufig von Teams angegebene Kriterien sind:

* Code für die Formatierung überprüft
* Kommentare/Javadoc hinzugefügt
* Erfüllt erforderliche Testabdeckungsstufen
* Besteht Einheits- und Integrationstests
* In der QA-Umgebung überprüft
* Lokalisierung implementiert

Ohne eine entsprechende Definition treten häufig Situationen auf, in denen vieles halbfertig, aber nichts abgeschlossen ist.

### Programmier- und Formatierungskonventionen definieren und einhalten  {#define-and-adhere-to-coding-and-formatting-conventions}

Dinge wie Einzüge und Leerräume erscheinen möglicherweise nicht wichtig, aber korrekt formatierter Code trägt erheblich zur Lesbarkeit und Pflegeleichtigkeit bei. Konventionen sollten im Team abgesprochen und beim Programmieren befolgt werden.

### Auf hohe Testabdeckung abzielen  {#aim-for-high-test-coverage}

Je größer eine Projektimplementierung, desto mehr Zeit ist auch erforderlich, um sie zu testen. Ohne entsprechende Testabdeckung kann das Testteam nicht skalieren und die Entwickler kommen irgendwann vor lauter Bugs nicht mehr hinterher.

Entwickler sollten TDD praktizieren und fehlschlagende Einheitstests vor dem Produktionscode schreiben, der ihre Anforderungen erfüllt. Die Qualitätssicherung sollte einen automatisierten Satz von Abnahmeprüfungen erstellen, um sicherzustellen, dass das System von einer hohen Ebene aus wie erwartet funktioniert.

Es gibt benutzerdefinierte Frameworks, z. B. Jackalope und Prosper, um die Imitation von JCR-APIs zu vereinfachen und so die Produktivität der Entwickler beim Schreiben von Einheitstests zu gewährleisten.

### Immer bereit für Demos sein  {#stay-demo-ready}

Das System sollte am Ende jeder Iteration für Demos im Unternehmen zur Verfügung stehen. Indem das System immer bereit für Demos gehalten wird, ist das Team immer nur eine Iteration von Produktionsbereitschaft entfernt und technische Rückstände werden auf ein vertretbares Maß beschränkt.

### Kontinuierliche Integrationsumgebung implementieren und verwenden {#implement-a-continuous-integration-environment-and-use-it}

Das Implementieren einer kontinuierlichen Integrationsumgebung ermöglicht das einfache und wiederholte Durchführen von Einheits- und Integrationstests. Außerdem werden so Bereitstellungen vom Entwicklungsteam entkoppelt, was andere Teile des Teams effizienter und Bereitstellungen stabiler sowie vorhersehbarer macht.

### Entwicklungszyklus durch niedrige Erstellungszeiten beschleunigen {#keep-the-development-cycle-fast-by-keeping-build-times-low}

Wenn Einheitstests zu viel Zeit beanspruchen, lassen Entwickler sie aus, wodurch sie ihren Wert verlieren. Wenn es viel Zeit in Anspruch nimmt, den Code zu erstellen und bereitzustellen, werden diese Aufgaben seltener durchgeführt. Indem Sie kurze Erstellungszeiten zur Priorität machen, wird sichergestellt, dass die Zeit, die wir in unsere Testabdeckung und CI-Infrastruktur investiert haben, weiterhin der Produktivität des Teams zugutekommt.

### „Sonar“ sowie andere statische Codeanalysewerkzeuge optimieren und ihre Berichte verwerten{#fine-tune-sonar-and-other-static-code-analysis-tools-and-act-on-their-reports}

Codeanalysewerkzeuge haben nur dann einen Wert, wenn ihre Berichte vom Entwicklerteam verwertet werden. Ohne die Optimierung der Analysen, die diese Tools bieten, sind die generierten Empfehlungen nicht relevant und verlieren ihren Wert.

### Der Pfadfinderregel folgen {#follow-the-boy-scout-rule}

Pfadfinder haben eine Regel: „Hinterlass es besser, als du es gefunden hast.“ Sofern sich alle Mitglieder des Entwicklerteams an diese Regel halten und eine Verbesserung vornehmen, wenn sie einen Fehler sehen, wird der Code konstant verbessert.

### Implementierung von YAGNI-Funktionen vermeiden {#avoid-implementing-yagni-features}

YAGNI (für „You Aren’t Gonna Need It“, zu deutsch: „Du wirst es nicht brauchen“)-Funktionen sind Dinge, die implementiert werden, wenn erwartet wird, dass sie in der Zukunft benötigt werden, momentan aber nicht benötigt werden. Idealerweise sollte der einfachste Code implementiert werden, der heute funktioniert, und anhand konstanter Refaktorierung sichergestellt werden, dass sich die Architektur des Systems mit den Anforderungen und der Zeit weiterentwickelt. Dies ermöglicht eine Konzentration auf das Wesentliche und verhindert das Aufblähen des Codes sowie das Einschleichen von Funktionen.
