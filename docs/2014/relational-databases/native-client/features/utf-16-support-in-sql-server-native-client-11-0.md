---
title: UTF-16-Unterstützung in SQL Server Native Client 11,0 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: f2520424-8ef4-409f-8147-d83da5076e96
author: rothja
ms.author: jroth
ms.openlocfilehash: af8581071400db888fb508b88f8e8ae93bc71f70
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85038998"
---
# <a name="utf-16-support-in-sql-server-native-client-110"></a>Unterstützung für UTF-16 in SQL Server Native Client 11.0
  [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]Wenn Sie ab einen Puffer fester Länge beim Binden eines Spalten Ergebnisses oder Ausgabe Parameters angeben und das Zeichen, das `wchar` vor dem abschließenden Zeichen in den Puffer geschrieben wurde, ein hoher Ersatz Zeichencode Punkt eines Ersatz Zeichen Paars ist, und wenn das nächste `wchar` Zeichen ein niedriger Ersatz Zeichencode Punkt ist, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fügt Native Client dem Puffer keinen hohen Ersatz Zeichencode Punkt hinzu.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client-Funktionen](sql-server-native-client-features.md)  
  
  
