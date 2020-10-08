---
description: SQLForeignKeys
title: Sqlfremdnkeys | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLForeignKeys function
ms.assetid: 6c01ce0d-30d7-4c86-8705-3ab254d8a845
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6af061afe5d05b03f4b36c71ea2c222efe8e8e08
ms.sourcegitcommit: 32135463a8494d9ed1600a58f51819359e3c09dc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/08/2020
ms.locfileid: "91809561"
---
# <a name="sqlforeignkeys"></a>SQLForeignKeys
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt Updateweitergaben und Löschungen über den Fremdschlüsseleinschränkungsmechanismus. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt SQL_CASCADE für UPDATE_RULE- und/oder DELETE_RULE-Spalten zurück, wenn die CASCADE-Option in der ON UPDATE-Klausel und/oder der ON DELETE-Klausel der FOREIGN KEY-Einschränkungen angegeben wird. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt SQL_NO_ACTION für UPDATE_RULE- und/oder DELETE_RULE-Spalten zurück, wenn die NO ACTION-Option in der ON UPDATE-Klausel und/oder der ON DELETE-Klausel der FOREIGN KEY-Einschränkungen angegeben wird.  
  
 Wenn in einem beliebigen **SQLForeignKeys** -Parameter ungültige Werte vorhanden sind, gibt **SQLForeignKeys** bei der Ausführung SQL_SUCCESS zurück. **SQLFetch** gibt SQL_NO_DATA zurück, wenn in diesen Parametern ungültige Werte verwendet werden.  
  
 **SQLForeignKeys** kann in einem statischen Servercursor ausgeführt werden. Wenn **SQLForeignKeys** in einem aktualisierbaren Cursor (dynamischer Cursor oder Keysetcursor) ausgeführt wird, wird SQL_SUCCESS_WITH_INFO zurückgegeben. Das bedeutet, dass der Cursortyp geändert wurde.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt die Meldung von Informationen für Tabellen auf Verbindungsservern, indem er einen zweiteiligen Namen für die Parameter *FKCatalogName* und *PKCatalogName* akzeptiert: *Linked_Server_Name.Catalog_Name*.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sqlfremdnkeys-Funktion](../../odbc/reference/syntax/sqlforeignkeys-function.md)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
