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
ms.openlocfilehash: b0721341cbf095e0aa27fab392c8d03f72dc2e3a
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67970891"
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
  
## <a name="remarks"></a>Bemerkungen  
 Zum Abrufen der Metadaten von Parametern werden vorbereitete Anweisungen mit SET FMT ONLY ausgeführt. Von aufrufbaren Anweisungen wird "sp_sproc_columns" aufgerufen, um Namen und Metadaten für die Prozedurparameter abzurufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerParameterMetaData-Elemente](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [API-Referenz für den JDBC-Treiber](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
