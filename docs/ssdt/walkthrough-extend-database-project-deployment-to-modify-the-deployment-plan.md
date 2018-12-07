---
title: 'Exemplarische Vorgehensweise: Erweitern der Datenbankprojektbereitstellung zum Bearbeiten des Bereitstellungsplans | Microsoft-Dokumentation'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 22b077b1-fa25-49ff-94f6-6d0d196d870a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 073d32e69df1ab852271b1c921f1f3e99bae92c4
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52531562"
---
# <a name="walkthrough-extend-database-project-deployment-to-modify-the-deployment-plan"></a>Exemplarische Vorgehensweise: Bereitstellung des Datenbankprojekts erweitern, um den Bereitstellungsplan zu bearbeiten
Sie können Bereitstellungs-Contributors erstellen, um benutzerdefinierte Aktionen durchzuführen, wenn Sie ein SQL-Projekt bereitstellen. Sie können [DeploymentPlanModifier](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplanmodifier.aspx) oder [DeploymentPlanExecutor](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplanexecutor.aspx) erstellen. Verwenden Sie [DeploymentPlanModifier](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplanmodifier.aspx), um den Plan zu ändern, bevor er ausgeführt wird, und [DeploymentPlanExecutor](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplanexecutor.aspx), um Vorgänge durchzuführen, während der Plan ausgeführt wird. In dieser exemplarischen Vorgehensweise erstellen Sie einen [DeploymentPlanModifier](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplanmodifier.aspx) mit der Bezeichnung „SqlRestartableScriptContributor“, der den Batches im Bereitstellungsskript IF-Anweisungen hinzufügt, um ein erneutes Ausführen des Skripts zu ermöglichen, bis es fertig gestellt ist, falls während der Ausführung ein Fehler auftritt.  
  
In dieser exemplarischen Vorgehensweise führen Sie folgende Hauptaufgaben aus:  
  
