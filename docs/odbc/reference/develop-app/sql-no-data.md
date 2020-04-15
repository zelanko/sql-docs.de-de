---
title: SQL_NO_DATA | Microsoft Docs
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
ms.openlocfilehash: 9a399a270eb1cd2f3daf9449c53b1f577a6b9545
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299790"
---
# <a name="sql_no_data"></a>SQL_NO_DATA
Wenn ein ODBC 3. *x-Anwendung* ruft **SQLExecDirect**, **SQLExecute**oder **SQLParamData** in einem ODBC 2 auf. *x-Treiber,* um eine durchsuchte Aktualisierungs- oder Löschanweisung auszuführen, die keine Zeilen in der Datenquelle betrifft, sollte der Treiber SQL_SUCCESS zurückgeben, nicht SQL_NO_DATA. Wenn ein ODBC 2. *x* oder ODBC 3. *x* Anwendung, die mit einem ODBC 3 arbeitet. *x-Treiber* ruft **SQLExecDirect**, **SQLExecute**oder **SQLParamData** mit dem gleichen Ergebnis auf, odBC 3. *x-Treiber* sollte SQL_NO_DATA zurückgeben.
