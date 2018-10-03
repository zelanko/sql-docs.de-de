---
title: Round-Funktion (XQuery) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:round function
- round function [XQuery]
ms.assetid: 320b572f-bd5b-4055-95a6-dec5718c0041
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: eb480cfe18a7f58dfb86a943a4cbdd34fa801138
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47683658"
---
# <a name="numeric-values-functions---round"></a>Funktionen für numerische Werte – round
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt die Zahl (ohne Stellen hinter dem Dezimalpunkt) zurück, die dem Argument am nächsten kommt. Wenn es mehr als eine solche Zahl gibt, wird diejenige zurückgegeben, die am nächsten an der positiv unendlichen Zahl liegt. Zum Beispiel:  
  
 Wenn das Argument 2.5 ist **round()** gibt 3 zurück.  
  
 Wenn das Argument 2.4999, **round()** gibt 2 zurück.  
  
 Wenn das Argument-2.5 ist **round()** -2 zurück.  
  
 Wenn das Argument eine leere Sequenz ist **round()** gibt die leere Sequenz zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
fn:round ( $arg as numeric?) as numeric?  
```  
  
## <a name="arguments"></a>Argumente  
 *$arg*  
 Anzahl, auf die die Funktion angewendet wird.  
  
## <a name="remarks"></a>Hinweise  
 Wenn der Typ des *$arg* ist einer der drei numerischen Basistypen **xs: float**, **xs: double**, oder **xs: decimal**, der Rückgabetyp ist identisch mit der *$arg* Typ. Wenn der Typ des *$arg* ist ein Typ, der von einem der numerischen Typen abgeleitet ist der Rückgabetyp ist der numerische Basistyp.  
  
 Wenn Eingabe für die **Fn: Floor**, **Fn: CEILING**, oder **Fn: Round** Functions **xdt: UntypedAtomic**, nicht typisierte Daten, es wird implizit umgewandelt in **xs: double**.  
  
 Alle anderen Typen führen zum Generieren eines statischen Fehlers.  
  
## <a name="examples"></a>Beispiele  
 In diesem Thema stellt XQuery-Beispiele für XML-Instanzen in verschiedenen gespeicherten **Xml** Spalten vom Typ, in der AdventureWorks-Datenbank.  
  
 Sie können das Arbeitsbeispiel im Verwenden der [Ceiling-Funktion (XQuery)](../xquery/numeric-values-functions-ceiling.md) für die **round()** XQuery-Funktion. Alles, was Sie tun wird, ersetzen Sie die **ceiling()** Funktion in der Abfrage durch die **round()** Funktion.  
  
## <a name="implementation-limitations"></a>Implementierungseinschränkungen  
 Die folgenden Einschränkungen sind zu beachten:  
  
-   Die **round()** -Funktion ordnet ganzzahligen Werte xs: Decimal.  
  
-   Die **round()** Funktion der xs: Double "und" xs: float-Werte zwischen - 0.5e0 und -0e0 werden 0e0 zugeordnet statt - 0e0 zugeordnet.  
  
## <a name="see-also"></a>Siehe auch  
 [Floor-Funktion &#40;XQuery&#41;](../xquery/numeric-values-functions-floor.md)   
 [CEILING-Funktion &#40;XQuery&#41;](../xquery/numeric-values-functions-ceiling.md)  
  
  
