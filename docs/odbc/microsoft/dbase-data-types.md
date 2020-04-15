---
title: dBASE-Datentypen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], DBasedriver
- desktop database drivers [ODBC], DBasedriver
- DBase driver [ODBC], data types
- data types [ODBC], DBase driver
- dbase data types [ODBC]
- ODBC desktop database drivers [ODBC], DBasedriver
ms.assetid: a0e31e6b-d02b-4ee2-9b37-5baf6a11c0a6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 17b96ad0b6674a2d120ef46d9bfa221e8df6d140
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307691"
---
# <a name="dbase-data-types"></a>dBASE-Datentypen
Die folgende Tabelle zeigt, wie dBASE-Datentypen ODBC SQL-Datentypen zugeordnet werden. Beachten Sie, dass nicht alle ODBC SQL-Datentypen unterstützt werden.  
  
|dBASE-Datentyp|ODBC-Datentyp|  
|---------------------|--------------------|  
|CHAR|SQL_VARCHAR|  
|DATE|SQL_DATE|  
|FLOAT[1]|SQL_DOUBLE|  
|Logische|SQL_BIT|  
|Memo|SQL_LONGVARCHAR|  
|NUMERIC (BCD)|SQL_DOUBLE|  
|OLEOBJECT[1]|SQL_LONGBINARY|  
  
 [1] Gültig nur für dBASE Version 5. *x*  
  
 Die Präzision in dBASE III ermöglicht Zahlen mit bis zu zweistelligen Exponenten und in dBASE IV-Nummern mit bis zu dreistelligen Exponenten. Da Zahlen als Text gespeichert werden, werden sie in Zahlen konvertiert. Wenn die zu konvertierende Zahl nicht in ein Feld passt, können unerklärliche Ergebnisse auftreten.  
  
 Während dBASE die Angabe einer Genauigkeit und einer Skalierung mit einem NUMERIC-Datentyp ermöglicht, wird sie vom ODBC dBASE-Treiber nicht unterstützt. Der ODBC dBASE-Treiber gibt immer eine Genauigkeit von 15 und eine Skala von 0 für einen NUMERIC-Datentyp zurück.  
  
 Eine Spalte, die mit dem Datentyp Numeric erstellt wurde, der den ODBC dBASE-Treiber verwendet, ordnet dem SQL_DOUBLE ODBC-Datentyps zu. Somit unterliegen die Daten in dieser Spalte einer Rundung. Dieses Verhalten entspricht nicht dem des NUMERIC-Datentyps in dBASE (Typ N), der Binary Coded Decimal (BCD) ist.  
  
> [!NOTE]  
>  **SQLGetTypeInfo** gibt ODBC SQL-Datentypen zurück. Alle Konvertierungen in Anhang D der *ODBC-Programmierreferenz* werden für die ODBC SQL-Datentypen unterstützt, die weiter oben in diesem Thema aufgeführt sind.  
  
 Die folgende Tabelle zeigt Einschränkungen für dBASE-Datentypen.  
  
|Datentyp|BESCHREIBUNG|  
|---------------|-----------------|  
|CHAR|Beim Erstellen einer CHAR-Spalte mit null oder nicht angegebener Länge wird tatsächlich eine 254-Byte-Spalte zurückgegeben.|  
|Verschlüsselte Daten|Der dBASE-Treiber unterstützt keine verschlüsselten dBASE-Tabellen.|  
|Logische|Der dBASE-Treiber kann keinen Index für eine LOGICAL-Spalte erstellen.|  
|Memo|Die maximale Länge einer MEMO-Spalte beträgt 65.500 Bytes.|  
  
 Weitere Einschränkungen für Datentypen finden Sie unter [Datentypeinschränkungen](../../odbc/microsoft/data-type-limitations.md).
