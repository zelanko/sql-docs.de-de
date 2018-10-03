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
manager: craigg
ms.openlocfilehash: b6f0e23abd31661210282967fa35080376eaaaf3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47765628"
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
