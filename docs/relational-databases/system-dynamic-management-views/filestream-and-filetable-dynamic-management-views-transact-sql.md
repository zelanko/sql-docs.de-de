---
title: 'FileStream und FileTable: dynamische Verwaltungssichten (Transact-SQL) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- FileTables [SQL Server], dynamic management views
ms.assetid: e50a135d-6644-42a4-a0df-1c7a2b722051
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 240da66536adb16c140e625ccefd99c672f80574
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47794598"
---
# <a name="filestream-and-filetable-dynamic-management-views-transact-sql"></a>Dynamische Verwaltungssichten für Filestream und FileTable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  In diesem Abschnitt werden die dynamischen Verwaltungssichten im Zusammenhang mit den FILESTREAM- und FileTable-Funktionen beschrieben.  
  
## <a name="filestream-dynamic-management-views-and-functions"></a>Filestream: Dynamische Verwaltungssichten und Funktionen  
 [sys.dm_filestream_file_io_handles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-handles-transact-sql.md)  
 Zeigt die aktuell geöffneten Transaktionsdateihandles an.  
  
 [sys.dm_filestream_file_io_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-requests-transact-sql.md)  
 Zeigt aktuelle Dateieingabe- und Dateiausgabeanforderungen an.  
  
## <a name="filetable-dynamic-management-views-and-functions"></a>FileTable: Dynamische Verwaltungssichten und Funktionen  
 [sys.dm_filestream_non_transacted_handles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md)  
 Zeigt die derzeit geöffneten nicht transaktionsgebundenen Dateihandles für FileTable-Daten an.  

## <a name="see-also"></a>Siehe auch
[FileStream](../../relational-databases/blob/filestream-sql-server.md)
<br>[Filetables](../../relational-databases/blob/filetables-sql-server.md)
<br>[Katalogsichten für Filestream und FileTable (Transact-SQL)](../system-catalog-views/filestream-and-filetable-catalog-views-transact-sql.md)
<br>[Gespeicherte Systemprozeduren für Filestream und FileTable (Transact-SQL)](../system-stored-procedures/filestream-and-filetable-system-stored-procedures.md)
  
