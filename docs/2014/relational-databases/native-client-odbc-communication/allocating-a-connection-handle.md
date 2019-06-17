---
title: Zuordnen eines Verbindungshandles | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 12962333f722032797470943d3f5ffc79d0cdee6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62864998"
---
# <a name="allocating-a-connection-handle"></a>Zuordnen eines Verbindungshandles
  Bevor die Anwendung eine Verbindung mit einer Datenquelle oder einem Treiber herstellen kann, muss sie ein Verbindungshandle zuordnen. Dies erfolgt durch Aufrufen von **SQLAllocHandle** mit der *HandleType* -Parameter auf SQL_HANDLE_DBC festgelegt wird und *InputHandle* auf ein initialisiertes Umgebungshandle zeigt.  
  
 Die Eigenschaften der Verbindung werden kontrolliert, indem Verbindungsattribute festgelegt werden. Da Transaktionen auf Verbindungsebene auftreten, handelt es sich bei der Transaktionsisolationsstufe beispielsweise um ein Verbindungsattribut. Um ein Verbindungsattribut handelt es sich entsprechend auch beim Anmeldungstimeout bzw. bei der Anzahl der Sekunden, die bei einem Verbindungsversuch bis zum Timeout verstreichen.  
  
 Verbindungsattribute festgelegt [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md), und ihre aktuellen Einstellungen werden abgerufen, mit [SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md). Wenn **SQLSetConnectAttr** wird aufgerufen, bevor, eine Verbindung versucht wird, der ODBC-Treiber-Manager speichert die Attribute in seiner Verbindungsstruktur und legt sie im Rahmen des Verbindungsprozesses im Treiber fest. Einige Verbindungsattribute müssen festgelegt werden, bevor die Anwendung einen Verbindungsversuch unternimmt. Andere hingegen können nach dem Herstellen der Verbindung festgelegt werden. SQL_ATTR_ODBC_CURSORS muss vor dem Herstellen einer Verbindung festgelegt werden, während SQL_ATTR_AUTOCOMMIT nach hergestellter Verbindung festgelegt werden kann.  
  
 Anwendungen, die unter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version 7.0 oder höher ausgeführt werden, können mitunter eine Leistungsverbesserung erzielen, indem die TDS-Netzwerkpaketgröße (Tabular Data Stream) neu festgelegt wird. Die Standardpaketgröße wird auf dem Server festlegt und beträgt 4 Byte. Mit einer Paketgröße von 4 KB bis 8 KB wird im Allgemeinen die beste Leistung erzielt. Wenn sich beim Testen herausstellt, dass eine andere Paketgröße eine bessere Leistung erzielt, kann die Anwendung die Paketgröße neu festlegen. ODBC-Anwendungen erreichen dies vor dem Herstellen einer Verbindung durch den Aufruf **SQLSetConnectAttr** mit der SQL_ATTR_PACKET_SIZE-Option. Einige Anwendungen zeigen zwar mit einer größeren Paketgröße eine bessere Leistung, die Leistungsverbesserungen sind im Allgemeinen jedoch für Paketgrößen über 8 KB minimal.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber bietet eine Reihe von erweiterten Verbindungsattributen, mit denen eine Anwendung ihre Funktionalität steigern. Einige dieser Attribute steuern die gleichen Optionen, die in Datenquellen festgelegt und zum Überschreiben von Optionen in einer Datenquelle verwendet werden können. Wenn eine Anwendung beispielsweise Bezeichner in Anführungszeichen verwendet, kann sie das treiberspezifische Attribut SQL_COPT_SS_QUOTED_IDENT auf SQL_QI_ON festlegen, um sicherzustellen, dass diese Option unabhängig von der Einstellung in einer Datenquelle stets festgelegt ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Kommunikation mit SQLServer &#40;ODBC&#41;](communicating-with-sql-server-odbc.md)  
  
  
