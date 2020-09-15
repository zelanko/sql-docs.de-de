---
description: supportsDataDefinitionAndDataManipulationTransactions-Methode (SQLServerDatabaseMetaData)
title: supportsDataDefinitionAndDataManipulationTransactions-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsDataDefinitionAndDataManipulationTransactions
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: fe91c601-9bb3-4364-9131-575a94d3a1b3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c9a275c5ed9fed28a9bdd40fc03262870ce5bdbd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88354156"
---
# <a name="supportsdatadefinitionanddatamanipulationtransactions-method-sqlserverdatabasemetadata"></a>supportsDataDefinitionAndDataManipulationTransactions-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob von dieser Datenbank in einer Transaktion sowohl Datendefinitions- als auch Datenbearbeitungsanweisungen unterstützt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean supportsDataDefinitionAndDataManipulationTransactions()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** unterstützt. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese supportsDataDefinitionAndDataManipulationTransactions-Methode wird von der supportsDataDefinitionAndDataManipulationTransactions-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
