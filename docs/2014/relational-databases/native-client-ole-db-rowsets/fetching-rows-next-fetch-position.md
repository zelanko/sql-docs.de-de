---
title: Nächste Abrufposition | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
ms.assetid: 9ef74b3f-c9c0-492f-9b93-d65738a61abd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2c47f1a8692cf7d2e3fb4f00c64770b3b0c69e5a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63183640"
---
# <a name="next-fetch-position"></a>Nächste Abrufposition
  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter verfolgt die nächste Abrufposition also, die eine Sequenz von Aufrufen an die **GetNextRows** Methode (ohne überspringt, Änderungen der Richtung oder dazwischen liegenden aufruft, um die  **FindNextRow**, **Seek**, oder **RestartPosition** Methoden) das gesamte Rowset liest, ohne zu überspringen oder eine beliebige Zeile wiederholt. Die nächste Abrufposition wird entweder durch Aufrufen von **IRowset::GetNextRows**, **IRowset::RestartPosition** oder **IRowsetIndex::Seek** oder durch Aufrufen von **FindNextRow** mit einem NULL-Wert für *pBookmark* geändert. Das Aufrufen von **FindNextRow** mit einem *pBookmark*-Wert ungleich NULL beeinflusst die nächste Abrufposition nicht.  
  
## <a name="see-also"></a>Siehe auch  
 [Abrufen von Zeilen](fetching-rows.md)  
  
  
