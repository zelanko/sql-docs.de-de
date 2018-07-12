---
title: Massenkopierfunktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], functions
- ODBC, bulk copy operations
- functions [ODBC]
ms.assetid: 6526b892-1d58-4f55-8335-f09887f6ea02
caps.latest.revision: 39
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bab3c80749bc7fedb721e7f0a8d776c98a3f312d
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425889"
---
# <a name="bulk-copy-functions"></a>Bulk Copy Functions
  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-spezifische API-Erweiterung für Massenkopierfunktionen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treibers ermöglicht es Clientanwendungen, einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle auf schnelle Weise Datenzeilen hinzuzufügen bzw. Datenzeilen aus einer Tabelle zu extrahieren.  
  
 Bei der Verwendung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client können Sie die Massenkopierfunktionen (BCP) in SQLNCLI11.LIB und SQLNCLI.H nutzen.  
  
 Eine Anwendung, die BCP-API-Funktionsaufrufe verwendet, sollte mit der Bibliothek (LIB-Datei) verknüpft werden, die mit dem von der Anwendung verwendeten Treiber (DLL-Datei) geliefert wurde. Eine BCP-Anwendung sollte nicht mit mehr als einer Treiberbibliothek verknüpft werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [bcp_batch](bcp-batch.md)  
  
-   [bcp_bind](bcp-bind.md)  
  
-   [bcp_colfmt](bcp-colfmt.md)  
  
-   [bcp_collen](bcp-collen.md)  
  
-   [bcp_colptr](bcp-colptr.md)  
  
-   [bcp_columns](bcp-columns.md)  
  
-   [bcp_control](bcp-control.md)  
  
-   [bcp_done](bcp-done.md)  
  
-   [bcp_exec](bcp-exec.md)  
  
-   [bcp_getcolfmt](bcp-getcolfmt.md)  
  
-   [bcp_gettypename](bcp-gettypename.md)  
  
-   [bcp_init](bcp-init.md)  
  
-   [bcp_moretext](bcp-moretext.md)  
  
-   [bcp_readfmt](bcp-readfmt.md)  
  
-   [bcp_sendrow](bcp-sendrow.md)  
  
-   [bcp_setbulkmode](bcp-setbulkmode.md)  
  
-   [bcp_setcolfmt](bcp-setcolfmt.md)  
  
-   [bcp_writefmt](bcp-writefmt.md)  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Treibererweiterungen](../../database-engine/dev-guide/sql-server-driver-extensions.md)   
 [Durchführen von Massenkopiervorgängen &#40;ODBC&#41;](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
