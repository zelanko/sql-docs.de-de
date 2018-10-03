---
title: Cursorbibliotheksvorgänge | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 32e3fcaf9c83c2613a1dc2df499f11c7df2570ad
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692398"
---
# <a name="cursor-library-operations"></a>Cursorbibliotheksvorgänge
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 Wenn eine Anwendung mit einer ODBC 2.*.x* Treiber sendet Aufrufe an die ODBC 3. *X* Cursor-Bibliothek, die Anwendung möglicherweise ODBC 3. *X* Funktionen, die nicht von der ODBC-2 unterstützt werden *.x* Treiber. Anwendungsentwickler Auswahllogik sollten vorsichtig sein, wie diese Features verwendet werden, jedoch wird. Verwenden der ODBC-3. *x* Cursorbibliothek macht nicht zu einer ODBC 2.*.x* Treiber in einer ODBC 3. *X* Treiber.
