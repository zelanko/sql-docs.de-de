---
title: SQLServerCallableStatement-Klasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 30710a63-c05d-47d9-9cf9-c087a1c76373
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 637b56c7f64d35501be0efef30e8f2a055b5be4b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67971916"
---
# <a name="sqlservercallablestatement-class"></a>SQLServerCallableStatement-Klasse
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Mit dieser Klasse kann der gespeicherte Prozedurname angegeben werden, der mit Eingabe- und Ausgabeparametern aufgerufen wird. Mit dieser Klasse kann der Rückgabestatus mit der Syntax "? = call( ?, ..)" abgerufen werden.  
  
 **Paket:** com.microsoft.sqlserver.jdbc  
  
 **Implementiert** [ISQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
 **Erweitert** [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final class SQLServerCallableStatement  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Mithilfe von SQLServerCallableStatement kann der gespeicherte Prozedurname angegeben werden, der mit Eingabe- und Ausgabeparametern aufgerufen wird. SQLServerCallableStatement bietet auch die Möglichkeit zum Abrufen des Rückgabestatus Werts mit der `? = call( ?, ..)` -Syntax.  
  
 Diese Klasse unterstützt das Entpacken in die SQLServerCallableStatement-Klasse, die isqlservercallablestatement-Schnittstelle, die Java. SQL. CallableStatement-Schnittstelle sowie die Klassen und Schnittstellen, die von SQLServerPreparedStatement zum Entpacken unterstützt werden. Weitere Informationen finden Sie unter [Wrapper und Schnittstellen](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
 Wenn eine der SQLServerCallableStatement-Set-Methoden für einen Typ aufgerufen wird, wird der von der letzten SQLServerCallableStatement-Set-Methode angegebene Typ verwendet, wenn dieser Typ mit dem mit [registerOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)angegebenen Typ in Konflikt steht. Dies kann jedoch zu Konvertierungsfehlern aufgrund von inkompatiblen Datentypen führen. Wird keine SQLServerCallableStatement-Set-Methode aufgerufen, wird der Typ verwendet, der mit dem ersten [registerOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)-Aufruf angegeben wird.  
  
 Der JDBC-Treiber 3.0 für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] folgt der Empfehlung für JDBC 4.0, die besagt, dass ein Resultset und die Anzahl von Updates abgerufen werden müssen, bevor OUT-Parameter abgerufen werden können. Sollten OUT-Parameter vor Abschluss der Verarbeitung des Resultsets und der Updatezählungen abgerufen werden, gehen alle noch nicht verarbeiteten Resultsets und Updatezählungen verloren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [API-Referenz für den JDBC-Treiber](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
