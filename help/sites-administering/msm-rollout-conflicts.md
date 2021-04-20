---
title: MSM-Rollout-Konflikte
seo-title: MSM-Rollout-Konflikte
description: Erfahren Sie, wie Sie Multi Site Manager-Rolloutkonflikte lösen.
seo-description: Erfahren Sie, wie Sie Multi Site Manager-Rolloutkonflikte lösen.
uuid: 7a640905-aae2-498e-b95c-2c73008fa1cd
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 16db5334-604f-44e2-9993-10d683dee5bb
feature: Multi Site Manager
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 59%

---


# MSM-Rollout-Konflikte{#msm-rollout-conflicts}

Konflikte können auftreten, wenn neue Seiten mit demselben Seitennamen sowohl in der Blueprint-Verzweigung als auch in einer abhängigen Live Copy-Verzweigung erstellt werden.

Solche Konflikte müssen nach dem Rollout gehandhabt und aufgelöst werden.

## Konfliktbehandlung {#conflict-handling}

Wenn Konfliktseiten (in den Blueprint- und Live Copy-Zweigen) vorhanden sind, gestattet Ihnen MSM die Definition, wie (oder sogar ob) dieser Konflikt behoben werden soll.

Um sicherzustellen, dass der Rollout nicht gesperrt ist, können mögliche Definitionen Folgendes umfassen:

* Welche Seite (Blueprint oder Live Copy) während des Rollouts Vorrang hat
* Welche Seiten umbenannt werden (und wie)
* Wie dies jeglichen veröffentlichten Inhalt beeinflusst

   Das Standardverhalten von AEM (Out-of-the-Box) besteht darin, dass veröffentlichte Inhalte davon unbeeinflusst bleiben. Wenn also eine Seite, die im Live Copy-Zweig manuell erstellt wurde, veröffentlicht wurde, wird dieser Inhalt nach der Konfliktbehandlung und dem Rollout auch weiterhin veröffentlicht.

Neben den Standardfunktionen können benutzerdefinierte Konflikt-Handler hinzugefügt werden, um unterschiedliche Regeln zu implementieren. Diese können auch das Veröffentlichen von Aktionen als Einzelprozess gestatten.

### Beispiel-Szenario {#example-scenario}

In den folgenden Abschnitten werden wir zum Veranschaulichen der verschiedenen Verfahren zur Konfliktbewältigung das Beispiel einer neuen Seite `b` verwenden, die sowohl im Blueprint- als auch im Live Copy-Zweig (manuell) erstellt wurde:

* Blueprint: `/b`

   Übergeordnet; mit 1 untergeordneter Seite, bp-level-1.

* Live Copy: `/b`

   Eine Seite, die manuell in der Live Copy-Verzweigung erstellt wurde; mit 1 untergeordneter Seite, `lc-level-1`.

   * Aktiviert beim Veröffentlichen als `/b` zusammen mit der untergeordneten Seite.

**Vor dem Rollout**

<table>
 <tbody>
  <tr>
   <td><strong>Blueprint vor dem Rollout</strong></td>
   <td><strong>Live Copy vor der Veröffentlichung</strong></td>
   <td><strong>vor der Veröffentlichung veröffentlichen</strong></td>
  </tr>
  <tr>
   <td><code>b</code> <br /> (erstellt in der Blueprint-Verzweigung, bereit für die Einführung)<br /> </td>
   <td><code>b</code> <br /> (manuell in einer Live-Kopie-Verzweigung erstellt)<br /> </td>
   <td><code>b</code> <br /> (enthält den Inhalt der Seite b, der manuell in der Live-Kopie-Verzweigung erstellt wurde)</td>
  </tr>
  <tr>
   <td><code> /bp-level-1</code></td>
   <td><code> /lc-level-1</code> <br /> (manuell in einer Live-Kopie-Verzweigung erstellt)<br /> </td>
   <td><code> /lc-level-1</code> <br /> (enthält den Inhalt der Seite<br /> untergeordneter Ebene-1, die manuell in der Live Copy-Verzweigung erstellt wurde)</td>
  </tr>
 </tbody>
