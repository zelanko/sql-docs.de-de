---
title: setDateTimeOffset-Methode (SQLServerPreparedStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5014dba9-1755-4769-b070-6cbeecee864e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0049865a188677e38f5385187e7e5fd171a5dd61
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922418"
---
# <a name="setdatetimeoffset-method-sqlserverpreparedstatement"></a>setDateTimeOffset-Methode (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Diese Methode wurde im JDBC-Treiber 3.0 für [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hinzugefügt.  
  
 Mit dieser Methode wird der Wert der angegebenen Spalte auf den Wert der Klasse [DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) festgelegt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final void setDateTimeOffset(int n, microsoft.sql.DateTimeOffset x)  
```  
  
#### <a name="parameters"></a>Parameter  
 *n*  
  
 Die nullbasierte Ordinalzahl einer Spalte.  
  
 *x*  
  
 Dies ist ein Objekt der [DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)-Klasse.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerPreparedStatement-Elemente](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement-Klasse](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
