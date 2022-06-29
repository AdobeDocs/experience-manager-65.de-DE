---
title: Gültige und abgelaufene Zertifikate in PDF-Dokumenten erkennen
seo-title: Recognizing valid and expired certificates in PDF documents
description: Erfahren Sie, wie Sie gültige und abgelaufene Zertifikate in PDF-Dokumenten erkennen.
seo-description: Learn how to recognize valid and expired certificates in PDF documents.
uuid: ceeff57a-586f-4f7b-852f-2a637f003d7e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 4559218a-65ba-4577-ad26-7721e28971bc
exl-id: dfe2823a-3a0d-4e45-8765-f618529e22dd
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '198'
ht-degree: 100%

---

# Gültige und abgelaufene Zertifikate in PDF-Dokumenten erkennen {#recognizing-valid-and-expired-certificates-in-pdf-documents}

Wird ein PDF-Dokument, dem über Reader Extensions Verwendungsrechte zugewiesen wurden, in Adobe Reader geöffnet, wird eine Statusleiste mit den spezifischen Verwendungsrechten angezeigt, die im PDF-Dokument aktiviert sind.

Wird das digitale Zertifikat, das die Verwendungsrechte für ein PDF-Dokument angibt, abläuft und das PDF-Dokument in Adobe Reader geöffnet, wird ein Dialogfeld mit der Meldung angezeigt, dass das PDF-Dokument Verwendungsrechte aufweist, die jedoch deaktiviert sind. In dieser Meldung wird angegeben, dass das PDF-Dokument geändert oder verfälscht wurde; dies ist jedoch nicht unbedingt der Fall. Adobe Reader zeigt diese Meldung an, wenn das Zertifikat abläuft oder ein Dokument geändert wird. In Adobe Reader 7.0.x oder höher kann nicht festgestellt werden, welcher Fall gerade vorliegt.

Nachdem Sie das Dialogfeld geschlossen haben, öffnet Adobe Reader das PDF-Dokument. Die Verwendungsrechte, die mit Acrobat Reader DC Extensions aktiviert wurden, sind wie erwartet nicht verfügbar. Wenn das PDF-Dokument ein interaktives Formular ist, sind die Formularfelder gesperrt, sodass der Benutzer die Formulardaten nicht ändern kann.
