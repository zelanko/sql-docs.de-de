---
title: Zuordnen von Resultsets zu Variablen in einem Task "SQL ausführen" | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- result sets [Integration Services]
- mapping result sets to variables [Integration Services]
- variables [Integration Services], mapping result sets to
ms.assetid: f76738b6-dc75-4ff9-a3dd-8b083d8e410e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 995afe55c1cd1b7d925c9267ba5dfa3aed038358
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66057759"
---
# <a name="map-result-sets-to-variables-in-an-execute-sql-task"></a>Zuordnen von Resultsets zu Variablen in einem Task „SQL ausführen“
  In diesem Thema wird das Erstellen einer Zuordnung zwischen einem Resultset und einer Variablen in einem Task "SQL ausführen" beschrieben. Indem Sie ein Resultset zu einer Variablen zuordnen, wird das Resultset für andere Elemente des Pakets zur Verfügung gestellt. Beispielsweise kann ein Skript eines Skripttasks die Variable lesen und dann die Werte des Resultsets verwenden, oder eine XML-Quelle kann das in einer Variable gespeicherte Resultset verwenden. Wenn das Resultset durch ein übergeordnetes Paket generiert wird, kann das Resultset für ein untergeordnetes Paket, das von einem Task Paket ausführen aufgerufen wird, zur Verfügung gestellt werden. Hierzu wird das Resultset im übergeordneten Paket einer Variablen zugeordnet. Anschließend wird im untergeordneten Paket eine übergeordnete Variablenkonfiguration erstellt, um den übergeordneten Variablenwert zu speichern.  
  
 Beschreibungen zu verschiedenen Resultsettypen und variablen Datentypen, die Sie Resultsets zuordnen können, finden Sie unter [Resultsets im Task „SQL ausführen“](control-flow/execute-sql-task.md).  
  
### <a name="to-map-a-result-set-to-a-variable"></a>So ordnen Sie einer Variablen ein Resultset zu  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im **Projektmappen-Explorer**auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Ablaufsteuerung** .  
  
4.  Wenn das Paket noch keinen Task SQL ausführen enthält, fügen Sie der Ablaufsteuerung des Pakets einen solchen Task hinzu. Weitere Informationen finden Sie unter [hinzufügen oder Löschen eines Tasks oder Containers in einer Ablaufsteuerung](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  .  
  
5.  Doppelklicken Sie auf den Task SQL ausführen.  
  
6.  Wählen Sie im Dialogfeld **Editor für den Task 'SQL ausführen'** auf der Seite **Allgemein** den Resultsettyp **Einzelne Zeile**, **Vollständiges Resultset**oder **XML** aus.  
  
     Beschreibungen zu den verschiedenen Resultsets finden Sie unter [Resultsets im Task „SQL ausführen“](result-sets-in-the-execute-sql-task.md).  
  
7.  Klicken Sie auf **Resultset**.  
  
8.  Klicken Sie auf **Hinzufügen**, um eine Resultsetzuordnung hinzuzufügen.  
  
9. Wählen Sie in der Liste **Variablenname** eine Variable aus, oder erstellen Sie eine neue Variable. Weitere Informationen finden Sie unter [Hinzufügen, Löschen, Ändern des Bereichs von benutzerdefinierten Variablen in einem Paket](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md).  
  
     Beschreibungen zu den variablen Datentypen, die Sie den unterschiedlichen Resultsets zuordnen können, finden Sie unter [Resultsets im Task „SQL ausführen“](result-sets-in-the-execute-sql-task.md).  
  
     Informationen dazu, wie eine Variable einer einzelnen Spalte und mehrere Variablen mehreren Spalten zugeordnet werden, finden Sie im Abschnitt **Auffüllen einer Variablen mit einem Resultset** in [Result Sets in the Execute SQL Task](control-flow/execute-sql-task.md).  
  
10. Ändern Sie in der Liste **Ergebnisname** optional den Namen des Resultsets.  
  
     Im Allgemeinen können Sie den Spaltennamen als Resultsetnamen verwenden, oder Sie können die Ordnungsposition der Spalte in der Spaltenliste als Resultset verwenden. Ob ein Spaltenname als Resultsetname verwendet werden kann, hängt davon ab, für welchen Anbieter der Task konfiguriert ist. Nicht alle Anbieter machen Spaltennamen verfügbar.  
  
11. Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL ausführen (Task)](control-flow/execute-sql-task.md)   
 [Resultsets den Task "SQL ausführen"](result-sets-in-the-execute-sql-task.md)   
 [Task "Paket ausführen"](control-flow/execute-package-task.md)   
 [Paketkonfigurationen](../../2014/integration-services/package-configurations.md)   
 [Erstellen von Paketkonfigurationen](../../2014/integration-services/create-package-configurations.md)   
 [Verwenden Sie die Werte von Variablen und Parametern in einem untergeordneten Paket](../../2014/integration-services/use-the-values-of-variables-and-parameters-in-a-child-package.md)   
 [Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md)  
  
  
