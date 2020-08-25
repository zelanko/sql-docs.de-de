---
description: SQLState-Eigenschaft
title: SQLSTATE-Eigenschaft | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::GetSQLState
- Error::SQLState
- Error::get_SQLState
helpviewer_keywords:
- SQLState property
ms.assetid: f9e25967-54b0-444d-af2a-0d2c75365d3e
author: rothja
ms.author: jroth
ms.openlocfilehash: 65d72fed54723f525f4e1426ed04886e9d474985
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777369"
---
# <a name="sqlstate-property"></a>SQLState-Eigenschaft
Gibt den SQL-Status für ein angegebenes [Fehler](./error-object.md) Objekt an.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen fünf **stelligen Zeichen folgen Wert zurück** , der dem ANSI SQL-Standard entspricht, und gibt den Fehlercode an.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **SQLSTATE** -Eigenschaft, um den Fehlercode aus fünf Zeichen zu lesen, den der Anbieter zurückgibt, wenn während der Verarbeitung einer SQL-Anweisung ein Fehler auftritt. Wenn Sie z. b. den Microsoft OLE DB-Anbieter für ODBC mit einer Microsoft SQL Server-Datenbank verwenden, werden SQL-Status Fehlercodes von ODBC abgeleitet, die entweder auf ODBC-spezifischen Fehlern oder auf Fehlern aus Microsoft SQL Server basieren und dann ODBC-Fehlern zugeordnet werden. Diese Fehlercodes sind im ANSI SQL-Standard dokumentiert, können aber von unterschiedlichen Datenquellen unterschiedlich implementiert werden.  
  
## <a name="applies-to"></a>Gilt für  
 [Error-Objekt](./error-object.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Beschreibung, HelpContext, HelpFile, NativeError, Number, Source und SQLSTATE Properties (VB)](./description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Beschreibung, HelpContext, HelpFile, NativeError, Number, Source und SQLSTATE Properties Example (VC + +)](./description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)