---
title: Standard-Gateway | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c70a558b065765dd9f8c0895345959e8aa22ebfe
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63232095"
---
# <a name="standard-gateway"></a>Standardgateway
Ein *Gateway* ist eine Softwarekomponente, die bewirkt, dass ein DBMS an, wie eine andere aus. Das heißt, akzeptiert das Gateway, die Programmierschnittstelle, die SQL-Grammatik, und Daten streamen Protokoll einer einzelnen DBMS und übersetzt diesen auf die Programmierschnittstelle, die SQL-Grammatik, und Protokolls des ausgeblendeten DBMS Data stream. Beispielsweise können Anwendungen so geschrieben, dass Microsoft® SQL Server™ auch DB2-Daten mithilfe der Micro Decisionware DB2-Gateway zugreifen. Dieses Produkt führt DB2, wie SQL Server zu suchen. Wenn Gateways verwendet werden, muss ein anderes Gateway für jede Zieldatenbank geschrieben werden.  
  
 Gateways durch architektonische Unterschiede zwischen den DBMS-Systeme beschränkt sind, sind jedoch ein guter Kandidat für die Standardisierung. Aber wenn allen DBMS sind Standardisierung auf die Programmierschnittstelle, SQL-Grammatik und Daten Protokolls stream einer einzelnen DBMS, deren DBMS wird als Standard ausgewählt werden? Sicherlich ist keine kommerziellen DBMS-Hersteller wahrscheinlich Standardisierung auf eines Konkurrenzprodukts zustimmen. Und wenn ein standard-Programmierschnittstelle, SQL-Grammatik und Data Stream-Protokoll entwickelt werden, ist kein Gateway erforderlich.
