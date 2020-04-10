---
title: getTrustManagerClass-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getTrustManagerClass
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 864476a18834dbc92c9dbc0d28958f317bc16e1c
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80911259"
---
# <a name="gettrustmanagerclass-method-sqlserverdatasource"></a>getTrustManagerClass-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt den Zeichenfolgenwert der Verbindungseigenschaft „TrustManagerClass“ zurück
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.String getTrustManagerClass()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Eine **Zeichenfolge**, die den Wert der Verbindungseigenschaft „TrustManagerClass“ enthält, oder NULL, wenn kein Wert festgelegt ist  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn die Eigenschaft „TrustManagerClass“ nicht festgelegt ist, gibt die [getTrustManagerClass](../../../connect/jdbc/reference/gettrustmanagerclass-method-sqlserverdatasource.md)-Methode NULL zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
