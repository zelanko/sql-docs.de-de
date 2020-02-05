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
ms.openlocfilehash: a0c867d9acba6542d90f72595fa0f71ab6d62e64
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "68026052"
---
# <a name="smo-and-dmo-xps-server-configuration-option"></a>SMO and DMO XPs (Serverkonfigurationsoption)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Verwenden Sie die Option SMO and DMO XPs, um erweiterte gespeicherte Prozeduren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object (SMO) auf diesem Server zu aktivieren.  
  
 Beachten Sie, dass DMO beginnend mit [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]entfernt wurde.  
  
 Eine Beschreibung der möglichen Werte finden Sie in der folgenden Tabelle:  
  
|value|Bedeutung|  
|-----------|-------------|  
|0|SMO-XPs sind nicht verfügbar.|  
|1|SMO-XPS sind verfügbar. Dies ist die Standardoption.|  
  
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
  
  
