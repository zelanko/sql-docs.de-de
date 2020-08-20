---
description: Verwenden der Betriebssystemauthentifizierung
title: Verwenden der Betriebs System Authentifizierung | Microsoft-Dokumentation
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
ms.openlocfilehash: 94563fee00c979addb6fc088bfb3881763e4d188
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471322"
---
# <a name="using-operating-system-authentication"></a>Verwenden der Betriebssystemauthentifizierung
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Die Oracle-Betriebssystem Authentifizierung basiert auf dem zugrunde liegenden Betriebssystem, um den Zugriff auf Daten Bankkonten zu steuern. Benutzer müssen kein Kennwort eingeben, wenn Sie diese Art von Anmeldung verwenden.  
  
 Um dieses Feature nutzen zu können, geben Sie "/" als Benutzer-ID an, und geben Sie kein Kennwort an, wenn Sie eine Verbindung mithilfe einer der folgenden Verbindungs-APIs herstellen: [sqlbrowseconnetct](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md), [SQLCONNECT](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md)oder [SQLDriverConnect](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md).  
  
 Oracle-Datenbanken verwenden SQL * Net Authentication-Dienste, um angemeldete Benutzer zu authentifizieren. Dieser Dienst funktioniert gut, wenn Benutzer über sqlplus bei Oracle angemeldet sind. Wenn der angemeldete Benutzer jedoch ein Dienst ist, z. b. Internetinformationsdienste, schlägt die Authentifizierung fehl. Dies ist eine bekannte Einschränkung der SQL \* -Netzwerk Authentifizierung und erzeugt den folgenden Fehler: "[Microsoft] [ODBC Driver for Oracle] [Oracle] Ora-12641: TNS: der Authentifizierungsdienst konnte nicht initialisiert werden."  
  
 Sie können dieses Problem beheben, indem Sie die Datei "SQLnet. Ora" bearbeiten. Diese Konfigurationsdatei wird in der Regel im Unterverzeichnis network\admin des Oracle-Basisverzeichnisses gespeichert. Fügen Sie SQLnet. ora die folgende Zeile hinzu:  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```
