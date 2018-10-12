---
title: SetURL-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setURL
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bea70100-ac98-4625-8748-ef7cc0b111ea
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 29e1b67caaf566f04cf01c7c93a5e8d2445c31ef
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47633948"
---
# <a name="seturl-method-sqlserverdatasource"></a>setURL-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt die URL fest, die zum Herstellen einer Verbindung mit der Datenquelle verwendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setURL(java.lang.String url)  
```  
  
#### <a name="parameters"></a>Parameter  
 *url*  
  
 Ein **String-Objekt**, das die URL enthält.  
  
## <a name="remarks"></a>Remarks  
 Aus Sicherheitsgründen sollte das Kennwort nicht in der URL für die setURL-Methode enthalten sein. Der Grund hierfür ist, dass Java-Anwendungsserver von Drittanbietern oft den für die URL-Eigenschaft festgelegten Wert auf der Benutzeroberfläche für die Datenquellenkonfiguration anzeigen. Verwenden Sie stattdessen die [setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md)-Methode, um den Wert für das Kennwort festzulegen. Java-Anwendungsserver zeigen kein in der Datenquelle festgelegtes Kennwort auf der Konfigurationsbenutzeroberfläche an.  
  
> [!NOTE]  
>  Wird die setURL-Methode nicht vor dem Aufruf der [getURL](../../../connect/jdbc/reference/geturl-method-sqlserverdatasource.md)-Methode aufgerufen, wird von getURL der Standardwert „(jdbc:sqlserver://)“ zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
