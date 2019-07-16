---
title: Aggregieren von Funktionen, die CALC-Funktion und das neue Schlüsselwort | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data shaping [ADO], functions
- CALC function [ADO]
- NEW keyword [ADO]
- aggregate functions [ADO]
ms.assetid: 0590b466-2a36-49a2-868e-028ef5e49394
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5a7ed836b9b57ddd690dd85dd94cc12cb967c472
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67926009"
---
# <a name="aggregate-functions-the-calc-function-and-the-new-keyword"></a>Aggregatfunktionen, die CALC-Funktion und das NEW-Schlüsselwort
Strukturieren von Daten unterstützt die folgenden Funktionen. Zugewiesene finden Sie im Kapitel mit der Spalte verwendet werden. Name ist der *Kapitel-Alias*.  
  
 Ein Kapitel-Alias kann vollqualifiziert sein bestehend aus den einzelnen Spaltennamen im Kapitel zum Kapitel mit führenden der *Spaltenname,* durch Punkte getrennt. Angenommen, wenn das übergeordnete Kapitel Kap1, untergeordnete Kapitel chap2, enthält, die eine Mengenspalte "Amt" hat und dann der qualifizierte Name wäre chap1.chap2.amt.  
  
|Aggregatfunktionen|Beschreibung|  
|-------------------------|-----------------|  
|SUM (*Kapitel-Alias*. *Spaltenname*)|Berechnet die Summe aller Werte in der angegebenen Spalte.|  
|AVG (*Kapitel-Alias*. *Spaltenname*)|Berechnet den Durchschnitt aller Werte in der angegebenen Spalte.|  
|MAX (*Kapitel-Alias*. *Spaltenname*)|Berechnet den maximalen Wert in der angegebenen Spalte.|  
|MIN (*Kapitel-Alias*. *Spaltenname*)|Berechnet den Mindestwert in der angegebenen Spalte an.|  
|COUNT (*Kapitel-Alias*[. *Spaltenname*])|Zählt die Anzahl der Zeilen in den angegebenen Alias. Wenn eine Spalte angegeben wird, sind nur Zeilen, die für die diese Spalte ungleich Null ist in der Zählung enthalten.|  
|STDEV (*Kapitel-Alias*. *Spaltenname*)|Berechnet die Standardabweichung in der angegebenen Spalte an.|  
|Alle (*Kapitel-Alias*. *Spaltenname*)|Ein Wert der angegebenen Spalte. Alle hat einen vorhersagbaren Wert nur, wenn der Wert der Spalte für alle Zeilen im Kapitel identisch ist.<br /><br /> **Beachten Sie** Wenn die Spalte nicht den gleichen Wert für alle Zeilen in das Kapitel enthält, gibt die SHAPE-Befehl nach dem Zufallsprinzip einen der Werte auf den Wert der ANY-Funktion.|  
  
|berechneter Ausdruck|Beschreibung|  
|---------------------------|-----------------|  
|CALC (*Ausdruck*)|Berechnet einen beliebigen Ausdruck, jedoch nur in der Zeile mit der **Recordset** , die die CALC-Funktion enthält. Ein Ausdruck, der mit diesen [Visual Basic für Applikationen (VBA) Funktionen](../../../ado/guide/data/visual-basic-for-applications-functions.md) ist zulässig.|  
  
|NEW-Schlüsselwort|Beschreibung|  
|-----------------|-----------------|  
|NEUE *Feldtyp* [(*Breite* &#124; *Skalierung* &#124; *Genauigkeit* &#124; *Fehler*[, *Skalierung* &#124; *Fehler*])]|Fügt eine leere Spalte des angegebenen Typs, der **Recordset**.|  
  
 Die *Feldtyp* mit dem neuen Schlüsselwort übergeben werden können, eine der folgenden Datentypen.  
  
|OLE DB-Datentypen|ADO-Datentyp equivalent(s)|  
|-----------------------|-----------------------------------|  
|DBTYPE_BSTR|adBSTR|  
|DBTYPE_BOOL|adBoolean|  
|DBTYPE_DECIMAL|adDecimal|  
|DBTYPE_UI1|adUnsignedTinyInt|  
|DBTYPE_I1|adTinyInt|  
|DBTYPE_UI2|adUnsignedSmallInt|  
|DBTYPE_UI4|adUnsignedInt|  
|DBTYPE_I8|adBigInt|  
|DBTYPE_UI8|adUnsignedBigInt|  
|DBTYPE_GUID|adGuid|  
|DBTYPE_BYTES|AdBinary, AdVarBinary, adLongVarBinary|  
|DBTYPE_STR|adChar, adVarChar, adLongVarChar|  
|DBTYPE_WSTR|adWChar, adVarWChar, adLongVarWChar|  
|DBTYPE_NUMERIC|Type|  
|DBTYPE_DBDATE|adDBDate|  
|DBTYPE_DBTIME|adDBTime|  
|DBTYPE_DBTIMESTAMP|adDBTimeStamp|  
|DBTYPE_VARNUMERIC|adVarNumeric|  
|DBTYPE_FILETIME|adFileTime|  
|DBTYPE_ERROR|adError|  
  
 Wenn das neue Feld vom Typ Decimal (in OLE DB DBTYPE_DECIMAL, oder in ADO AdDecimal) ist, müssen Sie die Genauigkeit und Dezimalstellenanzahl Werte angeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Beispiel für die datenstrukturierung](../../../ado/guide/data/data-shaping-example.md)   
 [Formale Grammatik für Formen](../../../ado/guide/data/formal-shape-grammar.md)   
 [Shape-Befehle im Allgemeinen](../../../ado/guide/data/shape-commands-in-general.md)
