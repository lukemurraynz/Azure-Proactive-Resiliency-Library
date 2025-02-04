+++
title = "ExpressRoute Gateway"
description = "Best practices and resiliency recommendations for ExpressRoute Gateway and associated resources."
date = "4/18/23"
author = "ehaslett"
msAuthor = "ethaslet"
draft = false
+++

The presented resiliency recommendations in this guidance include ExpressRoute Gateway and associated ExpressRoute Gateway settings.

## Summary of Recommendations

The below table shows the list of resiliency recommendations for ExpressRoute Gateway and associated resources.

{{< table style="table-striped" >}}
| Recommendation | State | ARG Query Available |
| :------------------------------------------------ | :------: | :-----------------: |
| [EXRGW-1 - Use Zone-redundant gateway SKUs](#exrgw-1---use-zone-redundant-gateway-skus) | Preview | Yes |
| [EXRGW-2 - Monitor gateway health](#exrgw-2---monitor-gateway-health) | Preview | TBD |
| [EXRGW-3 - Use VNET peering for VNET to VNET connectivity](#exrgw-3---use-vnet-peering-for-vnet-to-vnet-connectivity) | Preview | TBD |
| [EXRGW-4 - Configure ExpressRoute Gateways in different regions](#exrgw-4---configure-expressroute-gateways-in-different-regions) | Preview | TBD |
| [EXRGW-5 - Configure S2S VPN as a backup to ExpressRoute private peering](#exrgw-5---configure-s2s-vpn-as-a-backup-to-expressroute-private-peering) | Preview | TBD |
{{< /table >}}

{{< alert style="info" >}}

Definitions of states can be found [here]({{< ref "../../../_index.md#definitions-of-terms-used-in-aprl">}})

{{< /alert >}}

## Recommendations Details

### EXRGW-1 - Use Zone-redundant gateway SKUs

#### Importance: Critical

#### Recommendation/Guidance

Azure ExpressRoute gateway provides different SLAs when it’s deployed in a single availability zone and when it’s deployed in two or more availability zones. For information about all Azure SLAs, see SLA summary for Azure services. To automatically deploy your virtual network gateways across availability zones, you can use zone-redundant virtual network gateways. With zone-redundant gateways, you can benefit from zone-resiliency to access your mission-critical, scalable services on Azure

##### Resources

- [About ExpressRoute virtual network gateways - Zone-redundant gateway SKUs](https://learn.microsoft.com/en-us/azure/expressroute/expressroute-about-virtual-network-gateways#zrgw)
- [About zone-redundant virtual network gateway in Azure availability zones](https://learn.microsoft.com/en-us/azure/vpn-gateway/about-zone-redundant-vnet-gateways)
- [Create a zone-redundant virtual network gateway in Azure Availability Zones](https://learn.microsoft.com/en-us/azure/vpn-gateway/create-zone-redundant-vnet-gateway)

#### Queries/Scripts

##### Azure Resource Graph

{{< collapse title="Show/Hide Query/Script" >}}

{{< code lang="sql" file="code/exrgw-1/exrgw-1.kql" >}} {{< /code >}}

{{< /collapse >}}

<br><br>

### EXRGW-2 - Monitor gateway health

#### Importance: High

#### Recommendation/Guidance

Set up monitoring and alerts for Virtual Network Gateway health based on various metrics available.

##### Resources

- [Alerts for ExpressRoute gateway connections](https://learn.microsoft.com/en-us/azure/expressroute/monitor-expressroute#alerts-for-expressroute-gateway-connections)
- [Gateway Metrics](https://learn.microsoft.com/en-us/azure/expressroute/expressroute-network-insights#gateway-metrics)

#### Queries/Scripts

##### Azure Resource Graph

{{< collapse title="Show/Hide Query/Script" >}}

{{< code lang="sql" file="code/exrgw-2/exrgw-2.kql" >}} {{< /code >}}

{{< /collapse >}}

<br><br>

### EXRGW-3 - Use VNET peering for VNET to VNET connectivity

#### Importance: Medium

#### Recommendation/Guidance

By default, connectivity between virtual networks are enabled when you link multiple virtual networks to the same ExpressRoute circuit. However, Microsoft advises against using your ExpressRoute circuit for communication between virtual networks and instead uses VNet peering. For more information about why VNet-to-VNet connectivity isn't recommended over ExpressRoute, see connectivity between virtual networks over ExpressRoute.

##### Resources

- [About ExpressRoute virtual network gateways - VNet-to-VNet connectivity](https://learn.microsoft.com/en-us/azure/expressroute/expressroute-about-virtual-network-gateways#vnet-to-vnet-connectivity)

#### Queries/Scripts

##### Azure Resource Graph

{{< collapse title="Show/Hide Query/Script" >}}

{{< code lang="sql" file="code/exrgw-3/exrgw-3.kql" >}} {{< /code >}}

{{< /collapse >}}

<br><br>

### EXRGW-4 - Configure ExpressRoute Gateways in different regions

#### Importance: Medium

#### Recommendation/Guidance

When multiple Azure regions are in use, increase resilience by configuring ExpressRoute gateways in each region, along with corresponding ExpressRoute circuits.

##### Resources

- [Designing for disaster recovery with ExpressRoute private peering - Need for redundant connectivity solution](https://learn.microsoft.com/en-us/azure/expressroute/designing-for-disaster-recovery-with-expressroute-privatepeering#need-for-redundant-connectivity-solution)

#### Queries/Scripts

##### Azure Resource Graph

{{< collapse title="Show/Hide Query/Script" >}}

{{< code lang="sql" file="code/exrgw-4/exrgw-4.kql" >}} {{< /code >}}

{{< /collapse >}}

<br><br>

### EXRGW-5 - Configure S2S VPN as a backup to ExpressRoute private peering

#### Importance: Medium

#### Recommendation/Guidance

Consider using site-to-site VPN as a failover when an ExpressRoute circuit becomes unavailable.

##### Resources

- [Using S2S VPN as a backup for ExpressRoute private peering](https://learn.microsoft.com/en-us/azure/expressroute/use-s2s-vpn-as-backup-for-expressroute-privatepeering)

#### Queries/Scripts

##### Azure Resource Graph

{{< collapse title="Show/Hide Query/Script" >}}

{{< code lang="sql" file="code/exrgw-5/exrgw-5.kql" >}} {{< /code >}}

{{< /collapse >}}

<br><br>
