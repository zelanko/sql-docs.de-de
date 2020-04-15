---
title: Verwenden der Betriebssystemauthentifizierung | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], authentication
- authentication [ODBC]
ms.assetid: 613daef7-3171-42d0-b7e3-3879280f864d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d6520202bdbc31baf1156531457cb70a98656e88
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292840"
---
# <a name="using-operating-system-authentication"></a>Verwenden der Betriebssystemauthentifizierung
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Die Oracle-Betriebssystemauthentifizierung basiert auf dem zugrunde liegenden Betriebssystem, um den Zugriff auf Datenbankkonten zu steuern. Benutzer müssen bei der Verwendung dieses Anmeldetyps kein Kennwort eingeben.  
  
 Um diese Funktion zu nutzen, geben Sie "/" als Benutzer-ID an und geben Sie kein Kennwort an, wenn Sie eine Verbindung mit einer der folgenden Verbindungs-APIs herstellen: [SQLBrowseConnect](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md), [SQLConnect](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md)oder [SQLDriverConnect](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md).  
  
 Oracle-Datenbanken verwenden SQL*Net Authentication Services, um angemeldete Benutzer zu authentifizieren. Dieser Dienst funktioniert gut, wenn Benutzer über SQLPlus bei Oracle angemeldet sind. Wenn es sich bei dem angemeldeten Benutzer jedoch um einen Dienst wie Internetinformationsdienste handelt, schlägt die Authentifizierung fehl. Dies ist eine\*bekannte Einschränkung der SQL-Netzwerkauthentifizierung und führt zu dem folgenden Fehler: "[Microsoft][ODBC-Treiber für Oracle][Oracle]ORA-12641: TNS:authentication-Dienst konnte nicht initialisiert werden."  
  
 Sie können dieses Problem beheben, indem Sie die Datei Sqlnet.ora bearbeiten. Diese Konfigurationsdatei wird in der Regel im Unterverzeichnis Netzwerk-Admin des Oracle-Home-Verzeichnisses gespeichert. Fügen Sie die folgende Zeile zu Sqlnet.ora hinzu:  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```
