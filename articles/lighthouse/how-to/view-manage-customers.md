---
title: View and manage customers and delegated resources in the Azure portal
description: As a service provider or enterprise using Azure Lighthouse, you can view all of your delegated resources and subscriptions by going to My customers in the Azure portal. 
ms.date: 08/10/2021
ms.topic: how-to
---

# View and manage customers and delegated resources in the Azure portal

Service providers using [Azure Lighthouse](../overview.md) can use the **My customers** page in the [Azure portal](https://portal.azure.com) to view delegated customer resources and subscriptions.

> [!TIP]
> While we'll refer to service providers and customers here, [enterprises managing multiple tenants](../concepts/enterprise.md) can use the same process to consolidate their management experience.

To access the **My customers** page in the Azure portal, select **All services**, then search for **My customers** and select it. You can also find it by entering “My customers” in the search box near the top of the Azure portal.

Keep in mind that the top **Customers** section of the **My customers** page only shows info about customers who have delegated subscriptions or resource groups to your Azure Active Directory (Azure AD) tenant through Azure Lighthouse. If you work with other customers (such as through the [Cloud Solution Provider (CSP) program](/partner-center/csp-overview)), you won’t see info about those customers in the **Customers** section unless you have [onboarded their resources to Azure Lighthouse](onboard-customer.md) (though you may see details about certain CSP customers in the [Cloud Solution Provider (Preview) section](#cloud-solution-provider-preview) lower on the page).

> [!NOTE]
> Your customers can view info about service providers by navigating to **Service providers** in the Azure portal. For more info, see [View and manage service providers](view-manage-service-providers.md).

## View and manage customer details

To view customer details, select **Customers** on the left side of the **My customers** page.

> [!IMPORTANT]
> In order to see this information, users must have been granted the [Reader](../../role-based-access-control/built-in-roles.md#reader) role (or another built-in role which includes Reader access) in the onboarding process.

For each customer, you'll see the customer's name, customer ID (tenant ID), and the **Offer ID** and **Offer version** associated with the engagement. In the **Delegations** column, you'll see the number of delegated subscriptions and/or the number of delegated resource groups.

Options at the top of the page let you sort, filter, and group your customer information by specific customers, offers, or keywords.

You can view the following information from this page:

- To see all of the subscriptions, offers, and delegations associated with a customer, select the customer's name.
- To see more details about an offer and its delegations, select the offer name.
- To view more details about role assignments for delegated subscriptions or resource groups, select the entry in the **Delegations** column.

## View and manage delegations

Delegations show the subscription or resource group that has been delegated, along with the users and permissions that have access to it. To view this info, select **Delegations** on the left side of the **My customers** page.

Options at the top of the page let you sort, filter, and group this information by specific customers, offers, or keywords.

### View role assignments

The users and permissions associated with each delegation appear in the **Role assignments** column. You can select each entry to view the full list of users, groups, and service principals that have been granted access to the subscription or resource group. From there, you can select a particular user, group, or service principal name to get more details.

### Remove delegations

If you included users with the [Managed Services Registration Assignment Delete Role](../../role-based-access-control/built-in-roles.md#managed-services-registration-assignment-delete-role) when onboarding a customer to Azure Lighthouse, those users can remove a delegation by selecting the trash can icon that appears in the row for that delegation. When they do so, no users in the service provider's tenant will be able to access the resources that had been previously delegated.

For more information, see [Remove access to a delegation](remove-delegation.md).

## View delegation change activity

The **Activity log** section of the **My customers** page keeps track of every time customer subscriptions or resource groups are delegated to your tenant, and every time previously delegated resources are removed. This information can only be viewed by users who have been [assigned the Monitoring Reader role at root scope](monitor-delegation-changes.md).

For more information, see [View delegation changes in the Azure portal](monitor-delegation-changes.md#view-delegation-changes-in-the-azure-portal).

## Work in the context of a delegated subscription

You can work directly in the context of a delegated subscription within the Azure portal, without switching the directory you're signed in to. To do so:

1. Select the **Directory + subscriptions** or **Settings** icon near the top of the Azure portal.
1. In the [Directories + subscriptions settings page](../../azure-portal/set-preferences.md#directories--subscriptions), ensure that the **Advanced filters** toggle is [turned off](../../azure-portal/set-preferences.md#subscription-filters).
1. In the **Default subscription filter** section, select the appropriate directory and subscription.

:::image type="content" source="../media/subscription-filter-delegated.png" alt-text="Screenshot of a filter showing one delegated subscription.":::

If you then access a service which supports [cross-tenant management experiences](../concepts/cross-tenant-management-experience.md), the service will default to the context of the delegated subscription that you included in your filter. You can change this by following the steps above and checking the **Select all** box (or choosing one or more subscriptions to work in instead).

> [!NOTE]
> If you have been granted access to one or more resource groups, rather than access to an entire subscription, select the subscription to which that resource group belongs. You'll then work in the context of that subscription, but will only be able to access the designated resource group(s).

You can also access functionality related to delegated subscriptions or resource groups from within services that support cross-tenant management experiences by selecting the subscription or resource group from within an individual service.

## Cloud Solution Provider (Preview)

A separate **Cloud Solution Provider (Preview)** section of the **My customers** page shows billing info and resources for your CSP customers who have [signed the Microsoft Customer Agreement (MCA)](/partner-center/confirm-customer-agreement) and are [under the Azure plan](/partner-center/azure-plan-get-started). For more information, see [Get started with your Microsoft Partner Agreement billing account](../../cost-management-billing/understand/mpa-overview.md).

Such CSP customers will appear in this section whether or not you have also onboarded them to Azure Lighthouse. Similarly, a CSP customer does not have to appear in the **Cloud Solution Provider (Preview)** section of **My customers** in order for you to onboard them to Azure Lighthouse.

## Next steps

- Learn about [cross-tenant management experiences](../concepts/cross-tenant-management-experience.md).
- Learn how your customers can [view and manage service providers](view-manage-service-providers.md) by going to **Service providers** in the Azure portal.
