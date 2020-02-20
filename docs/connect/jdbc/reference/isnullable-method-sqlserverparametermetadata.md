---
title: isNullable-Methode (SQLServerParameterMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerParameterMetaData.sNullable
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d7e07cff-6fc4-4c9c-8e8f-838c77734bc5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f340a182da1cd232aab70e61c268ba6ec58633db
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67977535"
---
# <a name="isnullable-method-sqlserverparametermetadata"></a>isNullable-Methode (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob im angegebenen Parameter NULL-Werte zulässig sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int isNullable(int param)  
```  
  
#### <a name="parameters"></a>Parameter  
 *param*  
  
 Ein Wert vom Typ **int** zum Angeben des Parameterindexes.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **int** zum Angeben der NULL-Zulässigkeit des angegebenen Parameters. Mögliche Werte:  
  
 ParameterMetaData.parameterNoNulls  
  
 ParameterMetaData.parameterNullable  
  
 ParameterMetaData.parameterNullabilityUnknown  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese isNullable-Methode wird von der isNullable-Methode in der java.sql.ParameterMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerParameterMetaData-Methoden](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [SQLServerParameterMetaData-Elemente](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [SQLServerParameterMetaData-Klasse](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
