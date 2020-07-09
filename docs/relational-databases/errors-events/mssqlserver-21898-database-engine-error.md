---
title: MSSQLSERVER_21898 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 21898 (Database Engine error)
ms.assetid: 02405b21-3d4e-4c2d-b4b3-d7b1ec05edb4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3ba4350b6fc8b9b39833bdf5bdf0c7f7a8613ee7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780493"
---
# <a name="mssqlserver_21898"></a>MSSQLSERVER_21898
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|21898|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SQLErrorNum21898|  
|Meldungstext|Der Verleger '%s' verwendet Verteilungsdatenbank '%s' und nicht '%s', die erforderlich ist, um die Veröffentlichungsdatenbank '%s' zu hosten. Führen Sie **sp_changedistpublisher** auf dem Verteiler '%s' aus, um die vom Verleger verwendete Verteilungsdatenbank in '%s' zu ändern.|  
  
## <a name="explanation"></a>Erklärung  
**sp_validate_redirected_publisher** fragt „msdb.dbo.MSdistpublisher“ beim lokalen Verteiler ab, um zu überprüfen, ob die vom neuen Verleger verwendete Verteilungsdatenbank mit der vom ursprünglichen Verleger verwendeten Verteilungsdatenbank identisch ist. Dieser Fehler wird zurückgegeben, wenn diese Datenbanken verschieden sind und sich der Verleger deswegen nicht mehr als Host für die Verlegerdatenbank eignet.  
  
## <a name="user-action"></a>Benutzeraktion  
Führen Sie die gespeicherte Prozedur **sp_changedistpublisher** aus, um die Verteilungsdatenbank für den neuen Verleger in die vom ursprünglichen Verleger verwendete Verteilungsdatenbank zu ändern.  
  
> [!NOTE]  
> Durch die Ausführung von **sp_changedistpublisher** wird das Problem behoben, wenn die falsche Verteilungsdatenbank angegeben wurde, als **sp_adddistpublisher** beim Verteiler für den Verleger ausgeführt wurde. Wenn der Remoteverleger jedoch über vorhandene Veröffentlichungen aus einer anderen Veröffentlichungsdatenbank verfügt, für die die identifizierte Verteilungsdatenbank genutzt wird, dann ist diese Änderung ungeeignet. Die Replikation mit der benannten Verteilungsdatenbank muss systematisch entfernt und dann mit der Verteilungsdatenbank des ursprünglichen Verlegers wieder eingerichtet werden, damit der neue Verleger ordnungsgemäß als Host fungieren kann.  
  
