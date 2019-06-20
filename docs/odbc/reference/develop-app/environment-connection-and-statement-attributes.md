---
title: Umgebung, Verbindung und Anweisungsattribute | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- environment attributes [ODBC]
- connection attributes [ODBC]
- statement attributes [ODBC]
ms.assetid: 9e15b276-3b7a-428a-b72f-a3ddfe1ba1ce
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e77be71458eb10e97a82c925d34141a7bcaf1dc4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62943003"
---
# <a name="environment-connection-and-statement-attributes"></a>Umgebungs-, Verbindungs- und Anweisungsattribute
ODBC definiert eine Reihe von Attributen, die Umgebungen, Verbindungen oder Anweisungen zugeordnet sind.  
  
 Umgebungsattribute Auswirkungen auf die gesamte Umgebung, z. B., ob Verbindungspooling aktiviert ist. Umgebungsattribute festgelegt **SQLSetEnvAttr** und abgerufene mit **SQLGetEnvAttr**.  
  
 Verbindungsattribute beeinflussen jede Verbindung individuell, wie lange muss ein Treiber beim Versuch, eine Verbindung mit einer Datenquelle, bevor ein Timeout warten. Verbindungsattribute festgelegt **SQLSetConnectAttr** und abgerufene mit **SQLGetConnectAttr**. Weitere Informationen zu Verbindungsattributen finden Sie unter [Verbindungsattribute](../../../odbc/reference/develop-app/connection-attributes.md).  
  
 Jede Anweisung Auswirkungen von Anweisungsattribute einzeln auf, z. B., ob eine Anweisung asynchron ausgeführt werden soll. Anweisungsattribute werden mit festgelegt **SQLSetStmtAttr** und abgerufene mit **SQLGetStmtAttr**. Einige Anweisungsattribute sind nur-Lese Attribute und können nicht festgelegt werden. Beispielsweise ist das SQL_ATTR_ROW_NUMBER-Anweisung-Attribut, das zum Abrufen der Anzahl der aktuellen Zeile im Cursor verwendet wird, schreibgeschützt. Weitere Informationen zu Anweisungsattribute, finden Sie unter [Anweisungsattribute](../../../odbc/reference/develop-app/statement-attributes.md).  
  
 Zusätzlich zu Attributen, die von ODBC definiert werden kann ein Treiber eine eigene Verbindung und Anweisungsattribute definieren. Treiber benutzerdefinierte Attribute müssen registriert werden, mit Open Group, um sicherzustellen, dass zwei Treiber Anbieter unterschiedliche, proprietäre Attribute nicht den gleichen ganzzahligen Wert zuweisen. Weitere Informationen finden Sie unter [treiberspezifische Datentypen, Deskriptortypen, Informationstypen, Diagnosetypen und Attribute](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Eine vollständige Liste der Attribute, finden Sie unter [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md), [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), und [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md). Die meisten Attribute werden auch in der Beschreibung der ODBC-Funktion beschrieben, die sie betreffen.
