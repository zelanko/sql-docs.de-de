---
title: Servertrigger-Rekursion (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: f1fc67db5d7d62c9257f6d66359b0166b6ed8c0b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62808881"
---
# <a name="server-trigger-recursion-server-configuration-option"></a>Servertrigger-Rekursion (Serverkonfigurationsoption)
  Mithilfe der Option **server trigger recursion** geben Sie an, ob Trigger auf Serverebene rekursiv ausgelöst werden können. Wenn diese Option auf 1 (ON) festgelegt ist, können Trigger auf Serverebene rekursiv ausgelöst werden. Wenn sie auf 0 (OFF) festgelegt ist, können Trigger auf Serverebene nicht rekursiv ausgelöst werden. Nur die direkte Rekursion wird verhindert, wenn die Option server trigger recursion auf 0 (OFF) festgelegt ist. (Um die indirekte Rekursion zu deaktivieren, legen Sie die Option **nested triggers** auf 0 fest). Der Standardwert für diese Option ist 1 (ON). Die Einstellung ist ohne Neustart des Servers sofort wirksam.  
  
 Weitere Informationen finden Sie unter [Erstellen von geschachtelten Triggern](../../relational-databases/triggers/create-nested-triggers.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
