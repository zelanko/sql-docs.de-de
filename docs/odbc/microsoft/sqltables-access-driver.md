---
title: SQLTables (Access-Treiber) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 9931d3d02ff2d0afe69f410d94474c16f235b94e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62686823"
---
# <a name="sqltables-access-driver"></a>SQLTables (Access-Treiber)
> [!NOTE]  
>  Dieses Thema enthält die Access-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argument|Kommentare|  
|--------------|--------------|  
|*szTableOwner*|Das einzige gültige Argument für *SzTableOwner* ist NULL, weil keine Treiber Besitzernamens unterstützt. Mit *SzTableOwner* auf NULL festgelegt, werden alle Tabellen zurückgegeben. In der Spalte TABLE_OWNER wird NULL zurückgegeben.|  
|*szTableQualifier*|In der Spalte TABLE_QUALIFIER **SQLTables** gibt den Pfad zu einer Datenbankdatei zurück.|  
|*SzTableType*|Wenn die Microsoft Access-Treiber verwendet wird, wird für "SYSTEM-TABLE" unterstützt *SzTableType* für Systemtabellen, "Synonyms" wird für angefügte Tabellen unterstützt, und "VIEW" wird zum Zurückgeben von Zeilen unterstützt Abfragen.|  
  
## <a name="see-also"></a>Siehe auch  
 [SQLTables-Funktion](../../odbc/reference/syntax/sqltables-function.md)
