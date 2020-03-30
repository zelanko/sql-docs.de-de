---
title: setDateTimeOffset-Methode (SQLServerCallableStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 9383e14d-c83e-43c5-980c-50a3e0bedc31
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 264de7ac150aca7494a380fbbd4f5b490607c5c6
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67974642"
---
# <a name="setdatetimeoffset-method-sqlservercallablestatement"></a>setDateTimeOffset-Methode (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Diese Methode wurde im JDBC-Treiber 3.0 für [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hinzugefügt.  
  
 Mit dieser Methode wird der Wert der angegebenen Spalte auf den Wert der Klasse [DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) festgelegt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setDateTimeOffset(String sCol, microsoft.sql.DateTimeOffset t)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sCol*  
  
 Der Name einer Spalte.  
  
 *t*  
  
 Dies ist ein Objekt der [DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)-Klasse.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Sie können einen [DateTimeOffset Class](../../../connect/jdbc/reference/datetimeoffset-class.md)-Wert mit [SQLServerCallableStatement.getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-method-sqlservercallablestatement.md) abrufen.  
  
 [SetDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlserverpreparedstatement.md) verwendet die Ordnungszahl der Spalte.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
