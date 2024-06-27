---
title: Anpassen der Formular-Ereignisverfolgung
description: Wenn eine Benutzerin oder ein Benutzer mehr als 60 Sekunden in einem Feld verbleibt, wird ein fieldvisit-Ereignis ausgelöst, und die Details des Felds werden an Adobe SiteCatalyst gesendet.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
exl-id: d0280a15-5d0d-49cf-bce9-ad1c40530eae
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms,Foundation Components
source-git-commit: 8a77756e8ba771c8de9950c2323bef8f23cc59b4
workflow-type: ht
source-wordcount: '449'
ht-degree: 100%

---

# Anpassen der Formular-Ereignisverfolgung {#customizing-form-event-tracking}

Standardmäßig werden die folgenden Ereignisse in einem adaptiven Formular mit aktivierter Analyse nachverfolgt:

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

## Anpassen des Timeouts bei Feldbesuchen {#customizing-the-field-visit-event-timeout}

Wenn ein Benutzer bei der standardmäßigen AEM-Formularkonfiguration mehr als 60 Sekunden in einem Feld verbleibt, wird ein `fieldvisit`-Ereignis ausgelöst, und die Details des Feldes werden an Adobe Analytics gesendet. Sie können den Baseline-Zeitwert für das Tracking von Feldern unter der AEM Forms Analytics-Konfiguration in der AEM-Konfigurationskonsole (/system/console/configMgr) anpassen, um den Timeout-Wert zu erhöhen oder zu verringern.

## Anpassen der Tracking-Ereignisse {#customizing-the-tracking-events}

Sie können die Funktion `trackEvent`, die in der Datei `/libs/afanalytics/js/custom.js` verfügbar ist, ändern, um die Ereignisverfolgung anzupassen. Wenn ein verfolgtes Ereignis in einem adaptiven Formular auftritt, wird die Funktion `trackEvent` aufgerufen. Die Funktion `trackEvent` akzeptiert zwei Parameter: `eventName`und `variableValueMap`.

Sie können die Werte der Argumente *eventName* und *variableValueMap* auswerten, um das Verfolgungsverhalten von Ereignissen zu ändern. Sie können beispielsweise festlegen, dass die Informationen an den Analytics-Server gesendet werden, nachdem eine bestimmte Anzahl an Fehlerereignissen aufgetreten ist. Sie können außerdem die folgenden Anpassungen durchführen:

* Sie können eine Schwellenwertzeit festlegen, bevor das Ereignis gesendet wird.
* Sie können einen Status beibehalten, um die Aktion festzulegen (*fieldVisit* überträgt zum Beispiel ein Platzhalterereignis basierend auf dem Zeitstempel des letzten Ereignisses).
* Sie können die Funktion `pushEvent` verwenden, um das Ereignis an den Analytics-Server zu senden *.*

* Sie können festlegen, das Ereignis nicht an den Analytics-Server zu senden.

### Beispiel {#sample}

Im folgenden Beispiel wird der Status für das *error*-Ereignis für jedes *fieldName*-Attribut beibehalten. Das Ereignis wird nur dann an den Analytics-Server gesendet, wenn ein Fehler erneut auftritt.

```javascript
case 'error':
        if(errorOccurred[variableValueMap.fieldName] == true) {
            pushEvent(eventName, variableValueMap)
        }
        errorOccurred[variableValueMap.fieldName] = true;
        break;
```

## Anpassen des panelvisit-Ereignisses {#customizing-the-panelvisit-event}

Nach jeweils 60 Sekunden wird beim Standardsetup von AEM Forms überprüft, ob das Fenster mit dem adaptiven Formular aktiv ist. Wenn das Fenster aktiv ist, ist ein `panelVisit`-Ereignis ausgelöst, das an Adobe Analytics gesendet wird. Dies hilft dabei, zu ermitteln, ob das Dokument oder das Formular aktiv ist, und die für das entsprechende Formular oder Dokument aufgewendete Zeit zu berechnen.

>[!NOTE]
>
>Der Ereignisname, der zur Ermittlung der Aktivität und Berechnung der Zeit verwendet wird, lautet „panelVisit“. Dieses Ereignis unterscheidet sich vom panelVisit-Ereignis, das in der obigen Tabelle aufgelistet ist.

Sie können die Funktion scheduleHeartBeatCheck modifizieren, die in der Datei `/libs/afanalytics/js/custom.js` verfügbar ist, um dieses Ereignis zu ändern und anzuhalten, das regelmäßig an Adobe Analytics gesendet wird.
