---
title: catalog.Startup | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 271fd405-246a-4852-bfbe-f557241ce6ea
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1625d2a4fb9251d9d6a3722dc4f54578e0dbd8ed
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="catalogstartup"></a>catalog.startup
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Führt eine Wartung des Status von Vorgängen für den SSISDB-Katalog aus.  
  
 Durch die gespeicherte Prozedur wird der Status aller Pakete korrigiert, die während des Ausfalls (falls zutreffend) der [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Serverinstanz ausgeführt wurden.  
  
 Sie haben die Möglichkeit, die gespeicherte Prozedur automatisch ausführen zu lassen, sobald die [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Serverinstanz neu gestartet wird. Dazu wählen Sie im Dialogfeld **Katalog erstellen** die Option **Automatische Ausführung gespeicherter Integration Services-Prozeduren beim Starten von SQL Server aktivieren** aus.  
  
## <a name="syntax"></a>Syntax  
  
```sql  
catalog.startup  
```  
  
## <a name="return-code-value"></a>Rückgabecodewert  
 0 (Erfolg)  
  
## <a name="result-sets"></a>Resultsets  
 InclusionThresholdSetting  
  
## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur erfordert eine der folgenden Berechtigungen:  
  
-   READ-Berechtigung und MODIFY-Berechtigung für die Instanz der Ausführung, READ-Berechtigung und EXECUTE-Berechtigung für das Projekt und ggf. READ-Berechtigungen für die Umgebung, auf die verwiesen wird  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
  
