---
description: Bestimmen der unterstützten Vorgänge
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 769004bd74b248188cfa96e633ce5961d2330838
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88806894"
---
# <a name="determining-what-is-supported"></a>Bestimmen der unterstützten Vorgänge
Die **unterstützte** -Methode wird verwendet, um zu bestimmen, ob ein angegebenes **Recordset** -Objekt einen bestimmten Funktionstyp unterstützt. Es weist die folgende Syntax auf:  
  
```  
  
boolean = recordset.Supports(CursorOptions )  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Die **unterstützte** Methode gibt einen booleschen Wert zurück, der angibt, ob der Anbieter alle Funktionen unterstützt, die durch das Cursor options-Argument identifiziert werden. Sie können die **unterstützte** Methode verwenden, um zu bestimmen, welche Arten von Funktionen ein **Recordset** -Objekt unterstützt. Wenn das **Recordset** -Objekt die Funktionen unterstützt, deren zugehörige Konstanten in *Cursor Options*enthalten sind, gibt die **unterstützte** Methode **true**zurück. Andernfalls wird **false**zurückgegeben.  
  
 Mithilfe der **unterstützten** -Methode können Sie überprüfen, ob das **Recordset** -Objekt neue Datensätze hinzufügen, Lesezeichen verwenden, die **Find** -Methode verwenden, den scrollvorgang verwenden, die **Index** -Eigenschaft verwenden und Batch Aktualisierungen ausführen kann. Eine umfassende Liste der Konstanten und ihrer Bedeutungen finden Sie unter [Cursor optionenum](../../reference/ado-api/cursoroptionenum.md).  
  
 Obwohl die **unterstützte** Methode möglicherweise für eine bestimmte Funktionalität **true** zurückgibt, gewährleistet Sie nicht, dass der Anbieter die Funktion unter allen Umständen verfügbar machen kann. Die **unterstützte** Methode gibt einfach zurück, ob der Anbieter die angegebene Funktionalität unterstützen kann, vorausgesetzt, dass bestimmte Bedingungen erfüllt sind. Beispielsweise kann die **unterstützte** Methode angeben, dass ein **Recordset** -Objekt Updates unterstützt, auch wenn der Cursor auf einem Join mehrerer Tabellen basiert. einige Spalten, die nicht aktualisierbar sind, sind möglicherweise nicht aktualisierbar.