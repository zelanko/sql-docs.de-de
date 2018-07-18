---
title: Max. Bereich für Volltextdurchforstung (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- crawls [full-text search]
- max full-text crawl range option
ms.assetid: a49de86b-0891-4dcd-89c0-ead30aab00e0
caps.latest.revision: 24
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a58c55376176e44e73974fb867e44fddf36246a9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32863575"
---
# <a name="max-full-text-crawl-range-server-configuration-option"></a>Max. Bereich für Volltextdurchforstung (Serverkonfigurationsoption)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Verwenden Sie die Option **max full-text crawl range** , um die CPU-Auslastung zu optimieren. Hierdurch wird die Durchforstungsleistung während eines vollständigen Durchforstungsvorgangs verbessert. Mithilfe dieser Option können Sie die Anzahl von Partitionen angeben, die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] während eines vollständigen Indexdurchforstungsvorgangs verwenden sollte. Wenn z. B. viele CPUs vorhanden sind und ihre Auslastung nicht optimal ist, können Sie den maximalen Wert dieser Option erhöhen. Zusätzlich zu dieser Option verwendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Reihe anderer Faktoren, wie z. B. die Anzahl von Zeilen in der Tabelle und die Anzahl von CPUs, um die tatsächliche Anzahl von verwendeten Partitionen zu ermitteln.  
  
 Der Standardwert dieser Option ist 4, der Mindestwert 1 und der maximale Wert 256. Änderungen an dieser Option beeinflussen nur nachfolgende Crawls. Auf in Verarbeitung befindliche Durchforstungsvorgänge hat eine Änderung dieser Optionseinstellung keine Auswirkungen.  
  
 Bei der Option **max full-text crawl range** handelt es sich um eine erweiterte Option. Wenn Sie die Einstellung mithilfe der gespeicherten Systemprozedur **sp_configure** ändern, können Sie **max full-text crawl range** nur ändern, wenn **Erweiterte Optionen anzeigen** auf 1 festgelegt ist. Die Einstellung tritt ohne Neustarten des Servers sofort in Kraft.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
