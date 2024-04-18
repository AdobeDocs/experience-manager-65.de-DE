---
title: Anpassen der Willkommens-Konsole (klassische Benutzeroberfläche)
description: Die Willkommens-Konsole bietet eine Liste mit Links zu den unterschiedlichen Konsolen und Funktionen innerhalb von AEM.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: 9e171b62-8efb-4143-a202-ba6555658d4b
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 100%

---

# Anpassen der Willkommens-Konsole (klassische Benutzeroberfläche){#customizing-the-welcome-console-classic-ui}

>[!CAUTION]
>
>Diese Seite behandelt die klassische Benutzeroberfläche.
>
>Unter [Anpassung der Konsolen](/help/sites-developing/customizing-consoles-touch.md) finden Sie genauere Informationen zur standardmäßigen Touch-optimierten Benutzeroberfläche.

Die Willkommens-Konsole bietet eine Liste mit Links zu den unterschiedlichen Konsolen und Funktionen innerhalb von AEM.

![cq_welcomescreen](assets/cq_welcomescreen.png)

Sie können die sichtbaren Links konfigurieren. Sie können dies für bestimmte Benutzende und/oder Gruppen definieren. Die erforderlichen Handlungen hängen vom Zieltyp ab. Dieser hängt vom Abschnitt der Konsole ab, in dem sich die Ziele befinden:

