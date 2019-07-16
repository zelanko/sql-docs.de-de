---
title: Format der Verbindungszeichenfolge und Attribute | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a007f4c7c92bf4254e4d36638cf2d92ba0764be5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68082023"
---
# <a name="connection-string-format-and-attributes"></a>Format und Attribute von Verbindungszeichenfolgen
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den ODBC-Treiber, die von Oracle bereitgestellt.  
  
 Anstatt ein Dialogfeld, möglicherweise bei einigen Anwendungen eine Verbindungszeichenfolge, die Datenquellen-Verbindungsinformationen angibt. Die Verbindungszeichenfolge besteht aus einer Anzahl von Attributen, die angeben, wie ein Treiber eine Verbindung mit einer Datenquelle herstellt. Ein Attribut identifiziert eine bestimmte Information, die der Treiber muss wissen, bevor sie die entsprechenden datenquellenverbindung vornehmen kann. Jeder Treiber möglicherweise einen anderen Satz von Attributen, aber das Format der Verbindungszeichenfolge ist immer gleich. Eine Verbindungszeichenfolge hat das folgende Format:  
  
```  
"DSN=data-source-name[;SERVER=value] [;PWD=value] [;UID=value] [;<Attribute>=<value>]"  
```  
  
> [!NOTE]  
>  Der Microsoft ODBC-Treiber für Oracle unterstützt die Connection-Zeichenfolgenformat der ersten Version des Treibers, der verwendet `CONNECTSTRING`anstelle von = `SERVER=`.  
  
 Wenn Sie für einen Datenanbieter der Datenquelle, der Windows-Authentifizierung unterstützt herstellen, sollten Sie angeben `Trusted_Connection=yes` anstelle von Benutzer-ID und Kennwort-Informationen in der Verbindungszeichenfolge.  
  
 Sie müssen angeben, die die Datenquelle nennen, wenn Sie nicht die UID, PWD, SERVER (oder CONNECTSTRING) angeben und Treiber-Attribute. Alle anderen Attribute sind jedoch optional. Wenn Sie ein Attribut nicht angeben, dieses Attribut standardmäßig in der relevanten DSN-Registerkarte des angegebenen die **ODBC-Datenquellenadministrator** Dialogfeld. Den Wert des Attributs kann Groß-/Kleinschreibung beachtet werden.  
  
 Die Attribute für die Verbindungszeichenfolge lauten wie folgt aus:  
  
|Attribut|Beschreibung|Standardwert|  
|---------------|-----------------|-------------------|  
|DSN|Der Name der Datenquelle aufgeführt, in der Registerkarte "Treiber" der **ODBC-Datenquellenadministrator** Dialogfeld.|""|  
|PWD|Das Kennwort für den Oracle-Server, die Sie zugreifen möchten. Dieser Treiber unterstützt die Einschränkungen, die von Oracle auf Kennwörter platziert.|""|  
|SERVER|Die Verbindungszeichenfolge für den Oracle-Server, die Sie zugreifen möchten.|""|  
|UID|Der Name des Oracle-Server. Dieses Attribut kann nicht optional sein –, also bestimmte Datenbanken und Tabellen möglicherweise muss dieses Attribut aus Sicherheitsgründen, abhängig von Ihrem System.<br /><br /> Verwenden Sie "/" zur Verwendung von Oracle des System-Authentifizierung ausgeführt.|""|  
|PUFFERGRÖSSE|Die optimale Puffergröße, die beim Abrufen der Spalten verwendet wird.<br /><br /> Der Treiber optimiert werden abgerufen, sodass einen Abruf aus der Oracle-Server genügend Zeilen für einen Puffer dieser Größe füllen zurückgibt. Größere Werte neigen dazu, um die Leistung zu erhöhen, wenn Sie große Datenmengen abrufen.|65535|  
|SYNONYMCOLUMNS|Wenn dieser Wert ist "true" (1), ein SQLSpalten-()-API-Aufruf gibt Spalteninformationen zurück. Andernfalls SQLSpalten-() nur die Spalten für Tabellen und Sichten. Der ODBC-Treiber für Oracle bietet schnelleren Zugriff auf, wenn dieser Wert nicht festgelegt ist.|1|  
|REMARKS|Wenn dieser Wert ist "true" (1), gibt der Treiber "Hinweise"-Spalten für die [SQLColumns](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md) Resultset. Der ODBC-Treiber für Oracle bietet schnelleren Zugriff auf, wenn dieser Wert nicht festgelegt ist.|0|  
|StdDayOfWeek|Erzwingt die ODBC-Standard für die DAYOFWEEK skalare an. Dies ist standardmäßig auf Benutzer, die die lokalisierte Version können allerdings ändern das Verhalten, um den Rückgabewert Oracle zurück zu verwenden.|1|  
|GuessTheColDef|Gibt an, und zwar unabhängig davon, ob der Treiber einen Wert ungleich NULL für zurückgeben soll die *CbColDef* Argument **SQLDescribeCol**. Gilt nur für Spalten, in denen es keine Skalierung Oracle definiert, ist wie z. B. berechnete numerische, Spalten und Spalten als Zahl ohne eine Genauigkeit oder Dezimalstellenanzahl. Ein **SQLDescribeCol** für die Genauigkeit gibt 130 aufrufen, wenn Oracle diese Informationen nicht bereitstellt.|0|  
  
 Beispielsweise wäre eine Verbindungszeichenfolge, die mit der mit dem MyOracleServerOracle-Server und die Oracle-Benutzer-MyUserID MyDataSource-Datenquelle stellt eine Verbindung her:  
  
```  
"DSN={MyDataSource};UID={MyUserID};PWD={MyPassword};SERVER={MyOracleServer}"  
```  
  
 Eine Verbindungszeichenfolge, die mit der MyOtherDataSource-Datenquelle mit Betriebssystem-Authentifizierung und dem MyOtherOracleServerOracle-Server verbunden wäre:  
  
```  
"DSN=MyOtherDataSource;UID=/;PWD=;SERVER=MyOtherOracleServer"  
```