-   [DeploymentPlanModifier-Typ des Bereitstellungs-Contributors erstellen](#CreateDeploymentContributor)  
  
-   [Bereitstellungs-Contributor installieren](#InstallDeploymentContributor)  
  
-   [Bereitstellungs-Contributor ausführen oder testen](#TestDeploymentContributor)  
  
## <a name="prerequisites"></a>Voraussetzungen  
Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Sie müssen eine Version von Visual Studio installiert haben, die SQL Server Data Tools enthält und die Entwicklung in C# oder VB unterstützt.  
  
-   Sie müssen über ein SQL-Projekt verfügen, das SQL-Objekte enthält.  
  
-   Eine Instanz von SQL Server, auf der Sie ein Datenbankprojekt bereitstellen können.  
  
> [!NOTE]  
> Diese exemplarische Vorgehensweise ist für Benutzer gedacht, die bereits mit den SQL-Funktionen von SQL Server Data Tools vertraut sind. Außerdem wird von Ihnen erwartet, dass Sie mit den grundlegenden Visual Studio-Konzepten vertraut sind, wie etwa dem Erstellen einer Klassenbibliothek und dem Verwenden des Code-Editor zum Hinzufügen von Code zu einer Klasse.  
  
## <a name="CreateDeploymentContributor"></a>Erstellen eines Bereitstellungs-Contributors  
Zum Erstellen eines Bereitstellungs-Contributors führen Sie folgende Aufgaben aus:  
  
-   Erstellen Sie ein Klassenbibliotheksprojekt, und fügen Sie die erforderlichen Verweise hinzu.  
  
-   Definieren Sie eine Klasse mit der Bezeichnung „SqlRestartableScriptContributor“, die von [DeploymentPlanModifier](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplanmodifier.aspx) erbt.  
  
-   Überschreiben Sie die [OnExecute](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplancontributor.onexecute.aspx)-Methode.  
  
-   Fügen Sie private Hilfemethoden hinzu.  
  
-   Erstellen Sie die resultierende Assembly.  
  
#### <a name="to-create-a-class-library-project"></a>So erstellen Sie ein Klassenbibliotheksprojekt  
  
1.  Erstellen Sie ein Visual C#- oder ein Visual Basic-Klassenbibliotheksprojekt mit der Bezeichnung MyOtherDeploymentContributor.  
  
2.  Benennen Sie die Datei „Class1.cs“ in „SqlRestartableScriptContributor.cs“ um.  
  
3.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Projektknoten, und klicken Sie dann auf **Verweis hinzufügen**.  
  
4.  Wählen Sie auf der Registerkarte „Frameworks“ die Option **System.ComponentModel.Composition** aus.  
  
5.  Klicken Sie auf **Durchsuchen**, und navigieren Sie zum Verzeichnis **C:\Programme(x86)\Microsoft SQL Server\110\SDK\Assemblies**, wählen Sie **Microsoft.SqlServer.TransactSql.ScriptDom.dll** aus, und klicken Sie dann auf **OK**.  
  
6.  Erforderliche SQL-Verweise hinzufügen: Klicken Sie mit der rechten Maustaste auf den Projektknoten, und klicken Sie dann auf **Verweis hinzufügen**. Klicken Sie auf **Durchsuchen**, und navigieren Sie zum Ordner **C:\Programme (x86)\Microsoft SQL Server\110\DAC\Bin**. Wählen Sie die Einträge **Microsoft.SqlServer.Dac.dll**, **Microsoft.SqlServer.Dac.Extensions.dll** und **Microsoft.Data.Tools.Schema.Sql.dll**, klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **OK**.  
  
Beginnen Sie als Nächstes, der Klasse Code hinzuzufügen.  
  
#### <a name="to-define-the-sqlrestartablescriptcontributor-class"></a>So definieren Sie die SqlRestartableScriptContributor-Klasse  
  
1.  Aktualisieren Sie die im Code-Editor die class1.cs-Datei, damit sie folgenden **using**-Anweisungen entspricht:  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Globalization;  
    using System.Text;  
    using Microsoft.SqlServer.Dac.Deployment;  
    using Microsoft.SqlServer.Dac.Model;  
    using Microsoft.SqlServer.TransactSql.ScriptDom;  
    ```  
  
2.  Aktualisieren Sie die Klassendefinition, damit sie folgendem Beispiel entspricht:  
  
    ```csharp  
        /// <summary>  
    /// This deployment contributor modifies a deployment plan by adding if statements  
    /// to the existing batches in order to make a deployment script able to be rerun to completion  
    /// if an error is encountered during execution  
    /// </summary>  
    [ExportDeploymentPlanModifier("MyOtherDeploymentContributor.RestartableScriptContributor", "1.0.0.0")]  
    public class SqlRestartableScriptContributor : DeploymentPlanModifier  
    {  
    }  
  
    ```  
  
    Sie haben jetzt Ihren Bereitstellungs-Contributor definiert, der von [DeploymentPlanModifier](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplanmodifier.aspx) erbt. Während des Erstellungs- und Bereitstellungsprozesses werden benutzerdefinierte Contributors aus dem Standarderweiterungsverzeichnis geladen. Den Bereitstellungsplan ändernde Contributors werden anhand eines [ExportDeploymentPlanModifier](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.exportdeploymentplanmodifierattribute.aspx)-Attributs identifiziert. Dieses Attribut muss angegeben werden, damit die Contributors ermittelt werden können. Dieses Attribut sollte folgendem ähnlich sehen:  
  
    ```csharp  
    [ExportDeploymentPlanModifier("MyOtherDeploymentContributor.RestartableScriptContributor", "1.0.0.0")]  
  
    ```  
  
3.  Fügen Sie die folgenden Member-Deklarationen hinzu:  
  
    ```vb  
         private const string BatchIdColumnName = "BatchId";  
            private const string DescriptionColumnName = "Description";  
  
            private const string CompletedBatchesVariableName = "CompletedBatches";  
            private const string CompletedBatchesVariable = "$(CompletedBatches)";  
            private const string CompletedBatchesSqlCmd = @":setvar " + CompletedBatchesVariableName + " __completedBatches_{0}_{1}";  
            private const string TotalBatchCountSqlCmd = @":setvar TotalBatchCount {0}";  
            private const string CreateCompletedBatchesTable = @"  
    if OBJECT_ID(N'tempdb.dbo." + CompletedBatchesVariable + @"', N'U') is null  
    begin  
    use tempdb  
    create table [dbo].[$(CompletedBatches)]  
    (  
    BatchId int primary key,  
    Description nvarchar(300)  
    )  
    use [$(DatabaseName)]  
    end  
    ";  
  
    ```  
  
    Als Nächstes überschreiben Sie die OnExecute-Methode und fügen den Code hinzu, den Sie bei der Bereitstellung eines Datenbankprojekts ausführen.  
  
#### <a name="to-override-onexecute"></a>So überschreiben Sie OnExecute  
  
1.  Fügen Sie die folgende Methode der SqlRestartableScriptContributor-Klasse hinzu:  
  
    ```csharp  
    /// <summary>  
    /// You override the OnExecute method to do the real work of the contributor.  
    /// </summary>  
    /// <param name="context"></param>  
    protected override void OnExecute(DeploymentPlanContributorContext context)  
    {  
         // Replace this with the method body  
    }  
  
    ```  
  
    Sie überschreiben die [OnExecute](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplancontributor.onexecute.aspx)-Methode über die Basisklasse, [DeploymentPlanContributor](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplancontributor.aspx), die die Basisklasse für [DeploymentPlanModifier](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplanmodifier.aspx) und [DeploymentPlanExecutor](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplanexecutor.aspx) ist. An die „OnExecute“-Methode wird ein [DeploymentPlanContributorContext](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplancontributorcontext.aspx)-Objekt übergeben, das Zugriff auf alle angegebenen Argumente, das Quell- und Zieldatenbankmodell, den Bereitstellungsplan und die Bereitstellungsoptionen bietet. In diesem Beispiel erhalten wir den Bereitstellungsplan und den Namen der Zieldatenbank.  
  
2.  Fügen Sie jetzt die Anfänge eines Texts der OnExecute-Methode hinzu:  
  
    ```vb  
    // Obtain the first step in the Plan from the provided context  
    DeploymentStep nextStep = context.PlanHandle.Head;  
    int batchId = 0;  
    BeginPreDeploymentScriptStep beforePreDeploy = null;  
  
    // Loop through all steps in the deployment plan  
    while (nextStep != null)  
    {  
        // Increment the step pointer, saving both the current and next steps  
        DeploymentStep currentStep = nextStep;  
        nextStep = currentStep.Next;  
  
        // Add additional step processing here  
    }  
  
    // if we found steps that required processing, set up a temporary table to track the work that you are doing  
    if (beforePreDeploy != null)  
    {  
        // Add additional post-processing here  
    }  
  
    // Cleanup and drop the table   
    DeploymentScriptStep dropStep = new DeploymentScriptStep(DropCompletedBatchesTable);  
    base.AddAfter(context.PlanHandle, context.PlanHandle.Tail, dropStep);  
  
    ```  
  
    In diesem Code definieren wir einige lokale Variablen und richten die Schleife ein, die die Verarbeitung aller Schritte im Bereitstellungsplan verarbeitet. Nach Fertigstellung der Schleife müssen wir die Nachbearbeitung durchführen und dann die temporäre Tabelle löschen, die wir während der Bereitstellung erstellt haben, um während der Ausführung des Plans den Fortschritt nachzuverfolgen. Die wichtigsten Typen sind: [DeploymentStep](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentstep.aspx) und [DeploymentScriptStep](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentscriptstep.aspx). Eine wichtige Methode ist „AddAfter“.  
  
3.  Fügen Sie jetzt die Verarbeitung des zusätzlichen Schritts hinzu, und ersetzen Sie dadurch folgenden Kommentar: "Verarbeitung des zusätzlichen Schritts hier hinzufügen":  
  
    ```csharp  
    // Look for steps that mark the pre/post deployment scripts  
    // These steps will always be in the deployment plan even if the  
    // user's project does not have a pre/post deployment script  
    if (currentStep is BeginPreDeploymentScriptStep)  
    {  
        // This step marks the beginning of the predeployment script.  
        // Save the step and move on.  
        beforePreDeploy = (BeginPreDeploymentScriptStep)currentStep;  
        continue;  
    }  
    if (currentStep is BeginPostDeploymentScriptStep)  
    {  
        // This is the step that marks the beginning of the post deployment script.    
        // We do not continue processing after this point.  
        break;  
    }  
    if (currentStep is SqlPrintStep)  
    {  
        // We do not need to put if statements around these  
        continue;  
    }  
  
    // if we have not yet found the beginning of the pre-deployment script steps,   
    // skip to the next step.  
    if (beforePreDeploy == null)  
    {  
        // We only surround the "main" statement block with conditional  
        // statements  
        continue;  
    }  
  
    // Determine if this is a step that we need to surround with a conditional statement  
    DeploymentScriptDomStep domStep = currentStep as DeploymentScriptDomStep;  
    if (domStep == null)  
    {  
        // This step is not a step that we know how to modify,  
        // so skip to the next step.  
        continue;  
    }  
  
    TSqlScript script = domStep.Script as TSqlScript;  
    if (script == null)  
    {  
        // The script dom step does not have a script with batches - skip  
        continue;  
    }  
  
        // Loop through all the batches in the script for this step.  All the statements  
        // in the batch will be enclosed in an if statement that will check the  
        // table to ensure that the batch has not already been executed  
        TSqlObject sqlObject;  
        string stepDescription;  
        GetStepInfo(domStep, out stepDescription, out sqlObject);  
        int batchCount = script.Batches.Count;  
  
    for (int batchIndex = 0; batchIndex < batchCount; batchIndex++)  
    {  
        // Add batch processing here  
    }  
  
    ```  
  
    Die Kommentare zum Code erklären die Verarbeitung. Dieser Code sucht auf hoher Ebene nach den Schritten, um die Sie sich kümmern, wobei andere übersprungen und angehalten werden, wenn Sie den Anfang der Schritte nach der Bereitstellung erreichen. Falls der Schritt Anweisungen enthält, die wir mit Bedingungen umgeben müssen, führen wir die weitere Verarbeitung durch. Wichtige Typen, Methoden und Eigenschaften: [BeginPreDeploymentScriptStep](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.beginpredeploymentscriptstep.aspx), [BeginPostDeploymentScriptStep](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.beginpostdeploymentscriptstep.aspx), [TSqlObject](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.model.tsqlobject.aspx), [TSqlScript](https://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.tsqlscript.aspx), Script, [DeploymentScriptDomStep](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentscriptdomstep.aspx) und [SqlPrintStep](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.sqlprintstep.aspx).  
  
4.  Fügen Sie jetzt den Batchverarbeitungscode hinzu, indem Sie den Kommentar "Batchverarbeitung hier hinzufügen" ersetzen:  
  
    ```csharp  
        // Create the if statement that will contain the batch's contents  
        IfStatement ifBatchNotExecutedStatement = CreateIfNotExecutedStatement(batchId);  
        BeginEndBlockStatement statementBlock = new BeginEndBlockStatement();  
        ifBatchNotExecutedStatement.ThenStatement = statementBlock;  
        statementBlock.StatementList = new StatementList();  
  
        TSqlBatch batch = script.Batches[batchIndex];  
        int statementCount = batch.Statements.Count;  
  
        // Loop through all statements in the batch, embedding those in an sp_execsql  
        // statement that must be handled this way (schemas, stored procedures,   
        // views, functions, and triggers).  
        for (int statementIndex = 0; statementIndex < statementCount; statementIndex++)  
        {  
            // Add additional statement processing here  
        }  
  
        // Add an insert statement to track that all the statements in this  
        // batch were executed.  Turn on nocount to improve performance by  
        // avoiding row inserted messages from the server  
        string batchDescription = string.Format(CultureInfo.InvariantCulture,  
            "{0} batch {1}", stepDescription, batchIndex);  
  
        PredicateSetStatement noCountOff = new PredicateSetStatement();  
        noCountOff.IsOn = false;  
        noCountOff.Options = SetOptions.NoCount;  
  
        PredicateSetStatement noCountOn = new PredicateSetStatement();  
        noCountOn.IsOn = true;  
        noCountOn.Options = SetOptions.NoCount;   
        InsertStatement batchCompleteInsert = CreateBatchCompleteInsert(batchId, batchDescription);  
        statementBlock.StatementList.Statements.Add(noCountOn);  
    statementBlock.StatementList.Statements.Add(batchCompleteInsert);  
        statementBlock.StatementList.Statements.Add(noCountOff);  
  
        // Remove all the statements from the batch (they are now in the if block) and add the if statement  
        // as the sole statement in the batch  
        batch.Statements.Clear();  
        batch.Statements.Add(ifBatchNotExecutedStatement);  
  
        // Next batch  
        batchId++;  
  
    ```  
  
    Mit diesem Code wird eine IF-Anweisung neben dem BEGIN/END-Block erstellt. Wir führen anschließend die weitere Verarbeitung an den Anweisungen im Batch durch. Ist diese abgeschlossen, fügen wir eine INSERT-Anweisung hinzu, um der temporären Tabelle Informationen hinzuzufügen, die den Fortschritt der Skriptausführung nachzuverfolgen. Aktualisieren Sie schließlich den Batch, und ersetzen Sie die vorherigen Anweisungen durch die neue IF-Anweisung, die diese Anweisungen enthält. Wichtige Typen, Methoden und Eigenschaften: [IfStatement](https://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.ifstatement.aspx), [BeginEndBlockStatement](https://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.beginendblockstatement.aspx), [StatementList](https://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.statementlist.aspx), [TSqlBatch](https://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.tsqlbatch.aspx), [PredicateSetStatement](https://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.predicatesetstatement.aspx), [SetOptions](https://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.setoptions.aspx) und [InsertStatement](https://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.insertstatement.aspx).  
  
5.  Fügen Sie jetzt den Text der Anweisungsverarbeitungsschleife hinzu. Ersetzen Sie den Kommentar "Verarbeitung der zusätzlichen Anweisung hier hinzufügen":  
  
    ```csharp  
    TSqlStatement smnt = batch.Statements[statementIndex];  
  
    if (IsStatementEscaped(sqlObject))  
    {  
        // "escape" this statement by embedding it in a sp_executesql statement  
        string statementScript;  
        domStep.ScriptGenerator.GenerateScript(smnt, out statementScript);  
        ExecuteStatement spExecuteSql = CreateExecuteSql(statementScript);  
        smnt = spExecuteSql;  
    }  
  
    statementBlock.StatementList.Statements.Add(smnt);  
  
    ```  
  
    Ändern Sie jede Anweisung im Batch entsprechend, falls die Anweisung in einem Typ vorliegt, der in eine sp_executesql-Anweisung eingebunden sein muss. Vom Code wird die Anweisung dann zur Anweisungsliste für den von Ihnen erstellten BEGIN/END-Block hinzugefügt. Zu den wichtigen Typen, Methoden und Eigenschaften gehören [TSqlStatement](https://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.tsqlstatement.aspx) und [ExecuteStatement](https://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.executestatement.aspx).  
  
6.  Fügen Sie schließlich den Nachbearbeitungsabschnitt anstelle des folgenden Kommentars hinzu: "Nachbearbeitung hier hinzufügen":  
  
    ```csharp  
    // Declare a SqlCmd variables.  
    //  
    // CompletedBatches variable - defines the name of the table in tempdb that will track  
    // all the completed batches.  The temporary table's name has the target database name and  
    // a guid embedded in it so that:  
    // * Multiple deployment scripts targeting different DBs on the same server  
    // * Failed deployments with old tables do not conflict with more recent deployments  
    //  
    // TotalBatchCount variable - the total number of batches surrounded by if statements.  Using this  
    // variable pre/post deployment scripts can also use the CompletedBatches table to make their  
    // script rerunnable if there is an error during execution  
    StringBuilder sqlcmdVars = new StringBuilder();  
    sqlcmdVars.AppendFormat(CultureInfo.InvariantCulture, CompletedBatchesSqlCmd,  
        context.Options.TargetDatabaseName, Guid.NewGuid().ToString("D"));  
    sqlcmdVars.AppendLine();  
    sqlcmdVars.AppendFormat(CultureInfo.InvariantCulture, TotalBatchCountSqlCmd, batchId);  
  
    DeploymentScriptStep completedBatchesSetVarStep = new DeploymentScriptStep(sqlcmdVars.ToString());  
    base.AddBefore(context.PlanHandle, beforePreDeploy, completedBatchesSetVarStep);  
  
    // Create the temporary table we will use to track the work that we are doing  
    DeploymentScriptStep createStatusTableStep = new DeploymentScriptStep(CreateCompletedBatchesTable);  
    base.AddBefore(context.PlanHandle, beforePreDeploy, createStatusTableStep);  
  
    ```  
  
    Fall unsere Bearbeitung mindestens einen Schritt gefunden hat, den wir in eine bedingte Anweisung eingebunden haben, müssen wir dem Bereitstellungsskript Anweisungen hinzufügen, um SQLCMD-Variablen zu definieren. Die erste Variable CompletedBatches enthält einen eindeutigen Namen für die temporäre Tabelle, die das Bereitstellungsskript verwendet, um nachzuverfolgen, welche Batches bei der Ausführung des Skripts abgeschlossen wurden. Die zweite Variable TotalBatchCount enthält die Gesamtzahl der Batches im Bereitstellungsskript.  
  
    Weitere interessante Typen, Eigenschaften und Methoden:  
  
    „StringBuilder“, [DeploymentScriptStep](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentscriptstep.aspx) und „AddBefore“.  
  
    Als Nächstes definieren Sie die von dieser Methode aufgerufenen Hilfemethoden.  
  
#### <a name="to-add-the-helper-methods"></a>So fügen Sie die Hilfemethoden hinzu  
  
-   Die Anzahl der Hilfemethoden muss definiert werden. Wichtige Methoden:  
  
    |**Methode**|**Beschreibung**|  
    |--------------|-------------------|  
    |CreateExecuteSQL|Definieren Sie die CreateExecuteSQL-Methode so, dass eine angegebene Anweisung von einer EXEC sp_executesql-Anweisung umgeben wird. Wichtige Typen, Methoden und Eigenschaften: [ExecuteStatement](https://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.executestatement.aspx), [ExecutableProcedureReference](https://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.executableprocedurereference.aspx), [SchemaObjectName](https://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.schemaobjectname.aspx), [ProcedureReference](https://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.procedurereference.aspx) und [ExecuteParameter](https://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.executeparameter.aspx).|  
    |CreateCompletedBatchesName|Definieren Sie die CreateCompletedBatchesName-Methode. Von dieser Methode wird der Name erstellt, der in die temporäre Tabelle für einen Batch eingefügt wird. Wichtige Typen, Methoden und Eigenschaften: [SchemaObjectName](https://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.schemaobjectname.aspx).|  
    |IsStatementEscaped|Definieren Sie die IsStatementEscaped-Methode. Diese Methode bestimmt, ob ein Typ des Modellelements erfordert, dass die Anweisung von einer EXEC sp_executesql-Anweisung umgeben wird, bevor sie in eine IF-Anweisung eingefügt werden kann. Zu den wichtigen Typen, Methoden und Eigenschaften zählen: „TSqlObject.ObjectType“, „ModelTypeClass“ und die „TypeClass“-Eigenschaft für die folgenden Modelltypen: „Schema“, „Procedure“, „View“, „TableValuedFunction“, „ScalarFunction“, „DatabaseDdlTrigger“, „DmlTrigger“, „ServerDdlTrigger“.|  
    |CreateBatchCompleteInsert|Definieren Sie die CreateBatchCompleteInsert-Methode. Von dieser Methode wird die INSERT-Anweisung erstellt, die dem Bereitstellungsskript hinzugefügt wird, um den Fortschritt der Ausführung des Skripts nachzuverfolgen. Zu den wichtigen Typen, Methoden und Eigenschaften zählen die folgenden: „InsertStatement“, „NamedTableReference“, „ColumnReferenceExpression“, „ValuesInsertSource“ und „RowValue“.|  
    |CreateIfNotExecutedStatement|Definieren Sie die CreateIfNotExecutedStatement-Methode. Von dieser Methode wird eine IF-Anweisung generiert, die prüft, ob die von den temporären Batches ausgeführte Tabelle angibt, dass dieser Batch bereits ausgeführt wurde. Zu den wichtigen Typen, Methoden und Eigenschaften zählen diese: „IfStatement“, „ExistsPredicate“, „ScalarSubquery“, „NamedTableReference“, „WhereClause“, „ColumnReferenceExpression“, „IntegerLiteral“, „BooleanComparisonExpression“ und „BooleanNotExpression“.|  
    |GetStepInfo|Definieren Sie die GetStepInfo-Methode. Mit dieser Methode werden neben dem Namen des Schritts Informationen zum Modellelement extrahiert, das zum Erstellen des Skripts dieses Schritts verwendet wird. Interessante Typen und Methoden:[DeploymentPlanContributorContext](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplancontributorcontext.aspx), [DeploymentScriptDomStep](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentscriptdomstep.aspx), [TSqlObject](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.model.tsqlobject.aspx), [CreateElementStep](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.createelementstep.aspx), [AlterElementStep](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.alterelementstep.aspx) und [DropElementStep](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.dropelementstep.aspx).|  
    |GetElementName|Erstellt einen formatierten Namen für ein TSqlObject.|  
  
1.  Fügen Sie den folgenden Code hinzu, um die Hilfemethoden zu definieren:  
  
    ```csharp  
  
    /// <summary>  
    /// The CreateExecuteSql method "wraps" the provided statement script in an "sp_executesql" statement  
    /// Examples of statements that must be so wrapped include: stored procedures, views, and functions  
    /// </summary>  
    private static ExecuteStatement CreateExecuteSql(string statementScript)  
    {  
        // define a new Exec statement  
        ExecuteStatement executeSp = new ExecuteStatement();  
        ExecutableProcedureReference spExecute = new ExecutableProcedureReference();  
        executeSp.ExecuteSpecification = new ExecuteSpecification { ExecutableEntity = spExecute };  
  
        // define the name of the procedure that you want to execute, in this case sp_executesql  
        SchemaObjectName procName = new SchemaObjectName();  
        procName.Identifiers.Add(CreateIdentifier("sp_executesql", QuoteType.NotQuoted));  
        ProcedureReference procRef = new ProcedureReference { Name = procName };  
  
        spExecute.ProcedureReference = new ProcedureReferenceName { ProcedureReference = procRef };  
  
        // add the script parameter, constructed from the provided statement script  
        ExecuteParameter scriptParam = new ExecuteParameter();  
        spExecute.Parameters.Add(scriptParam);  
        scriptParam.ParameterValue = new StringLiteral { Value = statementScript };  
        scriptParam.Variable = new VariableReference { Name = "@stmt" };  
        return executeSp;  
    }  
  
    /// <summary>  
    /// The CreateIdentifier method returns a Identifier with the specified value and quoting type  
    /// </summary>  
    private static Identifier CreateIdentifier(string value, QuoteType quoteType)  
    {  
        return new Identifier { Value = value, QuoteType = quoteType };  
    }  
  
    /// <summary>  
    /// The CreateCompletedBatchesName method creates the name that will be inserted  
    /// into the temporary table for a batch.  
    /// </summary>  
    private static SchemaObjectName CreateCompletedBatchesName()  
    {  
        SchemaObjectName name = new SchemaObjectName();  
        name.Identifiers.Add(CreateIdentifier("tempdb", QuoteType.SquareBracket));  
        name.Identifiers.Add(CreateIdentifier("dbo", QuoteType.SquareBracket));  
        name.Identifiers.Add(CreateIdentifier(CompletedBatchesVariable, QuoteType.SquareBracket));  
        return name;  
    }  
  
    /// <summary>  
    /// Helper method that determins whether the specified statement needs to  
    /// be escaped  
    /// </summary>  
    /// <param name="sqlObject"></param>  
    /// <returns></returns>  
    private static bool IsStatementEscaped(TSqlObject sqlObject)  
    {  
        HashSet<ModelTypeClass> escapedTypes = new HashSet<ModelTypeClass>  
        {  
            Schema.TypeClass,  
            Procedure.TypeClass,  
            View.TypeClass,  
            TableValuedFunction.TypeClass,  
            ScalarFunction.TypeClass,  
            DatabaseDdlTrigger.TypeClass,  
            DmlTrigger.TypeClass,  
            ServerDdlTrigger.TypeClass  
        };  
        return escapedTypes.Contains(sqlObject.ObjectType);  
    }  
  
    /// <summary>  
    /// Helper method that creates an INSERT statement to track a batch being completed  
    /// </summary>  
    /// <param name="batchId"></param>  
    /// <param name="batchDescription"></param>  
    /// <returns></returns>  
    private static InsertStatement CreateBatchCompleteInsert(int batchId, string batchDescription)  
    {  
        InsertStatement insert = new InsertStatement();  
        NamedTableReference batchesCompleted = new NamedTableReference();  
        insert.InsertSpecification = new InsertSpecification();  
        insert.InsertSpecification.Target = batchesCompleted;  
        batchesCompleted.SchemaObject = CreateCompletedBatchesName();  
  
        // Build the columns inserted into  
        ColumnReferenceExpression batchIdColumn = new ColumnReferenceExpression();  
        batchIdColumn.MultiPartIdentifier = new MultiPartIdentifier();  
        batchIdColumn.MultiPartIdentifier.Identifiers.Add(CreateIdentifier(BatchIdColumnName, QuoteType.NotQuoted));  
  
        ColumnReferenceExpression descriptionColumn = new ColumnReferenceExpression();  
        descriptionColumn.MultiPartIdentifier = new MultiPartIdentifier();  
        descriptionColumn.MultiPartIdentifier.Identifiers.Add(CreateIdentifier(DescriptionColumnName, QuoteType.NotQuoted));  
  
        insert.InsertSpecification.Columns.Add(batchIdColumn);  
        insert.InsertSpecification.Columns.Add(descriptionColumn);  
  
        // Build the values inserted  
        ValuesInsertSource valueSource = new ValuesInsertSource();  
        insert.InsertSpecification.InsertSource = valueSource;  
  
        RowValue values = new RowValue();  
        values.ColumnValues.Add(new IntegerLiteral { Value = batchId.ToString() });  
        values.ColumnValues.Add(new StringLiteral { Value = batchDescription });  
        valueSource.RowValues.Add(values);  
  
        return insert;  
    }  
  
    /// <summary>  
    /// This is a helper method that generates an if statement that checks the batches executed  
    /// table to see if the current batch has been executed.  The if statement will look like this  
    ///   
    /// if not exists(select 1 from [tempdb].[dbo].[$(CompletedBatches)]   
    ///                where BatchId = batchId)  
    /// begin  
    /// end  
    /// </summary>  
    /// <param name="batchId"></param>  
    /// <returns></returns>  
    private static IfStatement CreateIfNotExecutedStatement(int batchId)  
    {  
        // Create the exists/select statement  
        ExistsPredicate existsExp = new ExistsPredicate();  
        ScalarSubquery subQuery = new ScalarSubquery();  
        existsExp.Subquery = subQuery;  
  
        subQuery.QueryExpression = new QuerySpecification  
        {  
            SelectElements =  
            {  
                new SelectScalarExpression  { Expression = new IntegerLiteral { Value ="1" } }  
            },  
            FromClause = new FromClause  
            {  
                TableReferences =  
                    {  
                        new NamedTableReference() { SchemaObject = CreateCompletedBatchesName() }  
                    }  
            },  
            WhereClause = new WhereClause  
            {  
                SearchCondition = new BooleanComparisonExpression  
                {  
                    ComparisonType = BooleanComparisonType.Equals,  
                    FirstExpression = new ColumnReferenceExpression  
                    {  
                        MultiPartIdentifier = new MultiPartIdentifier  
                        {  
                            Identifiers = { CreateIdentifier(BatchIdColumnName, QuoteType.SquareBracket) }  
                        }  
                    },  
                    SecondExpression = new IntegerLiteral { Value = batchId.ToString() }  
                }  
            }  
        };  
  
        // Put together the rest of the statement  
        IfStatement ifNotExists = new IfStatement  
        {  
            Predicate = new BooleanNotExpression  
            {  
                Expression = existsExp  
            }  
        };  
  
        return ifNotExists;  
    }  
  
    /// <summary>  
    /// Helper method that generates a useful description of the step.  
    /// </summary>  
    private static void GetStepInfo(  
        DeploymentScriptDomStep domStep,  
        out string stepDescription,  
        out TSqlObject element)  
    {  
        element = null;  
  
        // figure out what type of step we've got, and retrieve  
        // either the source or target element.  
        if (domStep is CreateElementStep)  
        {  
            element = ((CreateElementStep)domStep).SourceElement;  
        }  
        else if (domStep is AlterElementStep)  
        {  
            element = ((AlterElementStep)domStep).SourceElement;  
        }  
        else if (domStep is DropElementStep)  
        {  
            element = ((DropElementStep)domStep).TargetElement;  
        }  
  
        // construct the step description by concatenating the type and the fully qualified  
        // name of the associated element.  
        string stepTypeName = domStep.GetType().Name;  
        if (element != null)  
        {  
            string elementName = GetElementName(element);  
  
            stepDescription = string.Format(CultureInfo.InvariantCulture, "{0} {1}",  
                stepTypeName, elementName);  
        }  
        else  
        {  
            // if the step has no associated element, just use the step type as the description  
            stepDescription = stepTypeName;  
        }  
    }  
  
    private static string GetElementName(TSqlObject element)  
    {  
        StringBuilder name = new StringBuilder();  
        if (element.Name.HasExternalParts)  
        {  
            foreach (string part in element.Name.ExternalParts)  
            {  
                if (name.Length > 0)  
                {  
                    name.Append('.');  
                }  
                name.AppendFormat("[{0}]", part);  
            }  
        }  
  
        foreach (string part in element.Name.Parts)  
        {  
            if (name.Length > 0)  
            {  
                name.Append('.');  
            }  
            name.AppendFormat("[{0}]", part);  
        }  
  
        return name.ToString();  
    }  
  
    ```  
  
2.  Speichern Sie die Änderungen an SqlRestartableScriptContributor.cs.  
  
Als Nächstes erstellen Sie die Klassenbibliothek.  
  
#### <a name="to-sign-and-build-the-assembly"></a>So signieren und erstellen Sie die Assembly  
  
1.  Klicken Sie im Menü **Projekt** auf **Eigenschaften von MyOtherDeploymentContributor**.  
  
2.  Klicken Sie auf die Registerkarte **Signierung** .  
  
3.  Klicken Sie auf **Assembly signieren**.  
  
4.  Klicken Sie unter **Schlüsseldatei mit starkem Namen auswählen:** auf **<New>**.  
  
5.  Geben Sie im Dialogfeld **Schlüssel für einen starken Namen erstellen** unter **Schlüsseldateiname** **MyRefKey**ein.  
  
6.  (optional) Sie können ein Kennwort für Ihre Schlüsseldatei mit starkem Namen angeben.  
  
7.  Klicken Sie auf **OK**.  
  
8.  Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
9. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
    Als Nächstes müssen Sie die Assembly installieren, damit sie geladen wird, wenn Sie SQL-Projekte bereitstellen.  
  
## <a name="InstallDeploymentContributor"></a>Installieren eines Bereitstellungs-Contributors  
Zum Installieren eines Bereitstellungs-Contributors müssen Sie die Assembly und die zugehörige PDB-Datei in den Erweiterungsordner kopieren.  
  
#### <a name="to-install-the-myotherdeploymentcontributor-assembly"></a>So installieren Sie die MyOtherDeploymentContributor-Assembly  
  
1.  Im nächsten Schritt kopieren Sie die Assemblyinformationen in das Verzeichnis „Extensions“. Beim Start von Visual Studio werden alle Erweiterungen im Ordner %Programme%\Microsoft SQL Server\110\DAC\Bin\Extensions und dessen Unterverzeichnissen identifiziert und für die Verwendung zur Verfügung gestellt.  
  
2.  Kopieren Sie die **MyOtherDeploymentContributor.dll**-Assemblydatei aus dem Ausgabeverzeichnis in das Verzeichnis %Programme%\Microsoft SQL Server\110\DAC\Bin\Extensions. Der Pfad Ihrer kompilierten DLL-Datei lautet standardmäßig IhrProjektmappenpfad\IhrProjektpfad\bin\Debug oder IhrProjektmappenpfad\IhrProjektpfad\bin\Release.  
  
## <a name="TestDeploymentContributor"></a>Ausführen oder Testen eines Bereitstellungs-Contributors  
Zum Ausführen oder Testen eines Bereitstellungs-Contributors führen Sie folgende Aufgaben aus:  
  
-   Fügen Sie der SQLPROJ-Datei, die Sie zu erstellen planen, Eigenschaften hinzu.  
  
-   Stellen Sie das Datenbankprojekt mithilfe von MSBuild und durch Angeben der entsprechenden Parameter bereit.  
  
### <a name="add-properties-to-the-sql-project-sqlproj-file"></a>So fügen Sie der SQL Project (.sqlproj)-Datei Eigenschaften hinzu  
Sie müssen die SQL-Projektdatei immer aktualisieren, um die ID der Contributor festzulegen, die Sie ausführen möchten. Dazu haben Sie zwei Möglichkeiten:  
  
1.  Sie können die SQLPROJ-Datei manuell bearbeiten, um die erforderlichen Argumente hinzuzufügen. Sie können sich dafür entscheiden, falls Ihr Contributor über keine Contributor-Argumente verfügt, die zur Konfiguration erforderlich sind, oder falls Sie den Build-Contributor nicht für eine große Anzahl von Projekten wiederverwenden möchten. Falls Sie diese Option wählen, fügen Sie der SQLPROJ-Datei nach dem ersten Importknoten in der Datei die folgenden Anweisungen hinzu:  
  
    ```  
    <PropertyGroup>  
      <DeploymentContributors>  
        $(DeploymentContributors); MyOtherDeploymentContributor.RestartableScriptContributor  
      </DeploymentContributors>  
    </PropertyGroup>  
    ```  
  
2.  Die zweite Methode ist das Erstellen einer Zieledatei, die die erforderlichen Contributorargumente enthält. Diese ist hilfreich, falls Sie denselben Contributor für mehrere Projekte verwenden und Contributorargumente erforderlich sind, da sie die Standardwerte enthält. Erstellen Sie in diesem Fall eine Zieledatei im MSBuild-Erweiterungspfad:  
  
    1.  Navigieren Sie zu %Programme%\MSBuild.  
  
    2.  Erstellen Sie einen neuen Ordner namens „MyContributors“, in dem Ihre Zieldateien gespeichert werden.  
  
    3.  Erstellen Sie in diesem Verzeichnis eine neue Datei namens „MyContributors.targets“, fügen Sie den folgenden Text hinzu, und speichern Sie die Datei:  
  
        ```  
        <?xml version="1.0" encoding="utf-8"?>  
  
        <Project xmlns="https://schemas.microsoft.com/developer/msbuild/2003">  
          <PropertyGroup>  
            <DeploymentContributors>$(DeploymentContributors);MyOtherDeploymentContributor.RestartableScriptContributor</DeploymentContributors>  
          </PropertyGroup>  
        </Project>  
  
        ```  
  
    4.  Importieren Sie in die SQLPROJ-Datei für jedes Projekt, in dem Sie Contributors ausführen möchten, die Zieldatei durch Hinzufügen folgender Anweisung zur SQLPROJ-Datei nach dem Knoten \<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v$(VisualStudioVersion)\SSDT\Microsoft.Data.Tools.Schema.SqlTasks.targets" \/> in der Datei:  
  
        ```  
        <Import Project="$(MSBuildExtensionsPath)\MyContributors\MyContributors.targets " />  
  
        ```  
  
Nach dem Durchführen einer dieser Vorgehensweisen können Sie MSBuild verwenden, um die Parameter für Befehlszeilenbuilds zu übertragen.  
  
> [!NOTE]  
> Sie müssen die Eigenschaft „DeploymentContributors“ stets aktualisieren, damit Ihre Contributor-ID angegeben wird. Dies ist die gleiche ID, die auch im Attribut „ExportDeploymentPlanModifier“ in Ihrer Contributorquelldatei verwendet wird. Ohne diese wird Ihr Contributor nicht ausgeführt, wenn Sie das Projekt erstellen. Die Eigenschaft „ContributorArguments“ muss nur aktualisiert werden, wenn Argumente erforderlich sind, damit Ihr Contributor ausgeführt werden kann.  
  
## <a name="deploy-the-database-project"></a>Das Datenbankprojekt bereitstellen  
  
#### <a name="to-deploy-your-sql-project-and-generate-a-deployment-report"></a>So stellen Sie Ihr SQL-Projekt bereit und generieren einen Bereitstellungsbericht  
  
-   Ihr Projekt kann in Visual Studio normal veröffentlicht oder bereitgestellt werden. Öffnen Sie einfach eine Projektmappe, die Ihr SQL-Projekt enthält, und wählen Sie im Kontextmenü des Projekts die Option „Veröffentlichen...“ aus, oder verwenden Sie F5 für eine Debug-Bereitstellung in LocalDB. In diesem Beispiel wird das Dialogfeld „Veröffentlichen...“ verwendet, um ein Bereitstellungsskript zu generieren.  
  
    1.  Öffnen Sie Visual Studio und die Projektmappe, die Ihr SQL-Projekt enthält.  
  
    2.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie die Option **Veröffentlichen...** aus.  
  
    3.  Legen Sie den Servernamen und Datenbanknamen fest, auf dem veröffentlicht werden soll.  
  
    4.  Wählen Sie aus den Optionen unten im Dialogfeld **Skript generieren**. Dadurch wird ein Skript erstellt, das für die Bereitstellung verwendet werden kann. Wir untersuchen dies, um zu prüfen, ob unsere IF-Anweisungen hinzugefügt wurden, um die Startbarkeit des Skripts wiederherzustellen.  
  
    5.  Untersuchen Sie das resultierende Bereitstellungsskript. Direkt vor dem Abschnitt mit der Bezeichnung „Vorlage für ein Skript vor der Bereitstellung“ sehen Sie ein Element, das folgender Transact-SQL-Syntax ähnelt:  
  
        ```  
        :setvar CompletedBatches __completedBatches_CompareProjectDB_cd1e348a-8f92-44e0-9a96-d25d65900fca  
        :setvar TotalBatchCount 17  
        GO  
  
        if OBJECT_ID(N'tempdb.dbo.$(CompletedBatches)', N'U') is null  
        begin  
        use tempdb  
        create table [dbo].[$(CompletedBatches)]  
        (  
        BatchId int primary key,  
        Description nvarchar(300)  
        )  
        use [$(DatabaseName)]  
        end  
  
        ```  
  
        Später im Bereitstellungsskript sehen Sie um jeden Batch herum eine IF-Anweisung, die die ursprüngliche Anweisung umgibt. Folgendes könnte beispielsweise für eine CREATE SCHEMA-Anweisung angezeigt werden:  
  
        ```  
        IF NOT EXISTS (SELECT 1  
                       FROM   [tempdb].[dbo].[$(CompletedBatches)]  
                       WHERE  [BatchId] = 0)  
            BEGIN  
                EXECUTE sp_executesql @stmt = N'CREATE SCHEMA [Sales]  
            AUTHORIZATION [dbo]';  
                SET NOCOUNT ON;  
                INSERT  [tempdb].[dbo].[$(CompletedBatches)] (BatchId, Description)  
                VALUES                                      (0, N'CreateElementStep Sales batch 0');  
                SET NOCOUNT OFF;  
            END  
  
        ```  
  
        Beachten Sie, dass CREATE SCHEMA eine der Anweisungen ist, die innerhalb der IF-Anweisung in eine EXECUTE sp_executesql-Anweisung eingeschlossen werden muss. Anweisungen, wie etwa CREATE TABLE, benötigen die EXECUTE sp_executesql-Anweisung nicht und ähneln folgendem Beispiel:  
  
        ```  
        IF NOT EXISTS (SELECT 1  
                       FROM   [tempdb].[dbo].[$(CompletedBatches)]  
                       WHERE  [BatchId] = 1)  
            BEGIN  
                CREATE TABLE [Sales].[Customer] (  
                    [CustomerID]   INT           IDENTITY (1, 1) NOT NULL,  
                    [CustomerName] NVARCHAR (40) NOT NULL,  
                    [YTDOrders]    INT           NOT NULL,  
                    [YTDSales]     INT           NOT NULL  
                );  
                SET NOCOUNT ON;  
                INSERT  [tempdb].[dbo].[$(CompletedBatches)] (BatchId, Description)  
                VALUES                                      (1, N'CreateElementStep Sales.Customer batch 0');  
                SET NOCOUNT OFF;  
            END  
  
        ```  
  
        > [!NOTE]  
        > Falls Sie ein Datenbankprojekt bereitstellen, das mit der Zieldatenbank identisch ist, ist der daraus resultierende Bericht nicht sehr aussagekräftig. Weitere aussagekräftige Ergebnisse erhalten Sie, wenn Sie Änderungen an einer Datenbank bereitstellen oder eine neue Datenbank bereitstellen.  
  
## <a name="command-line-deployment-using-generated-dacpac-file"></a>Befehlszeilenbereitstellung mit der generierten DACPAC-Datei  
Sobald ein SQL-Projekt erstellt wurde, wird eine DACPAC-Datei erstellt, die zum Bereitstellen des Schemas über die Befehlszeile verwendet werden kann und die die Bereitstellung über einen anderen Computer als einen Buildcomputer aktivieren kann. SqlPackage ist ein Befehlszeilen-Hilfsprogramm, das die Bereitstellung von DACPAC-Dateien mit vollem Optionsumfang ermöglicht, mit denen Benutzer unter anderem eine DACPAC-Datei bereitstellen oder ein Bereitstellungsskript generieren können. Weitere Informationen finden Sie unter [SqlPackage.exe](https://msdn.microsoft.com/library/hh550080(v=VS.103).aspx).  
  
> [!NOTE]  
> Zur erfolgreichen Bereitstellung von DACPAC-Dateien, die über Projekte mit definierter DeploymentContributors-Eigenschaft erstellt wurden, müssen die DLLs, die Ihre Bereitstellungs-Contributors enthalten, auf dem verwendeten Computer installiert sein. Dies ist der Fall, weil sie für eine erfolgreiche Bereitstellung als erforderlich markiert wurden.  
>   
> Sie vermeiden diese Anforderung, indem Sie den Bereitstellungs-Contributor von der SQLPROJ-Datei ausschließen. Legen Sie stattdessen Contributors fest, die während der Bereitstellung mithilfe des SqlPackage mit dem **AdditionalDeploymentContributors**-Parameter ausgeführt werden sollen. Dies ist hilfreich, wenn Sie einen Contributor nur bei besonderen Umständen verwenden möchten, wie etwa beim Bereitstellen eines spezifischen Servers.  
  
## <a name="next-steps"></a>Next Steps  
Sie können mit anderen Änderungen an Bereitstellungsplänen experimentieren, bevor diese ausgeführt werden. Andere Änderungstypen:  
  
-   Hinzufügen einer erweiterten Eigenschaft zu allen Datenbankobjekten, denen eine Versionsnummer zugeordnet ist.  
  
-   Hinzufügen oder Entfernen weiterer Diagnosedruckanweisungen oder Kommentare zu/aus Bereitstellungsskripts.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Anpassen der Datenbankerstellung und -bereitstellung durch Erstellungs- und Bereitstellungs-Contributors](../ssdt/use-deployment-contributors-to-customize-database-build-and-deployment.md)  
[Exemplarische Vorgehensweise: Datenbankprojekt erweitern, um Modellstatistiken zu generieren](../ssdt/walkthrough-extend-database-project-build-to-generate-model-statistics.md)  
[Exemplarische Vorgehensweise: Bereitstellung des Datenbankprojekts erweitern, um den Bereitstellungsplan zu analysieren](../ssdt/walkthrough-extend-database-project-deployment-to-analyze-the-deployment-plan.md)  
  
