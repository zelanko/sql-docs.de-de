---
description: Unterstützte ODBC-SQL-Grammatik (Visual FoxPro-ODBC-Treiber)
title: Unterstützte ODBC-SQL-Grammatik (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
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
ms.openlocfilehash: 3057520e5aca5277a68971513ef28427f27208ed
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471502"
---
# <a name="supported-odbc-sql-grammar-visual-foxpro-odbc-driver"></a>Unterstützte ODBC-SQL-Grammatik (Visual FoxPro-ODBC-Treiber)
Der Microsoft Visual FoxPro-ODBC-Treiber unterstützt Folgendes:  
  
-   Alle SQL-Anweisungen und-Klauseln in der minimalen ODBC-SQL-Grammatik  
  
-   Eine zusätzliche SQL-Anweisung aus der ODBC Core SQL-Grammatik  
  
 In der folgenden Tabelle werden die vom Treiber unterstützten Elemente von der ODBC-SQL-Grammatik Ebene aufgelistet.  
  
|Ebene|Elemente|Artikel|  
|-----------|--------------|----------|  
|Minimum|Datendefinitionssprache (DDL)|CREATE TABLE und DROP TABLE|  
||Datenbearbeitungssprache (DML)|SELECT, INSERT, Update und DELETE|  
||Ausdrücke|Einfach (z. b. a>B + C)|  
||Datentypen|Char, varchar oder long varchar|  
  
 Zusätzlich zur unterstützten ODBC-SQL-Grammatik unterstützt der Visual FoxPro-ODBC-Treiber die gesamte Native Visual FoxPro-Sprachsyntax für die folgenden Visual FoxPro-Befehle:  
  
 [ALTER TABLE](../../odbc/microsoft/alter-table-sql-command.md)  
  
 [CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md)  
  
 [DELETE](../../odbc/microsoft/delete-sql-command.md)  
  
 [Tag löschen](../../odbc/microsoft/delete-tag-command.md)  
  
 [DROP TABLE](../../odbc/microsoft/drop-table-command.md)  
  
 [Sin](../../odbc/microsoft/index-command.md)  
  
 [INSERT](../../odbc/microsoft/insert-sql-command.md)  
  
 [SELECT](../../odbc/microsoft/select-sql-command.md)  
  
 [UPDATE](../../odbc/microsoft/update-sql-command.md)
