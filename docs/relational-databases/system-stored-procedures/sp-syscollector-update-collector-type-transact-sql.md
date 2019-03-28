---
title: Sp_syscollector_update_collector_type (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_update_collector_type_TSQL
- sp_syscollector_update_collector_type
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_update_collector_type
- data collector [SQL Server], stored procedures
ms.assetid: 3c414dfd-d9ca-4320-81aa-949465b967bf
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9d3529d01966c7f9780183d663823d8f4033f47a
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58535782"
---
# <a name="spsyscollectorupdatecollectortype-transact-sql"></a>sp_syscollector_update_collector_type (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aktualisiert einen Sammlertyp für ein Sammelelement. Aktualisiert anhand des Namens und der GUID eines Sammlertyps die Sammlertypkonfiguration, einschließlich des Sammlungs- und Uploadpakets, des Parameterschemas und des Parameterformatierungsschemas.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syscollector_update_collector_type [ @collector_type_uid = ] 'collector_type_uid' OUTPUT  
          , [ @name = ] 'name'  
          , [ @parameter_schema = ] 'parameter_schema'  
          , [ @collection_package_id = ] collection_package_id  
          , [ @upload_package_id = ] upload_package_id  
```  
  
## <a name="arguments"></a>Argumente  
`[ @collector_type_uid = ] 'collector_type_uid'` Ist die GUID für den sammlertyp. *Collector_type_uid* ist **Uniqueidentifier**, und wenn es NULL ist, es wird automatisch erstellt und als Ausgabe zurückgegeben.  
  
`[ @name = ] 'name'` Ist der Name des sammlertyps. *Namen* ist **Sysname** und muss angegeben werden.  
  
`[ @parameter_schema = ] 'parameter_schema'` Ist das XML-Schema für diesen sammlertyp. *Parameter_schema* ist **Xml** und möglicherweise bestimmte sammlertypen erforderlich sein. Wenn nicht erforderlich, kann dieses Argument NULL sein.  
  
`[ @collection_package_id = ] collection_package_id` Ist ein eindeutiger lokaler Bezeichner, der auf zeigt die [!INCLUDE[ssIS](../../includes/ssis-md.md)] Auflistung, das vom Sammlungssatz verwendet. *collection_package_id* is **uniqueidentifer** and is required. Zum Abrufen des Werts für *Collection_package_id*, Fragen Sie die syscollector_collector_types-Systemsicht in der Msdb-Datenbank.  
  
`[ @upload_package_id = ] upload_package_id` Ist ein eindeutiger lokaler Bezeichner, der auf zeigt die [!INCLUDE[ssIS](../../includes/ssis-md.md)] hochladen, das vom Sammlungssatz verwendet. *Upload_package_id* ist **Uniqueidentifier** und ist erforderlich. Zum Abrufen des Werts für *Upload_package_id*, Fragen Sie die syscollector_collector_types-Systemsicht in der Msdb-Datenbank.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **Dc_admin** (mit EXECUTE-Berechtigung) festen Datenbankrolle.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird der generische T-SQL-Abfrage-Sammlertyp aktualisiert. (In dem Beispiel wird das Standardschema für den generischen T-SQL-Abfrage-Sammlertyp verwendet.)  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_update_collector_type  
@collector_type_uid = '302E93D1-3424-4BE7-AA8E-84813ECF2419',  
@name = 'Generic T-SQL Query Collector Type',  
@parameter_schema = '<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="DataCollectorType">  
  <xs:element name="TSQLQueryCollector">  
<xs:complexType>  
  <xs:sequence>  
<xs:element name="Query" minOccurs="1" maxOccurs="unbounded">  
  <xs:complexType>  
<xs:sequence>  
  <xs:element name="Value" type="xs:string" />  
  <xs:element name="OutputTable" type="xs:string" />  
</xs:sequence>  
  </xs:complexType>  
</xs:element>  
<xs:element name="Databases" minOccurs="0" maxOccurs="1">  
  <xs:complexType>  
<xs:sequence>  
  <xs:element name="Database" minOccurs="0" maxOccurs="unbounded" type="xs:string" />  
</xs:sequence>  
<xs:attribute name="UseSystemDatabases" type="xs:boolean" use="optional" />  
<xs:attribute name="UseUserDatabases" type="xs:boolean" use="optional" />  
  </xs:complexType>  
</xs:element>  
  </xs:sequence>  
</xs:complexType>  
  </xs:element>  
</xs:schema>',  
@collection_package_id = '292B1476-0F46-4490-A9B7-6DB724DE3C0B',  
@upload_package_id = '6EB73801-39CF-489C-B682-497350C939F0';  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Datensammlung](../../relational-databases/data-collection/data-collection.md)  
  
  
