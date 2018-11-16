---
title: Floor-Funktion (XQuery) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- floor function [XQuery]
- fn:floor function
ms.assetid: 4ace57dd-b66e-4b60-a2b9-a1b0f1a0831d
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: d67244c125b2b85d3db7c0d511a1bf74bcfe91dd
ms.sourcegitcommit: 0f7cf9b7ab23df15624d27c129ab3a539e8b6457
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51293056"
---
# <a name="numeric-values-functions---floor"></a>Funktionen für numerische Werte – floor
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt die größte Zahl ohne Bruchanteil zurück, die nicht größer als der Wert ihres Arguments ist. Wenn das Argument eine leere Sequenz ist, wird die leere Sequenz zurückgegeben.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
fn:floor ($arg as numeric?) as numeric?  
```  
  
## <a name="arguments"></a>Argumente  
 *$arg*  
 Anzahl, auf die die Funktion angewendet wird.  
  
## <a name="remarks"></a>Hinweise  
 Wenn der Typ des *$arg* ist einer der drei numerischen Basistypen **xs: float**, **xs: double**, oder **xs: decimal**, der Rückgabetyp ist identisch mit der *$arg* Typ. Wenn der Typ des *$arg* ist ein Typ, der von einem der numerischen Typen abgeleitet ist der Rückgabetyp ist der numerische Basistyp.  
  
 Wenn die Eingabe für die Funktionen Fn: Floor, Fn: CEILING oder Fn: Round **xdt: UntypedAtomic**, nicht typisierte Daten, es wird implizit umgewandelt in **xs: double**. Alle anderen Typen führen zum Generieren eines statischen Fehlers.  
  
## <a name="examples"></a>Beispiele  
 In diesem Thema stellt XQuery-Beispiele für XML-Instanzen, die in verschiedenen gespeichert sind **Xml** Spalten vom Typ, in der AdventureWorks-Beispieldatenbank.  
  
 Sie können das Arbeitsbeispiel im Verwenden der [Ceiling-Funktion (XQuery)](../xquery/numeric-values-functions-ceiling.md) für die **floor()** XQuery-Funktion. Alles, was Sie tun wird, ersetzen Sie die **ceiling()** Funktion in der Abfrage durch die **floor()** Funktion.  
  
## <a name="implementation-limitations"></a>Implementierungseinschränkungen  
 Die folgenden Einschränkungen sind zu beachten:  
  
-   Die **floor()** -Funktion ordnet alle ganzzahligen Werte xs: Decimal.  
  
## <a name="see-also"></a>Siehe auch  
 [CEILING-Funktion &#40;XQuery&#41;](../xquery/numeric-values-functions-ceiling.md)   
 [Round-Funktion &#40;XQuery&#41;](../xquery/numeric-values-functions-round.md)   
 [XQuery Functions against the xml Data Type (XQuery-Funktionen für den xml-Datentyp)](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
