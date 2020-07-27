---
title: Erstellen benutzerdefinierter Layoutkomponenten für adaptive Formulare
seo-title: Erstellen benutzerdefinierter Layoutkomponenten für adaptive Formulare
description: Verfahren zum Erstellen benutzerdefinierter Layoutkomponenten für adaptive Formulare.
seo-description: Verfahren zum Erstellen benutzerdefinierter Layoutkomponenten für adaptive Formulare.
uuid: f0bb5fcd-3938-4804-ad0c-d96d3083fd01
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
discoiquuid: d4ae432d-557d-4e89-92b8-dca5f37cb6f8
docset: aem65
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 63%

---


# Erstellen benutzerdefinierter Layoutkomponenten für adaptive Formulare{#creating-custom-layout-components-for-adaptive-forms}

## Voraussetzung {#prerequisite}

Wissen bezüglich Layouts, das für das Erstellen/Verwenden benutzerdefinierter Layouts nötig ist. Siehe [Ändern des Bedienfeldlayouts](../../forms/using/layout-capabilities-adaptive-forms.md).

## Komponente für das Bedienfeldlayout für adaptiven Formulare {#adaptive-form-panel-layout-component}

Mit der Komponente für das Bedienfeldlayout für adaptive Formulare wird gesteuert, wie die Komponenten des adaptiven Formulars in einem Bedienfeld im Verhältnis zur Benutzeroberfläche angelegt werden.

## Erstellen eines benutzerdefinierten Bedienfeldlayouts {#creating-a-custom-panel-layout}

1. Navigate to the location `/crx/de`.
1. Copy a panel layout from the location `/libs/fd/af/layouts/panel` (for example, `tabbedPanelLayout`) to `/apps` (for example, `/apps/af-custom-layout`).
1. Rename the layout you copied to `customPanelLayout`. Change the properties of the nodes `qtip` and `jcr:description`. Ändern Sie sie beispielsweise in `Custom layout - Toggle tabs`.

qtip

![Abbildung des benutzerdefinierten Bedienfeldlayouts CRX DE](assets/custom_layout_new.png)

>[!NOTE]
>
>Setting the property `guideComponentType`to the value `fd/af/layouts/panel` determines that the layout is a panel-layout.

1. Rename the file `tabbedPanelLayout.jsp` under the new layout to customPanelLayout.jsp.
1. Um neue Stile und Verhaltensweisen einzuführen, erstellen Sie eine Client-Bibliothek unter dem Knoten `etc`. Erstellen Sie z. B. im Verzeichnis /etc/af-custom-layout-clientlib den Knoten client-library. Weisen Sie dem Knoten die Kategorieneigenschaft af.panel.custom zu. Sie verfügt über folgende .css- und .js-Dateien:

   ```css
   /** CSS defining new styles used by custom layout **/
   
   .menu-nav {
       background-color: rgb(198, 38, 76);
       height: 30px;
    width: 30px;
    font-size: 2em;
    color: white;
       -webkit-transition: -webkit-transform 1s;  /* For Safari 3.1 to 6.0 */
    transition: transform 1s;
   }
   
   .tab-content {
    border: 1px solid #08b1cf;
   }
   
   .custom-navigation {
       -webkit-transition: width 1s, height 1s, -webkit-transform 1s;  /* For Safari 3.1 to 6.0 */
    transition: width 1s, height 1s, transform 1s;
   }
   
   .panel-name {
       padding-left: 30px;
       font-size: 20px;
   }
   
   @media (min-width: 992px) {
    .nav-close {
     width: 0px;
       }
   }
   
   @media (min-width: 768px) and (max-width: 991px) {
    .nav-close {
     height: 0px;
       }
   }
   
   @media (max-width: 767px) {
    .menu-nav, .custom-navigation {
        display: none;
       }
   }
   ```

   ```javascript
   /** function for toggling the navigators **/
   var toggleNav = function () {
   
       var nav = $('.custom-navigation');
       if (nav) {
           nav.toggleClass('nav-close');
       }
   }
   
   /** function to populate the panel title **/
   $(window).on('load', function() {
       if (window.guideBridge) {
           window.guideBridge.on("elementNavigationChanged",
           function (evntName, evnt) {
                       var activePanelSom = evnt.newText,
                           activePanel = window.guideBridge._guideView.getView(activePanelSom);
                       $('.panel-name').html(activePanel.$itemNav.find('a').html());
                   }
           );
       }
   });
   ```

