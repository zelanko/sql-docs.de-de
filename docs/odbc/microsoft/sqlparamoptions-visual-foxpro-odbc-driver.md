---
description: SQLParamOptions (Visual FoxPro-ODBC-Treiber)
title: SQLParamOptions (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLParamOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 7f94a6e2-9c34-405c-b2b0-304d94269715
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e40af7f0bb03c0b5245717880e67e72b38559aed
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500193"
---
# <a name="sqlparamoptions-visual-foxpro-odbc-driver"></a>SQLParamOptions (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Unterstützung: vollständig  
  
 ODBC-API-Konformität: Ebene 1  
  
 Ermöglicht es einer Anwendung, mehrere Werte für den Satz von Parametern anzugeben, der von [SQLBindParameter](../../odbc/microsoft/sqlbindparameter-visual-foxpro-odbc-driver.md)zugewiesen wird. Die Möglichkeit, mehrere Werte für einen Satz von Parametern anzugeben, eignet sich für Massen Einfügungen und andere Aufgaben, bei denen die Datenquelle die gleiche SQL-Anweisung mehrmals mit verschiedenen Parameterwerten verarbeiten muss. Eine Anwendung kann z. b. drei Sätze von Werten für den Satz von Parametern angeben, die einer **Insert** -Anweisung zugeordnet sind, und dann die **Insert** -Anweisung einmal ausführen, um die drei Einfügevorgänge auszuführen.  
  
 Weitere Informationen finden Sie unter [SQLParamOptions](../../odbc/reference/syntax/sqlparamoptions-function.md) in der *ODBC Programmer es Reference*.
