---
title: SQLDriverConnect (Paradox-Treiber) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e17ca12e0c8745dcad30a3e5ce2c9689b041e7d2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67967487"
---
# <a name="sqldriverconnect-paradox-driver"></a>SQLDriverConnect (Paradox-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu Paradox-Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** ermöglicht Ihnen das Herstellen einer Verbindung mit einem Treiber, ohne eine Datenquelle (DSN) zu erstellen.  
  
 Die folgenden Schlüsselwörter werden in der Verbindungs Zeichenfolge für alle Treiber unterstützt: **DSN**, **DBQ**und **fil**.  
  
 Das **pwd** -Schlüsselwort wird ebenfalls unterstützt. Das pwd-Schlüsselwort darf keines der Sonderzeichen enthalten (siehe SQL_SPECIAL_CHARACTERS in den von **SQLGetInfo** zurückgegebenen Werten).  
  
 Wenn ein Benutzer eine Kenn Wort geschützte Datei geöffnet hat, können andere Benutzer die Datei nicht öffnen.  
  
 In der folgenden Tabelle sind die minimalen Schlüsselwörter aufgeführt, die zum Herstellen einer Verbindung mit den einzelnen Treibern erforderlich sind, sowie ein Beispiel für Schlüsselwort-Wert-Paare, die mit **SQLDriverConnect** Eine vollständige Liste der DriverID-Werte finden Sie unter [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).  
  
> [!NOTE]  
>  Wenn DBQ oder DefaultDir für den Paradox-Treiber nicht angegeben ist, stellt der Treiber eine Verbindung mit dem aktuellen Verzeichnis her.  
  
|Treiber|Schlüsselwörter erforderlich|Beispiel|  
|------------|-----------------------|-------------|  
|Gewissen|Treiber, DriverID|Driver = {Microsoft Paradox Driver (*. DB)}; Dbq = c:\temp; DriverID = 26|
