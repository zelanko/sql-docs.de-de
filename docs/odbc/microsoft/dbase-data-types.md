---
title: dBASE-Datentypen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fc4b4c7a5c1074a62bf0e84d265840109f65ea55
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63126313"
---
# <a name="dbase-data-types"></a>dBASE-Datentypen
Die folgende Tabelle zeigt, wie die dBASE-Datentypen in ODBC-SQL-Datentypen zugeordnet werden. Beachten Sie, dass nicht alle ODBC-SQL-Datentypen unterstützt werden.  
  
|dBASE-Datentyp|ODBC-Datentyp|  
|---------------------|--------------------|  
|CHAR|SQL_VARCHAR|  
|DATE|SQL_DATE|  
|FLOAT[1]|SQL_DOUBLE|  
|LOGISCHE|SQL_BIT|  
|MEMO|SQL_LONGVARCHAR|  
|NUMERIC (BCD)|SQL_DOUBLE|  
|OLEOBJECT[1]|SQL_LONGBINARY|  
  
 [1] gültig nur für dBASE, Version 5. *x*  
  
 Genauigkeit in dBASE III kann Zahlen mit um zweistellige Exponenten und dBASE IV Zahlen mit bis zu drei Ziffern bestehenden Exponenten. Da Zahlen als Text gespeichert sind, werden sie in Zahlen umgewandelt. Wenn die zu konvertierende Zahl in ein Feld nicht unerklärlichen Ergebnissen kommen passt.  
  
 Während dBASE eine Genauigkeit und Dezimalstellen mit einem numerischen Datentyp angegeben werden kann, wird es vom ODBC dBASE-Treiber nicht unterstützt. Der ODBC-dBASE-Treiber gibt immer eine Genauigkeit von 15 und einer Skala von 0 für einen numerischen Datentyp zurück.  
  
 Eine Spalte mit der numerische Datentyp, der mithilfe der ODBC-dBASE-Treiber ordnet den ODBC SQL_DOUBLE--Datentyp erstellt wurden. Daher werden die Daten in dieser Spalte Rundungsfehler ein. Dieses Verhalten entspricht nicht der, die der numerischen Daten dBASE (Typ N), geben Sie in der Binary Coded Decimal (BCD).  
  
> [!NOTE]  
>  **SQLGetTypeInfo** gibt der ODBC-SQL-Datentypen. Alle Konvertierungen, die in Anhang D des der *ODBC Programmer's Reference* werden unterstützt, für die ODBC-SQL-Datentypen, die weiter oben in diesem Thema aufgeführt.  
  
 Die folgende Tabelle zeigt Einschränkungen auf dBASE-Datentypen.  
  
|Datentyp|Description|  
|---------------|-----------------|  
|CHAR|Erstellen eine CHAR-Spalte 0 (null) oder nicht angegebene Länge gibt tatsächlich eine 254-Byte-Spalte zurück.|  
|Verschlüsselte Daten|DBASE-Treiber unterstützt keine verschlüsselten dBASE-Tabellen.|  
|LOGISCHE|DBASE-Treiber kann nicht über einen Index für eine logische Spalte erstellen.|  
|MEMO|Die maximale Länge einer Spalte SPRACHNOTIZ ist 65.500 Bytes.|  
  
 Weitere Einschränkungen für Datentypen finden Sie im [Datumstypen](../../odbc/microsoft/data-type-limitations.md).
