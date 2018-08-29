---
title: external_data_sources (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 1016db6e-9950-4ae2-a004-bd4171e27359
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6dec76073fbd0a6e0ed7da85dd247f3435dec85b
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43064928"
---
# <a name="sysexternaldatasources-transact-sql"></a>external_data_sources (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Enthält eine Zeile für jede externe Datenquelle in der aktuellen Datenbank für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)], und [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
 Enthält eine Zeile für jede externe Datenquelle auf dem Server für [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|data_source_id|**int**|Objekt-ID für die externe Datenquelle.||  
|NAME|**sysname**|Der Name der externen Datenquelle.||  
|location|**nvarchar(4000)**|Die Verbindungszeichenfolge, die das Protokoll, IP-Adresse und Port für die externe Datenquelle enthält.||  
|type_desc|**nvarchar(255)**|Der Datenquellentyp als Zeichenfolge angezeigt.|HADOOP, RDBMS SHARD_MAP_MANAGER, RemoteDataArchiveTypeExtDataSource|  
|Typ|**tinyint**|Der Datenquellentyp als Zahl angezeigt.|0: HADOOP<br /><br /> 1 - RDBMS<br /><br /> 2 – SHARD_MAP_MANAGER<br /><br /> 3 – RemoteDataArchiveTypeExtDataSource|  
|resource_manager_location|**nvarchar(4000)**|Geben Sie für HADOOP, IP und Port Speicherort des Hadoop-Ressourcen-Managers. Hiermit wird die Übergabe von Aufträgen in einem Hadoop-Datenquelle.<br /><br /> NULL für andere Arten von Daten aus externen Quellen.||  
|credential_id|**int**|Die Objekt-ID der Datenbank von datenbankweit gültigen Anmeldeinformationen zur Verbindung mit der externen Datenquelle.||  
|database_name|**sysname**|Für Typ RDBMS, den Namen der Remotedatenbank. Für Typ SHARD_MAP_MANAGER wird der Name der Datenbank des shardzuordnungs-Manager. NULL für andere Arten von Daten aus externen Quellen.||  
|shard_map_name|**sysname**|Für Typ SHARD_MAP_MANAGER wird der Name der Shard-Zuordnung. NULL für andere Arten von Daten aus externen Quellen.||  
  
## <a name="permissions"></a>Berechtigungen  
 Die Sichtbarkeit der Metadaten in Katalogsichten ist auf sicherungsfähige Elemente eingeschränkt, bei denen der Benutzer entweder der Besitzer ist oder für die dem Benutzer eine Berechtigung erteilt wurde. Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [external_file_formats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-file-formats-transact-sql.md)   
 [sys.external_tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-tables-transact-sql.md)   
 [CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)  
  
  
