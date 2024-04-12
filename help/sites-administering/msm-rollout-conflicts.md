---
title: MSM-Rollout-Konflikte
description: Erfahren Sie, wie Sie mit Rollout-Konflikten in Multi Site Manager umgehen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
feature: Multi Site Manager
exl-id: e145e79a-c363-4a33-b9f9-99502ed20563
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: eae057caed533ef16bb541b4ad41b8edd7aaa1c7
workflow-type: tm+mt
source-wordcount: '905'
ht-degree: 99%

---

# MSM-Rollout-Konflikte{#msm-rollout-conflicts}

Konflikte sind möglich, wenn neue Seiten mit demselben Seitennamen im Blueprint-Zweig und in einer abhängigen Live Copy-Verzweigung erstellt werden.

Solche Konflikte müssen nach dem Rollout gehandhabt und aufgelöst werden.

## Konfliktbehandlung {#conflict-handling}

Wenn Konfliktseiten (in den Blueprint- und Live Copy-Zweigen) vorhanden sind, gestattet Ihnen MSM die Definition, wie (oder überhaupt ob) dieser Konflikt behoben werden soll.

Um sicherzustellen, dass der Rollout nicht gesperrt ist, können mögliche Definitionen Folgendes umfassen:

* Welche Seite (Blueprint oder Live Copy) während des Rollouts Vorrang hat,
* welche Seiten umbenannt werden (und wie),
* wie sich dies auf veröffentlichte Inhalte auswirkt.

  Das Standardverhalten von Adobe Experience Manager (AEM) (vorkonfiguriert) sieht vor, dass veröffentlichte Inhalte nicht beeinträchtigt werden. Wenn also eine Seite, die im Live Copy-Zweig manuell erstellt wurde, veröffentlicht wurde, wird dieser Inhalt nach der Konfliktbehandlung und dem Rollout auch weiterhin veröffentlicht.

Neben der Standardfunktion können auch benutzerdefinierte Konflikt-Handler hinzugefügt werden, um verschiedene Regeln zu implementieren. Diese können auch die Veröffentlichung von Aktionen als individuellen Prozess ermöglichen.

### Beispiel-Szenario {#example-scenario}

In den folgenden Abschnitten müssen Sie das Beispiel einer neuen Seite `b` verwenden, die sowohl im Blueprint als auch in dem (manuell erstellten) Live Copy-Zweig erstellt wurde, um die verschiedenen Methoden der Konfliktlösung zu veranschaulichen:

* Blueprint: `/b`

  Eine Musterseite; mit einer untergeordneten Seite, bp-level-1.

* Live Copy: `/b`

  Eine im Live Copy-Zweig manuell erstellte Seite; mit einer untergeordneten Seite, `lc-level-1`.

   * Bei Veröffentlichung als `/b` aktiviert, zusammen mit der untergeordneten Seite.

**Vor dem Rollout**

<table>
 <tbody>
  <tr>
   <td><strong>Blueprint vor dem Rollout</strong></td>
   <td><strong>Live Copy vor dem Rollout</strong></td>
   <td><strong>Vor dem Rollout veröffentlichen</strong></td>
  </tr>
  <tr>
   <td><code>b</code><br /> <br /> (In der Blueprint-Verzweigung erstellt, bereit für den Rollout)<br /> </td>
   <td><code>b</code><br /> <br /> (Manuell in der Live Copy-Verzweigung erstellt)<br /> </td>
   <td><code>b</code><br /> <br /> (Enthält den Inhalt der Seite b, die in der Live Copy-Verzweigung manuell erstellt wurde)</td>
  </tr>
  <tr>
   <td><code> /bp-level-1</code></td>
   <td><code> /lc-level-1</code><br /> <br /> (Manuell in der Live Copy-Verzweigung erstellt)<br /> </td>
   <td><code> /lc-level-1</code><br /> <br /> (Enthält den Inhalt der Seite<br /> „child-level-1“, die in der Live Copy-Verzweigung manuell erstellt wurde)</td>
  </tr>
 </tbody>
