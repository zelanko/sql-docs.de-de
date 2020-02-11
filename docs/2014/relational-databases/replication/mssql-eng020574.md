---
title: MSSQL_ENG020574 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG02574 error
ms.assetid: 4e98f8de-287c-4090-81ee-dc8f80dfa6a1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4788e7696b9bb986ab5a16fb2fea618d0b996cc9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62938605"
---
# <a name="mssql_eng020574"></a>MSSQL_ENG020574
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|20574|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Fehler bei der Datenüberprüfung für das Abonnement des Abonnenten '%s' für den '%s'-Artikel in der '%s'-Veröffentlichung.|  
  
## <a name="explanation"></a>Erklärung  
 Die Daten des Abonnenten wurden gegen die Daten des Verlegers abgeglichen, und es wurde keine Übereinstimmung der Daten festgestellt. Daher konnte die Überprüfung nicht erfolgreich abgeschlossen werden. Weitere Informationen zur Überprüfung finden Sie unter [Validate Replicated Data](validate-data-at-the-subscriber.md).  
  
## <a name="user-action"></a>Benutzeraktion  
 Folgendes Vorgehen wird empfohlen:  
  
-   Ermitteln Sie den Grund für den Fehler bei der Überprüfung.  
  
-   Beheben Sie das zugrunde liegende Problem, das zu dem Fehler geführt hat.  
  
-   Stellen Sie die Konvergenz der Daten her, indem Sie das Abonnement erneut initialisieren oder eine andere geeignete Methode verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)  
  
  
