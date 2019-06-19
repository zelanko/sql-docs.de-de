---
title: Ändern der Edgeeinschränkungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- alter edge constraints
- edge constraints [SQL Server]
- CONNECTION constraints
- edge constraints [Azure SQL Database]
- graph edge constraints
- SQL Graph
ms.assetid: ''
author: shkale-msft
ms.author: shkale
manager: craigg
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e5b6a471156f0b1371c727ce96aac72f4f812dac
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62693304"
---
# <a name="modify-edge-constraints"></a>Ändern der Edgeeinschränkungen
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx.md](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

  Sie können mit [!INCLUDE[tsql](../../includes/tsql-md.md)] eine Edgeeinschränkung in [!INCLUDE[ssNoversion](../../includes/ssnoversion-md.md)] ändern. Sie können die Edgeeinschränkung einer Edgetabelle ändern, indem Sie die Reihenfolge der Edgeeinschränkungsklausel ändern oder eine neue Klausel hinzufügen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **So ändern Sie eine Edgeeinschränkung**  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für die Tabelle.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL
 Um eine Edgeeinschränkung mit Transact-SQL ändern zu können, müssen Sie zuerst die vorhandene Edgeeinschränkung löschen und sie dann mit der neuen Definition neu erstellen. Weitere Informationen finden Sie unter [Löschen von Edgeeinschränkungen](../../relational-databases/tables/delete-edge-constraint.md) und [Erstellen von Edgeeinschränkungen](../../relational-databases/tables/create-edge-constraints.md).    
 
