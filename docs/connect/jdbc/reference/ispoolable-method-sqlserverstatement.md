---
title: Methode „isPoolable“ (SQLServerStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b8a12ac5-57cb-4288-9973-c7d5cebd197c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3f0b0e45e24d1eb8ddf23b3b544d7f6e7b52d728
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925821"
---
# <a name="ispoolable-method-sqlserverstatement"></a>isPoolable-Methode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt einen Wert zurück, durch den angegeben wird, ob dem vom Benutzer bereitgestellten Anwendungspool eine Anweisung hinzugefügt werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean isPoolable() throws SQLException  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **TRUE** wird zurückgegeben, wenn dem vom Benutzer bereitgestellten Anwendungspool eine Anweisung hinzugefügt werden kann. Andernfalls wird **FALSE** zurückgegeben.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Mit [setPoolable](../../../connect/jdbc/reference/setpoolable-method-sqlserverstatement.md) wird für ein Objekt das Verhalten beim Hinzufügen zu Pools geändert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
