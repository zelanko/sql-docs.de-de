---
title: MSSQLSERVER_30089 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9992 (Database Engine error)
ms.assetid: 188e5bde-6865-4740-a2b2-582be8f55c77
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9cbf77c21b55542dac80d8d8ce376f0cc3a5e9d4
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551809"
---
# <a name="mssqlserver_30089"></a>MSSQLSERVER_30089
    
## <a name="details"></a>Details  
  
|attribute|Wert|  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|30089|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|IFTS_FDHOST_TERMINATEDABNORMAL|  
|Meldungstext|Der Hostprozess des Volltextfilterdaemons (FDHost) wurde fehlerbedingt beendet. Dieser Fehler kann auftreten, wenn eine falsch konfigurierte oder nicht ordnungsgemäß funktionierende linguistische Komponente, wie z. B. eine Wörtertrennung, eine Wortstammerkennung oder ein Filter, bei der Volltextindizierung oder Abfrageverarbeitung einen nicht behebbaren Fehler verursacht hat. Der Prozess wird automatisch neu gestartet.|  
  
## <a name="explanation"></a>Erklärung  
 Der Host des Volltextfilterdaemons hat ein Problem erkannt, wodurch der Prozess fehlerbedingt beendet wurde. Die Ursache des Problems kann ein falsch formatiertes Dokument, ein Fehler im Filter oder in der Wörtertrennung oder ein Fehler im Filterdaemon sein.  
  
## <a name="user-action"></a>Benutzeraktion  
 Normalerweise wird der Daemon wiederhergestellt. Wenn der Fehler weiterhin auftritt, ist eine Problembehandlung erforderlich. Versuchen Sie Folgendes, um das Problem zu isolieren:  
  
1.  Wenn kürzlich eine neue linguistische Komponente installiert wurde, entfernen Sie diese vom System.  
  
2.  Suchen Sie im Durchforstungsprotokoll nach neuen Dokumenten, bei deren Volltextindizierung ein Fehler aufgetreten ist, und entfernen Sie diese Dokumente.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_help_fulltext_system_components &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql)   
 [Konfigurieren und Verwalten von Wörter Trennungen und Wort Stamm Erkennungen für die Suche](../search/configure-and-manage-word-breakers-and-stemmers-for-search.md)   
 [Konfigurieren und Verwalten von Filtern für die Suche](../search/configure-and-manage-filters-for-search.md)  
  
  
