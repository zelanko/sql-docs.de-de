---
title: QuickInfo (IntelliSense)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Quick Info option [IntelliSense]
- declarations [IntelliSense]
- IntelliSense [SQL Server], Quick Info
- identifier declarations [IntelliSense]
ms.assetid: 3c8b59f4-1922-4bde-844f-5f2306514d96
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9fc27af899dd445f82d081de7c23158217cc7f6a
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75253773"
---
# <a name="quick-info-intellisense"></a>QuickInfo (IntelliSense)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Die Option [!INCLUDE[msCoName](../../includes/msconame-md.md)] IntelliSense **Quick Info** zeigt die vollständige Deklaration für jeden Bezeichner im Code an. Wenn Sie den Mauszeiger über einen Bezeichner bewegen, wird dessen Deklaration in einem gelben Popupfenster angezeigt. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] steht in der Datenbank-Engine und in den XML-Abfrage-Editoren **QuickInfo** zur Verfügung.  
  
## <a name="transact-sql-quick-info"></a>Transact-SQL-QuickInfo  
 Mit**QuickInfo** werden zwei Arten von Informationen im [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor angezeigt. Wenn der Debugmodus nicht aktiv ist, wird mit **QuickInfo** die Ausdrucksdeklaration angezeigt. Wenn der Debugmodus aktiv ist, werden mit **QuickInfo** stattdessen der Name des Ausdrucks sowie der zugehörige aktuelle Wert angezeigt.  
  
 Im [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor steht **Quick Info** nur für die Teile der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Syntax zu Verfügung, die IntelliSense unterstützen. Wenn Sie beispielsweise den Mauszeiger über einen Bezeichner für ein Objekt bewegen, das über einen Datentyp verfügt, der nicht von IntelliSense unterstützt wird, enthält das Popupfenster **Quick Info** eine Meldung, die angibt, dass der Datentyp nicht unterstützt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Von IntelliSense unterstützte Transact-SQL-Syntax](../../relational-databases/scripting/transact-sql-syntax-supported-by-intellisense.md)  
  
  
