---
title: Herstellen einer Verbindung mit einer Datenquelle (ODBC-Treiber für Oracle) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to data source [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], connecting to data sources
ms.assetid: f724a9c5-342a-4f4e-a030-ec34f7378eaf
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b0e9e62c8e03166ec2f76b1c6bcb5000a062bac3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68082042"
---
# <a name="connecting-to-a-data-source-odbc-driver-for-oracle"></a>Herstellen einer Verbindung mit einer Datenquelle (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den ODBC-Treiber, die von Oracle bereitgestellt.  
  
 Eine ODBC-Anwendung kann die Verbindungsinformationen in eine Reihe von Möglichkeiten übergeben. Die Anwendung möglicherweise z. B. den Treiber, die immer den Benutzer zur Verbindungsinformationen aufzufordern. Oder die Anwendung möglicherweise erwarten, dass eine Verbindungszeichenfolge, die angibt, die datenquellenverbindung. Wie Sie eine Verbindung mit einer Datenquelle herstellen, hängt von der Verbindungsmethode, die von der ODBC-Anwendung verwendet.  
  
 Eine gebräuchliche Möglichkeit zum Verbinden mit einer Datenquelle wird über das Dialogfeld für die Datenquelle. Wenn die ODBC-Anwendung so eingerichtet ist, ein Dialogfeld zu verwenden, das Dialogfeld geöffnet wird angezeigt, und Sie werden aufgefordert, die entsprechenden Datenquellen-Verbindungsinformationen.  
  
 Sie können auch eine Verbinden mit einer Datenquelle mit dem [Verbindungszeichenfolge](../../odbc/microsoft/connection-string-format-and-attributes.md).  
  
### <a name="to-connect-to-a-data-source-using-a-dialog-box"></a>Für die Verbindung mit einer Datenquelle mithilfe des Dialogfelds  
  
1.  Wenn das Dialogfeld "Datenquelle" angezeigt wird, wählen Sie eine Oracle-Datenquelle, und klicken Sie dann auf OK. Das Dialogfeld Verbinden wird angezeigt.  
  
2.  Geben Sie die entsprechenden Informationen für die Verbindung herstellen (Dialogfeld), und klicken Sie dann auf OK.  
  
 Nachdem die Verbindung werden Informationen überprüft, Ihre Anwendung den ODBC-Treiber für Oracle verwenden können, auf die Informationen zugreifen, die die Datenquelle enthält.
