---
title: Umgebungs-, Verbindungs-und Anweisungs Attribute | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300930"
---
# <a name="environment-connection-and-statement-attributes"></a>Umgebungs-, Verbindungs- und Anweisungsattribute
ODBC definiert eine Reihe von Attributen, die Umgebungen, Verbindungen oder Anweisungen zugeordnet sind.  
  
 Umgebungs Attribute wirken sich auf die gesamte Umgebung aus, z. b., ob Verbindungspooling aktiviert ist. Umgebungs Attribute werden mit **SQLSetEnvAttr** festgelegt und mit **SQLGetEnvAttr**abgerufen.  
  
 Verbindungs Attribute wirken sich einzeln auf jede Verbindung aus, z. b. wie lange ein Treiber beim Herstellen einer Verbindung mit einer Datenquelle warten soll, bevor ein Timeout eintritt. Verbindungs Attribute werden mit **SQLSetConnectAttr** festgelegt und mit **SQLGetConnectAttr**abgerufen. Weitere Informationen zu Verbindungs Attributen finden Sie unter [Verbindungs Attribute](../../../odbc/reference/develop-app/connection-attributes.md).  
  
 Anweisungs Attribute wirken sich einzeln auf jede Anweisung aus, z. b. ob eine Anweisung asynchron ausgeführt werden soll. Anweisungs Attribute werden mit **SQLSetStmtAttr** festgelegt und mit **SQLGetStmtAttr**abgerufen. Einige Anweisungs Attribute sind schreibgeschützte Attribute und können nicht festgelegt werden. Beispielsweise ist das SQL_ATTR_ROW_NUMBER Anweisungs Attribut, das verwendet wird, um die Nummer der aktuellen Zeile im Cursor abzurufen, schreibgeschützt. Weitere Informationen zu Anweisungs Attributen finden Sie unter [Anweisungs Attribute](../../../odbc/reference/develop-app/statement-attributes.md).  
  
 Zusätzlich zu den Attributen, die von ODBC definiert werden, kann ein Treiber seine eigenen Verbindungs-und Anweisungs Attribute definieren. Treiber definierte Attribute müssen bei einer offenen Gruppe registriert werden, um sicherzustellen, dass zwei Treiber Hersteller nicht denselben ganzzahligen Wert anderen, proprietären Attributen zuweisen. Weitere Informationen finden Sie unter [Treiber spezifische Datentypen, deskriptortypen, Informationstypen, Diagnose Typen und Attribute](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Eine umfassende Liste der Attribute finden Sie unter [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md), [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)und [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md). Die meisten Attribute werden auch in der Beschreibung der ODBC-Funktion beschrieben, die Sie betreffen.
