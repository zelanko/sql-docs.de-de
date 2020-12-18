---
title: Schätzen der Größe eines gruppierten Indexes | Microsoft-Dokumentation
description: Verwenden Sie dieses Verfahren, um einzuschätzen, wie viel Speicherplatz zum Speichern von Daten in einem gruppierten Index in SQL Server erforderlich ist.
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.reviewer: ''
ms.prod_service: database-engine, sql-database
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- space allocation [SQL Server], index size
- size [SQL Server], tables
- disk space [SQL Server], indexes
- predicting table size [SQL Server]
- table size [SQL Server]
- estimating table size
- space [SQL Server], indexes
- clustered indexes, table size
- nonclustered indexes [SQL Server], table size
- designing databases [SQL Server], estimating size
- calculating table size
ms.assetid: 2b5137f8-98ad-46b5-9aae-4c980259bf8d
author: stevestein
ms.author: sstein
monikerRange: = azuresqldb-current || >= sql-server-2016
ms.openlocfilehash: d963a8745d83be039fa2970a24d04a2a882bf7a9
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97478361"
---
# <a name="estimate-the-size-of-a-clustered-index"></a>Schätzen der Größe eines gruppierten Indexes

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Mit den folgenden Schritten können Sie den Umfang des Speicherplatzes schätzen, der zum Speichern eines gruppierten Indexes erforderlich ist:  
  
1.  Berechnen des Speicherplatzes, der zum Speichern der Daten in der Blattebene des gruppierten Indexes erforderlich ist.  
  
2.  Berechnen des Speicherplatzes, der zum Speichern von Indexinformationen für den gruppierten Index verwendet wird.  
  
3.  Addieren Sie die berechneten Werte.  
  
## <a name="step-1-calculate-the-space-used-to-store-data-in-the-leaf-level"></a>Schritt 1: Berechnen des Speicherplatzes, der zum Speichern der Daten in der Blattebene verwendet wird  
  
1.  Geben Sie die Anzahl der Zeilen an, die die Tabelle enthalten wird:  
  
     ***Num_Rows** _ = Anzahl der Zeilen in der Tabelle  
  
2.  Geben Sie die Anzahl der Spalten mit fester und mit variabler Länge an, und berechnen Sie den Speicherplatz, der für deren Speicherung erforderlich ist:  
  
     Berechnen Sie den Speicherplatz, der zum Speichern jeder dieser Spaltengruppen innerhalb der Datenzeile erforderlich ist. Die Größe einer Spalte hängt von der Angabe für Datentyp und -länge ab.  
  
     _*_Num_Cols_*_  = Gesamtanzahl der Spalten (mit fester und variabler Länge)  
  
     _*_Fixed_Data_Size_*_  = Gesamtzahl der Bytes in allen Spalten mit fester Länge  
  
     _*_Num_Variable_Cols_*_  = Anzahl der Spalten mit variabler Länge  
  
     _*_Max_Var_Size_*_ = Maximale Bytegröße aller Spalten mit variabler Länge  
  
3.  Wenn der gruppierte Index nicht eindeutig ist, berücksichtigen Sie die _uniqueifier*-Spalte:  
  
     Die Uniqueifier-Spalte ist eine Spalte variabler Länge mit NULL-Zulässigkeit. Sie ist in Spalten Nicht-NULL und 4 Byte lang, deren Schlüsselwerte nicht eindeutig sind. Dieser Wert ist Teil des Indexschlüssels und für die Sicherstellung erforderlich, dass jede Zeile über einen eindeutigen Schlüsselwert verfügt.  
  
     ***Num_Cols** _  = _*_Num_Cols_*_ + 1  
  
     _*_Num_Variable_Cols_*_  = _*_Num_Variable_Cols_*_ + 1  
  
     _*_Max_Var_Size_*_  = _*_Max_Var_Size_*_ + 4  
  
     Diese Änderungen gehen davon aus, dass alle Werte nicht eindeutig sind.  
  
