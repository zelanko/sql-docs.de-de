---
title: SetObject-Methode (Int, java.lang.Object) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setObject (int, java.lang.Object)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 61f19faa-3006-4a1c-974c-55951e3b3000
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0103dfd14dd8a51263945d0048a7b6c7cb550157
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="setobject-method-int-javalangobject"></a>setObject-Methode (int, java.lang.Object)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den Wert des angegebenen Parameters unter Verwendung des angegebenen Objekts fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final void setObject(int index,  
                            java.lang.Object obj)  
```  
  
#### <a name="parameters"></a>Parameter  
 *index*  
  
 Ein **Int** , der die Parameteranzahl angibt.  
  
 *obj*  
  
 Ein Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Hinweise  
 Diese SetObject-Methode wird von der SetObject-Methode in der java.sql.PreparedStatement-Schnittstelle angegeben.  
  
 Vor dem Aufrufen dieser SetObject-Methode kann die Anwendung den angegebenen Parameter festlegen, mithilfe einer der folgenden Methoden:  
  
-   Der Satz\<Typ >-Methoden der SQLServerPreparedStatement-Klasse oder der SQLServerCallableStatement-Klasse  
  
-   SetNull-Methoden von der SQLServerPreparedStatement-Klasse oder der SQLServerCallableStatement-Klasse  
  
-   Die [RegisterOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) -Methode der SQLServerCallableStatement-Klasse  
  
 In diesem Fall wird der Parametertyp automatisch festgelegt. Wenn die Anwendung diese SetObject-Methode mit einer Objektwert NULL aufgerufen wird, wird der Treiber davon ausgegangen, dass der Typ des Parameters ist, die von der zuvor aufgerufenen Methode festgelegt ist.  
  
 Wenn der Objektwert NULL ist und keine Typinformationen für diesen Parameter bestimmt werden kann, konvertiert diese SetObject-Methode den angegebenen Parameter in einen CHAR vor dem Senden an die Datenbank an.  
  
 Beginnend mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] JDBC Driver 3.0, das Verhalten dieser Methode geändert wird, indem die **SendTimeAsDatetime** Connection-Eigenschaft ([Festlegen der Verbindungseigenschaften](../../../connect/jdbc/setting-the-connection-properties.md)) und [ SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 Weitere Informationen finden Sie unter [konfigurieren wie java.sql.Time-Werte werden an den Server gesendet](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SetObject-Methode &#40;sqlserverpreparedstatement-Klasse&#41;](../../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement-Elemente](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement-Klasse](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
