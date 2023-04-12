---
title: Zuordnung benutzerdefinierter Benutzergruppen in AEM 6.5
seo-title: Custom User Group Mapping in AEM 6.5
description: Erfahren Sie, wie die Zuordnung benutzerspezifischer Benutzergruppen in AEM funktioniert.
seo-description: Lear how Custom User Group Mapping works in AEM.
uuid: 7520351a-ab71-4661-b214-a0ef012c0c93
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: 13085dd3-d283-4354-874b-cd837a9db9f9
docset: aem65
exl-id: 661602eb-a117-454d-93d3-a079584f7a5d
feature: Security
source-git-commit: 2981f11565db957fac323f81014af83cab2c0a12
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 24%

---

# Zuordnung benutzerdefinierter Benutzergruppen in AEM 6.5 {#custom-user-group-mapping-in-aem}

## Vergleich von JCR-Inhalten im Zusammenhang mit CUG (benutzerdefinierte Benutzergruppe) {#comparison-of-jcr-content-related-to-cug}

<table>
 <tbody>
  <tr>
   <td><strong>Ältere AEM-Versionen</strong></td>
   <td><strong>AEM 6.5</strong></td>
   <td><strong>Kommentare</strong></td>
  </tr>
  <tr>
   <td><p>Eigenschaft: cq:cugEnabled</p> <p>Deklarierender Knotentyp: N/A, Resteigenschaft</p> </td>
   <td><p>Autorisierung:</p> <p>Knoten: rep:cugPolicy des Knotentyps rep:CugPolicy</p> <p>Deklarierender Knotentyp: rep:CugMixin</p> <p> </p> <p> </p> <p> </p> Authentifizierung:</p> <p>Mixin-Typ: granite:AuthenticationRequired</p> </td>
   <td><p>Um den Lesezugriff zu beschränken, wird eine dedizierte CUG-Richtlinie auf den Zielknoten angewendet.</p> <p>HINWEIS: Richtlinien können nur auf die konfigurierten unterstützten Pfade angewendet werden.</p> <p>Knoten mit dem Namen rep:cugPolicy und Typ rep:CugPolicy sind geschützt und können nicht mit regulären JCR-API-Aufrufen geschrieben werden. Verwenden Sie stattdessen die Verwaltung der JCR-Zugriffssteuerung.</p> <p>Weitere Informationen finden Sie auf <a href="https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html">dieser Seite</a>.</p> <p>Um die Authentifizierungspflicht für einen Knoten zu erzwingen, reicht es aus, den Mixin-Typ granite:AuthenticationRequired hinzuzufügen.</p> <p>HINWEIS: Wird nur unterhalb der konfigurierten unterstützten Pfade berücksichtigt.</p> </td>
  </tr>
  <tr>
   <td><p>Eigenschaft: cq:cugPrincipals</p> <p>Deklarierender Knotentyp: NA, Resteigentum</p> </td>
   <td><p>Eigenschaft: rep:principalNames</p> <p>Deklarierender Knotentyp: rep:CugPolicy</p> </td>
   <td><p>Die -Eigenschaft, die die Namen der Prinzipale enthält, die den Inhalt unter der eingeschränkten CUG lesen dürfen, ist geschützt und kann nicht mit regulären JCR-API-Aufrufen geschrieben werden. Verwenden Sie stattdessen die Verwaltung der JCR-Zugriffssteuerung.</p> <p>Siehe <a href="https://jackrabbit.apache.org/api/2.12/org/apache/jackrabbit/api/security/authorization/PrincipalSetPolicy.html">diese Seite</a> für weitere Details zur Implementierung.</p> </td>
  </tr>
  <tr>
   <td><p>Eigenschaft: cq:cugLoginPage</p> <p>Deklarierender Knotentyp: NA, Resteigentum</p> </td>
   <td><p>Eigenschaft: granite:loginPath (optional)</p> <p>Deklarierender Knotentyp: granite:AuthenticationRequired</p> </td>
   <td><p>Ein JCR-Knoten, bei dem der Mixin-Typ granite:AuthenticationRequired definiert ist, kann optional einen alternativen Anmeldepfad definieren.</p> <p>HINWEIS: Wird nur unter den konfigurierten unterstützten Pfaden berücksichtigt.</p> </td>
  </tr>
  <tr>
   <td><p>Eigenschaft: cq:cugRealm</p> <p>Deklarierender Knotentyp: NA, Resteigentum</p> </td>
   <td>nicht vorhanden</td>
   <td>Wird von der neuen Implementierung nicht mehr unterstützt.</td>
  </tr>
 </tbody>
</table>

## Vergleich der OSGi-Dienste {#comparison-of-osgi-services}

**Ältere AEM-Versionen**

Titel: Adobe Granite Closed User Group (CUG)-Unterstützung

Name: com.day.cq.auth.impl.CugSupportImpl

**AEM 6.5**

