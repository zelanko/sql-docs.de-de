---
title: Anzeigen und Speichern von Ausführungsplänen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/21/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Showplan results
- execution plans [SQL Server]
- queries [SQL Server], tuning
- execution plans [SQL Server], how-to topics
- SQL Server Management Studio [SQL Server], execution plans
- tuning queries [SQL Server]
ms.assetid: bcd6f094-c613-4835-ae19-4caaadb4bb17
author: julieMSFT
ms.author: jrasnick
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3eb3ec4c2e788bf448a1aea1fced7a06e70c9053
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53358402"
---
# <a name="display-and-save-execution-plans"></a>Anzeigen und Speichern von Ausführungsplänen
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
In diesem Abschnitt erfahren Sie, wie Ausführungspläne mithilfe von Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]angezeigt und in einer Datei im XML-Format gespeichert werden.  
  
Ausführungspläne zeigen grafisch an, welche Datenabrufmethoden vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Abfrageoptimierer gewählt wurden. Ausführungspläne stellen die Ausführungskosten bestimmter Anweisungen und Abfragen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe von Symbolen dar und nicht in der tabellarischen Form, die von den [SET SHOWPLAN_ALL](../../t-sql/statements/set-showplan-all-transact-sql.md)- oder [SET SHOWPLAN_TEXT](../../t-sql/statements/set-showplan-text-transact-sql.md)-Anweisungen erzeugt wird. Durch diese grafische Darstellung sind die Leistungsmerkmale einer Abfrage wesentlich leichter zu verstehen.  

Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Abfrageoptimierer erzeugt nur einen Ausführungsplan. Es gibt jedoch das Konzept des **geschätzten** Ausführungsplans und des **tatsächlichen** Ausführungsplans.
-  Ein [geschätzter Ausführungsplan](../../relational-databases/performance/display-the-estimated-execution-plan.md) gibt den Ausführungsplan so zurück, wie er vom Abfrageoptimierer zur Kompilierzeit erzeugt wird. Das Erzeugen eines geschätzten Ausführungsplans führt die Abfrage oder den Batch nicht aus und enthält deshalb keine Laufzeitinformationen wie die tatsächlichen Nutzungsmetriken der Ressourcen oder Laufzeitwarnungen. 
-  Ein [tatsächlicher Ausführungsplan](../../relational-databases/performance/display-an-actual-execution-plan.md) gibt den Ausführungsplan so zurück, wie er vom Abfrageoptimierer nach der Ausführung von Abfragen und Batches erzeugt wird. Dies schließt Laufzeitinformationen über die Nutzungsmetriken der Ressourcen und Laufzeitwarnungen ein.  

Weitere Informationen zu Abfrageausführungsplänen finden Sie im [Handbuch zur Architektur der Abfrageverarbeitung](../../relational-databases/query-processing-architecture-guide.md).
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Anzeigen des geschätzten Ausführungsplans](../../relational-databases/performance/display-the-estimated-execution-plan.md)  
  
-   [Anzeigen eines tatsächlichen Ausführungsplans](../../relational-databases/performance/display-an-actual-execution-plan.md)  
  
-   [Speichern eines Ausführungsplans im XML-Format](../../relational-databases/performance/save-an-execution-plan-in-xml-format.md)  
  
  
