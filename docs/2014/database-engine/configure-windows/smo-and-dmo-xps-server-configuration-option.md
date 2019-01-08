---
title: SMO and DMO XPs (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: bcd945ba-5d81-4124-9a2b-d87491c2a369
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d55bd667909721a68d51bcd1db7128b809118843
ms.sourcegitcommit: 04dd0620202287869b23cc2fde998a18d3200c66
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "52641391"
---
# <a name="smo-and-dmo-xps-server-configuration-option"></a>SMO and DMO XPs (Serverkonfigurationsoption)
  Verwenden Sie die Option SMO and DMO XPs, um erweiterte gespeicherte Prozeduren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object (SMO) auf diesem Server zu aktivieren.  
  
 Beachten Sie, dass DMO beginnend mit [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]entfernt wurde.  
  
 Eine Beschreibung der möglichen Werte finden Sie in der folgenden Tabelle:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|0|SMO-XPs sind nicht verfügbar.|  
|1|SMO-XPS sind verfügbar. Dies ist die Standardeinstellung.|  
  
 Diese Einstellung wird sofort wirksam.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden die erweiterten gespeicherten Prozeduren von SMO aktiviert.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'SMO and DMO XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Programmierungshandbuch für SQL Server Management Objects &#40;SMO&#41;](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
  
