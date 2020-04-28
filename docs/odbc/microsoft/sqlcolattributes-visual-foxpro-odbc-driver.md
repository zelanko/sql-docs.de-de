---
title: SQLColAttribute (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColAttribute function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: d403dfa0-c26d-47d4-91d9-2f29aa387399
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9508fa7b9ada8273e1250d7584e577892acf5c51
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307911"
---
# <a name="sqlcolattributes-visual-foxpro-odbc-driver"></a>SQLColAttributes (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Unterstützung: vollständig  
  
 ODBC-API-Konformität: kernstufe  
  
 Gibt Deskriptorinformationen für eine Spalte in einem Resultset zurück. Deskriptorinformationen werden als Zeichenfolge, als 32-Bit-deskriptorabhängige Werte oder als ganzzahliger Wert zurückgegeben.  
  
> [!NOTE]  
>  **SQLColAttribute** können nicht zum Zurückgeben von Informationen über die Lesezeichen Spalte (Spalte 0) verwendet werden.  
  
 Der Visual FoxPro-ODBC-Treiber unterstützt alle Werte des *Typs* "vollständig". In der folgenden Tabelle sind Kommentare zur Implementierung ausgewählter Werte des Treibers enthalten.  
  
|*Typ "Typ"*|Kommentar|  
|-----------------|-------------|  
|SQL_COLUMN_AUTO_INCREMENT|Gibt false zurück: Visual FoxPro enthält keine Counter-Felder.|  
|SQL_COLUMN_CASE_SENSITIVE|Gibt immer true zurück, wenn der Spaltentyp ein Zeichen ist.|  
|SQL_COLUMN_LABEL|Gibt den Spaltennamen zurück, der ebenfalls von SQL_COLUMN_NAME zurückgegeben wird.|  
|SQL_COLUMN_MONEY|Gibt "true" zurück, wenn der Spaltentyp "Currency" (dargestellt durch "Y" in der Sprache von Visual FoxPro) ist.|  
|SQL_COLUMN_OWNER_NAME|Gibt immer eine leere Zeichenfolge zurück|  
|SQL_COLUMN_QUALIFIER_NAME|Gibt immer eine leere Zeichenfolge zurück|  
|SQL_COLUMN_SEARCHABLE|Gibt SQL_UNSEARCHABLE für Spalten vom Typ "Allgemein" zurück. Diese Spalten können nicht in einer WHERE-Klausel verwendet werden.<br /><br /> Gibt SQL_SEARCHABLE für Spalten vom Typ ' character ' oder ' Memo ' zurück, bei denen ' nocptrans ' nicht Diese Spalten können in einer WHERE-Klausel mit einem beliebigen Vergleichs Operator verwendet werden.<br /><br /> Gibt SQL_ALL_EXCEPT_LIKE für alle anderen Spaltentypen zurück. Diese Spalten können in einer WHERE-Klausel mit allen Vergleichs Operatoren mit Ausnahme von like verwendet werden.|  
|SQL_COLUMN_TABLE_NAME|Gibt immer eine leere Zeichenfolge zurück|  
  
 Weitere Informationen finden Sie unter [SQLColAttribute](../../odbc/reference/syntax/sqlcolattributes-function.md) in der *ODBC Programmer es Reference*.
