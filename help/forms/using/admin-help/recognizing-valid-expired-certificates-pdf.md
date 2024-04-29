---
title: Erkennen von gültigen und abgelaufenen Zertifikaten in PDF-Dokumenten
description: Erfahren Sie, wie Sie gültige und abgelaufene Zertifikate in PDF-Dokumenten erkennen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: dfe2823a-3a0d-4e45-8765-f618529e22dd
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '197'
ht-degree: 100%

---

# Erkennen von gültigen und abgelaufenen Zertifikaten in PDF-Dokumenten {#recognizing-valid-and-expired-certificates-in-pdf-documents}

Wird ein PDF-Dokument, dem über Reader Extensions Verwendungsrechte zugewiesen wurden, in Adobe Reader geöffnet, wird eine Statusleiste mit den spezifischen Verwendungsrechten angezeigt, die im PDF-Dokument aktiviert sind.

Wenn das digitale Zertifikat mit den für ein PDF-Dokument angegebenen Verwendungsrechten abläuft und das PDF-Dokument in Adobe Reader geöffnet wird, werden die Benutzenden über ein Dialogfeld darauf hingewiesen, dass das PDF-Dokument zwar Verwendungsrechte aufweist, diese jedoch deaktiviert sind. Diese Meldung besagt, dass das PDF-Dokument geändert oder manipuliert wurde. Dies muss jedoch nicht der Fall sein. Adobe Reader zeigt diese Meldung an, wenn das Zertifikat abläuft oder ein Dokument geändert wird. In Adobe Reader 7.0.x oder höher kann nicht festgestellt werden, welcher Fall gerade vorliegt.

Nachdem Sie das Dialogfeld geschlossen haben, öffnet Adobe Reader das PDF-Dokument. Die Verwendungsrechte, die mit den Acrobat Reader DC-Erweiterungen aktiviert wurden, sind wie erwartet nicht verfügbar. Wenn das PDF-Dokument ein interaktives Formular ist, sind die Formularfelder gesperrt, sodass Benutzende die Formulardaten nicht ändern können.
