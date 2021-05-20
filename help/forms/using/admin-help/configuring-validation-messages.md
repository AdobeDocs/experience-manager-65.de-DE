---
title: Überprüfungsmeldungen konfigurieren
seo-title: Überprüfungsmeldungen konfigurieren
description: Erfahren Sie, wie Sie angeben, wie die Validierungsnachrichten und deren Position relativ zum im Webbrowser zurückgegebenen Formular angezeigt werden.
seo-description: Erfahren Sie, wie Sie angeben, wie die Validierungsnachrichten und deren Position relativ zum im Webbrowser zurückgegebenen Formular angezeigt werden.
uuid: f6bff4fa-f90f-4135-ae40-7ab3d3613122
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 5f2f8129-e45e-4f3f-ae30-c09330d0e152
exl-id: 14314383-5228-4904-98c1-586f48a1142c
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 100%

---

# Überprüfungsmeldungen konfigurieren {#configuring-validation-messages}

Für Formulare, die als HTML wiedergegeben werden, werden Formular-Überprüfungsfehler für den Benutzer angezeigt. Sie können die Darstellung von Überprüfungsmeldungen anpassen. In Abhängigkeit davon, wo die Überprüfungsmeldungen angezeigt werden, können Sie auch die Position der Meldung im Formular sowie die Rahmenstärke steuern.

## Angeben, wie Überprüfungsmeldungen angezeigt werden {#specify-how-validation-messages-are-displayed}

1. Klicken Sie in Administration Console auf „Dienste“ > „Forms“.
1. Wählen Sie unter „Überprüfungsausgabe“ in der Liste „Berichte“ eine der folgenden Optionen aus:

   **Meldungsfeld**, um Überprüfungsmeldungen in einem gesonderten Dialogfeld anzuzeigen.

   **Frame**, um Überprüfungsmeldungen in einem Rahmen desselben Fensters anzuzeigen.

   **Kein Frame**, um Überprüfungsmeldungen im selben Fenster anzuzeigen. Dies ist der Standardwert.

   **Per API (mit Daten)**, um die Überprüfungsmeldungen über die API zurückzugeben (mit Daten). Die Überprüfungsmeldungen werden nicht auf dem Bildschirm angezeigt.

   **Per API (mit Formular)**, um die Überprüfungsmeldungen über die API zurückzugeben (mit dem Formular). Die Überprüfungsmeldungen werden nicht auf dem Bildschirm angezeigt.

   **Ohne**, um keine Überprüfungsmeldungen anzuzeigen.

1. Klicken Sie auf Speichern.

## Die Position der Überprüfungsmeldungen relativ zum im Webbrowser zurückgegebenen Formular angeben  {#specify-the-location-of-validation-messages-relative-to-the-form-returned-in-the-web-browser}

Wenn „Berichte“ auf „Frame“ oder „Kein Frame“ festgelegt ist, können Sie die Position der Überprüfungsmeldungen angeben.

1. Wählen Sie unter „Überprüfungsausgabe“ in der Liste „Position“ eine der folgenden Optionen aus:

   **Links**, um Überprüfungsmeldungen in der linken Hälfte des Webbrowsers anzuzeigen.

   **Rechts**, um Überprüfungsmeldungen in der rechten Hälfte des Webbrowsers anzuzeigen.

   **Oben**, um Überprüfungsmeldungen oben im Webbrowser anzuzeigen. Dies ist der Standardwert.

   **Unten**, um Überprüfungsmeldungen unten im Webbrowser anzuzeigen.

1. Klicken Sie auf Speichern.

## Die Rahmenstärke angeben  {#specify-the-frame-border-size}

Wenn „Berichte“ auf „Frame“ festgelegt ist, können Sie die Rahmenstärke angeben.

1. Geben Sie unter „Überprüfungsausgabe“ im Feld „Rahmenstärke“ die Stärke des Rahmens in Pixel ein.

   Die Rahmenstärke muss gleich oder größer 0 sein. Der Standardwert ist 1.

1. Klicken Sie auf Speichern.
