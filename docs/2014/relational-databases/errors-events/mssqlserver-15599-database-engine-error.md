---
title: MSSQLSERVER_15599 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 15599 (Database Engine error)
ms.assetid: 97e427a9-8587-46ea-954b-974b5df9c223
caps.latest.revision: 8
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 3678e5d075d4d81481aa0e814f85a1de4ad99009
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161812"
---
# <a name="mssqlserver15599"></a>MSSQLSERVER_15599
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|15599|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SEC_LOCAL_TEMP_AUDIT_PERMISSIONS|  
|Meldungstext|Überwachung und Berechtigungen können nicht für lokale temporäre Objekte festgelegt werden.|  
  
## <a name="explanation"></a>Erklärung  
 Überwachung und Berechtigungen haben keine Auswirkungen, wenn sie für lokale oder globale temp-Objekte festgelegt werden. Die Anweisungen haben keinem Fehler zur Folge (die Vorgänge geben Erfolg zurück), sie haben lediglich keine Auswirkungen.  
  
 Dieses Verhalten hat sich nicht geändert. Seit [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] wird der Benutzer jedoch in einer Informationsmeldung hierüber informiert.  
  
## <a name="user-action"></a>Benutzeraktion  
 Es ist keine Aktion notwendig. Sie sollten jedoch das Entfernen von Anweisungen in Erwägung ziehen, durch die Überwachung oder Berechtigungen für lokale oder globale temp-Objekte festgelegt werden.  
  
  