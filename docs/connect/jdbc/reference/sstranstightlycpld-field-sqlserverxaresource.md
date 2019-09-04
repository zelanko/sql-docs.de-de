---
title: SSTRANSTIGHTLYCPLD-Feld (sqlserverxaresource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SSTRANSTIGHTLYCPLD Field (SQLServerXAResource)
apilocation:
- SSTRANSTIGHTLYCPLD Field (SQLServerXAResource)
apitype: Assembly
ms.assetid: 379857c3-9de1-4964-8782-32df317cbfbb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 36563b76c4207b5924bb32f5c8e99cca575c9d72
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67970042"
---
# <a name="sstranstightlycpld-field-sqlserverxaresource"></a>SSTRANSTIGHTLYCPLD-Feld (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Hierdurch werden eng verkoppelte XA-Transaktionen ermöglicht, die unterschiedliche XA-Verzweigungstransaktions-IDs (XIDs) aber dieselbe globale Transaktions-ID (GTRID) aufweisen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public static final int SSTRANSTIGHTLYCPLD  
```  
  
## <a name="field-value"></a>Feldwert  
 Ein **int** -Wert von 32768.  
  
## <a name="remarks"></a>Bemerkungen  
 Jede Transaktion wird anhand einer XA-Verzweigungstransaktions-ID (XID) und einer globalen Transaktions-ID (GTRID) identifiziert. Damit von den Anwendungen eng verkoppelte XA-Transaktionen mit unterschiedlichen XIDs aber den gleichen GTRIDs verwendet werden können, muss [SSTRANSTIGHTLYCPLD](../../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md) für den flags-Parameter der XAResource.start-Methode festgelegt werden. Weitere Informationen zur Verwendung dieses Flags finden Sie Untergrund Legendes zu [XA-Transaktionen](../../../connect/jdbc/understanding-xa-transactions.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerXAResource-Felder](../../../connect/jdbc/reference/sqlserverxaresource-fields.md)   
 [SQLServerXAResource-Elemente](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource-Klasse](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
