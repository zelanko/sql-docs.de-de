---
title: MSSQLSERVER_50000 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: supportability
ms.topic: reference
helpviewer_keywords:
- 50000 [SQL Server Native Client setup error]
ms.assetid: 5426d87a-d5d9-4984-b211-b07d69e834a2
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a9200df4bf60b0eced76bafd0755f4dd8e9a17bb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62629677"
---
# <a name="sql-server-native-client-error-mssqlserver50000"></a>SQL Server-Fehler beim nativen Client MSSQLSERVER_50000
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

    
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
  
