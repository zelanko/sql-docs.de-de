---
title: Abfragen von nächsten Nachbarn aus räumlichen Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-spatial
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7af4ad5d-484e-45b4-aa16-83c33b358bb6
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 46d2c75b69d283d6122255ec9ac4a41c4ccdbc28
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160387"
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
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden `TOP`-Klauseln und `ORDER BY`-Klauseln verwendet, um eine Nächster Nachbar-Abfrage für Spalten mit räumlichen Daten auszuführen. Die `ORDER BY` -Klausel enthält einen Aufruf der `STDistance()` Methode für den Datentyp der räumlichen Spalte. Die `TOP` -Klausel gibt die Anzahl von Objekten, die bei der Abfrage zurückgegeben werden.  
  
 Die folgenden Anforderungen müssen erfüllt sein, damit eine Nächster Nachbar-Abfrage einen räumlichen Index verwendet:  
  
1.  Ein räumlicher Index muss in einer der räumlichen Spalten vorhanden sein, und die `STDistance()`-Methode muss diese Spalte in der `WHERE`-Klausel und der `ORDER BY`-Klausel verwenden.  
  
2.  Die `TOP`-Klausel darf keine `PERCENT`-Anweisung enthalten.  
  
3.  Die `WHERE`-Klausel muss eine `STDistance()`-Methode enthalten.  
  
4.  Wenn in der `WHERE`-Klausel mehrere Prädikate vorhanden sind, muss das Prädikat mit der `STDistance()`-Methode über eine `AND`-Konjunktion mit den anderen Prädikaten verbunden werden. Die `STDistance()` -Methode darf sich nicht in einem optionalen Teil der `WHERE` Klausel.  
  
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
  
 Die Abfrage fehlt eine `WHERE` -Klausel, verwendet `STDistance()` in einem Formular im Syntaxabschnitt angegeben werden, sodass die Abfrage einen räumlichen Index verwenden kann.  
  
## <a name="see-also"></a>Siehe auch  
 [Räumliche Daten &#40;SQL Server&#41;](spatial-data-sql-server.md)  
  
  