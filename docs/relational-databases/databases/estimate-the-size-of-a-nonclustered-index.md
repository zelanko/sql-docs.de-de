---
title: Schätzen der Größe eines nicht gruppierten Index | Microsoft-Dokumentation
description: Führen Sie dieses Verfahren durch, um einzuschätzen, wie viel Speicherplatz zum Speichern eines nicht gruppierten Index in SQL Server erforderlich ist.
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.reviewer: ''
ms.prod_service: database-engine, sql-database
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- space allocation [SQL Server], index size
- size [SQL Server], tables
- predicting table size [SQL Server]
- table size [SQL Server]
- estimating table size
- clustered indexes, table size
- designing databases [SQL Server], estimating size
- calculating table size
ms.assetid: c183b0e4-ef4c-4bfc-8575-5ac219c25b0a
author: stevestein
ms.author: sstein
monikerRange: = azuresqldb-current || >= sql-server-2016
ms.openlocfilehash: 9c234bb8371d99025bd97cfb86f5d85472d34ee4
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97474081"
---
# <a name="estimate-the-size-of-a-nonclustered-index"></a>Schätzen der Größe eines nicht gruppierten Index

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Befolgen Sie diese Schritte, um abzuschätzen, wie viel Speicherplatz zum Speichern eines nicht gruppierten Index erforderlich ist.  
  
1.  Berechnen Sie die Variablen zur Verwendung in Schritt 2 und 3.  
  
2.  Berechnen Sie den Speicherplatz, der zum Speichern der Indexinformationen in der Blattebene des nicht gruppierten Index verwendet wird.  
  
3.  Berechnen Sie den Speicherplatz, der zum Speichern der Indexinformationen in den inneren Knotenebenen des nicht gruppierten Index verwendet wird.  
  
4.  Addieren Sie die berechneten Werte.  
  
## <a name="step-1-calculate-variables-for-use-in-steps-2-and-3"></a>Schritt 1: Berechnen der zu verwendenden Variablen in Schritt 2 und 3  
 Mit den folgenden Schritten können Sie die Variablen berechnen, mit denen die Größe des Speicherplatzes geschätzt wird, die zum Speichern der oberen Ebenen des Indexes erforderlich ist.  
  
1.  Geben Sie die Anzahl der Zeilen an, die die Tabelle enthalten wird:  
  
     ***Num_Rows** _ = Anzahl der Zeilen in der Tabelle  
  
2.  Geben Sie die Anzahl der Spalten mit fester und mit variabler Länge im Indexschlüssel an, und berechnen Sie den Speicherplatz, der für deren Speicherung erforderlich ist:  
  
     Die Schlüsselspalten eines Indexes können Spalten fester und variabler Länge enthalten. Um die Größe der Indexzeilen auf der inneren Ebene zu schätzen, müssen Sie den Speicherplatz berechnen, der von jeder dieser Spaltengruppen innerhalb der Indexzeile belegt wird. Die Größe einer Spalte hängt von der Angabe für Datentyp und -länge ab.  
  
     _*_Num_Key_Cols_*_ = Gesamtanzahl der Schlüsselspalten (mit fester und variabler Länge)  
  
     _*_Fixed_Key_Size_*_ = Gesamtzahl der Bytes in allen Schlüsselspalten mit fester Länge  
  
     _*_Num_Variable_Key_Cols_*_ = Anzahl der Schlüsselspalten mit variabler Länge  
  
     _*_Max_Var_Key_Size_*_ = Maximale Bytegröße aller Schlüsselspalten mit variabler Länge  
  
