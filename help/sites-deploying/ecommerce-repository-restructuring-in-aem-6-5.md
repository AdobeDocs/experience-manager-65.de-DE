---
title: E-Commerce-Repository-Neustrukturierung in AEM 6.5
seo-title: E-Commerce-Repository-Neustrukturierung in AEM 6.5
description: Erfahren Sie, wie Sie die notwendigen Änderungen vornehmen können, um in AEM 6.5 für E-Commerce zur neuen Repository-Struktur zu migrieren.
seo-description: Erfahren Sie, wie Sie die notwendigen Änderungen vornehmen können, um in AEM 6.5 für E-Commerce zur neuen Repository-Struktur zu migrieren.
uuid: 1fff1a4b-c8d0-4016-92fb-e2ea26e3a302
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 28c92e7d-2106-4333-afa6-c5528a00d7b4
feature: Aktualisieren
exl-id: 78b7c497-c474-4308-bfab-8f424b5f7268
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 77%

---

# E-Commerce-Repository-Neustrukturierung in AEM 6.5{#e-commerce-repository-restructuring-in-aem}

Wie auf der übergeordneten Seite [Repository-Neustrukturierung in AEM 6.5](/help/sites-deploying/repository-restructuring.md) beschrieben, sollten Kunden, die auf AEM 6.5 aktualisieren, diese Seite verwenden, um den Arbeitsaufwand im Zusammenhang mit Repository-Änderungen zu bewerten, die sich auf die AEM E-Commerce-Lösung auswirken. Einige Änderungen erfordern während des Aktualisierungsprozesses von AEM 6.5 Arbeitsaufwand, während andere bis zu einer zukünftigen Aktualisierung verschoben werden können.

## Mit der Aktualisierung auf 6.5 {#with-upgrade}

### Produkt-, Auftrags-, Sammlungs-, Klassifizierungs-, Versand- und Zahlungsartendaten {#product-order-collections-classifications-shipping-methods-and-payment-methods-data}

<table>
 <tbody>
  <tr>
   <td><strong>Vorheriger Speicherort</strong></td>
   <td><p><code>/etc/commerce/products</code></p> <p><code>/etc/commerce/orders</code></p> <p><code>/etc/commerce/collections</code></p> <p><code>/etc/commerce/classifications</code></p> <p><code>/etc/commerce/shipping-methods</code></p> <p><code>/etc/commerce/payment-methods</code></p> </td>
  </tr>
  <tr>
   <td><strong>Neuer Speicherort</strong></td>
   <td><p><code>/var/commerce/products</code></p> <p><code>/var/commerce/orders</code></p> <p><code>/var/commerce/collections</code></p> <p><code>/var/commerce/classifications</code></p> <p><code>/var/commerce/shipping-methods</code></p> <p><code>/var/commerce/payment-methods</code></p> </td>
  </tr>
  <tr>
   <td><strong>Leitfaden für die Neustrukturierung</strong></td>
   <td><p>Sie können die Aufgabe <a href="/help/sites-deploying/lazy-content-migration.md" target="_blank">Lazy Migration</a> verwenden, um E-Commerce-Daten zu migrieren.</p> <p>Folgende Schritte werden ausgeführt:</p>
    <ul>
     <li>passt Referenzen auf den alten Speicherort so an, dass nur auf den neuen Speicherort verwiesen wird.</li>
     <li>verschiebt Inhalte vom alten Speicherort an den neuen Speicherort</li>
     <li>entfernt den alten Speicherort, um letztlich die Verwendung des neuen Speicherorts im gesamten System zu aktivieren</li>
    </ul> <p>Die von der Aufgabe betroffenen Speicherorte:</p>
    <ul>
     <li>/etc/commerce/products</li>
     <li>/etc/commerce/collections<br /> </li>
     <li>/etc/commerce/orders<br /> </li>
     <li>/etc/commerce/payment-methods<br /> </li>
     <li>/etc/commerce/shipping-methods<br /> </li>
    </ul> <p>Für größere Kataloge wird empfohlen, die Commerce-Migration einzeln auszuführen, indem die folgende Java-Systemeigenschaft an AEM übergeben wird:</p> <p><code>propertyname: com.adobe.upgrade.forcemigration</code></p> <p><code>property value: com.day.cq.compat.codeupgrade.impl.cq64.CQ64CommerceMigrationTask</code></p> <p>Nach der Migration muss AEM neu gestartet werden.</p> </td>
  </tr>
  <tr>
   <td><strong>Hinweise</strong></td>
   <td>Nicht zutreffend<br /> </td>
  </tr>
 </tbody>
</table>
