---
title: GetHostNameInCertificate-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- getHostNameInCertificate Method (SQLServerDataSource)
apilocation:
- getHostNameInCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 45ea04e2-9ea5-4171-9136-d09f8a95e128
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9d4873d1251f640f6347d844d46fcb94d63e3857
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47615778"
---
# <a name="gethostnameincertificate-method-sqlserverdatasource"></a>getHostNameInCertificate-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt den Hostnamen zurück, der bei der Überprüfung des Secure Sockets Layer (SSL)-Zertifikats von SQL Server verwendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.String getHostNameInCertificate()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Eine **Zeichenfolge**, die den Hostnamen oder – sofern kein Wert festgelegt ist – NULL enthält.  
  
## <a name="remarks"></a>Remarks  
 Der Hostname dient zum Überprüfen des SQL Server-SSL-Zertifikatwerts, wenn die Kommunikationsschicht mithilfe von SSL verschlüsselt wird.  
  
 Ist der Hostname nicht festgelegt, wird von der [getHostNameInCertificate](../../../connect/jdbc/reference/gethostnameincertificate-method-sqlserverdatasource.md)-Methode der Standardwert (NULL) zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
