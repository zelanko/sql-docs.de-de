---
title: SQLDriverConnect (Access-Treiber) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e211797147c4da8f197247244f6f2805185b3b0b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68053981"
---
# <a name="sqldriverconnect-access-driver"></a>SQLDriverConnect (Access-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu Zugriffs Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** ermöglicht Ihnen das Herstellen einer Verbindung mit einem Treiber, ohne eine Datenquelle (DSN) zu erstellen.  
  
 Die folgenden Schlüsselwörter werden in der Verbindungs Zeichenfolge für alle Treiber unterstützt: **DSN**, **DBQ**und **fil**.  
  
 Die Schlüsselwörter **UID** und **pwd** werden ebenfalls unterstützt.  
  
 Das pwd-Schlüsselwort darf keines der Sonderzeichen enthalten (siehe SQL_SPECIAL_CHARACTERS in den von **SQLGetInfo** zurückgegebenen Werten).  
  
 In der folgenden Tabelle sind die minimalen Schlüsselwörter aufgeführt, die zum Herstellen einer Verbindung mit den einzelnen Treibern erforderlich sind, sowie ein Beispiel für Schlüsselwort-Wert-Paare, die mit **SQLDriverConnect** Eine vollständige Liste der DriverID-Werte finden Sie unter [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).  
  
|Treiber|Schlüsselwörter erforderlich|Beispiele|  
|------------|-----------------------|--------------|  
|Microsoft Access|Treiber, DBQ|Driver = {Microsoft Access Driver (*. mdb)}; Dbq = c:\\\temp\\\sample.mdb|
