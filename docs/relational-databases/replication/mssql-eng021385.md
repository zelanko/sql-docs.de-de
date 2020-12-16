---
description: MSSQL_ENG021385
title: MSSQL_ENG021385 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021385 error
ms.assetid: a2c0444f-d97b-4760-8905-3574791c2e26
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016
ms.openlocfilehash: 84cd64ba75f7a87fa7d4f93173d8b0537ddc7f93
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97469081"
---
# <a name="mssql_eng021385"></a>MSSQL_ENG021385
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
    
## <a name="message-details"></a>Meldungsdetails  
  
|attribute|Wert|  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|21385|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Der Momentaufnahmevorgang konnte die %1!s!-Veröffentlichung nicht verarbeiten. Möglicherweise ist gerade eine Schemaänderungsaktivität aktiv, oder es werden neue Artikel hinzugefügt.|  
  
## <a name="explanation"></a>Erklärung  
 Dieser Fehler wird ausgelöst, wenn die Ausführung des Momentaufnahme-Agents beginnt, während gerade Änderungen an der Veröffentlichung vorgenommen werden, z. B. Hinzufügen oder Löschen von Artikeln oder das Ausführen von Schemaänderungen an veröffentlichten Objekten.  
  
## <a name="user-action"></a>Benutzeraktion  
 Starten Sie den Momentaufnahme-Agent erneut, nachdem die Änderungen an der Veröffentlichungsdatenbank abgeschlossen sind. Weitere Informationen finden Sie unter [Starten und Beenden eines Replikations-Agents &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) oder [Ausführbare Konzepte für die Programmierung von Replikations-Agents](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
