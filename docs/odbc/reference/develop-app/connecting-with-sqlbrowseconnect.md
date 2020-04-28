---
title: Herstellen einer Verbindung mit sqlbrowseconnetct | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to driver [ODBC], SQLBrowseConnect
- SQLBrowseConnect function [ODBC], connecting
- connecting to data source [ODBC], SQLBrowseConnect
ms.assetid: 6c2e9f76-b766-48df-b109-246bb05ae45d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e4d738d394bb3c507f6aa08f736016b51ac4fefb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81294660"
---
# <a name="connecting-with-sqlbrowseconnect"></a>Herstellen einer Verbindung mit SQLBrowseConnect
**Sqlbrowseconnetct**verwendet, wie **SQLDriverConnect**, eine Verbindungs Zeichenfolge. Mithilfe von **sqlbrowseconnetct**kann eine Anwendung jedoch zur Laufzeit eine vollständige Verbindungs Zeichenfolge erstellen. Dadurch kann die Anwendung zwei Funktionen erfüllen:  
  
-   Erstellen Sie eigene Dialogfelder, um diese Informationen einzugeben, und behalten Sie die Kontrolle über das "Aussehen und fühlen".  
  
-   Durchsuchen des Systems nach Datenquellen, die von einem bestimmten Treiber verwendet werden können. Dies sollte nach Möglichkeit in mehreren Schritten erfolgen. Beispielsweise kann der Benutzer zunächst das Netzwerk nach Servern durchsuchen und, sobald er einen Server ausgewählt hat, diesen nach Datenbanken durchsuchen, auf die der Treiber zugreifen kann.  
  
 Die Anwendung ruft **sqlbrowseconnetct** auf und übergibt eine Verbindungs Zeichenfolge, die als *Verbindungs Zeichenfolge für Suchanforderungen bezeichnet wird* und einen Treiber oder eine Datenquelle angibt. Der Treiber gibt eine Verbindungs Zeichenfolge zurück, die als Such *Ergebnis-Verbindungs Zeichenfolge* bezeichnet wird, die Schlüsselwörter enthält, mögliche Werte (wenn das Schlüsselwort einen diskreten Satz von Werten akzeptiert) und benutzerfreundliche Namen. Die Anwendung erstellt ein Dialogfeld mit den benutzerfreundlichen Namen und fordert den Benutzer zur Eingabe von Werten auf. Anschließend wird eine neue Verbindungs Zeichenfolge für die Such Anforderung aus diesen Werten erstellt und mit einem anderen **sqlbrowseconnetct**-Befehl an den Treiber zurückgegeben.  
  
 Da Verbindungs Zeichenfolgen hin-und hergeleitet werden, kann der Treiber mehrere browseebenen bereitstellen, indem eine neue Verbindungs Zeichenfolge zurückgegeben wird, wenn die Anwendung die alte zurückgibt. Wenn beispielsweise eine Anwendung zum ersten Mal **sqlbrowseconnetct**aufruft, gibt der Treiber möglicherweise Schlüsselwörter zurück, um den Benutzer zur Eingabe eines Server namens aufzufordern. Wenn die Anwendung den Servernamen zurückgibt, gibt der Treiber möglicherweise Schlüsselwörter zurück, um den Benutzer zur Eingabe einer Datenbank aufzufordern. Der Browserprozess wäre fertig, nachdem die Anwendung den Datenbanknamen zurückgegeben hat.  
  
 Jedes Mal, wenn **sqlbrowseconnetct** eine neue Verbindungs Zeichenfolge zum Durchsuchen von Ergebnissen zurückgibt, wird SQL_NEED_DATA als Rückgabecode zurückgegeben. Dadurch wird der Anwendung mitgeteilt, dass der Verbindungsprozess nicht beendet ist. Bis **sqlbrowseconnetct** SQL_SUCCESS zurückgibt, befindet sich die Verbindung in einem erforderlichen Daten Zustand und kann nicht für andere Zwecke verwendet werden, wie z. b. zum Festlegen eines Verbindungs Attributs. Die Anwendung kann den Vorgang zum Durchsuchen der Verbindung beenden, indem **SQLDisconnect**aufgerufen wird.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [SQL Server-Suchbeispiel](../../../odbc/reference/develop-app/sql-server-browsing-example.md)
