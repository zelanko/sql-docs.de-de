---
title: Methode „setEnablePrepareOnFirstPreparedStatementCall“ (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 26ac2cac075d08b8029ac0e85dacffd1674fb0da
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67974312"
---
# <a name="setenableprepareonfirstpreparedstatementcall-method-sqlserverdatasource"></a>setEnablePrepareOnFirstPreparedStatementCall-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Mit dieser Methode geben Sie das Verhalten einer bestimmten Verbindungsinstanz an. Bei FALSE ruft die erste Ausführung eines Prepared Statements sp_executesql auf und erstellt kein Prepared Statement. Sobald die zweite Ausführung erfolgt, ruft diese sp_prepexec auf und richtet tatsächlich ein Handle für Prepared Statements ein. Bei den folgenden Ausführungen wird sp_execute aufgerufen. Dadurch ist „sp_unprepare“ nicht mehr für den Abschluss einer vorbereiteten Anweisung erforderlich, falls diese nur einmal ausgeführt wird.  
## <a name="syntax"></a>Syntax  
  
```
public void setEnablePrepareOnFirstPreparedStatementCall(boolean enablePrepareOnFirstPreparedStatementCall);  
```  
  
#### <a name="parameters"></a>Parameter  
 *enablePrepareOnFirstPreparedStatementCall*  
  
 Der neue Wert der Verbindungseigenschaft **enablePrepareOnFirstPreparedStatementCall**  

## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Bemerkungen  
 Diese Methode ist über Version 6.4 und höher des JDCB-Treibers verfügbar.
 
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
