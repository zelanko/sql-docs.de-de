---
title: GetString-Methode (java.lang.String) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getString (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f67371e0-e879-4188-85fc-ecb85f0be2a9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 208fbad8a728775c8e8d985a6f7f28c7facc865f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47773492"
---
# <a name="getstring-method-javalangstring"></a>getString-Methode (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Wert des angegebenen Parameters unter Berücksichtigung des Parameternamens als **String-Objekt** in der Programmiersprache Java ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.String getString(java.lang.String sCol)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sCol*  
  
 Ein **String-Objekt**, das den Parameternamen enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **String-Wert**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese getString-Methode wird von der getString-Methode in der java.sql.CallableStatement-Schnittstelle angegeben.  
  
 Alle Spalten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] können als Zeichenfolge zurückgegeben werden. Es können also eine Zeichenfolgendarstellung aller zahlen- und zeichenfolgenbasierten Typen und eine hexadezimale Zeichenfolgendarstellung binärer Spalten wie "binary", "varbinary", "varbinary(max)", "image", "timestamp" oder "uniqueidentifier" zurückgegeben werden.  
  
 Den Speicherort berücksichtigende Typen wie „money“, „smallmoney“, „datetime“, „smalldatetime“, „float“, „real“, „decimal“ oder „numeric“ geben für den zugrunde liegenden Wert des Typs das kanonische toString()-Format zurück.  
  
 Benutzerdefinierte Typen werden als hexadezimale Zeichenfolgenwerte zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [getString-Methode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getstring-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
