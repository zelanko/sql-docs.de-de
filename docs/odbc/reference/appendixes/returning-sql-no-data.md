---
title: Rückgabe SQL_NO_DATA | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL_NO_DATA [ODBC]
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
ms.assetid: deed0163-9d1a-4e9b-9342-3f82e64477d2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3e2c806edd5d5647e09c00975ad7207ee5c2c876
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305111"
---
# <a name="returning-sql_no_data"></a>Rückgabe von SQL_NO_DATA
Wenn eine ODBC *2.x-Anwendung,* die mit einem ODBC *3.x-Treiber* arbeitet, **SQLExecDirect**, **SQLExecute**oder **SQLParamData**aufruft und eine suchte Aktualisierungs- oder Löschanweisung ausgeführt wurde, aber keine Zeilen in der Datenquelle beeinflusst hat, sollte der ODBC *3.x-Treiber* SQL_SUCCESS zurückgeben. Wenn eine ODBC *3.x-Anwendung,* die mit einem ODBC *3.x-Treiber* arbeitet, **SQLExecDirect**, **SQLExecute**oder **SQLParamData** mit demselben Ergebnis aufruft, sollte der ODBC *3.x-Treiber* SQL_NO_DATA zurückgeben.  
  
 Wenn sich eine durchsuchte Aktualisierungs- oder Löschanweisung in einem Batch von Anweisungen nicht auf Zeilen in der Datenquelle auswirkt, gibt **SQLMoreResults** SQL_SUCCESS zurück. Sie kann SQL_NO_DATA nicht zurückgeben, da dies bedeuten würde, dass es keine weiteren Ergebnisse gibt, nicht dass ein Ergebnis einer durchsuchten Aktualisierung/Löschung entsteht, die keine Zeilen betrifft.
