---
title: SetObject-Methode (Int, java.lang.Object) | Microsoft-Dokumentation
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
ms.openlocfilehash: cac0013c8867bce46dc9fd8ebbae9d0b0c487259
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42785314"
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
 *Index*  
  
 Ein Wert **ganzzahliger** Wert zum Angeben der Parameternummer.  
  
 *obj*  
  
 Ein Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese SetObject-Methode wird von der SetObject-Methode in der java.sql.PreparedStatement-Schnittstelle angegeben.  
  
 Vor dem Abrufen der setObject-Methode kann der angegebene Parameter von der Anwendung mit einer der folgenden Methoden festgelegt werden:  
  
-   Die set\<Type>-Methoden der SQLServerPreparedStatement-Klasse oder der SQLServerCallableStatement-Klasse  
  
-   Die setNull-Methoden der SQLServerPreparedStatement-Klasse oder der SQLServerCallableStatement-Klasse  
  
-   Die [RegisterOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) Methode der SQLServerCallableStatement-Klasse  
  
 In diesem Fall wird der Parametertyp automatisch festgelegt. Wird die setObject-Methode von der Anwendung mit NULL für den Objektwert aufgerufen, wird vom Treiber angenommen, dass der Parametertyp von der zuvor aufgerufenen Methode festgelegt wird.  
  
 Ist der obj-Wert NULL und können für diesen Parameter keine Typinformationen ermittelt werden, wird der angegebene Parameter vor dem Senden an die Datenbank von der setObject-Methode in einen CHAR-Wert konvertiert.  
  
 Beginnend mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0, das Verhalten dieser Methode wird geändert, indem die **SendTimeAsDatetime** Connection-Eigenschaft ([Festlegen der Verbindungseigenschaften](../../../connect/jdbc/setting-the-connection-properties.md)) und [ SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 Weitere Informationen finden Sie unter [Configuring How java.sql.Time Values are Sent to the Server (Konfigurieren der Art und Weise, wie java.sql.Time-Werte an den Server gesendet werden)](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [setObject-Methode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement-Elemente](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement-Klasse](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
