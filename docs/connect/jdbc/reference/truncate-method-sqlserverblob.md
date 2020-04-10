---
title: truncate-Methode (SQLServerBlob) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerBlob.truncate
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ef181e04-003a-442a-9b7e-0c508a7cc873
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ddcb67b6a679cadaa33775d11987d90a735ca799
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80908450"
---
# <a name="truncate-method-sqlserverblob"></a>truncate-Methode (SQLServerBlob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Kürzt ein BLOB auf die angegebene Länge.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void truncate(long len)  
```  
  
#### <a name="parameters"></a>Parameter  
 *len*  
  
 Die neue Länge für das BLOB.  
  
## <a name="exceptions"></a>Ausnahmen  
 java.sql.SQLException  
  
## <a name="remarks"></a>Bemerkungen  
 Diese truncate-Methode wird von der truncate-Methode in der java.sql.Blob-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerBlob-Methoden](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [SQLServerBlob-Elemente](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob-Klasse](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
