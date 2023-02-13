---
title: Repository-Neustrukturierung für AEM Communities in 6.4
seo-title: Repository Restructuring for AEM Communities in 6.4
description: Erfahren Sie, wie Sie die erforderlichen Änderungen vornehmen können, um zu der neuen Repository-Struktur in AEM 6.4 für Communities zu migrieren.
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.4 for Communities.
uuid: d161655f-4074-44a7-8d69-38e80934c58b
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 7383265b-0ed4-4ea7-b741-0a417d187bdd
feature: Upgrading
exl-id: 4d2bdd45-a29a-4936-b8da-f7e011d81e83
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '1011'
ht-degree: 100%

---

# Repository-Neustrukturierung für AEM Communities in 6.5 {#repository-restructuring-for-aem-communities-in}

Wie auf der übergeordneten Seite [Repository-Neustrukturierung in AEM 6.5](/help/sites-deploying/repository-restructuring.md) beschrieben, sollten Kunden, die auf AEM 6.4 aktualisieren, diese Seite verwenden, um den Arbeitsaufwand im Zusammenhang mit Repository-Neustrukturierungen einzuschätzen, die sich auf AEM Communities auswirken. Einige Änderungen erfordern einen Arbeitsaufwand während der Aktualisierung auf AEM 6.5, während andere bis zu einer zukünftigen Aktualisierung verschoben werden können.

**Mit der Aktualisierung auf 6.5**