3.  Berücksichtigen Sie auch den Datenzeilenlokator, der erforderlich ist, wenn der Index nicht eindeutig ist:  
  
     Wenn der nicht gruppierte Index nicht eindeutig ist, wird der Datenzeilenlokator mit dem Schlüssel des nicht gruppierten Indexes kombiniert, um einen eindeutigen Schlüsselwert für jede Zeile zu erstellen.  
  
     Wenn sich der nicht gruppierte Index über einem Heap befindet, ist der Datenzeilenlokator die Heap-RID. Die Größe beträgt dann 8 Byte.  
  
     _*_Num_Key_Cols_*_  = _*_Num_Key_Cols_*_ + 1  
  
     _*_Num_Variable_Key_Cols_*_  = _*_Num_Variable_Key_Cols_*_ + 1  
  
     _*_Max_Var_Key_Size_*_  = _*_Max_Var_Key_Size_*_ + 8  
  
     Wenn sich der nicht gruppierte Index über einem gruppierten Index befindet, dann ist der Datenzeilenlokator der Gruppierungsschlüssel. Bei den Spalten, die mit dem nicht gruppierten Index kombiniert werden müssen, handelt es sich um die im Gruppierungsschlüssel enthaltenen Spalten, die noch nicht in der Menge der nicht gruppierten Indexschlüsselspalten vorhanden sind.  
  
     _*_Num_Key_Cols_*_  = _*_Num_Key_Cols_*_ + Anzahl der Gruppierungsschlüsselspalten, die nicht in den nicht gruppierten Indexschlüsselspalten vorhanden sind (+ 1, wenn der gruppierte Index nicht eindeutig ist)  
  
     _*_Fixed_Key_Size_*_  = _*_Fixed_Key_Size_*_ + Gesamtanzahl der Bytes in allen Gruppierungsschlüsselspalten mit fester Länge, die nicht in den nicht gruppierten Indexschlüsselspalten vorhanden sind  
  
     _*_Num_Variable_Key_Cols_*_  = _*_Num_Variable_Key_Cols_*_ + Anzahl der Gruppierungsschlüsselspalten mit variabler Länge, die nicht in den nicht gruppierten Indexschlüsselspalten vorhanden sind (+ 1, wenn der gruppierte Index nicht eindeutig ist)  
  
     _*_Max_Var_Key_Size_*_  = _*_Max_Var_Key_Size_*_ + maximale Anzahl der Bytes in den Gruppierungsschlüsselspalten mit variabler Länge, die nicht in den nicht gruppierten Indexschlüsselspalten vorhanden sind (+ 4, wenn der gruppierte Index nicht eindeutig ist)  
  
4.  Ein Teil der Zeile, der als NULL-Bitmuster bezeichnet wird, kann für das Verwalten der NULL-Zulässigkeit der Spalte reserviert sein. Berechnen Sie dessen Größe:  
  
     Wenn der Indexschlüssel Spalten enthält, die NULL-Werte zulassen (einschließlich erforderlicher Gruppierungsschlüsselspalten wie in Schritt 1.3 beschrieben), ist ein Teil der Indexzeile für das NULL-Bitmuster reserviert.  
  
     _*_Index_Null_Bitmap_*_  = 2 + ((Anzahl der Spalten in der Indexzeile + 7) / 8)  
  
     Nur der ganzzahlige Teil des vorherigen Ausdrucks darf verwendet werden. Der Rest wird verworfen.  
  
     Wenn keine Schlüsselspalten vorhanden sind, die NULL-Werte zulassen, legen Sie _*_Index_Null_Bitmap_*_ auf 0 (null) fest.  
  
5.  Berechnen Sie die Größe der Daten variabler Länge:  
  
     Wenn der Indexschlüssel Spalten variabler Länge enthält (einschließlich erforderlicher Schlüsselspalten des gruppierten Indexes), müssen Sie ermitteln, wie viel Speicherplatz zum Speichern der Spalten innerhalb der Indexzeile verwendet wird:  
  
     _*_Variable_Key_Size_*_  = 2 + (_*_Num_Variable_Key_Cols_*_ × 2) + _*_Max_Var_Key_Size_*_  
  
     Die zu _*_Max_Var_Key_Size_*_ hinzugefügten Bytes dienen der Nachverfolgung jeder einzelnen Variablenspalte. Bei dieser Formel wird angenommen, dass alle Spalten mit variabler Länge zu 100 Prozent gefüllt sind. Wenn sich abzeichnet, dass ein niedrigerer Prozentsatz des Speicherplatzes für Spalten mit variabler Länge verwendet wird, können Sie den _*_Max_Var_Key_Size_*_-Wert mithilfe dieses Prozentsatzes anpassen, um einen genaueren Schätzwert für die Gesamtgröße der Tabelle zu erhalten.  
  
     Wenn keine Spalten mit variabler Länge vorhanden sind, legen Sie _*_Variable_Key_Size_*_ auf 0 (null) fest.  
  
