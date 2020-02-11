---
title: Verbindungs Attribute | Microsoft-Dokumentation
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
ms.openlocfilehash: 09b29277d74383abff1510ca7394aecad036fc7e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68036441"
---
# <a name="connection-attributes"></a>Verbindungsattribute
Verbindungs Attribute sind Eigenschaften der Verbindung. Da Transaktionen auf Verbindungsebene auftreten, handelt es sich bei der Transaktionsisolationsstufe beispielsweise um ein Verbindungsattribut. Entsprechend ist das Anmeldungs Timeout oder die Anzahl von Sekunden, die beim Verbindungsversuch gewartet werden soll, bevor ein Timeout auftritt, ein Verbindungs Attribut.  
  
 Verbindungs Attribute werden mit **SQLSetConnectAttr** und ihren aktuellen Einstellungen festgelegt, die mit **SQLGetConnectAttr**abgerufen werden. Wenn **SQLSetConnectAttr** vor dem Laden des Treibers aufgerufen wird, speichert der Treiber-Manager die Attribute in der Verbindungs Struktur und legt diese im Rahmen des Verbindungsprozesses im Treiber fest. Es ist nicht erforderlich, dass von einer Anwendung Verbindungs Attribute festgelegt werden. alle Verbindungs Attribute verfügen über Standardwerte, von denen einige Treiber spezifisch sind.  
  
 Ein Verbindungs Attribut kann vor oder nach der Verbindung oder je nach Attribut und Treiber festgelegt werden. Der Anmeldungs Timeout (SQL_ATTR_LOGIN_TIMEOUT) gilt für den Verbindungsprozess und ist nur wirksam, wenn er vor dem Herstellen einer Verbindung festgelegt wird. Die Attribute, die angeben, ob die ODBC-Cursor Bibliothek (SQL_ATTR_ODBC_CURSORS) und die Netzwerk Paketgröße (SQL_ATTR_PACKET_SIZE) verwendet werden müssen, bevor eine Verbindung hergestellt wird, da die ODBC-Cursor Bibliothek zwischen dem Treiber-Manager und dem Treiber und muss daher vor dem Treiber geladen werden.  
  
 Die Attribute, die angeben, ob eine Datenquelle schreibgeschützt oder Lese-/Schreibzugriff (SQL_ATTR_ACCESS_MODE) ist, und der aktuelle Katalog (SQL_ATTR_CURRENT_CATALOG) kann je nach Treiber vor oder nach dem Herstellen der Verbindung festgelegt werden. Allerdings werden von interoperablen Anwendungen diese vor der Verbindungs Herstellung festgelegt, da einige Treiber das Ändern dieser nach der Verbindung nicht unterstützen.  
  
 Einige Verbindungs Attribute verfügen über einen Standardwert, bevor die Verbindung hergestellt wird, andere hingegen nicht. Dabei handelt es sich um SQL_ATTR_ACCESS_MODE, SQL_ATTR_AUTOCOMMIT, SQL_ATTR_LOGIN_TIMEOUT, SQL_ATTR_ODBC_CURSORS, SQL_ATTR_TRACE und SQL_ATTR_TRACEFILE.  
  
 Die Übersetzungs Verbindungs Attribute (SQL_ATTR_TRANSLATE_DLL und SQL_ATTR_TRANSLATE_OPTION) müssen nach dem Herstellen der Verbindung festgelegt werden.  
  
 Alle anderen Verbindungs Attribute können jederzeit festgelegt werden. Weitere Informationen finden Sie in der Beschreibung der [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) -Funktion. (Verbindungs Attribute können nicht auf Umgebungs Ebene durch einen **SQLSetEnvAttr**-Befehl festgelegt werden.)
