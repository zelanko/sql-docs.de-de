---
title: SQLTables (Paradox-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Paradox driver [ODBC], SQLTables
- SQLTables function [ODBC], Paradox Driver
ms.assetid: d68adad6-97bd-4b47-bcf9-0102aafb00d4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c845bd2e5e3ec5e52cfd6d1c0891f8825af1e148
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62735197"
---
# <a name="sqltables-paradox-driver"></a>SQLTables (Paradox-Treiber)
> [!NOTE]  
>  Dieses Thema enthält die Paradox-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argument|Kommentare|  
|--------------|--------------|  
|*szTableOwner*|Das einzige gültige Argument für *SzTableOwner* ist NULL, weil keine Treiber Besitzernamens unterstützt. Mit *SzTableOwner* auf NULL festgelegt, werden alle Tabellen zurückgegeben. In der Spalte TABLE_OWNER wird NULL zurückgegeben.|  
|*szTableQualifier*|In der Spalte TABLE_QUALIFIER **SQLTables** gibt den Pfad zu einem Verzeichnis zurück.|  
|*SzTableType*|Für Dateien, Paradox ist "TABLE" der einzige unterstützte Tabellentyp.|  
  
## <a name="see-also"></a>Siehe auch  
 [SQLTables-Funktion](../../odbc/reference/syntax/sqltables-function.md)
