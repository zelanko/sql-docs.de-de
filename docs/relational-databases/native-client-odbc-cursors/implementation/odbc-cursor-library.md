---
title: ODBC-Cursor Bibliothek | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], library
- SQL_CUR_USE_DRIVER option
- ODBC applications, cursors
- ODBC cursors, library
- SQL_CUR_USE_IF_NEEDED option
- SQLSetConnectAttr function
- SQL_CUR_USE_ODBC option
ms.assetid: 3c610d3d-6e06-49cf-9a40-05b6a1c83a32
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2771c3418bc942de8ffeb54694b8395e5e5aa414
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85719765"
---
# <a name="odbc-cursor-library"></a>ODBC-Cursorbibliothek
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Einige ODBC-Treiber unterstützen nur die standardmäßigen Cursor Einstellungen. Diese Treiber unterstützen auch keine positionierten Cursor Vorgänge, wie z. b. **SQLSetPos**. Die ODBC-Cursorbibliothek ist eine Komponente von Microsoft Data Access Components (MDAC), mit der Block- oder statische Cursor in einem Treiber implementiert werden, der sie normalerweise nicht unterstützt. Die Cursor Bibliothek implementiert auch positionierte UPDATE-und DELETE-Anweisungen und **SQLSetPos** für die Cursor, die Sie erstellt.  
  
 Die ODBC-Cursorbibliothek wird als Ebene zwischen dem ODBC-Treiber-Manager und einem ODBC-Treiber implementiert. Wenn die ODBC-Cursorbibliothek geladen ist, leitet der ODBC-Treiber-Manager alle cursorspezifischen Befehle an die Cursorbibliothek statt an den Treiber weiter. Die Cursorbibliothek implementiert einen Cursor durch Abrufen des gesamten Resultsets aus dem zugrunde liegenden Treiber und durch Zwischenspeichern des Resultsets auf dem Client. Bei Verwendung der ODBC-Cursorbibliothek ist die Anwendung auf die Cursorfunktionen der Cursorbibliothek beschränkt. Zusätzliche Cursorfunktionen im zugrunde liegenden Treiber sind für die Anwendung nicht verfügbar.  
  
 Es besteht kaum Bedarf, die ODBC-Cursorbibliothek mit dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber zu verwenden, da der Treiber selbst mehr Cursorfunktionen unterstützt als die ODBC-Cursorbibliothek. Der einzige Grund für die Verwendung der ODBC-Cursor Bibliothek mit dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber besteht darin, dass der Treiber seine Cursor Unterstützung über Server Cursor implementiert und Server Cursor nicht alle SQL-Anweisungen unterstützen. Erwägen Sie die Verwendung der ODBC-Cursorbibliothek, wenn ein statischer Cursor mit gespeicherten Prozeduren, Batches oder SLQ-Anweisungen, die COMPUTE, COMPUTE BY, FOR BROWSE oder INTO enthalten, erforderlich ist. Gehen Sie mit der Cursorbibliothek jedoch sorgfältig um, da sie das gesamte Resultset auf dem Client zwischenspeichert und dadurch viel Speicherplatz belegt und die Leistung beeinträchtigt werden kann.  
  
 Eine Anwendung ruft die Cursor Bibliothek auf Verbindungs Basis mithilfe von [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) auf, um das SQL_ATTR_ODBC_CURSORS Verbindungs Attribut festzulegen, bevor eine Verbindung mit einer Datenquelle hergestellt wird. SQL_ATTR_ODBC_CURSORS wird auf einen von drei Werten festgelegt:  
  
 SQL_CUR_USE_ODBC  
 Wenn diese Option mit dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber festgelegt wird, überschreibt die ODBC-Cursor Bibliothek die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] native Cursor Unterstützung des Native Client-ODBC-Treibers. Für die Verbindung können nur von der Cursorbibliothek unterstützte Cursortypen verwendet werden. Servercursor können nicht verwendet werden.  
  
 SQL_CUR_USE_DRIVER  
 Wenn diese Option festgelegt ist, kann die gesamte Cursor Unterstützung für den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber für die Verbindung verwendet werden. Die ODBC-Cursorbibliothek kann nicht verwendet werden. Alle Cursor werden als Servercursor implementiert.  
  
 SQL_CUR_USE_IF_NEEDED  
 Wenn diese Option festgelegt ist, ist der Effekt identisch mit SQL_CUR_USE_DRIVER, wenn er mit dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber verwendet wird. Zur Verbindungszeit prüft der ODBC-Treiber-Manager, ob der ODBC-Treiber, mit dem eine Verbindung hergestellt wird, die SQL_FETCH_PRIOR-Option von [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)unterstützt. Wenn der Treiber die Option nicht unterstützt, lädt der ODBC-Treiber-Manager die ODBC-Cursorbibliothek. Unterstützt der Treiber die Option, so lädt der ODBC-Treiber-Manager die ODBC-Cursorbibliothek nicht und die Anwendung verwendet die systemeigene Unterstützung des Treibers. Da der ODBC- [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Treiber von Native Client SQL_FETCH_PRIOR unterstützt, lädt der ODBC-Treiber-Manager die ODBC-Cursor Bibliothek nicht.  
  
 Die Cursorbibliothek ermöglicht Anwendungen, mehrere aktive Anwendungen für eine Verbindung sowie bildlauffähige und aktualisierbare Cursor zu verwenden. Die Cursorbibliothek muss geladen sein, damit diese Funktion unterstützt wird. Verwenden Sie [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) , um anzugeben, wie die Cursor Bibliothek verwendet werden soll, und [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) , um den Cursortyp, die Parallelität und die Rowsetgröße anzugeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Implementieren von Cursorn](../../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)  
  
  