1. To enhance the appearance and behavior, you can include a `client library`.

   Aktualisieren Sie außerdem die Pfade der in .jsp-Dateien eingeschlossenen Skripts. For example, update the `customPanelLayout.jsp` file as follows:

   ```html
   <%-- jsp encapsulating navigator container and panel container divs --%>
   
   <%@include file="/libs/fd/af/components/guidesglobal.jsp"%>
   <cq:includeClientLib categories="af.panel.custom"/>
   <div>
       <div class="row">
           <div class="col-md-2 col-sm-2 hidden-xs menu-nav glyphicon glyphicon-align-justify" onclick="toggleNav();"></div>
           <div class="col-md-10 col-sm-10 hidden-xs panel-name"></div>
       </div>
       <div class="row">
           <div class="col-md-2 hidden-xs guide-tab-stamp-list custom-navigation">
               <cq:include script = "/apps/af-custom-layout/customPanelLayout/defaultNavigatorLayout.jsp" />
           </div>
           <div  class="col-md-10">
               <c:if test="${fn:length(guidePanel.description) > 0}">
                   <div class="<%=GuideConstants.GUIDE_PANEL_DESCRIPTION%>">
                       ${guide:encodeForHtml(guidePanel.description,xssAPI)}
                           <cq:include script="/libs/fd/af/components/panel/longDescription.jsp"/>
                   </div>
               </c:if>
               <cq:include script = "/apps/af-custom-layout/customPanelLayout/panelContainer.jsp"/>
           </div>
       </div>
   </div>
   ```

   Die `/apps/af-custom-layout/customPanelLayout/defaultNavigatorLayout.jsp` Datei:

   ```html
   <%-- jsp governing the navigation part --%>
   
   <%@include file="/libs/fd/af/components/guidesglobal.jsp"%>
   <%@ page import="com.adobe.aemds.guide.utils.StyleUtils" %>
   <%-- navigation tabs --%>
   <ul id="${guidePanel.id}_guide-item-nav-container" class="tab-navigators tab-navigators-vertical in"
       data-guide-panel-edit="reorderItems" role="tablist">
       <c:forEach items="${guidePanel.items}" var="panelItem">
           <c:set var="isNestedLayout" value="${guide:hasNestablePanelLayout(guidePanel,panelItem)}"/>
           <li id="${panelItem.id}_guide-item-nav" title="${guide:encodeForHtmlAttr(panelItem.navTitle,xssAPI)}" data-path="${panelItem.path}" role="tab" aria-controls="${panelItem.id}_guide-item">
               <c:set var="panelItemCss" value="${panelItem.cssClassName}"/>
               <% String panelItemCss = (String) pageContext.getAttribute("panelItemCss");%>
               <a data-guide-toggle="tab" class="<%= StyleUtils.addPostfixToClasses(panelItemCss, "_nav") %> guideNavIcon nested_${isNestedLayout}">${guide:encodeForHtml(panelItem.navTitle,xssAPI)}</a>
               <c:if test="${isNestedLayout}">
                   <guide:initializeBean name="guidePanel" className="com.adobe.aemds.guide.common.GuidePanel"
                       resourcePath="${panelItem.path}" restoreOnExit="true">
                       <sling:include path="${panelItem.path}"
                                      resourceType="/apps/af-custom-layout/customPanelLayout/defaultNavigatorLayout.jsp"/>
                   </guide:initializeBean>
               </c:if>
               <em></em>
           </li>
       </c:forEach>
   </ul>
   ```

   Die Aktualisierung `/apps/af-custom-layout/customPanelLayout/panelContainer.jsp`:

   ```html
   <%-- jsp governing the panel content --%>
   
   <%@include file="/libs/fd/af/components/guidesglobal.jsp"%>
   
   <div id="${guidePanel.id}_guide-item-container" class="tab-content">
       <c:if test="${guidePanel.hasToolbar && (guidePanel.toolbarPosition == 'Top') }">
           <sling:include path="${guidePanel.toolbar.path}"/>
       </c:if>
   
   <c:forEach items="${guidePanel.items}" var="panelItem">
       <div class="tab-pane" id="${panelItem.id}_guide-item" role="tabpanel">
           <c:set var="isNestedLayout" value="${guide:hasNestablePanelLayout(guidePanel,panelItem)}"/>
           <c:if test="${isNestedLayout}">
               <c:set var="guidePanelResourceType" value="/apps/af-custom-layout/customPanelLayout/panelContainer.jsp" scope="request"/>
           </c:if>
           <sling:include path="${panelItem.path}" resourceType="${panelItem.resourceType}"/>
       </div>
   </c:forEach>
   <c:if test="${guidePanel.hasToolbar && (guidePanel.toolbarPosition == 'Bottom')}">
       <sling:include path="${guidePanel.toolbar.path}"/>
   </c:if>
   </div>
   ```

1. Öffnen Sie ein adaptives Formular im Bearbeitungsmodus. Das Bedienfeldlayout, das Sie definiert haben, wird der Liste zur Konfiguration der Bereichslayouts hinzugefügt.

   ![Das benutzerdefinierte Bedienfeldlayout wird in der Liste](assets/auth-layt.png) des Bedienfeldlayouts des adaptiven Formulars im ![Screenshot angezeigt, in der das benutzerdefinierte Bedienfeldlayout](assets/s1.png) verwendet wird. In diesem Screenshot wird die Funktion des benutzerdefinierten Layouts ![zum Umschalten dargestellt](assets/s2.png)

Beispiel-ZIP-Datei für ein benutzerdefiniertes Bedienfeldlayout und ein adaptives Formular, das dieses verwendet.

[Datei laden](assets/af-custom-layout.zip)
