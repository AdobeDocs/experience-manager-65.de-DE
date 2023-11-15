---
title: Erkennen von gültigen und abgelaufenen Zertifikaten in PDF-Dokumenten
description: Erfahren Sie, wie Sie gültige und abgelaufene Zertifikate in PDF-Dokumenten erkennen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: dfe2823a-3a0d-4e45-8765-f618529e22dd
source-git-commit: 7f35fdee9dbca9dfd3992b56579d6d06633f8dec
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 8%

---

# Erkennen von gültigen und abgelaufenen Zertifikaten in PDF-Dokumenten {#recognizing-valid-and-expired-certificates-in-pdf-documents}

Wenn in Adobe Reader ein PDF-Dokument geöffnet wird, auf das von Reader Extensions Verwendungsrechte angewendet werden, wird eine Statusleiste angezeigt, in der die spezifischen Verwendungsrechte beschrieben werden, die im PDF-Dokument aktiviert sind.

Wenn das digitale Zertifikat, das die Verwendungsrechte für ein PDF-Dokument angibt, abläuft und das PDF-Dokument in Adobe Reader geöffnet wird, wird der Benutzer über ein Dialogfeld darauf hingewiesen, dass das PDF-Dokument über Verwendungsrechte verfügt, diese Rechte jedoch deaktiviert sind. Obwohl die Meldung darauf hinweist, dass das PDF-Dokument geändert oder manipuliert wurde, ist dies nicht unbedingt der Fall. Adobe Reader zeigt diese Meldung an, wenn ein Zertifikat abläuft oder ein Dokument geändert wird. In Adobe Reader 7.0.x oder höher können Sie nicht feststellen, welcher Fall derzeit das Problem ist.

Nachdem Sie das Dialogfeld geschlossen haben, öffnet Adobe Reader das PDF-Dokument. Die Verwendungsrechte, die mit Acrobat Reader DC-Erweiterungen angewendet wurden, sind nicht wie erwartet verfügbar. Wenn es sich beim PDF-Dokument um ein interaktives Formular handelt, sind die Formularfelder gesperrt und der Benutzer kann die Formulardaten nicht ändern.
