---
title: prepareStatement Method (java.lang.String) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/07/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.prepareStatement (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e825765c-eb55-4800-951b-f3495da36641
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0c91b965498c0b617a02c7707e369a2ba61c0065
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67976155"
---
# <a name="preparestatement-method-javalangstring"></a>prepareStatement-Methode (java.lang.String)

Erstellt ein [SQLServerPreparedStatement](./sqlserverpreparedstatement-class.md)-Objekt zum Senden von parametrisierten SQL-Anweisungen an die Datenbank.

## <a name="syntax"></a>Syntax

```
public java.sql.PreparedStatement prepareStatement(java.lang.String sql)
```

#### <a name="parameters"></a>Parameter
*sql*

Eine **Zeichenfolge**, die eine SQL-Anweisung enthält.

## <a name="return-value"></a>Rückgabewert
Ein PreparedStatement-Objekt.

## <a name="exceptions"></a>Ausnahmen  
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Bemerkungen
Diese prepareStatement-Methode wird von der prepareStatement-Methode in der Java. SQL. Connection-Schnittstelle angegeben.

## <a name="see-also"></a>Weitere Informationen

[prepareStatement-Methode &#40;SQLServerConnection&#41;](./preparestatement-method-sqlserverconnection.md)

[SQLServerConnection-Elemente](./sqlserverconnection-members.md)

[SQLServerConnection-Klasse](./sqlserverconnection-class.md)
