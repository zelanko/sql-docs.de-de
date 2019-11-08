---
title: SQLFreeHandle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLFreeHandle function
ms.assetid: d374e5c8-ed35-43bf-8dd6-c37e38d9b5f1
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2320ec5059535702d8fb203b32a316b49821b20c
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73786844"
---
# <a name="sqlfreehandle"></a>SQLFreeHandle
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Im Manualcommit-Modus führt das Aufrufen von **SQLFreeHandle** für ein Anweisungshandle mit einer offenen Transaktion zu einem Rollback ausstehender Änderungen an der Datenbank. Durch das Aufrufen von **SQLFreeHandle** für ein Anweisungshandle werden immer alle geöffneten Cursor geschlossen und ausstehende Ergebnisse verworfen. Auf diese Weise werden alle zum Anweisungshandle gehörenden Ressourcen freigegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLFreeHandle-Funktion](https://go.microsoft.com/fwlink/?LinkId=59345)   
 [ODBC-API-Implementierungsdetails](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
