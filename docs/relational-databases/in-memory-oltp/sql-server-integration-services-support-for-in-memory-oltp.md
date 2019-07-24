---
title: SQL Server Integration Services-Unterstützung für In-Memory OLTP | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: ea82a9b9-e9ed-4d6f-b3fd-917f6c687ae3
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a9dfaedb283f7b1dd6af08405f5229c994b8987a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68111691"
---
# <a name="sql-server-integration-services-support-for-in-memory-oltp"></a>SQL Server Integration Services-Unterstützung für In-Memory OLTP
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Sie können eine speicheroptimierte Tabelle, eine Sicht, die auf speicheroptimierte Tabellen verweist, oder eine systemintern kompilierte gespeicherte Prozedur als Quelle oder Ziel des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Pakets (SSIS) verwenden. Sie können [ADO NET Source](../../integration-services/data-flow/ado-net-source.md), [OLE DB Source](../../integration-services/data-flow/ole-db-source.md)oder [ODBC Source](../../integration-services/data-flow/odbc-source.md) im Datenfluss eines SSIS-Pakets verwenden und die Quellkomponente so konfigurieren, dass Daten aus einer speicheroptimierten Tabelle oder einer Sicht abgerufen werden. Sie können auch eine SQL-Anweisung angeben, um eine systemintern kompilierte gespeicherte Prozedur auszuführen. Ebenso können Sie [ADO NET Destination](../../integration-services/data-flow/ado-net-destination.md), [OLE DB Destination](../../integration-services/data-flow/ole-db-destination.md)oder [ODBC Destination](../../integration-services/data-flow/odbc-destination.md) verwenden, um Daten in eine speicheroptimierte Tabelle oder eine Sicht zu laden, oder Sie können eine SQL-Anweisung angeben, um eine systemintern kompilierte gespeicherte Prozedur auszuführen.  
  
 Sie können die oben erwähnten Quell- und Zielkomponenten in einem SSIS-Paket so konfigurieren, dass ebenso wie bei anderen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabellen und -Sichten aus speicheroptimierten Tabellen gelesen bzw. in speicheroptimierte Tabellen geschrieben wird. Beim Verwenden systemintern kompilierter gespeicherter Prozeduren sind jedoch die wichtigen Aspekte im folgenden Abschnitt zu beachten.  
  
## <a name="invoking-a-natively-compiled-stored-procedure-from-an-ssis-package"></a>Aufrufen einer systemintern kompilierten gespeicherten Prozedur aus einem SSIS-Paket  
 Zum Aufrufen einer systemintern kompilierten gespeicherten Prozedur aus einem SSIS-Paket empfiehlt es sich, eine ODBC-Quelle oder ein ODBC-Ziel mit einer SQL-Anweisung des folgenden Formats zu verwenden: **\<Prozedurname>** ohne das Schlüsselwort **EXEC**. Wenn Sie das EXEC-Schlüsselwort in der SQL-Anweisung angeben, wird eine Fehlermeldung zurückgegeben, weil der ODBC-Verbindungs-Manager den SQL-Befehlstext als [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung und nicht als gespeicherte Prozedur interpretiert und Cursor verwendet, die für die Ausführung von systemintern kompilierten gespeicherten Prozeduren nicht unterstützt werden. Der Verbindungs-Manager behandelt die SQL-Anweisung ohne EXEC-Schlüsselwort als Aufruf einer gespeicherten Prozedur, und es wird kein Cursor verwendet.  
  
 Sie können eine systemintern kompilierte gespeicherte Prozedur auch mit einer ADO.NET-Quelle und OLE DB-Quelle aufrufen, es wird jedoch empfohlen, eine ODBC-Quelle zu verwenden. Wenn Sie die ADO.NET-Quelle für die Ausführung einer systemintern kompilierten gespeicherten Prozedur konfigurieren, wird eine Fehlermeldung zurückgegeben, weil der Datenanbieter für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient), der von der ADO.NET-Quelle standardmäßig verwendet wird, die Ausführung von systemintern kompilierten gespeicherten Prozeduren nicht unterstützt. Sie können die ADO.NET-Quelle für die Verwendung des ODBC-Datenanbieters, des OLE DB-Anbieters für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]oder des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client konfigurieren. Beachten Sie jedoch, dass die ODBC-Quelle eine bessere Leistung als die ADO.NET-Quelle mit dem ODBC-Datenanbieter bietet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Unterstützung für In-Memory OLTP](../../relational-databases/in-memory-oltp/sql-server-support-for-in-memory-oltp.md)  
  
  
