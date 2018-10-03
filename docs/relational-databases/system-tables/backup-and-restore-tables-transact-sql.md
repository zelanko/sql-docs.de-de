---
title: Sichern und Wiederherstellen von Tabellen (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- system tables [SQL Server], backup tables
- backup system tables [SQL Server]
- system tables [SQL Server], restore tables
- restore system tables [SQL Server]
ms.assetid: aa615add-54e6-40f5-8b55-3728b26884ee
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 021077a7e127f9c93ee752dea7f87aa12e792d02
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47596408"
---
# <a name="backup-and-restore-tables-transact-sql"></a>Sichern und Wiederherstellen von Tabellen (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  In den Themen in diesem Abschnitt werden die Systemtabellen beschrieben, in denen die von Datenbank-Sicherungs- und Datenbank-Wiederherstellungsvorgängen verwendeten Informationen gespeichert werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [backupfile](../../relational-databases/system-tables/backupfile-transact-sql.md)  
 Enthält eine Zeile für jede Daten- oder Protokolldatei einer Datenbank.  
  
 [backupfilegroup](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)  
 Enthält eine Zeile für jede Dateigruppe in einer Datenbank zum Zeitpunkt der Sicherung.  
  
 [backupmediafamily](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)  
 Enthält eine Zeile für jede Medienfamilie.  
  
 [backupmediaset](../../relational-databases/system-tables/backupmediaset-transact-sql.md)  
 Enthält eine Zeile für jeden Sicherungsmediensatz.  
  
 [backupset](../../relational-databases/system-tables/backupset-transact-sql.md)  
 Enthält eine Zeile für jeden Sicherungssatz.  
  
 [logmarkhistory](../../relational-databases/system-tables/logmarkhistory-transact-sql.md)  
 Enthält eine Zeile für jede markierte Transaktion, für die ein Commit ausgeführt wurde.  
  
 [restorefile](../../relational-databases/system-tables/restorefile-transact-sql.md)  
 Enthält eine Zeile für jede wiederhergestellte Datei. Dazu gehören die Dateien, die indirekt nach Dateigruppennamen wiederhergestellt werden.  
  
 [restorefilegroup](../../relational-databases/system-tables/restorefilegroup-transact-sql.md)  
 Enthält eine Zeile für jede wiederhergestellte Dateigruppe.  
  
 [restorehistory](../../relational-databases/system-tables/restorehistory-transact-sql.md)  
 Enthält eine Zeile für jeden Wiederherstellungsvorgang.  
  
 [suspect_pages](../../relational-databases/system-tables/suspect-pages-transact-sql.md)  
 Enthält eine Zeile für jede Seite mit einem Fehler vom Typ 824 (maximal 1.000 Zeilen).  
  
 [sysopentapes](../../relational-databases/system-tables/sysopentapes-transact-sql.md)  
 Enthält eine Zeile für jedes aktuell geöffnete Bandmedium.  
  
  
