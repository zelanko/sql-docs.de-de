---
title: MSSQL_ENG003724 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG003724 error
ms.assetid: 10cb119d-92df-4124-b85d-cd2f2666c99c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f3ea7c8720d43fdba53821091c0664bfe375a57b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/25/2020
ms.locfileid: "63191447"
---
# <a name="mssql_eng003724"></a>MSSQL_ENG003724
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|3724|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Das %1!s! von '%3!s!' (%2!s!) ist nicht möglich, da das Objekt für die Replikation verwendet wird.|  
  
## <a name="explanation"></a>Erklärung  
 Wenn Sie Objekte in einer Datenbank replizieren, werden diese Objekte in der **sysarticles** -Systemtabelle (bei Momentaufnahmen- und Transaktionsveröffentlichungen) bzw. **sysmergearticles** (bei Mergeveröffentlichungen) als repliziert gekennzeichnet. Dieser Fehler wird ausgelöst, wenn Sie versuchen, ein repliziertes Objekt zu löschen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Stellen Sie vor dem Löschen sicher, dass das Datenbankobjekt nicht repliziert ist. Beispiel:  
  
-   Tritt der Fehler in der Veröffentlichungsdatenbank auf, löschen Sie den Artikel aus der Veröffentlichung, bevor Sie das Objekt löschen. Weitere Informationen finden Sie unter [Hinzufügen und Löschen von Artikeln aus vorhandenen Veröffentlichungen](publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
-   Tritt der Fehler in der Abonnementdatenbank auf, löschen Sie das Abonnement, bevor Sie das Objekt löschen. Weitere Informationen finden Sie unter [Abonnieren von Veröffentlichungen](subscribe-to-publications.md). Bei Abonnements für Transaktionsreplikationen besteht die Möglichkeit, nicht gleich die gesamte Veröffentlichung zu löschen, sondern nur das Abonnement eines einzelnen Artikels zu löschen. Weitere Informationen finden Sie unter [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql).  
  
 Falls dieser Fehler in einer Datenbank auftritt, die nicht repliziert wird, führen Sie [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) aus, um sicherzustellen, dass die Objekte in der Datenbank nicht als repliziert hervorgehoben sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)  
  
  
