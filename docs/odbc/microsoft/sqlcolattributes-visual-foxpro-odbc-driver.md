---
title: SQLColAttributes (Visual FoxPro ODBC-Treiber) | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307911"
---
# <a name="sqlcolattributes-visual-foxpro-odbc-driver"></a>SQLColAttributes (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro ODBC-Treiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: Voll  
  
 ODBC-API-Konformität: Kernebene  
  
 Gibt Deskriptorinformationen für eine Spalte in einem Resultset zurück. Deskriptorinformationen werden als Zeichenfolge, als 32-Bit-Deskriptor-abhängiger Wert oder als Ganzzahlwert zurückgegeben.  
  
> [!NOTE]  
>  **SQLColAttributes** kann nicht verwendet werden, um Informationen über die Lesezeichenspalte (Spalte 0) zurückzugeben.  
  
 Der Visual FoxPro ODBC-Treiber unterstützt alle *fDescType-Werte.* Die folgende Tabelle enthält Kommentare zur Implementierung ausgewählter Werte durch den Treiber.  
  
|*fDescType*|Comment|  
|-----------------|-------------|  
|SQL_COLUMN_AUTO_INCREMENT|Gibt FALSE zurück: Visual FoxPro hat keine Zählerfelder.|  
|SQL_COLUMN_CASE_SENSITIVE|Gibt immer TRUE zurück, wenn der Spaltentyp Zeichen ist.|  
|SQL_COLUMN_LABEL|Gibt den Spaltennamen zurück, der auch von SQL_COLUMN_NAME zurückgegeben wird.|  
|SQL_COLUMN_MONEY|Gibt TRUE zurück, wenn der Spaltentyp Währung ist (dargestellt durch ein "Y" in der Visual FoxPro-Sprache).|  
|SQL_COLUMN_OWNER_NAME|Gibt immer eine leere Zeichenfolge zurück|  
|SQL_COLUMN_QUALIFIER_NAME|Gibt immer eine leere Zeichenfolge zurück|  
|SQL_COLUMN_SEARCHABLE|Gibt SQL_UNSEARCHABLE für Spalten vom Typ Allgemein zurück. Diese Spalten können nicht in einer WHERE-Klausel verwendet werden.<br /><br /> Gibt SQL_SEARCHABLE für Spalten vom Typ Character oder Memo mit NOCPTRANS nicht festgelegt zurück. Diese Spalten können in einer WHERE-Klausel mit jedem Vergleichsoperator verwendet werden.<br /><br /> Gibt SQL_ALL_EXCEPT_LIKE für alle anderen Spaltentypen zurück. Diese Spalten können in einer WHERE-Klausel mit allen Vergleichsoperatoren außer LIKE verwendet werden.|  
|SQL_COLUMN_TABLE_NAME|Gibt immer eine leere Zeichenfolge zurück|  
  
 Weitere Informationen finden Sie unter [SQLColAttributes](../../odbc/reference/syntax/sqlcolattributes-function.md) in der *ODBC-Programmiererreferenz*.