6.  Berechnen Sie die Länge der Indexzeile:  
  
     _*_Index_Row_Size_*_  = _*_Fixed_Key_Size_*_ + _*_Variable_Key_Size_*_ + _*_Index_Null_Bitmap_*_ + 1 (für Zeilenheaderaufwand einer Indexzeile) + 6 (für ID-Zeiger der untergeordneten Seite)  
  
7.  Berechnen Sie die Anzahl der Indexzeilen pro Seite (8096 freie Byte pro Seite):  
  
     _*_Index_Rows_Per_Page_*_  = 8096 / (_*_Index_Row_Size_*_ + 2)  
  
     Da sich eine Indexzeile nicht auf zwei Seiten erstreckt, muss die Anzahl der Indexzeilen pro Seite auf die nächste ganze Zeile abgerundet werden. Die Angabe 2 in der Formel bezieht sich auf den Eingang der Zeile in das Slotarray der Seite.  
  
## <a name="step-2-calculate-the-space-used-to-store-index-information-in-the-leaf-level"></a>Schritt 2: Berechnen des Speicherplatzes, der zum Speichern der Indexinformationen in der Blattebene verwendet wird  
 Mit den folgenden Schritten können Sie den Umfang des Speicherplatzes schätzen, der zum Speichern der Blattebene des Indexes erforderlich ist. Sie benötigen die in Schritt 1 aufgezeichneten Werte, um diesen Schritt durchführen zu können.  
  
1.  Geben Sie die Anzahl der Spalten mit fester und mit variabler Länge auf Blattebene an, und berechnen Sie den Speicherplatz, der für deren Speicherung erforderlich ist:  
  
    > [!NOTE]  
    >  Sie können einen nicht gruppierten Index erweitern, indem Nichtschlüsselspalten zusätzlich zu Indexschlüsselspalten eingeschlossen werden. Diese zusätzlichen Spalten werden auf der Blattebene des nicht gruppierten Indexes gespeichert. Weitere Informationen finden Sie unter [Create Indexes with Included Columns](../../relational-databases/indexes/create-indexes-with-included-columns.md).  
  
    > [!NOTE]  
    >  Sie können _*varchar**-, **nvarchar**-, **varbinary**- oder **sql_variant**-Spalten kombinieren, mit dem Ergebnis, dass die definierte Tabellengesamtbreite größer als 8060 Bytes ist. Die Länge jeder einzelnen Spalte unterliegt auch weiterhin der Beschränkung von 8.000 Byte für eine **varchar**-, **varbinary**- oder **sql_variant** -Spalte und von 4.000 Byte für **nvarchar** -Spalten. Die kombinierte Breite kann jedoch den Grenzwert von 8.060 Byte in einer Tabelle überschreiten. Dies gilt auch für die Zeilen auf Blattebene eines nicht gruppierten Indexes, die eingeschlossene Spalten enthalten.  
  
     Wenn der nicht gruppierte Index keine eingeschlossenen Spalten besitzt, verwenden Sie die Werte aus Schritt 1 einschließlich aller Änderungen, die ggf. in Schritt 1.3 vorgenommen wurden:  
  
     **_Num_Leaf_Cols_* _  = _*_Num_Key_Cols_*_  
  
     _*_Fixed_Leaf_Size_*_  = _*_Fixed_Key_Size_*_  
  
     _*_Num_Variable_Leaf_Cols_*_  = _*_Num_Variable_Key_Cols_*_  
  
     _*_Max_Var_Leaf_Size_*_  = _*_Max_Var_Key_Size_*_  
  
     Wenn der nicht gruppierte Index keine eingeschlossenen Spalten besitzt, fügen Sie die entsprechenden Werte den Werten aus Schritt 1 einschließlich allen Änderungen, die ggf. in Schritt 1.3 vorgenommen wurden, hinzu. Die Größe einer Spalte hängt von der Angabe für Datentyp und -länge ab. Weitere Informationen finden Sie unter [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md).  
  
     _*_Num_Leaf_Cols_*_  = _*_Num_Key_Cols_*_ + Anzahl der enthaltenen Spalten  
  
     _*_Fixed_Leaf_Size_*_  = _*_Fixed_Key_Size_*_ + Gesamtzahl der Bytes der enthaltenen Schlüsselspalten mit fester Länge  
  
     _*_Num_Variable_Leaf_Cols_*_  = _*_Num_Variable_Key_Cols_*_ + Anzahl der enthaltenen Spalten mit variabler Länge  
  
     _*_Max_Var_Leaf_Size_*_  = _*_Max_Var_Key_Size_*_ + Maximale Bytegröße der enthaltenen Spalten mit variabler Länge  
  
