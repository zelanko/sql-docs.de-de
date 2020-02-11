---
title: SQLTables (Zugriffs Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLTables function [ODBC], Access Driver
- Access driver [ODBC], SQLTables
ms.assetid: 94423cf9-341a-4db6-bb10-8f5448df7fc3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e23e6993f66dd706a800ae2b34a9fdc0d219898d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68132459"
---
# <a name="sqltables-access-driver"></a>SQLTables (Access-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu Zugriffs Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argument|Kommentare|  
|--------------|--------------|  
|*sztableowner*|Das einzige gültige Argument für *sztableowner* ist NULL, da keiner der Treiber Besitzer Namen unterstützt. Wenn *sztableowner* auf NULL festgelegt ist, werden alle Tabellen zurückgegeben. NULL wird in der TABLE_OWNER Spalte zurückgegeben.|  
|*sztablequalifizierer*|In der Spalte TABLE_QUALIFIER gibt **SQLTables** den Pfad zu einer Datenbankdatei zurück.|  
|*Sztabletype*|Wenn der Microsoft Access-Treiber verwendet wird, wird "System Tabelle" für " *sztabletype* " für System Tabellen unterstützt, "Synonym" wird für angefügte Tabellen unterstützt, und "View" wird für Abfragen mit Zeilen Rückgabe unterstützt.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLTables-Funktion](../../odbc/reference/syntax/sqltables-function.md)
