---
title: MSSQLSERVER_15599 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 15599 (Database Engine error)
ms.assetid: 97e427a9-8587-46ea-954b-974b5df9c223
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 01ad3f136b948fc9d62d863a91c9c1b9a571edea
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver15599"></a>MSSQLSERVER_15599
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
