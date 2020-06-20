---
title: Sqlfremdnkeys | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLForeignKeys function
ms.assetid: 6c01ce0d-30d7-4c86-8705-3ab254d8a845
author: rothja
ms.author: jroth
ms.openlocfilehash: a61e80867abb8ecb4d2628b74dc9956051c8e4ce
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85022392"
---
# <a name="sqlforeignkeys"></a>SQLForeignKeys
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt Updateweitergaben und Löschungen über den Fremdschlüsseleinschränkungsmechanismus. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt SQL_CASCADE für UPDATE_RULE- und/oder DELETE_RULE-Spalten zurück, wenn die CASCADE-Option in der ON UPDATE-Klausel und/oder der ON DELETE-Klausel der FOREIGN KEY-Einschränkungen angegeben wird. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt SQL_NO_ACTION für UPDATE_RULE- und/oder DELETE_RULE-Spalten zurück, wenn die NO ACTION-Option in der ON UPDATE-Klausel und/oder der ON DELETE-Klausel der FOREIGN KEY-Einschränkungen angegeben wird.  
  
 Wenn in einem beliebigen **SQLForeignKeys** -Parameter ungültige Werte vorhanden sind, gibt **SQLForeignKeys** bei der Ausführung SQL_SUCCESS zurück. **SQLFetch** gibt SQL_NO_DATA zurück, wenn in diesen Parametern ungültige Werte verwendet werden.  
  
 **SQLForeignKeys** kann in einem statischen Servercursor ausgeführt werden. Wenn **SQLForeignKeys** in einem aktualisierbaren Cursor (dynamischer Cursor oder Keysetcursor) ausgeführt wird, wird SQL_SUCCESS_WITH_INFO zurückgegeben. Das bedeutet, dass der Cursortyp geändert wurde.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt die Meldung von Informationen für Tabellen auf Verbindungsservern, indem er einen zweiteiligen Namen für die Parameter *FKCatalogName* und *PKCatalogName* akzeptiert: *Linked_Server_Name.Catalog_Name*.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sqlfremdnkeys-Funktion](https://go.microsoft.com/fwlink/?LinkId=59344)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
