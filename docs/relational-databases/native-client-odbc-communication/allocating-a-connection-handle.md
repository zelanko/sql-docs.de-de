---
description: Zuordnen eines Verbindungshandles
title: Zuordnen eines Verbindungs Handles | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, passwords
- ODBC applications, connections
- handles [SQL Server Native Client]
- expiration [SQL Server Native Client]
- passwords [SQL Server], modifying
- SQL Server Native Client ODBC driver, connection handles
- connection handles [SQL Server Native Client]
- modifying passwords
- SQLAllocHandle function
ms.assetid: 471d8a31-199c-4f92-bb10-004fc7733b35
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b7c477627f8f4d8a4e060dcd29ab4c7fa97629d7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88420704"
---
# <a name="allocating-a-connection-handle"></a>Zuordnen eines Verbindungshandles
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Bevor die Anwendung eine Verbindung mit einer Datenquelle oder einem Treiber herstellen kann, muss sie ein Verbindungshandle zuordnen. Dies erfolgt durch Aufrufen von **sqlzuordchandle** , wobei der Parameter " *typtype* " auf "SQL_HANDLE_DBC" festgelegt ist und " *InputHandle* " auf ein initialisiertes Umgebungs Handle verweist.  
  
 Die Eigenschaften der Verbindung werden kontrolliert, indem Verbindungsattribute festgelegt werden. Da Transaktionen auf Verbindungsebene auftreten, handelt es sich bei der Transaktionsisolationsstufe beispielsweise um ein Verbindungsattribut. Um ein Verbindungsattribut handelt es sich entsprechend auch beim Anmeldungstimeout bzw. bei der Anzahl der Sekunden, die bei einem Verbindungsversuch bis zum Timeout verstreichen.  
  
 Verbindungs Attribute werden mit [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)festgelegt, und ihre aktuellen Einstellungen werden mit [SQLGetConnectAttr](../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md)abgerufen. Wenn **SQLSetConnectAttr** aufgerufen wird, bevor versucht wird, eine Verbindung herzustellen, speichert der ODBC-Treiber-Manager die Attribute in der Verbindungs Struktur und legt Sie im Rahmen des Verbindungsprozesses im Treiber fest. Einige Verbindungsattribute müssen festgelegt werden, bevor die Anwendung einen Verbindungsversuch unternimmt. Andere hingegen können nach dem Herstellen der Verbindung festgelegt werden. SQL_ATTR_ODBC_CURSORS muss vor dem Herstellen einer Verbindung festgelegt werden, während SQL_ATTR_AUTOCOMMIT nach hergestellter Verbindung festgelegt werden kann.  
  
 Anwendungen, die unter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version 7.0 oder höher ausgeführt werden, können mitunter eine Leistungsverbesserung erzielen, indem die TDS-Netzwerkpaketgröße (Tabular Data Stream) neu festgelegt wird. Die Standardpaketgröße wird auf dem Server festlegt und beträgt 4 Byte. Mit einer Paketgröße von 4 KB bis 8 KB wird im Allgemeinen die beste Leistung erzielt. Wenn sich beim Testen herausstellt, dass eine andere Paketgröße eine bessere Leistung erzielt, kann die Anwendung die Paketgröße neu festlegen. ODBC-Anwendungen können dies tun, bevor Sie eine Verbindung herstellen, indem Sie **SQLSetConnectAttr** mit der SQL_ATTR_PACKET_SIZE-Option aufrufen. Einige Anwendungen zeigen zwar mit einer größeren Paketgröße eine bessere Leistung, die Leistungsverbesserungen sind im Allgemeinen jedoch für Paketgrößen über 8 KB minimal.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber verfügt über eine Reihe von erweiterten Verbindungs Attributen, die eine Anwendung verwenden kann, um ihre Funktionalität zu erhöhen. Einige dieser Attribute steuern die gleichen Optionen, die in Datenquellen festgelegt und zum Überschreiben von Optionen in einer Datenquelle verwendet werden können. Wenn eine Anwendung beispielsweise Bezeichner in Anführungszeichen verwendet, kann sie das treiberspezifische Attribut SQL_COPT_SS_QUOTED_IDENT auf SQL_QI_ON festlegen, um sicherzustellen, dass diese Option unabhängig von der Einstellung in einer Datenquelle stets festgelegt ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kommunikation mit SQL Server &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
