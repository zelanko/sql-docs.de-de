---
title: MSSQLSERVER_21898 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21898 (Database Engine error)
ms.assetid: 02405b21-3d4e-4c2d-b4b3-d7b1ec05edb4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c59f74a3e0584ec70eea4832936d7dc08cc74087
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62868960"
---
# <a name="mssqlserver21898"></a>MSSQLSERVER_21898
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|21898|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SQLErrorNum21898|  
|Meldungstext|Der Verleger '%s' verwendet Verteilungsdatenbank '%s' und nicht '%s', die erforderlich ist, um die Veröffentlichungsdatenbank '%s' zu hosten. Führen Sie `sp_changedistpublisher` auf dem Verteiler '%s' aus, um die vom Verleger verwendete Verteilungsdatenbank in '%s' zu ändern.|  
  
## <a name="explanation"></a>Erklärung  
 `sp_validate_redirected_publisher` fragt "msdb.dbo.msdistpublisher" auf dem lokalen Verteiler, um sicherzustellen, dass die vom neuen Verleger verwendete Verteilungsdatenbank vom ursprünglichen Verleger verwendeten Verteilungsdatenbank identisch ist. Dieser Fehler wird zurückgegeben, wenn diese Datenbanken verschieden sind und sich der Verleger deswegen nicht mehr als Host für die Verlegerdatenbank eignet.  
  
## <a name="user-action"></a>Benutzeraktion  
 Führen Sie gespeicherte Prozedur `sp_changedistpublisher` aus, um die Verteilungsdatenbank für den neuen Verleger in die vom ursprünglichen Verleger verwendete Verteilungsdatenbank zu ändern.  
  
> [!NOTE]  
>  Durch die Ausführung von `sp_changedistpublisher` wird das Problem behoben, wenn die falsche Verteilungsdatenbank angegeben wurde, als `sp_adddistpublisher` beim Verteiler für den Verleger ausgeführt wurde. Wenn der Remoteverleger jedoch über vorhandene Veröffentlichungen aus einer anderen Veröffentlichungsdatenbank verfügt, für die die identifizierte Verteilungsdatenbank genutzt wird, dann ist diese Änderung ungeeignet. Die Replikation mit der benannten Verteilungsdatenbank muss systematisch entfernt und dann mit der Verteilungsdatenbank des ursprünglichen Verlegers wieder eingerichtet werden, damit der neue Verleger ordnungsgemäß als Host fungieren kann.  
  
  
