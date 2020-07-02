---
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
ms.openlocfilehash: b54af78e0156e85c872f5f487e06ef76b64a98d9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85789242"
---
# <a name="sqlforeignkeys"></a>SQLForeignKeys
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt Updateweitergaben und Löschungen über den Fremdschlüsseleinschränkungsmechanismus. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt SQL_CASCADE für UPDATE_RULE- und/oder DELETE_RULE-Spalten zurück, wenn die CASCADE-Option in der ON UPDATE-Klausel und/oder der ON DELETE-Klausel der FOREIGN KEY-Einschränkungen angegeben wird. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt SQL_NO_ACTION für UPDATE_RULE- und/oder DELETE_RULE-Spalten zurück, wenn die NO ACTION-Option in der ON UPDATE-Klausel und/oder der ON DELETE-Klausel der FOREIGN KEY-Einschränkungen angegeben wird.  
  
 Wenn in einem beliebigen **SQLForeignKeys** -Parameter ungültige Werte vorhanden sind, gibt **SQLForeignKeys** bei der Ausführung SQL_SUCCESS zurück. **SQLFetch** gibt SQL_NO_DATA zurück, wenn in diesen Parametern ungültige Werte verwendet werden.  
  
 **SQLForeignKeys** kann in einem statischen Servercursor ausgeführt werden. Wenn **SQLForeignKeys** in einem aktualisierbaren Cursor (dynamischer Cursor oder Keysetcursor) ausgeführt wird, wird SQL_SUCCESS_WITH_INFO zurückgegeben. Das bedeutet, dass der Cursortyp geändert wurde.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt die Meldung von Informationen für Tabellen auf Verbindungsservern, indem er einen zweiteiligen Namen für die Parameter *FKCatalogName* und *PKCatalogName* akzeptiert: *Linked_Server_Name.Catalog_Name*.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sqlfremdnkeys-Funktion](https://go.microsoft.com/fwlink/?LinkId=59344)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
