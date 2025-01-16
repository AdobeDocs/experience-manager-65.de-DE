---
title: Implementieren einer React-Komponente für SPAs
description: In diesem Artikel wird ein Beispiel dafür vorgestellt, wie eine einfache, vorhandene React-Komponente für den Adobe Experience Manager(AEM)-SPA-Editor angepasst werden kann.
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
docset: aem65
exl-id: f4959c12-54c5-403a-9973-7a4ab5f16bed
solution: Experience Manager, Experience Manager Sites
feature: Developing,SPA Editor
role: Developer
source-git-commit: 6d961456e0e1f7a26121da9be493308a62c53e04
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 100%

---


# Implementieren einer React-Komponente für SPAs {#implementing-a-react-component-for-spa}

Single Page Applications (SPAs) können Nutzerinnen und Nutzern von Websites ein überzeugendes Erlebnis bieten. Entwicklerinnen und Entwickler möchten in der Lage sein, Sites mithilfe von SPA-Frameworks zu erstellen. Autorinnen und Autoren möchten wiederum Inhalte innerhalb von Adobe Experience Manager (AEM) für eine mit SPA-Frameworks erstellte Site nahtlos bearbeiten können.

Die SPA-Autorenfunktion bietet eine umfassende Lösung zur Unterstützung von SPAs in AEM. In diesem Artikel wird ein Beispiel dafür vorgestellt, wie eine einfache, vorhandene React-Komponente für die Verwendung mit dem AEM-SPA-Editor angepasst werden kann.

{{ue-over-spa}}

## Einführung {#introduction}

Dank des simplen und übersichtlichen Kontrakts, den AEM verlangt und der zwischen der SPA und dem SPA-Editor eingerichtet wird, ist es einfach, eine vorhandene JavaScript-Anwendung zu verwenden und sie für die Verwendung mit einer SPA in AEM anzupassen.

Dieser Artikel veranschaulicht das Beispiel der Wetterkomponente in der Beispiel-SPA „We.Retail Journal“.

Sie sollten mit der [Struktur einer SPA für AEM](/help/sites-developing/spa-getting-started-react.md) vor dem Lesen dieses Artikels vertraut sein.

>[!CAUTION]
>In diesem Dokument dient die [We.Retail Journal-App](https://github.com/adobe/aem-sample-we-retail-journal) ausschließlich zu Demonstrationszwecken. Verwenden Sie sie nicht für Projektaufgaben.
>
>Für jedes AEM-Projekt sollte der [AEM-Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) genutzt werden, der SPA-Projekte mithilfe von React oder Angular unterstützt und das SPA-SDK verwendet.

## Die Wetterkomponente {#the-weather-component}

Die Wetterkomponente befindet sich oben links in der We.Retail Journal-App. Sie zeigt das aktuelle Wetter einer definierten Position an, wobei Wetterdaten dynamisch abgerufen werden.

### Verwenden des Wetter-Widgets {#using-the-weather-widget}

![screen_shot_2018-06-08at143224](assets/screen_shot_2018-06-08at143224.png)

Beim Bearbeiten von SPA-Inhalten im SPA-Editor wird die Wetterkomponente wie jede andere AEM-Komponente angezeigt: Sie weist eine Symbolleiste auf und kann bearbeitet werden.

![screen_shot_2018-06-08at143304](assets/screen_shot_2018-06-08at143304.png)

Die Stadt kann in einem Dialogfeld wie bei anderen AEM-Komponenten aktualisiert werden.

![screen_shot_2018-06-08at143446](assets/screen_shot_2018-06-08at143446.png)

Die Änderung wird gespeichert und die Komponente wird automatisch mit neuen Wetterdaten aktualisiert.

![screen_shot_2018-06-08at143524](assets/screen_shot_2018-06-08at143524.png)

### Implementierung der Wetterkomponente {#weather-component-implementation}

Die Wetterkomponente basiert auf einer öffentlich verfügbaren React-Komponente namens [React Open Weather](https://www.npmjs.com/package/react-open-weather). Sie wurde so angepasst, dass sie als Komponente in der Beispiel-SPA „We.Retail Journal“ verwendet werden kann.

Im Folgenden finden Sie Ausschnitte aus der NPM-Dokumentation zur Verwendung der Komponente „React Open Weather“.

![screen_shot_2018-06-08at144723](assets/screen_shot_2018-06-08at144723.png) ![screen_shot_2018-06-08at144215](assets/screen_shot_2018-06-08at144215.png)

Überprüfen des Codes der angepassten Wetterkomponente (`Weather.js`) in der We.Retail Journal-App:

* **Zeile 16**: Das Widget „React Open Weather“ wird nach Bedarf geladen.
* **Zeile 46**: Die Funktion `MapTo` verknüpft diese React-Komponente mit einer entsprechenden AEM-Komponente, sodass sie im SPA-Editor bearbeitet werden kann.

* **Zeilen 22–29**: `EditConfig` wird definiert und überprüft, ob die Stadt ausgefüllt wurde. Der Wert wird definiert, wenn er leer ist.

* **Zeilen 31–44**: Die Wetterkomponente erweitert die Klasse `Component` und stellt die erforderlichen Daten bereit, wie in der NPM-Nutzungsdokumentation für die Komponente „React Open Weather“ definiert. Dann wird die Komponente gerendert.

```javascript
/*~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 ~ Copyright 2018 Adobe Systems Incorporated
 ~
 ~ Licensed under the Apache License, Version 2.0 (the "License");
 ~ you may not use this file except in compliance with the License.
 ~ You may obtain a copy of the License at
 ~
 ~     https://www.apache.org/licenses/LICENSE-2.0
 ~
 ~ Unless required by applicable law or agreed to in writing, software
 ~ distributed under the License is distributed on an "AS IS" BASIS,
 ~ WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 ~ See the License for the specific language governing permissions and
 ~ limitations under the License.
 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
import React, {Component} from 'react';
import ReactWeather from 'react-open-weather';
import {MapTo} from '@adobe/aem-react-editable-components';

require('./Weather.css');

const WeatherEditConfig = {

    emptyLabel: 'Weather',

    isEmpty: function() {
        return !this.props || !this.props.cq_model || !this.props.cq_model.city || this.props.cq_model.city.trim().length < 1;
    }
};

class Weather extends Component {

    render() {
        let apiKey = "12345678901234567890";
        let city;

        if (this.props.cq_model) {
            city = this.props.cq_model.city;
            return <ReactWeather key={'react-weather' + Date.now()} forecast="today" apikey={apiKey} type="city" city={city} />
        }

        return null;
    }
}

MapTo('we-retail-journal/global/components/weather')(Weather, WeatherEditConfig);
```

Obwohl eine Backend-Komponente bereits vorhanden sein muss, kann das Frontend-Entwickler-Team die Komponente „React Open Weather“ in der We.Retail Journal-SPA bei geringem Programmieraufwand nutzen.

## Nächster Schritt {#next-step}

Weitere Informationen zur Entwicklung von SPAs für AEM finden Sie im Artikel [Entwickeln von SPAs für AEM](/help/sites-developing/spa-architecture.md).
