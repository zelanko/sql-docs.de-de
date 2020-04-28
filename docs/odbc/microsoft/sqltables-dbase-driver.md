---
title: SQLTables (dBase-Treiber) | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306071"
---
# <a name="sqltables-dbase-driver"></a>SQLTables (dBASE-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu dBASE-Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argument|Kommentare|  
|--------------|--------------|  
|*sztableowner*|Das einzige gültige Argument für *sztableowner* ist NULL, da keiner der Treiber Besitzer Namen unterstützt. Wenn *sztableowner* auf NULL festgelegt ist, werden alle Tabellen zurückgegeben. NULL wird in der TABLE_OWNER Spalte zurückgegeben.|  
|*sztablequalifizierer*|In der Spalte TABLE_QUALIFIER gibt **SQLTables** den Pfad zu einem Verzeichnis zurück.|  
|*Sztabletype*|Für dBASE-Dateien ist "Table" der einzige unterstützte Tabellentyp.|
