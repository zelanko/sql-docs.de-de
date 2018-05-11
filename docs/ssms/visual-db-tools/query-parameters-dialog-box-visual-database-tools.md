---
title: Abfrageparameter (Dialogfeld) (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:69645
- vdt.dlgbox.definequeryparameters
ms.assetid: 31cdaee2-d7cd-4d64-a45f-924b27e8b1f0
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a5b688934e40c8d5d61d46ac500bd9e8c8632afb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="query-parameters-dialog-box-visual-database-tools"></a>Abfrageparameter (Dialogfeld) (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
In diesem Dialogfeld können Sie Werte für in der Abfrage definierte Parameter eingeben. Dieses Dialogfeld wird angezeigt, wenn Sie eine Abfrage mit Parametern ausführen, für die eine Eingabe zur Laufzeit durch die Endbenutzer erforderlich ist.  
  
## <a name="options"></a>Optionen  
**Name**  
Listet die Parameter auf, die für die auszuführende Abfrage definiert sind. Wenn die Abfrage benannte Parameter enthält, werden die Namen in der Liste angezeigt. Falls die Abfrage unbenannte Parameter enthält, werden systemdefinierte Namen für die einzelnen Parameter in der Abfrage aufgelistet.  
  
**ReplTest1**  
Geben Sie den Wert für jeden Parameter ein, der unter **Name**aufgeführt wird. Der zuletzt verwendete Wert wird als Standardparameterwert angezeigt.  
  
## <a name="example"></a>Beispiel  
Wenn die folgenden Abfrage im SQL-Bereich in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject_md.md)] -Datenbank ausgeführt wird, wird das Dialogfeld Abfrageparameter geöffnet.  
  
```  
SELECT   FirstName, LastName  
FROM    Person.Person AS Lastname  
WHERE   (LastName = @Param1);  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Erstellen von Abfragen mit Parametern &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-with-parameters-visual-database-tools.md)  
  
