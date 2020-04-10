---
title: setBytes-Methode (SQLServerCallableStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setBytes
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f264f1a6-ee35-4eaf-81d8-ecf99f03b35d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4cb75f7d7e0ed77872e384d6e981a8fe8cae4410
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80929161"
---
# <a name="setbytes-method-sqlservercallablestatement"></a>setBytes-Methode (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den angegebenen Parameter auf das angegebene Array aus **byte**-Werten fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setBytes(java.lang.String sCol,  
                     byte[] b)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sCol*  
  
 Ein **String-Objekt**, das den Parameternamen enthält.  
  
 *b*  
  
 Ein Array von **byte**-Werten  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 In einer früheren Version des Treibers konnten Sie mithilfe von „SQLServerCallableStatement.setBytes“ Werte zwischen Bytearrays und dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentyp **date**, **time**, **datetime2** oder **datetimeoffset** konvertieren. Nun wird durch Verwendung der Methode mit diesen Datentypen eine Ausnahme ausgelöst, die angibt, dass die Konvertierung nicht unterstützt wird.  
  
 Diese setBytes-Methode wird von der setBytes-Methode in der java.sql.CallableStatement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
