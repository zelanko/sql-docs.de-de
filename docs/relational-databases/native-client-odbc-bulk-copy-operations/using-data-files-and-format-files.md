---
title: Verwenden von Datendateien und Format Dateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], file formats
- ODBC, functions
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [SQL Server Native Client]
- ODBC, bulk copy operations
- bulk copy [ODBC], data files
ms.assetid: c01b7155-3f0a-473d-90b7-87a97bc56ca5
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e7cf91baeb6771f0abb52fb5b8f4c4dc2bddafe0
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73785281"
---
# <a name="using-data-files-and-format-files"></a>Verwenden von Datendateien und Formatdateien
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Das einfachste Massenkopierprogramm geht wie folgt vor:  
  
1.  Ruft [bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) auf, um das Massen kopieren (BCP_OUT) aus einer Tabelle oder Sicht in eine Datendatei anzugeben.  
  
2.  Ruft [bcp_exec](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) auf, um den Massen Kopiervorgang auszuführen.  
  
 Die Datendatei wird im einheitlichen Modus erstellt. Daher werden Daten aus allen Spalten in der Tabelle oder Sicht in der Datendatei im gleichen Format wie in der Datenbank gespeichert. Die Datei kann dann mit derselben Vorgehensweise auf einen Server massenkopiert werden, mit der Ausnahme, dass DB_IN statt DB_OUT festgelegt wird. Dies funktioniert jedoch nur, wenn sowohl die Quell- als auch die Zieltabellen genau dieselbe Struktur aufweisen. Die resultierende Datendatei kann auch mit dem Schalter **/n** (einheitlicher Modus) als Eingabe für das **bcp** -Hilfsprogramm verwendet werden.  
  
 So führen Sie einen Massenkopiervorgang des Resultsets einer [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung aus, anstatt direkt aus einer Tabelle oder Sicht zu kopieren:  
  
1.  Ruft **bcp_init** auf, um das Massen kopieren anzugeben, aber geben Sie NULL für den Tabellennamen an.  
  
2.  Ruft [bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) auf, bei dem *eOption* auf BCPHINTS festgelegt und *iValue* auf einen Zeiger auf eine SQLTCHAR-Zeichenfolge festgelegt ist, die die Transact-SQL-Anweisung enthält.  
  
3.  Rufen Sie **bcp_exec** auf, um den Massenkopiervorgang auszuführen.  

 Die [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung kann jede Anweisung sein, die ein Resultset generiert. Die Datendatei wird mit dem ersten Resultset der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung erstellt. Beim Massenkopieren wird jedes Resultset nach dem ersten ignoriert, wenn die [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung mehrere Resultsets generiert.  
  
 Wenn Sie eine Datendatei erstellen möchten, in der Spaltendaten in einem anderen Format als in der Tabelle gespeichert werden, rufen Sie [bcp_columns](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md) auf, um anzugeben, wie viele Spalten geändert werden, und rufen Sie dann [bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md) für jede Spalte auf, deren Format Sie ändern möchten. Dies erfolgt nach dem Aufrufen von **bcp_init** , aber vor dem Aufrufen von **bcp_exec**. **bcp_colfmt** gibt das Format an, in dem die Daten der Spalte in der Datendatei gespeichert werden. Sie kann verwendet werden, wenn ein Massen Kopiervorgang oder ein Massen Kopiervorgang durch Sie können **bcp_colfmt** auch zum Festlegen der Zeilen-und Spalten Terminatoren verwenden. Wenn die Daten z. b. keine Tabulator Zeichen enthalten, können Sie eine durch Tabstopps getrennte Datei erstellen, indem Sie **bcp_colfmt** verwenden, um das Tabstopp Zeichen als Abschluss Zeichen für die einzelnen Spalten festzulegen.  
  
 Beim Massen kopieren und Verwenden von **bcp_colfmt**können Sie auf einfache Weise eine Format Datei erstellen, die die erstellte Datendatei beschreibt, indem Sie [bcp_writefmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md) nach dem letzten Aufruf von **bcp_colfmt**aufrufen.  
  
 Beim Massen kopieren aus einer Datendatei, die von einer Format Datei beschrieben wird, lesen Sie die Format Datei, indem Sie [bcp_readfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md) nach **bcp_init** , aber vor **bcp_exec**aufrufen.  
  
 Die **bcp_control** -Funktion steuert mehrere Optionen beim Massen Kopieren in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aus einer Datendatei. **bcp_control** legt Optionen fest, z. b. die maximale Anzahl von Fehlern vor dem Beenden, die Zeile in der Datei, in der der Massen Kopiervorgang gestartet werden soll, die Zeile, für die der Vorgang beendet werden soll, und die Batch Größe.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Massen Kopier &#40;Vorgängen (ODBC)&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
