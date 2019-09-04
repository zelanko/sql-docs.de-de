---
title: getapplicationname-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getApplicationName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f71e501c-ccd7-4a1e-b6ea-4d47a81c18c6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a3b7e55cbaa630a4c191eead93d3e016aa07ea5b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67954399"
---
# <a name="getapplicationname-method-sqlserverdatasource"></a>getApplicationName-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt den Anwendungsnamen zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.String getApplicationName()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **String**-Objekt, das den Anwendungsnamen enthält, oder „[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]“, wenn kein Wert festgelegt ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Anhand des Anwendungsnamens wird die jeweilige Anwendung in den verschiedenen Profilerstellungs- und Protokollierungstools von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] identifiziert. Ist der Anwendungsname nicht festgelegt, wird von der getApplicationName-Methode die nicht lokalisierte Zeichenfolge „[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]“ zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
