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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68053981"
---
# <a name="sqldriverconnect-access-driver"></a>SQLDriverConnect (Access-Treiber)
> [!NOTE]  
>  Dieses Thema enthält die Access-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** können Sie auf einen Treiber zu verbinden, ohne das Erstellen einer Datenquelle (DSN).  
  
 Die folgenden Schlüsselwörter werden in der Verbindungszeichenfolge für alle Treiber unterstützt: **DSN**, **DBQ**, und **FIL**.  
  
 Die **UID** und **PWD** Schlüsselwörter werden ebenfalls unterstützt.  
  
 Das PWD-Schlüsselwort muss die Sonderzeichen nicht enthalten (Siehe SQL_SPECIAL_CHARACTERS in **SQLGetInfo** zurückgegebenen Werte).  
  
 Die folgende Tabelle zeigt die minimale Schlüsselwörter, die für die Verbindung mit jeder Treiber und enthält ein Beispiel der Schlüsselwort-Wert-Paare, die mit verwendet **SQLDriverConnect**. Eine vollständige Liste der Werte von DRIVERID, finden Sie unter [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).  
  
|Treiber|Schlüsselwörter, die erforderlich sind|Beispiele|  
|------------|-----------------------|--------------|  
|Microsoft Access|DBQ-Treiber|Driver = {Microsoft Access-Treiber (*.mdb)}; DBQ = c:\\\temp\\\sample.mdb|