* [Vorlagen für E-Mail-Benachrichtigungen](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#e-mail-notification-templates)
* [Abonnement-Konfigurationen](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#subscription-configurations)

**Vor zukünftigen Aktualisierungen**

* [Badging-Konfigurationen](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#badging-configurations)
* [Klassische Konsolen-Designs für Communities](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#classic-communities-console-designs)
* [Konfigurationen zur Anmeldung über Facebook](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#facebook-social-login-configurations)
* [Konfigurationen zur Sprachwahl](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#language-options-configurations)

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
   <td><p>Manuelle Migration wird benötigt, wenn Sie zu einem neuen Pfad unter „<code>/apps/settings</code>“ wechseln möchten. Sie können den Granite Configuration Manager verwenden, um die Migration durchzuführen.</p> <p>Sie können die Migration durchführen, indem Sie auf dem Knoten <code>/libs/settings/community/subscriptions</code> die Eigenschaft <code>mergeList</code> auf <code>true</code> festlegen und einen untergeordneten Knoten <code>nt:unstructured</code> hinzuzufügen.</p> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Abonnement-Konfigurationen {#subscription-configurations}

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
   <td><p>Manuelle Migration wird benötigt, wenn Sie zu einem neuen Pfad unter „<code>/apps/settings</code>“ wechseln möchten. Sie können den Granite Configuration Manager verwenden, um die Migration durchzuführen.</p> <p>Sie können die Migration durchführen, indem Sie auf dem Knoten <code>/libs/settings/community/subscriptions</code> die Eigenschaft <code>mergeList</code> auf <code>true</code> festlegen und einen untergeordneten Knoten <code>nt:unstructured</code> hinzuzufügen.</p> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Schlagwortkonfigurationen {#watchwords-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td>/etc/watchwords</td>
  </tr>
  <tr>
   <td><strong>Neue Speicherorte</strong></td>
   <td>/libs/community/watchwords</td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td>Eine Aufgabe zur verzögerten Migration steht zur Verfügung, um die Communities-Konfigurationen zu bereinigen.<br /> <p>Die Aufgabe verschiebt Schlagwörter von <code>/etc/watchwords</code> nach <code>/conf/global/settings/community/watchwords</code>.</p> <p>Wenn benutzerdefinierte Schlagwörter in SCM gespeichert werden, sollten sie anschließend in <code>/apps/settings/...</code> bereitgestellt werden, und Sie müssen sicherstellen, dass es keine Überlagerung mit einer <code>/conf/global/settings/...</code>-Konfiguration gibt, die Vorrang hätte.</p> <p>Migrationsaufgabe entfernt <code>/etc</code>-Speicherorte.</p> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

## Vor zukünftigen Aktualisierungen {#prior-to-upgrade}

### Badging-Konfigurationen {#badging-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><code>/etc/community/badging</code></td>
  </tr>
  <tr>
   <td><strong>Neue Speicherorte</strong></td>
   <td><p><strong>Badge-Regeln:</strong></p> <p><code>/libs/settings/community/badging</code></p> <p><strong>Badge-Bilder: </strong></p> <p>Für Standardbilder: <code>/etc/community/badging/images are moved to /libs/community/badging/images</code></p> <p>Für benutzerdefinierte Bilder: <code>/content/community/badging/images</code></p> <p> </p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Manuelle Migration ist erforderlich.</p> <p>Wenn Ihre Instanz die Badging-/Bewertungsregeln angepasst hat, gibt es keine automatisierte Möglichkeit, alle Regeln in einem Behälter („Bucket“) zu platzieren. Sie benötigen Kundenangaben dazu, welchen Konfigurations-Bucket (global oder Site-spezifisch) Sie für Ihre Site verwenden möchten.</p> <p>Keine Benutzeroberfläche verfügbar, um Badging und Bewertung für eine Site zu konfigurieren.</p> <p>So nehmen Sie eine Anpassung an eine neue Repository-Sturktur vor:</p>
    <ol>
     <li>Erstellen Sie mit dem <strong>Konfigurationsbrowser</strong> unter <strong>Tools</strong> einen Bucket für den Site-Kontext.</li>
     <li>Wechseln Sie zum Stammordner der Site.</li>
     <li>Legen Sie <code>cq:confproperty</code> auf den Pfad des Buckets fest, in dem Sie alle Ihre Einstellungen speichern möchten. Dasselbe kann über die Site <strong>Bearbeitungsassistent - Eingabe der Cloud-Konfiguration festlegen</strong> festgelegt werden.</li>
     <li>Verschieben Sie die relevanten Badging- und Bewertungsregeln von <code>/etc/community/*</code> in den im vorherigen Schritt erstellten Kontext-Bucket der Site.</li>
     <li>Passen Sie die Eigenschaften der Badging- und Bewertungsregeln im Stammverzeichnis der Site an, um relative Referenzen auf neue Speicherorte der Regeln zu haben.
      <ol>
       <li>Beispiel: Bei der Eigenschaft <code>cq:conf = /conf/we-retail</code> gilt <code>badgingRules [] = community/badging/rules</code>, wenn Regeln jetzt in diesen neuen Bucket verschoben werden.</li>
      </ol> </li>
     <li>Passen Sie auf die gleiche Weise die Verweise auf Bewertungsregeln in einem Badging-Regelknoten an, um einen relativen Pfad zu erhalten.</li>
    </ol> <p> </p> <p>Schließlich bereinigen Sie durch Entfernen der Ressource <code>/etc/community/badging</code></p> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Klassische Konsolen-Designs für Communities {#classic-communities-console-designs}

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
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Konfigurationen zur Anmeldung über Facebook {#facebook-social-login-configurations}

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
       <li>Kopieren Sie alle neuen Facebook-Cloud-Konfigurationen vom bisherigen Speicherort an den entsprechenden neuen Speicherort unter <code>/conf/global or /conf/&lt;tenant&gt;</code>.</li>
      </ol> </li>
     <li>Aktualisieren Sie jedes Stammverzeichnis der AEM Communities-Site, um auf die neue Konfiguration zur Anmeldung über Facebook zu verweisen, indem Sie die Eigenschaft <code>[cq:Page]/jcr:content@cq:conf</code> auf den absoluten Pfad des neuen Speicherorts festlegen.</li>
     <li>Trennen Sie den bestehenden Facebook Connect Cloud Service von sämtlichen Stammverzeichnissen der AEM Communities-Sites, die aktualisiert wurden, um auf den neuen Speicherort zu verweisen.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Konfigurationen zur Sprachwahl {#language-options-configurations}

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
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Konfigurationen zur Anmeldung über Pinterest {#pinterest-social-login-configurations}

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
       <li>Kopieren Sie alle neuen Pinterest-Cloud-Konfigurationen vom bisherigen Speicherort an den entsprechenden neuen Speicherort unter <code>/conf/global or /conf/&lt;tenant&gt;</code>.</li>
      </ol> </li>
     <li>Aktualisieren Sie jedes Stammverzeichnis der AEM Communities-Site, um auf die neue Konfiguration zur Anmeldung über Pinterest zu verweisen, indem Sie die Eigenschaft <code>[cq:Page]/jcr:content@cq:conf</code> auf den absoluten Pfad des neuen Speicherorts festlegen.</li>
     <li>Trennen Sie den bestehenden Pinterest Connect Cloud Service von sämtlichen Stammverzeichnissen der AEM Communities-Sites, die aktualisiert wurden, um auf den neuen Speicherort zu verweisen.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Bewertungskonfigurationen {#scoring-configurations}

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
   <td><p>Zur Anpassung an die neue Repository-Struktur können Bewertungsregeln gespeichert werden unter: <code>/apps/settings/</code> oder /<code>conf/.../settings</code></p>
    <ol>
     <li>Für <code>/apps/settings</code> würde dies als globale oder Standardregeln dienen, die in SCM verwaltet werden.</li>
    </ol> <p>Erstellen Sie kontextbezogene Konfigurationen in <code>/conf/</code>, indem Sie CRXDELite verwenden:</p>
    <ol>
     <li>Erstellen Sie die Aktionen im gewünschten Speicherort <code>/conf/.../settings</code>.<br /> </li>
     <li>Für die Communities-Site muss die Eigenschaft <code>cq:conf </code> festgelegt sein.
      <ol>
       <li>Wenn <code>cq:conf</code> nicht festgelegt ist, würden die Bewertungsregeln direkt aus dem angegebenen Pfad für die Eigenschaft <code>scoringRules</code> auf dem Stammknoten der Site gelesen, z. B.: <code>/content/we-retail/us/en/community/jcr:content</code></li>
      </ol> </li>
    </ol> <p>Datenbereinigung: Entfernen Sie die Ressource <code>/etc/community/scoring</code></p> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>

### Konfigurationen zur Anmeldung über Twitter {#twitter-social-login-configurations}

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
       <li>Kopieren Sie alle neuen Twitter-Cloud-Konfigurationen vom bisherigen Speicherort an den entsprechenden neuen Speicherort unter <code>/conf/global or /conf/&lt;tenant&gt;</code>.</li>
      </ol> </li>
     <li>Aktualisieren Sie jedes Stammverzeichnis der AEM Communities-Site, um auf die neue Konfiguration zur Anmeldung über Twitter zu verweisen, indem Sie die Eigenschaft <code>[cq:Page]/jcr:content@cq:conf</code> auf den absoluten Pfad des neuen Speicherorts festlegen.</li>
     <li>Trennen Sie den bestehenden Twitter Connect Cloud Service von sämtlichen Stammverzeichnissen der AEM Communities-Sites, die aktualisiert wurden, um auf den neuen Speicherort zu verweisen.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
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
   <td><strong>Anmerkungen</strong></td>
   <td>Die vorhandenen benutzerdefinierten Vorlagen werden verschoben nach <code>/conf/global/settings/community/template/&lt;groups/sites/functions&gt;</code></td>
  </tr>
 </tbody>
</table>
