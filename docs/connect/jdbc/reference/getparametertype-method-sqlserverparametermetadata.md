---
title: getParameterType-Methode (SQLServerParameterMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerParameterMetaData.getParameterType
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 638aca05-63e4-4d73-a9c8-e0442f775720
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bd9252827e7c7bec70636937bc89dd5390e68519
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67980952"
---
# <a name="getparametertype-method-sqlserverparametermetadata"></a>getParameterType-Methode (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den SQL-Typ des angegebenen Parameters ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int getParameterType(int param)  
```  
  
#### <a name="parameters"></a>Parameter  
 *param*  
  
 Ein Wert vom Typ **int** zum Angeben des Parameterindexes.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **int**, der den im java.sql.Types-Element definierten JDBC-Typcode angibt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getParameterType-Methode wird von der getParameterType-Methode in der java.sql.ParameterMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerParameterMetaData-Methoden](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [SQLServerParameterMetaData-Elemente](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [SQLServerParameterMetaData-Klasse](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
