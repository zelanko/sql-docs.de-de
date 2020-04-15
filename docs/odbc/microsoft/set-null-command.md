---
title: SET NULL-Befehl | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7c83c9ef9f8a0ce143308b73d8df09b05fb2cdea
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300810"
---
# <a name="set-null-command"></a>SET NULL-Befehl
Bestimmt, wie NULL-Werte von den Befehlen ALTER TABLE - SQL, CREATE TABLE - SQL und INSERT - SQL unterstützt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET NULL ON | OFF  
```  
  
## <a name="arguments"></a>Argumente  
 EIN  
 (Standard für den Treiber; die Standardeinstellung für Visual FoxPro ist AUS.) Gibt an, dass alle Spalten in einer Tabelle, die mit ALTER TABLE und CREATE TABLE erstellt wurden, NULL-Werte zulassen. Sie können die Nullwertunterstützung für Spalten in der Tabelle überschreiben, indem Sie die NOT NULL-Klausel in die Spaltendefinitionen aufnehmen.  
  
 Gibt auch an, dass INSERT - SQL NULL-Werte in alle Spalten einfügt, die nicht in der INSERT - SQL VALUE-Klausel enthalten sind. INSERT - SQL fügt NULL-Werte nur in Spalten ein, die NULL-Werte zulassen.  
  
 OFF  
 Gibt an, dass alle Spalten in einer Tabelle, die mit ALTER TABLE und CREATE TABLE erstellt wurden, keine NULL-Werte zulassen. Sie können Nullwertunterstützung für Spalten in ALTER TABLE und CREATE TABLE festlegen, indem Sie die NULL-Klausel in die Spaltendefinitionen aufnehmen.  
  
 Gibt auch an, dass INSERT - SQL leere Werte in alle Spalten einfügt, die nicht in der INSERT - SQL VALUE-Klausel enthalten sind.  
  
## <a name="remarks"></a>Bemerkungen  
 SET NULL wirkt sich nur darauf aus, wie NULL-Werte von ALTER TABLE, CREATE TABLE und INSERT - SQL unterstützt werden. Andere Befehle sind von SET NULL nicht betroffen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER TABLE - SQL-Befehl](../../odbc/microsoft/alter-table-sql-command.md)   
 [CREATE TABLE - SQL-Befehl](../../odbc/microsoft/create-table-sql-command.md)   
 [INSERT (SQL-Befehl)](../../odbc/microsoft/insert-sql-command.md)
