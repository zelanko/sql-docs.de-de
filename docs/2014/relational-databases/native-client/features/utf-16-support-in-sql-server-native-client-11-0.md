---
title: UTF-16-Unterstützung in SQL Server Native Client 11,0 | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63205114"
---
# <a name="utf-16-support-in-sql-server-native-client-110"></a>Unterstützung für UTF-16 in SQL Server Native Client 11.0
  [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]Wenn Sie ab einen Puffer fester Länge beim Binden eines Spalten Ergebnisses oder Ausgabe Parameters angeben und das `wchar` Zeichen, das vor dem abschließenden Zeichen in den Puffer geschrieben wurde, ein hoher Ersatz Zeichencode Punkt eines Ersatz Zeichen Paars ist, und wenn das `wchar` nächste Zeichen ein niedriger Ersatz Zeichencode Punkt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ist, fügt Native Client dem Puffer keinen hohen Ersatz Zeichencode Punkt hinzu.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client-Funktionen](sql-server-native-client-features.md)  
  
  
