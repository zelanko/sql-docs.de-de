---
title: getHostNameInCertificate-Methode (SQLServerDataSource) | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5f35af25109bc68a36560c6496cf5f5268bd9319
ms.sourcegitcommit: 54cfeb36c9caa51ec68fa8f4a1918e305db5e00a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2020
ms.locfileid: "81219259"
---
# <a name="gethostnameincertificate-method-sqlserverdatasource"></a>getHostNameInCertificate-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt den Hostnamen zurück, der zum Überprüfen des TLS-Zertifikats (Transport Layer Security), zuvor bekannt als Secure Sockets Layer (SSL), für SQL Server verwendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.String getHostNameInCertificate()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Eine **Zeichenfolge**, die den Hostnamen oder – sofern kein Wert festgelegt ist – NULL enthält.  
  
## <a name="remarks"></a>Bemerkungen  
 Der Hostname dient zum Überprüfen des TLS-/SSL-Zertifikatwerts für SQL Server, wenn die Kommunikationsebene mithilfe von TLS/SSL verschlüsselt wird.  
  
 Ist der Hostname nicht festgelegt, wird von der [getHostNameInCertificate](../../../connect/jdbc/reference/gethostnameincertificate-method-sqlserverdatasource.md)-Methode der Standardwert (NULL) zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
