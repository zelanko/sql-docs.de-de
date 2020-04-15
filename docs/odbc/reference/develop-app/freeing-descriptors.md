---
title: Freiwerden von Deskriptoren | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305601"
---
# <a name="freeing-descriptors"></a>Freigeben von Deskriptoren
Explizit zugewiesene Deskriptoren können entweder explizit freigegeben werden, indem **SQLFreeHandle** mit *HandleType* von SQL_HANDLE_DESC aufgerufen wird, oder implizit, wenn das Verbindungshandle freigegeben wird. Wenn ein explizit zugewiesener Deskriptor freigegeben wird, werden alle Anweisungshandles, auf die der angewendete freigegebene Deskriptor angewendet wurde, automatisch auf die deskriptoren zurückgesetzt, die ihnen implizit zugewiesen wurden.  
  
 Implizit zugewiesene Deskriptoren können nur durch Aufrufen von **SQLDisconnect**freigegeben werden, das alle Anweisungen oder Deskriptoren löscht, die für die Verbindung geöffnet sind, oder indem **SQLFreeHandle** mit einem *HandleType* von SQL_HANDLE_STMT aufgerufen wird, um ein Anweisungshandle und alle implizit zugewiesenen Deskriptoren freizugeben, die der Anweisung zugeordnet sind. Ein implizit zugewiesener Deskriptor kann nicht durch Aufrufen von **SQLFreeHandle** mit einem *HandleType* von SQL_HANDLE_DESC freigegeben werden.  
  
 Selbst wenn diese freigegeben ist, bleibt ein implizit zugewiesener Deskriptor gültig, und **SQLGetDescField** kann für seine Felder aufgerufen werden.
