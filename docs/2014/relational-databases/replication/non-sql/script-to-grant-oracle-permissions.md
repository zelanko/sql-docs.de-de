---
title: Skript zum Erteilen von Oracle-Berechtigungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], script to grant permissions
ms.assetid: d742fd30-347a-452f-b5fc-b03232360c6b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d7c61a21f149a50c4893c9c82d3624e0905a481b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63022426"
---
# <a name="script-to-grant-oracle-permissions"></a>Skript zum Erteilen von Oracle-Berechtigungen
  Das in diesem Thema bereitgestellte Skript wird während der Konfiguration von Oracle-Datenbanken verwendet, die Daten mithilfe der [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Replikation veröffentlichen. Nach der Installation ist das Skript auch in folgendem Verzeichnis verfügbar: *\<Laufwerk>* :\\\Programme\Microsoft SQL Server\\ *\<Instanzname>* \MSSQL\Install\oracleadmin.sql. Weitere Informationen zum Konfigurieren der Oracle-Datenbank finden Sie unter [Konfigurieren eines Oracle-Verlegers](configure-an-oracle-publisher.md).  
  
> [!NOTE]  
>  Dieses Skript enthält die `GRANT CREATE ANY TRIGGER TO &&AdminLogin;`-Anweisung. Diese Anweisung ist für die von der Transaktionsreplikation verwendeten Trigger erforderlich. Wenn Sie ausschließlich mit Momentaufnahmereplikation arbeiten, können Sie diese Zeile aus dem Skript entfernen.  
  
 **Ausführen des Skripts vom Oracle SQL\*Plus-Hilfsprogramm**  
  
1.  Öffnen Sie auf dem SQL Server-Verteiler das Fenster Eingabeaufforderung.  
  
2.  Geben Sie die folgende Syntax ein, um SQL*PLUS zum Verbinden von Oracle-Datenbanken und zum Ausführen des oracleadmin.sql-Skripts von seinem Standardinstallationsverzeichnis zu verwenden:  
  
    ```  
    sqlplus system/P@$$W0rd@orcl @"c:\Program Files\Microsoft SQL Server\<InstanceName>\MSSQL\Install\oracleadmin.sql"  
    ```  
  
     In diesem Beispiel wird das in Oracle integrierte **system** -Konto zum Verbinden mit einer Oracle-Datenbank mit einem Netzwerknamen von "orcl" verwendet.  
  
3.  Geben Sie bei Aufforderung den Benutzernamen, das Benutzerkennwort und den standardmäßigen Tabellenbereich an.  
  
```  
--***********************************************************************  
-- Copyright (c) 2003 Microsoft Corporation  
--  
-- File:  
--  oracleadmin.sql  
--  
-- Purpose:  
-- PL/SQL script to create a database user with the required   
-- permissions to administer SQL Server publishing for an Oracle  
-- database.  
--  
-- &&ReplLogin        == Replication user login  
-- &&ReplPassword     == Replication user password  
-- &&DefaultTablespace == Tablespace that will serve as the default  
-- tablespace for the replication user.  
-- The replication user will be authorized to allocate UNLIMITED space  
-- on the default tablespace, which must already exist.  
--  
-- Notes:  
--  
-- This script must be run from an Oracle login having the  
-- authorization to create a new user and grant unlimited tablespace on  
-- any existing tablespace. The login must also be able to grant to the  
-- newly created login the following authorizations:  
--  
-- create public synonym  
-- drop public synonym  
-- create sequence  
--  create procedure  
-- create session  
-- create table  
-- create view  
--  
-- Additionally, the following properties are also required for  
-- transactional publications.  
--  
-- create any trigger  
--  
--  All of the privileges may be granted through a role, with the  
-- exception of create table, create view, and create any trigger.  
-- These must be granted explicitly to the replication user login.  
-- In the script, all grants are granted explicitly to the replication  
-- user.  
--  
-- In addition to these general grants, a table owner must explicitly  
-- grant select authorization to the replication user on a table before  
-- the table can be published.  
--  
***********************************************************************  
  
ACCEPT ReplLogin CHAR PROMPT 'User to create for replication: ';  
ACCEPT ReplPassword CHAR PROMPT 'Replication user passsword: ' HIDE;  
ACCEPT DefaultTableSpace CHAR DEFAULT 'SYSTEM' PROMPT 'Default tablespace: ';  
  
-- Create the replication user account  
CREATE USER &&ReplLogin IDENTIFIED BY &&ReplPassword DEFAULT TABLESPACE &&DefaultTablespace QUOTA UNLIMITED ON &&DefaultTablespace;  
  
-- It is recommended that only the required grants be granted to this  
-- user.  
--  
-- The following 5 privileges are granted explicitly, but could be  
-- granted through a role.  
GRANT CREATE PUBLIC SYNONYM TO &&ReplLogin;  
GRANT DROP PUBLIC SYNONYM TO &&ReplLogin;  
GRANT CREATE SEQUENCE TO &&ReplLogin;  
GRANT CREATE PROCEDURE TO &&ReplLogin;  
GRANT CREATE SESSION TO &&ReplLogin;  
  
-- The following privileges must be granted explicitly to the  
-- replication user.  
GRANT CREATE TABLE TO &&ReplLogin;  
GRANT CREATE VIEW TO &&ReplLogin;  
  
-- The replication user login needs to be able to create a tracking  
-- trigger on any table that is to be published in a transactional  
-- publication. The CREATE ANY privilege is used to obtain the  
-- authorization to create these triggers.  To replicate a table, the  
-- table owner must additionally explicitly grant select authorization  
-- on the table to the replication user.  
--  
-- NOTE: CREATE ANY TRIGGER is not required for snapshot publications.  
GRANT CREATE ANY TRIGGER TO &&ReplLogin;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren eines Oracle-Verlegers](configure-an-oracle-publisher.md)  
  
  
