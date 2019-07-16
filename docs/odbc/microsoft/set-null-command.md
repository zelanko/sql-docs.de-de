---
title: Befehl SET NULL | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- set nullSET NULL
ms.assetid: 410c5a6e-e957-4ecc-9e2d-e591cbc0bc4f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9f8addb9b4c7c200ee8f213bdd959067039ccfff
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68063669"
---
# <a name="set-null-command"></a>SET NULL-Befehl
Bestimmt, wie null-Werte, durch die ALTER TABLE - SQL, CREATE TABLE - SQL und INSERT unterstützt werden - SQL-Befehle.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET NULL ON | OFF  
```  
  
## <a name="arguments"></a>Argumente  
 ON  
 (Standard für den Treiber; der Standardwert für Visual FoxPro ist OFF). Gibt an, dass alle Spalten in einer Tabelle mit ALTER TABLE und CREATE TABLE erstellt null-Werte zulässt. Sie können null-Wert-Unterstützung für Spalten in der Tabelle einschließlich der nicht-NULL-Klausel in der Spalte Definitionen überschreiben.  
  
 Gibt auch an, dass INSERT - SQL null-Werte in Spalten nicht in einer INSERT - SQL-VALUE-Klausel enthalten eingefügt wird. INSERT - wird SQL null-Werte nur in Spalten einfügen, die null-Werte zulassen.  
  
 OFF  
 Gibt an, dass alle Spalten in einer Tabelle mit ALTER TABLE und CREATE TABLE erstellt keine null-Werte zulässt. Sie können null-Wert-Unterstützung für Spalten in der ALTER TABLE und CREATE TABLE festlegen, durch die NULL-Klausel in der Spalte Definitionen.  
  
 Gibt auch an, dass INSERT - SQL leere Werte in Spalten nicht in einer INSERT - SQL-VALUE-Klausel enthalten eingefügt wird.  
  
## <a name="remarks"></a>Hinweise  
 SET NULL wirkt sich auf nur wie null-Werte werden von ALTER TABLE, CREATE TABLE und INSERT - SQL unterstützt. Andere Befehle sind nicht betroffen von NULL festgelegt.  
  
## <a name="see-also"></a>Siehe auch  
 [ALTER TABLE - SQL-Befehl](../../odbc/microsoft/alter-table-sql-command.md)   
 [Erstellen Sie Tabelle - SQL-Befehl.](../../odbc/microsoft/create-table-sql-command.md)   
 [INSERT (SQL-Befehl)](../../odbc/microsoft/insert-sql-command.md)