* Titel: Apache Jackrabbit Oak CUG-Konfiguration

   Name: org.apache.jackrabbit.oak.spi.security.authorization.cug.impl.CugConfiguration

   ConfigurationPolicy = ERFORDERLICH

* Titel: Apache Jackrabbit Oak CUG Exclude List

   Name: org.apache.jackrabbit.oak.spi.security.authorization.cug.impl.CugExcludeImpl

   ConfigurationPolicy = ERFORDERLICH

* Name: com.adobe.granite.auth.requirement.impl.RequirementService
* Titel: Adobe Granite-Authentifizierungspflicht und Anmeldungspfad-Handler

   Name: com.adobe.granite.auth.requirement.impl.DefaultRequirementHandler

   ConfigurationPolicy = ERFORDERLICH

**Kommentare**

* Konfiguration der CUG-Autorisierung und Aktivieren/Deaktivieren der Bewertung.
Dienst zum Konfigurieren der Ausschlussliste der Prinzipale, die durch die CUG-Autorisierung nicht mehr beeinträchtigt werden sollten.

   >[!NOTE]
   > 
   >Wenn die Variable `CugExcludeImpl` nicht konfiguriert ist, wird die `CugConfiguration` wird auf den Standardwert zurückgesetzt.

   Es ist möglich, eine benutzerdefinierte CugExclude-Implementierung zu verwenden, wenn besondere Anforderungen auftreten.

* OSGi-Komponente zur Implementierung von LoginPathProvider , die einen übereinstimmenden Anmeldepfad für den LoginSelectorHandler bereitstellt. Sie enthält einen obligatorischen Verweis auf einen RequirementHandler, der zur Registrierung des Beobachters verwendet wird, der mithilfe des Mixin-Typs granite:AuthenticationRequired die geänderten Authentifizierungsanforderungen überwacht, die im Inhalt gespeichert sind.
* OSGi-Komponente, die den RequirementHandler implementiert, der den SlingAuthenticator über Änderungen an Authentifizierungspflichten benachrichtigt.

   Da die Konfigurationsrichtlinie für diese Komponente ERFORDERLICH ist, wird sie nur aktiviert, wenn eine Reihe unterstützter Pfade angegeben ist.

   Durch die Aktivierung des Dienstes wird der RequirementService gestartet.

<!-- nested tables not supported - text above is the table>
<table>
 <tbody>
  <tr>
   <td><strong>Older AEM Versions</strong></td>
   <td><strong>AEM 6.5</strong></td>
   <td><strong>Comments</strong></td>
  </tr>
  <tr>
   <td><p>Label: Adobe Granite Closed User Group (CUG) Support</p> <p>Name: com.day.cq.auth.impl.CugSupportImpl</p> </td>
   <td><p>Label: Apache Jackrabbit Oak CUG Configuration</p> <p>Name: org.apache.jackrabbit.oak.spi.security.authorization.cug.impl.CugConfiguration</p> <p>ConfigurationPolicy = REQUIRED</p> </td>
    <td><p>Label: Apache Jackrabbit Oak CUG Exclude List</p> <p>Name: org.apache.jackrabbit.oak.spi.security.authorization.cug.impl.CugExcludeImpl</p> <p>ConfigurationPolicy = REQUIRED</p> <p> </p> <p> </p> <p> </p> <p> </p> </td>
      </tr>
      <tr>
       <td>Name: com.adobe.granite.auth.requirement.impl.RequirementService</td>
      </tr>
      <tr>
       <td><p>Label: Adobe Granite Authentication Requirement and Login Path Handler</p> <p>Name: com.adobe.granite.auth.requirement.impl.DefaultRequirementHandler</p> <p>ConfigurationPolicy = REQUIRED</p> </td>
      </tr>
     </tbody>
    </table> </td>
   <td>
     <tbody>
      <tr>
       <td>Configuration of the CUG authorization and enable/disable the evaluation.</td>
      </tr>
      <tr>
       <td><p>Service to configure exclusion list of principals which should not be affected by the CUG authorization.</p> <p>NOTE: If the CugExcludeImpl is not configured, the CugConfiguration will fall back to the default.</p> <p>It is possible to plug a custom CugExclude implementation in case of special needs.</p> </td>
      </tr>
      <tr>
       <td>OSGi component implementing LoginPathProvider that exposes a matching login path to the LoginSelectorHandler. It has a mandatory reference to a RequirementHandler which is used to register the observer that listens to changed auth requirements stored in the content by the means of the granite:AuthenticationRequired mixin type. </td>
      </tr>
      <tr>
       <td><p>OSGi component implementing RequirementHandler that notifies the SlingAuthenticator about changes to authrequirements.</p> <p>As configuration policy for this component is REQUIRE it will only be activated if a set of supported paths is specified.</p> <p>Enabling the service will launch the RequirementService.</p> </td>
      </tr>
     </tbody>
     </td>
  </tr>
  <tr>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
 </tbody>
</table>
-->
