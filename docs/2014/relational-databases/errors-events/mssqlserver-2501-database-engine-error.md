---
title: MSSQLSERVER_2501 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2501 (Database Engine error)
ms.assetid: 895aafe3-a4e7-4ed8-acc5-93be76ef3664
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9d4920be6af560cbd5bd1d7699dd6378cdc2db3b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62914850"
---
# <a name="mssqlserver2501"></a>MSSQLSERVER_2501
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|2501|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC_NO_SUCH_TABLE_NAME|  
|Meldungstext|Eine Tabelle oder ein Objekt mit dem Namen 'NAME' wurde nicht gefunden. Überprüfen Sie den Systemkatalog.|  
  
## <a name="explanation"></a>Erklärung  
 Das angegebene Objekt wurde nicht gefunden.  
  
### <a name="possible-causes"></a>Mögliche Ursachen  
 Dieser Fehler kann durch eines der folgenden Probleme verursacht werden:  
  
-   Das Objekt ist nicht richtig angegeben.  
  
-   Das Objekt ist nicht vorhanden, oder das Objekt wurde entfernt, bevor von einer Anweisung versucht wurde, es zu verwenden.  
  
-   Das Objekt ist möglicherweise vorhanden, es konnte jedoch nicht für den Benutzer verfügbar gemacht werden. Beispielsweise besitzt der Benutzer möglicherweise keine Berechtigungen für das Objekt, oder das Objekt stellt eine interne Tabelle dar, die von einem Benutzer nicht angezeigt werden konnte.  
  
## <a name="user-action"></a>Benutzeraktion  
  
-   Überprüfen Sie, ob der aktuelle Datenbankkontext richtig ist. Weitere Informationen finden Sie unter [USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql).  
  
-   Überprüfen Sie, ob der Tabellen- oder Objektname richtig geschrieben wurde.  
  
-   Überprüfen Sie den Namen des Schemas, das das Objekt enthält. Wenn das Objekt zu einem anderen Schema als dem Standardschema (**dbo**) gehört, müssen Sie den Tabellen- bzw. Objektnamen im zweiteiligen Format *schema_name.object_name* angeben.  
  
-   Stellen Sie sicher, dass das Objekt in den Systemtabellen vorhanden ist. Wenn Sie überprüfen möchten, ob eine Tabelle oder ein anderes schemabezogenes Objekt vorhanden ist, fragen Sie die [sys.objects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql)-Katalogsicht ab. Wenn das Objekt in den Systemtabellen nicht vorhanden ist, wurde das Objekt gelöscht, oder der Benutzer besitzt keine Berechtigungen zum Anzeigen der Objektmetadaten. Weitere Informationen zu Berechtigungen zum Anzeigen von Objektmetadaten finden Sie unter [Konfiguration der Sichtbarkeit von Metadaten](../security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql)  
  
  
