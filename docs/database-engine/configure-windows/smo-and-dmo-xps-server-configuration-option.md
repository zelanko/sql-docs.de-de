---
title: SMO and DMO XPs (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: bcd945ba-5d81-4124-9a2b-d87491c2a369
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: 7c0f82a57cdbc9117e28e03b65a070055831ef13
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66775577"
---
# <a name="smo-and-dmo-xps-server-configuration-option"></a>SMO and DMO XPs (Serverkonfigurationsoption)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Verwenden Sie die Option SMO and DMO XPs, um erweiterte gespeicherte Prozeduren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object (SMO) auf diesem Server zu aktivieren.  
  
 Beachten Sie, dass DMO beginnend mit [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]entfernt wurde.  
  
 Eine Beschreibung der möglichen Werte finden Sie in der folgenden Tabelle:  
  
|value|Bedeutung|  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Programmierungshandbuch für SQL Server Management Objects &#40;SMO&#41;](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
  
