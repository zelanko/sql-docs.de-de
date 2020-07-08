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
ms.openlocfilehash: c5a1244ed340dcfd4794c14635d570530b88f5d9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85716730"
---
# <a name="replication-over-the-internet"></a>Replikation über das Internet
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  Das Replizieren von Daten über das Internet ermöglicht Remotebenutzern sowie Benutzern, die nicht mit dem Netzwerk verbunden sind, bei Bedarf auf Daten mithilfe einer Verbindung zum Internet zuzugreifen. Verwenden Sie Folgendes, um Daten über das Internet zu replizieren:  
  
-   Ein Virtuelles Privates Netzwerk (VPN). Weitere Informationen finden Sie unter [Veröffentlichen von Daten über das Internet mithilfe von VPN](../../relational-databases/replication/publish-data-over-the-internet-using-vpn.md).  
  
-   Die Websynchronisierungsoption für die Mergereplikation. Weitere Informationen finden Sie unter [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md).  
  
 Bei allen Arten der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Replikation können Daten über ein VPN repliziert werden. Falls Sie eine Mergereplikation verwenden, sollten Sie jedoch die Websynchronisierung in Betracht ziehen.  
  
  
