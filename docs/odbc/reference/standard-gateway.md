---
title: Standard Gateway | Microsoft-Dokumentation
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
ms.openlocfilehash: 8120f3cda584240b0b58ed5d6758621b18fe44d3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68070480"
---
# <a name="standard-gateway"></a>Standardgateway
Ein *Gateway* ist eine Software, die bewirkt, dass ein DBMS wie ein anderes aussieht. Dies bedeutet, dass das Gateway die Programmierschnittstelle, die SQL-Grammatik und das Datenstrom Protokoll eines einzelnen DBMS akzeptiert und in die Programmierschnittstelle, die SQL-Grammatik und das Datenstrom Protokoll des verborgenen DBMS übersetzt. Beispielsweise können Anwendungen, die für die Verwendung von Microsoft® SQL Server™ geschrieben wurden, auch über das Micro DecisionWare DB2-Gateway auf DB2-Daten zugreifen. Dieses Produkt bewirkt, dass DB2 wie SQL Server aussieht. Wenn Gateways verwendet werden, muss für jede Zieldatenbank ein anderes Gateway geschrieben werden.  
  
 Obwohl Gateways durch architektonische Unterschiede zwischen DBMSs beschränkt sind, sind Sie ein guter Kandidat für die Standardisierung. Wenn allerdings alle DBMSs die Programmierschnittstelle, die SQL-Grammatik und das Datenstrom Protokoll eines einzelnen DBMS standardisieren sollen, dessen DBMS als Standard ausgewählt werden soll? Sicherlich ist es wahrscheinlich, dass kein kommerzieller DBMS-Hersteller die Standardisierung des Produkts eines Mitbewerber zustimmt. Wenn eine Standard Programmierschnittstelle, eine SQL-Grammatik und ein Datenstrom Protokoll entwickelt werden, ist kein Gateway erforderlich.
