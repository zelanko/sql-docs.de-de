---
description: SET NULL-Befehl
title: NULL-Befehl festlegen | Microsoft-Dokumentation
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
ms.openlocfilehash: 5e98037838325a0bfe56b51cdcfec7df8539facd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421844"
---
# <a name="set-null-command"></a>SET NULL-Befehl
Bestimmt, wie NULL-Werte von den Befehlen ALTER TABLE-SQL, CREATE TABLE-SQL und INSERT-SQL unterstützt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET NULL ON | OFF  
```  
  
## <a name="arguments"></a>Argumente  
 EIN  
 (Standardwert für den Treiber; der Standardwert für Visual FoxPro ist off.) Gibt an, dass alle Spalten in einer Tabelle, die mit ALTER TABLE und CREATE TABLE erstellt wurde, NULL-Werte zulassen. Sie können die Unterstützung von NULL-Werten für Spalten in der Tabelle überschreiben, indem Sie die not NULL-Klausel in die Spaltendefinitionen einschließen.  
  
 Gibt auch an, dass INSERT-SQL NULL-Werte in Spalten einfügt, die nicht in der INSERT-SQL-wertklausel enthalten sind. INSERT-SQL fügt NULL-Werte nur in Spalten ein, die NULL-Werte zulassen.  
  
 OFF  
 Gibt an, dass alle Spalten in einer Tabelle, die mit ALTER TABLE und CREATE TABLE erstellt wurde, keine NULL-Werte zulassen. Sie können die Unterstützung von NULL-Werten für Spalten in ALTER TABLE und CREATE TABLE festlegen, indem Sie die NULL-Klausel in die Spaltendefinitionen einschließen.  
  
 Gibt auch an, dass INSERT-SQL leere Werte in Spalten einfügt, die nicht in der INSERT-SQL-wertklausel enthalten sind.  
  
## <a name="remarks"></a>Bemerkungen  
 Set NULL wirkt sich nur darauf aus, wie NULL-Werte von ALTER TABLE, CREATE TABLE und INSERT-SQL unterstützt werden. Andere Befehle sind von SET NULL nicht betroffen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER TABLE-SQL-Befehl](../../odbc/microsoft/alter-table-sql-command.md)   
 [CREATE TABLE-SQL-Befehl](../../odbc/microsoft/create-table-sql-command.md)   
 [INSERT (SQL-Befehl)](../../odbc/microsoft/insert-sql-command.md)
