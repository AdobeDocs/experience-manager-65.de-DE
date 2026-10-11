---
title: Neustarten des AEM SDK
description: Best Practices für den Neustart des AEM SDK
role: Admin, Developer, User
feature: Adaptive Forms,AEM Forms on JEE,AEM Forms on OSGi
exl-id: f5d69d04-b842-4329-b1b3-57b88266d13d
solution: Experience Manager, Experience Manager Forms
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 94663796-0ee7-58b9-84f4-b425ebb69e83
    internal-label: AEM Forms on JEE
  - id: 8c4fb903-572c-5473-ad45-8ebb0d5d8134
    internal-label: AEM Forms on OSGi
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 100%
---
# Neustarten des AEM SDK

Wenn Sie das AEM SDK neu starten, indem Sie die Java™-Prozesse stoppen, kann dies zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen. Es tritt ein Fehler wie der folgende auf:

`javax.jcr.RepositoryException: Applying repoinit operation failed despite retry; set loglevel to DEBUG to see all exceptions. Last exception message was: Failed to set ACL (javax.jcr.ValueFormatException: Invalid type: 0) AclLine ALLOW {principals=[forms-xfa-writers], privileges=[jcr:modifyProperties]} restrictions=[rep:glob=[*/jcr:content/*], rep:itemNames=[xfaForm], fd:condition=[xfaForm, 1]]`

![Fehler beim AEM SDK-Neustart](/help/forms/using/assets/restart-sdk-error.png)

## Lösung

Wechseln Sie zum aktiven Befehlsfenster und drücken Sie die Tastenkombination `Ctrl + C`, um das AEM SDK neu zu starten.

Es wird empfohlen, den Befehl „Strg+C“ zu verwenden, um das SDK neu zu starten. Das Neustarten des AEM SDK mithilfe alternativer Methoden, z. B. durch Beenden von Java™-Prozessen, kann zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen.
