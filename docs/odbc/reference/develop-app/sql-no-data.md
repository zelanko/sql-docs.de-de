---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1f899e7a034e1ec5fc967d834caad3a4ccc4caa1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68041830"
---
# <a name="sql_no_data"></a>SQL_NO_DATA
Bei ODBC 3. die *x* -Anwendung ruft **SQLExecDirect**, **SQLExecute**oder **SQLParamData** in einem ODBC 2 auf. *x* -Treiber um eine gesuchte Update-oder DELETE-Anweisung auszuführen, die keine Zeilen in der Datenquelle beeinflusst, sollte der Treiber SQL_SUCCESS und nicht SQL_NO_DATA zurückgeben. Bei ODBC 2. *x* oder ODBC 3. *x* -Anwendung, die mit ODBC 3 arbeitet. der *x* -Treiber ruft **SQLExecDirect**, **SQLExecute**oder **SQLParamData** mit dem gleichen Ergebnis (ODBC 3) auf. der *x* -Treiber sollte SQL_NO_DATA zurückgeben.
