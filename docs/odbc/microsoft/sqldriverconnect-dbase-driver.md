---
description: SQLDriverConnect (dBASE-Treiber)
title: SQLDriverConnect (dBase-Treiber) | Microsoft-Dokumentation
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
ms.openlocfilehash: e15925b52c096acb1a1021c1a2f968c0863eacf0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449202"
---
# <a name="sqldriverconnect-dbase-driver"></a>SQLDriverConnect (dBASE-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu dBASE-Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** ermöglicht Ihnen das Herstellen einer Verbindung mit einem Treiber, ohne eine Datenquelle (DSN) zu erstellen.  
  
 Die folgenden Schlüsselwörter werden in der Verbindungs Zeichenfolge für alle Treiber unterstützt: **DSN**, **DBQ**und **fil**.  
  
 Wenn der Paradox-Treiber verwendet wird, können andere Benutzer die Datei nicht öffnen, nachdem eine Kenn Wort geschützte Datei von einem Benutzer geöffnet wurde.  
  
 In der folgenden Tabelle sind die minimalen Schlüsselwörter aufgeführt, die zum Herstellen einer Verbindung mit den einzelnen Treibern erforderlich sind, sowie ein Beispiel für Schlüsselwort-Wert-Paare, die mit **SQLDriverConnect** Eine vollständige Liste der DriverID-Werte finden Sie unter [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).  
  
> [!NOTE]  
>  Wenn DBQ oder DefaultDir für dbasedriver nicht angegeben wird, stellt der Treiber eine Verbindung mit dem aktuellen Verzeichnis her.  
  
|Treiber|Schlüsselwörter erforderlich|Beispiele|  
|------------|-----------------------|--------------|  
|dBASE|Treiber, DriverID|Treiber = {Microsoft dBase-Treiber (*. dbf)}; Dbq = c:\temp; DriverID = 277|
