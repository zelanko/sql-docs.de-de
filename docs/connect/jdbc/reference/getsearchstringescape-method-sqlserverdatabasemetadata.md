---
title: getSearchStringEscape-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getSearchStringEscape
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ea0f95d0-0238-4dc8-9f26-7ff9b65f30c3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4f83f85e176e38ea163e7942fc641ce307863f76
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80929227"
---
# <a name="getsearchstringescape-method-sqlserverdatabasemetadata"></a>getSearchStringEscape-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft die **Zeichenfolge** ab, mit der sich Platzhalterzeichen mit Escapezeichen versehen lassen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.String getSearchStringEscape()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Eine **Zeichenfolge** zum Versehen der Platzhalterzeichenfolge mit Escapezeichen.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getSearchStringEscape-Methode wird von der getSearchStringEscape-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
 Diese Methode wird nur für Suchen nach Metadatenmustern verwendet. Sie gibt „\\“ zurück. Mit einem **Zeichenfolgen**-Suchmuster können Platzhalter („%“ und „_“) mit Escapezeichen versehen und durch Voranstellen eines umgekehrten Schrägstrichs als Literale bereitgestellt werden. Hierdurch wird „\\%“ in „[%]“ und „\\\_“ in „[\_]“ konvertiert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
