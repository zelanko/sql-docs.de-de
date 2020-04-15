---
title: SQLTables (Zugriffstreiber) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: df3a23af365efbef6a0f0da2c52568501425ecb3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306091"
---
# <a name="sqltables-access-driver"></a>SQLTables (Access-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Access Driver-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argument|Kommentare|  
|--------------|--------------|  
|*szTableOwner*|Das einzige gültige Argument für *szTableOwner* ist NULL, da keine der Treiber Besitzernamen unterstützt. Wenn *szTableOwner* auf NULL gesetzt ist, werden alle Tabellen zurückgegeben. NULL wird in der Spalte TABLE_OWNER zurückgegeben.|  
|*szTableQualifier*|In der Spalte TABLE_QUALIFIER gibt **SQLTables** den Pfad zu einer Datenbankdatei zurück.|  
|*SzTableType*|Wenn der Microsoft Access-Treiber verwendet wird, wird "SYSTEM TABLE" für *szTableType* für Systemtabellen unterstützt, "SYNONYM" wird für angefügte Tabellen und "VIEW" für zeilenzurückkehrende Abfragen unterstützt.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLTables-Funktion](../../odbc/reference/syntax/sqltables-function.md)
