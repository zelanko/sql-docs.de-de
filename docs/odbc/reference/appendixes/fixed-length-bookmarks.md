---
title: Lesezeichen mit fester Länge | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], bookmarks
- bookmarks [ODBC]
- compatibility [ODBC], bookmarks
- fixed-length bookmarks [ODBC]
ms.assetid: cbd8185e-fb03-408f-b80b-1a2e164534fd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f90c5888a68506c056b2a56fce516080148528e7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306981"
---
# <a name="fixed-length-bookmarks"></a>Textmarke mit fester Länge
Wenn ein ODBC *3. x* -Treiber mit einer ODBC *2. x* -Anwendung verwendet werden soll, die Lesezeichen mit fester Länge verwendet, muss der Treiber Folgendes unterstützen:  
  
-   SQL_UB_ON als Wert für die Option SQL_USE_BOOKMARKS Anweisung aus. (SQL_UB_ON in ODBC *3. x*als veraltet markiert.)  
  
-   Die SQL_GET_BOOKMARK Anweisungs Option.
