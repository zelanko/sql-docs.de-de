---
description: Überschreiben der Standardwerte für die Genauigkeit des führenden Intervallfelds und die Dezimalstellenanzahl für numerische Datentypen
title: Überschreiben der Standardgenauigkeit und-Skalierung für numerische Datentypen | Microsoft-Dokumentation
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
ms.openlocfilehash: 798e607ff6584bde27791a29e4b20aeb1d7bb3cf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466082"
---
# <a name="overriding-default-precision-and-scale-for-numeric-data-types"></a>Überschreiben der Standardwerte für die Genauigkeit des führenden Intervallfelds und die Dezimalstellenanzahl für numerische Datentypen
Wenn das SQL_DESC_TYPE-Feld in einer ARD auf SQL_C_NUMERIC festgelegt wird, indem entweder **SQLBindCol** oder **SQLSetDescField**aufgerufen wird, wird das Feld SQL_DESC_SCALE in der ARD auf 0 festgelegt, und das SQL_DESC_PRECISION Feld wird auf eine vom Treiber definierte Standardgenauigkeit festgelegt. Dies gilt auch, wenn das SQL_DESC_TYPE-Feld in einer APD auf SQL_C_NUMERIC festgelegt ist, indem entweder **SQLBindParameter** oder **SQLSetDescField**aufgerufen wird. Dies gilt für Eingabe-, Eingabe-/Ausgabe-oder Ausgabeparameter.  
  
 Wenn eine der zuvor beschriebenen Standardwerte für eine Anwendung nicht zulässig ist, sollte die Anwendung die SQL_DESC_SCALE oder SQL_DESC_PRECISION Feld durch Aufrufen von **SQLSetDescField** oder **SQLSetDescRec**festlegen.  
  
 Wenn die Anwendung **SQLGetData** aufruft, um Daten in eine SQL_C_NUMERIC Struktur zurückzugeben, werden die Standard Felder SQL_DESC_SCALE und SQL_DESC_PRECISION verwendet. Wenn die Standardwerte nicht zulässig sind, muss die Anwendung **SQLSetDescRec** oder **SQLSetDescField** aufrufen, um die Felder festzulegen, und dann **SQLGetData** mit einem *TargetType* SQL_ARD_TYPE aufrufen, um die Werte in den Deskriptorfeldern zu verwenden.  
  
 Wenn **SQLPutData** aufgerufen wird, verwendet der Aufruf die Felder SQL_DESC_SCALE und SQL_DESC_PRECISION des deskriptordaten Satzes, die dem Data-at-Execution-Parameter bzw. der-Spalte entsprechen. Dies sind APD-Felder für Aufrufe von **SQLExecute** oder **SQLExecDirect**oder für Aufrufe von **SQLBulkOperations** oder **SQLSetPos**.
