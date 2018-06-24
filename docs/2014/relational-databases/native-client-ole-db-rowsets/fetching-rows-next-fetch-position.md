---
title: Nächste Abrufposition | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
ms.assetid: 9ef74b3f-c9c0-492f-9b93-d65738a61abd
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 59af82cea07c73f346c4c8add2cd73e3de2444cc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049682"
---
# <a name="next-fetch-position"></a>Nächste Abrufposition
  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter nachverfolgt wird, der die nächste Abrufposition daher, die eine Sequenz von Aufrufen an die **GetNextRows** Methode (ohne überspringt, Änderungen der Richtung oder dazwischen liegende aufruft, um die  **FindNextRow**, **Seek**, oder **RestartPosition** Methoden) das gesamte Rowset liest, ohne überspringen oder eine beliebige Zeile wiederholt. Die nächste Abrufposition wird entweder durch Aufrufen geändert **IRowset:: GetNextRows**, **IRowset:: RestartPosition**, oder **IRowsetIndex:: Seek**, oder durch Aufrufen von **FindNextRow** mit einer Null *pBookmark* Wert. Aufrufen von **FindNextRow** mit einem ungleich NULL *pBookmark* Wert wirkt sich auf die nächste Abrufposition nicht.  
  
## <a name="see-also"></a>Siehe auch  
 [Abrufen von Zeilen](fetching-rows.md)  
  
  