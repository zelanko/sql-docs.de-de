---
title: Verbindungsattribute | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c295ce88eedf1d4cddc4173f5dea39c44b01f83d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299041"
---
# <a name="connection-attributes"></a>Verbindungsattribute
Verbindungsattribute sind Merkmale der Verbindung. Da Transaktionen auf Verbindungsebene auftreten, handelt es sich bei der Transaktionsisolationsstufe beispielsweise um ein Verbindungsattribut. Ebenso ist das Anmeldetimeout oder die Anzahl der Sekunden, die beim Herstellen einer Verbindung vor dem Timeout gewartet werden müssen, ein Verbindungsattribut.  
  
 Verbindungsattribute werden mit **SQLSetConnectAttr** und ihren aktuellen Einstellungen festgelegt, die mit **SQLGetConnectAttr**abgerufen werden. Wenn **SQLSetConnectAttr** aufgerufen wird, bevor der Treiber geladen wird, speichert der Treiber-Manager die Attribute in seiner Verbindungsstruktur und legt sie im Treiber als Teil des Verbindungsprozesses fest. Es ist nicht erforderlich, dass eine Anwendung Verbindungsattribute festgelegt hat. Alle Verbindungsattribute haben Standardwerte, von denen einige treiberspezifisch sind.  
  
 Ein Verbindungsattribut kann vor oder nach der Verbindung oder entweder abhängig vom Attribut und dem Treiber festgelegt werden. Das Anmeldetimeout (SQL_ATTR_LOGIN_TIMEOUT) gilt für den Verbindungsprozess und ist nur wirksam, wenn es vor dem Herstellen einer Verbindung festgelegt wird. Die Attribute, die angeben, ob die ODBC-Cursorbibliothek (SQL_ATTR_ODBC_CURSORS) und die Netzwerkpaketgröße (SQL_ATTR_PACKET_SIZE) verwendet werden sollen, müssen vor dem Herstellen einer Verbindung festgelegt werden, da sich die ODBC-Cursorbibliothek zwischen dem Treiber-Manager und dem Treiber befindet und daher vor dem Treiber geladen werden muss.  
  
 Die Attribute, die angeben sollen, ob eine Datenquelle schreibgeschützt oder schreibgeschützt ist (SQL_ATTR_ACCESS_MODE) und der aktuelle Katalog (SQL_ATTR_CURRENT_CATALOG) kann vor oder nach der Verbindung festgelegt werden, je nach Treiber. Interoperable Anwendungen legen sie jedoch vor dem Herstellen einer Verbindung fest, da einige Treiber das Ändern dieser Anwendungen nach dem Herstellen einer Verbindung nicht unterstützen.  
  
 Einige Verbindungsattribute haben eine Standardeinstellung, bevor die Verbindung hergestellt wird, während andere dies nicht tun. Diejenigen, die das tun, sind SQL_ATTR_ACCESS_MODE, SQL_ATTR_AUTOCOMMIT, SQL_ATTR_LOGIN_TIMEOUT, SQL_ATTR_ODBC_CURSORS, SQL_ATTR_TRACE und SQL_ATTR_TRACEFILE.  
  
 Die Übersetzungsverbindungsattribute (SQL_ATTR_TRANSLATE_DLL und SQL_ATTR_TRANSLATE_OPTION) müssen nach dem Herstellen des Verbindungssatzes festgelegt werden.  
  
 Alle anderen Verbindungsattribute können jederzeit festgelegt werden. Weitere Informationen finden Sie in der [SQLSetConnectAttr-Funktionsbeschreibung.](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) (Verbindungsattribute können auf Umgebungsebene nicht durch einen Aufruf von **SQLSetEnvAttr**festgelegt werden.)
