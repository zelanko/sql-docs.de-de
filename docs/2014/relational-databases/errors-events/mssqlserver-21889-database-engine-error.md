---
title: MSSQLSERVER_21889 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21889 (Database Engine error)
ms.assetid: ae199540-7986-4cc2-b782-cd22793236d3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 262b2c795da92b2ef32c6956d9a2deda0e45a39d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62915227"
---
# <a name="mssqlserver21889"></a>MSSQLSERVER_21889
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|21889|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SQLErrorNum21889|  
|Meldungstext|Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz '%s' ist kein Replikationsverleger. Führen Sie `sp_adddistributor` auf der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz '%s' mit dem Verteiler '%s' aus, um die Instanz als Host der Veröffentlichungsdatenbank '%s' zu aktivieren. Stellen Sie sicher, dass Sie die gleiche Anmeldung und das gleiche Kennwort angeben, die für den ursprünglichen Verleger verwendet worden sind.|  
  
## <a name="explanation"></a>Erklärung  
 Um die Verlegerdatenbank hosten zu können, muss die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ein Replikationsverleger sein. `sp_validate_redirected_publisher` ruft `sp_helpdistributor` beim Remoteserver auf, um zu bestimmen, ob der Server Replikationsverleger ist. Dieser Fehler wird zurückgegeben, wenn die Ausführung der gespeicherten Prozedur `sp_helpdistributor` ergibt, dass die Zielinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kein Replikationsverleger ist.  
  
## <a name="user-action"></a>Benutzeraktion  
 Führen Sie `sp_adddistributor` bei der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die als Host der Verlegerdatenbank fungiert hat. Wenn Sie `sp_adddistributor` ausführen, geben Sie den richtigen Verteiler an. Verwenden Sie den gleichen Wert für die *@password* Parameter, die verwendet wird, wenn `sp_adddistributor` anfänglich auf dem Verteiler ausgeführt wurde.  
  
  
