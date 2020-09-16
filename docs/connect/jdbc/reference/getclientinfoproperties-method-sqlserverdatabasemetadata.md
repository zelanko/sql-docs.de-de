---
description: getClientInfoProperties-Methode (SQLServerDatabaseMetaData)
title: getClientInfoProperties-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 1568aef4-f4c4-40a0-a1ab-9c106905bd92
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7a013bdc53a5699ba01accf5629326df7929e798
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88436712"
---
# <a name="getclientinfoproperties-method-sqlserverdatabasemetadata"></a>getClientInfoProperties-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft eine Liste mit den Eigenschaften für Clientinformationen ab, die vom Treiber unterstützt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.ResultSet getClientInfoProperties()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein ResultSet-Objekt  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getClientInfoProperties-Methode wird von der getClientInfoProperties-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
> [!NOTE]  
>  Von dieser Methode wird ein leeres Resultset zurückgegeben. Vom Treiber wird nur das Festlegen von **applicationName** unterstützt, und **applicationName** wird erst zum Zeitpunkt der Verbindungsherstellung festgelegt. Das Aktualisieren der Clientanwendungsinformationen nach der Verbindungsherstellung wird von SQL Server nicht unterstützt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
