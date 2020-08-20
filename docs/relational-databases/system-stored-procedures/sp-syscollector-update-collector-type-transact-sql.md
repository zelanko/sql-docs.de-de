---
description: sp_syscollector_update_collector_type (Transact-SQL)
title: sp_syscollector_update_collector_type (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 477fb448d91939933cea7132ad8b532de7a162e8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473582"
---
# <a name="sp_syscollector_update_collector_type-transact-sql"></a>sp_syscollector_update_collector_type (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Aktualisiert einen Sammlertyp für ein Sammelelement. Aktualisiert anhand des Namens und der GUID eines Sammlertyps die Sammlertypkonfiguration, einschließlich des Sammlungs- und Uploadpakets, des Parameterschemas und des Parameterformatierungsschemas.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syscollector_update_collector_type [ @collector_type_uid = ] 'collector_type_uid' OUTPUT  
          , [ @name = ] 'name'  
          , [ @parameter_schema = ] 'parameter_schema'  
          , [ @collection_package_id = ] collection_package_id  
          , [ @upload_package_id = ] upload_package_id  
```  
  
## <a name="arguments"></a>Argumente  
`[ @collector_type_uid = ] 'collector_type_uid'` Die GUID für den Sammlertyp. *collector_type_uid* ist vom Datentyp **uniqueidentifier**, und wenn er NULL ist, wird er automatisch erstellt und als Output zurückgegeben.  
  
`[ @name = ] 'name'` Der Name des Sammler Typs. *Name ist vom Datentyp* **vom Datentyp sysname** und muss angegeben werden.  
  
`[ @parameter_schema = ] 'parameter_schema'` Ist das XML-Schema für diesen Sammlertyp. *parameter_schema* ist **XML** und kann für bestimmte Sammlertypen erforderlich sein. Wenn nicht erforderlich, kann dieses Argument NULL sein.  
  
`[ @collection_package_id = ] collection_package_id` Ein eindeutiger lokaler Bezeichner, der auf das Sammlungs Paket verweist, das [!INCLUDE[ssIS](../../includes/ssis-md.md)] vom Sammlungs Satz verwendet wird. *collection_package_id* ist vom datnoch **uniqueidentifier** und ist erforderlich. Wenn Sie den Wert für *collection_package_id*abrufen möchten, Fragen Sie die dbo.syscollector_collector_types-Systemsicht in der msdb-Datenbank ab.  
  
`[ @upload_package_id = ] upload_package_id` Ein eindeutiger lokaler Bezeichner, der auf das [!INCLUDE[ssIS](../../includes/ssis-md.md)] Uploadpaket verweist, das vom Sammlungs Satz verwendet wird. *upload_package_id* ist vom Datentyp **uniqueidentifier** und ist erforderlich. Wenn Sie den Wert für *upload_package_id*abrufen möchten, Fragen Sie die dbo.syscollector_collector_types-Systemsicht in der msdb-Datenbank ab.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der Daten Bank Rolle " **dc_admin** (mit EXECUTE-Berechtigung)".  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Datensammlung](../../relational-databases/data-collection/data-collection.md)  
  
  
