---
title: Anpassen der Formular-Ereignisverfolgung
seo-title: Anpassen der Formular-Ereignisverfolgung
description: Wenn ein Benutzer mehr als 60 Sekunden in einem Feld verbleibt, wird ein fieldvisit-Ereignis ausgelöst, und die Details des Feldes werden an Adobe SiteCatalyst gesendet.
seo-description: Wenn ein Benutzer mehr als 60 Sekunden in einem Feld verbleibt, wird ein fieldvisit-Ereignis ausgelöst, und die Details des Feldes werden an Adobe SiteCatalyst gesendet.
uuid: 2f790085-2f1a-45be-9a69-6100c76dcae0
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
discoiquuid: 60d67c6b-5994-42ef-b159-ed6edf5cf9d4
translation-type: tm+mt
source-git-commit: dfa983db4446cbb0cbdeb42297248aba55b3dffd

---


# Anpassen der Formular-Ereignisverfolgung {#customizing-form-event-tracking}

Standardmäßig werden die folgenden Ereignisse in einem adaptiven Formular verfolgt, in dem die Analytik aktiviert ist:

<table>
 <tbody>
  <tr>
   <th>Ereignis</th>
   <th>Verfügbare Variablen</th>
  </tr>
  <tr>
   <td>render</td>
   <td>formName, formTitle, formInstance, source</td>
  </tr>
  <tr>
   <td>abandon</td>
   <td>formName, formTitle, formInstance, panelName, panelTitle</td>
  </tr>
  <tr>
   <td>save</td>
   <td>formName, formTitle, formInstance, panelName, source</td>
  </tr>
  <tr>
   <td>submit</td>
   <td>formName, formTitle, formInstance, source</td>
  </tr>
  <tr>
   <td>Fehler</td>
   <td>formName, formTitle, fieldName, fieldTitle, panelTitle</td>
  </tr>
  <tr>
   <td>help</td>
   <td>formName, formTitle, fieldName, fieldTitle, panelTitle</td>
  </tr>
  <tr>
   <td>fieldVisit</td>
   <td>formName, formTitle, fieldName, fieldTitle, panelTitle<br /> </td>
  </tr>
  <tr>
   <td>panelVisit</td>
   <td>formName, formTitle, panelName, panelTitle</td>
  </tr>
 </tbody>
</table>

## Anpassen der Zeitüberschreitung für Feldbesuche {#customizing-the-field-visit-event-timeout}

Wenn ein Benutzer bei der standardmäßigen AEM-Formularkonfiguration mehr als 60 Sekunden in einem Feld verbleibt, wird ein `fieldvisit`-Ereignis ausgelöst, und die Details des Feldes werden an Adobe Analytics gesendet. Sie können den Zeitschwellenwert für Feldverfolgung unter AEM forms-Analytics-Konfiguration in der AEM Configuration-Konsole (/system/console/configMgr) anpassen, um den Timeout-Wert zu erhöhen oder zu verringern.

## Anpassen der Verfolgungsereignisse {#customizing-the-tracking-events}

You can modify the `trackEvent`function available in `/libs/afanalytics/js/custom.js` file to customize the event tracking. Wenn ein verfolgtes Ereignis in einem adaptiven Formular auftritt, wird die Funktion `trackEvent` aufgerufen. The `trackEvent` function accepts two parameters: `eventName`and `variableValueMap`.

You can evaluate value of *eventName* and *variableValueMap* arguments to change the tracking behavior of events. Sie können beispielsweise festlegen, dass die Informationen an den Analytics-Server gesendet werden, nachdem eine bestimmte Anzahl an Fehlerereignissen aufgetreten ist. Sie können außerdem die folgenden Anpassungen ausführen:

* Sie können eine Schwellenwertzeit festlegen, bevor das Ereignis gesendet wird.
* You can maintain a state to decide action, for example, *fieldVisit* pushes a dummy event based on the timestamp of the last event.
* Sie können die Funktion `pushEvent` verwenden, um das Ereignis an den Analytics-Server zu senden *.*

* Sie können festlegen, das Ereignis nicht an den Analytics-Server zu senden.

### Beispiel {#sample}

In the following example, state for the *error* event of each *fieldName* attribute is maintained. Das Ereignis wird nur dann an den Analytics-Server gesendet, wenn ein Fehler erneut auftritt.

```
case 'error':
        if(errorOccurred[variableValueMap.fieldName] == true) {
            pushEvent(eventName, variableValueMap)
        }
        errorOccurred[variableValueMap.fieldName] = true;
        break;
```

## Anpassen des panelvisit-Ereignisses {#customizing-the-panelvisit-event}

Nach jeweils 60 Sekunden wird beim Standardsetup von AEM Forms überprüft, ob das Fenster mit dem adaptiven Formular aktiv ist. If the window is active, a `panelVisit`event is triggered to Adobe Analytics. Es ermittelt, of das Dokument oder das Formular aktiv ist und berechnet die Zeit, die für da entsprechende Formular oder Dokument verwendet wird.

>[!NOTE]
>
>Der Ereignisname, der zur Ermittlung der Aktivität und Berechnung der Zeit verwendet wird lautet „panelVisit“. Dieses Ereignis unterscheidet sich vom Bereichsbesuchsereignis, das in der obigen Tabelle aufgelistet ist.

You can modify the scheduleHeartBeatCheck function available in the `/libs/afanalytics/js/custom.js` file to change or stop this event sent to Adobe Analytics at a regular interval.
