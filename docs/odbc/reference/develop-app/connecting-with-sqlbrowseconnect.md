---
title: Herstellen einer Verbindung mit SQLBrowseConnect | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 04df089b97bf385925c87a98b3f89cdac3ef21e4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68083136"
---
# <a name="connecting-with-sqlbrowseconnect"></a>Herstellen einer Verbindung mit SQLBrowseConnect
**SQLBrowseConnect**, z. B. **SQLDriverConnect**, verwendet eine Verbindungszeichenfolge. Indem jedoch **SQLBrowseConnect**, eine Anwendung kann eine vollständige Verbindungszeichenfolge zur Laufzeit erstellen. Dadurch kann die Anwendung zwei Funktionen erfüllen:  
  
-   Erstellen Sie eigener Dialogfelder können diese Informationen, die beibehalten werden und die Kontrolle über das "Erscheinungsbild."  
  
-   Durchsuchen des Systems nach Datenquellen, die von einem bestimmten Treiber verwendet werden können. Dies sollte nach Möglichkeit in mehreren Schritten erfolgen. Beispielsweise kann der Benutzer zunächst das Netzwerk nach Servern durchsuchen und, sobald er einen Server ausgewählt hat, diesen nach Datenbanken durchsuchen, auf die der Treiber zugreifen kann.  
  
 Ruft die Anwendung **SQLBrowseConnect** und übergibt Sie eine Verbindungszeichenfolge, bekannt als die *Verbindungszeichenfolge Anforderung Durchsuchen* , einen Treiber oder eine Datenquelle angibt. Gibt eine Verbindungszeichenfolge, bekannt als der Treiber die *Ergebnis Verbindungszeichenfolge eingegeben haben, Durchsuchen* , Schlüsselwörter, die möglichen Werte (sofern das Schlüsselwort einen diskreten Satz von Werten akzeptiert), enthält und benutzerfreundliche Namen. Die Anwendung erstellt ein Dialogfeld mit den benutzerfreundlichen Namen und fordert den Benutzer nach Werten. Anschließend erstellt eine neue durchsuchen-Anforderung Verbindungszeichenfolge aus diesen Werten und gibt diese zurück an den Treiber mit einem weiteren Aufruf von **SQLBrowseConnect**.  
  
 Da Verbindungszeichenfolgen hin und her übergeben werden, kann der Treiber bereitstellen, mehrere Ebenen von unterbunden, indem Sie eine neue Verbindungszeichenfolge zurückgegeben, wenn die Anwendung die alte Version zurückgegeben. Z. B. die ersten Mal eine Anwendung ruft **SQLBrowseConnect**, der Treiber möglicherweise zurück, Schlüsselwörtern, um den Benutzer auf einen Servernamen anzugeben. Wenn die Anwendung den Namen des Servers zurückgegeben wird, kann der Treiber Schlüsselwörtern, um die benutzeraufforderung für eine Datenbank zurück. Die Durchsuchen-Prozess würde abgeschlossen werden, nachdem die Anwendung der Name der Datenbank zurückgegeben.  
  
 Jedes Mal **SQLBrowseConnect** eine neue durchsuchen-Verbindung Ergebniszeichenfolge zurückgibt, wird SQL_NEED_DATA zurückgegeben, als der Rückgabecode zurückgegeben. Dies weist die Anwendung, dass die Verbindung noch nicht abgeschlossen ist. Bis **SQLBrowseConnect** gibt SQL_SUCCESS zurück, die Verbindung ist in einem Zustand müssen Daten und kann nicht verwendet werden für andere Zwecke, z. B. um ein Verbindungsattribut festzulegen. Die Anwendung kann die Verbindung mit dem Durchsuchen der Prozess durch den Aufruf beendet **SQLDisconnect**.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [SQL Server-Suchbeispiel](../../../odbc/reference/develop-app/sql-server-browsing-example.md)
