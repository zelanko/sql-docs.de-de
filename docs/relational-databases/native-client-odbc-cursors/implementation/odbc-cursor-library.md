---
title: ODBC Cursor Bibliothek | Microsoft Docs
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
ms.openlocfilehash: 93c85bc943d1a6a081cbea6bbeae40ba85aeffc5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305394"
---
# <a name="odbc-cursor-library"></a>ODBC-Cursorbibliothek
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Einige ODBC-Treiber unterstützen nur die Standardcursoreinstellungen. Diese Treiber unterstützen auch keine positionierten Cursoroperationen, z. B. **SQLSetPos**. Die ODBC-Cursorbibliothek ist eine Komponente von Microsoft Data Access Components (MDAC), mit der Block- oder statische Cursor in einem Treiber implementiert werden, der sie normalerweise nicht unterstützt. Die Cursorbibliothek implementiert auch positionierte UPDATE- und DELETE-Anweisungen sowie **SQLSetPos** für die Cursor, die sie erstellt.  
  
 Die ODBC-Cursorbibliothek wird als Ebene zwischen dem ODBC-Treiber-Manager und einem ODBC-Treiber implementiert. Wenn die ODBC-Cursorbibliothek geladen ist, leitet der ODBC-Treiber-Manager alle cursorspezifischen Befehle an die Cursorbibliothek statt an den Treiber weiter. Die Cursorbibliothek implementiert einen Cursor durch Abrufen des gesamten Resultsets aus dem zugrunde liegenden Treiber und durch Zwischenspeichern des Resultsets auf dem Client. Bei Verwendung der ODBC-Cursorbibliothek ist die Anwendung auf die Cursorfunktionen der Cursorbibliothek beschränkt. Zusätzliche Cursorfunktionen im zugrunde liegenden Treiber sind für die Anwendung nicht verfügbar.  
  
 Es besteht kaum Bedarf, die ODBC-Cursorbibliothek mit dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber zu verwenden, da der Treiber selbst mehr Cursorfunktionen unterstützt als die ODBC-Cursorbibliothek. Der einzige Grund, die ODBC-Cursorbibliothek mit dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber zu verwenden, liegt darin, dass der Treiber seine Cursorunterstützung über Servercursor implementiert und Servercursor nicht alle SQL-Anweisungen unterstützen. Erwägen Sie die Verwendung der ODBC-Cursorbibliothek, wenn ein statischer Cursor mit gespeicherten Prozeduren, Batches oder SLQ-Anweisungen, die COMPUTE, COMPUTE BY, FOR BROWSE oder INTO enthalten, erforderlich ist. Gehen Sie mit der Cursorbibliothek jedoch sorgfältig um, da sie das gesamte Resultset auf dem Client zwischenspeichert und dadurch viel Speicherplatz belegt und die Leistung beeinträchtigt werden kann.  
  
 Eine Anwendung ruft die Cursorbibliothek auf Verbindungsbasis auf Basis von [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) auf, um das SQL_ATTR_ODBC_CURSORS Verbindungsattribut festzulegen, bevor eine Verbindung mit einer Datenquelle hergestellt wird. SQL_ATTR_ODBC_CURSORS wird auf einen von drei Werten festgelegt:  
  
 SQL_CUR_USE_ODBC  
 Wenn diese Option mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dem Native Client ODBC-Treiber festgelegt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ist, überschreibt die ODBC-Cursorbibliothek die unterstützung des nativen Client ODBC-Treibers. Für die Verbindung können nur von der Cursorbibliothek unterstützte Cursortypen verwendet werden. Servercursor können nicht verwendet werden.  
  
 SQL_CUR_USE_DRIVER  
 Wenn diese Option festgelegt ist, kann die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gesamte Cursorunterstützung, die für den ODBC-Treiber nativer Client systemistiert ist, für die Verbindung verwendet werden. Die ODBC-Cursorbibliothek kann nicht verwendet werden. Alle Cursor werden als Servercursor implementiert.  
  
 SQL_CUR_USE_IF_NEEDED  
 Wenn diese Option festgelegt ist, entspricht der Effekt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SQL_CUR_USE_DRIVER, wenn er mit dem Native Client ODBC-Treiber verwendet wird. Zur Verbindungszeit testet der ODBC-Treiber-Manager, ob der ODBC-Treiber, mit dem verbunden ist, die SQL_FETCH_PRIOR-Option von [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)unterstützt. Wenn der Treiber die Option nicht unterstützt, lädt der ODBC-Treiber-Manager die ODBC-Cursorbibliothek. Unterstützt der Treiber die Option, so lädt der ODBC-Treiber-Manager die ODBC-Cursorbibliothek nicht und die Anwendung verwendet die systemeigene Unterstützung des Treibers. Da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] der Native Client ODBC-Treiber SQL_FETCH_PRIOR unterstützt, lädt der ODBC-Treiber-Manager die ODBC-Cursorbibliothek nicht.  
  
 Die Cursorbibliothek ermöglicht Anwendungen, mehrere aktive Anwendungen für eine Verbindung sowie bildlauffähige und aktualisierbare Cursor zu verwenden. Die Cursorbibliothek muss geladen sein, damit diese Funktion unterstützt wird. Verwenden Sie [SQLSetConnectAttr,](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) um anzugeben, wie die Cursorbibliothek verwendet werden soll, und [SQLSetStmtAttr,](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) um den Cursortyp, die Parallelität und die Rowsetgröße anzugeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Implementieren von Cursorn](../../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)  
  
  