4.  Ein Teil der Zeile, der als NULL-Bitmuster (Null_Bitmap) bezeichnet wird, wird für das Verwalten der NULL-Zulässigkeit der Spalte reserviert. Berechnen Sie dessen Größe:  
  
     _*_Null_Bitmap_*_  = 2 + ((_*_Num_Cols_*_ + 7) / 8)  
  
     Nur der ganzzahlige Teil des oben aufgeführten Ausdrucks sollte verwendet werden; verwerfen Sie den Nachkommateil.  
  
5.  Berechnen Sie die Größe der Daten variabler Länge:  
  
     Wenn die Tabelle Spalten variabler Länge enthält, müssen Sie den Speicherplatz ermitteln, der von den Spalten innerhalb der Zeile verwendet wird:  
  
     _*_Variable_Data_Size_*_  = 2 + (_*_Num_Variable_Cols_*_ × 2) + _*_Max_Var_Size_*_  
  
     Die zu _*_Max_Var_Size_*_ hinzugefügten Bytes dienen der Nachverfolgung jeder einzelnen variablen Spalte. Bei dieser Formel wird angenommen, dass alle Spalten variabler Länge zu 100 % gefüllt sind. Wenn sich abzeichnet, dass ein niedrigerer Prozentsatz des Speicherplatzes für Spalten mit variabler Länge verwendet wird, können Sie den Wert _*_Max_Var_Size_*_ mithilfe dieses Prozentsatzes anpassen, um einen genaueren Schätzwert für die Gesamtgröße der Tabelle zu erhalten.  
  
    > [!NOTE]  
    >  Sie können _*varchar**-, **nvarchar**-, **varbinary**- oder **sql_variant**-Spalten kombinieren, mit dem Ergebnis, dass die definierte Tabellengesamtbreite größer als 8060 Bytes ist. Die Länge jeder einzelnen Spalte unterliegt auch weiterhin der Beschränkung von 8.000 Byte für eine **varchar**-, **varbinary**- oder **sql_variant** -Spalte und von 4.000 Byte für **nvarchar** -Spalten. Die kombinierte Breite kann jedoch den Grenzwert von 8.060 Byte in einer Tabelle überschreiten.  
  
     Wenn keine Spalten mit variabler Länge vorhanden sind, legen Sie **_Variable_Data_Size_* _ auf 0 (null) fest.  
  
6.  Berechnen Sie die Gesamtzeilenlänge:  
  
     _*_Row_Size_*_  = _*_Fixed_Data_Size_*_ + _*_Variable_Data_Size_*_ + _*_Null_Bitmap_*_ + 4  
  
     Der Wert 4 ist der Zeilenüberschriftenaufwand der Datenzeile.  
  
7.  Berechnen Sie die Anzahl der Zeilen pro Seite (8.096 freie Byte pro Seite):  
  
     _*_Rows_Per_Page_*_  = 8096 / (_*_Row_Size_*_ + 2)  
  
     Da sich eine Zeile nicht auf zwei Seiten erstreckt, muss die Anzahl der Zeilen pro Seite auf die nächste ganze Zeile abgerundet werden. Die Angabe 2 in der Formel bezieht sich auf den Eingang der Zeile in das Slotarray der Seite.  
  
8.  Berechnen Sie die Anzahl der reservierten freien Zeilen pro Seite anhand des angegebenen [Füllfaktors](../../relational-databases/indexes/specify-fill-factor-for-an-index.md) :  
  
     _*_Free_Rows_Per_Page_*_  = 8096 × ((100 – _*_Fill_Factor_*_) / 100) / (_*_Row_Size_*_ + 2)  
  
     Bei dem in der Berechnung verwendeten Füllfaktor handelt es sich nicht um einen Prozentwert, sondern um einen ganzzahligen Wert. Da sich eine Zeile nicht auf zwei Seiten erstreckt, muss die Anzahl der Zeilen pro Seite auf die nächste ganze Zeile abgerundet werden. Mit ansteigendem Füllfaktor werden mehr Daten auf jeder Seite gespeichert, und die Anzahl der Seiten nimmt ab. Die Angabe 2 in der Formel bezieht sich auf den Eingang der Zeile in das Slotarray der Seite.  
  
