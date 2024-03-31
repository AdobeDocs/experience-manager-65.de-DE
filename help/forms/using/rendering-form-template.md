---
title: Rendern einer Formularvorlage für HTML5-Formulare
description: HTML5-Formularprofile sind mit Profil-Renderern verknüpft. Profil-Renderer sind JSP-Seiten, auf denen Formulare im HTML-Format generiert werden. Dazu werden Forms OSGi-Dienste aufgerufen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: cb75b826-d044-44be-b364-790c046513e0
feature: HTML5 Forms
exl-id: 022b9953-2d64-473f-87b7-aac1602f6a7e
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 100%

---

# Rendern einer Formularvorlage für HTML5-Formulare {#rendering-form-template-for-html-forms}

## Rendern des Endpunktes {#render-endpoint}

HTML5-Formulare umfassen das Konzept der **Profile**, die als REST-Endpunkte bereitgestellt werden, um Formularvorlagen auf Mobilgeräten rendern zu können. Diese Profile sind mit einem **Profile Renderer** verknüpft. Es handelt sich um JSP-Seiten, auf denen Formulare im HTML-Format generiert werden. Dazu werden Forms OSGi-Services aufgerufen. Der JCR-Pfad des Profilknotens bestimmt die URL des Render-Endpunktes. Der Standard-Render-Endpunkt des Formulars, der auf das „Standard“-Profil verweist, sieht wie folgt aus:

https://&lt;*Host*>:&lt;*Port*>/content/xfaforms/profiles/default.html?contentRoot=&lt;*Pfad des Ordners mit der Formular-XDP*>&amp;template=&lt;*Name der XDP*>

Beispiel: `http://localhost:4502/content/xfaforms/profiles/default.html?contentRoot=c:/xdps&template=sampleForm.xdp`

Bei einem benutzerdefinierten Profil ändert sich der Endpunkt entsprechend. Der Endpunkt für das benutzerdefinierte Profil mit dem Namen „hrforms“ lautet beispielsweise:

`http://localhost:4502/content/xfaforms/profiles/hrforms.html?contentRoot=c:/xdps&template=sampleForm.xdp`

Wenn sich die Vorlage im AEM-Repository in einer Anwendung namens FormSubmission befindet, lautet die URI:

```http
http://localhost:4502/content/xfaforms/profiles/default.html?
 contentRoot=crx:///content/dam/formsanddocuments/FormSubmission/1.0
 &template=sampleForm.xdp
```

## Render-Parameter {#render-parameters}

Die beim Rendern des Formulars als HTML unterstützten Anforderungsparameter lauten wie folgt:

<table>
 <tbody>
  <tr>
   <th><strong>Parameter </strong></th>
   <th><strong>Beschreibung</strong></th>
  </tr>
  <tr>
   <td>template<br /> </td>
   <td>Dieser Parameter gibt den Namen der Vorlagendatei an.<br /> </td>
  </tr>
  <tr>
   <td>contentRoot<br /> </td>
   <td>Dieser Parameter gibt den Pfad an, unter dem sich die Vorlage und die zugehörigen Ressourcen befinden. Dieser Pfad kann der Dateisystempfad des Servers oder ein Repository-Pfad oder http oder ein FTP-Pfad sein.<br /> </td>
  </tr>
  <tr>
   <td>submitUrl<br /> </td>
   <td>Dieser Parameter gibt die URL an, an die die Formulardaten-XML gesendet wird.<br /> </td>
  </tr>
 </tbody>
</table>

### Zusammenführen von Daten mit einer Formularvorlage {#merge-data-with-form-template}

| Parameter | Beschreibung |
|---|---|
| dataRef | Dieser Parameter gibt den **absoluten Pfad** der Datendatei an, die mit der Vorlage zusammengeführt wird. Dieser Parameter kann eine URL eines REST-Services sein, der die Daten im XML-Format zurückgibt. |
| data | Dieser Parameter gibt die als UTF-8 kodierten Daten-Bytes an, die mit der Vorlage zusammengeführt werden. Wenn dieser Parameter festgelegt ist, wird der Parameter „dataRef“ im HTML5-Formular ignoriert. |

### Übergabe des Render-Parameters {#passing-the-render-parameter}

HTML5-Formulare unterstützen drei Methoden zum Übergeben der Render-Parameter. Sie können Parameter über URLs, Schlüssel-Wert-Paare und Profilknoten übergeben. Im Render-Parameter hat das Schlüssel-Wert-Paar die höchste Priorität, gefolgt vom Profilknoten. Der URL-Anforderungsparameter erhält die geringste Priorität.

* **URL-Anfrageparameter**: Sie können die Render-Parameter in der URL angeben. In den URL-Anfrageparametern sind die Parameter für Endbenutzende sichtbar. Beispielsweise enthält die folgende Sende-URL die Vorlagenparameter in der URL: `http://localhost:4502/content/xfaforms/profiles/default.html?contentRoot=/Applications/FormSubmission/1.0&template=sampleForm.xdp`

* **SetAttribute-Anforderungsparameter**: Sie können die Render-Parameter als Schlüssel-Wert-Paar angeben. In den SetAttribute-Anforderungsparametern sind die Parameter für Endbenutzende nicht sichtbar. Sie können eine Anforderung von einem beliebigen anderen JSP an den JSP des Profil-Renderers für HTML5-Formulare weiterleiten und als Anforderungsobjekt *setAttribute* verwenden, um alle Render-Parameter zu übergeben. Diese Methode hat die höchste Priorität.

* **Profilknoten-Anforderungsparameter:** Sie können die Render-Parameter als Knoteneigenschaften eines Profilknotens angeben. In den Anforderungsparametern des Profilknotens sind die Parameter für Endbenutzende nicht sichtbar. Der Profilknoten ist der Knoten, an den die Anfrage gesendet wird. Um Parameter als Knoteneigenschaften festzulegen, verwenden Sie CRXDE Lite.

### Absenden von Parametern {#submit-parameters}

HTML5-Formulare senden Daten und führen serverseitige Skripte und Webdienste auf AEM-Servern aus. Ausführliche Informationen zu Parametern, die zum Ausführen Server-seitiger Skripts und Web-Dienste auf AEM-Servern verwendet werden, finden Sie unter [HTML5-Formular-Service-Proxy](/help/forms/using/service-proxy.md).
