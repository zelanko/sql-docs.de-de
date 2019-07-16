---
title: Sys. database_filestream_options (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- database_filestream_options
- sys.database_filestream_options_TSQL
- database_filestream_options_TSQL
- sys.database_filestream_options
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_filestream_options catalog view
ms.assetid: 3383c607-0bbc-456a-ab37-7230f4cbf0e9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 95d9c980927d565b907d666af1317e883126087e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67915034"
---
# <a name="sysdatabasefilestreamoptions-transact-sql"></a>sys.database_filestream_options (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Zeigt Informationen zur Ebene des nicht transaktionalen Zugriffs auf die aktivierten FILESTREAM-Daten in FileTables an. Enthält eine Zeile für jede Datenbank in der SQL Server-Instanz.  
  
 Weitere Informationen zu FileTables finden Sie unter [FileTables &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md).  
  
  
|Spalte|Typ|Beschreibung|  
|------------|----------|-----------------|  
|**database_id**|**int**|Die ID der Datenbank. Dieser Wert ist innerhalb einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eindeutig.|  
|**directory_name**|**nvarchar(255)**|Das Verzeichnis auf Datenbankebene für alle FileTable-Namespaces.|  
|**non_transacted_access**|**tinyint**|Die Ebene des nicht transaktionalen Zugriffs auf FILESTREAM-Daten, die aktiviert sind. Die Ebene des Zugriffs festgelegt ist, durch die NON_TRANSACTED_ACCESS-Option von der **CREATE DATABASE** oder **ALTER DATABASE** Anweisung.<br /><br /> Diese Einstellung besitzt einen der folgenden Werte:<br /><br /> 0 – nicht aktiviert. Dies ist der Standardwert. Diese Ebene wird festgelegt, indem der Wert **OFF** für die **NON_TRANSACTED_ACCESS** -Option angegeben wird.<br /><br /> 1: die schreibgeschützten Zugriff. Diese Ebene wird festgelegt, indem der Wert **READ_ONLY** für die **NON_TRANSACTED_ACCESS** -Option angegeben wird.<br /><br /> 3 – Vollzugriff. Diese Ebene wird festgelegt, indem der Wert **FULL** für die **NON_TRANSACTED_ACCESS** -Option angegeben wird.<br /><br /> 5 – Im Übergang zu READONLY.<br /><br /> 6 – im Übergang zu OFF|  
|**non_transacted_access_desc**|**nvarchar(60)**|Die Beschreibung der Ebene des nicht transaktionalen Zugriffs im Non_transacted_access identifiziert.<br /><br /> Diese Einstellung besitzt einen der folgenden Werte:<br /><br /> NONE: Dies ist der Standardwert.<br /><br /> READ_ONLY<br /><br /> FULL<br /><br /> IN_TRANSITION_TO_READ_ONLY<br /><br /> IN_TRANSITION_TO_OFF|  
  
## <a name="see-also"></a>Siehe auch  
 [Aktivieren der erforderlichen Komponenten für FileTable](../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)  
  
  
