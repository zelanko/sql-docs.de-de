---
title: Suchen von Text mit Platzhaltern
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- vswildcardsbuilder
helpviewer_keywords:
- searches [SQL Server Management Studio], wildcards
- Query Editor [SQL Server Management Studio], wildcard searches
- wildcard options [SQL Server Management Studio]
ms.assetid: 449600f8-cc87-4b3f-878a-59c158a88a40
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 766bb8d9a90fb3f1af5a7697e52ae42f6c8fc8d7
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75253623"
---
# <a name="search-text-with-wildcards"></a>Suchen von Text mit Platzhaltern
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Mit den folgenden Ausdrücken lassen sich Zeichen oder Ziffern im Feld **Suchen nach** im Dialogfeld [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]Suchen und Ersetzen**in** ersetzen.  
  
#### <a name="to-search-using-wildcards"></a>So suchen Sie mit Platzhaltern  
  
1.  Um die Verwendung von Platzhaltern im Feld **Suchen nach** bei der Schnellsuche, **In Dateien suchen**, **Schnellersetzung**oder **In Dateien ersetzen** zu aktivieren, wählen Sie unter **Suchoptionen** nacheinander **Verwenden** und dann **Platzhalter**aus.  
  
2.  Die dreieckige Schaltfläche für die **Verweisliste** neben dem Feld **Suchen nach** ist jetzt aktiviert. Klicken Sie auf diese Schaltfläche, um eine Liste der verfügbaren Platzhalter anzuzeigen. Wenn Sie ein Element aus der Liste für die **Verweisliste** auswählen, wird es in die **Suchen nach** -Zeichenfolge eingefügt.  
  
 Die folgende Tabelle enthält eine Beschreibung der Platzhalter, die unter **Verweisliste**verfügbar sind.  
  
|Ausdruck|Syntax|BESCHREIBUNG|  
|----------------|------------|-----------------|  
|Ein einzelnes Zeichen|?|Entspricht einem beliebigen einzelnen Zeichen.|  
|Eine einzelne Ziffer|#|Entspricht einer beliebigen einzelnen Ziffer. Beispiel: 7# entspricht Zahlen, die aus einer 7 bestehen, gefolgt von einer anderen Zahl, wie 71, nicht aber 17.|  
|Zeichen außerhalb des Zeichensatzes|[! ]|Entspricht einem einzelnen Zeichen, das nicht im Zeichensatz angegeben ist.|  
|Ein oder mehrere Zeichen|*|Entspricht einem oder mehreren Zeichen. Beispiel: new* entspricht einem beliebigen Text mit der Buchstabenfolge "new", z. B. newfile.txt.|  
|Zeichensatz|[ ]|Entspricht einem einzelnen Zeichen, das im Zeichensatz angegeben ist.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Suchen und Ersetzen](../../relational-databases/scripting/search-and-replace.md)   
 [Suchen von Text mit regulären Ausdrücken](../../relational-databases/scripting/search-text-with-regular-expressions.md)  
