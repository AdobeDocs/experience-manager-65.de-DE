---
title: Entwicklungspraktiken
description: Best Practices für die Entwicklung mit Adobe Experience Manager.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: 65b2029e-03c9-4df4-8579-2b15dbee1035
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 94%

---

# Entwicklungspraktiken{#development-practices}

## Arbeiten nach einer Definition of Done (DoD) {#work-according-to-a-definition-of-done}

Jedes Team hat sein eigenes Verständnis davon, was „fertig“ bedeutet, aber es ist wichtig, eines zu haben und sicherzustellen, dass eine Story die definierten Kriterien erfüllt, bevor sie akzeptiert wird.

Zu den Kriterien, die häufig von Teams festgelegt werden, gehören:

* Code auf Formatierung überprüft
* Kommentare/Javadoc hinzugefügt
* Erfüllt die erforderlichen Testabdeckungsniveaus
* Besteht Unit- und Integrationstests
* Validiert in der QS-Umgebung
* Lokalisierung implementiert

Ohne ein klar definiertes DoD kann es leicht passieren, dass viele Dinge zur Hälfte erledigt sind und nichts wirklich abgeschlossen ist.

### Definieren und Befolgen von Kodierungs- und Formatierungskonventionen {#define-and-adhere-to-coding-and-formatting-conventions}

Dinge wie Einzüge und Leerräume erscheinen möglicherweise nicht wichtig, aber korrekt formatierter Code trägt erheblich zur Lesbarkeit und Pflegeleichtigkeit bei. Konventionen sollten im Team abgesprochen und beim Programmieren befolgt werden.

### Auf hohe Testabdeckung abzielen  {#aim-for-high-test-coverage}

Je größer eine Projektimplementierung wird, desto mehr Zeit ist auch erforderlich, um sie zu testen. Ohne entsprechende Testabdeckung kann das Test-Team nicht skalieren und die Entwickelnden kommen irgendwann vor lauter Bugs nicht mehr hinterher.

Entwickelnde sollten Test Driven Development (TDD) praktizieren und fehlschlagende Einheitstests vor dem Produktions-Code schreiben, der ihre Anforderungen erfüllt. Die Qualitätssicherung sollte einen automatisierten Satz von Abnahmeprüfungen erstellen, um sicherzustellen, dass das System von einer hohen Ebene aus wie erwartet funktioniert.

Es stehen benutzerdefinierte Frameworks wie Jackalope und Prosper zur Verfügung, um das Mocking von JCR-APIs zu vereinfachen und die Produktivität der Entwickelnden beim Schreiben von Einheitstests sicherzustellen.

### Für Demos bereithalten {#stay-demo-ready}

Das System sollte am Ende jeder Iteration für Demos im Unternehmen zur Verfügung stehen. Indem das System immer bereit für Demos gehalten wird, ist das Team immer nur eine Iteration von Produktionsbereitschaft entfernt und technische Rückstände werden auf ein vertretbares Maß beschränkt.

### Kontinuierliche Integrationsumgebung implementieren und verwenden {#implement-a-continuous-integration-environment-and-use-it}

Das Implementieren einer kontinuierlichen Integrationsumgebung ermöglicht das einfache und wiederholte Durchführen von Einheits- und Integrationstests. Außerdem werden so Bereitstellungen vom Entwicklungs-Team entkoppelt, was andere Teile des Teams effizienter und Bereitstellungen stabiler sowie vorhersehbarer macht.

### Entwicklungszyklus durch niedrige Erstellungszeiten beschleunigen {#keep-the-development-cycle-fast-by-keeping-build-times-low}

Wenn Einheitstests zu viel Zeit beanspruchen, lassen Entwickler sie aus, wodurch sie ihren Wert verlieren. Wenn es viel Zeit in Anspruch nimmt, den Code zu erstellen und bereitzustellen, werden diese Aufgaben seltener durchgeführt. Indem Sie kurze Erstellungszeiten zur Priorität machen, wird sichergestellt, dass die Zeit, die Sie in die Testabdeckung und CI-Infrastruktur investiert haben, weiterhin der Produktivität des Teams zugutekommt.

### Optimieren von „Sonar“ sowie anderen statischen Codeanalysewerkzeugen und Verwerten ihrer Berichte {#fine-tune-sonar-and-other-static-code-analysis-tools-and-act-on-their-reports}

Code-Analysewerkzeuge haben nur dann einen Wert, wenn ihre Berichte vom Entwickler-Team auch verwertet werden. Ohne die Optimierung der Analysen, die diese Tools bieten, sind die generierten Empfehlungen nicht relevant und verlieren ihren Wert.

### Der Pfadfinderregel folgen {#follow-the-boy-scout-rule}

Pfadfinder haben eine Regel: „Hinterlass es besser, als du es vorgefunden hast.“ Sofern sich alle Mitglieder des Entwicklungs-Teams an diese Regel halten und eine Verbesserung vornehmen, wenn sie einen Fehler sehen, wird der Code konstant verbessert. 

### Implementierung von YAGNI-Funktionen vermeiden {#avoid-implementing-yagni-features}

YAGNI (You Are Not Gonna Need It) Features sind Dinge, die implementiert werden, wenn wir erwarten, dass wir etwas in der Zukunft brauchen, auch wenn wir es jetzt nicht benötigen. Idealerweise sollte der einfachste Code implementiert werden, der heute funktioniert, und anhand konstanter Refaktorierung sichergestellt werden, dass sich die Architektur des Systems mit den Anforderungen und der Zeit weiterentwickelt. Dies ermöglicht eine Konzentration auf das Wesentliche und verhindert, dass der Code aufgebläht wird und die Funktionen überhandnehmen.
