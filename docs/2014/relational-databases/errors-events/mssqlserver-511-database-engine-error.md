---
title: MSSQLSERVER_511 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 511 (Database Engine error)
ms.assetid: 0c85686a-53c1-4180-ba8c-2000e68a0d63
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: a7127c975bfd85a4dc41ba930c5f5b8237fa5f1e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151141"
---
# <a name="mssqlserver511"></a>MSSQLSERVER_511
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|511|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|ROW_TOOBIG|  
|Meldungstext|Eine Zeile der Größe %d kann nicht erstellt werden, da sie länger als das zulässige Maximum von %d wäre.|  
  
## <a name="explanation"></a>Erklärung  
 Der Vorgang hat die maximale Größe für eine Zeile überschritten. Die maximale Größe einer Zeile beträgt normalerweise 8060 Bytes. Einige Speicherformate verfügen über Overhead, mit dem die für Daten verfügbare Zeilengröße reduziert werden kann. Wenn Sie z. B. Sparsespalten verwenden, ist die maximale Größe einer Zeile 8018 Bytes. Bei einigen Vorgängen zum Hinzufügen und Entfernen von Zeilen sowie bei einigen Vorgängen, mit denen der Datentyp einer Spalte geändert wird, muss die Zeile erneut auf die Datenseite geschrieben werden. Danach wird die ursprüngliche Zeile entfernt. Bei diesen Vorgängen liegt die wirksame Grenze für die Größe der Zeile bei der Hälfte der maximalen Grenze. Die Ursache hierfür liegt darin, dass sich sowohl die ursprüngliche Zeile als auch die geänderte Zeile kurzfristig gemeinsam auf der Datenseite befinden müssen.  
  
> [!WARNING]  
>  Jede **varchar(max)**- oder **nvarchar(max)**-Spalte, die ungleich NULL ist, erfordert 24 Byte an zusätzlicher fester Verteilung, die während eines Sortiervorgangs hinsichtlich des Zeilenlimits von 8.060 Byte gelten. Dies kann zur Erstellung einer impliziten Beschränkung der Anzahl der **varchar(max)**- oder **nvarchar(max)**-Spalten führen, die ungleich NULL sind und in einer Tabelle erstellt werden können. Beim Erstellen der Tabelle (außerhalb der üblichen Warnung darüber, dass die maximale Zeilengröße das zulässige Maximum von 8.060 Bytes überschreitet) oder zum Zeitpunkt der Dateneinfügung wird kein spezieller Fehler ausgegeben. Diese große Zeilengröße kann während einiger normaler Vorgänge Fehler (z. B. Fehler 512) verursachen. Dazu gehören z. B. die Aktualisierung des gruppierten Indexschlüssels oder Teile des vollständigen Spaltensatzes. Bis zum Ausführen eines Vorgangs können Benutzer diese Fehler nicht vorhersehen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Reduzieren Sie, sofern möglich, die Größe der Zeile.  
  
 Wenn Sie vermuten, dass das Problem aufgrund eines Updates der Zeile entstanden ist, müssen Sie die Tabelle in mehreren Schritten ändern. Erstellen Sie eine neue Tabelle, und übertragen Sie die Daten in die neue Tabelle. Löschen Sie dann die ursprüngliche Tabelle, und benennen Sie die neue Tabelle um, oder schneiden Sie die ursprüngliche Tabelle ab, ändern Sie die Zeilen in der ursprünglichen Tabelle, und fügen Sie die Daten dann wieder ein.  
  
  