---
title: Sys. fn_xe_file_target_read_file (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fn_xe_file_target_read_file_TSQL
- fn_xe_file_target_read_file
- sys.fn_xe_file_target_read_file_TSQL
- sys.fn_xe_file_target_read_file
dev_langs:
- TSQL
helpviewer_keywords:
- extended events [SQL Server], functions
- fn_xe_file_target_read_file function
- sys.fn_xe_file_target_read_file function
ms.assetid: cc0351ae-4882-4b67-b0d8-bd235d20c901
caps.latest.revision: 20
author: rothja
ms.author: jroth
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 29a0eda47d510292d657bfdb7912a9fe8940b023
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43099618"
---
# <a name="sysfnxefiletargetreadfile-transact-sql"></a>sys.fn_xe_file_target_read_file (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Liest Dateien, die vom asynchronen Dateiziel der erweiterten Ereignisse erstellt werden. Pro Zeile wird ein Ereignis im XML-Format zurückgegeben.  
  
> [!WARNING]  
>  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] akzeptieren im XEL-und XEM generierte Ablaufverfolgungsergebnisse. [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Erweiterte Ereignisse-unterstützen nur Ablaufverfolgungsergebnisse im XEL-Format. Verwenden Sie SQL Server Management Studio, um Ablaufverfolgungsergebnisse im XEL-Format lesen zu können.    
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.fn_xe_file_target_read_file ( path, mdpath, initial_file_name, initial_offset )  
```  
  
## <a name="arguments"></a>Argumente  
 *path*  
 Der Pfad zu den zu lesenden Dateien. *Pfad* kann Platzhalter und enthalten den Namen einer Datei enthalten. *Pfad* ist **nvarchar(260)**. Es gibt keinen Standardwert. Im Kontext von Azure SQL-Datenbank ist dieser Wert eine HTTP-URL in eine Datei im Azure-Speicher.
  
 *mdpath*  
 Der Pfad zur Metadatendatei, die der angegebenen Datei bzw. Dateigruppe von entspricht, dem *Pfad* Argument. *Mdpath* ist **nvarchar(260)**. Es gibt keinen Standardwert. Ab SQL Server 2016 wird kann dieser Parameter als null angegeben werden.
  
> [!NOTE]  
>  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] erfordert keine der *Mdpath* Parameter. Er wird jedoch beibehalten, um die Abwärtskompatibilität für in früheren Versionen von SQL Server erstellte Protokolldateien aufrechtzuerhalten.  
  
 *initial_file_name*  
 Die erste Datei zum Lesen aus *Pfad*. *' initial_file_name '* ist **nvarchar(260)**. Es gibt keinen Standardwert. Wenn **null** angegeben ist, als das Argument, das alle Dateien finden Sie in *Pfad* gelesen werden.  
  
> [!NOTE]  
>  *' initial_file_name '* und *Initial_offset* sind paarargumente. Wenn Sie einen Wert für eines der beiden Argumente angeben, müssen Sie auch einen Wert für das andere Argument angeben.  
  
 *initial_offset*  
 Wird verwendet, um den letzten zuvor gelesenen Offset anzugeben und überspringt alle Ereignisse bis (einschließlich) des Offsets. Die Ereignisenumeration startet nach dem angegebenen Offset. *Initial_offset* ist **Bigint**. Wenn **null** wird angegeben, wie das Argument die gesamte Datei gelesen werden.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|module_guid|**uniqueidentifier**|Die Ereignismodul-GUID. Lässt keine NULL-Werte zu.|  
|package_guid|**uniqueidentifier**|Die Ereignispaket-GUID. Lässt keine NULL-Werte zu.|  
|object_name|**nvarchar(256)**|Der Name des Ereignisses. Lässt keine NULL-Werte zu.|  
|event_data|**nvarchar(max)**|Der Ereignisinhalt im XML-Format. Lässt keine NULL-Werte zu.|  
|file_name|**nvarchar(260)**|Der Name der Datei, die das Ereignis enthält. Lässt keine NULL-Werte zu.|  
|file_offset|**bigint**|Der Offset des Blocks in der Datei, der das Ereignis enthält. Lässt keine NULL-Werte zu.|  
|timestamp_utc|**datetime2**|**Gilt für**: [!INCLUDE[ssSQLv14](../../includes/sssqlv14-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].<br /><br />Das Datum und Uhrzeit (UTC-Zeitzone) des Ereignisses. Lässt keine NULL-Werte zu.|  

  
## <a name="remarks"></a>Hinweise  
 Das Lesen großer Resultsets wird festgelegt, indem Sie Ausführung **fn_xe_file_target_read_file** in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] kann zu einem Fehler führen. Verwenden der **Ergebnisse in Datei** Modus (**STRG + UMSCHALT + F**) große Resultsets in eine Datei exportieren, und Lesen Sie stattdessen die Datei mit einem anderen Tool.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-retrieving-data-from-file-targets"></a>A. Abrufen von Daten aus Dateizielen  
 Im folgenden Beispiel werden alle Zeilen aus allen Dateien abgerufen. In dieser Beispieldatei befinden sich die Dateiziele und Metadateien im Ablaufverfolgungsordner auf dem Laufwerk C:\.  
  
```  
SELECT * FROM sys.fn_xe_file_target_read_file('C:\traces\*.xel', 'C:\traces\metafile.xem', null, null);  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Dynamische Verwaltungssichten für erweiterte Ereignisse](../../relational-databases/system-dynamic-management-views/extended-events-dynamic-management-views.md)   
 [Katalogsichten für erweiterte Ereignisse &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md)   
 [Erweiterte Ereignisse](../../relational-databases/extended-events/extended-events.md)  
  
  
