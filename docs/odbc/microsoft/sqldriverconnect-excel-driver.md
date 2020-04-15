---
title: SQLDriverConnect (Excel-Treiber) | Microsoft Docs
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
ms.openlocfilehash: 1108206bf38183887540b114fda5a1e913aa67d9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307121"
---
# <a name="sqldriverconnect-excel-driver"></a>SQLDriverConnect (Excel-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Excel-Treiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **Mit SQLDriverConnect** können Sie eine Verbindung zu einem Treiber herstellen, ohne eine Datenquelle (DSN) zu erstellen.  
  
 Die folgenden Schlüsselwörter werden in der Verbindungszeichenfolge für alle Treiber unterstützt: **DSN**, **DBQ**und **FIL**.  
  
 Die folgende Tabelle zeigt die minimalen Schlüsselwörter, die zum Herstellen einer Verbindung mit jedem Treiber erforderlich sind, und enthält ein Beispiel für Schlüsselwort-Wert-Paare, die mit **SQLDriverConnect**verwendet werden. Eine vollständige Liste der DRIVERID-Werte finden Sie unter [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).  
  
> [!NOTE]  
>  Wenn DBQ oder DefaultDir nicht für den Treiber Microsoft Excel 3.0 oder 4.0 angegeben ist, stellt der Treiber eine Verbindung mit dem aktuellen Verzeichnis her.  
  
|Treiber|Schlüsselwörter erforderlich|Beispiele|  
|------------|-----------------------|--------------|  
|Microsoft Excel 3.0 oder 4.0|Treiber, DriverID|Driver= ,Microsoft Excel-Treiber (*.xls); DBQ=c:-temp; DriverID=278|  
|Microsoft Excel 5.0/7.0|Treiber, DriverID, DBQ|Driver= ,Microsoft Excel-Treiber (*.xls); DBQ=c:-temp-Beispiel.xls; DriverID=22|  
|Microsoft Excel 97 und höher|Treiber, DriverID, DBQ|Driver= ,Microsoft Excel-Treiber (*.xls); DBQ=c:-temp-Beispiel.xls; DriverID=790|
