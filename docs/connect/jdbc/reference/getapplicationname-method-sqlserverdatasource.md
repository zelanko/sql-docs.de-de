---
title: getApplicationName-Methode (SQLServerDataSource) | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7ad1a1b199b391e00a3db1c916f349f9cec94713
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924180"
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
  
  
