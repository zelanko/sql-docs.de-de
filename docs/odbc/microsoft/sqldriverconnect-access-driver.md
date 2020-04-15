---
title: SQLDriverConnect (Zugriffstreiber) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLDriverConnect
- SQLDriverConnect function [ODBC], Access Driver
ms.assetid: 9d133e9b-7545-464d-aa3c-677fa7e2a41d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7a679cbb16ece3f239b1d17daabc8a294b808287
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302911"
---
# <a name="sqldriverconnect-access-driver"></a>SQLDriverConnect (Access-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Access Driver-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **Mit SQLDriverConnect** können Sie eine Verbindung zu einem Treiber herstellen, ohne eine Datenquelle (DSN) zu erstellen.  
  
 Die folgenden Schlüsselwörter werden in der Verbindungszeichenfolge für alle Treiber unterstützt: **DSN**, **DBQ**und **FIL**.  
  
 Die **Schlüsselwörter UID** und **PWD** werden ebenfalls unterstützt.  
  
 Das PWD-Schlüsselwort sollte keines der Sonderzeichen enthalten (siehe SQL_SPECIAL_CHARACTERS in **SQLGetInfo** Returned Values).  
  
 Die folgende Tabelle zeigt die minimalen Schlüsselwörter, die zum Herstellen einer Verbindung mit jedem Treiber erforderlich sind, und enthält ein Beispiel für Schlüsselwort-Wert-Paare, die mit **SQLDriverConnect**verwendet werden. Eine vollständige Liste der DRIVERID-Werte finden Sie unter [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).  
  
|Treiber|Schlüsselwörter erforderlich|Beispiele|  
|------------|-----------------------|--------------|  
|Microsoft Access|Treiber, DBQ|Driver= Microsoft Access Driver (*.mdb) ; DBQ=c:\\.mdb\\|
