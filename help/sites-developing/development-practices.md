---
title: Entwicklungspraktiken
description: Best Practices für die Entwicklung in Adobe Experience Manager.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: 65b2029e-03c9-4df4-8579-2b15dbee1035
source-git-commit: 9d497413d0ca72f22712581cf7eda1413eb8d643
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 44%

---

# Entwicklungspraktiken{#development-practices}

## Arbeiten nach einer Definition von Fertig (DoD) {#work-according-to-a-definition-of-done}

Jedes Team hat sein eigenes Verständnis davon, was „fertig“ bedeutet, aber es ist wichtig, eines zu haben und sicherzustellen, dass eine Story die definierten Kriterien erfüllt, bevor sie akzeptiert wird.

Einige häufig von Teams festgelegte Kriterien sind:

* Für die Formatierung überarbeiteter Code
* Kommentare/Javadoc hinzugefügt
* Erfüllt die erforderlichen Testabdeckung
* Übergibt Unit- und Integrationstests
* In der QS-Umgebung validiert
* Lokalisierung implementiert

Ohne ein klar definiertes DoD ist es einfach, in einer Situation zu landen, in der viele Dinge auf halbem Weg erledigt sind und nichts wirklich vollständig ist.

### Kodierungs- und Formatierungskonventionen definieren und einhalten {#define-and-adhere-to-coding-and-formatting-conventions}

Dinge wie Einzüge und Leerräume erscheinen möglicherweise nicht wichtig, aber korrekt formatierter Code trägt erheblich zur Lesbarkeit und Pflegeleichtigkeit bei. Konventionen sollten im Team abgesprochen und beim Programmieren befolgt werden.

### Auf hohe Testabdeckung abzielen  {#aim-for-high-test-coverage}

Je größer die Projektimplementierung wird, desto länger muss sie getestet werden. Ohne eine gute Testabdeckung kann das Testteam nicht skalieren und die Entwickler werden schließlich in Bugs begraben.

Entwickler sollten die Test Driven Development (TDD) praktizieren und fehlerhafte Komponententests vor dem Produktionscode schreiben, der ihre Anforderungen erfüllt. Die Qualitätssicherung sollte einen automatisierten Satz von Abnahmeprüfungen erstellen, um sicherzustellen, dass das System von einer hohen Ebene aus wie erwartet funktioniert.

Es stehen benutzerdefinierte Frameworks wie Jackalope und Prosper zur Verfügung, um die Nachahmung von JCR-APIs zu vereinfachen, um die Produktivität der Entwickler beim Schreiben von Komponententests sicherzustellen.

### Demo bereit halten {#stay-demo-ready}

Das System sollte am Ende jeder Iteration für Demos im Unternehmen zur Verfügung stehen. Indem das System immer bereit für Demos gehalten wird, ist das Team immer nur eine Iteration von Produktionsbereitschaft entfernt und technische Rückstände werden auf ein vertretbares Maß beschränkt.

### Kontinuierliche Integrationsumgebung implementieren und verwenden {#implement-a-continuous-integration-environment-and-use-it}

Durch die Implementierung einer kontinuierlichen Integrationsumgebung können Sie mühelos und wiederholt Unit-Tests und Integrationstests durchführen. Außerdem werden Bereitstellungen des Entwicklungsteams entkoppelt, sodass die anderen Teile des Teams effizienter werden und stabilere und berechenbarere Bereitstellungen möglich sind.

### Entwicklungszyklus durch niedrige Erstellungszeiten beschleunigen {#keep-the-development-cycle-fast-by-keeping-build-times-low}

Wenn Einheitstests zu viel Zeit beanspruchen, lassen Entwickler sie aus, wodurch sie ihren Wert verlieren. Wenn es viel Zeit in Anspruch nimmt, den Code zu erstellen und bereitzustellen, werden diese Aufgaben seltener durchgeführt. Die Festlegung kurzer Erstellungszeiten als Priorität stellt sicher, dass die Zeit, die Sie in die Testabdeckung und CI-Infrastruktur investiert haben, das Team produktiver macht.

### Optimieren Sie Sonar und andere statische Code-Analyse-Tools und reagieren Sie auf ihre Berichte. {#fine-tune-sonar-and-other-static-code-analysis-tools-and-act-on-their-reports}

Code-Analysewerkzeuge haben nur dann einen Wert, wenn ihre Berichte vom Entwickler-Team verwertet werden. Ohne eine Feinabstimmung der Analyse, die diese Instrumente bieten, werden die Empfehlungen, die sie generieren, irrelevant und verlieren ihren Wert.

### Der Pfadfinderregel folgen {#follow-the-boy-scout-rule}

Pfadfinder haben eine Regel: „Hinterlass es besser, als du es vorgefunden hast.“ Solange alle Mitglieder des Entwicklungsteams diese Regel befolgen und etwas bereinigen, wenn sie auf ein Chaos stoßen, wird sich der Code ständig verbessern.

### Implementierung von YAGNI-Funktionen vermeiden {#avoid-implementing-yagni-features}

YAGNI (You Are Not Gonna Need It) Features sind Dinge, die implementiert werden, wenn wir erwarten, dass wir etwas in der Zukunft brauchen, auch wenn wir es jetzt nicht benötigen. Idealerweise sollte der einfachste Code implementiert werden, der heute funktioniert, und anhand konstanter Refaktorierung sichergestellt werden, dass sich die Architektur des Systems mit den Anforderungen und der Zeit weiterentwickelt. Auf diese Weise können wir uns darauf konzentrieren, was wichtig ist, und verhindern, dass Code-Aufblasen und Funktionen umgehen.
