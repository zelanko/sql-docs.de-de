---
title: SetNString-Methode (Int, java.lang.String) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b7da6d44-f5b1-44f8-95f5-40179968b1b0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cef8c88654cf29f9a860a30fc3b79ef6d5124ce4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47650018"
---
# <a name="setnstring-method-int-javalangstring"></a>setNString-Methode (int, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den angegebenen Parameter auf das angegebene **Zeichenfolgenobjekt** fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final void setNString(int parameterIndex,  
                                                  java.lang.String value)  
```  
  
#### <a name="parameters"></a>Parameter  
 *parameterIndex*  
  
 Ein Wert vom Typ **int** zum Angeben des Parameterindexes.  
  
 *value*  
  
 Ein **Zeichenfolgenobjekt**, das den Parameterwert enthält.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese Methode sollte verwendet werden, für die **NCHAR**, **NVARCHAR**, **NTEXT**, und **XML** -Datentypen.  
  
 Diese setNString-Methode wird von der setNString-Methode in der java.sql.PreparedStatement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerPreparedStatement-Elemente](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
