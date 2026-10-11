---
title: Umgestaltung von Social Media-Dienstprogrammen
description: Das Paket com.adobe.cq.social.ugcbase.SocialUtils wird in AEM 6.1 nicht mehr unterstützt
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 0f731ec6-a12e-4098-a1ec-ee4cd4dc1432
solution: Experience Manager
feature: Communities
role: Admin
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: b013f126-a97e-52d1-9f79-cb5bbb12114e
    internal-label: Communities
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 1%
---
# Umgestaltung von Social Media-Dienstprogrammen {#socialutils-refactoring}

## Soziales Utils-Paket veraltet {#socialutils-package-deprecated}

Das Paket `com.adobe.cq.social.ugcbase.SocialUtils` ist seit AEM 6.1 veraltet.

In den folgenden Tabellen sind die Methoden aufgeführt, die anstelle von `SocialUtils` Methoden verwendet werden sollen.

## SocialResourceUtilities-Paket  {#socialresourceutilities-package}

| Methoden in com.adobe.cq.social.srp.utilities.api.SocialResourceUtilities | Anmerkungen |
|---|---|
| Boolean checkPermission(ResourceResolver, String path, String action) |  |
| SocialResourceProvider getSocialResourceProvider(resource) |  |
| SocialResourceConfiguration(resource) |  |
| Resource getUGCResource(Resource userResource) |  |
| Resource getUGCResource(Resource userResource, ResourceResolverFactory rf) | Neu |
| Resource getUGCResource(ResourceUserResource, ResourceResolverFactory rf, String resourceTypeHint) | Neu |
| Resource getUGCResource(ResourceUserResource, String resourceTypeHint) |  |
| boolean hasModeratePermissions(resource) |  |
| string resourceToACLPath(resource) |  |
| String resourceToUGCStoragePath(resource) | ersetzt String resourceToUGCPath(resource) |
| String UGCToResourcePath(resource) |  |
| String UGCToResourcePath(String ugcPath) | Methodensignatur geändert |
| String UGCToResourcePath(String ugcPath, ResourceResolver) | Neu |

| Methoden in `com.adobe.cq.social.`utilities.resource.api.SocialResourceUtilities | Anmerkungen |
|---|---|
| SocialResourceProvider getSocialResourceProvider(resource) | ersetzt SocialResourceProvider: getConfigedProvider(resource) |

## SCFUtilities-Paket {#scfutilities-package}

| Methoden in `com.adobe.cq.social.`utilities.scf.api.SCFUtilites |
|---|
| String getAvatar(UserProperties) |
| String getAvatar(UserProperties, int size) |
| String getAvatar(UserProperties, String absoluteDefaultAvatar) |
| String getAvatar(UserProperties, userProperties, String absoluteDefaultAvatar, SocialUtils.AVATAR_SIZE) |
| Page getContainingPage(resource) |
| String getSocialProfileURL(String username, ResourceResolver, page) |
| UserProperties getUserProperties(ResourceResolver, String userId) |

## Nur zur internen Verwendung {#for-internal-use-only}

| boolescher Wert canAddNode(session, String path) |
|---|
| String createUniqueNameHint(string message) |
| String createUniqueNameHint(String message, int numRandomChars) |
| string generateRandomString(int length) |
| socialResourceConfiguration() |
| Page getPage(String path, ResourceResolver) |
| String getPagePath(Resource) |
| String getPagePath(String path) |
| String getResourceTypeForIncludedResource(Resource component, String defaultResourceType, String designPropertyName) |
| String getResourceTypeFromDesign(resource, string styleProperty, string defaultValue) |
| boolean isResourceOwner(resource) |
| String mapUGCPath(resource) |
| String mapUGCPath(String ugcPath, ResourceResolver) |
| boolescher Wert („mayPost“, ResourceResolver) |
| String preUserGeneratedContent(ResourceResolver, String path) |

## Methoden nicht mehr verfügbar {#methods-no-longer-available}

| node createNode(ResourceResolver, String path, String nodeType) |
|---|
| Resource getResourceAtPath(ResourceResolver, String path) |
| Resource getResourceAtPath(ResourceResolver, String path, String resourceType) |
| Konfiguration getStorageCloudServiceConfig(Ressource) |
| TranslationManager getTranslationManager() |
| TranslationSaveQueue getTranslationSaveQueue() |
| Boolescher Wert „mayAccessUGC(ResourceResolver)“ |
