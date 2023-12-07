---
title: Konfigurieren der Überprüfungsmeldungen
description: Erfahren Sie, wie Sie angeben, wie Überprüfungsmeldungen angezeigt werden und wo sie sich im Verhältnis zum im Webbrowser zurückgegebenen Formular befinden.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 14314383-5228-4904-98c1-586f48a1142c
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 4%

---

# Konfigurieren der Überprüfungsmeldungen {#configuring-validation-messages}

Bei Formularen, die als HTML wiedergegeben werden, werden Fehler bei der Formularüberprüfung für den Benutzer angezeigt. Sie können die Anzeige von Validierungsmeldungen anpassen. Je nachdem, wo die Überprüfungsmeldungen angezeigt werden, können Sie auch die Position der Nachricht im Formular und die Größe des Rahmenrahmens steuern.

## Angeben, wie Überprüfungsmeldungen angezeigt werden {#specify-how-validation-messages-are-displayed}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Forms&quot;.
1. Wählen Sie unter &quot;Überprüfungsausgabe&quot;in der Liste &quot;Berichte&quot;eine der folgenden Optionen aus:

   **Meldungsfeld:** So zeigen Sie Überprüfungsmeldungen in einem separaten Dialogfeld an.

   **Frame:** Zum Anzeigen von Überprüfungsmeldungen innerhalb eines Rahmens desselben Fensters.

   **Kein Frame:** So zeigen Sie Überprüfungsmeldungen im selben Fenster an. Dieser Wert ist der Standardwert.

   **Über API (mit Daten):** So geben Sie die Validierungsmeldungen über die API (mit Daten) zurück. Die Überprüfungsmeldungen werden nicht auf dem Bildschirm angezeigt.

   **Über API (mit Formular):** So geben Sie die Überprüfungsmeldungen über die API (mit dem Formular) zurück. Die Überprüfungsmeldungen werden nicht auf dem Bildschirm angezeigt.

   **Keine:** So zeigen Sie keine Überprüfungsmeldungen an.

1. Klicken Sie auf Speichern.

## Geben Sie den Speicherort der Überprüfungsmeldungen relativ zum im Webbrowser zurückgegebenen Formular an {#specify-the-location-of-validation-messages-relative-to-the-form-returned-in-the-web-browser}

Wenn &quot;Berichterstellung&quot;auf &quot;Frame&quot;oder &quot;Kein Frame&quot;festgelegt ist, können Sie den Speicherort der Überprüfungsmeldungen angeben.

1. Wählen Sie unter &quot;Überprüfungsausgabe&quot;in der Liste &quot;Position&quot;eine der folgenden Optionen aus:

   **Links:** Zum Anzeigen von Validierungsmeldungen auf der linken Seite des Webbrowsers.

   **Rechts:** Zum Anzeigen von Validierungsmeldungen auf der rechten Seite des Webbrowsers.

   **Oben**: So zeigen Sie Überprüfungsmeldungen oben im Webbrowser an. Dieser Wert ist der Standardwert.

   **Unten**: Zum Anzeigen von Validierungsmeldungen am unteren Rand des Webbrowsers.

1. Klicken Sie auf Speichern.

## Festlegen der Rahmenrahmengröße {#specify-the-frame-border-size}

Wenn für die Berichterstellung &quot;Frame&quot;festgelegt ist, können Sie die Rahmenrahmengröße angeben.

1. Geben Sie unter &quot;Überprüfungsausgabe&quot;im Feld &quot;Rahmengröße&quot;die Größe des Rahmenrahmens in Pixel ein.

   Die Rahmengröße muss größer/gleich 0 sein. Der Standardwert ist 1.

1. Klicken Sie auf Speichern.
