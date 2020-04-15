---
title: Überschreiben der Standardgenauigkeit und Skalierung für numerische Datentypen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- numeric data type [ODBC], precision and scale
- precision [ODBC], numeric data types
- data types [ODBC], numeric data types
- numeric data type [ODBC]
- numeric literals [ODBC]
ms.assetid: 84292334-0e33-4a1b-84de-8c018dd787f3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 365c5f69d21dd3a4ad8e89805d81f1b3b0c9dcba
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303591"
---
# <a name="overriding-default-precision-and-scale-for-numeric-data-types"></a>Überschreiben der Standardwerte für die Genauigkeit des führenden Intervallfelds und die Dezimalstellenanzahl für numerische Datentypen
Wenn das SQL_DESC_TYPE Feld in einer ARD auf SQL_C_NUMERIC festgelegt ist, wird durch Aufrufen von **SQLBindCol** oder **SQLSetDescField**das SQL_DESC_SCALE Feld in der ARD auf 0 und das Feld SQL_DESC_PRECISION auf eine treiberdefinierte Standardgenauigkeit festgelegt. Dies gilt auch, wenn das feld SQL_DESC_TYPE in einer APD auf SQL_C_NUMERIC festgelegt ist, indem entweder **SQLBindParameter** oder **SQLSetDescField**aufgerufen wird. Dies gilt für Eingabe-, Ein-/Ausgabe- oder Ausgabeparameter.  
  
 Wenn eine der zuvor beschriebenen Standardeinstellungen für eine Anwendung nicht akzeptabel ist, sollte die Anwendung das Feld SQL_DESC_SCALE oder SQL_DESC_PRECISION festlegen, indem sie **SQLSetDescField** oder **SQLSetDescRec**aufruft.  
  
 Wenn die Anwendung **SQLGetData** aufruft, um Daten in eine SQL_C_NUMERIC-Struktur zurückzugeben, werden die standardmäßigen SQL_DESC_SCALE- und SQL_DESC_PRECISION-Felder verwendet. Wenn die Standardwerte nicht akzeptabel sind, muss die Anwendung **SQLSetDescRec** oder **SQLSetDescField** aufrufen, um die Felder festzulegen, und dann **SQLGetData** mit einem *TargetType* von SQL_ARD_TYPE aufrufen, um die Werte in den Deskriptorfeldern zu verwenden.  
  
 Wenn **SQLPutData** aufgerufen wird, verwendet der Aufruf die SQL_DESC_SCALE und SQL_DESC_PRECISION Felder des Deskriptordatensatzes, die dem Data-at-Execution-Parameter oder der Spalte entsprechen, d. h. APD-Felder für Aufrufe von **SQLExecute** oder **SQLExecDirect**oder ARD-Felder für Aufrufe von **SQLBulkOperations** oder **SQLSetPos**.
