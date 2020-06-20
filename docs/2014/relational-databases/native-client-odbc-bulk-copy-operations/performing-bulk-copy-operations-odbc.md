---
title: Ausführen von Massen Kopier Vorgängen (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC]
- ODBC, bulk copy operations
- minimally logged operations [SQL Server Native Client]
- bulk copy [ODBC], about bulk copy
ms.assetid: 5c793405-487c-4f52-88b8-0091d529afb3
author: rothja
ms.author: jroth
ms.openlocfilehash: 62e7188d61ebdad573d8966ed6e262cc819c4c59
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85021266"
---
# <a name="performing-bulk-copy-operations-odbc"></a>Durchführen von Massenkopiervorgängen (ODBC)
  Der ODBC-Standard unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Massenkopiervorgänge nicht direkt. Wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version 7.0 oder höher verbunden ist, unterstützt er die DB-Library-Funktionen, die die Massenkopiervorgänge in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] durchführen. Diese treiberspezifische Erweiterung stellt eine einfache Möglichkeit dar, bestehende DB-Library-Anwendungen zu aktualisieren, die Funktionen zum Massenkopieren verwenden. Die spezialisierte Unterstützung für Massenkopiervorgänge befindet sich in den folgenden Dateien:  
  
-   sqlncli.h  
  
     Enthält Funktionsprototypen und Konstantendefinitionen für Funktionen zum Massenkopieren. sqlncli.h muss in der ODBC-Anwendung, die Massenkopiervorgänge ausführt, enthalten sein und im Includepfad der Anwendung angegeben werden, wenn die Anwendung kompiliert wird.  
  
-   sqlncli11.lib  
  
     Muss im Bibliothekspfad des Linkers enthalten sein und als zu verknüpfende Datei angegeben werden. sqlncli11.lib wird zusammen mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber bereitgestellt.  
  
-   sqlncli11.dll  
  
     Muss zur Ausführungszeit verfügbar sein. sqlncli11.dll wird mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC-Treiber von Native Client verteilt.  
  
> [!NOTE]  
>  Die ODBC-Funktion **SQLBulkOperations** hat keine Beziehung zu den Funktionen für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Massen Kopiervorgang. Anwendungen müssen die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-spezifischen Massenkopierfunktionen verwenden, um Massenkopiervorgänge durchzuführen.  
  
## <a name="minimally-logging-bulk-copies"></a>Minimales Protokollieren von Massenkopiervorgängen  
 Beim vollständigen Wiederherstellungsmodell werden alle beim Massenladen ausgeführten Vorgänge für das Einfügen von Zeilen vollständig im Transaktionsprotokoll protokolliert. Bei umfangreichen Datenladevorgängen kann dies dazu führen, dass das Transaktionsprotokoll schnell aufgefüllt wird. Unter bestimmten Umständen ist die minimale Protokollierung möglich. Bei der minimalen Protokollierung wird das Risiko verkleinert, dass ein Massenladevorgang das Protokoll auffüllt. Außerdem ist sie effizienter als die vollständige Protokollierung.  
  
 Informationen zur Verwendung der minimalen Protokollierung finden Sie unter [Voraussetzungen für die minimale Protokollierung beim Massen Import](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md).  
  
## <a name="remarks"></a>Hinweise  
 Bei der Verwendung von bcp.exe in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höher erhalten Sie unter Umständen Fehler in Situationen, die in Versionen vor [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] keine Fehler hervorriefen. Das liegt daran, dass bcp.exe in höheren Versionen keine implizite Datentypkonvertierung mehr vornimmt. Vor [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] wurden numerische Daten von bcp.exe in den money-Datentyp konvertiert, wenn die Zieltabelle einen money-Datentyp aufwies. Allerdings wurden in dieser Situation zusätzliche Felder von bcp.exe einfach abgeschnitten. Ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] gibt bcp.exe einen Fehler aus, wenn die Datentypen von Datei und Zieltabelle nicht übereinstimmen, und dadurch Daten abgeschnitten werden müssten, um in die Zieltabelle zu passen. Um diesen Fehler zu beheben, korrigieren Sie die Daten so, dass sie zum Zieldatentyp passen. Optional können Sie die Datei bcp.exe aus einer Version vor [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] verwenden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Verwenden von Datendateien und Formatdateien](using-data-files-and-format-files.md)  
  
-   [Massenkopieren aus Programmvariablen](bulk-copying-from-program-variables.md)  
  
-   [Verwalten von Batchgrößen für das Massenkopieren](managing-bulk-copy-batch-sizes.md)  
  
-   [Massenkopieren von Text- und Bilddaten](bulk-copying-text-and-image-data.md)  
  
-   [Konvertieren von DB-Library-Programmen zum Massenkopieren in ODBC-Programme](converting-from-db-library-to-odbc-bulk-copy.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;ODBC-&#41;](../native-client/odbc/sql-server-native-client-odbc.md)   
 [Massenimport und -export von Daten &#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md)  
  
  
