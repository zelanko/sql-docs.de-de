---
title: Getpathlocator (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- GetPathLocator
- GetPathLocator_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- GetPathLocator function
ms.assetid: 78b7e220-445b-4fdf-811b-7253f4f2b058
author: rothja
ms.author: jroth
ms.openlocfilehash: 133d2b109c54271c2e94cba2e88831f8f7aecf16
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85662881"
---
# <a name="getpathlocator-transact-sql"></a>GetPathLocator (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt den path_locator-ID-Wert für die angegebene Datei bzw. das angegebene Verzeichnis in einer FileTable zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
GetPathLocator(filenamespace_path)  
```  
  
## <a name="arguments"></a>Argumente  
 *filenamespace_path*  
 Ein Namespacepfad in der FileTable. Der Namespacepfad hat den Typ **nvarchar(max)**.  
  
 Wenn die Datenbank zu einer Always on-Verfügbarkeits Gruppe gehört, akzeptiert die **getpathlocator** -Funktion den Namen des virtuellen Netzwerks (vnn) oder den Computernamen.  
  
## <a name="return-type"></a>Rückgabetyp  
 **hierarchyid**  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
 Weitere Informationen finden Sie unter [Work with Directories and Paths in FileTables](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md).  
  
## <a name="examples"></a>Beispiele  
 Sie können die **GetPathLocator** -Funktion verwenden, wenn Sie Dateien von einem Dateiserver zu einer FileTable migrieren. In diesem Szenario sollen die Dateien in die FileTable verschoben und anschließend der ursprüngliche UNC-Pfad für jede Datei durch den FileTable-UNC-Pfad ersetzt werden. Ein umfassendes Beispiel finden Sie unter [Laden von Dateien in filetables](../../relational-databases/blob/load-files-into-filetables.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeiten mit Verzeichnissen und Pfaden in FileTables](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)  
  
  
