---
description: SQL_NO_DATA
title: SQL_NO_DATA | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL_NO_DATA [ODBC]
- application upgrades [ODBC], SQL_NO_DATA
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
- upgrading applications [ODBC], SQL_NO_DATA
ms.assetid: 07a4144a-a548-4578-b2be-715c3cf73bf8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: eb81d6f1fce50a27aba203eec4b78648754010e5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424572"
---
# <a name="sql_no_data"></a>SQL_NO_DATA
Bei ODBC 3. die *x* -Anwendung ruft **SQLExecDirect**, **SQLExecute**oder **SQLParamData** in einem ODBC 2 auf. *x* -Treiber um eine gesuchte Update-oder DELETE-Anweisung auszuführen, die keine Zeilen in der Datenquelle beeinflusst, sollte der Treiber SQL_SUCCESS und nicht SQL_NO_DATA zurückgeben. Bei ODBC 2. *x* oder ODBC 3. *x* -Anwendung, die mit ODBC 3 arbeitet. der *x* -Treiber ruft **SQLExecDirect**, **SQLExecute**oder **SQLParamData** mit dem gleichen Ergebnis (ODBC 3) auf. der *x* -Treiber sollte SQL_NO_DATA zurückgeben.
