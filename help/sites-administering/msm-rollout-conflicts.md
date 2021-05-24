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
feature: Multi-Site-Manager
exl-id: e145e79a-c363-4a33-b9f9-99502ed20563
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 62%

---

# MSM-Rollout-Konflikte{#msm-rollout-conflicts}

Konflikte können auftreten, wenn neue Seiten mit demselben Seitennamen sowohl in der Blueprint-Verzweigung als auch in einer abhängigen Live Copy-Verzweigung erstellt werden.

Solche Konflikte müssen nach dem Rollout gehandhabt und aufgelöst werden.

## Konfliktbehandlung  {#conflict-handling}

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

   eine Übergeordnete Seite; mit einer untergeordneten Seite, bp-level-1.

* Live Copy: `/b`

   Eine manuell im Live Copy-Zweig erstellte Seite; mit einer untergeordneten Seite, `lc-level-1`.

   * Bei Veröffentlichung als `/b` aktiviert, zusammen mit der untergeordneten Seite.

**Vor dem Rollout**

<table>
 <tbody>
  <tr>
   <td><strong>Blueprint vor Rollout</strong></td>
   <td><strong>Live Copy vor Rollout</strong></td>
   <td><strong>vor dem Rollout veröffentlichen</strong></td>
  </tr>
  <tr>
   <td><code>b</code> <br /> (erstellt in Blueprint-Verzweigung, bereit für Rollout)<br /> </td>
   <td><code>b</code> <br /> (manuell im Live Copy-Zweig erstellt)<br /> </td>
   <td><code>b</code> <br /> (enthält den Inhalt der Seite b, die manuell im Live Copy-Zweig erstellt wurde)</td>
  </tr>
  <tr>
   <td><code> /bp-level-1</code></td>
   <td><code> /lc-level-1</code> <br /> (manuell im Live Copy-Zweig erstellt)<br /> </td>
   <td><code> /lc-level-1</code> <br /> (enthält den Inhalt der Seite<br /> der untergeordneten Ebene-1, die manuell im Live Copy-Zweig erstellt wurde)</td>
  </tr>
 </tbody>
</table>

## Rollout-Manager und Konfliktbehandlung {#rollout-manager-and-conflict-handling}

Mit dem Rollout-Manager können Sie das Konflikt-Management aktivieren oder deaktivieren.

Dies erfolgt mithilfe der [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) von **Day CQ WCM Rollout Manager**:

* **Konflikt mit manuell erstellten Seiten** beheben:

   ( `rolloutmgr.conflicthandling.enabled`)

   Setzen Sie dies auf &quot;true&quot;, wenn der Rollout-Manager Konflikte von einer Seite handhaben soll, die in der Live Copy mit einem Namen erstellt wurde, der im Blueprint vorhanden ist.