2.  Konto für den Datenzeilenlokator:  
  
     Wenn der nicht gruppierte Index nicht eindeutig ist, wurde der Aufwand für den Datenzeilenlokator bereits in Schritt 1.3 berücksichtigt. In diesem Fall sind keine zusätzlichen Änderungen erforderlich. Fahren Sie mit dem nächsten Schritt fort.  
  
     Wenn der nicht gruppierte Index eindeutig ist, muss der Datenzeilenlokator in allen Zeilen auf der Blattebene berücksichtigt werden.  
  
     Wenn sich der nicht gruppierte Index über einem Heap befindet, ist der Datenzeilenlokator die Heap-RID (Größe 8 Byte).  
  
     _*_Num_Leaf_Cols_*_  = _*_Num_Leaf_Cols_*_ + 1  
  
     _*_Num_Variable_Leaf_Cols_*_  = _*_Num_Variable_Leaf_Cols_*_ + 1  
  
     _*_Max_Var_Leaf_Size_*_  = _*_Max_Var_Leaf_Size_*_ + 8  
  
     Wenn sich der nicht gruppierte Index über einem gruppierten Index befindet, dann ist der Datenzeilenlokator der Gruppierungsschlüssel. Bei den Spalten, die mit dem nicht gruppierten Index kombiniert werden müssen, handelt es sich um die im Gruppierungsschlüssel enthaltenen Spalten, die noch nicht in der Menge der nicht gruppierten Indexschlüsselspalten vorhanden sind.  
  
     _*_Num_Leaf_Cols_*_  = _*_Num_Leaf_Cols_*_ + Anzahl der Gruppierungsschlüsselspalten, die nicht in den nicht gruppierten Indexschlüsselspalten vorhanden sind (+ 1, wenn der gruppierte Index nicht eindeutig ist)  
  
     _*_Fixed_Leaf_Size_*_  = _*_Fixed_Leaf_Size_*_ + Anzahl der Bytes in allen Gruppierungsschlüsselspalten mit fester Länge, die nicht in den nicht gruppierten Indexschlüsselspalten vorhanden sind  
  
     _*_Num_Variable_Leaf_Cols_*_  = _*_Num_Variable_Leaf_Cols_*_ + Anzahl der Gruppierungsschlüsselspalten mit variabler Länge, die nicht in den nicht gruppierten Indexschlüsselspalten vorhanden sind (+ 1, wenn der gruppierte Index nicht eindeutig ist)  
  
     _*_Max_Var_Leaf_Size_*_  = _*_Max_Var_Leaf_Size_*_ + Anzahl der Bytes in den Gruppierungsschlüsselspalten mit variabler Länge, die nicht in den nicht gruppierten Indexschlüsselspalten vorhanden sind (+ 4, wenn der gruppierte Index nicht eindeutig ist)  
  
3.  Berechnen der Größe des NULL-Bitmusters:  
  
     _*_Leaf_Null_Bitmap_*_  = 2 + ((_*_Num_Leaf_Cols_*_ + 7) / 8)  
  
     Nur der ganzzahlige Teil des vorherigen Ausdrucks darf verwendet werden. Der Rest wird verworfen.  
  
4.  Berechnen Sie die Größe der Daten variabler Länge:  
  
     Wenn Spalten mit variabler Länge (Schlüsselspalten oder eingeschlossene Spalten) vorliegen, einschließlich erforderlicher Gruppierungsschlüsselspalten (siehe Schritt 2.2), müssen Sie ermitteln, wie viel Speicherplatz zum Speichern der Spalten in der Indexzeile verwendet wird:  
  
     _*_Variable_Leaf_Size_*_  = 2 + (_*_Num_Variable_Leaf_Cols_*_ × 2) + _*_Max_Var_Leaf_Size_*_  
  
     Die zu _*_Max_Var_Key_Size_*_ hinzugefügten Bytes dienen der Nachverfolgung jeder einzelnen Variablenspalte. Bei dieser Formel wird angenommen, dass alle Spalten mit variabler Länge zu 100 Prozent gefüllt sind. Wenn sich abzeichnet, dass ein niedrigerer Prozentsatz des Speicherplatzes für Spalten mit variabler Länge verwendet wird, können Sie den _*_Max_Var_Leaf_Size_*_-Wert mithilfe dieses Prozentsatzes anpassen, um einen genaueren Schätzwert für die Gesamtgröße der Tabelle zu erhalten.  
  
     Wenn keine Spalten mit variabler Länge (Schlüsselspalten oder eingeschlossene Spalten) vorliegen, legen Sie _*_Variable_Leaf_Size_*_ auf 0 (null) fest.  
  
