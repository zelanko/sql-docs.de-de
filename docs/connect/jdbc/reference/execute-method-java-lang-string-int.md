---
title: execute-Methode (java.lang.String, int[]) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/07/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.execute (javal.lang.String.int[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: dc73d1c3-e756-43af-b1fc-ac438cbd0965
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7195d5c5bf4efb593e53dea6e5404cc8adb70830
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922130"
---
# <a name="execute-method-javalangstring-int"></a>execute-Methode (java.lang.String, int[])

  Führt die angegebene SQL-Anweisung aus, von der mehrere Ergebnisse zurückgegeben werden können, und signalisiert [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)], dass die automatisch generierten Schlüssel, die in dem angegebenen Array angegeben sind, zum Abrufen verfügbar gemacht werden sollen.

## <a name="syntax"></a>Syntax

```Java
public final boolean execute(
    java.lang.String sql,
    int[] columnIndexes)
```

#### <a name="parameters"></a>Parameter
*sql*

Eine **Zeichenfolge** mit einer SQL-Anweisung.

*columnIndexes*

Ein Array von Werten vom Typ **int** zum Angeben der Spaltenindizes der automatisch generierten Schlüssel, die verfügbar gemacht werden sollen.

## <a name="return-value"></a>Rückgabewert
Der Wert **TRUE** wird zurückgegeben, wenn das erste Ergebnis ein Resultset ist. Andernfalls lautet der Wert **false**.
  
## <a name="exceptions"></a>Ausnahmen
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Bemerkungen
Diese execute-Methode wird von der execute-Methode in der java.sql.Statement-Schnittstelle angegeben.

## <a name="see-also"></a>Weitere Informationen

[execute-Methode &#40;SQLServerStatement&#41;](./execute-method-sqlserverstatement.md)

[SQLServerStatement-Elemente](./sqlserverstatement-members.md)

[SQLServerStatement-Klasse](./sqlserverstatement-class.md)
