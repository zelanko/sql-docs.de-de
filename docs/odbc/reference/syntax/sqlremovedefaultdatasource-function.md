---
title: SQLRemoveDefaultDataSource-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 90270f119b351592348287823c2b9d879a15154b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63262238"
---
# <a name="sqlremovedefaultdatasource-function"></a>SQLRemoveDefaultDataSource-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 1.0, als veraltet markiert  
  
 **Zusammenfassung**  
 In ODBC 3.0 die **SQLRemoveDefaultDataSource** Funktion wurde durch einen Aufruf von ersetzt [SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md) mit einer *häufigsten* ODBC_REMOVE_DEFAULT_DSN Argument. Wenn eine ODBC 2.*.x* Installationsprogramm ruft diese Funktion, des ODBC-Installationsprogramms ordnen sie die folgenden **SQLConfigDataSource** aufrufen:  
  
```  
SQLConfigDataSource (NULL, ODBC_REMOVE_DEFAULT_DSN, NULL, NULL)  
```
