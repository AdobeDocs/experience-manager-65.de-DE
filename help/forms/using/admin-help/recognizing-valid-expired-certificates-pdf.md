---
title: Erkennen von gültigen und abgelaufenen Zertifikaten in PDF-Dokumenten
description: Erfahren Sie, wie Sie gültige und abgelaufene Zertifikate in PDF-Dokumenten erkennen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: dfe2823a-3a0d-4e45-8765-f618529e22dd
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 100%
---
# Erkennen von gültigen und abgelaufenen Zertifikaten in PDF-Dokumenten {#recognizing-valid-and-expired-certificates-in-pdf-documents}

Wird ein PDF-Dokument, dem über Reader Extensions Verwendungsrechte zugewiesen wurden, in Adobe Reader geöffnet, wird eine Statusleiste mit den spezifischen Verwendungsrechten angezeigt, die im PDF-Dokument aktiviert sind.

Wenn das digitale Zertifikat mit den für ein PDF-Dokument angegebenen Verwendungsrechten abläuft und das PDF-Dokument in Adobe Reader geöffnet wird, werden die Benutzenden über ein Dialogfeld darauf hingewiesen, dass das PDF-Dokument zwar Verwendungsrechte aufweist, diese jedoch deaktiviert sind. Diese Meldung besagt, dass das PDF-Dokument geändert oder manipuliert wurde. Dies muss jedoch nicht der Fall sein. Adobe Reader zeigt diese Meldung an, wenn das Zertifikat abläuft oder ein Dokument geändert wird. In Adobe Reader 7.0.x oder höher kann nicht festgestellt werden, welcher Fall gerade vorliegt.

Nachdem Sie das Dialogfeld geschlossen haben, öffnet Adobe Reader das PDF-Dokument. Die Verwendungsrechte, die mit den Acrobat Reader DC-Erweiterungen aktiviert wurden, sind wie erwartet nicht verfügbar. Wenn das PDF-Dokument ein interaktives Formular ist, sind die Formularfelder gesperrt, sodass Benutzende die Formulardaten nicht ändern können.
