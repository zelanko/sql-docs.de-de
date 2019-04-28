---
title: SQLColAttributes (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e34929315d3a3548799bc605dbb8f3c4a2f665d0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62928162"
---
# <a name="sqlcolattributes-visual-foxpro-odbc-driver"></a>SQLColAttributes (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: Vollständig  
  
 ODBC-API-Übereinstimmung: Kern-Ebene  
  
 Gibt Informationen der Sicherheitsbeschreibung für eine Spalte in einem Resultset zurück. Informationen der Sicherheitsbeschreibung wird als eine Zeichenfolge, eine 32-Bit-Deskriptor-abhängige Wert oder ein ganzzahliger Wert zurückgegeben.  
  
> [!NOTE]  
>  **SQLColAttributes** kann nicht verwendet werden, um Informationen über die Lesezeichenspalte (Spalte 0) zurückgegeben werden sollen.  
  
 Der Visual FoxPro-ODBC-Treiber unterstützt alle *fDescType* Werte. Die folgende Tabelle enthält Kommentare vom Treiber-Implementierung der ausgewählten Werte.  
  
|*fDescType*|Anmerkung|  
|-----------------|-------------|  
|SQL_COLUMN_AUTO_INCREMENT|"False" zurückgibt: Visual FoxPro weist keine Zählerfelder auf.|  
|SQL_COLUMN_CASE_SENSITIVE|Wenn der Spaltentyp Zeichen ist, wird immer TRUE zurückgegeben.|  
|SQL_COLUMN_LABEL|Gibt den Namen der Spalte, die auch von SQL_COLUMN_NAME zurückgegeben wird.|  
|SQL_COLUMN_MONEY|Gibt TRUE zurück, wenn der Spaltentyp Währung (dargestellt durch "Y" in der Visual FoxPro-Sprache).|  
|SQL_COLUMN_OWNER_NAME|Gibt immer eine leere Zeichenfolge zurück.|  
|SQL_COLUMN_QUALIFIER_NAME|Gibt immer eine leere Zeichenfolge zurück.|  
|SQL_COLUMN_SEARCHABLE|Für Spalten vom Typ Allgemein SQL_UNSEARCHABLE zurückgegeben; Diese Spalten können nicht in einer WHERE-Klausel verwendet werden.<br /><br /> Gibt SQL_SEARCHABLE für Spalten vom Typ Zeichen oder Memo mit NOCPTRANS nicht festgelegt werden; Diese Spalten können in einer WHERE-Klausel mit jedem Vergleichsoperator verwendet werden.<br /><br /> Für alle anderen Spaltentypen SQL_ALL_EXCEPT_LIKE zurückgegeben; Diese Spalten können in einer WHERE-Klausel mit allen Vergleichsoperatoren mit Ausnahme von ähnlichen verwendet werden.|  
|SQL_COLUMN_TABLE_NAME|Gibt immer eine leere Zeichenfolge zurück.|  
  
 Weitere Informationen finden Sie unter [SQLColAttributes](../../odbc/reference/syntax/sqlcolattributes-function.md) in die *ODBC Programmer's Reference*.
