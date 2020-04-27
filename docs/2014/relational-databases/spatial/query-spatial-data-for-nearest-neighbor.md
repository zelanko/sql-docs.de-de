---
title: Abfragen von nächsten Nachbarn aus räumlichen Daten | Microsoft-Dokumentation
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 7af4ad5d-484e-45b4-aa16-83c33b358bb6
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 099771b9900d4c39de40b176cde5c92fa0c95462
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66014111"
---
# <a name="query-spatial-data-for-nearest-neighbor"></a>Abfragen von nächsten Nachbarn aus räumlichen Daten
  Eine häufig für räumliche Daten verwendete Abfrage ist die Nächster Nachbar-Abfrage. Mithilfe von Nächster Nachbar-Abfragen werden die räumlichen Objekte gesucht, die einem bestimmten räumlichen Objekt am nächsten liegen. Beispielsweise muss von einer Filialsuche auf einer Website häufig die Filiale bestimmt werden, die dem Standort des Kunden am nächsten liegt.  
  
 Eine Nächster Nachbar-Abfrage kann in einer Vielzahl von gültigen Abfrageformaten geschrieben werden. Damit jedoch für die Nächster Nachbar-Abfrage ein räumlicher Index verwendet wird, muss die folgende Syntax angegeben werden.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
SELECT TOP ( number )  
        [ WITH TIES ]  
        [ * | expression ]   
        [, ...]  
    FROM spatial_table_reference, ...   
        [ WITH   
            (   
                [ INDEX ( index_ref ) ]   
                [ , SPATIAL_WINDOW_MAX_CELLS = <value>]   
                [ ,... ]   
            )   
        ]  
    WHERE   
        column_ref.STDistance ( @spatial_ object )   
            {   
                [ IS NOT NULL ] | [ < const ] | [ > const ]   
                | [ <= const ] | [ >= const ] | [ <> const ] ]   
            }  
            [ AND { other_predicate } ]   
    }  
    ORDER BY column_ref.STDistance ( @spatial_ object ) [ ,...n ]  
[ ; ]  
  
```  
  
## <a name="nearest-neighbor-query-and-spatial-indexes"></a>Nächster Nachbar-Abfrage und räumliche Indizes  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden `TOP`-Klauseln und `ORDER BY`-Klauseln verwendet, um eine Nächster Nachbar-Abfrage für Spalten mit räumlichen Daten auszuführen. Die `ORDER BY`-Klausel enthält einen Aufruf der `STDistance()`-Methode für den Typ der Spalte mit räumlichen Daten. Die `TOP`-Klausel gibt die für die Abfrage zurückzugebende Anzahl von Objekten an.  
  
 Die folgenden Anforderungen müssen erfüllt sein, damit eine Nächster Nachbar-Abfrage einen räumlichen Index verwendet:  
  
1.  Ein räumlicher Index muss in einer der räumlichen Spalten vorhanden sein, und die `STDistance()`-Methode muss diese Spalte in der `WHERE`-Klausel und der `ORDER BY`-Klausel verwenden.  
  
2.  Die `TOP`-Klausel darf keine `PERCENT`-Anweisung enthalten.  
  
3.  Die `WHERE`-Klausel muss eine `STDistance()`-Methode enthalten.  
  
4.  Wenn in der `WHERE`-Klausel mehrere Prädikate vorhanden sind, muss das Prädikat mit der `STDistance()`-Methode über eine `AND`-Konjunktion mit den anderen Prädikaten verbunden werden. Die `STDistance()`-Methode darf sich nicht in einem optionalen Teil der `WHERE`-Klausel befinden.  
  
5.  Der erste Ausdruck in der `ORDER BY`-Klausel muss die `STDistance()`-Methode verwenden.  
  
6.  Die Sortierreihenfolge für den ersten `STDistance()`-Ausdruck in der `ORDER BY`-Klausel muss auf `ASC` festgelegt sein.  
  
7.  Alle Zeilen, für die `STDistance` den Wert `NULL` zurückgibt, müssen herausgefiltert werden.  
  
> [!WARNING]  
>  Methoden, die den Datentyp `geography` oder `geometry` als Argument annehmen, geben `NULL` zurück, wenn die SRIDs für die Typen nicht identisch sind.  
  
 Es wird empfohlen, dass für Indizes in Nächster Nachbar-Abfragen die neuen Mosaiken für räumliche Indizes verwendet werden. Weitere Informationen zu Mosaiken für räumliche Indizes finden Sie unter [Räumliche Daten &#40;SQL Server&#41;](spatial-data-sql-server.md)festgelegt sein.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird eine Nächster Nachbar-Abfrage veranschaulicht, die einen räumlichen Index verwenden kann. Im Beispiel wird die Tabelle `Person.Address` in der `AdventureWorks2012` -Datenbank verwendet.  
  
```  
USE AdventureWorks2012  
GO  
DECLARE @g geography = 'POINT(-121.626 47.8315)';  
SELECT TOP(7) SpatialLocation.ToString(), City FROM Person.Address  
WHERE SpatialLocation.STDistance(@g) IS NOT NULL  
ORDER BY SpatialLocation.STDistance(@g);  
  
```  
  
 Erstellen Sie einen räumlichen Index in der SpatialLocation-Spalte, um zu veranschaulichen, wie eine Nächster Nachbar-Abfrage einen räumlichen Index verwendet. Weitere Informationen zum Erstellen von räumlichen Indizes finden Sie unter [Create, Modify, and Drop Spatial Indexes](create-modify-and-drop-spatial-indexes.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird eine Nächster Nachbar-Abfrage veranschaulicht, die keine räumlichen Indizes verwenden kann.  
  
```  
USE AdventureWorks2012  
GO  
DECLARE @g geography = 'POINT(-121.626 47.8315)';  
SELECT TOP(7) SpatialLocation.ToString(), City FROM Person.Address  
ORDER BY SpatialLocation.STDistance(@g);  
  
```  
  
 In der Abfrage fehlt eine `WHERE`-Klausel, die `STDistance()` in einem im Syntaxabschnitt angegebenen Format verwendet, sodass die Abfrage keine räumlichen Indizes verwenden kann.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Räumliche Daten &#40;SQL Server&#41;](spatial-data-sql-server.md)  
  
  