9. Berechnen Sie die Anzahl der Seiten, die zum Speichern aller Zeilen benötigt werden:  
  
     _*_Num_Leaf_Pages_*_  = _*_Num_Rows_*_ / (_*_Rows_Per_Page_*_ - _*_Free_Rows_Per_Page_*_ )  
  
     Die geschätzte Seitenanzahl muss auf die nächste ganze Seite aufgerundet werden.  
  
10. Berechnen Sie den Umfang des Speicherplatzes, der zum Speichern der Daten in der Blattebene erforderlich ist (insgesamt 8192 Byte pro Seite):  
  
     _*_Leaf_space_used_*_  = 8192 × _*_Num_Leaf_Pages_*_  
  
## <a name="step-2-calculate-the-space-used-to-store-index-information"></a>Schritt 2: Berechnen des Speicherplatzes, der zum Speichern der Indexinformationen verwendet wird  
 Mit den folgenden Schritten können Sie den Umfang des Speicherplatzes schätzen, der zum Speichern der oberen Ebenen des Indexes erforderlich ist:  
  
1.  Geben Sie die Anzahl der Spalten mit fester und mit variabler Länge im Indexschlüssel an, und berechnen Sie den Speicherplatz, der für deren Speicherung erforderlich ist:  
  
     Die Schlüsselspalten eines Indexes können Spalten fester und variabler Länge enthalten. Um die Größe der Indexzeilen auf der inneren Ebene zu schätzen, müssen Sie den Speicherplatz berechnen, der von jeder dieser Spaltengruppen innerhalb der Indexzeile belegt wird. Die Größe einer Spalte hängt von der Angabe für Datentyp und -länge ab.  
  
     _*_Num_Key_Cols_*_ = Gesamtanzahl der Schlüsselspalten (mit fester und variabler Länge)  
  
     _*_Fixed_Key_Size_*_ = Gesamtzahl der Bytes in allen Schlüsselspalten mit fester Länge  
  
     _*_Num_Variable_Key_Cols_*_ = Anzahl der Schlüsselspalten mit variabler Länge  
  
     _*_Max_Var_Key_Size_*_ = Maximale Bytegröße aller Schlüsselspalten mit variabler Länge  
  
2.  Berücksichtigen Sie ggf. den Uniqueifier, der erforderlich ist, wenn der Index nicht eindeutig ist:  
  
     Die Uniqueifier-Spalte ist eine Spalte variabler Länge mit NULL-Zulässigkeit. Sie ist in Spalten Nicht-NULL und 4 Byte lang, deren Indexschlüsselwerte nicht eindeutig sind. Dieser Wert ist Teil des Indexschlüssels und für die Sicherstellung erforderlich, dass jede Zeile über einen eindeutigen Schlüsselwert verfügt.  
  
     _*_Num_Key_Cols_*_  = _*_Num_Key_Cols_*_ + 1  
  
     _*_Num_Variable_Key_Cols_*_  = _*_Num_Variable_Key_Cols_*_ + 1  
  
     _*_Max_Var_Key_Size_*_  = _*_Max_Var_Key_Size_*_ + 4  
  
     Diese Änderungen gehen davon aus, dass alle Werte nicht eindeutig sind.  
  
