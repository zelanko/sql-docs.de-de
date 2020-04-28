---
title: Cursor Bibliotheks Vorgänge | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], backward compatibility
- compatibility [ODBC], cursor library
- upgrading applications [ODBC], cursor library
- application upgrades [ODBC], cursor library
- backward compatibility [ODBC], cursor library
- cursor library [ODBC], backward compatibility
ms.assetid: 04d514b1-dc4d-4b84-bf35-60f4657ef1f6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a2297e72aacad7ea91b7af934a47bebbc61f0686
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301617"
---
# <a name="cursor-library-operations"></a>Cursorbibliotheksvorgänge
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 Wenn eine Anwendung, die mit einem ODBC *2. x* -Treiber arbeitet, Aufrufe an die ODBC *3. x* -Cursor Bibliothek durchführt, kann die Anwendung möglicherweise ODBC *3. x* -Funktionen verwenden, die nicht vom ODBC *2. x* -Treiber unterstützt werden. Ein anwendungswriter sollte jedoch darauf achten, dass diese Features verwendet werden. Die Verwendung der ODBC *3. x* -Cursor Bibliothek macht keinen ODBC *2. x* -Treiber in einen ODBC *3. x* -Treiber.
