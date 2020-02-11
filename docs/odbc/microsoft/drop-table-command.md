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
ms.openlocfilehash: 278950bac7589b8a6b02d894c8133a699c3bd1ef
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68071806"
---
# <a name="drop-table-command"></a>DROP TABLE-Befehl
Entfernt eine Tabelle aus der Datenbank, die mit der Datenquelle angegeben wurde, und löscht sie von der Festplatte.  
  
 Der Visual FoxPro-ODBC-Treiber unterstützt die native Visual FoxPro-Sprachsyntax für diesen Befehl. Treiber spezifische Informationen finden Sie in den hinweisen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DROP TABLE TableName | FileName | ?  
```  
  
## <a name="settings"></a>Einstellungen  
 *TableName*  
 Gibt die Tabelle an, die aus der mit der Datenquelle angegebenen Datenbank entfernt und von der Festplatte gelöscht werden soll.  
  
 *Einfügen*  
 Gibt eine freie Tabelle an, die vom Datenträger gelöscht werden soll.  
  
 ?  
 Zeigt das Dialogfeld "entfernen" an, in dem Sie eine Tabelle auswählen können, die aus der mit der Datenquelle angegebenen Datenbank entfernt und vom Datenträger gelöscht werden soll.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn DROP TABLE ausgegeben wird, werden alle primären Indizes, Standardwerte und Validierungsregeln, die der Tabelle zugeordnet sind, ebenfalls entfernt. DROP TABLE wirkt sich auch auf andere Tabellen in der Datenbank aus, die mit der Datenquelle angegeben sind, wenn diese Tabellen über Regeln oder Beziehungen verfügen, die der zu entfernende Tabelle zugeordnet Die Regeln und Beziehungen sind nicht mehr gültig, wenn die Tabelle aus der Datenbank entfernt wird.  
  
## <a name="driver-remarks"></a>Hinweise zu Treibern  
 Wenn die Anwendung die DROP TABLE-Anweisung der ODBC-SQL-Anweisung an die Datenquelle sendet, konvertiert der Visual FoxPro-ODBC-Treiber den Befehl mithilfe der in der folgenden Tabelle gezeigten Syntax in den Visual foxprodrop TABLE-Befehl.  
  
|ODBC-Syntax|Datenquelle|Syntax von Visual FoxPro|  
|-----------------|-----------------|--------------------------|  
|Drop Table *Basis-Tabellenname*|Datenbank (DBC-Datei)|Tabelle mit *TableName* löschen entfernen|  
||Verzeichnis mit freien Tabellen (DBF-Dateien)|Löschen von *DBF-Name*<br /><br /> *Cdxname* löschen<br /><br /> *Fptname* löschen|
