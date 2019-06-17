---
title: SQLTables (dBASE-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBase driver [ODBC], SQLTables
- SQLTables function [ODBC], dBASE Driver
ms.assetid: 45938efb-b678-47d8-9345-644fa26ad679
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 63e42091ed0e1763cb24eef5e6a32f551b29ad5f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62686776"
---
# <a name="sqltables-dbase-driver"></a>SQLTables (dBASE-Treiber)
> [!NOTE]  
>  Dieses Thema enthält die dBASE-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argument|Kommentare|  
|--------------|--------------|  
|*szTableOwner*|Das einzige gültige Argument für *SzTableOwner* NULL ist, da der Treiber keine Besitzernamens unterstützt. Mit *SzTableOwner* auf NULL festgelegt, werden alle Tabellen zurückgegeben. In der Spalte TABLE_OWNER wird NULL zurückgegeben.|  
|*szTableQualifier*|In der Spalte TABLE_QUALIFIER **SQLTables** gibt den Pfad zu einem Verzeichnis zurück.|  
|*SzTableType*|DBASE-Dateien ist "TABLE" der einzige unterstützte Tabellentyp.|
