---
title: MSSQLSERVER_30053 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: 8ad23889-e243-4bd7-bc3e-150403399d89
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2b753397b4791d658692a8cb63dbc6a3d779c621
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62914357"
---
# <a name="mssqlserver_30053"></a>MSSQLSERVER_30053
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|30053|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|FTXT_QUERY_E_WORDBREAKINGTIMEOUT|  
|Meldungstext|Timeout bei der Wörtertrennung für die Volltextabfragezeichenfolge. Dies kann passieren, wenn die Verarbeitung der Volltextabfragezeichenfolge lange dauert oder eine große Anzahl von Abfragen auf dem Server ausgeführt wird. Führen Sie die Abfrage bei geringerer Auslastung erneut aus.|  
  
## <a name="explanation"></a>Erklärung  
 In den folgenden Fällen kann es zu Timeoutfehlern bei der Wörtertrennung kommen:  
  
-   Die Wörtertrennung für die Abfragesprache ist falsch konfiguriert; z. B. sind die entsprechenden Registrierungseinstellungen falsch.  
  
-   Die Wörtertrennung schlägt bei einer bestimmten Abfragezeichenfolge fehl.  
  
-   Die Wörtertrennung gibt bei einer bestimmten Abfragezeichenfolge zu viele Daten zurück. Diese Daten werden als möglicher Angriff in Form eines Pufferüberlaufs interpretiert, was dafür sorgt, dass der für die Ausführung der Wörtertrennungsdienste verantwortliche Filterdaemonprozess (fdhost.exe) beendet wird.  
  
-   Der Filterdaemonprozess wurde falsch konfiguriert.  
  
     Zu den häufigsten Konfigurationsproblemen gehören abgelaufene Kennwörter oder Domänenrichtlinien, die eine Anmeldung am Filterdaemonkonto verhindern.  
  
-   Auf der Serverinstanz wird eine sehr große Abfragelast ausgeführt, z. B. dauert die Verarbeitung der Volltextabfragezeichenfolge sehr lange, oder es wird eine große Anzahl von Abfragen auf dem Server ausgeführt. Dies ist die wahrscheinliche Ursache.  
  
## <a name="user-action"></a>Benutzeraktion  
 Wählen Sie wie folgt die Benutzeraktion aus, die der wahrscheinlichen Ursache des Timeouts entspricht:  
  
|Wahrscheinliche Ursache|Benutzeraktion|  
|--------------------|-----------------|  
|Die Wörtertrennung ist für die Abfragesprache nicht richtig konfiguriert.|Wenn Sie die Wörtertrennung eines Drittanbieters verwenden, ist sie möglicherweise auf dem Betriebssystem falsch registriert. Registrieren Sie die Wörtertrennung in diesem Fall erneut. Weitere Informationen finden Sie unter [Wiederherstellen der von der Suche verwendeten Wörtertrennungen auf die vorherige Version](../search/revert-the-word-breakers-used-by-search-to-the-previous-version.md).|  
|Die Wörtertrennung schlägt bei einer bestimmten Abfragezeichenfolge fehl.|Wenn die Wörtertrennung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt wird, wenden Sie sich an den Microsoft-Kundenservice und -support.|  
|Die Wörtertrennung gibt bei einer bestimmten Abfragezeichenfolge zu viele Daten zurück.|Wenn die Wörtertrennung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt wird, wenden Sie sich an den Microsoft-Kundenservice und -support.|  
|Der Filterdaemonprozess wurde falsch konfiguriert.|Stellen Sie sicher, dass Sie das aktuelle Kennwort verwenden und dass die Anmeldung unter dem Filterdaemonkonto nicht von einer Domänenrichtlinie verhindert wird.|  
|Auf der Serverinstanz wird eine große Abfragelast ausgeführt.|Führen Sie die Abfrage bei geringerer Auslastung erneut aus.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Festlegen des Dienstkontos für das Startprogramm des Volltextfilterdaemon](../search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md)   
 [Voll Text Suche](../search/full-text-search.md)   
 [sp_help_fulltext_system_components &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql)   
 [Konfigurieren und Verwalten von Wörter Trennungen und Wort Stamm Erkennungen für die Suche](../search/configure-and-manage-word-breakers-and-stemmers-for-search.md)   
 [Konfigurieren und Verwalten von Filtern für die Suche](../search/configure-and-manage-filters-for-search.md)  
  
  
