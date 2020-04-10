---
title: Methode „commit“ (SQLServerConnection) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.commit
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c7346165-51bf-4844-b64c-29833c147236
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 50afbfa25052e0f602c486d011ce666a599372e0
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923587"
---
# <a name="commit-method-sqlserverconnection"></a>commit-Methode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Macht alle Änderungen, die seit dem letzten Commit oder Rollback vorgenommen wurden, zu dauerhaften Änderungen und hebt sämtliche Datenbanksperren auf, die derzeit von diesem [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt aufrecht erhalten werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void commit()  
```  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese commit-Methode wird von der commit-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
 Die Methode sollte nur bei deaktiviertem Modus für automatische Commits verwendet werden.  
  
 Diese Methode ergibt einen Fehler und löst eine Ausnahme aus, wenn der Client mit einer manuellen Transaktion beginnt und von SQL Server aus irgendeinem Grund ein Rollback der manuellen Transaktion ausgeführt wird. Beispielsweise wird eine Ausnahme ausgelöst, wenn vom Client eine gespeicherte Prozedur, die explizit ROLLBACK TRANSACTION aufruft, und anschließend die commit-Methode aufgerufen wird. Wird von SQL Server zudem ein Fehler mit einem Schweregrad ab 16 ausgelöst, um ein Rollback der vom Client initiierten manuellen Transaktion auszuführen, wird eine Ausnahme ausgelöst, wenn anschließend die commit-Methode aufgerufen wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
