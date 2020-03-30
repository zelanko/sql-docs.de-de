---
title: Replikation über das Internet | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Web publishing [SQL Server replication], about Web publishing
- Web publishing [SQL Server replication]
- Internet [SQL Server replication]
- Internet [SQL Server replication], publishing
ms.assetid: 04e7f4ed-e244-4bbe-ba12-09c33abea09e
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: d7dd25b2b1cd2aa0cc8560072702bc8188191d09
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "76287384"
---
# <a name="replication-over-the-internet"></a>Replikation über das Internet
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Das Replizieren von Daten über das Internet ermöglicht Remotebenutzern sowie Benutzern, die nicht mit dem Netzwerk verbunden sind, bei Bedarf auf Daten mithilfe einer Verbindung zum Internet zuzugreifen. Verwenden Sie Folgendes, um Daten über das Internet zu replizieren:  
  
-   Ein Virtuelles Privates Netzwerk (VPN). Weitere Informationen finden Sie unter [Veröffentlichen von Daten über das Internet mithilfe von VPN](../../relational-databases/replication/publish-data-over-the-internet-using-vpn.md).  
  
-   Die Websynchronisierungsoption für die Mergereplikation. Weitere Informationen finden Sie unter [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md).  
  
 Bei allen Arten der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Replikation können Daten über ein VPN repliziert werden. Falls Sie eine Mergereplikation verwenden, sollten Sie jedoch die Websynchronisierung in Betracht ziehen.  
  
  
