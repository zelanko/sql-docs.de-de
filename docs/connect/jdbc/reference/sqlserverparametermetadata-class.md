---
title: SQLServerParameterMetaData-Klasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 546290e0-9411-4a2b-aa36-61251e70e9cf
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6d24d63765f31f6c3218d8ed161af77298326ab7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47797223"
---
# <a name="sqlserverparametermetadata-class"></a>SQLServerParameterMetaData-Klasse
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Stellt die Metadaten für die Parameter vorbereiteter Anweisungen dar.  
  
 **Paket:** com.microsoft.sqlserver.jdbc  
  
 **Erweitert:** java.lang.Object  
  
 **Implementiert:** java.sql.ParameterMetaData  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public class SQLServerParameterMetaData  
```  
  
## <a name="remarks"></a>Remarks  
 Zum Abrufen der Metadaten von Parametern werden vorbereitete Anweisungen mit SET FMT ONLY ausgeführt. Von aufrufbaren Anweisungen wird "sp_sproc_columns" aufgerufen, um Namen und Metadaten für die Prozedurparameter abzurufen.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerParameterMetaData-Elemente](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [API-Referenz für den JDBC-Treiber](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
