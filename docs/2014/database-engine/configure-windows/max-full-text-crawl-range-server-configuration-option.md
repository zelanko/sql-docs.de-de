---
title: Max. Bereich für Volltextdurchforstung (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- crawls [full-text search]
- max full-text crawl range option
ms.assetid: a49de86b-0891-4dcd-89c0-ead30aab00e0
caps.latest.revision: 23
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: a5a1903dfab71b78923a7747cf7a947d83e023e3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36061455"
---
# <a name="max-full-text-crawl-range-server-configuration-option"></a>Max. Bereich für Volltextdurchforstung (Serverkonfigurationsoption)
  Verwenden Sie die Option **max full-text crawl range** , um die CPU-Auslastung zu optimieren. Hierdurch wird die Durchforstungsleistung während eines vollständigen Durchforstungsvorgangs verbessert. Mithilfe dieser Option können Sie die Anzahl von Partitionen angeben, die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] während eines vollständigen Indexdurchforstungsvorgangs verwenden sollte. Wenn z. B. viele CPUs vorhanden sind und ihre Auslastung nicht optimal ist, können Sie den maximalen Wert dieser Option erhöhen. Zusätzlich zu dieser Option verwendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Reihe anderer Faktoren, wie z. B. die Anzahl von Zeilen in der Tabelle und die Anzahl von CPUs, um die tatsächliche Anzahl von verwendeten Partitionen zu ermitteln.  
  
 Der Standardwert dieser Option ist 4, der Mindestwert 1 und der maximale Wert 256. Änderungen an dieser Option beeinflussen nur nachfolgende Crawls. Auf in Verarbeitung befindliche Durchforstungsvorgänge hat eine Änderung dieser Optionseinstellung keine Auswirkungen.  
  
 Bei der Option **max full-text crawl range** handelt es sich um eine erweiterte Option. Wenn Sie die Einstellung mithilfe der gespeicherten Systemprozedur **sp_configure** ändern, können Sie **max full-text crawl range** nur ändern, wenn **Erweiterte Optionen anzeigen** auf 1 festgelegt ist. Die Einstellung tritt ohne Neustarten des Servers sofort in Kraft.  
  
## <a name="see-also"></a>Siehe auch  
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
