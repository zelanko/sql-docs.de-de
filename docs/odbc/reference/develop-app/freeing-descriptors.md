---
description: Freigeben von Deskriptoren
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
ms.openlocfilehash: 95c87b7ac70369509a72ff539c63ac888e5f3262
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465802"
---
# <a name="freeing-descriptors"></a>Freigeben von Deskriptoren
Explizit zugeordnete Deskriptoren können entweder explizit freigegeben werden, indem **SQLFreeHandle** mit dem *Handlertyp* SQL_HANDLE_DESC aufgerufen wird, oder implizit, wenn das Verbindungs Handle freigegeben wird. Wenn ein explizit zugeordneter Deskriptor freigegeben wird, werden alle Anweisungs Handles, auf die der freigegebene Deskriptor angewendet wird, automatisch auf die Deskriptoren zurückgesetzt, die Ihnen implizit zugeordnet  
  
 Implizit zugeordnete Deskriptoren können nur durch Aufrufen von **SQLDisconnect**freigegeben werden, wodurch alle in der Verbindung geöffneten Anweisungen oder Deskriptoren gelöscht werden, oder durch Aufrufen von **SQLFreeHandle** mit dem *Handlertyp* SQL_HANDLE_STMT, um ein Anweisungs Handle und alle implizit zugeordneten Deskriptoren, die der Anweisung zugeordnet sind, freizugeben. Ein implizit zugeordneter Deskriptor kann nicht freigegeben werden, indem **SQLFreeHandle** mit dem *Typ* "SQL_HANDLE_DESC" aufgerufen wird.  
  
 Auch wenn freigegeben, bleibt ein implizit zugeordneter Deskriptor gültig, und **SQLGetDescField** kann für seine Felder aufgerufen werden.
