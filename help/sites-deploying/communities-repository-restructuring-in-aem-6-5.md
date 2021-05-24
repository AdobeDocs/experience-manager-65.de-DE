---
title: Repository-Neustrukturierung für AEM Communities in 6.4
seo-title: Repository-Neustrukturierung für AEM Communities in 6.4
description: Erfahren Sie, wie Sie die erforderlichen Änderungen vornehmen können, um zu der neuen Repository-Struktur in AEM 6.4 für Communities zu migrieren.
seo-description: Erfahren Sie, wie Sie die erforderlichen Änderungen vornehmen können, um zu der neuen Repository-Struktur in AEM 6.4 für Communities zu migrieren.
uuid: d161655f-4074-44a7-8d69-38e80934c58b
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 7383265b-0ed4-4ea7-b741-0a417d187bdd
feature: Aktualisieren
exl-id: 4d2bdd45-a29a-4936-b8da-f7e011d81e83
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1038'
ht-degree: 60%

---

# Repository-Neustrukturierung für AEM Communities in 6.5 {#repository-restructuring-for-aem-communities-in}

Wie auf der übergeordneten Seite [Repository-Neustrukturierung in AEM 6.4](/help/sites-deploying/repository-restructuring.md) beschrieben, sollten Kunden, die auf AEM 6.5 aktualisieren, diese Seite verwenden, um den Arbeitsaufwand im Zusammenhang mit Repository-Änderungen zu bewerten, die sich auf die AEM Communities-Lösung auswirken. Einige Änderungen erfordern während des Aktualisierungsprozesses von AEM 6.5 Arbeitsaufwand, während andere bis zu einer zukünftigen Aktualisierung verschoben werden können.

**Mit der Aktualisierung auf 6.5**

