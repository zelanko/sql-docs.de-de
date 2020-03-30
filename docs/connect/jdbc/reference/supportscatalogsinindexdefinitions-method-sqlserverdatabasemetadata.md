---
title: supportsCatalogsInIndexDefinitions-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsCatalogsInIndexDefinitions
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a19423a0-e7b6-4f5c-94be-80ddf3fa4717
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 15d253050f557c799bef717962bc0e3750656147
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67969700"
---
# <a name="supportscatalogsinindexdefinitions-method-sqlserverdatabasemetadata"></a>supportsCatalogsInIndexDefinitions-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob in einer Indexdefinitionsanweisung ein Katalogname verwendet werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean supportsCatalogsInIndexDefinitions()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** unterstützt. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese supportsCatalogsInIndexDefinitions-Methode wird von der supportsCatalogsInIndexDefinitions-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
