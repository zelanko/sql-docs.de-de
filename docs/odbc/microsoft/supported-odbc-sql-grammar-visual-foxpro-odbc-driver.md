---
title: Unterstützte ODBC SQL-Grammatik (Visual FoxPro ODBC-Treiber) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f72548d0708a63f887f7d6da4d4f5988500f0eef
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304083"
---
# <a name="supported-odbc-sql-grammar-visual-foxpro-odbc-driver"></a>Unterstützte ODBC-SQL-Grammatik (Visual FoxPro-ODBC-Treiber)
Der Microsoft Visual FoxPro ODBC-Treiber unterstützt Folgendes:  
  
-   Alle SQL-Anweisungen und -Klauseln in der ODBC-Mindest-SQL-Grammatik  
  
-   Eine zusätzliche SQL-Anweisung aus der ODBC-Kern-SQL-Grammatik  
  
 In der folgenden Tabelle sind die vom Treiber unterstützten Elemente auf ODBC SQL Grammar-Ebene aufgeführt.  
  
|Ebene|Elements|Element|  
|-----------|--------------|----------|  
|Minimum|Datendefinitionssprache (DDL)|CREATE TABLE und DROP TABLE|  
||Datenbearbeitungssprache (DML)|SELECT, INSERT, UPDATE und DELETE|  
||Ausdrücke|Einfach (z. B. A>B+C)|  
||Datentypen|CHAR, VARCHAR oder LONG VARCHAR|  
  
 Zusätzlich zur unterstützten ODBC SQL-Grammatik unterstützt der Visual FoxPro ODBC-Treiber die vollständige native Visual FoxPro-Sprachsyntax für die folgenden Visual FoxPro-Befehle:  
  
 [ALTER TABLE](../../odbc/microsoft/alter-table-sql-command.md)  
  
 [CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md)  
  
 [Löschen](../../odbc/microsoft/delete-sql-command.md)  
  
 [DELETE-TAG](../../odbc/microsoft/delete-tag-command.md)  
  
 [DROP-TABELLE](../../odbc/microsoft/drop-table-command.md)  
  
 [Index](../../odbc/microsoft/index-command.md)  
  
 [Einfügen](../../odbc/microsoft/insert-sql-command.md)  
  
 [Auswählen](../../odbc/microsoft/select-sql-command.md)  
  
 [aktualisieren](../../odbc/microsoft/update-sql-command.md)
