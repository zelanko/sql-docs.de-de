---
description: ASSEMBLYPROPERTY (Transact-SQL)
title: ASSEMBLYPROPERTY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ASSEMBLYPROPERTY_TSQL
- ASSEMBLYPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- ASSEMBLYPROPERTY statement
- assemblies [CLR integration], properties
ms.assetid: cf03d1b1-724c-48bf-a8df-3fe2586b150a
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 722d6c4b2130ad51c2249f083691233524d3834c
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96124919"
---
# <a name="assemblyproperty-transact-sql"></a>ASSEMBLYPROPERTY (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Diese Funktion gibt Informationen zu einer Eigenschaft einer Assembly zurück.
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
ASSEMBLYPROPERTY('assembly_name', 'property_name')  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
*assembly_name*  
Der Name der Assembly.
  
*property_name*  
Der Name einer Eigenschaft, zu der Informationen abgerufen werden sollen. *property_name* kann einen der folgenden Werte enthalten:
  
|Wert|BESCHREIBUNG|  
|---|---|
|**CultureInfo**|Gebietsschema der Assembly.|  
|**PublicKey**|Öffentlicher Schlüssel oder öffentlicher Schlüsseltoken der Assembly.|  
|**MvID**|Vollständige, vom Compiler generierte Versions-ID der Assembly.|  
|**VersionMajor**|Komponente für die Angabe der Hauptversion (erster Teil) der aus vier Teilen bestehenden Versions-ID der Assembly.|  
|**VersionMinor**|Komponente für die Angabe der Nebenversion (zweiter Teil) der aus vier Teilen bestehenden Versions-ID der Assembly.|  
|**VersionBuild**|Komponente für die Angabe der Buildnummer (dritter Teil) der aus vier Teilen bestehenden Versions-ID der Assembly.|  
|**VersionRevision**|Komponente für die Angabe der Revisionsnummer (vierter Teil) der aus vier Teilen bestehenden Versions-ID der Assembly.|  
|**SimpleName**|Einfacher Name der Assembly.|  
|**Aufbau**|Prozessorarchitektur der Assembly.|  
|**CLRName**|Kanonische Zeichenfolge, die den einfachen Namen, die Versionsnummer, die Kultur, den öffentlichen Schlüssel und die Architektur der Assembly codiert. Durch diesen Wert wird die CLR-seitige Assembly (Common Language Runtime) eindeutig identifiziert.|  
  
## <a name="return-type"></a>Rückgabetyp
**sql_variant**
  
## <a name="examples"></a>Beispiele  
In diesem Beispiel wird von einer `HelloWorld`-Assembly ausgegangen, die in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank registriert ist. Weitere Informationen finden Sie unter [Beispiel „Hello World“](/previous-versions/sql/sql-server-2016/ff878250(v=sql.130)).
  
```sql
USE AdventureWorks2012;  
GO  
SELECT ASSEMBLYPROPERTY ('HelloWorld' , 'PublicKey');  
```  
  
## <a name="see-also"></a>Weitere Informationen
[CREATE ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/create-assembly-transact-sql.md)  
[DROP ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-assembly-transact-sql.md)
  
