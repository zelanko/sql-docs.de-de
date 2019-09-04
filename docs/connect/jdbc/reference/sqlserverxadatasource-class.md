---
title: SQLServerXADataSource-Klasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 95fc7b07-2498-4a7e-8f7f-ee0d86b598b4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4c456336170cd7d4ad7cf37a0eebc52637f0a070
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67970223"
---
# <a name="sqlserverxadatasource-class"></a>SQLServerXADataSource-Klasse
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Stellt eine intern verwendete Factory für [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)-Objekte dar.  
  
 **Paket:** com.microsoft.sqlserver.jdbc  
  
 **Erweitert** [SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)  
  
 **Implementiert** javax.sql.XADataSource  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public class SQLServerXADataSource  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Ein Objekt, von dem die SQLServerXADataSource-Schnittstelle implementiert wird, ist normalerweise bei einem Bezeichnungsdienst registriert, der JNDI (Java Naming and Directory Interface) verwendet.  
  
 Die SQLServerXADataSource-Klasse stellt Datenbankverbindungen zur Verwendung in verteilten (XA-)Transaktionen bereit. Die SQLServerXADataSource-Klasse unterstützt auch das Verbindungspooling physischer Verbindungen. Die SQLServerXADataSource-und sqlserverxaconnection-Schnittstellen, die im Paket "javax. SQL" definiert sind [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], werden von implementiert.  
  
 Ein SQLServerXAConnection-Objekt ist eine Poolverbindung, die Teil einer verteilten Transaktion sein kann. Genauer ist, erweitert sqlserverxaconnetction die SQLServerPooledConnection-Schnittstelle durch Hinzufügen der [getXAResource](../../../connect/jdbc/reference/getxaresource-method-sqlserverxaconnection.md)-Methode. Von dieser Methode wird ein [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)-Objekt erzeugt, das von einem Transaktions-Manager zur Koordination der Arbeit an dieser Verbindung mit den anderen Teilnehmern an der verteilten Transaktion verwendet werden kann. Da Sie die SQLServerPooledConnection-Schnittstelle erweitern, unterstützen sqlserverxaconnetction-Objekte alle Methoden von SQLServerPooledConnection-Objekten. Sie sind wiederverwendbare physikalische Verbindungen mit einer zu Grunde liegenden Datenquelle und erzeugen logische Verbindungshandles, die an eine JDBC-Anwendung zurückgegeben werden können.  
  
 Sqlserverxaconnection-Objekte werden von einem SQLServerXADataSource-Objekt erstellt. SQLServerConnectionPoolDataSource-Objekte und SQLServerXADataSource-Objekte sind ähnlich, da Sie beide unter einer Datenquellen Schicht implementiert sind, die für die JDBC-Anwendung sichtbar ist. Dank dieser Architektur kann [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verteilte Transaktionen auf eine Weise unterstützen, die für die Anwendung transparent ist. SQLServerXADataSource kann für die Integration mit [!INCLUDE[msCoName](../../../includes/msconame_md.md)]-DTC (Distributed Transaction Coordinator) konfiguriert werden, um echte verteilte Transaktionsverarbeitung zu ermöglichen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerXADataSource-Elemente](../../../connect/jdbc/reference/sqlserverxadatasource-members.md)   
 [API-Referenz für den JDBC-Treiber](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
