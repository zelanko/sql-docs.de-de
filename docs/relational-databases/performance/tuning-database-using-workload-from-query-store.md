---
title: Datenbankoptimierung mithilfe der Arbeitsauslastung aus dem Abfragespeicher | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Database Engine Tuning Advisor, Query Store
ms.assetid: 17107549-5073-4fa2-8ee7-5ed33b38821e
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: 15f9bb429509f64909888883a718325b76efae27
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63013675"
---
# <a name="tuning-database-using-workload-from-query-store"></a>Datenbankoptimierung mithilfe der Arbeitsauslastung aus dem Abfragespeicher
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]


Die Funktion [Abfragespeicher](../../relational-databases/performance/how-query-store-collects-data.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erfasst automatisch einen Verlauf der Abfragen, Pläne und Laufzeitstatistiken und speichert diese Informationen in der Datenbank. Der [Datenbankoptimierungsratgeber (Database Engine Tuning Advisor, DTA)](../../relational-databases/performance/database-engine-tuning-advisor.md) unterstützt eine neue Option, bei der man den Abfragespeicher verwenden kann, um automatisch eine entsprechende Arbeitsauslastung für die Optimierung auszuwählen. Viele Benutzer müssen dadurch nicht mehr explizit eine Arbeitsauslastung für die Optimierung erfassen. Diese Funktion ist nur verfügbar, wenn in der Datenbank die Abfragespeicherfunktion aktiviert ist. 
  
Diese Funktion ist mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **v16.4** oder höher verfügbar. 
  
## <a name="how-to-tune-a-workload-from-query-store-in-database-engine-tuning-advisor-gui"></a>So optimieren Sie eine Arbeitsauslastung aus dem Abfragespeicher in der GUI des Datenbankoptimierungsratgebers
Wählen Sie über die DTA GUI das Optionsfeld **Abfragespeicher** im Bereich **Allgemein** aus, um diese Funktion zu aktivieren (siehe folgende Abbildung).

![DTA-Workload aus Abfragespeicher](../../relational-databases/performance/media/dta-workload-from-query-store.gif)
 
## <a name="how-to-tune-a-workload-from-query-store-in-dtaexe-command-line-utility"></a>So optimieren Sie eine Arbeitsauslastung aus dem Abfragespeicher im Befehlszeilenprogramm „dta.exe“
Wählen Sie aus der Befehlszeile („dta.exe“) die Option **-iq** aus, um die Arbeitsauslastung aus dem Abfragespeicher auszuwählen. 

Es stehen zwei zusätzliche Optionen über die Befehlszeile zur Verfügung, über die Sie das Verhalten von DTA bei der Auswahl der Arbeitsauslastung aus dem Abfragespeicher optimieren können. Folgende Optionen sind nicht über die GUI verfügbar:
  1. **Anzahl der zu optimierenden Workloadereignisse:** Diese Option, die mithilfe des Befehlszeilenarguments **-n** angegeben wird, ermöglicht Benutzern die Kontrolle darüber, wie viele Ereignisse aus dem Abfragespeicher optimiert werden. Standardmäßig verwendet DTA einen Wert von 1000 für diese Option. DTA wählt immer die ressourcenintensivsten Ereignisse nach Gesamtdauer aus. 
  
  2. **Zeitfenster der zu optimierenden Ereignisse:** Da der Abfragespeicher möglicherweise Abfragen enthält, die vor langer Zeit ausgeführt wurden, ermöglicht diese Option dem Benutzer das Angeben eines vergangenen Zeitfensters (in Stunden), in dem eine Abfrage ausgeführt worden sein muss, damit sie von DTA für die Optimierung berücksichtigt wird. Diese Option wird mithilfe des Befehlszeilenarguments **-I** angegeben. 

Weitere Informationen finden Sie unter [dta Utility](../../tools/dta/dta-utility.md).

## <a name="difference-between-using-workload-from-query-store-and-plan-cache"></a>Unterschied zwischen der Verwendung der Arbeitsauslastung aus dem Abfragespeicher und Plancache 
Der Unterschied zwischen den Optionen „Abfragespeicher“ und „Plancache“ liegt darin, dass ersterer einen langen Verlauf von Abfragen enthält, die in der Datenbank ausgeführt wurden und zwischen Serverneustarts beibehalten werden. Der Plancache enthält dagegen nur eine Teilmenge von kürzlich ausgeführten Abfragen, deren Pläne im Arbeitsspeicher zwischengespeichert werden. Wenn der Server neu gestartet wird, werden die Einträge im Plancache gelöscht.

## <a name="see-also"></a>Weitere Informationen  
[Datenbankoptimierungsratgeber](../../relational-databases/performance/database-engine-tuning-advisor.md)     
[Tutorial: Database Engine Tuning Advisor (Tutorial: Datenbankoptimierungsratgeber)](../../tools/dta/tutorial-database-engine-tuning-advisor.md)        
[So werden Daten im Abfragespeicher gesammelt](../../relational-databases/performance/how-query-store-collects-data.md)     
[Abfragespeicher, bewährte Methoden](../../relational-databases/performance/best-practice-with-the-query-store.md)
