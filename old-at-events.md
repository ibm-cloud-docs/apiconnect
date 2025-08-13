---

copyright:
   years: 2020, 2025
lastupdated: "2025-08-13"

keywords: activity tracker, event, security, audit logs, viewing events, management, API Connect

subcollection: apiconnect

---

{{site.data.keyword.attribute-definition-list}}

# Auditing events
{: #old-at_events}

As a security officer, auditor, or manager, you can use the Activity Tracker service to track how users and applications interact with the {{site.data.keyword.apiconnect_full}} V10 Reserved instance service in {{site.data.keyword.cloud}}.
{: shortdesc}

{{site.data.keyword.at_full_notm}} records user-initiated activities that change the state of a service in {{site.data.keyword.cloud_notm}}. You can use this service to investigate abnormal activity and critical actions and to comply with regulatory audit requirements. In addition, you can be alerted about actions as they happen. The events that are collected comply with the Cloud Auditing Data Federation (CADF) standard. For more information, see the [Getting started with IBM Cloud Logs](/docs/cloud-logs?topic=cloud-logs-getting-started&interface=ui).

IBM Cloud Activity Tracker Event Routing and IBM Cloud Logs replaces IBM Cloud Activity Tracker, which is deprecated and will be removed from support in March 2025.
{: note}

## List of events
{: #at_events-actions}

Table 1 describes the actions that the {{site.data.keyword.apiconnect_short}} V10 Reserved service provides for APIs, subscriptions, and domains.

| Action                          | Description     |
|---------------------------------|-----------------|
| apiconnect.user_registry_create.create | Create a User Registry object |
| apiconnect.user_registry_clear.delete | Clear the User Registry objects |
| apiconnect.user_registry_update.update | Update the User Registry object by name or ID |
| apiconnect.user_registry_del.delete | Delete the User Registry object by name or ID |
| apiconnect.user_registry_executeById.create | Execute a User Registry operation |
| apiconnect.user_registry_testConnectionById.create | Test a User Registry connection |
| apiconnect.user_registry_execute.create | Execute a User Registry operation |
| apiconnect.user_registry_testConnection.create | Test a User Registry connection |
| apiconnect.user_registry_search.create | Search for users in the user registry |
| apiconnect.user_create.create | Create a User object |
| apiconnect.user_clear.delete | Clear the User objects |
| apiconnect.user_update.update | Update the User object by name or ID |
| apiconnect.user_del.delete | Delete the User object by name or ID |
| apiconnect.user_requestPasswordReset.create | Send reset password link |
| apiconnect.user_resetPassword.create | Reset password |
| apiconnect.user_searchAdmin.create | Search for users in the admin realm |
| apiconnect.user_searchProvider.create | Search for users in the provider realm |
| apiconnect.oauth2_token.create | Generate a token |
| apiconnect.oauth2_redirect_post.create | Authorization provider redirect endpoint |
| apiconnect.api_key_create.create | Create a API Key object |
| apiconnect.api_key_del.delete | Delete the API Key object by name or ID |
| apiconnect.org_setting_singletonUpdate.update | Update the Organization Setting object |
| apiconnect.notification_template_updateProviderSubcollectionOrgScope.update | Update the Notification Template object by name or ID |
| apiconnect.notification_template_updateCatalogSubcollectionOrgScope.update | Update the Notification Template object by name or ID |
| apiconnect.notification_template_updateSpaceSubcollectionOrgScope.update | Update the Notification Template object by name or ID |
| apiconnect.notification_template_updateConsumerSubcollectionOrgScope.update | Update the Notification Template object by name or ID |
| apiconnect.org_update.update | Update the Organization object by name or ID |
| apiconnect.org_del.delete | Delete the Organization object by name or ID |
| apiconnect.org_transferOwner.create | Transfer owner to an associate |
| apiconnect.user_searchProviderOrgScope.create | Search provider users from an organization. |
| apiconnect.member_invitation_createOrgScope.create | Create a Member Invitation object |
| apiconnect.member_invitation_clearOrgScope.delete | Clear the Member Invitation objects |
| apiconnect.member_invitation_updateOrgScope.update | Update the Member Invitation object by name or ID |
| apiconnect.member_invitation_delOrgScope.delete | Delete the Member Invitation object by name or ID |
| apiconnect.member_invitation_regenerateOrgScope.create | Regenerate the Member Invitation |
| apiconnect.member_invitation_registerOrgScope.create | Register using the Member Invitation |
| apiconnect.member_invitation_acceptOrgScope.create | Accept using the Member Invitation |
| apiconnect.member_createOrgScope.create | Create a Member object |
| apiconnect.member_clearOrgScope.delete | Clear the Member objects |
| apiconnect.member_updateOrgScope.update | Update the Member object by name or ID |
| apiconnect.member_delOrgScope.delete | Delete the Member object by name or ID |
| apiconnect.role_createOrgScope.create | Create a Role object |
| apiconnect.role_clearOrgScope.delete | Clear the Role objects |
| apiconnect.role_updateOrgScope.update | Update the Role object by name or ID |
| apiconnect.role_delOrgScope.delete | Delete the Role object by name or ID |
| apiconnect.oauth_provider_create.create | Create a OAuth Provider object |
| apiconnect.oauth_provider_clear.delete | Clear the OAuth Provider objects |
| apiconnect.oauth_provider_update.update | Update the OAuth Provider object by name or ID |
| apiconnect.oauth_provider_del.delete | Delete the OAuth Provider object by name or ID |
| apiconnect.billing_create.create | Create a Billing object |
| apiconnect.billing_clear.delete | Clear the Billing objects |
| apiconnect.billing_update.update | Update the Billing object by name or ID |
| apiconnect.billing_del.delete | Delete the Billing object by name or ID |
| apiconnect.job_clear.delete | Clear the Job objects |
| apiconnect.job_del.delete | Delete the Job object by name or ID |
| apiconnect.tls_client_profile_create.create | Create a TLS Client Profile object |
| apiconnect.tls_client_profile_clearAll.delete | Clear all TLS Client Profile objects in all collections |
| apiconnect.tls_client_profile_clear.delete | Clear the TLS Client Profile objects |
| apiconnect.tls_client_profile_update.update | Update the TLS Client Profile object by ID |
| apiconnect.tls_client_profile_del.delete | Delete the TLS Client Profile object by ID |
| apiconnect.tls_client_profile_updateByNameVersion.update | Update the TLS Client Profile object by name and version |
| apiconnect.tls_client_profile_delByNameVersion.delete | Delete a TLS Client Profile |
| apiconnect.keystore_create.create | Create a Keystore object |
| apiconnect.keystore_clear.delete | Clear the Keystore objects |
| apiconnect.keystore_update.update | Update the Keystore object by name or ID |
| apiconnect.keystore_del.delete | Delete the Keystore object by name or ID |
| apiconnect.truststore_create.create | Create a Truststore object |
| apiconnect.truststore_clear.delete | Clear the Truststore objects |
| apiconnect.truststore_update.update | Update the Truststore object by name or ID |
| apiconnect.truststore_del.delete | Delete the Truststore object by name or ID |
| apiconnect.entry_createTruststoreScope.create | Create a Entry object |
| apiconnect.entry_clearTruststoreScope.delete | Clear the Entry objects |
| apiconnect.entry_updateTruststoreScope.update | Update the Entry object by name or ID |
| apiconnect.entry_delTruststoreScope.delete | Delete the Entry object by name or ID |
| apiconnect.catalog_setting_singletonUpdate.update | Update the Catalog Setting object |
| apiconnect.configured_gateway_service_createCatalogScope.create | Create a Configured Gateway Service object |
| apiconnect.configured_gateway_service_clearCatalogScope.delete | Clear the Configured Gateway Service objects |
| apiconnect.configured_gateway_service_delCatalogScope.delete | Delete the Configured Gateway Service object by name or ID |
| apiconnect.configured_gateway_service_createSpaceScope.create | Create a Configured Gateway Service object |
| apiconnect.configured_gateway_service_clearSpaceScope.delete | Clear the Configured Gateway Service objects |
| apiconnect.configured_gateway_service_delSpaceScope.delete | Delete the Configured Gateway Service object by name or ID |
| apiconnect.configured_catalog_user_registry_create.create | Create a Configured Catalog User Registry object |
| apiconnect.configured_catalog_user_registry_del.delete | Delete the Configured Catalog User Registry object by name or ID |
| apiconnect.configured_catalog_user_registry_search.create | Search for users in the catalog user registry |
| apiconnect.configured_api_user_registry_createCatalogScope.create | Create a Configured API User Registry object |
| apiconnect.configured_api_user_registry_clearCatalogScope.delete | Clear the Configured API User Registry objects |
| apiconnect.configured_api_user_registry_delCatalogScope.delete | Delete the Configured API User Registry object by name or ID |
| apiconnect.configured_api_user_registry_createSpaceScope.create | Create a Configured API User Registry object |
| apiconnect.configured_api_user_registry_clearSpaceScope.delete | Clear the Configured API User Registry objects |
| apiconnect.configured_api_user_registry_delSpaceScope.delete | Delete the Configured API User Registry object by name or ID |
| apiconnect.configured_tls_client_profile_createCatalogScope.create | Create a Configured TLS Client Profile object |
| apiconnect.configured_tls_client_profile_clearAllCatalogScope.delete | Clear all Configured TLS Client Profile objects in all collections |
| apiconnect.configured_tls_client_profile_clearCatalogScope.delete | Clear the Configured TLS Client Profile objects |
| apiconnect.configured_tls_client_profile_delCatalogScope.delete | Delete the Configured TLS Client Profile object by ID |
| apiconnect.configured_tls_client_profile_delByNameVersionCatalogScope.delete | Delete a Configured TLS Client Profile |
| apiconnect.configured_tls_client_profile_createSpaceScope.create | Create a Configured TLS Client Profile object |
| apiconnect.configured_tls_client_profile_clearAllSpaceScope.delete | Clear all Configured TLS Client Profile objects in all collections |
| apiconnect.configured_tls_client_profile_clearSpaceScope.delete | Clear the Configured TLS Client Profile objects |
| apiconnect.configured_tls_client_profile_delSpaceScope.delete | Delete the Configured TLS Client Profile object by ID |
| apiconnect.configured_tls_client_profile_delByNameVersionSpaceScope.delete | Delete a Configured TLS Client Profile |
| apiconnect.configured_billing_create.create | Create a Configured Billing object |
| apiconnect.configured_billing_clear.delete | Clear the Configured Billing objects |
| apiconnect.configured_billing_del.delete | Delete the Configured Billing object by name or ID |
| apiconnect.configured_oauth_provider_createCatalogScope.create | Create a Configured OAuth Provider object |
| apiconnect.configured_oauth_provider_clearCatalogScope.delete | Clear the Configured OAuth Provider objects |
| apiconnect.configured_oauth_provider_delCatalogScope.delete | Delete the Configured OAuth Provider object by name or ID |
| apiconnect.configured_oauth_provider_createSpaceScope.create | Create a Configured OAuth Provider object |
| apiconnect.configured_oauth_provider_clearSpaceScope.delete | Clear the Configured OAuth Provider objects |
| apiconnect.configured_oauth_provider_delSpaceScope.delete | Delete the Configured OAuth Provider object by name or ID |
| apiconnect.notification_template_updateCatalogSubcollectionCatalogScope.update | Update the Notification Template object by name or ID |
| apiconnect.notification_template_updateSpaceSubcollectionCatalogScope.update | Update the Notification Template object by name or ID |
| apiconnect.notification_template_updateConsumerSubcollectionCatalogScope.update | Update the Notification Template object by name or ID |
| apiconnect.role_default_createConsumerSubcollectionCatalogScope.create | Create a Role Default object |
| apiconnect.role_default_clearConsumerSubcollectionCatalogScope.delete | Clear the Role Default objects |
| apiconnect.role_default_updateConsumerSubcollectionCatalogScope.update | Update the Role Default object by name or ID |
| apiconnect.role_default_delConsumerSubcollectionCatalogScope.delete | Delete the Role Default object by name or ID |
| apiconnect.property_mapCreateCatalogScope.update | Augment the Configuration Property with additional name/value pairs |
| apiconnect.property_mapClearCatalogScope.delete | Clear the Configuration Property objects |
| apiconnect.property_mapUpdateCatalogScope.update | Update the Configuration Property object |
| apiconnect.property_mapDelCatalogScope.delete | Delete the Configuration Property object |
| apiconnect.catalog_create.create | Create a Catalog object |
| apiconnect.catalog_clear.delete | Clear the Catalog objects |
| apiconnect.catalog_update.update | Update the Catalog object by name or ID |
| apiconnect.catalog_del.delete | Delete the Catalog object by name or ID |
| apiconnect.catalog_transferOwner.create | Transfer owner to an associate |
| apiconnect.catalog_sendEmail.create | Send email |
| apiconnect.user_searchCatalog.create | Search for users in the catalog realm |
| apiconnect.catalog_stageDraftProduct.create | Stage a draft product |
| apiconnect.catalog_publishDraftProduct.create | Publish a draft product |
| apiconnect.catalog_stage.create | Stage the product |
| apiconnect.catalog_publish.create | Publish the product |
| apiconnect.invitation_createCatalogScope.create | Create a Catalog Invitation object |
| apiconnect.invitation_clearCatalogScope.delete | Clear the Catalog Invitation objects |
| apiconnect.invitation_updateCatalogScope.update | Update the Catalog Invitation object by name or ID |
| apiconnect.invitation_delCatalogScope.delete | Delete the Catalog Invitation object by name or ID |
| apiconnect.invitation_regenerateCatalogScope.create | Regenerate the Catalog Invitation |
| apiconnect.invitation_registerCatalogScope.create | Register using the Catalog Invitation |
| apiconnect.invitation_acceptCatalogScope.create | Accept using the Catalog Invitation |
| apiconnect.member_invitation_createCatalogScope.create | Create a Member Invitation object |
| apiconnect.member_invitation_clearCatalogScope.delete | Clear the Member Invitation objects |
| apiconnect.member_invitation_updateCatalogScope.update | Update the Member Invitation object by name or ID |
| apiconnect.member_invitation_delCatalogScope.delete | Delete the Member Invitation object by name or ID |
| apiconnect.member_invitation_regenerateCatalogScope.create | Regenerate the Member Invitation |
| apiconnect.member_invitation_registerCatalogScope.create | Register using the Member Invitation |
| apiconnect.member_invitation_acceptCatalogScope.create | Accept using the Member Invitation |
| apiconnect.member_createCatalogScope.create | Create a Member object |
| apiconnect.member_clearCatalogScope.delete | Clear the Member objects |
| apiconnect.member_updateCatalogScope.update | Update the Member object by name or ID |
| apiconnect.member_delCatalogScope.delete | Delete the Member object by name or ID |
| apiconnect.task_updateCatalogScope.update | Update the Task object by name or ID |
| apiconnect.role_updateCatalogScope.update | Update the Role object by name or ID |
| apiconnect.global_policy_createCatalogScope.create | Create a Global Policy object |
| apiconnect.global_policy_clearAllCatalogScope.delete | Clear all Global Policy objects in all collections |
| apiconnect.global_policy_clearCatalogScope.delete | Clear the Global Policy objects |
| apiconnect.global_policy_updateCatalogScope.update | Update the Global Policy object by ID |
| apiconnect.global_policy_delCatalogScope.delete | Delete the Global Policy object by ID |
| apiconnect.global_policy_updateByNameVersionCatalogScope.update | Update the Global Policy object by name and version |
| apiconnect.global_policy_delByNameVersionCatalogScope.delete | Delete a Global Policy |
| apiconnect.global_policy_createSpaceScope.create | Create a Global Policy object |
| apiconnect.global_policy_clearAllSpaceScope.delete | Clear all Global Policy objects in all collections |
| apiconnect.global_policy_clearSpaceScope.delete | Clear the Global Policy objects |
| apiconnect.global_policy_updateSpaceScope.update | Update the Global Policy object by ID |
| apiconnect.global_policy_delSpaceScope.delete | Delete the Global Policy object by ID |
| apiconnect.global_policy_updateByNameVersionSpaceScope.update | Update the Global Policy object by name and version |
| apiconnect.global_policy_delByNameVersionSpaceScope.delete | Delete a Global Policy |
| apiconnect.policy_createCatalogScope.create | Create a Policy object |
| apiconnect.policy_clearAllCatalogScope.delete | Clear all Policy objects in all collections |
| apiconnect.policy_clearCatalogScope.delete | Clear the Policy objects |
| apiconnect.policy_updateCatalogScope.update | Update the Policy object by ID |
| apiconnect.policy_delCatalogScope.delete | Delete the Policy object by ID |
| apiconnect.policy_updateByNameVersionCatalogScope.update | Update the Policy object by name and version |
| apiconnect.policy_delByNameVersionCatalogScope.delete | Delete a Policy |
| apiconnect.policy_createSpaceScope.create | Create a Policy object |
| apiconnect.policy_clearAllSpaceScope.delete | Clear all Policy objects in all collections |
| apiconnect.policy_clearSpaceScope.delete | Clear the Policy objects |
| apiconnect.policy_updateSpaceScope.update | Update the Policy object by ID |
| apiconnect.policy_delSpaceScope.delete | Delete the Policy object by ID |
| apiconnect.policy_updateByNameVersionSpaceScope.update | Update the Policy object by name and version |
| apiconnect.policy_delByNameVersionSpaceScope.delete | Delete a Policy |
| apiconnect.extension_createCatalogScope.create | Create a Extension object |
| apiconnect.extension_clearAllCatalogScope.delete | Clear all Extension objects in all collections |
| apiconnect.extension_clearCatalogScope.delete | Clear the Extension objects |
| apiconnect.extension_updateCatalogScope.update | Update the Extension object by ID |
| apiconnect.extension_delCatalogScope.delete | Delete the Extension object by ID |
| apiconnect.extension_updateByNameVersionCatalogScope.update | Update the Extension object by name and version |
| apiconnect.extension_delByNameVersionCatalogScope.delete | Delete a Extension |
| apiconnect.extension_createSpaceScope.create | Create a Extension object |
| apiconnect.extension_clearAllSpaceScope.delete | Clear all Extension objects in all collections |
| apiconnect.extension_clearSpaceScope.delete | Clear the Extension objects |
| apiconnect.extension_updateSpaceScope.update | Update the Extension object by ID |
| apiconnect.extension_delSpaceScope.delete | Delete the Extension object by ID |
| apiconnect.extension_updateByNameVersionSpaceScope.update | Update the Extension object by name and version |
| apiconnect.extension_delByNameVersionSpaceScope.delete | Delete a Extension |
| apiconnect.service_create.create | Create a Service object |
| apiconnect.service_clearAll.delete | Clear all Service objects in all collections |
| apiconnect.service_clear.delete | Clear the Service objects |
| apiconnect.service_update.update | Update the Service object by ID |
| apiconnect.service_del.delete | Delete the Service object by ID |
| apiconnect.service_updateByNameVersion.update | Update the Service object by name and version |
| apiconnect.service_delByNameVersion.delete | Delete a Service |
| apiconnect.service_createSpaceInitiated.create | Create a Service object |
| apiconnect.service_clearAllSpaceInitiated.delete | Clear all Service objects in all collections |
| apiconnect.service_clearSpaceInitiated.delete | Clear the Service objects |
| apiconnect.service_updateSpaceInitiated.update | Update the Service object by ID |
| apiconnect.service_delSpaceInitiated.delete | Delete the Service object by ID |
| apiconnect.service_updateByNameVersionSpaceInitiated.update | Update the Service object by name and version |
| apiconnect.service_delByNameVersionSpaceInitiated.delete | Delete a Service |
| apiconnect.global_policy_prehook_singletonCreateCatalogScope.create | Create the Global Policy Prehook object |
| apiconnect.global_policy_prehook_singletonUpdateCatalogScope.update | Update the Global Policy Prehook object |
| apiconnect.global_policy_prehook_singletonDelCatalogScope.delete | Delete the Global Policy Prehook object |
| apiconnect.global_policy_prehook_singletonCreateSpaceScope.create | Create the Global Policy Prehook object |
| apiconnect.global_policy_prehook_singletonUpdateSpaceScope.update | Update the Global Policy Prehook object |
| apiconnect.global_policy_prehook_singletonDelSpaceScope.delete | Delete the Global Policy Prehook object |
| apiconnect.global_policy_posthook_singletonCreateCatalogScope.create | Create the Global Policy Posthook object |
| apiconnect.global_policy_posthook_singletonUpdateCatalogScope.create | Update the Global Policy Posthook object |
| apiconnect.global_policy_posthook_singletonDelCatalogScope.create | Delete the Global Policy Posthook object |
| apiconnect.global_policy_posthook_singletonCreateSpaceScope.create | Create the Global Policy Posthook object |
| apiconnect.global_policy_posthook_singletonUpdateSpaceScope.create | Update the Global Policy Posthook object |
| apiconnect.global_policy_posthook_singletonDelSpaceScope.create | Delete the Global Policy Posthook object |
| apiconnect.analytics_createCatalogScope.create | Create an Analytics object |
| apiconnect.analytics_createSpaceScope.create | Create an Analytics object |
| apiconnect.space_setting_singletonUpdate.update | Update the Space Setting object |
| apiconnect.notification_template_updateSpaceSubcollectionSpaceScope.update | Update the Notification Template object by name or ID |
| apiconnect.notification_template_updateConsumerSubcollectionSpaceScope.update | Update the Notification Template object by name or ID |
| apiconnect.role_default_createConsumerSubcollectionSpaceScope.create | Create a Role Default object |
| apiconnect.role_default_clearConsumerSubcollectionSpaceScope.delete | Clear the Role Default objects |
| apiconnect.role_default_updateConsumerSubcollectionSpaceScope.update | Update the Role Default object by name or ID |
| apiconnect.role_default_delConsumerSubcollectionSpaceScope.delete | Delete the Role Default object by name or ID |
| apiconnect.space_create.create | Create a Space object |
| apiconnect.space_clear.delete | Clear the Space objects |
| apiconnect.space_update.update | Update the Space object by name or ID |
| apiconnect.space_del.delete | Delete the Space object by name or ID |
| apiconnect.space_transferOwner.create | Transfer owner to an associate |
| apiconnect.space_stageDraftProductSpaceSubcollection.create | Stage a draft product |
| apiconnect.space_publishDraftProductSpaceSubcollection.create | Publish a draft product |
| apiconnect.space_stageSpaceSubcollection.create | Stage the product |
| apiconnect.space_publishSpaceSubcollection.create | Publish the product |
| apiconnect.invitation_createSpaceScope.create | Create a Space Invitation object |
| apiconnect.invitation_clearSpaceScope.delete | Clear the Space Invitation objects |
| apiconnect.invitation_updateSpaceScope.update | Update the Space Invitation object by name or ID |
| apiconnect.invitation_delSpaceScope.delete | Delete the Space Invitation object by name or ID |
| apiconnect.invitation_regenerateSpaceScope.create | Regenerate the Space Invitation |
| apiconnect.invitation_registerSpaceScope.create | Register using the Space Invitation |
| apiconnect.invitation_acceptSpaceScope.create | Accept using the Space Invitation |
| apiconnect.role_updateSpaceScope.update | Update the Role object by name or ID |
| apiconnect.member_invitation_createSpaceScope.create | Create a Member Invitation object |
| apiconnect.member_invitation_clearSpaceScope.delete | Clear the Member Invitation objects |
| apiconnect.member_invitation_updateSpaceScope.update | Update the Member Invitation object by name or ID |
| apiconnect.member_invitation_delSpaceScope.delete | Delete the Member Invitation object by name or ID |
| apiconnect.member_invitation_regenerateSpaceScope.create | Regenerate the Member Invitation |
| apiconnect.member_invitation_registerSpaceScope.create | Register using the Member Invitation |
| apiconnect.member_invitation_acceptSpaceScope.create | Accept using the Member Invitation |
| apiconnect.member_createSpaceScope.create | Create a Member object |
| apiconnect.member_clearSpaceScope.delete | Clear the Member objects |
| apiconnect.member_updateSpaceScope.update | Update the Member object by name or ID |
| apiconnect.member_delSpaceScope.delete | Delete the Member object by name or ID |
| apiconnect.task_updateSpaceScope.update | Update the Task object by name or ID |
| apiconnect.consumer_org_setting_singletonUpdate.update | Update the Consumer Organization Setting object |
| apiconnect.consumer_org_setting_singletonDel.delete | Delete the Consumer Organization Setting object |
| apiconnect.consumer_org_setting_singletonUpdateSpaceInitiated.update | Update the Consumer Organization Setting object |
| apiconnect.consumer_org_setting_singletonDelSpaceInitiated.delete | Delete the Consumer Organization Setting object |
| apiconnect.activation_clearOrgScope.delete | Clear the Activation objects |
| apiconnect.activation_delOrgScope.delete | Delete the Activation object by name or ID |
| apiconnect.invitation_createConsumerOrgScope.create | Create a Consumer Organization Invitation object |
| apiconnect.invitation_clearConsumerOrgScope.delete | Clear the Consumer Organization Invitation objects |
| apiconnect.invitation_updateConsumerOrgScope.update | Update the Consumer Organization Invitation object by name or ID |
| apiconnect.invitation_delConsumerOrgScope.delete | Delete the Consumer Organization Invitation object by name or ID |
| apiconnect.invitation_regenerateConsumerOrgScope.create | Regenerate the Consumer Organization Invitation |
| apiconnect.invitation_createConsumerOrgScopeSpaceInitiated.create | Create a Consumer Organization Invitation object |
| apiconnect.invitation_clearConsumerOrgScopeSpaceInitiated.delete | Clear the Consumer Organization Invitation objects |
| apiconnect.invitation_updateConsumerOrgScopeSpaceInitiated.update | Update the Consumer Organization Invitation object by name or ID |
| apiconnect.invitation_delConsumerOrgScopeSpaceInitiated.delete | Delete the Consumer Organization Invitation object by name or id |
| apiconnect.invitation_regenerateConsumerOrgScopeSpaceInitiated.create | Regenerate the Consumer Organization Invitation |
| apiconnect.consumer_org_create.create | Create a Consumer Organization object |
| apiconnect.consumer_org_clear.delete | Clear the Consumer Organization objects |
| apiconnect.consumer_org_update.update | Update the Consumer Organization object by name or ID |
| apiconnect.consumer_org_del.delete | Delete the Consumer Organization object by name or ID |
| apiconnect.consumer_org_transferOwner.create | Transfer owner to an associate |
| apiconnect.consumer_org_createSpaceInitiated.create | Create a Consumer Organization object |
| apiconnect.consumer_org_clearSpaceInitiated.delete | Clear the Consumer Organization objects |
| apiconnect.consumer_org_updateSpaceInitiated.update | Update the Consumer Organization object by name or ID |
| apiconnect.consumer_org_delSpaceInitiated.delete | Delete the Consumer Organization object by name or ID |
| apiconnect.consumer_org_transferOwnerSpaceInitiated.create | Transfer owner to an associate |
| apiconnect.group_createCatalogScope.create | Create a Group object |
| apiconnect.group_clearCatalogScope.delete | Clear the Group objects |
| apiconnect.group_updateCatalogScope.update | Update the Group object by name or ID |
| apiconnect.group_delCatalogScope.delete | Delete the Group object by name or ID |
| apiconnect.group_createSpaceInitiated.create | Create a Group object |
| apiconnect.group_clearSpaceInitiated.delete | Clear the Group objects |
| apiconnect.group_updateSpaceInitiated.update | Update the Group object by name or ID |
| apiconnect.group_delSpaceInitiated.delete | Delete the Group object by name or ID |
| apiconnect.payment_method_create.create | Create a Payment Method object |
| apiconnect.payment_method_update.update | Update the Payment Method object by name or ID |
| apiconnect.payment_method_del.delete | Delete the Payment Method object by name or ID |
| apiconnect.payment_method_createSpaceInitiated.create | Create a Payment Method object |
| apiconnect.payment_method_updateSpaceInitiated.update | Update the Payment Method object by name or ID |
| apiconnect.payment_method_delSpaceInitiated.delete | Delete the Payment Method object by name or ID |
| apiconnect.role_createConsumerOrgScope.create | Create a Role object |
| apiconnect.role_clearConsumerOrgScope.delete | Clear the Role objects |
| apiconnect.role_updateConsumerOrgScope.update | Update the Role object by name or ID |
| apiconnect.role_delConsumerOrgScope.delete | Delete the Role object by name or ID |
| apiconnect.role_createConsumerOrgScopeSpaceInitiated.create | Create a Role object |
| apiconnect.role_clearConsumerOrgScopeSpaceInitiated.delete | Clear the Role objects |
| apiconnect.role_updateConsumerOrgScopeSpaceInitiated.update | Update the Role object by name or ID |
| apiconnect.role_delConsumerOrgScopeSpaceInitiated.delete | Delete the Role object by name or ID |
| apiconnect.member_invitation_createConsumerOrgScope.create | Create a Member Invitation object |
| apiconnect.member_invitation_clearConsumerOrgScope.delete | Clear the Member Invitation objects |
| apiconnect.member_invitation_updateConsumerOrgScope.update | Update the Member Invitation object by name or ID |
| apiconnect.member_invitation_delConsumerOrgScope.delete | Delete the Member Invitation object by name or ID |
| apiconnect.member_invitation_regenerateConsumerOrgScope.create | Regenerate the Member Invitation |
| apiconnect.member_invitation_createConsumerOrgScopeSpaceInitiated.create | Create a Member Invitation object |
| apiconnect.member_invitation_clearConsumerOrgScopeSpaceInitiated.delete | Clear the Member Invitation objects |
| apiconnect.member_invitation_updateConsumerOrgScopeSpaceInitiated.update | Update the Member Invitation object by name or ID |
| apiconnect.member_invitation_delConsumerOrgScopeSpaceInitiated.delete | Delete the Member Invitation object by name or ID |
| apiconnect.member_invitation_regenerateConsumerOrgScopeSpaceInitiated.create | Regenerate the Member Invitation |
| apiconnect.member_createConsumerOrgScope.create | Create a Member object |
| apiconnect.member_clearConsumerOrgScope.delete | Clear the Member objects |
| apiconnect.member_updateConsumerOrgScope.update | Update the Member object by name or ID |
| apiconnect.member_delConsumerOrgScope.delete | Delete the Member object by name or ID |
| apiconnect.member_createConsumerOrgScopeSpaceInitiated.create | Create a Member object |
| apiconnect.member_clearConsumerOrgScopeSpaceInitiated.delete | Clear the Member objects |
| apiconnect.member_updateConsumerOrgScopeSpaceInitiated.update | Update the Member object by name or ID |
| apiconnect.member_delConsumerOrgScopeSpaceInitiated.delete | Delete the Member object by name or ID |
| apiconnect.app_create.create | Create a Application object |
| apiconnect.app_clear.delete | Clear the Application objects |
| apiconnect.app_update.update | Update the Application object by name or ID |
| apiconnect.app_del.delete | Delete the Application object by name or ID |
| apiconnect.app_createSpaceInitiated.create | Create a Application object |
| apiconnect.app_clearSpaceInitiated.delete | Clear the Application objects |
| apiconnect.app_updateSpaceInitiated.update | Update the Application object by name or ID |
| apiconnect.app_delSpaceInitiated.delete | Delete the Application object by name or ID |
| apiconnect.credential_create.create | Create a Application Credential object |
| apiconnect.credential_update.update | Update the Application Credential object by name or ID |
| apiconnect.credential_del.delete | Delete the Application Credential object by name or ID |
| apiconnect.credential_reset.create | Reset the client id and client secret |
| apiconnect.credential_resetClientSecret.create | Reset the client secret |
| apiconnect.credential_verifyClientSecret.create | Verify the client secret |
| apiconnect.credential_createSpaceInitiated.create | Create a Application Credential object |
| apiconnect.credential_clearSpaceInitiated.delete | Clear the Application Credential objects |
| apiconnect.credential_updateSpaceInitiated.update | Update the Application Credential object by name or ID |
| apiconnect.credential_delSpaceInitiated.delete | Delete the Application Credential object by name or ID |
| apiconnect.credential_resetSpaceInitiated.create | Reset the client id and client secret |
| apiconnect.credential_resetClientSecretSpaceInitiated.create | Reset the client secret |
| apiconnect.credential_verifyClientSecretSpaceInitiated.create | Verify the client secret |
| apiconnect.subscription_create.create | Create a Subscription object |
| apiconnect.subscription_clear.delete | Clear the Subscription objects |
| apiconnect.subscription_update.update | Update the Subscription object by name or ID |
| apiconnect.subscription_del.delete | Delete the Subscription object by name or ID |
| apiconnect.subscription_createSpaceInitiated.create | Create a Subscription object |
| apiconnect.subscription_clearSpaceInitiated.delete | Clear the Subscription objects |
| apiconnect.subscription_updateSpaceInitiated.update | Update the Subscription object by name or ID |
| apiconnect.subscription_delSpaceInitiated.delete | Delete the Subscription object by name or ID |
| apiconnect.draft_clear.delete | Clear the Draft objects |
| apiconnect.draft_introspectWsdl.create | Introspect the WSDL |
| apiconnect.draft_product_create.create | Create a Draft Product object |
| apiconnect.draft_product_clearAll.delete | Clear all Draft Product objects in all collections |
| apiconnect.draft_product_clear.delete | Clear the Draft Product objects |
| apiconnect.draft_product_update.update | Update the Draft Product object by ID |
| apiconnect.draft_product_del.delete | Delete the Draft Product object by ID |
| apiconnect.draft_product_updateByNameVersion.update | Update the Draft Product object by name and version |
| apiconnect.draft_product_delByNameVersion.delete | Delete a Draft Product |
| apiconnect.draft_product_validate.create | Validate the draft product |
| apiconnect.draft_product_validateByNameVersion.create | Validate the draft product |
| apiconnect.draft_api_create.create | Create a Draft API object |
| apiconnect.draft_api_clearAll.delete | Clear all Draft API objects in all collections |
| apiconnect.draft_api_clear.delete | Clear the Draft API objects |
| apiconnect.draft_api_update.update | Update the Draft API object by ID |
| apiconnect.draft_api_del.delete | Delete the Draft API object by ID |
| apiconnect.draft_api_updateByNameVersion.update | Update the Draft API object by name and version |
| apiconnect.draft_api_delByNameVersion.delete | Delete a Draft API |
| apiconnect.draft_api_validate.create | Validate the draft api |
| apiconnect.draft_api_validateByNameVersion.create | Validate the draft api |
| apiconnect.product_clearAllCatalogScope.delete | Clear all Product objects in all collections |
| apiconnect.product_clearCatalogScope.delete | Clear the Product objects |
| apiconnect.product_updateCatalogScope.update | Update the Product object by ID |
| apiconnect.product_delCatalogScope.delete | Delete the Product object by ID |
| apiconnect.product_updateByNameVersionCatalogScope.update | Update the Product object by name and version |
| apiconnect.product_delByNameVersionCatalogScope.delete | Delete a Product |
| apiconnect.product_replaceCatalogScope.create | Hot replace a product |
| apiconnect.product_supersedeCatalogScope.create | Supersede a product |
| apiconnect.product_migrateSubscriptionsCatalogScope.create | Migrate list of subscriptions between products |
| apiconnect.product_replaceByNameVersionCatalogScope.create | Hot replace the product |
| apiconnect.product_supersedeByNameVersionCatalogScope.create | Supersede a product |
| apiconnect.product_migrateSubscriptionsByNameVersionCatalogScope.create | Migrate list of subscriptions between products |
| apiconnect.api_updateCatalogScope.update | Update the API object by ID |
| apiconnect.api_updateByNameVersionCatalogScope.update | Update the API object by name and version |
| apiconnect.product_clearAllSpaceScope.delete | Clear all Product objects in all collections |
| apiconnect.product_clearSpaceScope.delete | Clear the Product objects |
| apiconnect.product_updateSpaceScope.update | Update the Product object by ID |
| apiconnect.product_delSpaceScope.delete | Delete the Product object by ID |
| apiconnect.product_updateByNameVersionSpaceScope.update | Update the Product object by name and version |
| apiconnect.product_delByNameVersionSpaceScope.delete | Delete a Product |
| apiconnect.product_replaceSpaceScope.create | Hot replace a product |
| apiconnect.product_supersedeSpaceScope.create | Supersede a product |
| apiconnect.product_migrateSubscriptionsSpaceScope.create | Migrate list of subscriptions between products |
| apiconnect.product_replaceByNameVersionSpaceScope.create | Hot replace the product |
| apiconnect.product_supersedeByNameVersionSpaceScope.create | Supersede a product |
| apiconnect.product_migrateSubscriptionsByNameVersionSpaceScope.create | Migrate list of subscriptions between products |
| apiconnect.api_updateSpaceScope.update | Update the API object by ID |
| apiconnect.api_updateByNameVersionSpaceScope.update | Update the API object by name and version |
| apiconnect.me_singletonUpdate.update | Update the Me object |
| apiconnect.me_singletonDel.delete | Delete the Me object |
| apiconnect.me_changePassword.create | Change my password |
| apiconnect.me_resetPassword.create | Reset password |
| apiconnect.me_signOut.create | Sign out |
| apiconnect.webhook_updateCatalogScope.update | Update the Webhook object by name or ID |
{: caption="Actions that generate events" caption-side="top"}

## Viewing events
{: #at_events-ui}

Events that are generated by an {{site.data.keyword.apiconnect_short}} Reserved instance are automatically forwarded to the {{site.data.keyword.at_full_notm}} service instance that is available in the same location.

{{site.data.keyword.at_full_notm}} can have only one instance per location. To view events, you must access the web UI of the {{site.data.keyword.at_full_notm}} service in the same location where your service instance is available. For more information, see [Getting started with IBM Cloud Logs](/docs/cloud-logs?topic=cloud-logs-getting-started&interface=ui).
