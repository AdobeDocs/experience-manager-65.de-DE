---
title: Bereitstellung von großen Mengen geschützter Informationen
seo-title: High-volume secure information delivery
description: In solchen Fällen unterstützt Document Security die Zuordnung von Lizenzen zu Benutzern anstatt zu Dokumenten.
seo-description: Document security supports the association of licenses to users, rather than to the documents in mass production environments.
uuid: 9747d283-506c-434e-9850-e50b95290cc8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: b76d7d93-23a5-4c08-81f5-a56267b1556a
feature: Document Security
exl-id: 616e8821-ca96-4471-9120-0e1076a06178
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '324'
ht-degree: 100%

---

# Bereitstellung von großen Mengen geschützter Informationen {#high-volume-secure-information-delivery}

In einer Massenproduktionsumgebung, wie z. B. der Erstellung von geschützten monatlichen Rechnungen für ein Telecom-Unternehmen, kann das Erstellen von für jedes einzelne Dokument spezifischen Lizenzen ein ressourcenintensiver Prozess werden. In solchen Fällen unterstützt Document Security die Zuordnung von Lizenzen zu Benutzern anstatt zu Dokumenten. Die für einen Benutzer generierte Lizenz wird für alle Dokumente verwendet, die für den Benutzer geschützt werden.

Ein Vorteil dieser Vorgehensweise besteht darin, dass die Größe der Document Security-Datenbank nicht linear mit den Dokumenten anwächst, sondern mit der Anzahl der Benutzer. Da Sie die Lizenz für einen Benutzer nur einmal erstellen müssen, wird der anschließende Schutz von Dokumenten durch diese Richtlinien schneller. Funktionen wie Offlinezugriff, Ablauf von Dokumenten und Rücknahme werden für alle derartigen Dokumente unterstützt.

Document Security unterstützt auch abstrakte Richtlinien. Abstrakte Richtlinien ist Richtlinienvorlagen, die alle Richtlinienattribute wie Dokumentsicherheitseinstellungen und Verwendungsrechte beinhalten, jedoch keine Prinzipalliste. Die Administratoren können eine beliebige Anzahl Richtlinien anhand der abstrakten Richtlinie mit verschiedenen Prinzipalen erstellen, die Zugriff auf die Dokumente haben. Die Änderungen, die an der abstrakten Richtlinie vorgenommen wurden, wirken sich nicht auf die Richtlinien aus, die anhand der abstrakten Richtlinie generiert wurden.

In dem Beispiel der monatlichen Rechnungserstellung für ein Telecom-Unternehmen erstellen Sie eine abstrakte Richtlinie, erstellen Benutzer und dann eindeutige Lizenzen für jeden Benutzer. Die Lizenzen werden dann für jeden Benutzer auf Dokumente angewendet.

Das Erstellen einer abstrakten Richtlinie wird nur von Document Security Java SDK unterstützt. Sie können die Richtlinien, die Sie aus der abstrakten Richtlinie erstellt haben, allerdings auf den Document Security-Webseiten verwalten. Richtlinien, die mit dieser Methode erstellt werden, sind im Verhalten mit denen identisch, die über die Document Security-Webseiten erstellt werden.

Weitere Informationen finden Sie unter [Programmieren mit AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63_de).
