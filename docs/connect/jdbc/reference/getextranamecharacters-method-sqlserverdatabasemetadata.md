---
title: getExtraNameCharacters-Methode (SQLServerDatabaseMetaData)
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
- SQLServerDatabaseMetaData.getExtraNameCharacters
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a22becfe-0f07-4a15-8d11-06d4054b2369
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 99ffe958cae6a13f4df573385b91143c7c259ea9
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39084812"
---
# <a name="getextranamecharacters-method-sqlserverdatabasemetadata"></a>getExtraNameCharacters-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft alle zusätzlichen Zeichen ab, die in Bezeichnernamen ohne Anführungszeichen verwendet werden können (beispielsweise Zeichen, die über "a - z", "A - Z", "0 - 9" und "_" hinausgehen).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.String getExtraNameCharacters()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Eine **Zeichenfolge** mit den zusätzlichen Zeichen.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese GetExtraNameCharacters-Methode wird von der GetExtraNameCharacters-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
 Wird [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]-Datenbank verwendet, werden von dieser Methode die folgenden zusätzlichen Zeichen zurückgegeben: „$“, „#“ und „\@“.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
