---
description: Verbindungshandles
title: Verbindungs Handles | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connection handles [ODBC]
- handles [ODBC], connection
ms.assetid: 12222653-f04d-46d6-bdee-61348f5d550f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a4457fa72c40892e208057ac013d3da1e557a6d1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424792"
---
# <a name="connection-handles"></a>Verbindungshandles
Eine *Verbindung* besteht aus einem Treiber und einer Datenquelle. Mit einem Verbindungs Handle wird jede Verbindung identifiziert. Das Verbindungs Handle definiert nicht nur den zu verwendenden Treiber, sondern die Datenquelle, die mit diesem Treiber verwendet werden soll. Innerhalb eines Code Segments, das ODBC (Treiber-Manager oder Treiber) implementiert, identifiziert das Verbindungs Handle eine Struktur, die Verbindungsinformationen enthält, wie z. b. Folgendes:  
  
-   Der Status der Verbindung.  
  
-   Die aktuelle Diagnose auf Verbindungs Ebene  
  
-   Die Handles von Anweisungen und Deskriptoren, die derzeit für die Verbindung zugeordnet sind.  
  
-   Die aktuellen Einstellungen der einzelnen Verbindungs Attribute  
  
 ODBC verhindert nicht mehrere gleichzeitige Verbindungen, wenn Sie vom Treiber unterstützt werden. Daher können mehrere Verbindungs Handles in einer bestimmten ODBC-Umgebung auf eine Vielzahl von Treibern und Datenquellen, auf denselben Treiber und eine Vielzahl von Datenquellen oder sogar auf mehrere Verbindungen mit dem gleichen Treiber und der gleichen Datenquelle verweisen. Einige Treiber begrenzen die Anzahl der aktiven Verbindungen, die Sie unterstützen. die Option SQL_MAX_DRIVER_CONNECTIONS in **SQLGetInfo** gibt an, wie viele aktive Verbindungen von einem bestimmten Treiber unterstützt werden.  
  
 Verbindungs Handles werden hauptsächlich verwendet, wenn eine Verbindung mit der Datenquelle hergestellt wird (**SQLCONNECT**, **SQLDriverConnect**oder **sqlbrowseconnetct**), Trennen der Verbindung mit der Datenquelle (**SQLDisconnect**), Abrufen von Informationen über den Treiber und die Datenquelle (**SQLGetInfo**), Abrufen der Diagnose (**SQLGetDiagField** und **SQLGetDiagRec**) und Durchführen von Transaktionen (**SQLEndTran**). Sie werden auch verwendet, wenn Verbindungs Attribute festgelegt und abgerufen werden (**SQLSetConnectAttr** und **SQLGetConnectAttr**) und wenn das systemeigene Format einer SQL-Anweisung (**SQLNativeSql**) abgerufen wird.  
  
 Verbindungs Handles werden mit **sqlzuordchandle** zugeordnet und mit **SQLFreeHandle**freigegeben.
