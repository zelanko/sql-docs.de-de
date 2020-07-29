---
title: DDL-Ereignisse | Microsoft Dokumentation
ms.custom: ''
ms.date: 11/01/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- DDL events
- DDL triggers, events
- events [SQL Server], DDL
ms.assetid: 62ef24b4-3553-4aed-b62a-670980bae501
author: rothja
ms.author: jroth
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4281b67d44e7a1aa7404e89b07a505416f38260f
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87243321"
---
# <a name="ddl-events"></a>DDL-Ereignisse
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Die folgenden Tabellen geben einen Überblick über die DDL-Ereignisse, die verwendet werden können, um einen DDL-Trigger oder eine Ereignisbenachrichtigung auszuführen. Beachten Sie, dass jedes Ereignis einer [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung oder einer gespeicherten Prozedur entspricht. Dabei wird die Anweisungssyntax so geändert, dass Unterstriche (_) zwischen Schlüsselwörtern eingefügt werden.  
  
> [!IMPORTANT]  
>  Gespeicherte Systemprozeduren, die DDL-ähnliche Vorgänge ausführen, können auch DDL-Trigger und Ereignisbenachrichtigungen auslösen. Testen Sie die DDL-Trigger oder Ereignisbenachrichtigungen, um ihre Reaktion auf gespeicherte Systemprozeduren, die ausgeführt werden, zu bestimmen. Die CREATE TYPE-Anweisung und die gespeicherte Prozedur **sp_addtype** lösen z.B. beide einen DDL-Trigger oder eine Ereignisbenachrichtigung aus, die für ein CREATE_TYPE-Ereignis erstellt wird.  
  
## <a name="ddl-statements-that-have-server-or-database-scope"></a>DDL-Anweisungen, die für Server- oder Datenbankbereich gültig sind  
 DDL-Trigger oder Ereignisbenachrichtigungen können erstellt werden, um als Antwort auf die folgenden Ereignisse ausgelöst zu werden, wenn sie in der Datenbank, in der der Trigger oder die Ereignisbenachrichtigung erstellt wurden, oder irgendwo in der Serverinstanz auftreten.  
  
:::row:::
    :::column:::
        CREATE_APPLICATION_ROLE (gilt für die CREATE APPLICATION ROLE-Anweisung und **sp_addapprole**. Wenn ein neues Schema erstellt wird, löst dieses Ereignis auch ein CREATE_SCHEMA-Ereignis aus.)
    :::column-end:::
    :::column:::
        ALTER_APPLICATION_ROLE (gilt für die ALTER APPLICATION ROLE-Anweisung und **sp_approlepassword**.)
    :::column-end:::
    :::column:::
        DROP_APPLICATION_ROLE (gilt für die DROP APPLICATION ROLE-Anweisung und **sp_dropapprole**.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_ASSEMBLY
    :::column-end:::
    :::column:::
        ALTER_ASSEMBLY
    :::column-end:::
    :::column:::
        DROP_ASSEMBLY
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_ASYMMETRIC_KEY
    :::column-end:::
    :::column:::
        ALTER_ASYMMETRIC_KEY
    :::column-end:::
    :::column:::
        DROP_ASYMMETRIC_KEY
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ALTER_AUTHORIZATION
    :::column-end:::
    :::column:::
        ALTER_AUTHORIZATION_DATABASE (gilt für die ALTER AUTHORIZATION-Anweisung, wenn ON DATABASE angegeben wird, und **sp_changedbowner**.)
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_BROKER_PRIORITY
    :::column-end:::
    :::column:::
        CREATE_BROKER_PRIORITY
    :::column-end:::
    :::column:::
        CREATE_BROKER_PRIORITY
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_CERTIFICATE
    :::column-end:::
    :::column:::
        ALTER_CERTIFICATE
    :::column-end:::
    :::column:::
        DROP_CERTIFICATE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_CONTRACT
    :::column-end:::
    :::column:::
        DROP_CONTRACT
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_CREDENTIAL
    :::column-end:::
    :::column:::
        ALTER_CREDENTIAL
    :::column-end:::
    :::column:::
        DROP_CREDENTIAL
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        GRANT_DATABASE
    :::column-end:::
    :::column:::
        DENY_DATABASE
    :::column-end:::
    :::column:::
        REVOKE_DATABASE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_DATABASE_AUDIT_SPEFICIATION
    :::column-end:::
    :::column:::
        ALTER_DATABASE_AUDIT_SPEFICIATION
    :::column-end:::
    :::column:::
        DENY_DATABASE_AUDIT_SPEFICIATION
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_DATABASE_ENCRYPTION_KEY
    :::column-end:::
    :::column:::
        ALTER_DATABASE_ENCRYPTION_KEY
    :::column-end:::
    :::column:::
        DROP_DATABASE_ENCRYPTION_KEY
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_DEFAULT
    :::column-end:::
    :::column:::
        DROP_DEFAULT
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        BIND_DEFAULT (gilt für **sp_bindefault**.)
    :::column-end:::
    :::column:::
        UNBIND_DEFAULT (gilt für **sp_unbindefault**.)
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_EVENT_NOTIFICATION
    :::column-end:::
    :::column:::
        DROP_EVENT_NOTIFICATION
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_EXTENDED_PROPERTY (gilt für **sp_addextendedproperty**.)
    :::column-end:::
    :::column:::
        ALTER_EXTENDED_PROPERTY (gilt für **sp_updateextendedproperty**.)
    :::column-end:::
    :::column:::
        DROP_EXTENDED_PROPERTY (gilt für **sp_dropextendedproperty**.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_FULLTEXT_CATALOG (gilt für die CREATE FULLTEXT CATALOG-Anweisung und **sp_fulltextcatalog** , wenn *create* angegeben wird.)
    :::column-end:::
    :::column:::
        ALTER_FULLTEXT_CATALOG (gilt für die ALTER FULLTEXT CATALOG-Anweisung und **sp_fulltextcatalog** , wenn *start_incremental*, *start_full*, *Stop*oder *Rebuild* angegeben wird, und für **sp_fulltext_database** , wenn *enable* angegeben wird.)
    :::column-end:::
    :::column:::
        DROP_FULLTEXT_CATALOG (gilt für die DROP FULLTEXT CATALOG-Anweisung und **sp_fulltextcatalog** , wenn *drop* angegeben wird.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_FULLTEXT_INDEX (gilt für die CREATE FULLTEXT INDEX-Anweisung und **sp_fulltexttable** , wenn *create* angegeben wird.)
    :::column-end:::
    :::column:::
        ALTER_FULLTEXT_INDEX (gilt für die ALTER FULLTEXT INDEX-Anweisung und **sp_fulltextcatalog** , wenn *start_full*, *start_incremental*oder *stop* angegeben wird, sowie für **sp_fulltext_column**und **sp_fulltext_table** , wenn eine andere Aktion als *create* oder *drop* angegeben wird.)
    :::column-end:::
    :::column:::
        DROP_FULLTEXT_INDEX (gilt für die DROP FULLTEXT INDEX-Anweisung und **sp_fulltexttable** , wenn *drop* angegeben wird.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_FULLTEXT_STOPLIST
    :::column-end:::
    :::column:::
        ALTER_FULLTEXT_STOPLIST
    :::column-end:::
    :::column:::
        DROP_FULLTEXT_STOPLIST
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_FUNCTION
    :::column-end:::
    :::column:::
        ALTER_FUNCTION
    :::column-end:::
    :::column:::
        DROP_FUNCTION
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_INDEX
    :::column-end:::
    :::column:::
        ALTER_INDEX (gilt für die ALTER INDEX-Anweisung und **sp_indexoption**.)
    :::column-end:::
    :::column:::
        DROP_INDEX
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_MASTER_KEY
    :::column-end:::
    :::column:::
        ALTER_MASTER_KEY
    :::column-end:::
    :::column:::
        DROP_MASTER_KEY
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_MESSAGE_TYPE
    :::column-end:::
    :::column:::
        ALTER_MESSAGE_TYPE
    :::column-end:::
    :::column:::
        DROP_MESSAGE_TYPE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_PARTITION_FUNCTION
    :::column-end:::
    :::column:::
        ALTER_PARTITION_FUNCTION
    :::column-end:::
    :::column:::
        DROP_PARTITION_FUNCTION
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_PARTITION_SCHEME
    :::column-end:::
    :::column:::
        ALTER_PARTITION_SCHEME
    :::column-end:::
    :::column:::
        DROP_PARTITION_SCHEME
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_PLAN_GUIDE (gilt für **sp_create_plan_guide**.)
    :::column-end:::
    :::column:::
        ALTER_PLAN_GUIDE (gilt für **sp_control_plan_guide** , wenn ENABLE, ENABLE ALL, DISABLE oder DISABLE ALL angegeben wird.)
    :::column-end:::
    :::column:::
        DROP_PLAN_GUIDE (gilt für **sp_control_plan_guide** , wenn DROP oder DROP ALL angegeben wird.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_PROCEDURE
    :::column-end:::
    :::column:::
        ALTER_PROCEDURE (gilt für die ALTER PROCEDURE-Anweisung und **sp_procoption**.)
    :::column-end:::
    :::column:::
        DROP_PROCEDURE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_QUEUE
    :::column-end:::
    :::column:::
        ALTER_QUEUE
    :::column-end:::
    :::column:::
        DROP_QUEUE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_REMOTE_SERVICE_BINDING
    :::column-end:::
    :::column:::
        ALTER_REMOTE_SERVICE_BINDING
    :::column-end:::
    :::column:::
        DROP_REMOTE_SERVICE_BINDING
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SPATIAL_INDEX
    :::column-end:::
    :::column:::
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        RENAME (gilt für **sp_rename**)
    :::column-end:::
    :::column:::
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_ROLE (gilt für die CREATE ROLE-Anweisung, **sp_addrole**und **sp_addgroup**.)
    :::column-end:::
    :::column:::
        ALTER_ROLE
    :::column-end:::
    :::column:::
        DROP_ROLE (gilt für die DROP ROLE-Anweisung, **sp_droprole**und **sp_dropgroup**.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ADD_ROLE_MEMBER
    :::column-end:::
    :::column:::
        DROP_ROLE_MEMBER
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_ROUTE
    :::column-end:::
    :::column:::
        ALTER_ROUTE
    :::column-end:::
    :::column:::
        DROP_ROUTE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_RULE
    :::column-end:::
    :::column:::
        DROP_RULE
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        BIND_RULE (gilt für **sp_bindrule**.)
    :::column-end:::
    :::column:::
        UNBIND_RULE (gilt für **sp_unbindrule**.)
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SCHEMA (gilt für die CREATE SCHEMA-Anweisung, **sp_addrole**, **sp_adduser**, **sp_addgroup**und **sp_grantdbaccess**.)
    :::column-end:::
    :::column:::
        ALTER_SCHEMA (gilt für die ALTER SCHEMA-Anweisung und **sp_changeobjectowner**.)
    :::column-end:::
    :::column:::
        DROP_SCHEMA
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SEARCH_PROPERTY_LIST
    :::column-end:::
    :::column:::
        ALTER_SEARCH_PROPERTY_LIST
    :::column-end:::
    :::column:::
        DROP_SEARCH_PROPERTY_LIST
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SEQUENCE_EVENTS
    :::column-end:::
    :::column:::
        CREATE_SEQUENCE_EVENTS
    :::column-end:::
    :::column:::
        CREATE_SEQUENCE_EVENTS
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SERVER_ROLE
    :::column-end:::
    :::column:::
        ALTER_SERVER_ROLE
    :::column-end:::
    :::column:::
        DROP_SERVER_ROLE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SERVICE
    :::column-end:::
    :::column:::
        ALTER_SERVICE
    :::column-end:::
    :::column:::
        DROP_SERVICE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ALTER_SERVICE_MASTER_KEY
    :::column-end:::
    :::column:::
        BACKUP_SERVICE_MASTER_KEY
    :::column-end:::
    :::column:::
        RESTORE_SERVICE_MASTER_KEY
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ADD_SIGNATURE (für Signaturvorgänge von Objekten ohne Schemabereich; Datenbank, Assembly, Trigger)
    :::column-end:::
    :::column:::
        DROP_SIGNATURE
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ADD_SIGNATURE_SCHEMA_OBJECT (für Objekte mit Schemabereich; gespeicherte Prozeduren, Funktionen)
    :::column-end:::
    :::column:::
        DROP_SIGNATURE_SCHEMA_OBJECT
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SPATIAL_INDEX
    :::column-end:::
    :::column:::
        ALTER_INDEX kann für räumliche Indizes verwendet werden.
    :::column-end:::
    :::column:::
        DROP_INDEX kann für räumliche Indizes verwendet werden.
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_STATISTICS
    :::column-end:::
    :::column:::
        DROP_STATISTICS
    :::column-end:::
    :::column:::
        UPDATE_STATISTICS
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SYMMETRIC_KEY
    :::column-end:::
    :::column:::
        ALTER_SYMMETRIC_KEY
    :::column-end:::
    :::column:::
        DROP_SYMMETRIC_KEY
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SYNONYM
    :::column-end:::
    :::column:::
        DROP_SYNONYM
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_TABLE
    :::column-end:::
    :::column:::
        ALTER_TABLE (gilt für die ALTER TABLE-Anweisung und **sp_tableoption**.)
    :::column-end:::
    :::column:::
        DROP_TABLE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_TRIGGER
    :::column-end:::
    :::column:::
        ALTER_TRIGGER (gilt für die ALTER TRIGGER-Anweisung und **sp_settriggerorder**.)
    :::column-end:::
    :::column:::
        DROP_TRIGGER
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_TYPE (gilt für die CREATE TYPE-Anweisung und **sp_addtype**.)
    :::column-end:::
    :::column:::
        DROP_TYPE (gilt für die DROP TYPE-Anweisung und **sp_droptype**.)
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_USER (gilt für die CREATE USER-Anweisung, **sp_adduser**und **sp_grantdbaccess**.)
    :::column-end:::
    :::column:::
        ALTER_USER (gilt für die ALTER USER-Anweisung und **sp_change_users_login**.)
    :::column-end:::
    :::column:::
        DROP_USER (gilt für die DROP USER-Anweisung, **sp_dropuser**und **sp_revokedbaccess**.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_VIEW
    :::column-end:::
    :::column:::
        ALTER_VIEW
    :::column-end:::
    :::column:::
        DROP_VIEW
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_XML_INDEX
    :::column-end:::
    :::column:::
        ALTER_INDEX kann für XML-Indizes verwendet werden.
    :::column-end:::
    :::column:::
        DROP_INDEX kann für XML-Indizes verwendet werden.
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_XML_SCHEMA_COLLECTION
    :::column-end:::
    :::column:::
        ALTER_XML_SCHEMA_COLLECTION
    :::column-end:::
    :::column:::
        DROP_XML_SCHEMA_COLLECTION
    :::column-end:::
:::row-end:::
 
## <a name="ddl-statements-that-have-server-scope"></a>DDL-Anweisungen, die für den Serverbereich gültig sind  
 DDL-Trigger oder Ereignisbenachrichtigungen können erstellt werden, um als Antwort auf die folgenden Ereignisse ausgelöst zu werden, wenn sie irgendwo in der Serverinstanz auftreten.  
  
:::row:::
    :::column:::
        ALTER_AUTHORIZATION_SERVER
    :::column-end:::
    :::column:::
        ALTER_SERVER_CONFIGURATION
    :::column-end:::
    :::column:::
        ALTER_INSTANCE (gilt für **sp_configure** und **sp_addserver** , wenn eine lokale Serverinstanz angegeben wird.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_AVAILABILITY_GROUP
    :::column-end:::
    :::column:::
        ALTER_AVAILABILITY_GROUP
    :::column-end:::
    :::column:::
        DROP_AVAILABILITY_GROUP
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_CREDENTIAL
    :::column-end:::
    :::column:::
        ALTER_CREDENTIAL
    :::column-end:::
    :::column:::
        DROP_CREDENTIAL
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_CRYPTOGRAPHIC_PROVIDER
    :::column-end:::
    :::column:::
        ALTER_CRYPTOGRAPHIC_PROVIDER
    :::column-end:::
    :::column:::
        DROP_CRYPTOGRAPHIC_PROVIDER
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_DATABASE
    :::column-end:::
    :::column:::
        ALTER_DATABASE (gilt für die ALTER DATABASE-Anweisung und **sp_fulltext_database**.)
    :::column-end:::
    :::column:::
        DROP_DATABASE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_ENDPOINT
    :::column-end:::
    :::column:::
        ALTER_ENDPOINT
    :::column-end:::
    :::column:::
        DROP_ENDPOINT
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_EVENT_SESSION
    :::column-end:::
    :::column:::
        ALTER_EVENT_SESSION
    :::column-end:::
    :::column:::
        DROP_EVENT_SESSION
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_EXTENDED_PROCEDURE (gilt für **sp_addextendedproc**.)
    :::column-end:::
    :::column:::
        DROP_EXTENDED_PROCEDURE (gilt für **sp_dropextendedproc**.)
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_LINKED_SERVER (gilt für **sp_addlinkedserver**.)
    :::column-end:::
    :::column:::
        ALTER_LINKED_SERVER (gilt für **sp_serveroption**.)
    :::column-end:::
    :::column:::
        DROP_LINKED_SERVER (gilt für **sp_dropserver** , wenn ein Verbindungsserver angegeben wird.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_LINKED_SERVER_LOGIN (gilt für **sp_addlinkedsrvlogin**.)
    :::column-end:::
    :::column:::
        DROP_LINKED_SERVER_LOGIN (gilt für **sp_droplinkedsrvlogin**.)
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_LOGIN (gilt für die CREATE LOGIN-Anweisung, **sp_addlogin**, **sp_grantlogin**, **xp_grantlogin**und **sp_denylogin** bei Verwendung für einen nicht vorhandenen Anmeldenamen, der implizit erstellt werden muss.)
    :::column-end:::
    :::column:::
        ALTER_LOGIN (gilt für die ALTER LOGIN-Anweisung, **sp_defaultdb**, **sp_defaultlanguage**, **sp_password**und **sp_change_users_login** , wenn *Auto_Fix* angegeben wird.)
    :::column-end:::
    :::column:::
        DROP_LOGIN (gilt für die DROP LOGIN-Anweisung, **sp_droplogin**, **sp_revokelogin**und **xp_revokelogin**.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_MESSAGE (gilt für **sp_addmessage**.)
    :::column-end:::
    :::column:::
        ALTER_MESSAGE (gilt für **sp_altermessage**.)
    :::column-end:::
    :::column:::
        DROP_MESSAGE (gilt für **sp_dropmessage**.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_REMOTE_SERVER (gilt für **sp_addserver**.)
    :::column-end:::
    :::column:::
        ALTER_REMOTE_SERVER (gilt für **sp_setnetname**.)
    :::column-end:::
    :::column:::
        DROP_REMOTE_SERVER (gilt für **sp_dropserver** , wenn ein Remoteserver angegeben wird.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_RESOURCE_POOL
    :::column-end:::
    :::column:::
        ALTER_RESOURCE_POOL
    :::column-end:::
    :::column:::
        DROP_RESOURCE_POOL
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        GRANT_SERVER
    :::column-end:::
    :::column:::
        DENY_SERVER
    :::column-end:::
    :::column:::
        REVOKE_SERVER
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ADD_SERVER_ROLE_MEMBER
    :::column-end:::
    :::column:::
        DROP_SERVER_ROLE_MEMBER
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SERVER_AUDIT
    :::column-end:::
    :::column:::
        ALTER_SERVER_AUDIT
    :::column-end:::
    :::column:::
        DROP_SERVER_AUDIT
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SERVER_AUDIT_SPECIFICATION
    :::column-end:::
    :::column:::
        ALTER_SERVER_AUDIT_SPECIFICATION
    :::column-end:::
    :::column:::
        DROP_SERVER_AUDIT_SPECIFICATION
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_WORKLOAD_GROUP
    :::column-end:::
    :::column:::
        ALTER_WORKLOAD_GROUP
    :::column-end:::
    :::column:::
        DROP_WORKLOAD_GROUP
    :::column-end:::
:::row-end:::
 
## <a name="see-also"></a>Weitere Informationen  
 [DDL-Trigger](../../relational-databases/triggers/ddl-triggers.md)   
 [Ereignisbenachrichtigungen](../../relational-databases/service-broker/event-notifications.md)   
 [DDL-Ereignisgruppen](../../relational-databases/triggers/ddl-event-groups.md)  
  
  
