---
title: Commerce-Multi-Store-Einrichtung
description: Informationen dazu, wie Sie mehrere Store-Ansichten von Magento AEM zuordnen. Dadurch können Projekte auch mehrinstanzenfähige und mehrsprachige Anwendungsfälle unterstützen.
sub-product: Commerce
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
kt: 3046
thumbnail: 28952.jpg
translation-type: tm+mt
source-git-commit: d92a635d41cf1b14e109c316bd7264cf7d45a9fe
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 90%

---

# Commerce-Multi-Store-Einrichtung {#multi-store}

Die AEM-CIF-Kernkomponenten können auf mehreren AEM Site-Strukturen verwendet werden und die zugrunde liegende GraphQL-Client-Implementierung kann mit verschiedenen Magento-Stores/Store-Ansichten verbunden werden. Dadurch können Projekte komplexe Multi-Store-/Multi-Site-Setups implementieren.

Videoeinführung mit detaillierten Optionen zur Integration mehrerer Magento-Store-Ansichten mit Adobe Experience Manager Sites:

>[!VIDEO](https://video.tv.adobe.com/v/28952/?quality=12)

AEM-Funktionen zur Verwaltung mehrerer Websites von Live Copy und Sprachkopie werden zusammen mit dem Commerce Integration Framework verwendet, um global Sites über Regionen und Gebietsschemata hinweg zu verwalten.

Es empfiehlt sich, eine 1:1-Beziehung zwischen AEM-Site und Magento Store-Ansicht zu verwenden.

Gehen Sie wie folgt vor, um eine AEM-Site und die AEM-CIF-Kernkomponenten zu einer dedizierten Store-Ansicht zu verbinden:

## Konfiguration {#configuration}

1. Konfigurieren Sie mehrere Stores und Store-Ansichten nach dem Muster, das unter [Websites, Stores und Ansichten](https://docs.magento.com/m2/ce/user_guide/stores/websites-stores-views.html) beschrieben ist.

2. Stellen Sie sicher, dass die Verbindung zwischen AEM und Magento hergestellt ist.

3. Erstellen Sie eine untergeordnete Konfiguration der CIF-Cloud Service-Konfiguration wie folgt:

   * Wechseln Sie in AEM zu „Tools“ > „Allgemein“ > [Konfigurations-Browser](/help/sites-administering/configurations.md#using-configuration-browser).
   * Wählen Sie die von Ihnen erstellte Basiskonfiguration aus.
   * Erstellen Sie eine neue Konfiguration mithilfe der unter Punkt 2 beschriebenen Schritte.

   Diese neue Konfiguration wird als untergeordnete Konfiguration der Basiskonfiguration erstellt. Sie können nun die Konfigurationseinstellungen unter „Tools“ -> „Allgemein“ -> „Konfigurationsbrowser“ erstellen.

   >[!TIP]
   >
   > Commerce-Kataloge können mit IDs oder UIDs adressiert werden. UIDs wurden in Magento 2.4.2 eingeführt. Aktivieren Sie dies nur, wenn Ihr Commerce-Backend ein GraphQL-Schema der Version 2.4.2 oder höher unterstützt.

4. Weisen Sie die untergeordnete Konfiguration zu einer AEM-Site zu.

   * Wechseln Sie zur AEM Sites-Konsole.
   * Navigieren Sie zum Regions- oder zum Sprach-Stamm Ihrer Site-Struktur, z. B. „/content/venia/us“ _oder_ „/content/venia/us/en“ für die Venia-Beispielseite.
   * Wählen Sie die Seiten aus und öffnen Sie die Seiteneigenschaften.
   * Wählen Sie die Registerkarte „Erweitert“ aus.
   * Wählen Sie im Abschnitt `Configuration` die zuvor erstellte Konfiguration aus.

## Zusätzliche Ressourcen

* [Websites, Stores und Ansichten](https://docs.magento.com/m2/ce/user_guide/stores/websites-stores-views.html)
* [AEM-CIF-Kernkomponenten – Multi-Store-/Multi-Site-Konfiguration](https://github.com/adobe/aem-core-cif-components/wiki/configuration#multi-store--site-configuration)
* [Verwenden von Multi-Site-Manager](https://docs.adobe.com/content/help/de-DE/experience-manager-learn/sites/translation/multi-site-manager-feature-video-use.html)
* [Wiederverwenden von Inhalten: Multi-Site-Manager und Live Copy](/help/sites-administering/msm.md)
