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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: af30ceb29e032764b89aa2069086aa898a7d35db
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305601"
---
# <a name="freeing-descriptors"></a>Freigeben von Deskriptoren
Explizit zugeordnete Deskriptoren können entweder explizit freigegeben werden, indem **SQLFreeHandle** mit dem *Handlertyp* SQL_HANDLE_DESC aufgerufen wird, oder implizit, wenn das Verbindungs Handle freigegeben wird. Wenn ein explizit zugeordneter Deskriptor freigegeben wird, werden alle Anweisungs Handles, auf die der freigegebene Deskriptor angewendet wird, automatisch auf die Deskriptoren zurückgesetzt, die Ihnen implizit zugeordnet  
  
 Implizit zugeordnete Deskriptoren können nur durch Aufrufen von **SQLDisconnect**freigegeben werden, wodurch alle in der Verbindung geöffneten Anweisungen oder Deskriptoren gelöscht werden, oder durch Aufrufen von **SQLFreeHandle** mit dem *Handlertyp* SQL_HANDLE_STMT, um ein Anweisungs Handle und alle implizit zugeordneten Deskriptoren, die der Anweisung zugeordnet sind, freizugeben. Ein implizit zugeordneter Deskriptor kann nicht freigegeben werden, indem **SQLFreeHandle** mit dem *Typ* "SQL_HANDLE_DESC" aufgerufen wird.  
  
 Auch wenn freigegeben, bleibt ein implizit zugeordneter Deskriptor gültig, und **SQLGetDescField** kann für seine Felder aufgerufen werden.
