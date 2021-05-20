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
exl-id: d0280a15-5d0d-49cf-bce9-ad1c40530eae
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 77%

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
   <td>Speichern</td>
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

## Anpassen der Zeitüberschreitung für Feldbesuche  {#customizing-the-field-visit-event-timeout}

Wenn ein Benutzer bei der standardmäßigen AEM-Formularkonfiguration mehr als 60 Sekunden in einem Feld verbleibt, wird ein `fieldvisit`-Ereignis ausgelöst, und die Details des Feldes werden an Adobe Analytics gesendet. Sie können den Zeitschwellenwert für Feldverfolgung unter AEM forms-Analytics-Konfiguration in der AEM Configuration-Konsole (/system/console/configMgr) anpassen, um den Timeout-Wert zu erhöhen oder zu verringern.

## Anpassen der Verfolgungsereignisse  {#customizing-the-tracking-events}

Sie können die in der Datei `trackEvent`verfügbare Funktion `/libs/afanalytics/js/custom.js` ändern, um die Ereignisverfolgung anzupassen. Wenn ein verfolgtes Ereignis in einem adaptiven Formular auftritt, wird die Funktion `trackEvent` aufgerufen. Die Funktion `trackEvent` akzeptiert zwei Parameter: `eventName`und `variableValueMap`.

Sie können den Wert der Argumente *eventName* und *variableValueMap* auswerten, um das Tracking-Verhalten von Ereignissen zu ändern. Sie können beispielsweise festlegen, dass die Informationen an den Analytics-Server gesendet werden, nachdem eine bestimmte Anzahl an Fehlerereignissen aufgetreten ist. Sie können außerdem die folgenden Anpassungen ausführen:

* Sie können eine Schwellenwertzeit festlegen, bevor das Ereignis gesendet wird.
* Sie können einen Status beibehalten, um die Aktion zu bestimmen. So wird beispielsweise *fieldVisit* ein Platzhalterereignis basierend auf dem Zeitstempel des letzten Ereignisses übergeben.
* Sie können die Funktion `pushEvent` verwenden, um das Ereignis an den Analytics-Server zu senden *.*

* Sie können festlegen, das Ereignis nicht an den Analytics-Server zu senden.

### Beispiel {#sample}

Im folgenden Beispiel wird der Status für das *error*-Ereignis jedes *fieldName*-Attributs beibehalten. Das Ereignis wird nur dann an den Analytics-Server gesendet, wenn ein Fehler erneut auftritt.

```javascript
case 'error':
        if(errorOccurred[variableValueMap.fieldName] == true) {
            pushEvent(eventName, variableValueMap)
        }
        errorOccurred[variableValueMap.fieldName] = true;
        break;
```

## Anpassen des panelvisit-Ereignisses {#customizing-the-panelvisit-event}

Nach jeweils 60 Sekunden wird beim Standardsetup von AEM Forms überprüft, ob das Fenster mit dem adaptiven Formular aktiv ist. Wenn das Fenster aktiv ist, wird ein `panelVisit`Ereignis an Adobe Analytics ausgelöst. Es ermittelt, of das Dokument oder das Formular aktiv ist und berechnet die Zeit, die für da entsprechende Formular oder Dokument verwendet wird.

>[!NOTE]
>
>Der Ereignisname, der zur Ermittlung der Aktivität und Berechnung der Zeit verwendet wird lautet „panelVisit“. Dieses Ereignis unterscheidet sich vom Bereichsbesuchsereignis, das in der obigen Tabelle aufgelistet ist.

Sie können die scheduleHeartBeatCheck-Funktion ändern, die in der Datei `/libs/afanalytics/js/custom.js` verfügbar ist, um dieses Ereignis, das regelmäßig an Adobe Analytics gesendet wird, zu ändern oder anzuhalten.
