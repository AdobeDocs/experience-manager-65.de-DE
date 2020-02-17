---
title: Rendern einer Formularvorlage für HTML5-Formulare
seo-title: Rendern einer Formularvorlage für HTML5-Formulare
description: Profile für HTML5-Formulare sind mit Profil-Renderern verknüpft. Profil-Renderer sind JSP-Seiten, auf denen Formulare im HTML-Format generiert werden. Dazu werden Forms OSGi-Dienste aufgerufen.
seo-description: Profile für HTML5-Formulare sind mit Profil-Renderern verknüpft. Profil-Renderer sind JSP-Seiten, auf denen Formulare im HTML-Format generiert werden. Dazu werden Forms OSGi-Dienste aufgerufen.
uuid: 34daed78-0611-4355-9698-0d7f758e6b61
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: cb75b826-d044-44be-b364-790c046513e0
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Rendern einer Formularvorlage für HTML5-Formulare {#rendering-form-template-for-html-forms}

## Render-Endpunkt {#render-endpoint}

HTML5 forms have the notion of **Profiles** which are exposed as REST Endpoints to enable Mobile Rendering of Form Templates. These Profiles have associated **Profile Renderer**. Es handelt sich dabei um JSP-Seiten, die für die Generierung der HTML-Darstellung des Formulars durch Aufruf des Forms OSGi-Dienstes verantwortlich sind. Der JCR-Pfad der Profil-Node bestimmt die URL des Render-Endpunkts. Der Standard-Render-Endpunkt des Formulars, der auf das Standard-Profil verweist, sieht wie folgt aus:

https://&lt;*host*>:&lt;*port*>/content/xfaforms/profiles/default.html?contentRoot=&lt;*path of the folder containg form xdp*>&amp;template=&lt;*name of the xdp*>

Beispiel: `http://localhost:4502/content/xfaforms/profiles/default.html?contentRoot=c:/xdps&template=sampleForm.xdp`

Bei einem benutzerdefinierten Profil wird der Endpunkt entsprechend geändert. Beispiel: Der Endpunkt für das benutzerdefinierte Profil mit dem Namen „hrforms“ lautet:

`http://localhost:4502/content/xfaforms/profiles/hrforms.html?contentRoot=c:/xdps&template=sampleForm.xdp`

Wenn sich die Vorlage im AEM-Repository in einer Anwendung namens FormSubmission befindet, lautet die URI:

```
http://localhost:4502/content/xfaforms/profiles/default.html?
 contentRoot=crx:///content/dam/formsanddocuments/FormSubmission/1.0
 &template=sampleForm.xdp
```

## Render-Parameter {#render-parameters}

Die folgenden Anforderungsparameter werden beim Rendern von Formularen als HTML unterstützt:

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
   <td>Dieser Parameter gibt den Pfad an, in dem sich die Vorlage und die zugehörigen Ressourcen befinden. Dieser Pfad kann der Server-Dateisystempfad, ein Repository-Pfad, ein HTTP- oder ein FTP-Pfad sein.<br /> </td>
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
| dataRef | Dieser Parameter gibt den **absoluten Pfad** der Datendatei an, die mit der Vorlage zusammengeführt wird. Dieser Parameter kann eine URL zu einem REST-Dienst sein, der die Daten im XML-Format zurückgibt. |
| data | Dieser Parameter gibt die als UTF-8 kodierte Datenbyte an, die mit der Vorlage zusammengeführt werden. Wenn dieser Parameter festgelegt ist, wird der Parameter „dataRef“ im HTML5-Formular ignoriert. |

### Übergeben eines Render-Parameters {#passing-the-render-parameter}

HTML5-Formulare unterstützen drei Methoden zum Übergeben der Render-Parameter. Sie können Parameter mithilfe von URLs, Schlüssel/Wert-Paaren und Profilknoten übergeben. Im Render-Parameter erhalten die Schlüssel/Wert-Paare die höchste Priorität, gefolgt von den Profilknoten. Der URL-Anforderungsparameter hat die geringste Priorität.

* **URL-Anforderungsparameter**: Sie können die Render-Parameter in der URL angeben. In den URL-Anforderungsparametern sind die Parameter für den Endbenutzer sichtbar. For example, the following submit URL contains template parameter in the URL: `http://localhost:4502/content/xfaforms/profiles/default.html?contentRoot=/Applications/FormSubmission/1.0&template=sampleForm.xdp`

* **setAttribute-Anforderungsparameter**: Sie können die Render-Parameter als Schlüssel/Wert-Paar angeben. In den setAttribute-Anforderungsparametern sind die Parameter für den Endbenutzer nicht sichtbar. Sie können eine Anforderung von einem beliebigen anderen JSP an den JSP des Profil-Renderers für HTML5-Formulare weiterleiten und als Anforderungsobjekt *setAttribute* verwenden, um alle Render-Parameter zu übergeben. Diese Methode hat die höchste Priorität.

* **** Profilknoten-Anforderungsparameter: Sie können die Render-Parameter als Knoteneigenschaften eines Profilknotens angeben. In den Profilknoten-Anforderungsparametern sind die Parameter für den Endbenutzer nicht sichtbar. Profilknoten ist der Knoten, an den die Anforderung gesendet wird. Um Parameter als Knoteneigenschaften festzulegen, verwenden Sie CRXDE lite.

### Sende-Parameter {#submit-parameters}

HTML5-Formulare senden Daten und führen serverseitige Skripte und Webdienste auf AEM-Servern aus. Detaillierte Informationen zu Parametern für die Ausführung serverseitiger Skripte und Webdienste auf AEM-Servern finden Sie unter [HTML5 forms Service Proxy](/help/forms/using/service-proxy.md).

**[Support kontaktieren](https://www.adobe.com/account/sign-in.supportportal.html)**