3.  Berechnen der Größe des NULL-Bitmusters:  
  
     Wenn der Index Spalten mit NULL-Zulässigkeit enthält, ist ein Teil der Indexzeile dem NULL-Bitmuster zugeordnet. Berechnen Sie dessen Größe:  
  
     _*_Index_Null_Bitmap_*_  = 2 + ((Anzahl der Spalten in der Indexzeile + 7) / 8)  
  
     Nur der ganzzahlige Teil des vorherigen Ausdrucks darf verwendet werden. Der Rest wird verworfen.  
  
     Wenn keine Schlüsselspalten vorhanden sind, die NULL-Werte zulassen, legen Sie _*_Index_Null_Bitmap_*_ auf 0 (null) fest.  
  
4.  Berechnen Sie die Größe der Daten variabler Länge:  
  
     Wenn der Index Spalten variabler Länge enthält, müssen Sie den Speicherplatz ermitteln, der von den Spalten innerhalb der Indexzeile verwendet wird:  
  
     _*_Variable_Key_Size_*_  = 2 + (_*_Num_Variable_Key_Cols_*_ × 2) + _*_Max_Var_Key_Size_*_  
  
     Die zu _*_Max_Var_Key_Size_*_ hinzugefügten Bytes dienen der Nachverfolgung der einzelnen Spalten mit variabler Länge. Bei dieser Formel wird angenommen, dass alle Spalten variabler Länge zu 100 % gefüllt sind. Wenn sich abzeichnet, dass ein niedrigerer Prozentsatz des Speicherplatzes für Spalten mit variabler Länge verwendet wird, können Sie den _*_Max_Var_Key_Size_*_-Wert mithilfe dieses Prozentsatzes anpassen, um einen genaueren Schätzwert für die Gesamtgröße der Tabelle zu erhalten.  
  
     Wenn keine Spalten mit variabler Länge vorhanden sind, legen Sie _*_Variable_Key_Size_*_ auf 0 (null) fest.  
  
5.  Berechnen Sie die Länge der Indexzeile:  
  
     _*_Index_Row_Size_*_  = _*_Fixed_Key_Size_*_ + _*_Variable_Key_Size_*_ + _*_Index_Null_Bitmap_*_ + 1 (für Zeilenheaderaufwand einer Indexzeile) + 6 (für ID-Zeiger der untergeordneten Seite)  
  
6.  Berechnen Sie die Anzahl der Indexzeilen pro Seite (8096 freie Byte pro Seite):  
  
     _*_Index_Rows_Per_Page_*_  = 8096 / (_*_Index_Row_Size_*_ + 2)  
  
     Da sich eine Indexzeile nicht auf zwei Seiten erstreckt, muss die Anzahl der Indexzeilen pro Seite auf die nächste ganze Zeile abgerundet werden. Die Angabe 2 in der Formel bezieht sich auf den Eingang der Zeile in das Slotarray der Seite.  
  
7.  Berechnen Sie die Anzahl der Ebenen im Index:  
  
     _*_Non-leaf_Levels_*_  = 1 + log (Index_Rows_Per_Page) (_*_Num_Leaf_Pages_*_ / _*_Index_Rows_Per_Page_*_)  
  
     Runden Sie diese Zahl auf die nächste ganze Zahl auf. Dieser Wert schließt die Blattebene des gruppierten Index nicht mit ein.  
  
