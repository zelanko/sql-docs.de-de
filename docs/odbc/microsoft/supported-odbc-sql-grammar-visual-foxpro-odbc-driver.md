---
title: ODBC-SQL-Grammatik (Visual FoxPro-ODBC-Treiber) unterstützt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- native Visual FoxPro language syntax [ODBC]
- FoxPro ODBC driver [ODBC], SQL grammar
- SQL grammar [ODBC], Visual FoxPro ODBC driver
- Visual FoxPro ODBC driver [ODBC], SQL grammar
- grammar support in Visual FoxPro ODBC driver [ODBC]
- Visual FoxPro ODBC driver [ODBC], native Visual FoxPro language syntax
- FoxPro ODBC driver [ODBC], native Visual FoxPro language syntax
ms.assetid: f41a38c2-e22e-4c65-a32e-9a6777435160
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 10df35f4f29de4ac3899efa0e86e48af861f1e65
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62633771"
---
# <a name="supported-odbc-sql-grammar-visual-foxpro-odbc-driver"></a>Unterstützte ODBC-SQL-Grammatik (Visual FoxPro-ODBC-Treiber)
Die Microsoft Visual FoxPro-ODBC-Treiber unterstützt Folgendes:  
  
-   Alle SQL-Anweisungen und Klauseln in die minimale ODBC-SQL-Grammatik  
  
-   Eine zusätzliche SQL-Anweisung von ODBC-zentralen SQL-Grammatik  
  
 Die folgende Tabelle enthält die Elemente, die vom Treiber, nach der Ebene der ODBC-SQL-Grammatik unterstützt wird.  
  
|Ebene|Elemente|Element|  
|-----------|--------------|----------|  
|Minimum|Datendefinitionssprache (DDL)|CREATE TABLE und DROP TABLE|  
||Datenbearbeitungssprache (DML)|AUSWÄHLEN, einfügen, aktualisieren und löschen|  
||Ausdrücke|Einfache (z. B. ein > B + C)|  
||Datentypen|CHAR, VARCHAR oder LONG VARCHAR|  
  
 Zusätzlich zu den unterstützten ODBC-SQL-Grammatik unterstützt der Visual FoxPro-ODBC-Treiber die vollständige systemeigene Visual FoxPro-Language-Syntax für die folgenden Visual FoxPro-Befehle:  
  
 [ALTER TABLE](../../odbc/microsoft/alter-table-sql-command.md)  
  
 [CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md)  
  
 [DELETE](../../odbc/microsoft/delete-sql-command.md)  
  
 [TAG LÖSCHEN](../../odbc/microsoft/delete-tag-command.md)  
  
 [DROP TABLE](../../odbc/microsoft/drop-table-command.md)  
  
 [INDEX](../../odbc/microsoft/index-command.md)  
  
 [INSERT](../../odbc/microsoft/insert-sql-command.md)  
  
 [SELECT](../../odbc/microsoft/select-sql-command.md)  
  
 [UPDATE](../../odbc/microsoft/update-sql-command.md)
