---
title: Servertrigger-Rekursion (Serverkonfigurationsoption) | Microsoft-Dokumentation
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
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dcd67a89ea5605647d6736d9d28a6e070a483c16
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68027623"
---
# <a name="server-trigger-recursion-server-configuration-option"></a>Servertrigger-Rekursion (Serverkonfigurationsoption)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Mithilfe der Option **server trigger recursion** geben Sie an, ob Trigger auf Serverebene rekursiv ausgelöst werden können. Wenn diese Option auf 1 (ON) festgelegt ist, können Trigger auf Serverebene rekursiv ausgelöst werden. Wenn sie auf 0 (OFF) festgelegt ist, können Trigger auf Serverebene nicht rekursiv ausgelöst werden. Nur die direkte Rekursion wird verhindert, wenn die Option server trigger recursion auf 0 (OFF) festgelegt ist. (Um die indirekte Rekursion zu deaktivieren, legen Sie die Option **nested triggers** auf 0 fest). Der Standardwert für diese Option ist 1 (ON). Die Einstellung ist ohne Neustart des Servers sofort wirksam.  
  
 Weitere Informationen finden Sie unter [Erstellen von geschachtelten Triggern](../../relational-databases/triggers/create-nested-triggers.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
