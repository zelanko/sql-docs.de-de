---
title: catalog.Startup | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 271fd405-246a-4852-bfbe-f557241ce6ea
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 4d3087f5816b32ffa83876a32a07ccca521c9394
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68038643"
---
# <a name="catalogstartup"></a>catalog.startup 

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


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
 None  
  
## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur erfordert eine der folgenden Berechtigungen:  
  
-   READ-Berechtigung und MODIFY-Berechtigung für die Instanz der Ausführung, READ-Berechtigung und EXECUTE-Berechtigung für das Projekt und ggf. READ-Berechtigungen für die Umgebung, auf die verwiesen wird  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
  
