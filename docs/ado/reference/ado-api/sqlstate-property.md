---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e43ace17f3f2b709c327f185a189a107b6b73065
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67916887"
---
# <a name="sqlstate-property"></a>SQLState-Eigenschaft
Gibt den SQL-Status für ein angegebenes [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt an.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen fünf **stelligen Zeichen folgen Wert zurück** , der dem ANSI SQL-Standard entspricht, und gibt den Fehlercode an.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **SQLSTATE** -Eigenschaft, um den Fehlercode aus fünf Zeichen zu lesen, den der Anbieter zurückgibt, wenn während der Verarbeitung einer SQL-Anweisung ein Fehler auftritt. Wenn Sie z. b. den Microsoft OLE DB-Anbieter für ODBC mit einer Microsoft SQL Server-Datenbank verwenden, werden SQL-Status Fehlercodes von ODBC abgeleitet, die entweder auf ODBC-spezifischen Fehlern oder auf Fehlern aus Microsoft SQL Server basieren und dann ODBC zugeordnet werden. mern. Diese Fehlercodes sind im ANSI SQL-Standard dokumentiert, können aber von unterschiedlichen Datenquellen unterschiedlich implementiert werden.  
  
## <a name="applies-to"></a>Gilt für  
 [Error-Objekt](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Beschreibung, HelpContext, HelpFile, NativeError, Number, Source und SQLSTATE Properties (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Beschreibung, HelpContext, HelpFile, NativeError, Number, Source und SQLSTATE Properties Example (VC + +)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
