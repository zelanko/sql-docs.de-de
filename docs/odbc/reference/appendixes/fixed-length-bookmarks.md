---
title: Feste Länge Lesezeichen | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306981"
---
# <a name="fixed-length-bookmarks"></a>Textmarke mit fester Länge
Wenn ein ODBC *3.x-Treiber* mit einer ODBC *2.x-Anwendung* arbeiten soll, die Lesezeichen mit fester Länge verwendet, muss der Treiber Folgendes unterstützen:  
  
-   SQL_UB_ON als Wert für die SQL_USE_BOOKMARKS-Anweisungsoption. (SQL_UB_ON ist in ODBC *3.x*veraltet.)  
  
-   Die SQL_GET_BOOKMARK Anweisungsoption.
