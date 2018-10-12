---
title: GetSearchStringEscape-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1a12b9ca70dd8e48fa92df9b1b2be55b22ee6994
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47721358"
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
  
## <a name="remarks"></a>Remarks  
 Diese GetSearchStringEscape-Methode wird von der GetSearchStringEscape-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
 Diese Methode wird nur für Suchen nach Metadatenmustern verwendet. Sie gibt „\\“ zurück. Mit einem **Zeichenfolgen**-Suchmuster können Platzhalter („%“ und „_“) mit Escapezeichen versehen und durch Voranstellen eines umgekehrten Schrägstrichs als Literale bereitgestellt werden. Hierdurch wird „\\%“ in „[%]“ und „\\\_“ in „[\_]“ konvertiert.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
