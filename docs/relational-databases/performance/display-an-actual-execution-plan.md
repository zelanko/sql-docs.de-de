---
title: Anzeigen eines tatsächlichen Ausführungsplans | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie tatsächliche grafische Ausführungspläne mithilfe von SQL Server Management Studio generieren. Ein tatsächlicher grafischer Ausführungsplan enthält Laufzeitinformationen.
ms.custom: ''
ms.date: 11/21/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- displaying execution plans
- actual execution plans
- viewing execution plans
- execution plans [SQL Server], displaying
ms.assetid: 9e583a18-5f4a-4054-bfe1-4b2a76630db6
author: julieMSFT
ms.author: jrasnick
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2c1d781e54672263e08daac2101caccfecd8e32e
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2020
ms.locfileid: "86457300"
---
# <a name="display-an-actual-execution-plan"></a>Anzeigen eines tatsächlichen Ausführungsplans
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  In diesem Thema wird das Generieren tatsächlicher grafischer Ausführungspläne mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]beschrieben. Tatsächliche Ausführungspläne werden nach der Ausführung der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Abfragen oder -Batches generiert. Deshalb enthält ein tatsächlicher Ausführungsplan Laufzeitinformationen wie die tatsächlichen Nutzungsmetriken der Ressourcen oder Laufzeitwarnungen (falls vorhanden). Der generierte Ausführungsplan zeigt den tatsächlichen Abfrageausführungsplan an, der von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] zur Ausführung der Abfragen verwendet wurde.  
  
 Benutzer müssen zum Verwenden dieser Funktion die entsprechenden Berechtigungen zum Ausführen der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Abfragen besitzen, für die ein grafischer Ausführungsplan generiert wird. Darüber hinaus muss ihnen die SHOWPLAN-Berechtigung für alle Datenbanken erteilt werden, auf die die Abfrage verweist.  
  
## <a name="to-include-an-execution-plan-for-a-query-during-execution"></a>So schließen Sie einen Ausführungsplan für eine Abfrage bei der Ausführung ein  
  
1.  Klicken Sie auf der Symbolleiste von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] auf **Datenbank-Engine-Abfrage**. Sie können auch eine vorhandene Abfrage öffnen und den geschätzten Ausführungsplan anzeigen, indem Sie auf die Symbolleisten-Schaltfläche **Datei öffnen** klicken und die vorhandene Abfrage suchen. 
  
2.  Geben Sie die Abfrage ein, für die Sie den tatsächlichen Ausführungsplan anzeigen möchten.  
  
3.  Klicken Sie im Menü **Abfrage** auf **Tatsächlichen Ausführungsplan einschließen**, oder klicken Sie auf die Symbolleistenschaltfläche **Tatsächlichen Ausführungsplan einschließen**.

    ![Schaltfläche für den tatsächlichen Ausführungsplan in der Symbolleiste](../../relational-databases/performance/media/actualexecplantoolbar.png "Schaltfläche für den tatsächlichen Ausführungsplan in der Symbolleiste")   
  
4.  Führen Sie die Abfrage aus, indem Sie auf die Symbolleistenschaltfläche **Ausführen** klicken. Der vom Abfrageoptimierer verwendete Plan wird im Ergebnisbereich auf der Registerkarte **Ausführungsplan** angezeigt. 

    ![Tatsächlicher Ausführungsplan](../../relational-databases/performance/media/actualexecplan.png "Tatsächlicher Ausführungsplan")   

5.  Positionieren Sie die Maus über den logischen und physischen Operatoren, um die Beschreibung und Eigenschaften der Operatoren in der angezeigten QuickInfo anzuzeigen, einschließlich der Eigenschaften des gesamten Ausführungsplans, indem Sie den Stammknotenoperator (den SELECT-Knoten in der Abbildung oben) auswählen.   
  
    Sie können die Operatoreigenschaften auch im Eigenschaftenfenster anzeigen. Klicken Sie mit der rechten Maustaste auf einen Operator, und klicken Sie auf **Eigenschaften**, wenn die Eigenschaften nicht sichtbar sind. Wählen Sie einen Operator aus, um seine Eigenschaften anzuzeigen.  

    ![Rechtsklick, „Eigenschaften“ im Planoperator](../../relational-databases/performance/media/planproperties.png "Rechtsklick, „Eigenschaften“ im Planoperator")    
  
6.  Sie können die Anzeige des Ausführungsplans ändern, indem Sie mit der rechten Maustaste auf den Ausführungsplan klicken und **Vergrößern**, **Verkleinern**, **Vergrößern/Verkleinern**oder **Zoom anpassen**auswählen. Mit**Vergrößern** und **Verkleinern** können Sie den Ausführungsplan vergrößern bzw. verkleinern. Mit **Vergrößern/Verkleinern** können Sie dagegen einen eigenen Zoomfaktor definieren, z. B. 80 Prozent. Mit**Zoom anpassen** können Sie den Ausführungsplan an die Größe des Ergebnisbereichs anpassen. Verwenden Sie alternativ eine Kombination aus der STRG-Taste und Ihrem Mausrad, um den **dynamischen Zoom** zu aktivieren.  

7.  Um in der Anzeige des Ausführungsplans zu navigieren, verwenden Sie die vertikalen und horizontalen Scrollleisten, oder **klicken Sie in einem beliebigen leeren Bereich** des Ausführungsplans, und halten Sie die Maustaste gedrückt, und **ziehen Sie die Maus**. Alternativ können Sie auch auf das Pluszeichen (+) in der rechten unteren Ecke des Ausführungsplanfensters klicken und die Maustaste gedrückt halten, um eine Miniaturansicht des gesamten Ausführungsplans anzuzeigen.

> [!NOTE] 
> Verwenden Sie alternativ [SET STATISTICS XML](../../t-sql/statements/set-statistics-xml-transact-sql.md), um Informationen zum Ausführungsplan an jede Anweisung nach deren Ausführung zurückzugeben. Bei der Verwendung in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verfügt die Registerkarte *Ergebnisse* über einen Link, der den Ausführungsplan im grafischen Format öffnet.   
> Weitere Informationen finden Sie unter [Profilerstellungsinfrastruktur für Abfragen](../../relational-databases/performance/query-profiling-infrastructure.md).
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführungspläne](../../relational-databases/performance/execution-plans.md)    
 [Handbuch zur Architektur der Abfrageverarbeitung](../../relational-databases/query-processing-architecture-guide.md)  
