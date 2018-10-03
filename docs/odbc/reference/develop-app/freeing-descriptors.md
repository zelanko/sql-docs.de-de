---
title: Freigeben von Deskriptoren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFreeHandle function [ODBC]
- descriptors [ODBC], allocating and freeing
- freeing descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 317213f4-0ebb-4bf8-a37a-4d6b1313823f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d643ccad0110796127524a10e82aef7c3339b163
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47694628"
---
# <a name="freeing-descriptors"></a>Freigeben von Deskriptoren
Explizit zugewiesene Deskriptoren können werden freigegeben, entweder explizit durch Aufrufen von **SQLFreeHandle** mit *HandleType* SQL_HANDLE_DESC oder implizit, wenn das Verbindungshandle freigegeben. Wenn ein explizit zugewiesene Deskriptor freigegeben wird, alle Anweisungshandles auf die freigegebene Deskriptor automatisch angewendet, die implizit für sie reservierten Deskriptoren wiederherstellen.  
  
 Implizit zugewiesene Deskriptoren freigegeben werden können, nur durch das Aufrufen **SQLDisconnect**, die löscht alle Anweisungen oder zum Öffnen von Deskriptoren für die Verbindung oder durch Aufrufen von **SQLFreeHandle** mit einem  *HandleType* von SQL_HANDLE_STMT auf, um ein Anweisungshandle und alle der Anweisung zugeordneten implizit zugewiesenen Deskriptoren freizugeben. Ein implizit zugewiesene Deskriptor nicht freigegeben werden, durch den Aufruf **SQLFreeHandle** mit einem *HandleType* von SQL_HANDLE_DESC.  
  
 Auch wenn freigegeben, ein implizit zugewiesene Deskriptor gültig bleibt, und **SQLGetDescField** ihren Feldern aufgerufen werden kann.
