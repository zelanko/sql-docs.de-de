---
title: Herstellen einer Verbindung mit einer Datenquelle (ODBC-Treiber für Oracle) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6ef567c9e3c7b63e7f5044de699750de856f3e52
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81281300"
---
# <a name="connecting-to-a-data-source-odbc-driver-for-oracle"></a>Herstellen einer Verbindung mit einer Datenquelle (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Eine ODBC-Anwendung kann Verbindungsinformationen auf verschiedene Weise übergeben. Die Anwendung kann z. B. dazu führen, dass der Treiber den Benutzer immer zur Eingabe von Verbindungsinformationen auffordert. Oder die Anwendung erwartet eine Verbindungszeichenfolge, die die Datenquellenverbindung angibt. Wie Sie eine Verbindung mit einer Datenquelle herstellen, hängt von der Verbindungsmethode ab, die von Ihrer ODBC-Anwendung verwendet wird.  
  
 Eine häufige Möglichkeit zum Herstellen einer Verbindung mit einer Datenquelle ist das Dialogfeld Datenquelle. Wenn Ihre ODBC-Anwendung für die Verwendung eines Dialogfelds eingerichtet ist, wird dieses Dialogfeld angezeigt und Sie werden zur Eingabe der entsprechenden Datenquellenverbindungsinformationen aufgefordert.  
  
 Sie können auch eine Verbindung mit einer Datenquelle über die [Verbindungszeichenfolge](../../odbc/microsoft/connection-string-format-and-attributes.md)herstellen.  
  
### <a name="to-connect-to-a-data-source-using-a-dialog-box"></a>So stellen Sie eine Verbindung mit einer Datenquelle über ein Dialogfeld her  
  
1.  Wenn das Dialogfeld Datenquelle angezeigt wird, wählen Sie eine Oracle-Datenquelle aus, und klicken Sie dann auf OK. Das Dialogfeld Verbinden wird angezeigt.  
  
2.  Geben Sie die entsprechenden Informationen für das Dialogfeld Verbinden ein, und klicken Sie dann auf OK.  
  
 Nachdem die Verbindungsinformationen überprüft wurden, kann Ihre Anwendung den ODBC-Treiber für Oracle verwenden, um auf die Informationen zuzugreifen, die die Datenquelle enthält.
