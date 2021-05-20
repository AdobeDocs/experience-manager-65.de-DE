---
title: Bildschirmlesehilfen für HTML5-Formulare
seo-title: Bildschirmlesehilfen für HTML5-Formulare
description: Listet die in Verbindung mit HTML5-Formularen unterstützten Bildschirmlesehilfen auf.
seo-description: Listet die in Verbindung mit HTML5-Formularen unterstützten Bildschirmlesehilfen auf.
uuid: 035354e2-957f-4eb6-bc16-4ca96ec7ac74
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 53c57180-7004-4534-9146-603f7770a6fe
feature: Mobile Forms
exl-id: 07d20c2f-7d13-48ac-8d58-b367eb194558
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 84%

---

# Bildschirmlesehilfen für HTML5-Formulare {#screen-readers-for-html-forms}

HTML5-Formularkomponenten rendern XFA-Formularvorlagen in einem HTML5-Format. Diese Formulare können in allen Standardbrowsern wiedergegeben werden, die HTML5 unterstützen. Um ähnliche Datenerfassungsergebnisse bei allen PDF- und HTML5-Formularen zu erzielen, wird das Layout der PDF-Formulare in den HTML5-Formularen beibehalten.

HTML5-Formulare verwenden standardmäßige HTML-Konstrukte, sodass für diese Formulare barrierefreie HTML-Anwendungen verwendet werden können. Wenn ein Formular nach den bewährten Verfahren für barrierefreie Formulare entworfen wurde, funktioniert er mit jeder unterstützten Bildschirmlesehilfe. Zusätzlich bieten diese Formulare die Option der Tastaturnavigation.

## Barrierefreiheitsstandards {#accessibility-standards}

HTML5-Formulare erfüllen Abschnitt 508 für Barrierefreiheit mit bekannten Ausnahmen. Ausführliche Informationen finden Sie in [VPAT für HTML5-Forms](https://www.adobe.com/mena_en/accessibility/compliance/livecycle-mobile-forms-es4-section-508-vpat.html).

## Zertifizierte Bildschirmlesehilfen für HTML5-Formulare {#certified-screen-readers-for-html-forms}

* JAWS 14.0 unter Microsoft Windows
* VoiceOver unter Mac OS X und auf iPad

### JAWS {#jaws}

In HTML5-Formularen funktionieren alle standardmäßigen Tasteneingaben und Tastaturbefehle. Weitere Informationen zur Verwendung von JAWS finden Sie unter [https://www.freedomscientific.com/jaws-hq.asp](https://www.freedomscientific.com/jaws-hq.asp).

### VoiceOver {#voiceover}

HTML5-Formulare unterstützen alle Standard-Tasteneingaben und Gesten für VoiceOver. Weitere Informationen zum Einrichten und Verwenden von VoiceOver finden Sie unter [https://www.apple.com/accessibility/voiceover/](https://www.apple.com/accessibility/voiceover/).

## Bekannte Probleme {#known-issues}

* **(Nur Internet Explorer 9)** In HTML5-Formularen werden die Seiten bei Bedarf geladen (dynamisch). Das Laden von Seiten bei Bedarf verursacht Probleme mit Bildschirmlesehilfen. Wenn der Fokus der Bildschirmlesehilfe am letzten Seitenfeld angelangt ist und der Benutzer die Tabulator-Taste drückt, statt den Fokus auf das erste Feld der nächsten Seite zu legen, kehrt die Bildschirmlesehilfe auf das erste Feld der ersten Seite des Formulars zurück.
* **(Ausschließlich Internet Explorer 9)** Das Datumsauswahl-Steuerelement in HTML5-Formularen lässt sich nicht vollständig über die Tastatur steuern. Wenn Sie im Datumsauswahl -Steuerelement die Bild-Auf/Bild-Ab-Tasten mehrmals hintereinander drücken, wird das Datumsauswahl-Steuerelement geschlossen und der Fokus wird auf das nächste/letzte Feld gerichtet.

* VoiceOver kann Pfeiltasten auf dem Datumswidget auf iPad Safari nicht erkennen.
