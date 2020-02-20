---
title: getScale-Methode (SQLServerParameterMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerParameterMetaData.getScale
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7b8d8d9c-74aa-4e6e-88f1-2fc5c74004ae
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 29c2da8d8b6645ec9d5186f79db80b03626b2978
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67980207"
---
# <a name="getscale-method-sqlserverparametermetadata"></a>getScale-Methode (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft für den angegebenen Parameter die Anzahl von Stellen hinter dem Dezimalzeichen ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int getScale(int param)  
```  
  
#### <a name="parameters"></a>Parameter  
 *param*  
  
 Ein Wert vom Typ **int** zum Angeben des Parameterindexes.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **int**, der die Dezimalstellen des angegebenen Parameters angibt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getScale-Methode wird von der getScale-Methode in der java.sql.ParameterMetaData-Schnittstelle angegeben.  
  
 Von dieser Methode werden Spaltendezimalstellen abgerufen. Bei Typen ohne Dezimalzeichen wird "0" zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerParameterMetaData-Methoden](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [SQLServerParameterMetaData-Elemente](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [SQLServerParameterMetaData-Klasse](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