8.  Berechnen Sie die Anzahl der inneren Knotenseiten im Index:  
  
     _*_Num_Index_Pages =_*_ ∑Level _*_ (Num_Leaf_Pages / (Index_Rows_Per_Page_ *_^Level_* _))_ *_  
  
     wobei 1 <= Level <= _*_Non-leaf_Levels_*_  
  
     Runden Sie jeden Summanden auf die nächste ganze Zahl auf. Stellen Sie sich als einfaches Beispiel einen Index vor, bei dem _*_Num_Leaf_Pages_*_ = 1000 und _*_Index_Rows_Per_Page_*_ = 25. Die erste Indexebene über der Blattebene speichert 1.000 Indexzeilen, dies bedeutet eine Indexzeile pro Blattseite. Dabei passen 25 Indexzeilen auf eine Seite. Dies bedeutet, dass 40 Seiten zum Speichern dieser 1.000 Indexzeilen erforderlich sind. Die nächste Ebene des Indexes muss 40 Zeilen speichern. Dies bedeutet, dass 2 Seiten erforderlich sind. Die letzte Ebene des Indexes muss zwei Zeilen speichern. Dies bedeutet, dass eine Seite erforderlich ist. Daraus ergeben sich 43 innere Knotenseiten im Index. Wenn Sie diese Werte in den oben genannten Formeln verwenden, ergibt sich Folgendes:  
  
     _*_Non-leaf_Levels_*_  = 1 + log(25) (1000 / 25) = 3  
  
     _*_Num_Index_Pages_*_ = 1000/(25^3)+ 1000/(25^2) + 1000/(25^1) = 1 + 2 + 40 = 43, was der Anzahl der Seiten im Beispiel entspricht.  
  
9. Berechnen Sie die Größe des Indexes (insgesamt 8.192 Byte pro Seite):  
  
     _*_Index_Space_Used_*_  = 8192 × _*_Num_Index_Pages_*_  
  
## <a name="step-3-total-the-calculated-values"></a>Schritt 3: Addieren der berechneten Werte  
 Addieren Sie die Werte, die in den beiden vorherigen Schritten erzielt wurden:  
  
 Größe des gruppierten Indexes (in Bytes) = _*_Leaf_Space_Used_*_ + _*_Index_Space_used_*_  
  
 In dieser Berechnung wird Folgendes nicht berücksichtigt:  
  
-   Partitionierung  
  
     Der Speicherplatzaufwand aus der Partitionierung ist geringfügig, seine Berechnung jedoch komplex. Er muss nicht berücksichtigt werden.  
  
-   Zuordnungsseiten  
  
     Mindestens eine IAM-Seite wird zum Nachverfolgen der für einen Heap zugeordneten Seiten verwendet, der Speicherplatzaufwand ist jedoch nur minimal. Außerdem ist kein Algorithmus verfügbar, um deterministisch genau zu berechnen, wie viele IAM-Seiten verwendet werden.  
  
-   LOB-Werte (Large Object)  
  
     Der Algorithmus zum Berechnen des genauen Speicherplatzes, der zum Speichern der Werte der LOB-Datentypen _*varchar(max)**, **varbinary(max)** , **nvarchar(max)** , **text**, **ntext**, **xml** und **image** erforderlich ist, ist komplex. Es ist ausreichend, einfach die durchschnittliche Größe der erwarteten LOB-Werte zu addieren, diese mit **_Num_Rows_** zu multiplizieren und das Ergebnis dann zur Gesamtgröße des gruppierten Indexes zu addieren.  
  
-   Komprimierung  
  
     Sie können die Größe eines komprimierten Index nicht im Vorfeld berechnen.  
  
-   Spalten mit geringer Dichte  
  
     Informationen zu den Speicherplatzanforderungen von Sparsespalten finden Sie unter [Use Sparse Columns](../../relational-databases/tables/use-sparse-columns.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beschreibung von gruppierten und nicht gruppierten Indizes](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md)   
 [Schätzen der Größe einer Tabelle](../../relational-databases/databases/estimate-the-size-of-a-table.md)   
 [Erstellen gruppierter Indizes](../../relational-databases/indexes/create-clustered-indexes.md)   
 [Erstellen nicht gruppierter Indizes](../../relational-databases/indexes/create-nonclustered-indexes.md)   
 [Schätzen der Größe eines nicht gruppierten Index](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md)   
 [Schätzen der Größe eines Heaps](../../relational-databases/databases/estimate-the-size-of-a-heap.md)   
 [Schätzen der Größe einer Datenbank](../../relational-databases/databases/estimate-the-size-of-a-database.md)  
  
  
