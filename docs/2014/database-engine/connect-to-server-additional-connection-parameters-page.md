---
title: Verbindung mit Server herstellen (Seite „Zusätzliche Verbindungsparameter“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttoserver.options.registeredservers.f1
ms.assetid: ba34b01a-6289-4eb8-8341-fa3d9ec87b3f
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e92fbb8bc29aed54e43925a0670d9a365388df62
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62808671"
---
# <a name="connect-to-server-additional-connection-parameters-page"></a>Verbindung mit Server herstellen (Seite 'Zusätzliche Verbindungsparameter')
  Im Dialogfeld **Verbinden mit** von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] werden die gängigsten Verbindungszeichenfolgenwerte als Optionen angezeigt. Mithilfe der Seite **Zusätzliche Verbindungsparameter** können Sie der Verbindungszeichenfolge weitere Verbindungsparameter hinzufügen.  
  
-   Zusätzliche Verbindungsparameter können beliebige ODBC-Verbindungsparameter sein.  
  
-   Zusätzliche Verbindungsparameter sollten im Format **;Parameter1=Wert1;Parameter2=Wert2**hinzugefügt werden.  
  
-   Parameter, die mithilfe der Seite **Zusätzliche Verbindungsparameter** hinzugefügt werden, werden den Parametern hinzugefügt, die mithilfe der Optionen des Dialogfelds **Verbinden mit** ausgewählt wurden.  
  
-   Durch die letzte Instanz eines Parameters werden alle vorherigen Instanzen des Parameters überschrieben. Parameter, die mithilfe der Seite **Zusätzliche Verbindungsparameter** hinzugefügt werden, orientieren sich an den Parametern, die auf den Registerkarten **Anmeldung** und **Verbindungseigenschaften** bereitgestellt sind, und ersetzen diese. Wird auf der Registerkarte **Anmeldung** beispielsweise **SERVER1** als **Servername**bereitgestellt, und enthält die Seite **Zusätzliche Verbindungsparameter** die Option **;SERVER=SERVER2**, wird die Verbindung mit **SERVER2**hergestellt.  
  
-   Parameter, die mithilfe der Seite **Zusätzliche Verbindungsparameter** hinzugefügt wurden, werden immer als Nur-Text übergeben.  
  
    > [!IMPORTANT]  
    >  Auf der Seite **Zusätzliche Verbindungsparameter** dürfen keine Anmeldeinformationen und Kennwörter eingefügt werden. Sie werden nicht verschlüsselt, wenn sie über das Netzwerk übergeben werden. Verwenden Sie stattdessen die Registerkarte **Anmeldung** .  
  
## <a name="task-list"></a>Aufgabenliste  
  
### <a name="to-show-the-additional-connection-parameters-page"></a>So zeigen Sie die Seite 'Zusätzliche Verbindungsparameter' an  
  
1.  Zeigen Sie in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]im Menü **Abfrage** auf **Verbindung**, und klicken Sie dann auf **Verbinden**.  
  
2.  Klicken Sie im Dialogfeld **Verbinden mit** auf **Optionen**, und klicken Sie dann auf die Registerkarte **Zusätzliche Verbindungsparameter** .  
  
## <a name="examples"></a>Beispiele  
  
### <a name="example-a-connecting-to-the-database-engine"></a>Beispiel A: Herstellen einer Verbindung mit der Datenbank-Engine  
 Um eine Verbindung mit der [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] -Datenbank auf einem Server mit dem Namen ACCOUNTING herzustellen, geben Sie auf der Seite **Zusätzliche Verbindungsparameter** Folgendes ein:  
  
```  
;SERVER=ACCOUNTING;DATABASE=AdventureWorks2012  
```  
  
### <a name="example-b-connecting-to-analysis-services"></a>Beispiel B: Herstellen einer Verbindung mit Analysis Services  
 Um eine Verbindung mit den Analysis-Servern herzustellen und zu bewirken, dass alle Partitionen, die Benachrichtigungen überwachen, in Echtzeit abgefragt werden (wobei das Caching umgangen wird), und den Timeoutwert für das Rückschreiben auf 5 festzulegen, geben Sie auf der Seite **Zusätzliche Verbindungsparameter** Folgendes ein:  
  
```  
;Real Time Olap=TRUE;Writeback Timeout=5  
```  
  
  
