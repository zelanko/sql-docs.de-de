---
title: setServerPreparedStatementDiscardThreshold Method (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 96c5454ed116c8e7264f475b6488db29bab66a9c
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927801"
---
# <a name="setserverpreparedstatementdiscardthreshold-method-sqlserverdatasource"></a>setServerPreparedStatementDiscardThreshold-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Diese Methode legt den Wert der Verbindungseigenschaft serverPreparedStatementDiscardThreshold fest. Mit dieser Einstellung steuern Sie, wie viele ausstehende Aktionen zum Verwerfen vorbereiteter Anweisungen (sp_unprepare) pro Verbindung vorhanden sein dürfen, bevor ein Aufruf zum Bereinigen der ausstehenden Handles auf dem Server ausgeführt wird. Wenn diese Eigenschaft auf „<= 1“ festgelegt ist, werden unprepare-Aktionen sofort nach Abschluss der Prepared Statements ausgeführt. Wenn die Eigenschaft auf „>1“ festgelegt ist, werden diese Aufrufe in einem Batch zusammengefasst, um einen durch zu häufiges Aufrufen von „sp_unprepare“ entstehenden Overhead zu vermeiden.
 
## <a name="syntax"></a>Syntax  
  
```
public void setServerPreparedStatementDiscardThreshold(int enablePrepareOnFirstPreparedStatementCall);  
```  
  
#### <a name="parameters"></a>Parameter  
 *serverPreparedStatementDiscardThreshold*  
  
 Der neue Wert der Verbindungseigenschaft **serverPreparedStatementDiscardThreshold**.  

## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Bemerkungen  
 Diese Methode ist über Version 6.4 und höher des JDCB-Treibers verfügbar.
 
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
