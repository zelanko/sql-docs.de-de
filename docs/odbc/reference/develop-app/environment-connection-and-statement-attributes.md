---
title: Umgebungs-, Verbindungs- und Anweisungsattribute | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 86cecaf0b82c7b6d15b3f37262507d2cff0c3c10
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300930"
---
# <a name="environment-connection-and-statement-attributes"></a>Umgebungs-, Verbindungs- und Anweisungsattribute
ODBC definiert eine Reihe von Attributen, die Umgebungen, Verbindungen oder Anweisungen zugeordnet sind.  
  
 Umgebungsattribute wirken sich auf die gesamte Umgebung aus, z. B. ob das Verbindungspooling aktiviert ist. Umgebungsattribute werden mit **SQLSetEnvAttr** festgelegt und mit **SQLGetEnvAttr**abgerufen.  
  
 Verbindungsattribute wirken sich individuell auf jede Verbindung aus, z. B. wie lange ein Treiber warten soll, während er versucht, eine Verbindung mit einer Datenquelle herzustellen, bevor ein Timeout durchgeführt wird. Verbindungsattribute werden mit **SQLSetConnectAttr** festgelegt und mit **SQLGetConnectAttr**abgerufen. Weitere Informationen zu Verbindungsattributen finden Sie unter [Verbindungsattribute](../../../odbc/reference/develop-app/connection-attributes.md).  
  
 Anweisungsattribute wirken sich individuell auf jede Anweisung aus, z. B. ob eine Anweisung asynchron ausgeführt werden soll. Anweisungsattribute werden mit **SQLSetStmtAttr** festgelegt und mit **SQLGetStmtAttr**abgerufen. Einige Anweisungsattribute sind schreibgeschützte Attribute und können nicht festgelegt werden. Beispielsweise ist das attribut SQL_ATTR_ROW_NUMBER Anweisung, das zum Abrufen der Nummer der aktuellen Zeile im Cursor verwendet wird, schreibgeschützt. Weitere Informationen zu Anweisungsattributen finden Sie unter [Anweisungsattribute](../../../odbc/reference/develop-app/statement-attributes.md).  
  
 Zusätzlich zu den von ODBC definierten Attributen kann ein Treiber seine eigenen Verbindungs- und Anweisungsattribute definieren. Treiberdefinierte Attribute müssen bei Open Group registriert werden, um sicherzustellen, dass zwei Treiberanbieter unterschiedlichen, proprietären Attributen nicht denselben Ganzzahlwert zuweisen. Weitere Informationen finden Sie unter [Treiberspezifische Datentypen, Deskriptortypen, Informationstypen, Diagnosetypen und Attribute](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Eine vollständige Liste der Attribute finden Sie unter [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md), [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)und [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md). Die meisten Attribute werden auch in der Beschreibung der ODBC-Funktion beschrieben, die sie beeinflussen.
