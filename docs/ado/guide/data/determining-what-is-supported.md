---
title: Ermitteln der unterstützten Vorgänge | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- editing data [ADO], Supports method
- Supports method [ADO]
ms.assetid: 65090cba-6d46-4775-8d61-f6838e7752a6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dc42e9128ccc1ccb43996f554ffe280916884307
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67925523"
---
# <a name="determining-what-is-supported"></a>Bestimmen der unterstützten Vorgänge
Die **unterstützte** -Methode wird verwendet, um zu bestimmen, ob ein angegebenes **Recordset** -Objekt einen bestimmten Funktionstyp unterstützt. Es weist die folgende Syntax auf:  
  
```  
  
boolean = recordset.Supports(CursorOptions )  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Die **unterstützte** Methode gibt einen booleschen Wert zurück, der angibt, ob der Anbieter alle Funktionen unterstützt, die durch das Cursor options-Argument identifiziert werden. Sie können die **unterstützte** Methode verwenden, um zu bestimmen, welche Arten von Funktionen ein **Recordset** -Objekt unterstützt. Wenn das **Recordset** -Objekt die Funktionen unterstützt, deren zugehörige Konstanten in *Cursor Options*enthalten sind, gibt die **unterstützte** Methode **true**zurück. Andernfalls wird **false**zurückgegeben.  
  
 Mithilfe der **unterstützten** -Methode können Sie überprüfen, ob das **Recordset** -Objekt neue Datensätze hinzufügen, Lesezeichen verwenden, die **Find** -Methode verwenden, den scrollvorgang verwenden, die **Index** -Eigenschaft verwenden und Batch Aktualisierungen ausführen kann. Eine umfassende Liste der Konstanten und ihrer Bedeutungen finden Sie unter [Cursor optionenum](../../../ado/reference/ado-api/cursoroptionenum.md).  
  
 Obwohl die **unterstützte** Methode möglicherweise für eine bestimmte Funktionalität **true** zurückgibt, gewährleistet Sie nicht, dass der Anbieter die Funktion unter allen Umständen verfügbar machen kann. Die **unterstützte** Methode gibt einfach zurück, ob der Anbieter die angegebene Funktionalität unterstützen kann, vorausgesetzt, dass bestimmte Bedingungen erfüllt sind. Beispielsweise kann die **unterstützte** Methode angeben, dass ein **Recordset** -Objekt Updates unterstützt, auch wenn der Cursor auf einem Join mehrerer Tabellen basiert. einige Spalten, die nicht aktualisierbar sind, sind möglicherweise nicht aktualisierbar.