</table>

## Rollout-Manager und Konfliktbehandlung {#rollout-manager-and-conflict-handling}

Mit dem Rollout-Manager können Sie das Konfliktmanagement aktivieren oder deaktivieren.

Dies erfolgt mithilfe der [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) von **Day CQ WCM Rollout Manager**:

* **Beheben Sie Konflikte mit manuell erstellten Seiten**:

   ( `rolloutmgr.conflicthandling.enabled`)

   Auf &quot;true&quot;setzen, wenn der Rollout-Manager Konflikte von einer Seite behandeln soll, die in der Live-Kopie mit einem Namen erstellt wurde, der im Entwurf vorhanden ist.

AEM verfügt über ein [vordefiniertes Verhalten, wenn das Konfliktmanagement deaktiviert wurde](#behavior-when-conflict-handling-deactivated).

## Konflikt-Handler {#conflict-handlers}

AEM nutzt Konflikt-Handler zum Lösen von Seitenkonflikten, die beim Rollout von Inhalten von einem Blueprint zu einer Live Copy vorliegen. Das Umbenennen von Seiten ist ein (das übliche) Verfahren zum Beheben derartiger Konflikte. Mehrere Konflikt-Handler können aktiv sein, um eine Reihe verschiedener Verhaltensweisen zu ermöglichen.

AEM stellt Folgendes bereit:

* Den [Standard-Konflikt-Handler](#default-conflict-handler):

   * `ResourceNameRolloutConflictHandler`

* [Die Möglichkeit, einen benutzerdefinierten Handler zu implementieren](#customized-handlers)
* Den Service-Ranking-Mechanismus, mit dem Sie die Priorität jedes einzelnen Handlers festlegen können. Der Service mit dem höchsten Ranking wird verwendet.

### Standard-Konflikt-Handler {#default-conflict-handler}

Der Standard-Konflikt-Handler:

* Wird als `ResourceNameRolloutConflictHandler` bezeichnet

* Mit diesem Handler hat die Blueprint-Seite Vorrang.
* Die Dienstrangliste für diesen Handler ist niedrig (&quot;d.h. unter dem Standardwert für die `service.ranking`-Eigenschaft), da davon ausgegangen wird, dass benutzerdefinierte Handler eine höhere Rangfolge benötigen. Allerdings ist das Ranking nicht das absolute Minimum, um bei Bedarf Flexibilität zu gewährleisten.

Dieser Konflikt-Handler gibt dem Blueprint Vorrang. Die Live Copy-Seite `/b` wird (innerhalb der Live Copy-Verzweigung) nach `/b_msm_moved` verschoben.

* Live Copy: `/b`

   Wird (innerhalb der Live-Kopie) nach `/b_msm_moved` verschoben. Dies dient als Sicherung und stellt sicher, dass keine Inhalte verloren gehen.

   * `lc-level-1` nicht verschoben.

* Blueprint: `/b`

   Wird auf die Live-Kopierseite `/b` Rollout ausgeführt.

   * `bp-level-1` wird beim Rollout auf die Live Copy-Seite verschoben.

**Nach dem Rollout**

<table>
 <tbody>
  <tr>
   <td><strong>Blueprint nach dem Rollout</strong></td>
   <td><strong>Live Copy nach der Aktualisierung</strong><br /> </td>
   <td></td>
   <td><strong>Live Copy nach der Aktualisierung</strong><br /> <br /> <br /> </td>
   <td><strong>nach der Veröffentlichung veröffentlichen</strong><br /> <br /> </td>
  </tr>
  <tr>
   <td><code>b</code></td>
   <td><code>b</code> <br /> (hat den Inhalt der Seite "Blueprint b", auf der das Rolout erfolgte)<br /> </td>
   <td></td>
   <td><code>b_msm_moved</code> <br /> (hat den Inhalt der Seite b, der manuell in der Live Copy-Verzweigung erstellt wurde)</td>
   <td><code>b</code> <br /> (keine Änderung; enthält den Inhalt der Originalseite b, der manuell in der Live-Kopie-Verzweigung erstellt wurde und jetzt "b_msm_move"heißt)<br /> </td>
  </tr>
  <tr>
   <td><code> /bp-level-1</code></td>
   <td><code class="code"> /bp-level-1</code></td>
   <td><code> /lc-level-1</code> <br /> (keine Änderung)</td>
   <td><code> </code></td>
   <td><code> /lc-level-1</code> <br /> (keine Änderung)</td>
  </tr>
 </tbody>
</table>

### Angepasste Handler {#customized-handlers}

Mit angepassten Konflikt-Handlern können Sie Ihre eigenen Regeln implementieren. Mit dem Service-Ranking-Mechanismus können Sie zudem festlegen, wie sie mit anderen Handlern interagieren.

Benutzerdefinierte Konflikt-Handler können:

* gemäß Ihren Anforderungen benannt werden;
* gemäß Ihren Anforderungen entwickelt/konfiguriert werden. Beispiel: Sie können einen Handler entwickeln, sodass die Live Copy-Seite Vorrang erhält.
* so konzipiert sein, dass die Konfiguration unter Verwendung der [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) erfolgt; insbesondere gilt:

   * **Dienstpriorität**:

      Definiert die Reihenfolge für andere Konflikthandler ( `service.ranking`).

      Der Standardwert ist 0.

### Verhalten, wenn die Konflikt-Behandlung deaktiviert ist {#behavior-when-conflict-handling-deactivated}

Wenn Sie [die Konfliktbehebung manuell deaktivieren](#rollout-manager-and-conflict-handling), ergreift AEM auf keiner der Konfliktseiten Maßnahmen (das Rollout von nicht im Konflikt befindlichen Seiten erfolgt erwartungsgemäß).

>[!CAUTION]
>
>AEM zeigt nicht an, dass Konflikte ignoriert werden, da dieses Verhalten explizit konfiguriert werden muss. Daher wird davon ausgegangen, dass dies das erforderliche Verhalten ist.

In diesem Fall hat die Live Copy effektiv Vorrang. Die Blueprint-Seite `/b` wird nicht kopiert und die Live Copy-Seite `/b` bleibt unberührt.

* Blueprint: `/b`

   Wird überhaupt nicht kopiert, wird aber ignoriert.

* Live Copy: `/b`

   Steht gleich.

<table>
 <caption>
   Nach dem Rollout
 </caption>
 <tbody>
  <tr>
   <td><strong>Blueprint nach dem Rollout</strong></td>
   <td><strong>Live Copy nach der Aktualisierung</strong><br /> <br /> <br /> </td>
   <td><strong>nach der Veröffentlichung veröffentlichen</strong><br /> <br /> </td>
  </tr>
  <tr>
   <td><code>b</code></td>
   <td><code>b</code> <br /> (keine Änderung; hat den Inhalt der Seite b, der manuell in der Live-Kopie-Verzweigung erstellt wurde)</td>
   <td><code>b</code> <br /> (keine Änderung; enthält den Inhalt der Seite b, der manuell in der Live-Kopie-Verzweigung erstellt wurde)<br /> </td>
  </tr>
  <tr>
   <td><code> /bp-level-1</code> </td>
   <td><code> /lc-level-1</code> <br /> (keine Änderung)</td>
   <td><code> /lc-level-1</code> <br /> (keine Änderung)</td>
  </tr>
 </tbody>
</table>

### Service-Rankings {#service-rankings}

Das [OSGi](https://www.osgi.org/)-Service-Ranking kann zum Definieren der Priorität von einzelnen Konflikt-Handlern verwendet werden.
