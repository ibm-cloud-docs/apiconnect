---

copyright:
   years: 2020, 2024
lastupdated: "2024-07-02"

keywords: IBM Cloud, API Connect, Reserved instance, lifecycle, develop, create, manage, API, user, role, access, group, upgrade

subcollection: apiconnect

---

{{site.data.keyword.attribute-definition-list}}

# Upgrading your Reserved instance
{: #ri-upgrade}

You can perform an upgrade of your {{site.data.keyword.apiconnect_short}} Reserved instance on the {{site.data.keyword.apiconnect_short}} services page.
{: shortdesc}

## Is an upgrade available?
{: #avail_ri-upgrade}

When an upgrade is available for your Reserved instance, the "(Upgrade available)" message displays on the {{site.data.keyword.apiconnect_short}} services page, next to the instance's status.

To learn more about the upgrade, click the overflow menu on the same row of the services table, and select **Apply upgrade**.

## Scheduling and running an upgrade
{: #run_ri-upgrade}

1. To start the upgrade, click the overflow menu on the same row of the services table, and select **Apply upgrade**.

2. Review the upgrade description, which notes the current version, the newest available version, and the deadline (the date when the upgrade becomes unavailable).

   - The description includes a summary of the changes (fixes, new features, and so on) in the upgrade.

   - The description also indicates whether the upgrade will disrupt service, in which case you might want to schedule it for a later time to avoid impacting users.

   - If your service is using an outdated remote gateway, a reminder to upgrade the gateway displays in the Upgrade description window. For best results, you should upgrade the remote gateway before upgrading your Reserved instance. If you are scheduling the upgrade for a later date and time, you can choose when to upgrade the remote gateway. For information on adding a remote gateway, see [Adding a remote gateway](/docs/apiconnect?topic=apiconnect-ri-reg-gwy).

3. Choose when to start the upgrade process:

   - **Now** Select this option to start the upgrade immediately.
   - **Schedule** Select the date, time, and timezone to start the upgrade. You will receive an email reminder several days before the upgrade.

4. If the upgrade will disrupt service, you must indicate your agreement by selecting "I understand that my {{site.data.keyword.apiconnect_short}} service will be disrupted".

   You cannot start the upgrade until you acknowledge the potential disruption to service.

5. Click **Upgrade** to confirm the upgrade.

   If you chose to run the upgrade **Now** then the upgrade starts immediately. If you chose to **Schedule** the upgrade for later, you can continue working in {{site.data.keyword.apiconnect_short}} until the upgrade begins.

   The status of the upgrade displays next to the service's status on the {{site.data.keyword.apiconnect_short}} services page:
   - If the upgrade is in progress, the status displays "Upgrading" with an approximate duration.
   - If the upgrade is scheduled for a later time, the status displays the date and time of the scheduled upgrade. Use the overflow menu to reschedule the upgrade.
