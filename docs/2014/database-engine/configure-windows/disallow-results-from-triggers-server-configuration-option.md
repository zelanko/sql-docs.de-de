---
title: Ergebnisse von Triggern nicht zulassen (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- triggers [SQL Server], result sets
- result sets [SQL Server], triggers
- disallow results from triggers option
ms.assetid: 47149073-307d-47a5-b7d2-66a737d3231d
caps.latest.revision: 28
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 482b544aa5609578d6310dfee849b404d31e1ac3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046725"
---
# <a name="disallow-results-from-triggers-server-configuration-option"></a>Ergebnisse von Triggern nicht zulassen (Serverkonfigurationsoption)
  Verwenden Sie die Option **Ergebnisse von Triggern nicht zulassen** , um zu steuern, ob Trigger Resultsets zurückgeben. Durch Trigger, die Resultsets zurückgeben, kann es in Anwendungen, die hierfür nicht konzipiert wurden, zu unerwartetem Verhalten kommen.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Diesen Wert sollten Sie auf 1 festlegen.  
  
 1 bedeutet, dass die Option **Ergebnisse von Triggern nicht zulassen** auf ON festgelegt ist. Die Standardeinstellung für diese Option ist 0 (OFF). Wenn diese Option auf 1 (ON) festgelegt ist, können Trigger keine Resultsets zurückgeben, und es wird folgende Fehlermeldung ausgegeben:  
  
 "Meldung '524', Ebene '16', Status '1', Prozedur '\<Prozedurname>', Zeile \<Zeilennummer>"  
  
 "Ein Trigger hat ein Resultset zurückgegeben, und die disallow_results_from_triggers-Serveroption ist TRUE".  
  
 Die Option **Ergebnisse von Triggern nicht zulassen** wird auf der Instanzebene von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] angewendet und bestimmt das Verhalten sämtlicher vorhandener Trigger in der Instanz.  
  
 Bei der Option **Ergebnisse von Triggern nicht zulassen** handelt es sich um eine erweiterte Option. Wenn Sie die Einstellung mithilfe der gespeicherten Systemprozedur **sp_configure** ändern, können Sie **Ergebnisse von Triggern nicht zulassen** nur ändern, wenn Erweiterte Optionen anzeigen auf 1 festgelegt ist. Die Einstellung tritt ohne Neustarten des Servers sofort in Kraft.  
  
## <a name="see-also"></a>Siehe auch  
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