5.  Berechnen Sie die Länge der Indexzeile:  
  
     _*_Leaf_Row_Size_*_  = _*_Fixed_Leaf_Size_*_ + _*_Variable_Leaf_Size_*_ + _*_Leaf_Null_Bitmap_*_ + 1 (für Zeilenheaderaufwand einer Indexzeile)  
  
6.  Berechnen Sie die Anzahl der Indexzeilen pro Seite (8096 freie Byte pro Seite):  
  
     _*_Leaf_Rows_Per_Page_*_  = 8096 / (_*_Leaf_Row_Size_*_ + 2)  
  
     Da sich eine Indexzeile nicht auf zwei Seiten erstreckt, muss die Anzahl der Indexzeilen pro Seite auf die nächste ganze Zeile abgerundet werden. Die Angabe 2 in der Formel bezieht sich auf den Eingang der Zeile in das Slotarray der Seite.  
  
7.  Berechnen Sie die Anzahl der reservierten freien Zeilen pro Seite anhand des angegebenen [Füllfaktors](../../relational-databases/indexes/specify-fill-factor-for-an-index.md) :  
  
     _*_Free_Rows_Per_Page_*_  = 8096 × ((100 - _*_Fill_Factor_*_) / 100) / (_*_Leaf_Row_Size_*_ + 2)  
  
     Bei dem in der Berechnung verwendeten Füllfaktor handelt es sich nicht um einen Prozentwert, sondern um einen ganzzahligen Wert. Da sich eine Zeile nicht auf zwei Seiten erstreckt, muss die Anzahl der Zeilen pro Seite auf die nächste ganze Zeile abgerundet werden. Mit ansteigendem Füllfaktor werden mehr Daten auf jeder Seite gespeichert, und die Anzahl der Seiten nimmt ab. Die Angabe 2 in der Formel bezieht sich auf den Eingang der Zeile in das Slotarray der Seite.  
  
8.  Berechnen Sie die Anzahl der Seiten, die zum Speichern aller Zeilen benötigt werden:  
  
     _*_Num_Leaf_Pages_*_  = _*_Num_Rows_*_ / (_*_Leaf_Rows_Per_Page_*_ - _*_Free_Rows_Per_Page_*_ )  
  
     Die geschätzte Seitenanzahl muss auf die nächste ganze Seite aufgerundet werden.  
  
9. Berechnen Sie die Größe des Indexes (insgesamt 8.192 Byte pro Seite):  
  
     _*_Leaf_Space_Used_*_  = 8192 × _*_Num_Leaf_Pages_*_  
  
## <a name="step-3-calculate-the-space-used-to-store-index-information-in-the-non-leaf-levels"></a>Schritt 3: Berechnen des Speicherplatzes, der zum Speichern der Indexinformationen in den inneren Knotenebenen verwendet wird  
 Befolgen Sie diese Schritte, um abzuschätzen, wie viel Speicherplatz zum Speichern der Zwischen- und Stammebenen des Indexes erforderlich ist. Sie benötigen die in Schritt 2 und 3 errechneten Werte, um diesen Schritt durchführen zu können.  
  
1.  Berechnen Sie die Anzahl der inneren Knotenebenen im Index:  
  
     _*_Non-leaf_Levels_*_  = 1 + log( Index_Rows_Per_Page) (_*_Num_Leaf_Pages_*_ / _*_Index_Rows_Per_Page_*_)  
  
     Runden Sie diese Zahl auf die nächste ganze Zahl auf. Dieser Wert schließt die Blattebene des nicht gruppierten Index nicht mit ein.  
  
