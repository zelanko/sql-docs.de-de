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
ms.openlocfilehash: 1753e0d50655205bc6f459548f2ef2b77d5cc885
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68096452"
---
# <a name="dbase-data-types"></a>dBASE-Datentypen
In der folgenden Tabelle wird gezeigt, wie dBase-Datentypen ODBC-SQL-Datentypen zugeordnet werden. Beachten Sie, dass nicht alle ODBC-SQL-Datentypen unterstützt werden.  
  
|dBASE-Datentyp|ODBC-Datentyp|  
|---------------------|--------------------|  
|CHAR|SQL_VARCHAR|  
|DATE|SQL_DATE|  
|FLOAT [1]|SQL_DOUBLE|  
|Richtig|SQL_BIT|  
|Anruf|SQL_LONGVARCHAR|  
|numerisch (BCD)|SQL_DOUBLE|  
|OLEObject [1]|SQL_LONGBINARY|  
  
 [1] nur gültig für dBASE, Version 5. *x*  
  
 Die Genauigkeit in dBASE III ermöglicht Zahlen mit bis zu zweistelligen Exponenten und in dBASE-IV-Zahlen mit bis zu dreistelligen Exponenten. Da Zahlen als Text gespeichert werden, werden Sie in Zahlen konvertiert. Wenn die zu konvertierende Zahl nicht in ein Feld passt, können ggf. nicht aufgetrebene Ergebnisse auftreten.  
  
 Während dBASE das Angeben einer Genauigkeit und einer Skala mit einem numerischen Datentyp zulässt, wird es vom ODBC-dBase-Treiber nicht unterstützt. Der ODBC-dBase-Treiber gibt immer eine Genauigkeit von 15 und eine Skala von 0 für einen numerischen Datentyp zurück.  
  
 Eine mit dem numerischen Datentyp erstellte Spalte, die den ODBC-dBase-Treiber verwendet, wird dem SQL_DOUBLE ODBC-Datentyp zugeordnet. Daher können die Daten in dieser Spalte gerundet werden. Dieses Verhalten ist nicht mit dem des numerischen Datentyps in dBASE (Typ N) identisch (Binary Coded Decimal (BCD)).  
  
> [!NOTE]  
>  **SQLGetTypeInfo** gibt ODBC-SQL-Datentypen zurück. Alle Konvertierungen in Anhang D der *ODBC-Programmier Referenz* werden für die zuvor in diesem Thema aufgeführten ODBC-SQL-Datentypen unterstützt.  
  
 In der folgenden Tabelle sind die Einschränkungen für dBASE-Datentypen aufgeführt.  
  
|Datentyp|BESCHREIBUNG|  
|---------------|-----------------|  
|CHAR|Beim Erstellen einer char-Spalte mit NULL oder einer nicht angegebenen Länge wird tatsächlich eine 254-Byte-Spalte zurückgegeben.|  
|Verschlüsselte Daten|Verschlüsselte dBASE-Tabellen werden vom dBase-Treiber nicht unterstützt.|  
|Richtig|Der dBase-Treiber kann keinen Index für eine logische Spalte erstellen.|  
|Anruf|Die maximale Länge einer Memo Spalte beträgt 65.500 Bytes.|  
  
 Weitere Einschränkungen für Datentypen finden Sie unter [Datentyp Einschränkungen](../../odbc/microsoft/data-type-limitations.md).
