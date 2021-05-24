---
title: Implementieren einer Reaktionskomponente für SPA
seo-title: Implementieren einer Reaktionskomponente für SPA
description: In diesem Artikel wird ein Beispiel dafür vorgestellt, wie eine einfache, vorhandene React-Komponente für die Verwendung mit dem AEM-SPA-Editor angepasst werden kann.
seo-description: In diesem Artikel wird ein Beispiel dafür vorgestellt, wie eine einfache, vorhandene React-Komponente für die Verwendung mit dem AEM-SPA-Editor angepasst werden kann.
uuid: ae6a0a6f-0c3c-4820-9b58-c2a85a9f5291
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
discoiquuid: 6ed15763-02cc-45d1-adf6-cf9e5e8ebdb0
docset: aem65
exl-id: f4959c12-54c5-403a-9973-7a4ab5f16bed
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 19%

---

# Implementieren einer Reaktionskomponente für SPA{#implementing-a-react-component-for-spa}

Single Page Applications (SPAs) können ansprechende Erlebnisse für Website-Benutzer bieten. Entwickler möchten in der Lage sein, Websites mithilfe von SPA-Frameworks zu erstellen, und Autoren möchten Inhalte innerhalb von AEM für eine Website, die mit SPA-Frameworks erstellt wurde, nahtlos bearbeiten.

Die SPA-Erstellungsfunktion bietet eine umfassende Lösung zur Unterstützung von SPAs in AEM. In diesem Artikel wird ein Beispiel dafür vorgestellt, wie eine einfache, vorhandene React-Komponente für die Verwendung mit dem AEM-SPA-Editor angepasst werden kann.

>[!NOTE]
>
>Der SPA Editor ist die empfohlene Lösung für Projekte, die SPA Framework-basiertes Client-seitiges Rendering erfordern (z. B. React oder Angular).

## Einführung {#introduction}

Dank des einfachen und leichten Vertrags, der von AEM benötigt und zwischen dem SPA und dem SPA Editor etabliert wird, ist es einfach, eine vorhandene JavaScript-Anwendung zu verwenden und sie für die Verwendung mit einer SPA in AEM anzupassen.

Dieser Artikel veranschaulicht das Beispiel der Wetterkomponente im Beispiel-SPA &quot;We.Retail Journal&quot;.

Sie sollten mit der [Struktur einer SPA Anwendung für AEM](/help/sites-developing/spa-getting-started-react.md) vertraut sein, bevor Sie diesen Artikel lesen.

>[!CAUTION]
>In diesem Dokument wird die [We.Retail Journal-App](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal) nur zu Demonstrationszwecken verwendet. Sie sollte nicht für Projektaufgaben verwendet werden.
>
>Für jedes AEM-Projekt sollte der [AEM-Projektarchetyp](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/developing/archetype/overview.html) genutzt werden, der SPA-Projekte mithilfe von React oder Angular unterstützt und das SPA SDK verwendet.

## Die Wetterkomponente {#the-weather-component}

Die Wetterkomponente befindet sich oben links in der App &quot;We.Retail Journal&quot;. Es zeigt das aktuelle Wetter einer definierten Position an, wobei Wetterdaten dynamisch abgerufen werden.

### Verwenden des Wetter-Widgets {#using-the-weather-widget}

![screen_shot_2018-06-08at143224](assets/screen_shot_2018-06-08at143224.png)

Beim Bearbeiten von Inhalten des SPA im SPA Editor wird die Wetterkomponente wie jede andere AEM-Komponente angezeigt, mit einer Symbolleiste gefüllt und kann bearbeitet werden.

![screen_shot_2018-06-08at143304](assets/screen_shot_2018-06-08at143304.png)

Die Stadt kann in einem Dialogfeld wie jede andere AEM aktualisiert werden.

![screen_shot_2018-06-08at143446](assets/screen_shot_2018-06-08at143446.png)

Die Änderung wird beibehalten und die Komponente wird automatisch mit neuen Wetterdaten aktualisiert.

![screen_shot_2018-06-08at143524](assets/screen_shot_2018-06-08at143524.png)

### Implementierung der Wetterkomponente {#weather-component-implementation}

Die Wetterkomponente basiert tatsächlich auf einer öffentlich verfügbaren React-Komponente namens [React Open Weather](https://www.npmjs.com/package/react-open-weather), die für die Verwendung als Komponente in der We.Retail Journal-SPA-Beispielanwendung angepasst wurde.

Im Folgenden finden Sie Ausschnitte aus der NPM-Dokumentation zur Verwendung der React Open Weather-Komponente.

![screen_shot_2018-06-08at144723](assets/screen_shot_2018-06-08at144723.png) ![screen_shot_2018-06-08at144215](assets/screen_shot_2018-06-08at144215.png)

Überprüfen des Codes der angepassten Wetterkomponente ( `Weather.js`) in der Anwendung &quot;We.Retail Journal&quot;:

* **Zeile 16**: Das React Open Weather-Widget wird nach Bedarf geladen.
* **Zeile 46**: Die  `MapTo` Funktion ordnet diese React-Komponente einer entsprechenden AEM-Komponente zu, damit sie im SPA Editor bearbeitet werden kann.

* **Zeilen 22-29**: Der  `EditConfig` wird definiert, wobei geprüft wird, ob die Stadt ausgefüllt wurde, und der Wert definiert wird, wenn er leer ist.

* **Zeilen 31-44**: Die Wetterkomponente erweitert die  `Component` Klasse und stellt die erforderlichen Daten bereit, wie in der NPM-Nutzungsdokumentation für die React Open Weather-Komponente definiert, und rendert die Komponente.

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

Obwohl bereits eine Back-End-Komponente vorhanden sein muss, kann der Frontend-Entwickler die React Open Weather-Komponente im We.Retail Journal-SPA mit sehr wenig Kodierung nutzen.

## Nächster Schritt {#next-step}

Weitere Informationen zur Entwicklung von SPA für AEM finden Sie im Artikel [Entwickeln von SPA für AEM](/help/sites-developing/spa-architecture.md).
