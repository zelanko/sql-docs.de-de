---
title: SQLDriverConnect (Excel-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLDriverConnect
- SQLDriverConnect function [ODBC], Excel Driver
ms.assetid: 285cb1ea-f461-4596-97f2-fc57af05dede
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b2d7e879c35e7cbf2f2b261d94eff22936f7880b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63238095"
---
# <a name="sqldriverconnect-excel-driver"></a>SQLDriverConnect (Excel-Treiber)
> [!NOTE]  
>  Dieses Thema enthält die Excel-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** können Sie auf einen Treiber zu verbinden, ohne das Erstellen einer Datenquelle (DSN).  
  
 Die folgenden Schlüsselwörter werden in der Verbindungszeichenfolge für alle Treiber unterstützt: **DSN**, **DBQ**, und **FIL**.  
  
 Die folgende Tabelle zeigt die minimale Schlüsselwörter, die für die Verbindung mit jeder Treiber und enthält ein Beispiel der Schlüsselwort-Wert-Paare, die mit verwendet **SQLDriverConnect**. Eine vollständige Liste der Werte von DRIVERID, finden Sie unter [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).  
  
> [!NOTE]  
>  Wenn es sich bei DBQ oder Wert nicht für die Microsoft Excel 3.0 oder 4.0-Treibers angegeben ist, werden die Treiber in das aktuelle Verzeichnis verbunden.  
  
|Treiber|Schlüsselwörter, die erforderlich sind|Beispiele|  
|------------|-----------------------|--------------|  
|Microsoft Excel 3.0 oder 4.0|Driver, DriverID|Driver = {Microsoft Excel-Treiber (*.xls)}; DBQ = "c:\Temp"; DriverID 278 =|  
|Microsoft Excel 5.0/7.0|Driver, DriverID,  DBQ|Driver = {Microsoft Excel-Treiber (*.xls)}; DBQ=c:\temp\sample.xls; DriverID = 22|  
|Microsoft Excel 97 und höher|Driver, DriverID,  DBQ|Driver = {Microsoft Excel-Treiber (*.xls)}; DBQ=c:\temp\sample.xls; DriverID 790 =|
