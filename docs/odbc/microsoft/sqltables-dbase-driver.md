---
title: SQLTables (dBASE-Treiber) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 242be06eafc7657f37f55ce266af471cbc72597f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306071"
---
# <a name="sqltables-dbase-driver"></a>SQLTables (dBASE-Treiber)
> [!NOTE]  
>  Dieses Thema enthält dBASE-Treiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argument|Kommentare|  
|--------------|--------------|  
|*szTableOwner*|Das einzige gültige Argument für *szTableOwner* ist NULL, da keine der Treiber Besitzernamen unterstützt. Wenn *szTableOwner* auf NULL gesetzt ist, werden alle Tabellen zurückgegeben. NULL wird in der Spalte TABLE_OWNER zurückgegeben.|  
|*szTableQualifier*|In der Spalte TABLE_QUALIFIER gibt **SQLTables** den Pfad in ein Verzeichnis zurück.|  
|*SzTableType*|Bei dBASE-Dateien ist "TABLE" der einzige unterstützte Tabellentyp.|
