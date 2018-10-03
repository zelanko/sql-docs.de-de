---
title: Unterstützung für UTF-16 in SQL Server Native Client 11.0 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: f2520424-8ef4-409f-8147-d83da5076e96
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 415cb2fe8a3295770cfc8bd2d5c6e56750adb6d9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48226720"
---
# <a name="utf-16-support-in-sql-server-native-client-110"></a>Unterstützung für UTF-16 in SQL Server Native Client 11.0
  Ab [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], wenn Sie beim Binden eines Spaltenergebnisses oder Ausgabeparameters einen Puffer fester Länge angeben, und wenn die `wchar` Zeichen, die in den Puffer geschrieben wird, vor das abschließende Zeichen ein hoher Ersatzzeichencodepunkt eines Ersatzzeichenpaars und wenn die nächste `wchar` Zeichen ist ein niedriger Ersatzzeichencodepunkt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client den hohe Ersatzzeichen-Codepunkt in den Puffer wird nicht hinzugefügt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client-Features](sql-server-native-client-features.md)  
  
  
