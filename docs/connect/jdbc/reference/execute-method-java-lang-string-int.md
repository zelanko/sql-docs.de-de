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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6e96e0c9c957522db6a766b3491d394b7337d7b6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67954980"
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
**true** , wenn das erste Ergebnis ein Resultset ist. Andernfalls lautet der Wert **false**.
  
## <a name="exceptions"></a>Ausnahmen
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Bemerkungen
Diese execute-Methode wird von der execute-Methode in der java.sql.Statement-Schnittstelle angegeben.

## <a name="see-also"></a>Weitere Informationen

[Execute- &#40;Methode SQLServerStatement&#41;](./execute-method-sqlserverstatement.md)

[SQLServerStatement-Elemente](./sqlserverstatement-members.md)

[SQLServerStatement-Klasse](./sqlserverstatement-class.md)