* [Vorlagen für E-Mail-Benachrichtigungen](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#e-mail-notification-templates)
* [Abonnement-Konfigurationen](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#subscription-configurations)

**Vor der künftigen Aktualisierung**

* [Badging-Konfigurationen](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#badging-configurations)
* [Klassische Konsolen-Designs für Communities](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#classic-communities-console-designs)
* [Konfigurationen zur Anmeldung über Facebook](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#facebook-social-login-configurations)
* [Sprachwahl-Konfigurationen](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#language-options-configurations)

* [Konfigurationen zur Anmeldung über Pinterest](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#pinterest-social-login-configurations)
* [Bewertungskonfigurationen](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#scoring-configurations)
* [Konfigurationen zur Anmeldung über Twitter](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#twitter-social-login-configurations)
* [Verschiedenes](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#misc)

## Mit der Aktualisierung auf 6.5 {#with-upgrade}

### Vorlagen für E-Mail-Benachrichtigungen {#e-mail-notification-templates}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/community/notifications</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><code>/libs/settings/community/notifications</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Manuelle Migration ist erforderlich, wenn Sie unter "<code>/apps/settings</code>"zu einem neuen Pfad wechseln möchten. Sie können den Granite Configuration Manager verwenden, um die Migration durchführen.</p> <p>Sie können die Migration durchführen, indem Sie die Eigenschaft <code>mergeList</code> auf <code>true</code> auf dem Knoten "<code>/libs/settings/community/subscriptions</code>"festlegen und einen untergeordneten Knoten <code>nt:unstructured</code> hinzufügen.</p> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Abonnement-Konfigurationen  {#subscription-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/community/subscriptions</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><code>/libs/settings/community/subscriptions</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Manuelle Migration ist erforderlich, wenn Sie unter "<code>/apps/settings</code>"zu einem neuen Pfad wechseln möchten. Sie können den Granite Configuration Manager verwenden, um die Migration durchführen.</p> <p>Sie können die Migration durchführen, indem Sie die Eigenschaft <code>mergeList</code> auf <code>true</code> auf dem Knoten "<code>/libs/settings/community/subscriptions</code>"festlegen und einen untergeordneten Knoten <code>nt:unstructured</code> hinzufügen.</p> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Schlagwortkonfigurationen  {#watchwords-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td>/etc/watchwords</td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td>/libs/community/watchwords</td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td>Eine Aufgabe zur verzögerten Migration steht zur Verfügung, um die Communities-Konfigurationen zu bereinigen.<br /> <p>Die Aufgabe verschiebt Schlagwörter von <code>/etc/watchwords</code> in <code>/conf/global/settings/community/watchwords</code>.</p> <p>Wenn angepasste Schlagwörter in SCM gespeichert sind, sollten sie in <code>/apps/settings/...</code> bereitgestellt werden und Sie müssen sicherstellen, dass keine überlagernde <code>/conf/global/settings/...</code>-Konfiguration vorhanden ist, die Vorrang hätte.</p> <p>Migrationsaufgabe entfernt <code>/etc</code> Speicherorte.</p> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

## Vor der künftigen Aktualisierung {#prior-to-upgrade}

### Badging-Konfigurationen {#badging-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/community/badging</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><strong>Badge-Regeln:</strong></p> <p><code>/libs/settings/community/badging</code></p> <p><strong>Badge-Bilder: </strong></p> <p>Für Standardbilder: <code>/etc/community/badging/images are moved to /libs/community/badging/images</code></p> <p>Für benutzerdefinierte Bilder: <code>/content/community/badging/images</code></p> <p> </p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Manuelle Migration ist erforderlich.</p> <p>Wenn Ihre Instanz die Badging-/Bewertungsregeln angepasst hat, gibt es keine automatisierte Möglichkeit, alle Regeln in einem Behälter („Bucket“) zu platzieren. Sie benötigen Kundenangaben dazu, welchen Konfigurations-Bucket (global oder Site-spezifisch) Sie für Ihre Site verwenden möchten.</p> <p>Keine Benutzeroberfläche verfügbar, um Badging und Bewertung für eine Site zu konfigurieren.</p> <p>So nehmen Sie eine Anpassung an eine neue Repository-Sturktur vor:</p>
    <ol>
     <li>Erstellen Sie mit dem <strong>Konfigurationsbrowser</strong> unter <strong>Tools</strong> einen Bucket für den Site-Kontext.</li>
     <li>Wechseln Sie zum Stammordner der Site.</li>
     <li>Setzen Sie <code>cq:confproperty</code> auf den Pfad des Buckets, in dem Sie alle Ihre Einstellungen speichern wollen. Dasselbe kann über die Site <strong>Bearbeitungsassistent - Eingabe der Cloud-Konfiguration festlegen</strong> festgelegt werden.</li>
     <li>Verschieben Sie die relevanten Badging- und Scoring-Regeln von <code>/etc/community/*</code> in den im vorherigen Schritt erstellten Site-Kontext-Behälter.</li>
     <li>Passen Sie die Eigenschaften der Badging- und Bewertungsregeln im Stammverzeichnis der Site an, um relative Referenzen auf neue Speicherorte der Regeln zu haben.
      <ol>
       <li>Wenn beispielsweise die -Eigenschaft für <code>cq:conf = /conf/we-retail</code> ist, dann <code>badgingRules [] = community/badging/rules</code> wenn die Regeln jetzt in diesen neuen Behälter verschoben werden.</li>
      </ol> </li>
     <li>Passen Sie auf die gleiche Weise die Verweise auf Bewertungsregeln in einem Badging-Regel-Knoten an, um einen relativen Pfad zu erhalten.</li>
    </ol> <p> </p> <p>Bereinigen Sie schließlich durch Entfernen der Ressource. <code>/etc/community/badging</code></p> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Klassische Konsolen-Designs für Communities  {#classic-communities-console-designs}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/designs/social/console</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/libs/settings/wcm/designs/social/console</code></p> <p><code>/apps/settings/wcm/designs/social/console</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td>Nicht zutreffend</td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Konfigurationen zur Anmeldung über Facebook  {#facebook-social-login-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/cloudservices/facebookconnect</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code class="code">/conf/global/settings/cloudconfigs/facebookconnect
       </code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/facebookconnect</code></p> <p> </p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Alle neuen Facebook-Cloud-Konfigurationen müssen zum neuen Speicherort migriert werden.</p>
    <ol>
     <li>Migrieren Sie vorhandene Konfigurationen im bisherigen Speicherort an den neuen Speicherort.
      <ol>
       <li>Erstellen Sie manuell neue Konfigurationen zur Anmeldung über Facebook über die AEM-Authoring-Benutzeroberfläche unter <strong>Tools &gt; Cloud-Services &gt; Konfiguration zur Anmeldung über Facebook</strong>.<br /> oder <br /> </li>
       <li>Kopieren Sie alle neuen Facebook Cloud-Konfigurationen vom vorherigen Speicherort an den entsprechenden neuen Speicherort unter <code>/conf/global or /conf/&lt;tenant&gt;</code>.</li>
      </ol> </li>
     <li>Aktualisieren Sie jeden AEM Communities-Site-Stamm, um auf die neue Facebook Social-Anmeldekonfiguration zu verweisen, indem Sie die Eigenschaft <code>[cq:Page]/jcr:content@cq:conf</code> auf den absoluten Pfad am neuen Speicherort setzen.</li>
     <li>Trennen Sie den bestehenden Facebook Connect Cloud Service von sämtlichen Stammverzeichnissen der AEM Communities-Sites, die aktualisiert wurden, um auf den neuen Speicherort zu verweisen.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Sprachwahl-Konfigurationen  {#language-options-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/social/config/languageOpts</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><code>/libs/social/translation/languageOpts</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Konfigurationen zur Anmeldung über Pinterest  {#pinterest-social-login-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/cloudservices/pinterestconnect</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code class="code">/conf/global/settings/cloudconfigs/pinterestconnect
       </code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/pinterestconnect</code></p> <p> </p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Alle neuen Pinterest-Cloud-Konfigurationen müssen zum neuen Speicherort migriert werden.</p>
    <ol>
     <li>Migrieren Sie vorhandene Konfigurationen im bisherigen Speicherort an den neuen Speicherort.
      <ol>
       <li>Erstellen Sie manuell neue Konfigurationen zur Anmeldung über Pinterest über die AEM-Authoring-Benutzeroberfläche unter <strong>Tools &gt; Cloud-Services &gt; Konfiguration zur Anmeldung über Pinterest</strong>.<br /> oder</li>
       <li>Kopieren Sie alle neuen Pinterest Cloud-Konfigurationen vom vorherigen Speicherort an den entsprechenden neuen Speicherort unter <code>/conf/global or /conf/&lt;tenant&gt;</code>.</li>
      </ol> </li>
     <li>Aktualisieren Sie jeden AEM Communities-Site-Stamm, um auf die neue Pinterest Social-Anmeldekonfiguration zu verweisen, indem Sie die Eigenschaft <code>[cq:Page]/jcr:content@cq:conf</code> auf den absoluten Pfad am neuen Speicherort einstellen.</li>
     <li>Trennen Sie den bestehenden Pinterest Connect Cloud Service von sämtlichen Stammverzeichnissen der AEM Communities-Sites, die aktualisiert wurden, um auf den neuen Speicherort zu verweisen.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Bewertungskonfigurationen  {#scoring-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/community/scoring</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><code>/libs/settings/community/scoring</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Zur Anpassung an die neue Repository-Struktur können Scoring-Regeln in <code>/apps/settings/</code> oder / gespeichert werden.<code>conf/.../settings</code></p>
    <ol>
     <li>Für <code>/apps/settings</code> würde dies als globale oder Standardregeln fungieren, die in SCM verwaltet werden.</li>
    </ol> <p>Erstellen Sie kontextbezogene Konfigurationen in <code>/conf/</code> mithilfe von CRXDELite:</p>
    <ol>
     <li>Erstellen Sie die Konfigurationen im gewünschten <code>/conf/.../settings</code>-Speicherort<br /> </li>
     <li>Auf der Communities-Site muss die Eigenschaft <code>cq:conf </code>property festgelegt sein.
      <ol>
       <li>Wenn kein <code>cq:conf</code> festgelegt ist, werden die Scoring-Regeln direkt aus dem angegebenen Pfad für die Eigenschaft "<code>scoringRules</code>"im Stammknoten der Site gelesen, z. B.: <code>/content/we-retail/us/en/community/jcr:content</code></li>
      </ol> </li>
    </ol> <p>Bereinigung: Ressource entfernen <code>/etc/community/scoring</code></p> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Konfigurationen zur Anmeldung über Twitter  {#twitter-social-login-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/cloudservices/twitterconnect</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code class="code">/conf/global/settings/cloudconfigs/twitterconnect
       </code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/twitterconnect</code></p> <p> </p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Alle neuen Twitter-Cloud-Konfigurationen müssen zum neuen Speicherort migriert werden.</p>
    <ol>
     <li>Migrieren Sie vorhandene Konfigurationen im bisherigen Speicherort an den neuen Speicherort.
      <ol>
       <li>Erstellen Sie manuell neue Konfigurationen zur Anmeldung über Twitter über die AEM-Authoring-Benutzeroberfläche unter <strong>Tools &gt; Cloud-Services &gt; Konfiguration zur Anmeldung über Twitter</strong>.<br /> oder <br /> </li>
       <li>Kopieren Sie alle neuen Twitter Cloud-Konfigurationen vom vorherigen Speicherort an den entsprechenden neuen Speicherort unter <code>/conf/global or /conf/&lt;tenant&gt;</code>.</li>
      </ol> </li>
     <li>Aktualisieren Sie jeden AEM Communities-Site-Stamm, um auf die neue Twitter Social-Anmeldekonfiguration zu verweisen, indem Sie die Eigenschaft <code>[cq:Page]/jcr:content@cq:conf</code> auf den absoluten Pfad am neuen Speicherort setzen.</li>
     <li>Trennen Sie den bestehenden Twitter Connect Cloud Service von sämtlichen Stammverzeichnissen der AEM Communities-Sites, die aktualisiert wurden, um auf den neuen Speicherort zu verweisen.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Verschiedenes {#misc}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/community/templates</code></td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><code>/libs/settings/community/templates</code></td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Adobe hat ein Migrationsprogramm bereitgestellt unter:</p> <p><a href="https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-template-migration">https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-template-migration</a></p> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Die vorhandenen benutzerdefinierten Vorlagen werden zu <code>/conf/global/settings/community/template/&lt;groups/sites/functions&gt;</code></td>
  </tr>
 </tbody>
</table>
