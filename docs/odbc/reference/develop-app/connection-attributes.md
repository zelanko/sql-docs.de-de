---
title: Verbindungsattribute | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection attributes
- ODBC drivers [ODBC], connection attributes
- connecting to data source [ODBC], connection attributes
- connection attributes [ODBC]
- connecting to driver [ODBC], connection attributes
ms.assetid: e6d03089-30a3-4627-a642-591ba0980894
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f0fad1db10e40c71d22dd75417420c54cefa7803
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63194437"
---
# <a name="connection-attributes"></a>Verbindungsattribute
Verbindungsattribute sind Eigenschaften der Verbindung. Da Transaktionen auf Verbindungsebene auftreten, handelt es sich bei der Transaktionsisolationsstufe beispielsweise um ein Verbindungsattribut. Ebenso ist das Anmeldungstimeout oder Anzahl von Sekunden zu warten, bevor ein Timeout, eine Verbindung herstellen möchten, ein Verbindungsattribut.  
  
 Verbindungsattribute festgelegt **SQLSetConnectAttr** und ihre aktuellen Einstellungen abgerufen werden, mit **SQLGetConnectAttr**. Wenn **SQLSetConnectAttr** wird aufgerufen, bevor der Treiber geladen ist, wird der Treiber-Manager speichert die Attribute in seiner Verbindungsstruktur und legt sie im Rahmen des Verbindungsprozesses im Treiber fest. Es ist nicht erforderlich, dass eine Anwendung Verbindungsattribute festlegen. Alle Verbindungsattribute haben Standardwerte, von die einige Treiber-spezifisch sind.  
  
 Ein Verbindungsattribut kann vor oder nach der Verbindung oder entweder, abhängig von das Attribut und der Treiber festgelegt werden. Das Anmeldungstimeout (SQL_ATTR_LOGIN_TIMEOUT) angewendet wird, um den Verbindungsprozess aus, und nur dann wirksam, wenn vor dem Herstellen einer Verbindung festgelegt. Die Attribute, die angeben, ob die ODBC-Cursorbibliothek (SQL_ATTR_ODBC_CURSORS) und die Netzwerk-Paketgröße (SQL_ATTR_PACKET_SIZE) verwenden müssen, bevor Sie eine Verbindung herstellen, festgelegt werden, da die ODBC-Cursorbibliothek zwischen der Treiber-Manager und der Treiber befindet und aus diesem Grund muss vor der Treiber geladen werden.  
  
 Die Attribute angeben, ob eine Datenquelle schreibgeschützt ist oder Lese-/ Schreibzugriff (SQL_ATTR_ACCESS_MODE) und den aktuellen Katalog (SQL_ATTR_CURRENT_CATALOG) festgelegt werden, können vor oder nach der eine Verbindung herstellen, je nach den Treiber. Jedoch festlegen, interoperable Anwendungen ausführen können sie vor dem Herstellen einer Verbindung, da einige Treiber ist es nicht möglich, diese nach dem Herstellen einer Verbindung zu ändern.  
  
 Einige Verbindungsattribute ist standardmäßig auf, bevor die Verbindung hergestellt wird, andere jedoch nicht. Führen Sie die sind SQL_ATTR_ACCESS_MODE SQL_ATTR_AUTOCOMMIT, SQL_ATTR_LOGIN_TIMEOUT, SQL_ATTR_ODBC_CURSORS, SQL_ATTR_TRACE und SQL_ATTR_TRACEFILE.  
  
 Die Übersetzung Verbindungsattribute (SQL_ATTR_TRANSLATE_DLL und SQL_ATTR_TRANSLATE_OPTION) müssen nach dem Herstellen einer Verbindung festgelegt werden.  
  
 Alle weiteren Verbindungsattributen können zu einem beliebigen Zeitpunkt festgelegt werden. Weitere Informationen finden Sie unter den [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) funktionsbeschreibung. (Verbindungsattribute können nicht auf der Umgebungsebene festgelegt werden, durch einen Aufruf von **SQLSetEnvAttr**.)
