---
title: BEFEHL DROP TABLE | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 779c519f720027aea3a6f6cf2587d3c6e0b59b52
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303421"
---
# <a name="drop-table-command"></a>DROP TABLE-Befehl
Entfernt eine Tabelle aus der mit der Datenquelle angegebenen Datenbank und löscht sie vom Datenträger.  
  
 Der Visual FoxPro ODBC-Treiber unterstützt die native Visual FoxPro-Sprachsyntax für diesen Befehl. Treiberspezifische Informationen finden Sie in den Anmerkungen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DROP TABLE TableName | FileName | ?  
```  
  
## <a name="settings"></a>Einstellungen  
 *TableName*  
 Gibt die Tabelle an, die aus der mit der Datenquelle angegebenen Datenbank entfernt und vom Datenträger gelöscht werden soll.  
  
 *Dateiname*  
 Gibt eine freie Tabelle an, die vom Datenträger gelöscht werden soll.  
  
 ?  
 Zeigt das Dialogfeld Entfernen an, aus dem Sie eine Tabelle auswählen können, die aus der mit der Datenquelle angegebenen Datenbank entfernt und vom Datenträger gelöscht werden soll.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn DROP TABLE ausgegeben wird, werden alle primären Indizes, Standardwerte und Validierungsregeln, die der Tabelle zugeordnet sind, ebenfalls entfernt. DROP TABLE wirkt sich auch auf andere Tabellen in der Datenbank aus, die mit der Datenquelle angegeben sind, wenn diese Tabellen Regeln oder Beziehungen haben, die der entfernten Tabelle zugeordnet sind. Die Regeln und Beziehungen sind nicht mehr gültig, wenn die Tabelle aus der Datenbank entfernt wird.  
  
## <a name="driver-remarks"></a>Driver-Bemerkungen  
 Wenn Ihre Anwendung die ODBC SQL-Anweisung DROP TABLE an die Datenquelle sendet, konvertiert der Visual FoxPro ODBC-Treiber den Befehl mithilfe der in der folgenden Tabelle gezeigten Syntax in den Befehl Visual FoxProDROP TABLE.  
  
|ODBC-Syntax|Datenquelle|Visuelle FoxPro-Syntax|  
|-----------------|-----------------|--------------------------|  
|DROP TABLE *Basistabellenname*|Datenbank (.dbc-Datei)|REMOVE TABLE *TableName* DELETE|  
||Verzeichnis der freien Tabellen (.dbf-Dateien)|ERASE *dbfName*<br /><br /> ERASE *cdxName*<br /><br /> ERASE *fptName*|
