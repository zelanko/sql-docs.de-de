---
title: Cursorbibliotheksoperationen | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301617"
---
# <a name="cursor-library-operations"></a>Cursorbibliotheksvorgänge
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 Wenn eine Anwendung, die mit einem ODBC *2.x-Treiber* arbeitet, Aufrufe an die ODBC *3.x-Cursorbibliothek* ausführt, kann die Anwendung möglicherweise ODBC *3.x-Funktionen* verwenden, die vom ODBC *2.x-Treiber* nicht unterstützt werden. Ein Anwendungsschreiber sollte jedoch vorsichtig sein, wie diese Features verwendet werden. Durch die Verwendung der ODBC *3.x-Cursorbibliothek* wird kein ODBC *2.x-Treiber* zu einem ODBC *3.x-Treiber.*
