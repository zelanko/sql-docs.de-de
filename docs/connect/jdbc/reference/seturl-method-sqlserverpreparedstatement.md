---
title: setURL-Methode (SQLServerPreparedStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setURL
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d853b2f3-fb72-4d4b-8997-f4a45a9dfefc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 47b1cff27860a09e4f9b8cc43f8523b5a1846a3c
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67972086"
---
# <a name="seturl-method-sqlserverpreparedstatement"></a>setURL-Methode (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den angegebenen Parameter auf den angegebenen URL-Wert fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final void setURL(int parameterIndex,  
                         java.net.URL x)  
```  
  
#### <a name="parameters"></a>Parameter  
 *parameterindex*  
  
 Ein Wert **ganzzahliger** Wert zum Angeben der Parameternummer.  
  
 *x*  
  
 Ein URL-Objekt  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese -Methode wird von der -Methode in der java.sql.PreparedStatement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerPreparedStatement-Elemente](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement-Klasse](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
