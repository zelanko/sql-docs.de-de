---
title: Ergebnisse von Triggern nicht zulassen (Serverkonfigurationsoption) | Microsoft-Dokumentation
description: Informationen zur Option „disallow results from triggers“ Hier erfahren Sie, wie Probleme in Anwendungen vermieden werden können, die nicht für die Verwendung von Resultsets entwickelt wurden.
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- triggers [SQL Server], result sets
- result sets [SQL Server], triggers
- disallow results from triggers option
ms.assetid: 47149073-307d-47a5-b7d2-66a737d3231d
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 8cbe799b72a88da9785e778cb0688fe3ff1a3f44
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85772526"
---
# <a name="disallow-results-from-triggers-server-configuration-option"></a>Ergebnisse von Triggern nicht zulassen (Serverkonfigurationsoption)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Verwenden Sie die Option **Ergebnisse von Triggern nicht zulassen** , um zu steuern, ob Trigger Resultsets zurückgeben. Durch Trigger, die Resultsets zurückgeben, kann es in Anwendungen, die hierfür nicht konzipiert wurden, zu unerwartetem Verhalten kommen.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Diesen Wert sollten Sie auf 1 festlegen.  
  
 1 bedeutet, dass die Option **Ergebnisse von Triggern nicht zulassen** auf ON festgelegt ist. Die Standardeinstellung für diese Option ist 0 (OFF). Wenn diese Option auf 1 (ON) festgelegt ist, können Trigger keine Resultsets zurückgeben, und es wird folgende Fehlermeldung ausgegeben:  
  
 "Meldung 524, Ebene 16, Status 1, Prozedur \<Procedure Name>, Zeile \<Line#>  
  
 "Ein Trigger hat ein Resultset zurückgegeben, und die disallow_results_from_triggers-Serveroption ist TRUE".  
  
 Die Option **Ergebnisse von Triggern nicht zulassen** wird auf der Instanzebene von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] angewendet und bestimmt das Verhalten sämtlicher vorhandener Trigger in der Instanz.  
  
 Bei der Option **Ergebnisse von Triggern nicht zulassen** handelt es sich um eine erweiterte Option. Wenn Sie die Einstellung mithilfe der gespeicherten Systemprozedur **sp_configure** ändern, können Sie **Ergebnisse von Triggern nicht zulassen** nur ändern, wenn Erweiterte Optionen anzeigen auf 1 festgelegt ist. Die Einstellung tritt ohne Neustarten des Servers sofort in Kraft.  
  
## <a name="see-also"></a>Weitere Informationen  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
