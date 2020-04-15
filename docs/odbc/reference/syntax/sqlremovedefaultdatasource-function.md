---
title: SQLRemoveDefaultDataSource-Funktion | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303941"
---
# <a name="sqlremovedefaultdatasource-function"></a>SQLRemoveDefaultDataSource-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0, Veraltet  
  
 **Zusammenfassung**  
 In ODBC 3.0 wurde die **SQLRemoveDefaultDataSource-Funktion** durch einen Aufruf von [SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md) mit dem *fRequest-Argument* von ODBC_REMOVE_DEFAULT_DSN ersetzt. Wenn ein ODBC 2 *.x-Installationsprogramm* diese Funktion aufruft, wird sie vom ODBC-Installationsprogramm dem folgenden **SQLConfigDataSource-Aufruf** zugeordnet:  
  
```cpp  
SQLConfigDataSource (NULL, ODBC_REMOVE_DEFAULT_DSN, NULL, NULL)  
```
