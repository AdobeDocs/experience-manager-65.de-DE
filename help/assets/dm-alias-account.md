---
title: Dynamic Media-Unternehmensalias-Konto konfigurieren
description: Erfahren Sie, wie Sie ein Unternehmensalias-Konto in Dynamic Media konfigurieren.
contentOwner: Rick Brough
topic-tags: administering
content-type: reference
feature: Image Profiles
role: User,Admin
mini-toc-levels: 4
exl-id: 2ca7b8b2-573c-40e9-b8c3-f38736e819ef
source-git-commit: 787c0c25da2258f234d3c821038d62bf8ef68932
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 9%

---

<!-- hide: yes
hidefromtoc: yes -->

# Informationen zum Konfigurieren eines Dynamic Media-Unternehmensalias-Kontos {#about-dm-alias-acct}

Dynamic Media-URLs und der Viewer-Einbettungscode enthalten Ihren Unternehmenskontonamen. Dieser Kontoname wurde zum Zeitpunkt der Bereitstellung von Dynamic Media erstellt. Es kann Situationen geben, in denen Ihr Unternehmen eine Akquise oder ein Rebranding durchlaufen hat oder einfach einen unvergesslicheren Namen verwenden möchte. In solchen Fällen ist es nicht einfach, den Namen Ihres Unternehmenskontos in allen vordefinierten URLs und im Viewer-Einbettungscode manuell zu aktualisieren. Darüber hinaus besteht die Möglichkeit, dass Sie sich auf Ihr vorhandenes Dynamic Media-Repository auswirken oder Live-Inhalte beeinflussen können. Um dieses Problem zu beheben, können Sie ein Dynamic Media-Unternehmensalias-Konto konfigurieren.

Ein Dynamic Media-Unternehmensalias-Konto stellt sicher, dass alle nativen Dynamic Media-URLs und der Viewer-Einbettungscode in der Benutzeroberfläche alle Aktualisierungen an Ihrem Geschäftskontext widerspiegeln, z. B. das Rebranding. Ein Alias-Konto wirkt sich auch positiv auf Ihre SEO (Suchmaschinenoptimierung) aus, da die Dynamic Media-URLs und der eingebettete Viewer-Code den neuen Unternehmenskontonamen widerspiegeln.

Beachten Sie beim Konfigurieren eines Dynamic Media-Unternehmensalias-Kontos Folgendes:

* Beliebiger Dynamic Media-URLs oder Viewer-Einbettungscode in Ihrem *live* digitale Eigenschaften müssen manuell aktualisiert werden, um den neuen Aliasnamen widerzuspiegeln. Jeder URLs- oder Viewer-Einbettungscode mit Ihrem ursprünglichen Dynamic Media-Unternehmensnamen funktioniert jedoch weiterhin für vorhandene oder neue Assets.
* Die Funktion des Dynamic Media-Unternehmensalias-Kontos ist auf den Experience Manager Assets-Authoring-Modus und den Versand beschränkt. Der Aliasname des Unternehmens funktioniert nicht mit Experience Manager Sites. WCM-Komponenten (Web Content Management) werden für diese Änderung nicht aktualisiert. Diese Komponenten funktionieren weiterhin mit dem ursprünglichen Dynamic Media-Unternehmensnamen zum Abrufen von Dynamic Media-Assets.
* Sie können nur ein Unternehmensalias-Konto auf der **[!UICONTROL Dynamic Media-Konfiguration bearbeiten]** Seite. Sie können jedoch im Support-Fall so viele Unternehmensalias-Konten erstellen und manuell den erforderlichen Aliasnamen in den Dynamic Media-URLs oder im Viewer-Einbettungscode widerspiegeln.
* Die vordefinierten [Cache-Invalidierung](/help/assets/invalidate-cdn-cache-dynamic-media.md) -Funktion von Dynamic Media macht die URLs für ungültig, sowohl für Firmen- als auch für Firmenalias-Konten, die auf der Dynamic Media-Konfigurationsseite in Cloud Services konfiguriert sind.
* Wenn Sie ein Unternehmensalias-Konto für die **[!UICONTROL Dynamic Media-Konfiguration bearbeiten]** -Seite verwenden, müssen Sie URLs ungültig machen, damit die Cache-Invalidierung erfolgreich ist für *both* die **[!UICONTROL Firma]** und **[!UICONTROL Firmenalias]** -Konto gleichzeitig.

Siehe auch [Erstellen einer Dynamic Media-Konfiguration in Cloud Services](/help/assets/config-dms7.md#configuring-dynamic-media-cloud-services)

## Dynamic Media-Unternehmensalias-Konto konfigurieren {#configure-dm-alias-account}

Sie beginnen mit der Konfiguration eines Dynamic Media-Firmenalias-Kontos, indem Sie zunächst einen Support-Fall einreichen. Dieser Schritt ist erforderlich.

1. [Verwenden Sie die Admin Console, um einen Support-Fall zu erstellen](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html).
1. Geben Sie in Ihrem Support-Fall die folgenden Informationen an:

   * Der Aliasname des Dynamic Media-Unternehmens, den Sie verwenden möchten. Der Name muss *only* Buchstaben (Groß- und Kleinschreibung zulässig), Zahlen, Bindestriche und Unterstriche.
   * Ihre Region.
   * Ob [rulesets](/help/assets/using-rulesets-to-transform-urls.md) werden zuvor verwendet, um die Bereitstellung von Dynamic Media-Inhalten über einen alternativen Dynamic Media-Unternehmenskontonamen zu erreichen.

1. Nachdem das Dynamic Media-Alias-Konto vom Support erstellt wurde, wählen Sie in der Experience Manager as a Cloud Service Author-Instanz das as a Cloud Service Experience Manager-Logo aus, um auf die globale Navigationskonsole zuzugreifen.
1. Wählen Sie auf der linken Seite der Konsole das Symbol „Tools“ und anschließend **[!UICONTROL Cloud Services > Dynamic Media-Konfiguration]** aus.
1. Wählen Sie auf der Seite zur Dynamic Media-Konfiguration im linken Bereich **[!UICONTROL global]** aus (wählen Sie nicht das Ordnersymbol links neben **[!UICONTROL global]** aus). Wählen Sie dann **[!UICONTROL Bearbeiten]** aus.

   ![Textfeld &quot;Dynamic Media-Unternehmensalias&quot;](/help/assets/assets-dm/dm-company-alias.png)

1. Im **[!UICONTROL Dynamic Media-Konfiguration bearbeiten]** in der **[!UICONTROL Firmenalias]** Textfeld den Namen des Dynamic Media-Alias-Kontos eingeben, den Sie zuvor in Ihrem Support-Fall angegeben haben.
1. Wählen Sie rechts oben auf der Seite die Option **[!UICONTROL Speichern]**.
Das Dynamic Media-Unternehmensalias-Konto wird jetzt gespeichert und aktiviert. Alle URLs und der Viewer-Einbettungscode für vorhandene und neue Assets spiegeln jetzt den neuen Aliasnamen des Unternehmens wider.
