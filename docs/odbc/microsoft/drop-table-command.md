---
title: DROP TABLE-Befehl | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- drop table command [ODBC]
ms.assetid: bc50459b-8861-4889-84a9-129ae9065aa8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0865502928e98329764ae6085ab2b67aa26f0517
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63128037"
---
# <a name="drop-table-command"></a>DROP TABLE-Befehl
Entfernt eine Tabelle aus der Datenbank, mit der Datenquelle angegeben, und vom Datenträger gelöscht.  
  
 Der Visual FoxPro-ODBC-Treiber unterstützt die systemeigene Visual FoxPro-Sprachsyntax für diesen Befehl. Treiberspezifische Informationen finden Sie in den Hinweisen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DROP TABLE TableName | FileName | ?  
```  
  
## <a name="settings"></a>Einstellungen  
 *TableName*  
 Gibt die Tabelle aus der Datenbank mit der Datenquelle zu entfernen und vom Datenträger zu löschen.  
  
 *FileName*  
 Gibt eine kostenlose Tabelle vom Datenträger zu löschen.  
  
 ?  
 Zeigt das Dialogfeld "entfernen" in dem Sie eine Tabelle aus der Datenbank mit der Datenquelle zu entfernen und vom Datenträger löschen auswählen können.  
  
## <a name="remarks"></a>Hinweise  
 Wenn DROP TABLE ausgegeben wird, werden alle primären Indizes, Standardwerte und Regeln zur Überprüfung der Tabelle zugeordneten ebenfalls entfernt. DROP TABLE wirkt sich auch auf andere Tabellen in der Datenbank, die mit der Datenquelle angegeben werden, wenn diese Tabellen Regeln haben oder die Beziehungen der Tabelle entfernt wird. Die Regeln und Beziehungen sind nicht mehr gültig, wenn die Tabelle aus der Datenbank entfernt wird.  
  
## <a name="driver-remarks"></a>Treiber "Hinweise".  
 Wenn Ihre Anwendung die ODBC-SQL-Anweisung DROP TABLE an die Datenquelle sendet, konvertiert der Visual FoxPro-ODBC-Treiber den Befehl in der Visual FoxProDROP TABLE-Befehl mit der Syntax in der folgenden Tabelle gezeigt.  
  
|ODBC-syntax|Datenquelle|Visual FoxPro-syntax|  
|-----------------|-----------------|--------------------------|  
|DROP TABLE *Basis-Table-Name*|Datenbank (DBC-Datei)|REMOVE-Tabelle *TableName* löschen|  
||Verzeichnis des kostenlosen Tabellen (DBF-Dateien)|ERASE *dbfName*<br /><br /> ERASE *cdxName*<br /><br /> ERASE *fptName*|
