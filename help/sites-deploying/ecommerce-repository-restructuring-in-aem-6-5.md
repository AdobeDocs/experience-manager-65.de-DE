---
title: E-Commerce-Repository-Neustrukturierung in AEM 6.5
description: Erfahren Sie, wie Sie die notwendigen Änderungen vornehmen, um in AEM 6.5 für E-Commerce zur neuen Repository-Struktur zu migrieren.
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
feature: Upgrading
exl-id: 78b7c497-c474-4308-bfab-8f424b5f7268
source-git-commit: 5af420c8e95fed88a8516cce27b8bbc7d3974e75
workflow-type: ht
source-wordcount: '201'
ht-degree: 100%

---

# E-Commerce-Repository-Neustrukturierung in AEM 6.5{#e-commerce-repository-restructuring-in-aem}

Wie auf der übergeordneten Seite [Repository-Neustrukturierung in AEM 6.5](/help/sites-deploying/repository-restructuring.md) beschrieben, sollten Kunden, die auf AEM 6.5 aktualisieren, diese Seite verwenden, um den Arbeitsaufwand im Zusammenhang mit Repository-Neustrukturierungen einzuschätzen, die sich auf die AEM E-Commerce-Lösung auswirken. Einige Änderungen erfordern einen Arbeitsaufwand während des Upgrades auf AEM 6.5, während andere auf eine zukünftige Aktualisierung verschoben werden können.

## Mit der Aktualisierung auf 6.5 {#with-upgrade}

### Produkt-, Auftrags-, Sammlungs-, Klassifizierungs-, Versandarten- und Zahlungsartendaten {#product-order-collections-classifications-shipping-methods-and-payment-methods-data}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><p><code>/etc/commerce/products</code></p> <p><code>/etc/commerce/orders</code></p> <p><code>/etc/commerce/collections</code></p> <p><code>/etc/commerce/classifications</code></p> <p><code>/etc/commerce/shipping-methods</code></p> <p><code>/etc/commerce/payment-methods</code></p> </td>
  </tr>
  <tr>
   <td><strong>Neue Speicherorte</strong></td>
   <td><p><code>/var/commerce/products</code></p> <p><code>/var/commerce/orders</code></p> <p><code>/var/commerce/collections</code></p> <p><code>/var/commerce/classifications</code></p> <p><code>/var/commerce/shipping-methods</code></p> <p><code>/var/commerce/payment-methods</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Sie können die Aufgabe <a href="/help/sites-deploying/lazy-content-migration.md" target="_blank">Lazy Migration</a> verwenden, um E-Commerce-Daten zu migrieren.</p> <p>Sie führt die folgenden Schritte aus:</p>
    <ul>
     <li>Anpassen von Verweisen auf den alten Speicherort, sodass sie auf den neuen Speicherort verweisen</li>
     <li>Verschieben von Inhalten vom alten Speicherort zum neuen Speicherort</li>
     <li>Entfernen des alten Speicherorts, um die Verwendung des neuen Speicherorts im gesamten System zu aktivieren</li>
    </ul> <p>Die von der Aufgabe betroffenen Speicherorte sind:</p>
    <ul>
     <li>/etc/commerce/products</li>
     <li>/etc/commerce/collections<br /> </li>
     <li>/etc/commerce/orders<br /> </li>
     <li>/etc/commerce/payment-methods<br /> </li>
     <li>/etc/commerce/shipping-methods<br /> </li>
    </ul> <p>Für größere Kataloge empfiehlt Adobe, dass Sie die Aufgabe für die Commerce-Migration einzeln ausführen, indem die folgende Java™-Systemeigenschaft an AEM übergeben wird:</p> <p><code>propertyname: com.adobe.upgrade.forcemigration</code></p> <p><code>property value: com.day.cq.compat.codeupgrade.impl.cq64.CQ64CommerceMigrationTask</code></p> <p>Starten Sie AEM nach der Migration neu.</p> </td>
  </tr>
  <tr>
   <td><strong>Anmerkungen</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>
