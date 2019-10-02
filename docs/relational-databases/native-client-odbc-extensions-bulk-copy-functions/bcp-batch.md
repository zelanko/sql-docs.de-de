---
title: bcp_batch | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_batch
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_batch function
ms.assetid: 0bda489e-86bc-4a7e-80f6-96047e03f281
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d1dd7b42ba6fcf4ea5b45fb779d4e6c67cd3074a
ms.sourcegitcommit: 8732161f26a93de3aa1fb13495e8a6a71519c155
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2019
ms.locfileid: "71707719"
---
# <a name="bcp_batch"></a>bcp_batch
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Führt einen Commit für alle zuvor aus Programmvariablen massenkopierten Zeilen aus, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bcp_sendrow [an](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)gesendet wurden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DBINT bcp_batch (HDBC  
        hdbc);  
```  
  
## <a name="arguments"></a>Argumente  
 *hdbc*  
 Das für den Massenkopiervorgang aktivierte ODBC-Verbindungshandle.  
  
## <a name="returns"></a>Rückgabewert  
 Die Anzahl von Zeilen, die nach dem letzten Aufruf von **bcp_batch**gespeichert wurden, oder -1 im Fall eines Fehlers.  
  
## <a name="remarks"></a>Hinweise  
 Batches von Massenkopiervorgängen stellen Transaktionen dar. Wenn eine Anwendung mit [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) und **bcp_sendrow** Zeilen von Programmvariablen in SQL-Server-Tabellen massenkopiert, wird für die Zeilen nur dann ein Commit durchgeführt, wenn das Programm **bcp_batch** oder [bcp_done](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md)aufruft.  
  
 Sie können **bcp_batch** einmal für jede *n* Zeilen aufrufen oder dann, wenn bei den eingehenden Daten eine Pause auftritt (wie in einer Telemetrieanwendung). Wenn eine Anwendung **bcp_batch** nicht aufruft, wird nur dann ein Commit für die massenkopierten Zeilen ausgeführt, wenn **bcp_done** aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Massenkopierfunktionen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
