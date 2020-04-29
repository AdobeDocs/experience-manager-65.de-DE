---
title: SocialUtils-Umgestaltung
seo-title: SocialUtils-Umgestaltung
description: Das Paket com.adobe.cq.social.ugcbase.SocialUtils wurde in AEM 6.1 nicht mehr unterstützt.
seo-description: Das Paket com.adobe.cq.social.ugcbase.SocialUtils wurde in AEM 6.1 nicht mehr unterstützt.
uuid: 54a0d98e-5ead-4c12-850f-8252ea9b3263
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 4ade0d6b-041e-4a2f-98f8-3b8fcae0fb29
translation-type: tm+mt
source-git-commit: 3296db289b2e2f4ca0d1981597ada6ca1310bd46

---


# SocialUtils-Umgestaltung {#socialutils-refactoring}

## SocialUtils-Paket veraltet {#socialutils-package-deprecated}

Das Paket `com.adobe.cq.social.ugcbase.SocialUtils` wurde in AEM 6.1 nicht mehr unterstützt.

In den folgenden Tabellen werden die Methoden Liste, die anstelle der SocialUtils-Methoden verwendet werden sollen.

## SocialResourceUtilities-Paket {#socialresourceutilities-package}

| Methoden in com.adobe.cq.social.srp.utilities.api.SocialResourceUtilities |
|---|
| Boolean checkPermission(ResourceResolver resolver, String path, String action) |  |
| SocialResourceProvider getSocialResourceProvider(Resource resource) |  |
| SocialResourceConfiguration getStorageConfig(ResourceResource) |  |
| Resource getUGCResource(Resource userResource) |  |
| Resource getUGCResource(Resource userResource, ResourceResolverFactory rrf) | new |
| Resource getUGCResource(Resource userResource, ResourceResolverFactory rf, String resourceTypeHint) | new |
| Resource getUGCResource(Resource userResource, String resourceTypeHint) |  |
| boolean hasModeratePermissions(Resource resource) |  |
| String resourceToACLPath(Resource resource) |  |
| String resourceToUGCStoragePath(Resource resource) | ersetzt String resourceToUGCPath(Resource resource) |
| String UGCToResourcePath(Resource resource) |  |
| String UGCToResourcePath(String ugcPath) | Methodenunterschrift geändert |
| String UGCToResourcePath(String ugcPath, ResourceResolver resolver) | new |

| Methoden in `com.adobe.cq.social.`utilities.resource.api.SocialResourceUtilities |
|---|
| SocialResourceProvider getSocialResourceProvider(Resource resource) | ersetzt SocialResourceProvider getConfigurationProvider(Resource resource) |

## SCFUtilities-Paket {#scfutilities-package}

| Methoden in `com.adobe.cq.social.`utilities.scf.api.SCFUtilites |
|---|
| String getAvatar(UserProperties userProperties) |
| String getAvatar(UserProperties userProperties, int size) |
| String getAvatar(UserProperties userProperties, String absoluteDefaultAvatar) |
| String getAvatar(UserProperties userProperties, String absoluteDefaultAvatar, SocialUtils.AVATAR_SIZE size) |
| Page getContainingPage(Resource resource) |
| String getSocialProfileURL(String username, ResourceResolver resolver, Page page) |
| UserProperties getUserProperties(ResourceResolver resolver, String userId) |

## For Internal Use Only {#for-internal-use-only}

| boolean canAddNode(Session session, String path) |
|---|
| String createUniqueNameHint(String message) |
| String createUniqueNameHint(String message, int numRandomChars) |
| String generateRandomString(int length) |
| SocialResourceConfiguration getDefaultStorageConfig() |
| Page getPage(String path, ResourceResolver resolver) |
| String getPagePath(Resource resource) |
| String getPagePath(String path) |
| String getResourceTypeForIncludedResource(Resource component, String defaultResourceType, String designPropertyName) |
| String getResourceTypeFromDesign(Resource resource, String styleProperty, String defaultValue) |
| boolean isResourceOwner(Resource resource) |
| String mapUGCPath(Resource resource) |
| String mapUGCPath(String ugcPath, ResourceResolver resolver) |
| boolean mayPost(ResourceResolver resolver, Resource resource) |
| String prepareUserGeneratedContent(ResourceResolver resolver, String path) |

## Methoden nicht mehr verfügbar {#methods-no-longer-available}

| Node createNode(ResourceResolver resolver, String path, String nodeType) |
|---|
| Resource getResourceAtPath(ResourceResolver resolver, String path) |
| Resource getResourceAtPath(ResourceResolver resolver, String path, String resourceType) |
| Configuration getStorageCloudServiceConfig(Resource resource) |
| TranslationManager getTranslationManager() |
| TranslationSaveQueue getTranslationSaveQueue() |
| boolean mayAccessUGC(ResourceResolver resolver) |

