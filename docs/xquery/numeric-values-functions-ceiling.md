---
title: CEILING-Funktion (XQuery) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:ceiling function
- ceiling function [XQuery]
ms.assetid: 594f1dd0-3c27-41b3-b809-9ce6714c5a97
author: rothja
ms.author: jroth
ms.openlocfilehash: fe18f488b83c1a8c9236c642751c1dc80bfe7e6c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67946579"
---
# <a name="numeric-values-functions---ceiling"></a>Funktionen für numerische Werte – ceiling 
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt die kleinste Anzahl ohne Stellen hinter dem Dezimalpunkt zurück, die nicht geringer ist als der Wert des Funktionsarguments. Wenn das Argument eine leere Sequenz ist, wird die leere Sequenz zurückgegeben.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
fn:ceiling ( $arg as numeric?) as numeric?  
```  
  
## <a name="arguments"></a>Argumente  
 *$arg*  
 Anzahl, auf die die Funktion angewendet wird.  
  
## <a name="remarks"></a>Hinweise  
 Wenn der Typ des *$arg* ist einer der drei numerischen Basistypen **xs: float**, **xs: double**, oder **xs: decimal**, der Rückgabetyp ist identisch mit die *$arg* Typ.  
  
 Wenn der Typ des *$arg* ist ein Typ, der von einem der numerischen Typen abgeleitet ist der Rückgabetyp ist der numerische Basistyp.  
  
 Wenn die Eingabe für die Funktionen Fn: Floor, Fn: CEILING oder Fn: Round **xdt: UntypedAtomic**, es wird implizit umgewandelt in **xs: double**.  
  
 Alle anderen Typen führen zum Generieren eines statischen Fehlers.  
  
## <a name="examples"></a>Beispiele  
 In diesem Thema stellt XQuery-Beispiele für XML-Instanzen, die in verschiedenen gespeichert sind **Xml** Spalten vom Typ, in der AdventureWorks-Datenbank.  
  
### <a name="a-using-the-ceiling-xquery-function"></a>A. Verwenden der XQuery-Funktion ceiling()  
 Für Produktmodell 7 gibt die Abfrage eine Liste der Arbeitsplatzstandorte im Produktionsprozess des Produktmodells zurück. Für jeden einzelnen Arbeitsplatzstandort gibt die Abfrage die Standortkennung, die Arbeitsstunden sowie die Losgröße zurück, sofern diese dokumentiert ist. Die Abfrage verwendet die **Ceiling** Funktion, um die Arbeitsstunden als Werte des Typs zurückzugeben **decimal**.  
  
```  
SELECT ProductModelID, Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";   
     for $i in /AWMI:root/AWMI:Location  
     return   
       <Location LocationID="{ $i/@LocationID }"   
                   LaborHrs="{ ceiling($i/@LaborHours) }" >  
                    {   
                      $i/@LotSize  
                    }    
       </Location>  
') AS Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Beachten Sie hinsichtlich der vorherigen Abfrage Folgendes:  
  
-   Das AWMI-Namespacepräfix steht für Adventure Works Manufacturing Instructions. Dieses Präfix verweist auf denselben Namespace, der im abgefragten Dokument verwendet wird.  
  
-   **Anweisungen** ist ein **Xml** Type-Spalte. Aus diesem Grund die [Query()-Methode (XML-Datentyp)](../t-sql/xml/query-method-xml-data-type.md) dient zum Angeben von XQuery. Die XQuery-Anweisung wird als Argument der query-Methode angegeben.  
  
-   **für... zurückgeben** ist eine Schleifenkonstruktion. In der Abfrage die **für** Schleife gibt eine Liste mit \<Speicherort > Elemente. Für jeden einzelnen arbeitsplatzstandort die **zurückgeben** -Anweisung in der **für** Schleife beschreibt den XML-Code generiert werden:  
  
    -   Ein \<Location >-Element mit LocationId- und ein LaborHrs-Attributen ist. Der entsprechende Ausdruck in den geschweiften Klammern ({ }) ruft die erforderlichen Werte aus dem Dokument ab.  
  
    -   Die {$i/@LotSize } Ausdruck ruft das LotSize-Attribut aus dem Dokument, ab, falls vorhanden.  
  
    -   Dies ist das Ergebnis:  
  
```  
ProductModelID Result    
-------------- ------------------------------------------------------  
7      <Location LocationID="10" LaborHrs="3" LotSize="100"/>  
       <Location LocationID="20" LaborHrs="2" LotSize="1"/>     
       <Location LocationID="30" LaborHrs="1" LotSize="1"/>     
       <Location LocationID="45" LaborHrs="1" LotSize="20"/>  
       <Location LocationID="60" LaborHrs="3" LotSize="1"/>     
       <Location LocationID="60" LaborHrs="4" LotSize="1"/>  
```  
  
### <a name="implementation-limitations"></a>Implementierungseinschränkungen  
 Die folgenden Einschränkungen sind zu beachten:  
  
-   Die **ceiling()** -Funktion ordnet alle ganzzahligen Werte xs: Decimal.  
  
## <a name="see-also"></a>Siehe auch  
 [Floor-Funktion &#40;XQuery&#41;](../xquery/numeric-values-functions-floor.md)   
 [Round-Funktion &#40;XQuery&#41;](../xquery/numeric-values-functions-round.md)  
  
  
