---
title: Abschließen von Transact-SQL-Ausschnitten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [SQL Server], completing snippets
- snippets [Transact-SQL], completing
- Transact-SQL snippets, completing
ms.assetid: a8316a58-bb57-485e-845f-84c23360314c
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 198699516b4246f171bbd7a5c3f3fe2d5124b04d
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/14/2018
ms.locfileid: "51643330"
---
# <a name="complete-transact-sql-snippets"></a>Abschließen von Transact-SQL-Ausschnitten
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Sobald ein [!INCLUDE[tsql](../../includes/tsql-md.md)] -Codeausschnitt in ein Skript eingefügt wurde, bearbeiten Sie den Inhalt des Ausschnitts, um eine vollständige [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung zu erstellen.  
  
## <a name="completing-snippets"></a>Vervollständigen von Ausschnitten  
 Wenn Sie dem Skript einen [!INCLUDE[tsql](../../includes/tsql-md.md)] -Ausschnitt hinzufügen, enthält die eingefügte Ausschnittanweisung einen oder mehrere Ersetzungspunkte, die hervorgehoben werden. Wenn Sie mit der Maus auf einen Ersetzungspunkt zeigen, wird eine QuickInfo mit einer Beschreibung des Syntaxelements angezeigt, das Sie angeben können. Der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor erkennt den Ausschnitt als vom umgebenden Skript separaten Code, bis Sie die Quelldatei schließen. Die Ersetzungspunkte bleiben aktiv, bis Sie die Quelldatei schließen.  
  
 Sie können auch dem durch einen Ausschnitt eingefügten Vorlagencode zusätzliche Syntaxelemente hinzufügen. Beispielsweise werden mit der Ausschnittvorlage Tabelle erstellen zwei Spaltendefinitionen hinzugefügt. Sie müssen weitere Spaltendefinitionen hinzufügen, um eine Tabelle mit mehr als zwei Spalten zu erstellen.  
  
#### <a name="completing-the-snippet-statement"></a>Vervollständigen der Ausschnittanweisung  
  
1.  Wechseln Sie mithilfe der TAB-TASTE von einem Ersetzungspunkt zum nächsten Ersetzungspunkt. Mit UMSCHALT+TAB wechseln Sie zum vorherigen Ersetzungspunkt.  
  
2.  Drücken Sie STRG+LEERTASTE, um IntelliSense aufzurufen.  
  
3.  Wählen Sie aus der Liste ein Element aus, oder geben Sie eine gewünschte Ersetzung ein.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Einfügen von Transact-SQL-Ausschnitten](../../relational-databases/scripting/insert-transact-sql-snippets.md)   
 [Einfügen von Transact-SQL-Umschließungsausschnitten](../../relational-databases/scripting/insert-surround-with-transact-sql-snippets.md)  
  
  
