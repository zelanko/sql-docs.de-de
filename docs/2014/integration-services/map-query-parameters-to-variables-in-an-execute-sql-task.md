---
title: Zuordnen von Abfrage Parametern zu Variablen in einem Task "SQL ausführen" | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- queries [Integration Services], parameter mapping
- parameterized SQL commands [Integration Services]
- parameters [Integration Services]
- mapping query parameters to variables [Integration Services]
- Execute SQL task [Integration Services]
- variables [Integration Services], mapping parameters to
ms.assetid: 6a164349-dfcf-4995-80bc-d4e7aee52a83
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b2e105e2ccccce912965cbfc0662a380ea1a6264
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85440267"
---
# <a name="map-query-parameters-to-variables-in-an-execute-sql-task"></a>Zuordnen von Abfrageparametern zu Variablen in einem Task SQL ausführen

  In diesem Thema wird beschrieben, wie Sie eine parametrisierte SQL-Anweisung im Task 'SQL ausführen' verwenden und wie Sie Zuordnungen zwischen Variablen und den Parametern der SQL-Anweisung erstellen.  
  
 Weitere Informationen zum Task SQL ausführen, zu den Parametermarkierungen und den Parameternamen, die Sie mit verschiedenen Verbindungstypen verwenden, finden Sie unter [SQL ausführen (Task)](control-flow/execute-sql-task.md) und [Parameter und Rückgabecodes im Task „SQL ausführen“](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).  
  
### <a name="to-map-a-query-parameter-to-a-variable"></a>So ordnen Sie einer Variablen einen Abfrageparameter zu  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das gewünschte [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Ablaufsteuerung** .  
  
4.  Wenn das Paket noch keinen Task SQL ausführen enthält, fügen Sie der Ablaufsteuerung des Pakets einen solchen Task hinzu. Weitere Informationen finden Sie unter [Hinzufügen oder Löschen eines Tasks oder Containers in einer Ablauf Steuerung](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md) .  
  .  
  
5.  Doppelklicken Sie auf den Task SQL ausführen.  
  
6.  Stellen Sie auf eine der folgenden Arten einen parametrisierten SQL-Befehl bereit:  
  
    -   Verwenden Sie die direkte Eingabe, und geben Sie den SQL-Befehl für die SQLStatement-Eigenschaft ein.  
  
    -   Verwenden Sie die direkte Eingabe, klicken Sie auf **Abfrage erstellen**, und erstellen Sie einen SQL-Befehl mithilfe der grafischen Tools des Abfrage-Generators.  
  
    -   Verwenden Sie eine Dateiverbindung, und verweisen Sie auf die Datei, die den SQL-Befehl enthält.  
  
    -   Verwenden Sie eine Variable, und verweisen Sie auf die Variable, die den SQL-Befehl enthält.  
  
     Die in parametrisierten SQL-Anweisungen verwendeten Parametermarkierungen hängen vom Verbindungstyp ab, den der Task SQL ausführen verwendet.  
  
    |Verbindungstyp|Parametermarkierung|  
    |---------------------|----------------------|  
    |ADO|?|  
    |ADO.NET und SQLMOBILE|@\<parameter name>|  
    |ODBC|?|  
    |EXCEL und OLE DB|?|  
  
     In der folgenden Tabelle finden Sie eine Auflistung von Beispielen des SELECT-Befehls nach verschiedenen Verbindungs-Managertypen. Parameter stellen die Filterwerte in den WHERE-Klauseln bereit. In den Beispielen wird die SELECT-Anweisung verwendet, um Produkte aus der **Product** -Tabelle in [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)] zurückzugeben, die eine **ProductID** aufweisen, die größer oder kleiner als die angegebenen Werte von zwei Parametern ist.  
  
    |Verbindungstyp|SELECT-Syntax|  
    |---------------------|-------------------|  
    |EXCEL, ODBC und OLEDB|`SELECT* FROM Production.Product WHERE ProductId > ? AND ProductID < ?`|  
    |ADO|`SELECT* FROM Production.Product WHERE ProductId > ? AND ProductID < ?`|  
    |[!INCLUDE[vstecado](../includes/vstecado-md.md)]|`SELECT* FROM Production.Product WHERE ProductId > @parmMinProductID AND ProductID < @parmMaxProductID`|  
  
     Beispiele zum Verwenden von Parametern mit gespeicherten Prozeduren finden Sie unter [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).  
  
7.  Klicken Sie auf **Parameterzuordnung**.  
  
8.  Klicken Sie auf **Hinzufügen**, um eine Parameterzuordnung hinzuzufügen.  
  
9. Stellen Sie im Feld **Parametername** einen Namen bereit.  
  
     Die verwendeten Parameternamen hängen vom Verbindungstyp ab, den der Task 'SQL ausführen' verwendet.  
  
    |Verbindungstyp|Parametername|  
    |---------------------|--------------------|  
    |ADO|Param1, Param2, …|  
    |ADO.NET und SQLMOBILE|@\<parameter name>|  
    |ODBC|1, 2, 3, ...|  
    |EXCEL und OLE DB|0, 1, 2, 3, ...|  
  
10. Wählen Sie in der Liste **Variablenname** eine Variable aus. Weitere Informationen finden Sie unter [Hinzufügen, Löschen, Ändern des Bereichs von benutzerdefinierten Variablen in einem Paket](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md).  
  
11. Geben Sie in der Liste **Richtung** an, ob der Parameter eine Eingabe, eine Ausgabe oder ein Rückgabewert ist.  
  
12. Legen Sie in der Liste **Datentyp** den Datentyp des Parameters fest.  
  
    > [!IMPORTANT]  
    >  Der Datentyp des Parameters muss mit dem Datentyp der Variablen kompatibel sein.  
  
13. Wiederholen Sie die Schritte 8 bis 11 für jeden Parameter in der SQL-Anweisung.  
  
    > [!IMPORTANT]  
    >  Die Reihenfolge von Parameterzuordnungen muss mit der Reihenfolge identisch sein, in der Parameter in der SQL-Anweisung aufgeführt sind.  
  
14. Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL ausführen (Task)](control-flow/execute-sql-task.md)   
 [Parameter und Rückgabe Codes im Task "SQL ausführen"](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)   
 [Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md)  
  
  
