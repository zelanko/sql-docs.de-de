---
title: Sqlremovedefaultdatasource-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRemoveDefaultDataSource
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDefaultDataSource
helpviewer_keywords:
- SQLRemoveDefaultDataSource function [ODBC]
ms.assetid: db803266-57df-4864-a41b-901247549c1f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 952ace7d17e8bb5b4c824761b02e5c8a0895f519
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303941"
---
# <a name="sqlremovedefaultdatasource-function"></a>SQLRemoveDefaultDataSource-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0, veraltet  
  
 **Zusammenfassung**  
 In ODBC 3,0 wurde die **sqlremovedefaultdatasource** -Funktion durch einen-Befehl von [SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md) mit einem *fRequest* -Argument ODBC_REMOVE_DEFAULT_DSN ersetzt. Wenn diese Funktion von einem ODBC 2 *. x* -Installationsprogramm aufgerufen wird, ordnet das ODBC-Installationsprogramm es folgendem **SQLConfigDataSource** -Aufruf zu:  
  
```cpp  
SQLConfigDataSource (NULL, ODBC_REMOVE_DEFAULT_DSN, NULL, NULL)  
```
