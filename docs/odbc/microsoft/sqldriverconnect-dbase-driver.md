---
title: SQLDriverConnect (dBASE-Treiber) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBase driver [ODBC], SQLDriverConnect
- SQLDriverConnect function [ODBC], dBASE Driver
ms.assetid: c837aa31-068e-4fa3-bc00-aae09bec21de
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 39d3d062ef8371ce37f812216cbb642d103eff98
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302921"
---
# <a name="sqldriverconnect-dbase-driver"></a>SQLDriverConnect (dBASE-Treiber)
> [!NOTE]  
>  Dieses Thema enthält dBASE-Treiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **Mit SQLDriverConnect** können Sie eine Verbindung zu einem Treiber herstellen, ohne eine Datenquelle (DSN) zu erstellen.  
  
 Die folgenden Schlüsselwörter werden in der Verbindungszeichenfolge für alle Treiber unterstützt: **DSN**, **DBQ**und **FIL**.  
  
 Wenn der Paradox-Treiber verwendet wird, nachdem eine kennwortgeschützte Datei von einem Benutzer geöffnet wurde, dürfen andere Benutzer dieselbe Datei nicht öffnen.  
  
 Die folgende Tabelle zeigt die minimalen Schlüsselwörter, die zum Herstellen einer Verbindung mit jedem Treiber erforderlich sind, und enthält ein Beispiel für Schlüsselwort-Wert-Paare, die mit **SQLDriverConnect**verwendet werden. Eine vollständige Liste der DRIVERID-Werte finden Sie unter [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).  
  
> [!NOTE]  
>  Wenn DBQ oder DefaultDir für den dBASEdriver nicht angegeben ist, stellt der Treiber eine Verbindung mit dem aktuellen Verzeichnis her.  
  
|Treiber|Schlüsselwörter erforderlich|Beispiele|  
|------------|-----------------------|--------------|  
|Dbase|Treiber, DriverID|Driver= 'Microsoft dBASE Driver (*.dbf)'; DBQ=c:-temp; TreiberID=277|
