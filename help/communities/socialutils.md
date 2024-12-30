---
title: Umgestaltung von Social Media-Dienstprogrammen
description: Das Paket com.adobe.cq.social.ugcbase.SocialUtils ist seit AEM 6.1 veraltet
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 0f731ec6-a12e-4098-a1ec-ee4cd4dc1432
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 1%

---

# Umgestaltung von Social Media-Dienstprogrammen {#socialutils-refactoring}

## Soziales Utils-Paket veraltet {#socialutils-package-deprecated}

Das Paket `com.adobe.cq.social.ugcbase.SocialUtils` ist seit AEM 6.1 veraltet.

In den folgenden Tabellen sind die Methoden aufgeführt, die anstelle von `SocialUtils` Methoden verwendet werden sollen.

## SocialResourceUtilities-Paket  {#socialresourceutilities-package}

| Methoden in com.adobe.cq.social.srp.utilities.api.SocialResourceUtilities |
|---|
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

| Methoden in `com.adobe.cq.social.`utilities.resource.api.SocialResourceUtilities |
|---|
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
