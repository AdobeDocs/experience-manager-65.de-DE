---
title: Zuordnung benutzerdefinierter Benutzergruppen in AEM 6.5
seo-title: Zuordnung benutzerdefinierter Benutzergruppen in AEM 6.5
description: Erfahren Sie, wie benutzerdefinierte Benutzergruppen in AEM zugeordnet werden.
seo-description: Erfahren Sie, wie benutzerdefinierte Benutzergruppen in AEM zugeordnet werden.
uuid: 7520351a-ab71-4661-b214-a0ef012c0c93
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: 13085dd3-d283-4354-874b-cd837a9db9f9
docset: aem65
exl-id: 661602eb-a117-454d-93d3-a079584f7a5d
feature: Security
translation-type: tm+mt
source-git-commit: 9134130f349c6c7a06ad9658a87f78a86b7dbf9c
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 74%

---

# Zuordnung benutzerdefinierter Benutzergruppen in AEM 6.5 {#custom-user-group-mapping-in-aem}

## Vergleich von JCR-Inhalt mit CUG-Bezug {#comparison-of-jcr-content-related-to-cug}

<table>
 <tbody>
  <tr>
   <td><strong>Ältere AEM-Versionen</strong></td>
   <td><strong>AEM 6.5</strong></td>
   <td><strong>Kommentare</strong></td>
  </tr>
  <tr>
   <td><p>Eigenschaft: cq:cugEnabled</p> <p>Deklarierender Knotentyp: nicht zutreffend, Resteigenschaft</p> </td>
   <td><p>Autorisierung:</p> <p>Knoten: rep:cugPolicy des Knotentyps rep:CugPolicy</p> <p>Deklarierender Knotentyp: rep:CugMixin</p> <p> </p> <p> </p> <p> </p> Authentifizierung:</p> <p>Mixin-Typ: granite:AuthenticationRequired</p> </td>
   <td><p>Um den Lesezugriff einzuschränken, wird eine dedizierte CUG-Richtlinie auf den Zielknoten angewendet.</p> <p>HINWEIS: Richtlinien können nur für die konfigurierten unterstützten Pfade angewendet werden.</p> <p>Knoten mit dem Namen rep:Cugpolicy und Typ rep:Cugpolicy sind geschützt und können nicht mit normalen JCR-API-Aufrufen geschrieben werden. Verwenden Sie stattdessen JCR-Zugangssteuerungsverwaltung.</p> <p>Weitere Informationen finden Sie auf <a href="https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html">dieser Seite</a>.</p> <p>Um die Authentifizierungsanforderung für einen Knoten zu erzwingen, reicht es aus, den mixin-Typ granite:AuthenticationRequired hinzuzufügen.</p> <p>HINWEIS: Wird nur unter den konfigurierten unterstützten Pfaden berücksichtigt.</p> </td>
  </tr>
  <tr>
   <td><p>Eigenschaft: cq:cugPrincipals</p> <p>Deklarierender Knotentyp: nicht zutreffend, Resteigenschaft</p> </td>
   <td><p>Eigenschaft: rep:principalNames</p> <p>Deklarierender Knotentyp: rep:CugPolicy</p> </td>
   <td><p>Die Eigenschaft, die die Namen der Prinzipale enthält, die den Inhalt unterhalb der eingeschränkten CUG lesen dürfen, ist geschützt und kann nicht mit normalen JCR-API-Aufrufen geschrieben werden. Verwenden Sie stattdessen JCR-Zugangssteuerungsverwaltung.</p> <p>Weitere Informationen zur Implementierung finden Sie auf <a href="https://svn.apache.org/repos/asf/jackrabbit/trunk/jackrabbitapi/src/main/java/org/apache/jackrabbit/api/security/authorization/PrincipalSetPolicy.java">dieser Seite</a>.</p> </td>
  </tr>
  <tr>
   <td><p>Eigenschaft: cq:cugLoginPage</p> <p>Deklarierender Knotentyp: nicht zutreffend, Resteigenschaft</p> </td>
   <td><p>Eigenschaft: granite:loginPath (optional)</p> <p>Deklarierender Knotentyp: granite:AuthenticationRequired</p> </td>
   <td><p>Ein JCR-Knoten, für den der mixin-Typ "granite:AuthenticationRequired"definiert ist, kann optional einen alternativen Anmeldepfad definieren.</p> <p>HINWEIS: Wird nur unter den konfigurierten unterstützten Pfaden berücksichtigt.</p> </td>
  </tr>
  <tr>
   <td><p>Eigenschaft: cq:cugRealm</p> <p>Deklarierender Knotentyp: nicht zutreffend, Resteigenschaft</p> </td>
   <td>nicht vorhanden</td>
   <td>Wird bei der neuen Implementierung nicht mehr unterstützt.</td>
  </tr>
 </tbody>
</table>

## Vergleich der OSGi-Dienste {#comparison-of-osgi-services}

**Ältere AEM-Versionen**

Bezeichnung: Adobe Granite Closed User Group (CUG) Support

Name: com.day.cq.auth.impl.CugSupportImpl

**AEM 6.5**

* Bezeichnung: Apache Jackrabbit Oak CUG Configuration

   Name: org.apache.jackrabbit.oak.spi.security.authorization.cug.impl.CugConfiguration

   ConfigurationPolicy = ERFORDERLICH

* Bezeichnung: Apache Jackrabbit Oak CUG Exclude List

   Name: org.apache.jackrabbit.oak.spi.security.authorization.cug.impl.CugExcludeImpl

   ConfigurationPolicy = ERFORDERLICH

* Name: com.adobe.granite.auth.requirement.impl.RequirementService
* Bezeichnung: Adobe Granite Authentication Requirement and Login Path Handler

   Name: com.adobe.granite.auth.requirement.impl.DefaultRequirementHandler

   ConfigurationPolicy = ERFORDERLICH

**Kommentare**

* Konfiguration der CUG-Autorisierung und Aktivieren/Deaktivieren der Bewertung.
Dienst zum Konfigurieren der Liste von Prinzipalen, die von der CUG-Genehmigung nicht betroffen sein sollten.

   >[!NOTE]
   > 
   >Wenn `CugExcludeImpl` nicht konfiguriert ist, wird `CugConfiguration` auf die Standardeinstellung zurückgesetzt.

   Es ist möglich, bei besonderen Anforderungen eine benutzerdefinierte CugExclude-Implementierung zu verbinden.

* OSGi-Komponente, die den LoginPathProvider implementiert, der einen übereinstimmenden Anmeldepfad zum LoginSelectorHandler bereitstellt. Verfügt über einen obligatorischen Verweis auf einen RequirementHandler. Dieser wird dazu verwendet, den Beobachter zu registrieren, der auf geänderte Authentifizierungsanforderungen wartet, die im Inhalt durch den Mixin-Typ granite:AuthenticationRequired gespeichert sind.
* OSGi-Komponente zur Implementierung von RequirementHandler, die den SlingAuthenticator über Änderungen an Authoring-Anforderungen informiert.

   Da die Konfigurationspolitik für diese Komponente ERFORDERLICH ist, wird sie nur aktiviert, wenn eine Reihe unterstützter Pfade angegeben ist.

   Durch Aktivierung des Dienstes wird RequirementService gestartet.

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
