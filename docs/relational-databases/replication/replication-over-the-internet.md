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
manager: craigg
ms.openlocfilehash: 03ed843cff2160562c6512c875762b4b20d877d9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47777910"
---
# <a name="replication-over-the-internet"></a>Replikation über das Internet
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Das Replizieren von Daten über das Internet ermöglicht Remotebenutzern sowie Benutzern, die nicht mit dem Netzwerk verbunden sind, bei Bedarf auf Daten mithilfe einer Verbindung zum Internet zuzugreifen. Verwenden Sie Folgendes, um Daten über das Internet zu replizieren:  
  
-   Ein Virtuelles Privates Netzwerk (VPN). Weitere Informationen finden Sie unter [Veröffentlichen von Daten über das Internet mithilfe von VPN](../../relational-databases/replication/publish-data-over-the-internet-using-vpn.md).  
  
-   Die Websynchronisierungsoption für die Mergereplikation. Weitere Informationen finden Sie unter [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md).  
  
 Bei allen Typen der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Replikation können Daten über ein VPN repliziert werden. Sie sollten jedoch die Websynchronisierung in Betracht ziehen, falls Sie die Mergereplikation verwenden.  
  
  