2.  Berechnen Sie die Anzahl der inneren Knotenseiten im Index:  
  
     _*_Num_Index_Pages_*_  = ∑Level (_*_Num_Leaf_Pages/Index_Rows_Per_Page_*_^Level), wobei 1 <= Level <= _*_Levels_*_  
  
     Runden Sie jeden Summanden auf die nächste ganze Zahl auf. Stellen Sie sich als einfaches Beispiel einen Index vor, bei dem _*_Num_Leaf_Pages_*_ = 1000 und _*_Index_Rows_Per_Page_*_ = 25. Die erste Indexebene über der Blattebene speichert 1.000 Indexzeilen, dies bedeutet eine Indexzeile pro Blattseite. Dabei passen 25 Indexzeilen auf eine Seite. Dies bedeutet, dass 40 Seiten zum Speichern dieser 1.000 Indexzeilen erforderlich sind. Die nächste Ebene des Indexes muss 40 Zeilen speichern. Dies bedeutet, dass zwei Seiten erforderlich sind. Die letzte Ebene des Indexes muss zwei Zeilen speichern. Dies bedeutet, dass eine Seite erforderlich ist. Daraus ergeben sich 43 innere Knotenseiten im Index. Wenn Sie diese Werte in den oben genannten Formeln verwenden, erhalten Sie folgendes Ergebnis:  
  
     _*_Non-leaf_Levels_*_  = 1 + log(25) (1000 / 25) = 3  
  
     _*_Num_Index_Pages_*_ = 1000/(25^3)+ 1000/(25^2) + 1000/(25^1) = 1 + 2 + 40 = 43, was der Anzahl der Seiten im Beispiel entspricht.  
  
3.  Berechnen Sie die Größe des Indexes (insgesamt 8.192 Byte pro Seite):  
  
     _*_Index_Space_Used_*_  = 8192 × _*_Num_Index_Pages_*_  
  
## <a name="step-4-total-the-calculated-values"></a>Schritt 4. Addieren der berechneten Werte  
 Addieren Sie die Werte, die in den beiden vorherigen Schritten erzielt wurden:  
  
 Größe des nicht gruppierten Indexes (in Bytes) = _*_Leaf_Space_Used_*_ + _*_Index_Space_used_*_  
  
 In dieser Berechnung wird Folgendes nicht berücksichtigt:  
  
-   Partitionierung  
  
     Der Speicherplatzaufwand aus der Partitionierung ist geringfügig, seine Berechnung jedoch komplex. Er muss nicht berücksichtigt werden.  
  
-   Zuordnungsseiten  
  
     Mindestens eine IAM-Seite wird zum Nachverfolgen der für einen Heap zugeordneten Seiten verwendet, der Speicherplatzaufwand ist jedoch nur minimal. Außerdem ist kein Algorithmus verfügbar, um deterministisch genau zu berechnen, wie viele IAM-Seiten verwendet werden.  
  
-   LOB-Werte (Large Object)  
  
     Der Algorithmus zum Berechnen des genauen Speicherplatzes, der zum Speichern der Werte der LOB-Datentypen _*varchar(max)**, **varbinary(max)** , **nvarchar(max)** , **text**, **ntext**, **xml** und **image** erforderlich ist, ist komplex. Es ist ausreichend, einfach die durchschnittliche Größe der erwarteten LOB-Werte zu addieren, diese mit **_Num_Rows_** zu multiplizieren und das Ergebnis dann zur Gesamtgröße des nicht gruppierten Indexes zu addieren.  
  
-   Komprimierung  
  
     Sie können die Größe eines komprimierten Index nicht im Vorfeld berechnen.  
  
-   Spalten mit geringer Dichte  
  
     Informationen zu den Speicherplatzanforderungen von Sparsespalten finden Sie unter [Use Sparse Columns](../../relational-databases/tables/use-sparse-columns.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beschreibung von gruppierten und nicht gruppierten Indizes](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md)   
 [Erstellen nicht gruppierter Indizes](../../relational-databases/indexes/create-nonclustered-indexes.md)   
 [Erstellen gruppierter Indizes](../../relational-databases/indexes/create-clustered-indexes.md)   
 [Schätzen der Größe einer Tabelle](../../relational-databases/databases/estimate-the-size-of-a-table.md)   
 [Schätzen der Größe eines gruppierten Indexes](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md)   
 [Schätzen der Größe eines Heaps](../../relational-databases/databases/estimate-the-size-of-a-heap.md)   
 [Schätzen der Größe einer Datenbank](../../relational-databases/databases/estimate-the-size-of-a-database.md)  
  
  
