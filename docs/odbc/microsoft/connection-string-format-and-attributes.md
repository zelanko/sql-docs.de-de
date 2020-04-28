---
title: Format und Attribute der Verbindungs Zeichenfolge | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connection strings [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], connection strings
ms.assetid: 0c360112-8720-4e54-a1a6-b9b18d943557
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d95866976d2e83c058f83b3a0ae5e9a4e8888ed1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81281150"
---
# <a name="connection-string-format-and-attributes"></a>Format und Attribute von Verbindungszeichenfolgen
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Anstatt ein Dialogfeld zu verwenden, benötigen einige Anwendungen möglicherweise eine Verbindungs Zeichenfolge, die Informationen zur Datenquellen Verbindung angibt. Die Verbindungs Zeichenfolge besteht aus einer Reihe von Attributen, die angeben, wie ein Treiber eine Verbindung mit einer Datenquelle herstellt. Ein Attribut identifiziert eine bestimmte Information, die der Treiber wissen muss, bevor er die entsprechende Datenquellen Verbindung herstellen kann. Jeder Treiber verfügt möglicherweise über einen anderen Satz von Attributen, aber das Format der Verbindungs Zeichenfolge ist immer identisch. Eine Verbindungs Zeichenfolge weist das folgende Format auf:  
  
```  
"DSN=data-source-name[;SERVER=value] [;PWD=value] [;UID=value] [;<Attribute>=<value>]"  
```  
  
> [!NOTE]  
>  Der Microsoft ODBC Driver for Oracle unterstützt das Format der Verbindungs Zeichenfolge der ersten Version des Treibers `CONNECTSTRING`, bei der `SERVER=`= anstelle von verwendet wird.  
  
 Wenn Sie eine Verbindung mit einem Datenquellen Anbieter herstellen, der die Windows-Authentifizierung unter `Trusted_Connection=yes` stützt, sollten Sie anstelle von Benutzer-ID-und Kenn Wort Informationen in der Verbindungs Zeichenfolge angeben.  
  
 Sie müssen den Namen der Datenquelle angeben, wenn Sie die Attribute "UID", "pwd", "Server" (oder "connectstring") und "Driver" nicht angeben. Alle anderen Attribute sind jedoch optional. Wenn Sie kein Attribut angeben, wird dieses Attribut standardmäßig auf den Wert festgelegt, der im Dialogfeld **ODBC-Datenquellen-Administrator** auf der Registerkarte relevante DSN angegeben ist. Beim Attribut Wert kann die Groß-/Kleinschreibung beachtet werden.  
  
 Die Attribute für die Verbindungs Zeichenfolge lauten wie folgt:  
  
|Attribut|BESCHREIBUNG|Standardwert|  
|---------------|-----------------|-------------------|  
|DSN|Der Datenquellen Name, der im Dialogfeld **ODBC-Datenquellen-Administrator** auf der Registerkarte Treiber aufgelistet ist.|""|  
|PWD|Das Kennwort für den Oracle-Server, auf den Sie zugreifen möchten. Dieser Treiber unterstützt Beschränkungen, die Oracle auf Kenn Wörtern platziert.|""|  
|SERVER|Die Verbindungs Zeichenfolge für den Oracle-Server, auf den Sie zugreifen möchten.|""|  
|UID|Der Benutzername des Oracle-Servers. Abhängig von Ihrem System ist dieses Attribut möglicherweise nicht optional, d. h., bestimmte Datenbanken und Tabellen benötigen dieses Attribut möglicherweise aus Sicherheitsgründen.<br /><br /> Verwenden Sie "/", um die Betriebssystem Authentifizierung von Oracle zu verwenden.|""|  
|BufferSize|Die optimale Puffergröße, die zum Abrufen von Spalten verwendet wird.<br /><br /> Der Treiber optimiert das Abrufen, sodass ein Abruf vom Oracle-Server genügend Zeilen zurückgibt, um einen Puffer dieser Größe auszufüllen. Größere Werte verbessern tendenziell die Leistung, wenn Sie viele Daten abrufen.|65.535|  
|Synonymcolumns|Wenn dieser Wert true (1) ist, gibt ein sqlcolumn ()-API-Rückruf Spalten Informationen zurück. Andernfalls gibt sqlcolumn () nur Spalten für Tabellen und Sichten zurück. Der ODBC-Treiber für Oracle bietet schnelleren Zugriff, wenn dieser Wert nicht festgelegt ist.|1|  
|ANMERKUNGEN|Wenn dieser Wert true (1) ist, gibt der Treiber Hinweise Spalten für das [SQLColumns](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md) -Resultset zurück. Der ODBC-Treiber für Oracle bietet schnelleren Zugriff, wenn dieser Wert nicht festgelegt ist.|0|  
|Stddayof-Woche|Erzwingt den ODBC-Standard für das dayooweek-Skalar. Standardmäßig ist diese Einstellung aktiviert, aber Benutzer, die die lokalisierte Version benötigen, können das Verhalten ändern, um die von Oracle zurückgegebenen Werte zu verwenden.|1|  
|Guess thecoldef|Gibt an, ob der Treiber für das *cbcoldef* -Argument von **SQLDescribeCol**einen Wert ungleich 0 (null) zurückgeben soll. Gilt nur für Spalten, bei denen keine Oracle-definierte Skala vorhanden ist, z. b. berechnete numerische Spalten und Spalten, die als Zahl ohne Genauigkeit oder Dezimalstelle definiert sind. Ein **SQLDescribeCol** -Befehl gibt 130 für die Genauigkeit zurück, wenn Oracle diese Informationen nicht bereitstellt.|0|  
  
 Eine Verbindungs Zeichenfolge, die eine Verbindung mit der MyDatasource-Datenquelle mithilfe des myoracleserveroracle-Servers und des Oracle-Benutzers myuserid herstellt, lautet beispielsweise wie folgt:  
  
```  
"DSN={MyDataSource};UID={MyUserID};PWD={MyPassword};SERVER={MyOracleServer}"  
```  
  
 Eine Verbindungs Zeichenfolge, die mithilfe der Betriebssystem Authentifizierung und des myotheroracleserveroracle-Servers eine Verbindung mit der myotherdatasource-Datenquelle herstellt:  
  
```  
"DSN=MyOtherDataSource;UID=/;PWD=;SERVER=MyOtherOracleServer"  
```
