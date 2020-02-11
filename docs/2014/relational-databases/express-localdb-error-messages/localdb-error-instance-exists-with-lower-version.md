---
title: LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: a7c5ce08-8841-49a3-b252-116807ba469a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b3bc344e3e23ce965a2057628e4662ebe41508d2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62990928"
---
# <a name="localdb_error_instance_exists_with_lower_version"></a>LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|258|  
|Ereignisquelle|Lokale SQL Server-Datenbanklaufzeit 12.0|  
|Komponente|Laufzeit-API der lokalen Datenbank|  
|Meldungstext|Es konnte keine lokale Datenbankinstanz der angegebenen Version erstellt werden. Eine Instanz mit diesem Namen ist zwar bereits vorhanden, aber deren Version ist niedriger als die angegebene Version.|  
  
## <a name="explanation"></a>Erklärung  
 Die angegebene Instanz ist bereits vorhanden, aber ihre Version ist niedriger als angefordert.  
  
## <a name="user-action"></a>Benutzeraktion  
 Löschen Sie die vorhandene Instanz, und wiederholen Sie den Vorgang.  
  
  
