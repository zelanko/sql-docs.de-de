---
title: Servertrigger-Rekursion (Serverkonfigurationsoption) | Microsoft-Dokumentation
description: Informationen zu den Auswirkungen der Option „server trigger recursion“ auf die Rekursion in SQL Server-Triggern auf Serverebene So aktivieren oder deaktivieren Sie die direkte und indirekte Rekursion.
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- recursive triggers [SQL Server]
- triggers [SQL Server], recursive
- server trigger recursion option
ms.assetid: da4c25f5-d04c-4951-a3db-409e71a1b468
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 7dc2dcd132ef32ba4f026a1a9b76d4e67df28b26
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715563"
---
# <a name="server-trigger-recursion-server-configuration-option"></a>Servertrigger-Rekursion (Serverkonfigurationsoption)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Mithilfe der Option **server trigger recursion** geben Sie an, ob Trigger auf Serverebene rekursiv ausgelöst werden können. Wenn diese Option auf 1 (ON) festgelegt ist, können Trigger auf Serverebene rekursiv ausgelöst werden. Wenn sie auf 0 (OFF) festgelegt ist, können Trigger auf Serverebene nicht rekursiv ausgelöst werden. Nur die direkte Rekursion wird verhindert, wenn die Option server trigger recursion auf 0 (OFF) festgelegt ist. (Um die indirekte Rekursion zu deaktivieren, legen Sie die Option **nested triggers** auf 0 fest). Der Standardwert für diese Option ist 1 (ON). Die Einstellung ist ohne Neustart des Servers sofort wirksam.  
  
 Weitere Informationen finden Sie unter [Erstellen von geschachtelten Triggern](../../relational-databases/triggers/create-nested-triggers.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
