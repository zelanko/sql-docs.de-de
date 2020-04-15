---
title: SQLDriverConnect (Paradox-Treiber) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLDriverConnect function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLDriverConnect
ms.assetid: c2ba486e-5e01-4e67-adb1-68511f5f0206
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 68171cfab2b65634433b107d829dd2a6e9b5c985
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307111"
---
# <a name="sqldriverconnect-paradox-driver"></a>SQLDriverConnect (Paradox-Treiber)
> [!NOTE]  
>  Dieses Thema enthält paradox driverspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **Mit SQLDriverConnect** können Sie eine Verbindung zu einem Treiber herstellen, ohne eine Datenquelle (DSN) zu erstellen.  
  
 Die folgenden Schlüsselwörter werden in der Verbindungszeichenfolge für alle Treiber unterstützt: **DSN**, **DBQ**und **FIL**.  
  
 Das **Schlüsselwort PWD** wird ebenfalls unterstützt. Das PWD-Schlüsselwort sollte keines der Sonderzeichen enthalten (siehe SQL_SPECIAL_CHARACTERS in **SQLGetInfo** Returned Values).  
  
 Nachdem eine kennwortgeschützte Datei von einem Benutzer geöffnet wurde, dürfen andere Benutzer dieselbe Datei nicht öffnen.  
  
 Die folgende Tabelle zeigt die minimalen Schlüsselwörter, die zum Herstellen einer Verbindung mit jedem Treiber erforderlich sind, und enthält ein Beispiel für Schlüsselwort-Wert-Paare, die mit **SQLDriverConnect**verwendet werden. Eine vollständige Liste der DRIVERID-Werte finden Sie unter [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).  
  
> [!NOTE]  
>  Wenn DBQ oder DefaultDir nicht für den Paradox-Treiber angegeben ist, stellt der Treiber eine Verbindung mit dem aktuellen Verzeichnis her.  
  
|Treiber|Schlüsselwörter erforderlich|Beispiel|  
|------------|-----------------------|-------------|  
|Paradox|Treiber, DriverID|Driver = Microsoft Paradox Driver (*.db ); DBQ=c:-temp;DriverID=26|
