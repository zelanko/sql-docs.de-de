---
title: supportsSchemasInDataManipulation-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsSchemasInDataManipulation
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 812dc551-c718-494e-80d9-75732464c8ba
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8f1c2c73c6397b2618798ddf4d32cdbedf9fa59a
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928497"
---
# <a name="supportsschemasindatamanipulation-method-sqlserverdatabasemetadata"></a>supportsSchemasInDataManipulation-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ab, ob in einer Datenbearbeitungsanweisung ein Schemaname verwendet werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean supportsSchemasInDataManipulation()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** unterstützt. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese supportsSchemasInDataManipulation-Methode wird von der supportsSchemasInDataManipulation-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
