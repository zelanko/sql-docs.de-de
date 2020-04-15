---
title: Standard-Gateway | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- standardizing database access [ODBC], gateways
- standard gateways [ODBC]
- gateways [ODBC]
ms.assetid: b8341492-2141-4bab-80bd-f2752223079e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 67551845c0dd8c6a28c0c4bc1c50f54ee8232df1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280073"
---
# <a name="standard-gateway"></a>Standardgateway
Ein *Gateway* ist eine Software, die bewirkt, dass ein DBMS wie ein anderes aussieht. Das heißt, das Gateway akzeptiert die Programmierschnittstelle, die SQL-Grammatik und das Datenstromprotokoll eines einzelnen DBMS und übersetzt es in die Programmierschnittstelle, SQL-Grammatik und das Datenstromprotokoll des ausgeblendeten DBMS. Beispielsweise können Anwendungen, die für die Verwendung von Microsoft® SQL Server geschrieben wurden™ auch über das Micro Decisionware DB2 Gateway auf DB2-Daten zugreifen. Dieses Produkt bewirkt, dass DB2 wie SQL Server aussieht. Wenn Gateways verwendet werden, muss für jede Zieldatenbank ein anderes Gateway geschrieben werden.  
  
 Obwohl Gateways durch architektonische Unterschiede zwischen DBMS begrenzt sind, sind sie ein guter Kandidat für die Standardisierung. Wenn jedoch alle DBMS auf der Programmierschnittstelle, der SQL-Grammatik und dem Datenstromprotokoll eines einzelnen DBMS standardisieren sollen, deren DBMS als Standard ausgewählt werden soll? Sicherlich wird kein kommerzieller DBMS-Anbieter einer Standardisierung des Produkts eines Mitbewerbers zustimmen. Und wenn eine Standard-Programmierschnittstelle, SQL-Grammatik und ein Datenstromprotokoll entwickelt werden, wird kein Gateway benötigt.
