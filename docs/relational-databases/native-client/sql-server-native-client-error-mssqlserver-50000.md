---
title: MSSQLSERVER_50000 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- 50000 [SQL Server Native Client setup error]
ms.assetid: 5426d87a-d5d9-4984-b211-b07d69e834a2
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 70def08da23491bbfce4d17a38037efc7f6477c8
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85787619"
---
# <a name="sql-server-native-client-error-mssqlserver_50000"></a>SQL Server-Fehler beim nativen Client MSSQLSERVER_50000
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Produktversion|11.0|  
|Ereignis-ID|50000|  
|Ereignisquelle|SETUP|  
|Komponente|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client|  
|Symbolischer Name||  
|Meldungstext|Netzwerkfehler beim Lesen der Datei '% * ls'.|  
  
## <a name="explanation"></a>Erklärung  
 Es wurde versucht, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client auf einem Computer zu installieren (oder zu aktualisieren), auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client bereits installiert ist und die vorhandene Installation über eine MSI-Datei ausgeführt wurde, die ursprünglich den Namen sqlncli.msi hatte und dann umbenannt wurde.  
  
## <a name="user-action"></a>Benutzeraktion  
 Um diesen Fehler zu beheben, deinstallieren Sie die vorhandene Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Um den Fehler zu verhindern, installieren Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client über eine MSI-Datei, die nicht sqlncli.msi heißt.  
  
## <a name="internal-only"></a>Nur intern  
  
