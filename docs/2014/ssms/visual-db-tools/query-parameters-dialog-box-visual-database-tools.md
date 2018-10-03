---
title: Abfrageparameter (Dialogfeld) (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:69645
- vdt.dlgbox.definequeryparameters
ms.assetid: 31cdaee2-d7cd-4d64-a45f-924b27e8b1f0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c726b1a79544af126201f827b18ad4c69113b4b7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48181970"
---
# <a name="query-parameters-dialog-box-visual-database-tools"></a>Abfrageparameter (Dialogfeld) (Visual Database Tools)
  In diesem Dialogfeld können Sie Werte für in der Abfrage definierte Parameter eingeben. Dieses Dialogfeld wird angezeigt, wenn Sie eine Abfrage mit Parametern ausführen, für die eine Eingabe zur Laufzeit durch die Endbenutzer erforderlich ist.  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Listet die Parameter auf, die für die auszuführende Abfrage definiert sind. Wenn die Abfrage benannte Parameter enthält, werden die Namen in der Liste angezeigt. Falls die Abfrage unbenannte Parameter enthält, werden systemdefinierte Namen für die einzelnen Parameter in der Abfrage aufgelistet.  
  
 **Wert**  
 Geben Sie den Wert für jeden Parameter ein, der unter **Name**aufgeführt wird. Der zuletzt verwendete Wert wird als Standardparameterwert angezeigt.  
  
## <a name="example"></a>Beispiel  
 Wenn die folgenden Abfrage im SQL-Bereich in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank ausgeführt wird, wird das Dialogfeld Abfrageparameter geöffnet.  
  
```  
SELECT   FirstName, LastName  
FROM    Person.Person AS Lastname  
WHERE   (LastName = @Param1);  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Abfragen mit Parametern &#40;Visual Database Tools&#41;](visual-database-tools.md)  
  
  