* [Hauptkonsolen](#links-in-main-console-left-pane): links in der Hauptkonsole (linker Bereich)
* [Ressourcen, Dokumentation und Verweis, Funktionen](#links-in-sidebar-right-pane): links in der Seitenleiste (rechter Bereich)

## Links in der Hauptkonsole (linker Bereich) {#links-in-main-console-left-pane}

Dies sind die Hauptkonsolen von AEM.

![cq_welcomescreenmainconsole](assets/cq_welcomescreenmainconsole.png)

### Legt fest, ob Hauptkonsolen-Links sichtbar sind {#configuring-whether-main-console-links-are-visible}

Berechtigungen auf Knotenebene legen fest, ob der Link sichtbar ist. Die betreffenden Knoten sind Folgende:

* **Websites:** `/libs/wcm/core/content/siteadmin`

* **Digitale Assets:** `/libs/wcm/core/content/damadmin`

* **Community:** `/libs/collab/core/content/admin`

* **Kampagnen:** `/libs/mcm/content/admin`

* **Posteingang:** `/libs/cq/workflow/content/inbox`

* **Benutzer:** `/libs/cq/security/content/admin`

* **Tools:** `/libs/wcm/core/content/misc`

* **Tagging:** `/libs/cq/tagging/content/tagadmin`

Beispiel:

* Um den Zugriff auf **Tools** einzuschränken, entfernen Sie den Lesezugriff von

  `/libs/wcm/core/content/misc`

Im [Abschnitt „Sicherheit“](/help/sites-administering/security.md) finden Sie weitere Informationen zum Festlegen der gewünschten Berechtigungen.

### Links in der Seitenleiste (rechter Bereich) {#links-in-sidebar-right-pane}

![cq_welcomescreensidebar](assets/cq_welcomescreensidebar.png)

Diese Links basieren auf dem Vorhandensein *und* dem Lesezugriff auf Knoten unter dem folgenden Pfad:

`/libs/cq/core/content/welcome`

Drei Abschnitte werden standardmäßig bereitgestellt (leicht getrennt):

<table>
 <tbody>
  <tr>
   <td><strong>Ressourcen</strong></td>
   <td> </td>
  </tr>
  <tr>
   <td> Cloud Services</td>
   <td><code>/libs/cq/core/content/welcome/resources/cloudservices</code></td>
  </tr>
  <tr>
   <td> Workflows</td>
   <td><code>/libs/cq/core/content/welcome/resources/workflows</code></td>
  </tr>
  <tr>
   <td> Aufgabenverwaltung</td>
   <td><code>/libs/cq/core/content/welcome/resources/taskmanager</code></td>
  </tr>
  <tr>
   <td> Replikation</td>
   <td><code>/libs/cq/core/content/welcome/resources/replication</code></td>
  </tr>
  <tr>
   <td> Berichte</td>
   <td><code>/libs/cq/core/content/welcome/resources/reports</code></td>
  </tr>
  <tr>
   <td> Veröffentlichungen</td>
   <td><code>/libs/cq/core/content/welcome/resources/publishingadmin</code></td>
  </tr>
  <tr>
   <td> Manuskripte</td>
   <td><code>/libs/cq/core/content/welcome/resources/manuscriptsadmin</code></td>
  </tr>
  <tr>
   <td><strong>Dokumentation und Referenz</strong></td>
   <td> </td>
  </tr>
  <tr>
   <td> Dokumentation</td>
   <td><code>/libs/cq/core/content/welcome/docs/docs</code></td>
  </tr>
  <tr>
   <td> Entwicklungsressourcen</td>
   <td><code>/libs/cq/core/content/welcome/docs/dev</code></td>
  </tr>
  <tr>
   <td><strong>Funktionen</strong></td>
   <td> </td>
  </tr>
  <tr>
   <td> CRXDE Lite</td>
   <td><code>/libs/cq/core/content/welcome/features/crxde</code></td>
  </tr>
  <tr>
   <td> Pakete</td>
   <td><code>/libs/cq/core/content/welcome/features/packages</code></td>
  </tr>
  <tr>
   <td> Package Share</td>
   <td><code>/libs/cq/core/content/welcome/features/share</code></td>
  </tr>
  <tr>
   <td> Cluster</td>
   <td><code>/libs/cq/core/content/welcome/features/cluster</code></td>
  </tr>
  <tr>
   <td> Sicherung</td>
   <td><code>/libs/cq/core/content/welcome/features/backup</code></td>
  </tr>
  <tr>
   <td> Web-Konsole<br /> </td>
   <td><code>/libs/cq/core/content/welcome/features/config</code></td>
  </tr>
  <tr>
   <td> Sicherungskopie für Web-Konsolenstatus<br /> </td>
   <td><code>/libs/cq/core/content/welcome/features/statusdump</code></td>
  </tr>
 </tbody>
</table>

#### Konfiguration der Sichtbarkeit von Seitenleisten-Links {#configuring-whether-sidebar-links-are-visible}

Sie können einen Link für bestimmte Benutzende oder Gruppen ausblenden, indem Sie den Lesezugriff auf die Knoten entfernen, die diesen Link repräsentieren.

* Ressourcen – Entfernen des Zugriffs auf:

  `/libs/cq/core/content/welcome/resources/<link-target>`

* Dokumente – Entfernen des Zugriffs auf:

  `/libs/cq/core/content/welcome/docs/<link-target>`

* Funktionen – Entfernen des Zugriffs auf:

  `/libs/cq/core/content/welcome/features/<link-target>`

Beispiel:

* Um den Link auf **Berichte** zu entfernen, entfernen Sie den Lesezugriff von

  `/libs/cq/core/content/welcome/resources/reports`

* Um den Link auf **Pakete** zu entfernen, entfernen Sie den Lesezugriff von

  `/libs/cq/core/content/welcome/features/packages`

Im [Abschnitt „Sicherheit“](/help/sites-administering/security.md) finden Sie weitere Informationen zum Festlegen der gewünschten Berechtigungen.

### Link-Auswahlmechanismus {#link-selection-mechanism}

In `/libs/cq/core/components/welcome/welcome.jsp` wird [ConsoleUtil](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/ConsoleUtil.html) genutzt, das eine Abfrage auf Knoten mit folgender Eigenschaft durchführt:

* `jcr:mixinTypes` mit dem Wert: `cq:Console`

>[!NOTE]
>
>Führen Sie die folgende Abfrage aus, um die bestehende Liste zu finden:
>
>* `select * from cq:Console`
>

Wenn ein Benutzer oder eine Gruppe keine Leseberechtigungen für einen Knoten mit dem Mixin `cq:Console` hat, wird dieser Knoten nicht mit der `ConsoleUtil`-Suche abgerufen und wird daher nicht in der Konsole aufgeführt.

### Hinzufügen eines benutzerdefinierten Elements {#adding-a-custom-item}

Mit dem [Link-Auswahlmechanismus](#link-selection-mechanism) können Sie Ihr selbst definiertes Element zur Liste der Links hinzufügen.

Fügen Sie Ihr benutzerdefiniertes Element zur Liste hinzu, indem Sie das Mixin `cq:Console` zu Ihrem Widget oder Ihrer Ressource hinzufügen. Definieren Sie dazu die Eigenschaft:

* `jcr:mixinTypes` mit dem Wert: `cq:Console`
