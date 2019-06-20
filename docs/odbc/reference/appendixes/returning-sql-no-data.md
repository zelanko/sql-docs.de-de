---
title: Rückgabe von SQL_NO_DATA | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 74c122819980abaa328db5ad46f240cae24b92d3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63280590"
---
# <a name="returning-sqlnodata"></a>Rückgabe von SQL_NO_DATA
Wenn eine ODBC-2. *x* Anwendung arbeiten, eine ODBC 3. *.x* Treiber ruft **SQLExecDirect**, **SQLExecute**, oder **der SQLParamData**, und ein gesuchtes Update oder Delete-Anweisung wurde ausgeführt, aber keine Auswirkungen auf die Zeilen in der Datenquelle, die ODBC 3. *.x* Treiber sollte SQL_SUCCESS zurück. Wenn eine ODBC 3. *.x* Anwendung mit einer ODBC 3. *.x* Treiber ruft **SQLExecDirect**, **SQLExecute**, oder  **SQLParamData** dasselbe Ergebnis erzielt, die ODBC 3. *.x* Treiber sollte SQL_NO_DATA zurückgegeben werden.  
  
 Wenn eine gesuchte update oder-Anweisung in DELETE ein Batch von Anweisungen hat keine Auswirkungen auf alle Zeilen in der Datenquelle **SQLMoreResults** gibt SQL_SUCCESS zurück. Es kann keine SQL_NO_DATA, zurückgeben, da dieser Wert bedeuten würde, dass es sind keine weiteren Ergebnisse, nicht, die es ein Ergebnis aus einer komplexen aktualisieren/löschen, die keine Zeilen betroffen.
