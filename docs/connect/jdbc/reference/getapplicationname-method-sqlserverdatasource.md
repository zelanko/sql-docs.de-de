---
title: GetApplicationName-Methode (SQLServerDataSource) | Microsoft-Dokumentation
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
- SQLServerDataSource.getApplicationName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f71e501c-ccd7-4a1e-b6ea-4d47a81c18c6
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 79aa683f829e28144580585ab9afc0f517b2ec61
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42785286"
---
# <a name="getapplicationname-method-sqlserverdatasource"></a>getApplicationName-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt den Anwendungsnamen zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.String getApplicationName()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **String-Objekt**, das den Anwendungsnamen enthält, oder „[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]“, wenn kein Wert festgelegt ist.  
  
## <a name="remarks"></a>Remarks  
 Anhand des Anwendungsnamens wird die jeweilige Anwendung in den verschiedenen Profilerstellungs- und Protokollierungstools von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] identifiziert. Ist der Anwendungsname nicht festgelegt, wird von der getApplicationName-Methode die nicht lokalisierte Zeichenfolge "[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]" zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
