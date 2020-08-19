---
description: 'SQL Server-Treibererweiterungen: Funktionen für Massenkopiervorgänge'
title: Massen Kopierfunktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], functions
- ODBC, bulk copy operations
- functions [ODBC]
ms.assetid: 6526b892-1d58-4f55-8335-f09887f6ea02
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 51fbc9b4c5ffdcb6c787c164a68ebdf790bc1ca6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88448532"
---
# <a name="sql-server-driver-extensions---bulk-copy-functions"></a>SQL Server-Treibererweiterungen: Funktionen für Massenkopiervorgänge
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  ODBC (Open Database Connectivity) ist eine Win32-Anwendungsprogrammierschnittstelle von Microsoft, mit deren Hilfe Anwendungen auf Daten in ODBC-Datenquellen zugreifen. In der Referenz zum ODBC-Treiber von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sind nicht sämtliche ODBC-Funktionsaufrufe dokumentiert. Es werden nur diejenigen Funktionen besprochen, die über treiberspezifische Parameter verfügen oder ein treiberspezifisches Verhalten zeigen, wenn sie mit dem ODBC-Treiber von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client verwendet werden.  
  
 Der ODBC-Treiber von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Native Client entspricht der Spezifikation für ODBC 3.51. Um eine umfassende Referenz zu ODBC 3,51 zu erhalten, laden Sie das Microsoft Data Access Components SDK aus dem [Developer Center für Datenzugriff und-Speicherung](https://go.microsoft.com/fwlink?linkid=4173)herunter, oder zeigen Sie die [ODBC-Programmier Referenz](https://go.microsoft.com/fwlink/?LinkId=45250) Online an.  
 
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-spezifische API-Erweiterung für Massenkopierfunktionen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treibers ermöglicht es Clientanwendungen, einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle auf schnelle Weise Datenzeilen hinzuzufügen bzw. Datenzeilen aus einer Tabelle zu extrahieren.  Bei der Verwendung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client können Sie die Massenkopierfunktionen (BCP) in SQLNCLI11.LIB und SQLNCLI.H nutzen.  
  
 Eine Anwendung, die BCP-API-Funktionsaufrufe verwendet, sollte mit der Bibliothek (LIB-Datei) verknüpft werden, die mit dem von der Anwendung verwendeten Treiber (DLL-Datei) geliefert wurde. Eine BCP-Anwendung sollte nicht mit mehr als einer Treiberbibliothek verknüpft werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [bcp_batch](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md)  
  
-   [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)  
  
-   [bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)  
  
-   [bcp_collen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md)  
  
-   [bcp_colptr](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colptr.md)  
  
-   [bcp_columns](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)  
  
-   [bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)  
  
-   ['bcp_done'](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md)  
  
-   [bcp_exec](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md)  
  
-   [bcp_getcolfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-getcolfmt.md)  
  
-   [bcp_gettypename](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-gettypename.md)  
  
-   [bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)  
  
-   [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md)  
  
-   [bcp_readfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md)  
  
-   ['bcp_sendrow'](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)  
  
-   [bcp_setbulkmode](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md)  
  
-   [bcp_setcolfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setcolfmt.md)  
  
-   [bcp_writefmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterungen des SQL Server Treibers](https://msdn.microsoft.com/library/1043bc93-965d-4939-bd1c-21e9d8d3e9ac)   
 [Ausführen von Massen Kopier Vorgängen &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