AEM verfügt über ein [vordefiniertes Verhalten, wenn das Konflikt-Management deaktiviert wurde](#behavior-when-conflict-handling-deactivated).

## Konflikt-Handler {#conflict-handlers}

AEM nutzt Konflikt-Handler zum Lösen von Seitenkonflikten, die beim Rollout von Inhalten von einem Blueprint zu einer Live Copy vorliegen. Das Umbenennen von Seiten ist ein (das übliche) Verfahren zum Beheben derartiger Konflikte. Mehrere Konflikt-Handler können aktiv sein, um eine Reihe verschiedener Verhaltensweisen zu ermöglichen.

AEM stellt Folgendes bereit:

* Den [Standard-Konflikt-Handler](#default-conflict-handler):

   * `ResourceNameRolloutConflictHandler`

* Die Möglichkeit, einen [benutzerdefinierten Handler](#customized-handlers) zu implementieren.
* Den Service-Ranking-Mechanismus, mit dem Sie die Priorität jedes einzelnen Handlers festlegen können. Der Service mit dem höchsten Ranking wird verwendet.

### Standard-Konflikt-Handler {#default-conflict-handler}

Der Standard-Konflikt-Handler:

* Wird genannt `ResourceNameRolloutConflictHandler`

* Mit diesem Handler hat die Blueprint-Seite Vorrang.
* Der Service-Rang für diesen Handler ist niedrig (&quot;d. h. unter dem Standardwert für die Eigenschaft `service.ranking`), da davon ausgegangen wird, dass benutzerdefinierte Handler einen höheren Rang benötigen. Allerdings ist das Ranking nicht das absolute Minimum, um bei Bedarf Flexibilität zu gewährleisten.

Dieser Konflikt-Handler gibt dem Blueprint Vorrang. Die Live Copy-Seite `/b` wird (innerhalb des Live Copy-Zweigs) nach `/b_msm_moved` verschoben.

* Live Copy: `/b`

   Wird (innerhalb der Live Copy) nach `/b_msm_moved` verschoben. Dies dient als Sicherung und stellt sicher, dass keine Inhalte verloren gehen.

   * `lc-level-1` wird nicht verschoben.

* Blueprint: `/b`

   Wird auf die Live Copy-Seite `/b` übertragen.

   * `bp-level-1` wird beim Rollout auf die Live Copy-Seite verschoben.

**Nach dem Rollout**

<table>
 <tbody>
  <tr>
   <td><strong>Blueprint nach Rollout</strong></td>
   <td><strong>Live Copy nach Rollout</strong><br /> </td>
   <td></td>
   <td><strong>Live Copy nach Rollout</strong><br /> <br /> <br /> </td>
   <td><strong>nach dem Rollout veröffentlichen</strong><br /> <br /> </td>
  </tr>
  <tr>
   <td><code>b</code></td>
   <td><code>b</code> <br /> (hat den Inhalt der Blueprint-Seite b, die bereitgestellt wurde)<br /> </td>
   <td></td>
   <td><code>b_msm_moved</code> <br /> (weist den Inhalt der Seite b auf, die manuell im Live Copy-Zweig erstellt wurde)</td>
   <td><code>b</code> <br /> (keine Änderung; enthält den Inhalt der Originalseite b , die manuell im Live Copy-Zweig erstellt wurde und jetzt als b_msm_moved bezeichnet wird)<br /> </td>
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

      Definiert die Reihenfolge für andere Konflikt-Handler ( `service.ranking`).

      Der Standardwert ist 0.

### Verhalten, wenn die Konflikt-Behandlung deaktiviert ist {#behavior-when-conflict-handling-deactivated}

Wenn Sie [die Konfliktbehebung manuell deaktivieren](#rollout-manager-and-conflict-handling), ergreift AEM auf keiner der Konfliktseiten Maßnahmen (das Rollout von nicht im Konflikt befindlichen Seiten erfolgt erwartungsgemäß).

>[!CAUTION]
>
>AEM zeigt nicht an, dass Konflikte ignoriert werden, da dieses Verhalten explizit konfiguriert werden muss. Daher wird davon ausgegangen, dass dies das erforderliche Verhalten ist.

In diesem Fall hat die Live Copy effektiv Vorrang. Die Blueprint-Seite `/b` wird nicht kopiert und die Live Copy-Seite `/b` bleibt unberührt.

* Blueprint: `/b`

   wird überhaupt nicht kopiert, sondern ignoriert.

* Live Copy: `/b`

   Bleibt gleich.

<table>
 <caption>
   Nach dem Rollout
 </caption>
 <tbody>
  <tr>
   <td><strong>Blueprint nach Rollout</strong></td>
   <td><strong>Live Copy nach Rollout</strong><br /> <br /> <br /> </td>
   <td><strong>nach dem Rollout veröffentlichen</strong><br /> <br /> </td>
  </tr>
  <tr>
   <td><code>b</code></td>
   <td><code>b</code> <br /> (keine Änderung; den Inhalt der Seite b hat, die manuell im Live Copy-Zweig erstellt wurde)</td>
   <td><code>b</code> <br /> (keine Änderung; enthält den Inhalt der Seite b , die manuell im Live Copy-Zweig erstellt wurde)<br /> </td>
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
