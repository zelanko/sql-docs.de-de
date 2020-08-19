---
description: sysssispackagefolders (Transact-SQL)
title: sysssispackagefolders (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdtspackagefolders90
- sysdtspackagefolders90_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysssispackagefolders system table
ms.assetid: ddc4833f-27bf-4610-b739-d257961d17ac
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7924de782ca499f5a92458d0024b57877c7310c0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419124"
---
# <a name="sysssispackagefolders-transact-sql"></a>sysssispackagefolders (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Enthält eine Zeile für jeden logischen Ordner in der Ordnerhierarchie, der von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] verwendet wird. Diese Ordner sind im Objekt-Explorer von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] aufgeführt, wenn Sie eine Verbindung mit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]herstellen. In einem Ordner sind Pakete aufgeführt, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder im Dateisystem gespeichert sind.  
  
 In der **parentfolderid** -Spalte wird die Ordnerhierarchie beschrieben. Der oberste Ordner in der Ordnerhierarchie enthält einen NULL-Wert in **parentfolderid**.  
  
 Die **foldername** -Spalte enthält den Namen der im Objekt-Explorer angezeigten Ordner.  
  
 Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  

  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**folderid**|**uniqueidentifier**|Der GUID des Ordners.|  
|**parentfolderid**|**uniqueidentifier**|Der GUID des Ordners, der als übergeordneter Ordner verwendet wird.|  
|**FolderName**|**sysname**|Der Name des Ordners. Dieser Name wird in der Ordnerhierarchie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]angezeigt.|  
  
  
