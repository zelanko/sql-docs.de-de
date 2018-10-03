---
title: GetPathLocator (Transact-SQL) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 7770ced88953fd64d9ce48b624416b9a7e787f7e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47699128"
---
# <a name="getpathlocator-transact-sql"></a>GetPathLocator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt den path_locator-ID-Wert für die angegebene Datei bzw. das angegebene Verzeichnis in einer FileTable zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
GetPathLocator(filenamespace_path)  
```  
  
## <a name="arguments"></a>Argumente  
 *filenamespace_path*  
 Ein Namespacepfad in der FileTable. Der Namespacepfad hat den Typ **nvarchar(max)**.  
  
 Wenn die Datenbank zu einer Always On-verfügbarkeitsgruppe gehört die **GetPathLocator** -Funktion akzeptiert den Namen des virtuellen Netzwerks (VNN) oder den Namen des Computers.  
  
## <a name="return-type"></a>Rückgabetyp  
 **hierarchyid**  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
 Weitere Informationen finden Sie unter [Work with Directories and Paths in FileTables](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md).  
  
## <a name="examples"></a>Beispiele  
 Sie können die **GetPathLocator** -Funktion verwenden, wenn Sie Dateien von einem Dateiserver zu einer FileTable migrieren. In diesem Szenario sollen die Dateien in die FileTable verschoben und anschließend der ursprüngliche UNC-Pfad für jede Datei durch den FileTable-UNC-Pfad ersetzt werden. Ein vollständiges Beispiel finden Sie unter [Laden von Dateien in FileTables](../../relational-databases/blob/load-files-into-filetables.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Verzeichnissen und Pfaden in FileTables](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)  
  
  
