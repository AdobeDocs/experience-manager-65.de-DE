---
title: Bereitstellung von großen Mengen geschützter Informationen
description: Die Dokumentensicherheit unterstützt in Massenproduktionsumgebungen die Zuordnung von Lizenzen zu Benutzenden anstatt zu Dokumenten.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Document Security
exl-id: 616e8821-ca96-4471-9120-0e1076a06178
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 92%

---

# Bereitstellung von großen Mengen geschützter Informationen {#high-volume-secure-information-delivery}

In einer Massenproduktionsumgebung, wie z. B. der Erstellung von geschützten monatlichen Rechnungen für ein Telecom-Unternehmen, kann das Erstellen von Lizenzen, die für jedes einzelne Dokument spezifisch sind, ein ressourcenintensiver Prozess werden. In solchen Fällen unterstützt die Dokumentensicherheit die Zuordnung von Lizenzen zu Benutzenden anstatt zu Dokumenten. Die für eine Person generierte Lizenz wird für alle Dokumente verwendet, die für diese Person geschützt sind.

Ein Vorteil dieses Ansatzes besteht darin, dass die Größe der Document Security-Datenbank nicht linear mit den Dokumenten wächst, sondern mit der Anzahl der Benutzer. Da Sie die Lizenz für eine Person nur einmal erstellen müssen, wird der anschließende Schutz von Dokumenten durch diese Richtlinien schneller. Funktionen wie Offline-Zugriff, Ablauf von Dokumenten und Widerruf werden für alle derartigen Dokumente unterstützt.

Die Dokumentensicherheit unterstützt auch abstrakte Richtlinien. Abstrakte Richtlinien sind Richtlinienvorlagen, die alle Richtlinienattribute wie Dokumentensicherheitseinstellungen und Nutzungsrechte beinhalten, jedoch keine Prinzipalliste. Admins können anhand der abstrakten Richtlinie eine beliebige Anzahl von Richtlinien mit verschiedenen Prinzipalen erstellen, die Zugriff auf die Dokumente haben. An der abstrakten Richtlinie vorgenommene Änderungen wirken sich nicht auf die Richtlinien aus, die anhand der abstrakten Richtlinie generiert wurden.

In dem Beispiel der monatlichen Rechnungserstellung für ein Telecom-Unternehmen erstellen Sie eine abstrakte Richtlinie, dann Benutzerinnen und Benutzer und schließlich eindeutige Lizenzen für jede Person. Die Lizenzen werden dann für jede Person auf Dokumente angewendet.

Das Erstellen einer abstrakten Richtlinie wird nur von Document Security Java SDK unterstützt. Sie können die Richtlinien, die Sie aus der abstrakten Richtlinie erstellt haben, allerdings auf den Web-Seiten zur Dokumentensicherheit verwalten. Richtlinien, die mit dieser Methode erstellt werden, sind im Verhalten mit denen identisch, die über Web-Seiten der Dokumentensicherheit erstellt werden.

Weitere Informationen finden Sie unter [Programmieren mit AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63_de).
