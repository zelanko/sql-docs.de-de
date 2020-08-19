---
description: Aggregatfunktionen, die CALC-Funktion und das NEW-Schlüsselwort
title: Aggregatfunktionen, die Calc-Funktion und das New-Schlüsselwort | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: ad6bf4b041fbae0f30e327bd32dd067c1e9c429a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453752"
---
# <a name="aggregate-functions-the-calc-function-and-the-new-keyword"></a>Aggregatfunktionen, die CALC-Funktion und das NEW-Schlüsselwort
Die Daten Strukturierung unterstützt die folgenden Funktionen. Der Name, der dem Kapitel mit der zu verwendenden Spalte zugewiesen ist, ist das *Kapitel-Alias*.  
  
 Ein Kapitel-Alias kann voll qualifiziert sein, bestehend aus jedem Kapitel Spaltennamen, der zu dem Kapitel mit dem *Spaltennamen führt,* der alle durch Zeiträume getrennt ist. Wenn das übergeordnete Kapitel chap1 beispielsweise ein untergeordnetes Kapitel chap2 enthält, das eine Spalte Amount (Amt) aufweist, lautet der qualifizierte Name chap1. chap2. Amt.  
  
|Aggregatfunktionen|Beschreibung|  
|-------------------------|-----------------|  
|Sum (*Chapter-Alias*.* Spaltenname*)|Berechnet die Summe aller Werte in der angegebenen Spalte.|  
|AVG (*Chapter-Alias*.* Spaltenname*)|Berechnet den Durchschnitt aller Werte in der angegebenen Spalte.|  
|Max (*Chapter-Alias*.* Spaltenname*)|Berechnet den maximalen Wert in der angegebenen Spalte.|  
|MIN (*Kapitel-Alias*).* Spaltenname*)|Berechnet den minimalen Wert in der angegebenen Spalte.|  
|COUNT (*Chapter-Alias*[.* Spaltenname*])|Zählt die Anzahl der Zeilen im angegebenen Alias. Wenn eine Spalte angegeben wird, werden nur Zeilen, für die diese Spalte nicht NULL ist, in die Anzahl eingeschlossen.|  
|StDev (*Chapter-Alias*.* Spaltenname*)|Berechnet die Standardabweichung in der angegebenen Spalte.|  
|Any (*Chapter-Alias*.* Spaltenname*)|Ein Wert der angegebenen Spalte. ANY hat nur dann einen vorhersagbaren Wert, wenn der Wert der-Spalte für alle Zeilen im Kapitel gleich ist.<br /><br /> **Hinweis** Wenn die Spalte nicht denselben Wert für alle Zeilen im Kapitel enthält, gibt der Shape-Befehl willkürlich einen der-Werte als Wert der any-Funktion zurück.|  
  
|Berechneter Ausdruck|Beschreibung|  
|---------------------------|-----------------|  
|Calc (*Ausdruck*)|Berechnet einen beliebigen Ausdruck, aber nur in der Zeile des **Recordsets** , das die Calc-Funktion enthält. Jeder Ausdruck, der diese [Visual Basic for Applications Funktionen (VBA)](../../../ado/guide/data/visual-basic-for-applications-functions.md) verwendet, ist zulässig.|  
  
|New-Schlüsselwort|Beschreibung|  
|-----------------|-----------------|  
|Neuer *Feldtyp* [(*Breite* &#124; *Skala* &#124; *Genauigkeit* &#124; *Fehler* [, *skalieren* &#124; *Fehler*])]|Fügt dem **Recordset**eine leere Spalte vom angegebenen Typ hinzu.|  
  
 Der *Feldtyp* , der mit dem New-Schlüsselwort übermittelt wird, kann einen der folgenden Datentypen aufweisen.  
  
|Datentypen OLE DB|ADO-Datentyp Äquivalent (s)|  
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
|DBTYPE_BYTES|adbinary, adVarBinary, adLongVarBinary|  
|DBTYPE_STR|adchar, adVarChar, adLongVarChar|  
|DBTYPE_WSTR|adwchar, adVarWchar, adLongVarWChar|  
|DBTYPE_NUMERIC|adNumeric|  
|DBTYPE_DBDATE|adDBDate|  
|DBTYPE_DBTIME|adDBTime|  
|DBTYPE_DBTIMESTAMP|adDBTimeStamp|  
|DBTYPE_VARNUMERIC|adVarNumeric|  
|DBTYPE_FILETIME|adFileTime|  
|DBTYPE_ERROR|adError|  
  
 Wenn das neue Feld den Typ Decimal hat (in OLE DB, DBTYPE_DECIMAL oder in ADO, addecimal), müssen Sie die Werte für Genauigkeit und Dezimalstelle angeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Beispiel für Daten Strukturierung](../../../ado/guide/data/data-shaping-example.md)   
 [Formale Form Grammatik](../../../ado/guide/data/formal-shape-grammar.md)   
 [Shape-Befehle im Allgemeinen](../../../ado/guide/data/shape-commands-in-general.md)
