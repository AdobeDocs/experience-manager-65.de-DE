---
title: Bereitstellung von großen Mengen geschützter Informationen
description: Document Security unterstützt die Zuordnung von Lizenzen zu Benutzern und nicht zu Dokumenten in Massenproduktionsumgebungen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Document Security
exl-id: 616e8821-ca96-4471-9120-0e1076a06178
source-git-commit: 9d497413d0ca72f22712581cf7eda1413eb8d643
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 5%

---

# Bereitstellung von großen Mengen geschützter Informationen {#high-volume-secure-information-delivery}

In einer Massenproduktionsumgebung, z. B. bei der Erstellung gesicherter monatlicher Rechnungen für ein Telekommunikationsunternehmen, kann die Erstellung von Lizenzen, die für jedes Dokument spezifisch sind, zu einem ressourcenintensiven Prozess werden. In solchen Fällen unterstützt Document Security die Zuordnung von Lizenzen zu Benutzern und nicht zu Dokumenten. Die für einen Benutzer generierte Lizenz wird für alle Dokumente verwendet, die für diesen Benutzer geschützt sind.

Ein Vorteil dieses Ansatzes besteht darin, dass die Größe der Document Security-Datenbank nicht linear mit den Dokumenten wächst, sondern mit der Anzahl der Benutzer. Da Sie die Lizenz nur einmal für einen Benutzer erstellen müssen, wird der anschließende Schutz von Dokumenten durch diese Richtlinien schneller. Funktionen wie Offline-Zugriff, Ablauf von Dokumenten und Sperrung werden für alle diese Dokumente unterstützt.

Document Security unterstützt auch abstrakte Richtlinien. Abstrakte Richtlinien sind Richtlinienvorlagen, die alle Richtlinienattribute wie Document Security-Einstellungen und Verwendungsrechte enthalten, jedoch keine Liste von Prinzipalen enthalten. Administratoren können eine beliebige Anzahl von Richtlinien aus der abstrakten Richtlinie mit verschiedenen Prinzipalen erstellen, die Zugriff auf die Dokumente haben sollten. Änderungen an der abstrakten Richtlinie wirken sich nicht auf die tatsächlichen Richtlinien aus, die aus den abstrakten Richtlinien generiert werden.

Wenn für ein Telekommunikationsunternehmen eine monatliche Rechnungserstellung erfolgt, erstellen Sie eine abstrakte Richtlinie, erstellen Benutzer und generieren dann eindeutige Lizenzen für jeden Benutzer. Die Lizenzen werden später für jeden Benutzer auf Dokumente angewendet.

Die Erstellung einer abstrakten Richtlinie wird nur über das Document Security Java SDK unterstützt. Sie können jedoch die Richtlinien, die Sie aus der abstrakten Richtlinie erstellen, auf den Document Security-Webseiten verwalten. Richtlinien, die mit dieser Methode erstellt werden, sind im Verhalten mit denen identisch, die von Document Security-Webseiten erstellt wurden.

Weitere Informationen finden Sie unter [Programmieren mit AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63_de).
