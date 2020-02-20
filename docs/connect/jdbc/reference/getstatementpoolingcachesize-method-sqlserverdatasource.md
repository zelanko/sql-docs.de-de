---
title: getStatementPoolingCacheSize-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a90d00957310c64f908816198a47e4c3ba7293b9
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67979512"
---
# <a name="getstatementpoolingcachesize-method-sqlserverdatasource"></a>getStatementPoolingCacheSize-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Diese Methode gibt den Wert der Verbindungseigenschaft **statementPoolingCacheSize** zurück. Sie gibt die Größe des Prepared Statement-Caches für diese Verbindung zurück. 0 (null) bedeutet, dass das Zwischenspeichern nicht aktiviert ist.
  
## <a name="syntax"></a>Syntax  
  
```
public boolean getStatementPoolingCacheSize();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Dies ist der Wert **int** der Verbindungseigenschaft **statementPoolingCacheSize**.  

## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Bemerkungen  
 Diese Methode ist über Version 6.4 und höher des JDCB-Treibers verfügbar.
 
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
