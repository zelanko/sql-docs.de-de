---
title: setApplicationName-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setApplicationName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 24d6e48d-53c4-4da2-a6de-1cdff463c9cd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: df502532cb25ab79aa101629f8ca891cfac89ce3
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920231"
---
# <a name="setapplicationname-method-sqlserverdatasource"></a>setApplicationName-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den Anwendungsnamen fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setApplicationName(java.lang.String applicationName)  
```  
  
#### <a name="parameters"></a>Parameter  
 *applicationName*  
  
 Ein **String-Objekt**, das den Namen der Anwendung enthält.  
  
## <a name="remarks"></a>Bemerkungen  
 Anhand des Anwendungsnamens wird die jeweilige Anwendung in den verschiedenen Profilerstellungs- und Protokollierungstools von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] identifiziert. Ist der Anwendungsname nicht festgelegt, wird von der getApplicationName-Methode die nicht lokalisierte Zeichenfolge „[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]“ zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
