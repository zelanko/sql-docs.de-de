---
title: AVG-Funktion (XQuery) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:avg function
- avg function [XQuery]
ms.assetid: 0cc60267-3c56-4a88-8ad7-bb07f0255d56
author: rothja
ms.author: jroth
ms.openlocfilehash: b659aa13a8704a060be12bb015bd0de0fd126562
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67985994"
---
# <a name="aggregate-functions---avg"></a>Aggregatfunktionen – avg
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt den Mittelwert einer Sequenz von Zahlen zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
fn:avg($arg as xdt:anyAtomicType*) as xdt:anyAtomicType?  
```  
  
## <a name="arguments"></a>Argumente  
 *$arg*  
 Die Sequenz der atomaren Werte, deren Mittelwert berechnet wird.  
  
## <a name="remarks"></a>Bemerkungen  
 Alle Typen der atomisierten Werte, die an **AVG ()** übergeben werden, müssen ein Untertyp von genau einem der drei integrierten numerischen Basis Typen oder xdt: untypedAtomic sein. Es darf keine Mischung vorliegen. Werte des Typs xdt:untypedAtomic werden wie xs:double behandelt. Das Ergebnis von **AVG ()** empfängt den Basistyp der bestandenen Typen, z. b. xs: Double im Fall von xdt: untypedAtomic.  
  
 Wenn die Eingabe statisch leer ist, wird Empty impliziert und ein statischer Fehler ausgelöst.  
  
 Die **AVG ()** -Funktion gibt den Durchschnitt der berechneten Zahlen zurück. Beispiel:  
  
 **Summe (** *$arg* **) div count (** *$arg* **)**  
  
 Wenn *$arg* eine leere Sequenz ist, wird die leere Sequenz zurückgegeben.  
  
 Wenn ein xdt: untypedAtomic-Wert nicht in xs: Double umgewandelt werden kann, wird der Wert in der Eingabe Sequenz ignoriert, *$arg*.  
  
 In allen anderen Fällen gibt die Funktion einen statischen Fehler zurück.  
  
## <a name="examples"></a>Beispiele  
 Dieses Thema stellt XQuery-Beispiele für XML-Instanzen bereit, die in verschiedenen Spalten vom Typ **XML** in der AdventureWorks-Datenbank gespeichert sind.  
  
### <a name="a-using-the-avg-xquery-function-to-find-work-center-locations-in-the-manufacturing-process-in-which-labor-hours-are-greater-than-the-average-for-all-work-center-locations"></a>A. Verwenden der XQuery-Funktion avg() zum Suchen nach Arbeitsplatzstandorten im Fertigungsprozess, an denen die Anzahl der Arbeitsstunden größer als der Mittelwert für alle Arbeitsplatzstandorte ist.  
 Sie können die in der Min- [Funktion (XQuery)](../xquery/aggregate-functions-min.md) bereitgestellte Abfrage so umschreiben, dass die **AVG ()** -Funktion verwendet wird.  
  
## <a name="implementation-limitations"></a>Implementierungseinschränkungen  
 Die folgenden Einschränkungen sind zu beachten:  
  
-   Die **AVG ()** -Funktion ordnet alle ganzzahligen Werte xs: Decimal zu.  
  
-   Die **AVG ()** -Funktion wird für Werte des Typs xs: Duration nicht unterstützt.  
  
-   Sequenzen, die Typen über Basistypbegrenzungen hinweg mischen, werden nicht unterstützt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [XQuery-Funktionen für den xml-Datentyp](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
