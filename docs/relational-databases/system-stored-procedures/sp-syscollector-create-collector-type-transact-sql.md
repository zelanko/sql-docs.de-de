---
title: sp_syscollector_create_collector_type (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_create_collector_type
- sp_syscollector_create_collector_type_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_create_collector_type
- data collector [SQL Server], stored procedures
ms.assetid: 568e9119-b9b0-4284-9cef-3878c691de5f
author: stevestein
ms.author: sstein
ms.openlocfilehash: bd8c82a401f78f4907bb891ede845017c00ac5ad
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68032632"
---
# <a name="sp_syscollector_create_collector_type-transact-sql"></a>sp_syscollector_create_collector_type (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Erstellt einen Sammlertyp für den Datensammler. Ein Sammlertyp ist ein logischer Wrapper um [!INCLUDE[ssIS](../../includes/ssis-md.md)] die Pakete, die den eigentlichen Mechanismus für das Sammeln von Daten und das Hochladen in die Verwaltungs Data Warehouse bereitstellen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syscollector_create_collector_type   
    [ [@collector_type_uid = ] 'collector_type_uid' OUTPUT ]  
    , [ @name = ] 'name'  
    , [ [ @parameter_schema = ] 'parameter_schema' ]  
    , [ [ @parameter_formatter = ] 'parameter_formatter' ]  
    , [ @collection_package_id = ] 'collection_package_id'  
    , [ @upload_package_id = ] 'upload_package_id'  
```  
  
## <a name="arguments"></a>Argumente  
 [ @collector_type_uid = ] "*collector_type_uid*"  
 Die GUID für den Sammlertyp. *collector_type_uid* ist vom Datentyp **uniqueidentifier** , und wenn er NULL ist, wird er automatisch erstellt und als Output zurückgegeben.  
  
 [ @name = ] "*Name*"  
 Der Name des Sammlertyps. *Name ist vom Datentyp* **vom Datentyp sysname** und muss angegeben werden.  
  
 [ @parameter_schema = ] "*parameter_schema*"  
 Das XML-Schema für diesen Sammlertyp. *parameter_schema* ist vom Typ **XML** und hat den Standardwert NULL.  
  
 [ @parameter_formatter = ] "*parameter_formatter*"  
 Die Vorlage, mit der das XML für die Eigenschaftenseite des Sammlungssatzes umgewandelt werden kann. *parameter_formatter* ist vom Typ **XML** und hat den Standardwert NULL.  
  
 [@collection_package_id = ] *collection_package_id*  
 Ein eindeutiger lokaler Bezeichner, der auf das [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Sammlungspaket verweist, das vom Sammlungssatz verwendet wird. *collection_package_id* ist vom datnoch **uniqueidentifier** und ist erforderlich.  
  
 [@upload_package_id = ] *upload_package_id*  
 Ein eindeutiger lokaler Bezeichner, der auf das [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Uploadpaket verweist, das vom Sammlungssatz verwendet wird. *upload_package_id* ist vom Datentyp **uniqueidentifier** und ist erforderlich.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="permissions"></a>Berechtigungen  
 Damit diese Prozedur ausgeführt werden kann, ist die Mitgliedschaft in der festen Datenbankrolle dc_admin (mit EXECUTE-Berechtigung) erforderlich.  
  
## <a name="example"></a>Beispiel  
 Dies erstellt den generischen T-SQL-Abfragesammlertyp.  
  
```  
EXEC sp_syscollector_create_collector_type  
@collector_type_uid = '302E93D1-3424-4be7-AA8E-84813ECF2419',  
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
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Datensammlung](../../relational-databases/data-collection/data-collection.md)  
  
  
