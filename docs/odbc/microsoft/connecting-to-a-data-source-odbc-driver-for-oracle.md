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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68082042"
---
# <a name="connecting-to-a-data-source-odbc-driver-for-oracle"></a>Herstellen einer Verbindung mit einer Datenquelle (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Eine ODBC-Anwendung kann Verbindungsinformationen auf verschiedene Weise übergeben. Beispielsweise kann die Anwendung den Treiber immer zur Eingabe von Verbindungsinformationen auffordern. Oder die Anwendung erwartet eine Verbindungs Zeichenfolge, die die Datenquellen Verbindung angibt. Wie Sie eine Verbindung mit einer Datenquelle herstellen, hängt von der Verbindungsmethode ab, die von der ODBC-Anwendung verwendet wird.  
  
 Eine gängige Methode zum Herstellen einer Verbindung mit einer Datenquelle ist das Dialogfeld Datenquelle. Wenn Ihre ODBC-Anwendung für die Verwendung eines Dialog Felds eingerichtet ist, wird dieses Dialogfeld angezeigt, und Sie werden aufgefordert, die entsprechenden Datenquellen-Verbindungsinformationen einzugeben.  
  
 Sie können auch mit der [Verbindungs Zeichenfolge](../../odbc/microsoft/connection-string-format-and-attributes.md)eine Verbindung mit einer Datenquelle herstellen.  
  
### <a name="to-connect-to-a-data-source-using-a-dialog-box"></a>So stellen Sie über ein Dialogfeld eine Verbindung mit einer Datenquelle her  
  
1.  Wenn das Dialogfeld Datenquelle angezeigt wird, wählen Sie eine Oracle-Datenquelle aus, und klicken Sie dann auf OK. Das Dialogfeld Verbinden wird angezeigt.  
  
2.  Geben Sie die entsprechenden Informationen für das Verbindungs Dialogfeld ein, und klicken Sie dann auf OK.  
  
 Nachdem die Verbindungsinformationen überprüft wurden, kann die Anwendung mit dem ODBC-Treiber für Oracle auf die Informationen zugreifen, die in der Datenquelle enthalten sind.
