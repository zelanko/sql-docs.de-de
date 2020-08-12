---
title: Verwenden von Verbindungspools
description: In diesem Artikel erfahren Sie, wie der JDBC-Treiber für SQL Server JDBC-konforme Schnittstellen bereitstellt, um das Verbindungspooling in Java zu unterstützen.
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 699d4e8a-34bf-4c60-b0d5-4a10dad6084a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c3bcacec5f85150f7de437d936463a3b3807f9ef
ms.sourcegitcommit: cb620c77fe6bdefb975968837706750c31048d46
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86391747"
---
# <a name="using-connection-pooling"></a>Verwenden von Verbindungspools

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] unterstützt Verbindungspoolfunktionen der Java-Plattform, Enterprise Edition (Java EE). Der JDBC-Treiber implementiert die erforderlichen JDBC 3.0-Schnittstellen, damit der Treiber Verbindungspoolimplementierungen von Middlewareherstellern nutzen kann. Der JDBC-Treiber ist JDBC 3.0-kompatibel. Middleware wie Java EE-Anwendungsserver bieten häufig kompatible Verbindungspoolfunktionen. Der JDBC-Treiber nutzt in diesen Umgebungen Verbindungspools.  
  
> [!NOTE]  
> Obwohl der JDBC-Treiber Java EE-Verbindungspools unterstützt, stellt er keine eigene Poolimplementierung bereit. Der Treiber benötigt Java-Anwendungsserver eines Drittanbieters zum Verwalten der Verbindungen.  
  
## <a name="remarks"></a>Bemerkungen

Für die Verbindungspoolimplementierung stehen die folgenden Klassen zur Verfügung.  
  
| Klasse                                                           | Implementiert                                                    | BESCHREIBUNG                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| --------------------------------------------------------------- | ------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| com.microsoft.sqlserver.jdbc. SQLServerXADataSource             | javax.sql.ConnectionPoolDataSource und javax.sql.XADataSource | Sie sollten für alle erforderlichen Java EE-Serverfunktionen die [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md)-Klasse verwenden, da sie alle JDBC 3.0-Poolfunktionen und XA-Schnittstellen implementiert.                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| com.microsoft.sqlserver.jdbc. SQLServerConnectionPoolDataSource | javax.sql.ConnectionPoolDataSource                            | Bei dieser Klasse handelt es sich um ein Verbindungsfactory, das es dem Java EE-Anwendungsserver ermöglicht, den Verbindungspool mit physischen Verbindungen zu füllen. Wenn die Konfiguration des Java EE-Herstellers eine Klasse erfordert, die „javax.sql.ConnectionPoolDataSource“ implementiert, geben Sie den Klassennamen als [SQLServerConnectionPoolDataSource](../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md) an. Sie sollten stattdessen im Allgemeinen die [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md)-Klasse verwenden, da sie sowohl Poolfunktionen als auch XA-Schnittstellen implementiert und in einer größeren Zahl von Java EE-Serverkonfigurationen überprüft wurde. |
  
 Der JDBC-Anwendungscode sollte die Verbindungen immer explizit schließen, damit die Pools optimal genutzt werden können. Wenn die Anwendung eine Verbindung explizit schließt, kann die Poolimplementierung die Verbindung sofort wiederverwenden kann. Wenn die Verbindung nicht geschlossen wird, kann sie von anderen Anwendungen nicht wiederverwendet werden. Die Anwendungen können im `finally`-Konstrukt sicherstellen, dass Poolverbindungen auch beim Auftreten von Fehlern geschlossen werden.  
  
> [!NOTE]  
> Der JDBC-Treiber ruft zurzeit nicht die gespeicherte Prozedur "sp_reset_connection" auf, wenn die Verbindung an den Pool zurückgegeben wird. Der Treiber geht stattdessen davon aus, dass die Java-Anwendungsserver der Drittanbieter die Verbindungen wieder in den ursprünglichen Status zurück versetzen.  
  
## <a name="see-also"></a>Weitere Informationen

[Verbinden mit SQL Server mit dem JDBC-Treiber](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
