---
description: Abfrageparameter (Dialogfeld) (Visual Database Tools)
title: Dialogfeld „Abfrageparameter“
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:69645
- vdt.dlgbox.definequeryparameters
ms.assetid: 31cdaee2-d7cd-4d64-a45f-924b27e8b1f0
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: ea62b4a278ca2f6b6c272f404d8446973fa51680
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88313956"
---
# <a name="query-parameters-dialog-box-visual-database-tools"></a>Abfrageparameter (Dialogfeld) (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
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
  
## <a name="see-also"></a>Weitere Informationen  
[Erstellen von Abfragen mit Parametern &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-with-parameters-visual-database-tools.md)  
  
