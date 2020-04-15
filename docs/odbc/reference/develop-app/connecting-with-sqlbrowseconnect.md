---
title: Herstellen einer Verbindung mit SQLBrowseConnect | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294660"
---
# <a name="connecting-with-sqlbrowseconnect"></a>Herstellen einer Verbindung mit SQLBrowseConnect
**SQLBrowseConnect**verwendet, z. B. **SQLDriverConnect**, eine Verbindungszeichenfolge. Mit **SQLBrowseConnect**kann eine Anwendung jedoch zur Laufzeit eine vollständige Verbindungszeichenfolge erstellen. Dadurch kann die Anwendung zwei Funktionen erfüllen:  
  
-   Erstellen Sie eigene Dialogfelder, um diese Informationen zu erhalten, und behalten Sie so die Kontrolle über ihr "Look and Feel".  
  
-   Durchsuchen des Systems nach Datenquellen, die von einem bestimmten Treiber verwendet werden können. Dies sollte nach Möglichkeit in mehreren Schritten erfolgen. Beispielsweise kann der Benutzer zunächst das Netzwerk nach Servern durchsuchen und, sobald er einen Server ausgewählt hat, diesen nach Datenbanken durchsuchen, auf die der Treiber zugreifen kann.  
  
 Die Anwendung ruft **SQLBrowseConnect** auf und übergibt eine Verbindungszeichenfolge, die als Verbindungszeichenfolge für *Suchanforderungen* bezeichnet wird und einen Treiber oder eine Datenquelle angibt. Der Treiber gibt eine Verbindungszeichenfolge zurück, die als *Verbindungszeichenfolge* zum Durchsuchen bezeichnet wird und Schlüsselwörter, mögliche Werte (wenn das Schlüsselwort einen diskreten Satz von Werten akzeptiert) und benutzerfreundliche Namen enthält. Die Anwendung erstellt ein Dialogfeld mit den benutzerfreundlichen Namen und fordert den Benutzer zur Eingabe von Werten auf. Anschließend wird eine neue Suchanforderungsverbindungszeichenfolge aus diesen Werten erstellt und diese an den Treiber mit einem weiteren Aufruf von **SQLBrowseConnect**zurückgegeben.  
  
 Da Verbindungszeichenfolgen hin und her übergeben werden, kann der Treiber mehrere Ebenen des Browsens bereitstellen, indem er eine neue Verbindungszeichenfolge zurückgibt, wenn die Anwendung die alte zurückgibt. Wenn z. B. eine Anwendung **SQLBrowseConnect**zum ersten Mal aufruft, gibt der Treiber möglicherweise Schlüsselwörter zurück, um den Benutzer zur Eingabe eines Servernamens aufzufordern. Wenn die Anwendung den Servernamen zurückgibt, gibt der Treiber möglicherweise Schlüsselwörter zurück, um den Benutzer zur Eingabe einer Datenbank aufzufordern. Der Browservorgang ist abgeschlossen, nachdem die Anwendung den Datenbanknamen zurückgegeben hat.  
  
 Jedes Mal, **wenn SQLBrowseConnect** eine neue Suchergebnisverbindungszeichenfolge zurückgibt, gibt es SQL_NEED_DATA als Rückgabecode zurück. Dadurch wird der Anwendung mitteilt, dass der Verbindungsvorgang nicht abgeschlossen ist. Bis **SQLBrowseConnect** SQL_SUCCESS zurückgibt, befindet sich die Verbindung im Status "Need Data" und kann nicht für andere Zwecke verwendet werden, z. B. zum Festlegen eines Verbindungsattributs. Die Anwendung kann den Vorgang zum Durchsuchen der Verbindung beenden, indem sie **SQLDisconnect aufruft.**  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [SQL Server-Suchbeispiel](../../../odbc/reference/develop-app/sql-server-browsing-example.md)
