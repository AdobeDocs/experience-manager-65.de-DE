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
role: User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 50158d81-1c06-57f7-8bd7-e8ff76a93f85
    internal-label: Document Security
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 100%
---
# Bereitstellung von großen Mengen geschützter Informationen {#high-volume-secure-information-delivery}

In einer Massenproduktionsumgebung, wie z. B. der Erstellung von geschützten monatlichen Rechnungen für ein Telecom-Unternehmen, kann das Erstellen von Lizenzen, die für jedes einzelne Dokument spezifisch sind, ein ressourcenintensiver Prozess werden. In solchen Fällen unterstützt die Dokumentensicherheit die Zuordnung von Lizenzen zu Benutzenden anstatt zu Dokumenten. Die für eine Person generierte Lizenz wird für alle Dokumente verwendet, die für diese Person geschützt sind.

Ein Vorteil dieser Vorgehensweise besteht darin, dass die Größe der Dokumentensicherheits-Datenbank nicht linear mit der Anzahl der Dokumente anwächst, sondern mit der Anzahl der Benutzenden. Da Sie die Lizenz für eine Person nur einmal erstellen müssen, wird der anschließende Schutz von Dokumenten durch diese Richtlinien schneller. Funktionen wie Offline-Zugriff, Ablauf von Dokumenten und Widerruf werden für alle derartigen Dokumente unterstützt.

Die Dokumentensicherheit unterstützt auch abstrakte Richtlinien. Abstrakte Richtlinien sind Richtlinienvorlagen, die alle Richtlinienattribute wie Dokumentensicherheitseinstellungen und Nutzungsrechte beinhalten, jedoch keine Prinzipalliste. Admins können anhand der abstrakten Richtlinie eine beliebige Anzahl von Richtlinien mit verschiedenen Prinzipalen erstellen, die Zugriff auf die Dokumente haben. An der abstrakten Richtlinie vorgenommene Änderungen wirken sich nicht auf die Richtlinien aus, die anhand der abstrakten Richtlinie generiert wurden.

In dem Beispiel der monatlichen Rechnungserstellung für ein Telecom-Unternehmen erstellen Sie eine abstrakte Richtlinie, dann Benutzerinnen und Benutzer und schließlich eindeutige Lizenzen für jede Person. Die Lizenzen werden dann für jede Person auf Dokumente angewendet.

Das Erstellen einer abstrakten Richtlinie wird nur von Document Security Java SDK unterstützt. Sie können die Richtlinien, die Sie aus der abstrakten Richtlinie erstellt haben, allerdings auf den Web-Seiten zur Dokumentensicherheit verwalten. Richtlinien, die mit dieser Methode erstellt werden, sind im Verhalten mit denen identisch, die über Web-Seiten der Dokumentensicherheit erstellt werden.

Weitere Informationen finden Sie unter [Programmieren mit AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63_de).
