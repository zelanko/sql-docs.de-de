---
title: Verwalten von Big Data-Clustern (BDC) in einem privaten Azure Kubernetes Service-Cluster (AKS-Cluster)
titleSuffix: SQL Server Big Data Cluster
description: Erfahren Sie, wie Sie Big Data-Cluster in SQL Server in einem privaten Azure Kubernetes Service-Cluster (AKS-Cluster) verwalten.
author: cloudmelon
ms.author: melqin
ms.reviewer: mikeray
ms.date: 08/20/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 442f5def7e1378b750460cfc6860e780b1dcfd80
ms.sourcegitcommit: fe5dedb2a43516450696b754e6fafac9f5fdf3cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2020
ms.locfileid: "89202233"
---
# <a name="manage-big-data-cluster-in-aks-private-cluster"></a>Verwalten von Big Data-Clustern in einem privaten AKS-Cluster

In diesem Artikel wird erläutert, wie ein in Azure bereitgestellter privater Azure Kubernetes Service-Cluster (AKS-Cluster) mit Big Data Clustern (BDC) in SQL Server verwaltet wird.

Wie unter [Erstellen eines privaten Clusters](/azure/aks/private-clusters/) beschrieben, verfügt der API-Serverendpunkt des privaten AKS-Clusters nicht über eine öffentliche IP-Adresse. Verwenden Sie zum Verwalten des API-Servers einen virtuellen Computer, der Zugriff auf das Azure Virtual Network (VNet) des AKS-Clusters hat.

## <a name="azure-vm---same-vnet"></a>Azure-VM im selben VNet

Die einfachste Methode besteht darin, einen virtuellen Azure-Computer in dem VNet bereitzustellen, in dem sich auch der AKS-Cluster befindet.

1. Stellen Sie einen virtuellen Azure-Computer in dem VNet bereit, in dem sich auch Ihr AKS-Cluster befindet. Dies wird manchmal als *Jumpbox* bezeichnet.
1. Stellen Sie eine Verbindung mit diesem virtuellen Computer her, und [installieren Sie Big Data-Tools für SQL Server 2019](deployment-guidance.md#install-sql-server-2019-big-data-tools).

Aus Sicherheitsgründen können Sie AKS-Features für die autorisierten IP-Adressbereiche des API-Servers verwenden, um den Zugriff auf den API-Server (auf der AKS-Steuerungsebene) einzuschränken. Der eingeschränkte Zugriff lässt bestimmte IP-Adressen wie einen virtuellen Jumpbox-Computer oder eine Verwaltungs-VM oder einen IP-Adressbereich für eine Gruppe von Entwicklern und die öffentliche Front-End-IP-Adresse der Firewall zu.

## <a name="other-options"></a>Weitere Optionen

Mögliche Alternativen zur Verwendung einer Jumpbox:

* Verwenden Sie einen virtuellen Computer in einem separaten Netzwerk, und richten Sie ein [Peering virtueller Netzwerke](/azure/virtual-network/virtual-network-peering-overview) für das VNet ein.

* Eine [Azure ExpressRoute](/azure/expressroute/expressroute-introduction)- oder [VPN Gateway](/azure/vpn-gateway/vpn-gateway-about-vpngateways)-Verbindung.

   Unter [Optionen zum Herstellen einer Verbindung mit dem privaten Cluster](/azure/aks/private-clusters#options-for-connecting-to-the-private-cluster) werden die oben genannten Methoden erläutert.

* Wenn Ihr Dienst hinter einer [Instanz von Azure Load Balancer Standard](/azure/aks/load-balancer-standard) ausgeführt wird, kann er für [Azure Private Link](/azure/private-link/private-link-service-overview#limitations) aktiviert werden. Mit Azure Private Link können Sie den privaten Zugriff über andere Azure-VNets aktivieren.

* In Hybridszenarien können Sie auch eine [Azure ExpressRoute](/azure/expressroute/expressroute-introduction)- oder [VPN Gateway](/azure/vpn-gateway/vpn-gateway-about-vpngateways)-Verbindung einrichten.

## <a name="next-steps"></a>Nächste Schritte

[Herstellen einer Verbindung mit einem Big-Data-Cluster für SQL Server mit Azure Data Studio](connect-to-big-data-cluster.md)