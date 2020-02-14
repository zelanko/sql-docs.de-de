---
title: Anzeigen des geschätzten Ausführungsplans | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/21/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- zoom [SQL Server]
- estimated execution plan [SQL Server]
- displaying execution plans
- viewing execution plans
- execution plans [SQL Server], displaying
- customizing execution plan display [SQL Server]
- modifying execution plan display
- custom zoom [SQL Server]
ms.assetid: e94aa576-4c0c-4c54-ad05-6c3432cc615b
author: julieMSFT
ms.author: jrasnick
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4d0d5930734bb48c0914300a735f81e3ca2ced38
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "67946866"
---
# <a name="display-the-estimated-execution-plan"></a>Anzeigen des geschätzten Ausführungsplans
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  In diesem Thema wird das Generieren grafischer geschätzter Ausführungspläne mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]beschreiben. Beim Generieren von geschätzten Ausführungsplänen werden die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Abfragen oder -Batches nicht ausgeführt. Deshalb enthält ein geschätzter Ausführungsplan keine Laufzeitinformationen wie die tatsächlichen Nutzungsmetriken der Ressourcen oder Laufzeitwarnungen. Stattdessen zeigt der generierte Ausführungsplan den Abfrageausführungsplan an, den [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] bei tatsächlicher Ausführung der Abfragen mit größter Wahrscheinlichkeit verwenden würde sowie die geschätzten Reihen, die durch die Operatoren im Plan fließen.  
  
 Zum Verwenden dieser Funktion müssen die Benutzer die entsprechenden Berechtigungen haben, um die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Abfrage auszuführen, für die ein grafischer Ausführungsplan generiert wird. Den Benutzern muss auch die SHOWPLAN-Berechtigung für alle Datenbanken erteilt werden, auf die die Abfrage verweist.  
  
## <a name="to-display-the-estimated-execution-plan-for-a-query"></a>So zeigen Sie den geschätzten Ausführungsplan für eine Abfrage an  
  
1.  Klicken Sie auf der Symbolleiste auf **Datenbank-Engine-Abfrage**. Sie können auch eine vorhandene Abfrage öffnen und den geschätzten Ausführungsplan anzeigen, indem Sie auf die Symbolleisten-Schaltfläche **Datei öffnen** klicken und die vorhandene Abfrage suchen.  
  
2.  Geben Sie die Abfrage, für die Sie den geschätzten Ausführungsplan anzeigen möchten, ein.  
  
3.  Klicken Sie im Menü **Abfrage** auf **Geschätzten Ausführungsplan anzeigen** , oder klicken Sie auf die Symbolleisten-Schaltfläche **Geschätzten Ausführungsplan anzeigen** . Der geschätzte Ausführungsplan wird im Ergebnisbereich auf der Registerkarte **Ausführungsplan** angezeigt. 

    ![Schaltfläche für den geschätzten Ausführungsplan in der Symbolleiste](../../relational-databases/performance/media/estimatedexecplantoolbar.png "Schaltfläche für den geschätzten Ausführungsplan in der Symbolleiste")    

    Um weitere Informationen anzuzeigen, lassen Sie den Mauszeiger über den logischen und physischen Operatorsymbolen ruhen. Die Beschreibung und die Eigenschaften des Operators werden nun in der QuickInfo angezeigt. Sie können die Operatoreigenschaften auch im Eigenschaftenfenster anzeigen. Klicken Sie mit der rechten Maustaste auf einen Operator, und klicken Sie auf **Eigenschaften**, wenn die Eigenschaften nicht sichtbar sind. Wählen Sie einen Operator aus, um seine Eigenschaften anzuzeigen.  

    ![Rechtsklick auf „Eigenschaften“ im Planoperator](../../relational-databases/performance/media/planproperties.png "Rechtsklick auf „Eigenschaften“ im Planoperator")    
  
4.  Um die Anzeige des Ausführungsplans zu ändern, klicken Sie mit der rechten Maustaste auf den Ausführungsplan, und wählen Sie **Vergrößern**, **Verkleinern**, **Vergrößern/Verkleinern**oder **Zoom anpassen**aus. Mit**Vergrößern** und **Verkleinern** können Sie den Ausführungsplan in festgelegten Schritten vergrößern oder verkleinern. **Vergrößern/Verkleinern** ermöglicht Ihnen, die Anzeigevergrößerung nach Wunsch festzulegen, etwa auf 80 Prozent. Mit**Zoom anpassen** können Sie den Ausführungsplan an die Größe des Ergebnisbereichs anpassen. Verwenden Sie alternativ eine Kombination aus der STRG-Taste und Ihrem Mausrad, um den **dynamischen Zoom** zu aktivieren.  

5.  Um in der Anzeige des Ausführungsplans zu navigieren, verwenden Sie die vertikalen und horizontalen Scrollleisten, oder **klicken Sie in einem beliebigen leeren Bereich** des Ausführungsplans, und halten Sie die Maustaste gedrückt, und **ziehen Sie die Maus**. Alternativ können Sie auch auf das Pluszeichen (+) in der rechten unteren Ecke des Ausführungsplanfensters klicken und die Maustaste gedrückt halten, um eine Miniaturansicht des gesamten Ausführungsplans anzuzeigen.
 
> [!NOTE] 
> Verwenden Sie alternativ [SET SHOWPLAN_XML](../../t-sql/statements/set-showplan-xml-transact-sql.md), um Informationen zum Ausführungsplan jeder Anweisung zurückzugeben, ohne diese ausführen zu müssen. Bei der Verwendung in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verfügt die Registerkarte *Ergebnisse* über einen Link, der den Ausführungsplan im grafischen Format öffnet.   
