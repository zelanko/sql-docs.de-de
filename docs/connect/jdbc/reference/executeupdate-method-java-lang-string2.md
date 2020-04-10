---
title: executeUpdate-Methode (java.lang.String) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/07/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.executeUpdate (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 91ecb1cd-001d-4ac9-9ae8-5db05c3c2959
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 428127147d00885dc379752e97154e8eabad54d1
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924210"
---
# <a name="executeupdate-method-javalangstring"></a>executeUpdate-Methode (java.lang.String)

Führt die angegebene SQL-Anweisung aus. Hierbei kann es sich um eine Anweisung vom Typ "INSERT", "UPDATE", "MERGE" oder "DELETE" oder um eine SQL-Anweisung handeln, von der nichts zurückgegeben wird (beispielsweise eine SQL-DDL-Anweisung).

## <a name="syntax"></a>Syntax

```
public final int executeUpdate(java.lang.String sql)
```

#### <a name="parameters"></a>Parameter
*sql*

Ein **String-Objekt** mit der SQL-Anweisung.

## <a name="return-value"></a>Rückgabewert
Ein **int**-Wert, der die Anzahl der betroffenen Zeilen angibt, oder „0“ bei Verwendung einer DDL-Anweisung.

## <a name="exceptions"></a>Ausnahmen
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Bemerkungen
Diese executeUpdate-Methode wird von der executeUpdate-Methode in der java.sql.PreparedStatement-Schnittstelle angegeben.

Durch den Aufruf dieser Methode wird eine Ausnahme ausgelöst, da die SQL-Anweisung für das SQLServerPreparedStatement-Objekt bei der Erstellung des Objekts angegeben wird.

## <a name="see-also"></a>Weitere Informationen

[executeUpdate-Methode &#40;SQLServerPreparedStatement&#41;](./executeupdate-method-sqlserverpreparedstatement.md)

[SQLServerPreparedStatement-Elemente](./sqlserverpreparedstatement-members.md)

[SQLServerPreparedStatement-Klasse](./sqlserverpreparedstatement-class.md)
