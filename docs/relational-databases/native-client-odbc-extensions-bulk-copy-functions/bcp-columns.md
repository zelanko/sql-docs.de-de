---
description: bcp_columns
title: bcp_columns | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_columns
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_columns function
ms.assetid: 5376f6fe-9508-439a-8c66-778d77f19ac3
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 867ab836c1ab31d1deac348bc63b74e76d1970fe
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97473611"
---
# <a name="bcp_columns"></a>bcp_columns
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Legt die Gesamtanzahl der Spalten fest, die in der Benutzerdatei gefunden wurden und mit einem Massenkopiervorgang in oder aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet werden sollen. [bcp_setbulkmode](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md) können anstelle von bcp_columns und [bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)verwendet werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RETCODE bcp_columns (  
        HDBC hdbc,  
        INT nColumns);  
```  
  
## <a name="arguments"></a>Argumente  
 *hdbc*  
 Das für den Massenkopiervorgang aktivierte ODBC-Verbindungshandle.  
  
 *nColumns*  
 Die Gesamtzahl der Spalten in der Benutzerdatei. Auch wenn Sie das Massen Kopieren von Daten aus der Benutzerdatei in eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle vorbereiten und nicht alle Spalten in der Benutzerdatei kopieren möchten, müssen Sie *nColumns* trotzdem auf die Gesamtzahl der Benutzerdatei Spalten festlegen.  
  
## <a name="returns"></a>Gibt zurück  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion kann erst aufgerufen werden, nachdem [bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) mit einem gültigen Dateinamen aufgerufen wurde.  
  
 Sie sollten diese Funktion nur aufrufen, wenn Sie ein Benutzerdateiformat verwenden möchten, das sich vom Standardformat unterscheidet. Weitere Informationen zu einer Beschreibung des standardmäßigen Benutzerdatei Formats finden Sie unter **bcp_init**.  
  
 Nachdem Sie **bcp_columns** aufgerufen haben, müssen Sie [bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md) für jede Spalte in der Benutzerdatei aufrufen, um ein benutzerdefiniertes Dateiformat vollständig zu definieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bulk Copy Functions](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
