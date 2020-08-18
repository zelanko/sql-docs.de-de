---
description: SQLDriverConnect (Excel-Treiber)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6320033d83e9b46c3567b3bf0b845144dbe9250e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449192"
---
# <a name="sqldriverconnect-excel-driver"></a>SQLDriverConnect (Excel-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu Excel-Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** ermöglicht Ihnen das Herstellen einer Verbindung mit einem Treiber, ohne eine Datenquelle (DSN) zu erstellen.  
  
 Die folgenden Schlüsselwörter werden in der Verbindungs Zeichenfolge für alle Treiber unterstützt: **DSN**, **DBQ**und **fil**.  
  
 In der folgenden Tabelle sind die minimalen Schlüsselwörter aufgeführt, die zum Herstellen einer Verbindung mit den einzelnen Treibern erforderlich sind, sowie ein Beispiel für Schlüsselwort-Wert-Paare, die mit **SQLDriverConnect** Eine vollständige Liste der DriverID-Werte finden Sie unter [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).  
  
> [!NOTE]  
>  Wenn DBQ oder DefaultDir für den Microsoft Excel 3,0-oder 4,0-Treiber nicht angegeben wird, stellt der Treiber eine Verbindung mit dem aktuellen Verzeichnis her.  
  
|Treiber|Schlüsselwörter erforderlich|Beispiele|  
|------------|-----------------------|--------------|  
|Microsoft Excel 3,0 oder 4,0|Treiber, DriverID|Driver = {Microsoft Excel Driver (*. xls)}; Dbq = c:\temp; DriverID = 278|  
|Microsoft Excel 5.0/7.0|Driver, DriverID, DBQ|Driver = {Microsoft Excel Driver (*. xls)}; DBQ =c:\temp\sample.xls; DriverID = 22|  
|Microsoft Excel 97 und höher|Driver, DriverID, DBQ|Driver = {Microsoft Excel Driver (*. xls)}; DBQ =c:\temp\sample.xls; DriverID = 790|
