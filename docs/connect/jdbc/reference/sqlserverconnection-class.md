---
title: SQLServerConnection-Klasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 937292a6-1525-423e-a2b2-a18fd34c2893
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4746e09839e2015e4b7b14963ae698c66066ac78
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42786298"
---
# <a name="sqlserverconnection-class"></a>SQLServerConnection-Klasse
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Stellt eine JDBC-Verbindung mit einer [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank dar.  
  
 **Paket:** com.microsoft.sqlserver.jdbc  
  
 **Implementiert** [ISQLServerConnection](../../../connect/jdbc/reference/isqlserverconnection-interface.md) und java.io.Serializable  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public class SQLServerConnection  
```  
  
## <a name="remarks"></a>Remarks  
 SQLServerConnection unterstützt JDBC-Verbindungspooling und kann entweder eine physische JDBC-Verbindung oder eine logische JDBC-Verbindung sein. SQLServerConnection verwaltet die Transaktionssteuerung für alle Anweisungen, die aus ihr erstellt wurden, und kann an verteilten XA-Transaktionen teilnehmen, die über einen XAResource-Adapter verwaltet werden.  
  
 SQLServerConnection verwaltet einen Pool vorbereiteter Anweisungshandles. Vorbereitete Anweisungen werden einmal vorbereitet und werden normalerweise mehrere Male mit unterschiedlichen Parameterdatenwerten ausgeführt. Vorbereitete Anweisungen werden ebenfalls über logische (als Poolverbindung verwendete) Verbindungsgrenzen hinweg beibehalten.  
  
> [!NOTE]  
>  SQLServerConnection ist nicht threadsicher. Mehrere aus einer einzelnen Verbindung erstellte Anweisungen können simultan in parallelen Threads verarbeitet werden.  
  
 Diese Klasse unterstützt das Entpacken in die SQLServerConnection-Klasse, java.sql.connection-Schnittstelle und ISQLServerConnection-Schnittstelle. Weitere Informationen finden Sie unter [Wrapper und Schnittstellen](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [API-Referenz für den JDBC-Treiber](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