</table>

## Rollout-Manager und Konfliktbehandlung {#rollout-manager-and-conflict-handling}

Mit dem Rollout-Manager können Sie das Konflikt-Management aktivieren oder deaktivieren.

Dies erfolgt mithilfe der [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) von **Day CQ WCM Rollout Manager**:

* **So können Sie einen Konflikt mit manuell erstellten Seiten beheben**:

  (`rolloutmgr.conflicthandling.enabled`)

  Legen Sie auf „true“ fest, wenn der Rollout-Manager Konflikte von einer Seite bewältigen soll, die in der Live Copy mit einem in der Blueprint vorhandenen Namen erstellt wurde.

AEM verfügt über ein [vordefiniertes Verhalten, wenn das Konflikt-Management deaktiviert wurde](#behavior-when-conflict-handling-deactivated).

## Konflikt-Handler {#conflict-handlers}

AEM nutzt Konflikt-Handler zum Lösen von Seitenkonflikten, die beim Rollout von Inhalten von einer Blueprint zu einer Live Copy vorliegen. Das Umbenennen von Seiten ist eine (die übliche) Methode zur Lösung solcher Konflikte. Es können mehrere Konflikt-Handler verwendet werden, um eine Auswahl verschiedener Verhaltensweisen zu ermöglichen.

AEM bietet:

* Den [standardmäßigen Konflikt-Handler](#default-conflict-handler):

   * `ResourceNameRolloutConflictHandler`

* Die Möglichkeit, eine [angepasster Handler](#customized-handlers).
* Den Service-Ranking-Mechanismus, mit dem Sie die Priorität jedes einzelnen Handlers festlegen können. Der Service mit dem höchsten Ranking wird verwendet.

### Standard-Konflikt-Handler {#default-conflict-handler}

Der standardmäßige Konflikt-Handler:

* Heißt `ResourceNameRolloutConflictHandler`

* Mit diesem Handler hat die Blueprint-Seite Vorrang.
* Das Service-Ranking für diesen Handler wurde als niedrig festgelegt, d. h. unterhalb des Standardwerts für die `service.ranking`-Eigenschaft, da davon ausgegangen wird, dass benutzerdefinierte Handler ein höheres Ranking benötigen. Allerdings ist das Ranking nicht das absolute Minimum, um bei Bedarf Flexibilität zu gewährleisten.

Dieser Konflikt-Handler hat Vorrang vor dem Blueprint. Die Live Copy-Seite `/b` wird (innerhalb der Live Copy-Verzweigung) nach `/b_msm_moved` verschoben.

* Live Copy: `/b`

  Wird (innerhalb der Live Copy) nach `/b_msm_moved` verschoben. Dies dient als Sicherung und stellt sicher, dass keine Inhalte verloren gehen.

   * `lc-level-1` wird nicht verschoben.

* Blueprint: `/b`

  Wird beim Rollout auf die Live Copy-Seite `/b` verschoben.

   * `bp-level-1` wird beim Rollout zur Live Copy verschoben.

**Nach dem Rollout**

<table>
 <tbody>
  <tr>
   <td><strong>Blueprint nach dem Rollout</strong></td>
   <td><strong>Live Copy nach dem Rollout</strong><br /> </td>
   <td></td>
   <td><strong>Live Copy nach dem Rollout</strong><br /> <br /> <br /> </td>
   <td><strong>Nach dem Rollout veröffentlichen</strong><br /> <br /> </td>
  </tr>
  <tr>
   <td><code>b</code></td>
   <td><code>b</code><br /> <br /> (Enthält den Inhalt der Blueprint-Seite b, die beim Rollout verschoben wurde)<br /> </td>
   <td></td>
   <td><code>b_msm_moved</code><br /> <br /> (Enthält den Inhalt der Seite b, die in der Live Copy-Verzweigung manuell erstellt wurde)</td>
   <td><code>b</code><br /> <br /> (Keine Änderung, enthält den Inhalt der Originalseite b, die manuell in der Live Copy-Verzweigung erstellt wurde und jetzt b_msm_moved heißt)<br /> </td>
  </tr>
  <tr>
   <td><code> /bp-level-1</code></td>
   <td><code class="code"> /bp-level-1</code></td>
   <td><code> /lc-level-1</code><br /> <br /> (Keine Änderung)</td>
   <td><code> </code></td>
   <td><code> /lc-level-1</code><br /> <br /> (Keine Änderung)</td>
  </tr>
 </tbody>
</table>

### Angepasste Handler {#customized-handlers}

Mit benutzerdefinierten Konflikt-Handlern können Sie Ihre eigenen Regeln implementieren. Mit dem Service-Ranking-Mechanismus können Sie auch definieren, wie sie mit anderen Handlern interagieren.

Benutzerdefinierte Konflikt-Handler können:

* Gemäß Ihren Anforderungen benannt werden.
* Gemäß Ihren Anforderungen entwickelt/konfiguriert werden. Beispiel: Sie können einen Handler so entwickeln, dass die Live Copy-Seite Vorrang erhält.
* So konzipiert sein, dass die Konfiguration unter Verwendung der [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) erfolgt. Insbesondere gilt:

   * **Dienstpriorität**:

     Bestimmt die Reihenfolge in Bezug auf andere Konflikt-Handler (`service.ranking`).

     Der Standardwert ist 0.

### Verhalten, wenn die Konflikt-Behandlung deaktiviert ist {#behavior-when-conflict-handling-deactivated}

Wenn Sie die [Konfliktbehandlung manuell deaktivieren](#rollout-manager-and-conflict-handling), ergreift AEM keine Maßnahmen bei konfliktbehafteten Seiten (das Rollout von nicht im Konflikt befindlichen Seiten erfolgt erwartungsgemäß).

>[!CAUTION]
>
>AEM gibt keinen Hinweis darauf, dass Konflikte ignoriert werden, da dieses Verhalten explizit konfiguriert werden muss. Daher wird davon ausgegangen, dass es sich um das erforderliche Verhalten handelt.

In diesem Fall hat die Live Copy effektiv Vorrang. Die Blueprint-Seite `/b` wird nicht kopiert und die Live Copy-Seite `/b` bleibt unberührt.

* Blueprint: `/b`

  Wird überhaupt nicht kopiert, sondern ignoriert.

* Live Copy: `/b`

  Hier gilt dasselbe.

<table>
 <caption>
   Nach dem Rollout
 </caption>
 <tbody>
  <tr>
   <td><strong>Blueprint nach dem Rollout</strong></td>
   <td><strong>Live Copy nach dem Rollout</strong><br /> <br /> <br /> </td>
   <td><strong>Nach dem Rollout veröffentlichen</strong><br /> <br /> </td>
  </tr>
  <tr>
   <td><code>b</code></td>
   <td><code>b</code><br /> <br /> (keine Änderung; enthält den Inhalt der Seite b, die in der Verzweigung der Live Copy manuell erstellt wurde)</td>
   <td><code>b</code><br /> <br /> (keine Änderung; enthält den Inhalt der Seite b, die manuell in der Verzweigung der Live Copy erstellt wurde)<br /> </td>
  </tr>
  <tr>
   <td><code> /bp-level-1</code><br /> </td>
   <td><code> /lc-level-1</code><br /> <br /> (Keine Änderung)</td>
   <td><code> /lc-level-1</code><br /> <br /> (Keine Änderung)</td>
  </tr>
 </tbody>
</table>

### Service-Rangfolge {#service-rankings}

Die [OSGi](https://www.osgi.org/)-Service-Rangfolge kann zum Definieren der Priorität von einzelnen Konflikt-Handlern verwendet werden.
