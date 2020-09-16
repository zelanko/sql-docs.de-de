---
description: SQLServerPreparedStatement-Klasse
title: SQLServerPreparedStatement-Klasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a8481c06-fbba-432b-8c69-4f4619c20ad4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 75a04a0873308cc09c16b54f5d482ed54a20c0b1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88472139"
---
# <a name="sqlserverpreparedstatement-class"></a>SQLServerPreparedStatement-Klasse
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Stellt die grundlegende Implementierung der JDBC-Funktion für vorbereitete Anweisungen dar.  
  
 **Paket:** com.microsoft.sqlserver.jdbc  
  
 **Erweitert:** SQLServerStatement  
  
 **Implementiert** [ISQLServerPreparedStatement](../../../connect/jdbc/reference/isqlserverpreparedstatement-interface.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public class SQLServerPreparedStatement  
```  
  
## <a name="remarks"></a>Bemerkungen  
 SQLServerPreparedStatement stellt Methoden bereit, mit denen Sie Parameter in Form beliebiger nativer Java-Typen und verschiedener Java-Objekttypen angeben können. SQLServerPreparedStatement bereitet anhand der gespeicherten [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **sp_prepare**-Prozedur Anweisungen vor und verwendet das zurückgegebene Anweisungshandle noch mal für jede nachfolgende Ausführung einer Anweisung, wobei normalerweise verschiedene vom Benutzer bereitgestellte Parameter verwendet werden.  
  
 SQLServerPreparedStatement unterstützt Batchverarbeitung, wobei eine Reihe von vorbereiteten Anweisungen in einem einzelnen Datenbankroundtrip ausgeführt wird, um die Laufzeitleistung zu verbessern.  
  
 Diese Klasse unterstützt das Entpacken in die SQLServerPreparedStatement-Klasse, die Schnittstellen „ISQLServerPreparedStatement“ und „java.sql.PreparedStatement“ und die von SQLServerStatement für das Entpacken unterstützten Klassen und Schnittstellen. Weitere Informationen finden Sie unter [Wrapper und Schnittstellen](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerPreparedStatement-Elemente](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [API-Referenz für den JDBC-Treiber](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
