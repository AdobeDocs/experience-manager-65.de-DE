---
title: Konfigurieren eines Firmen-Alias-Kontos für Dynamic Media
description: Erfahren Sie, wie Sie ein Firmen-Alias-Konto in Dynamic Media konfigurieren.
contentOwner: Rick Brough
topic-tags: administering
content-type: reference
feature: Image Profiles
role: User,Admin
mini-toc-levels: 4
exl-id: 2ca7b8b2-573c-40e9-b8c3-f38736e819ef
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 100%

---

<!-- hide: yes
hidefromtoc: yes -->

# Informationen zum Konfigurieren eines Firmen-Alias-Kontos in Dynamic Media {#about-dm-alias-acct}

Dynamic Media-URLs und der Viewer-Einbettungs-Code enthalten den Namen Ihres Firmenkontos. Dieser Kontoname wurde zum Zeitpunkt der Bereitstellung von Dynamic Media erstellt. Es kann Situationen geben, in denen Ihr Unternehmen eine Akquise oder ein Rebranding durchlaufen hat oder einfach einen einprägsameren Namen verwenden möchte. In solchen Fällen ist es nicht einfach, den Namen Ihres Firmenkontos in allen vordefinierten URLs und im Viewer-Einbettungs-Code manuell zu aktualisieren. Darüber hinaus besteht die Möglichkeit, dass sich dies auf Ihr vorhandenes Dynamic Media-Repository auswirken oder Live-Inhalte beeinflussen kann. Um dieses Problem zu beheben, können Sie ein Firmen-Alias-Konto in Dynamic Media konfigurieren.

Ein Firmen-Alias-Konto in Dynamic Media stellt sicher, dass alle nativen Dynamic Media-URLs und der Viewer-Einbettungs-Code in der Benutzeroberfläche alle Aktualisierungen an Ihrem Geschäftskontext widerspiegeln, z. B. ein Rebranding. Ein Alias-Konto wirkt sich auch positiv auf Ihre SEO (Suchmaschinenoptimierung) aus, da die Dynamic Media-URLs und der Viewer-Einbettungs-Code den neuen Namen des Firmenkontos widerspiegeln.

Beachten Sie beim Konfigurieren eines Firmen-Alias-Kontos in Dynamic Media Folgendes:

* Vorhandene Dynamic Media-URLs oder Viewer-Einbettungs-Code in Ihren digitalen *live*-Eigenschaften müssen manuell aktualisiert werden, um den neuen Alias-Namen wiederzugeben. Alle URLs oder Einbettungs-Codes für Viewer mit Ihrem ursprünglichen Dynamic Media-Firmennamen funktionieren jedoch auch weiterhin für vorhandene oder neue Assets.
* Die Funktion des Firmen-Alias-Kontos in Dynamic Media ist auf den Authoring-Modus und den Versand in Experience Manager Assets beschränkt. Der Aliasname einer Firma funktioniert nicht mit Experience Manager Sites. WCM-Komponenten (Web Content Management) werden für diese Änderung nicht aktualisiert. Diese Komponenten funktionieren weiterhin mit dem ursprünglichen Dynamic Media-Firmennamen zum Abrufen von Dynamic Media-Assets.
* Sie können auf der Seite **[!UICONTROL Dynamic Media-Konfiguration bearbeiten]** nur ein Firmen-Alias-Konto einrichten. Sie können jedoch über einen Support-Fall beliebig viele Firmen-Alias-Konten erstellen und den erforderlichen Aliasnamen manuell in den URLs von Dynamic Media oder im Viewer-Einbettungs-Code berücksichtigen.
* Die vordefinierte Funktion der [Cache-Invalidierung](/help/assets/invalidate-cdn-cache-dynamic-media.md) von Dynamic Media macht die URLs mit Firmen- und Firmen-Alias-Konten ungültig, die auf der Seite „Dynamic Media-Konfiguration“ in Cloud Services konfiguriert sind.
* Wenn Sie ein Firmen-Alias-Konto auf der Seite **[!UICONTROL Dynamic Media-Konfiguration bearbeiten]** konfigurieren, müssen Sie die URLs für *sowohl* das **[!UICONTROL Firmenkonto]** als auch das **[!UICONTROL Firmen-Alias-Konto]** gleichzeitig ungültig machen, damit die Cache-Invalidierung erfolgreich ist.

Weitere Informationen finden Sie unter [Erstellen einer Dynamic Media-Konfiguration in Cloud Services](/help/assets/config-dms7.md#configuring-dynamic-media-cloud-services)

## Konfigurieren eines Firmen-Alias-Kontos für Dynamic Media {#configure-dm-alias-account}

Sie beginnen mit der Konfiguration eines Firmen-Alias-Kontos in Dynamic Media, indem Sie zunächst einen Support-Fall einreichen. Dieser Schritt ist erforderlich.

1. [Verwenden Sie die Admin Console, um einen Support-Fall zu erstellen](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html).
1. Geben Sie in Ihrem Support-Fall die folgenden Informationen an:

   * Der Firmen-Aliasname in Dynamic Media, den Sie verwenden möchten. Der Name darf *nur* Buchstaben (gemischte Groß- und Kleinschreibung erlaubt), Zahlen, Bindestriche und Unterstriche enthalten.
   * Ihre Region.
   * Ob bereits [Regelsätze](/help/assets/using-rulesets-to-transform-urls.md) verwendet werden, um die Bereitstellung von Dynamic Media-Inhalten über einen alternativen Dynamic Media-Firmenkontonamen zu erreichen.

1. Nachdem das Alias-Konto für Dynamic Media vom Support erstellt wurde, klicken Sie in der Autoreninstanz von Experience Manager as a Cloud Service auf das Logo von Experience Manager as a Cloud Service, um auf die globale Navigationskonsole zuzugreifen.
1. Wählen Sie auf der linken Seite der Konsole das Symbol „Tools“ und anschließend **[!UICONTROL Cloud Services > Dynamic Media-Konfiguration]** aus.
1. Wählen Sie auf der Seite zur Dynamic Media-Konfiguration im linken Bereich **[!UICONTROL global]** aus (wählen Sie nicht das Ordnersymbol links neben **[!UICONTROL global]** aus). Wählen Sie dann **[!UICONTROL Bearbeiten]** aus.

   ![Textfeld „Firmen-Alias in Dynamic Media“](/help/assets/assets-dm/dm-company-alias.png)

1. Geben Sie auf der Seite **[!UICONTROL Dynamic Media-Konfiguration bearbeiten]** im Textfeld **[!UICONTROL Firmen-Alias]** den Namen des Alias-Kontos für Dynamic Media ein, den Sie zuvor in Ihrem Support-Fall angegeben haben.
1. Klicken Sie oben rechts auf der Seite auf **[!UICONTROL Speichern]**.
Das Firmen-Alias-Konto in Dynamic Media ist jetzt gespeichert und aktiviert. Alle URLs und der Viewer-Einbettungs-Code für vorhandene und neue Assets spiegeln jetzt den neuen Aliasnamen des Unternehmens wider.
