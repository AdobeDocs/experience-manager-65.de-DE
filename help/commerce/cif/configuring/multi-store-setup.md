---
title: Multi-Store-Einrichtung in Commerce
description: Erfahren Sie, wie Sie mehrere Store-Ansichten von Adobe Commerce AEM zuordnen. Dadurch können Projekte auch mehrinstanzenfähige und mehrsprachige Anwendungsfälle unterstützen.
sub-product: Commerce
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
kt: 3046
thumbnail: 28952.jpg
exl-id: 1d4e9b7b-848b-4007-b884-dd48682d62e8
source-git-commit: a467009851937c4a10b165a3d253c47bf990bbc5
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 55%

---

# Commerce Multi-Store-Setup {#multi-store}

Die AEM CIF-Kernkomponenten können auf mehreren AEM Site-Strukturen verwendet werden und die zugrunde liegende GraphQL-Client-Implementierung kann eine Verbindung zu verschiedenen Adobe Commerce Stores/Store-Ansichten herstellen. Dadurch können Projekte komplexe Multi-Store-/Multi-Site-Setups implementieren.

Eine Videoeinführung mit detaillierten Optionen zur Integration mehrerer Adobe Commerce Store-Ansichten mit Adobe Experience Manager Sites.

>[!VIDEO](https://video.tv.adobe.com/v/28952/?quality=12)

AEM-Funktionen zur Verwaltung mehrerer Websites von Live Copy und Sprachkopie werden zusammen mit dem Commerce Integration Framework verwendet, um global Sites über Regionen und Gebietsschemata hinweg zu verwalten.

Es wird empfohlen, eine 1:1-Beziehung zwischen AEM Site und der Adobe Commerce Store-Ansicht zu verwenden.

Gehen Sie wie folgt vor, um eine AEM Site zu verbinden und CIF-Kernkomponenten so zu einer dedizierten Store-Ansicht AEM:

## Konfiguration {#configuration}

1. Konfigurieren Sie mehrere Stores und Store-Ansichten nach dem Muster, das unter [Websites, Stores und Ansichten in Adobe Commerce](https://docs.magento.com/m2/ce/user_guide/stores/websites-stores-views.html)

2. Stellen Sie sicher, dass die Verbindung zwischen AEM und Adobe Commerce funktioniert.

3. Erstellen Sie eine untergeordnete Konfiguration der CIF-Cloud Service-Konfiguration wie folgt:

   * Wechseln Sie in AEM zu „Tools“ > „Allgemein“ > [Konfigurations-Browser](/help/sites-administering/configurations.md#using-configuration-browser).
   * Wählen Sie die von Ihnen erstellte Basiskonfiguration aus.
   * Erstellen Sie eine neue Konfiguration mithilfe der unter Punkt 2 beschriebenen Schritte.

   Diese neue Konfiguration wird als untergeordnete Konfiguration der Basiskonfiguration erstellt. Sie können nun die Konfigurationseinstellungen unter „Tools“ -> „Allgemein“ -> „Konfigurationsbrowser“ erstellen.

   >[!TIP]
   >
   > Commerce-Kataloge können mit IDs oder UIDs adressiert werden. UIDs wurden in Adobe Commerce 2.4.2 eingeführt. Aktivieren Sie dies nur, wenn Ihr Commerce-Backend ein GraphQL-Schema der Version 2.4.2 oder höher unterstützt.

4. Weisen Sie die untergeordnete Konfiguration zu einer AEM-Site zu.

   * Wechseln Sie zur AEM Sites-Konsole.
   * Navigieren Sie zum Regions- oder zum Sprachstamm Ihrer Site-Struktur, z. B. /content/venia/us _oder_ /content/venia/us/en für die Venia-Beispielseite
   * Wählen Sie die Seiten aus und öffnen Sie die Seiteneigenschaften.
   * Wählen Sie die Registerkarte „Erweitert“ aus.
   * Wählen Sie im Abschnitt `Configuration` die zuvor erstellte Konfiguration aus.

## Zusätzliche Ressourcen

* [Websites, Stores und Ansichten in Adobe Commerce](https://docs.magento.com/m2/ce/user_guide/stores/websites-stores-views.html)
* [AEM-CIF-Kernkomponenten – Multi-Store-/Multi-Site-Konfiguration](https://github.com/adobe/aem-core-cif-components/wiki/configuration#multi-store--site-configuration)
* [Verwenden von Multi Site Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/translation/multi-site-manager-feature-video-use.html?lang=de)
* [Wiederverwenden von Inhalten: Multi Site Manager und Live Copy](/help/sites-administering/msm.md)
