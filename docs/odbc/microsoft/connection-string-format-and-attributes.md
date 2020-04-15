---
title: Verbindungszeichenfolgenformat und Attribute | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81281150"
---
# <a name="connection-string-format-and-attributes"></a>Format und Attribute von Verbindungszeichenfolgen
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Anstatt ein Dialogfeld zu verwenden, benötigen einige Anwendungen möglicherweise eine Verbindungszeichenfolge, die Datenquellenverbindungsinformationen angibt. Die Verbindungszeichenfolge besteht aus einer Reihe von Attributen, die angeben, wie ein Treiber eine Verbindung mit einer Datenquelle herstellt. Ein Attribut identifiziert eine bestimmte Information, die der Treiber kennen muss, bevor er die entsprechende Datenquellenverbindung herstellen kann. Jeder Treiber kann über einen anderen Satz von Attributen verfügen, aber das Verbindungszeichenfolgenformat ist immer gleich. Eine Verbindungszeichenfolge hat das folgende Format:  
  
```  
"DSN=data-source-name[;SERVER=value] [;PWD=value] [;UID=value] [;<Attribute>=<value>]"  
```  
  
> [!NOTE]  
>  Der Microsoft ODBC-Treiber für Oracle unterstützt das Verbindungszeichenfolgenformat `CONNECTSTRING`der ersten `SERVER=`Version des Treibers, die = anstelle von verwendet hat.  
  
 Wenn Sie eine Verbindung zu einem Datenquellenanbieter herstellen, `Trusted_Connection=yes` der die Windows-Authentifizierung unterstützt, sollten Sie anstelle von Benutzer-ID- und Kennwortinformationen in der Verbindungszeichenfolge angeben.  
  
 Sie müssen den Datenquellennamen angeben, wenn Sie die Attribute UID, PWD, SERVER (oder CONNECTSTRING) und DRIVER nicht angeben. Alle anderen Attribute sind jedoch optional. Wenn Sie kein Attribut angeben, entspricht dieses Attribut dem Attribut, das auf der entsprechenden Registerkarte DSN des Dialogfelds **ODBC Data Source Administrator** angegeben ist. Bei dem Attributwert kann die Groß-/Kleinschreibung beachtet werden.  
  
 Die Attribute für die Verbindungszeichenfolge lauten wie folgt:  
  
|Attribut|Beschreibung|Standardwert|  
|---------------|-----------------|-------------------|  
|DSN|Der Datenquellenname, der auf der Registerkarte Treiber des Dialogfelds **ODBC Data Source Administrator** aufgeführt ist.|""|  
|PWD|Das Kennwort für den Oracle Server, auf den Sie zugreifen möchten. Dieser Treiber unterstützt Einschränkungen, die Oracle für Kennwörter aufstellt.|""|  
|SERVER|Die Verbindungszeichenfolge für den Oracle Server, auf den Sie zugreifen möchten.|""|  
|UID|Der Oracle Server-Benutzername. Je nach System ist dieses Attribut möglicherweise nicht optional, d. h. bestimmte Datenbanken und Tabellen erfordern dieses Attribut möglicherweise aus Sicherheitsgründen.<br /><br /> Verwenden Sie "/", um die Authentifizierung des Betriebssystems von Oracle zu verwenden.|""|  
|Buffersize|Die optimale Puffergröße, die beim Abrufen von Spalten verwendet wird.<br /><br /> Der Treiber optimiert das Abrufen, sodass ein Abruf vom Oracle Server genügend Zeilen zurückgibt, um einen Puffer dieser Größe zu füllen. Größere Werte erhöhen tendenziell die Leistung, wenn Sie viele Daten abrufen.|65.535|  
|SYNONYMCOLUMNS|Wenn dieser Wert true (1) ist, gibt ein SQLColumn( ) API-Aufruf Spalteninformationen zurück. Andernfalls gibt SQLColumn( nur Spalten für Tabellen und Ansichten zurück. Der ODBC-Treiber für Oracle bietet einen schnelleren Zugriff, wenn dieser Wert nicht festgelegt ist.|1|  
|ANMERKUNGEN|Wenn dieser Wert true ist (1), gibt der Treiber Remarks-Spalten für das [SQLColumns-Resultset](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md) zurück. Der ODBC-Treiber für Oracle bietet einen schnelleren Zugriff, wenn dieser Wert nicht festgelegt ist.|0|  
|StdDayOfWeek|Erzwingt den ODBC-Standard für den DAYOFWEEK-Skalar. Standardmäßig ist dies aktiviert, aber Benutzer, die die lokalisierte Version benötigen, können das Verhalten ändern, um die von Oracle zurückgibt verwenden.|1|  
|GuessTheColDef|Gibt an, ob der Treiber einen Wert ungleich Null für das *cbColDef-Argument* von **SQLDescribeCol**zurückgeben soll. Gilt nur für Spalten, in denen es keinen Oracle-definierten Maßstab gibt, z. B. berechnete numerische Spalten und Spalten, die als NUMBER ohne Genauigkeit oder Skalierung definiert sind. Ein **SQLDescribeCol-Aufruf** gibt 130 für die Genauigkeit zurück, wenn Oracle diese Informationen nicht zur Verfügung stellt.|0|  
  
 Eine Verbindungszeichenfolge, die mit der MyDataSource-Datenquelle über MyOracleServerOracle Server und Oracle User MyUserID eine Verbindung herstellt, wäre z. B.:  
  
```  
"DSN={MyDataSource};UID={MyUserID};PWD={MyPassword};SERVER={MyOracleServer}"  
```  
  
 Eine Verbindungszeichenfolge, die mithilfe der Betriebssystemauthentifizierung und des MyOtherOracleServerOracle Servers eine Verbindung mit der MyOtherDataSource-Datenquelle herstellt, wäre:  
  
```  
"DSN=MyOtherDataSource;UID=/;PWD=;SERVER=MyOtherOracleServer"  
```
