---
title: refreshRow-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.refreshRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 048fe245-157f-4fd8-be75-ce54b83e02b3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 570a9185a83ecf1af0e47ee25cce5445dca1b958
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67975981"
---
# <a name="refreshrow-method-sqlserverresultset"></a>refreshRow-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aktualisiert die aktuelle Zeile mit dem aktuellen Wert aus der Datenbank.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void refreshRow()  
```  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese refreshRow-Methode wird von der refreshRow-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Diese Methode kann nicht aufgerufen werden, wenn sich der Cursor in der Einfügezeile befindet.  
  
 Mit dieser Methode kann der JDBC-Treiber von einer Anwendung explizit angewiesen werden, Zeilen aus der Datenbank erneut abzurufen. Die Methode muss von der Anwendung u. U. aufgerufen werden, wenn von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] Inhalte zwischengespeichert oder vorab abgerufen werden, um den aktuellen Wert einer Zeile aus der Datenbank abzurufen. Vom JDBC-Treiber werden möglicherweise mehrere Zeilen gleichzeitig aktualisiert, wenn die Abrufgröße den Wert "1" übersteigt.  
  
 Beim erneuten Abrufen von Werten werden die Transaktionsisolationsstufe und der Cursor berücksichtigt. Wird diese Methode nach dem Aufrufen einer Updatemethode, aber vor dem Aufrufen der [updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md)-Methode aufgerufen, gehen die vorgenommenen Zeilenupdates verloren. Häufiges Aufrufen dieser Methode kann sich negativ auf die Leistung auswirken.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
