---
title: 'Exemplarische Vorgehensweise: Erweitern der Bereitstellung eines Datenbankprojekts zum Analysieren des Bereitstellungsplans | Microsoft-Dokumentation'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 9ead8470-93ba-44e3-8848-b59322e37621
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 13e2b010a193e8c610c54a5b619d8a67c9b4d2d3
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2019
ms.locfileid: "65097457"
---
# <a name="walkthrough-extend-database-project-deployment-to-analyze-the-deployment-plan"></a>Exemplarische Vorgehensweise: Erweitern der Bereitstellung eines Datenbankprojekts für die Analyse des Bereitstellungsplans
Sie können Bereitstellungs-Contributors erstellen, um benutzerdefinierte Aktionen durchzuführen, wenn Sie ein SQL-Projekt bereitstellen. Sie können DeploymentPlanModifier oder DeploymentPlanExecutor erstellen. Verwenden Sie DeploymentPlanModifier, um den Plan zu ändern, bevor er ausgeführt wird, und DeploymentPlanExecutor, um Vorgänge durchzuführen, während der Plan ausgeführt wird. In dieser exemplarischen Vorgehensweise erstellen Sie einen DeploymentPlanExecutor mit der Bezeichnung DeploymentUpdateReportContributor, der einen Bericht über die Aktionen erstellt, die beim Bereitstellen eines Datenbankprojekts ausgeführt werden. Da dieser Erstellungs-Contributor einen Parameter akzeptiert, mit dem gesteuert wird, ob der Bericht erstellt wird, müssen Sie einen weiteren erforderlichen Schritt durchführen.  
  
In dieser exemplarischen Vorgehensweise führen Sie folgende Hauptaufgaben aus:  
  
-   [Erstellen des DeploymentPlanExecutor-Typs des Bereitstellungs-Contributors](#CreateDeploymentContributor)  
  
-   [Installieren des Bereitstellungs-Contributors](#InstallDeploymentContributor)  
  
-   [Testen des Bereitstellungs-Contributors](#TestDeploymentContributor)  
  
## <a name="prerequisites"></a>Voraussetzungen  
Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Sie müssen eine Version von Visual Studio installiert haben, die SQL Server Data Tools (SSDT) enthält und die Entwicklung in C# oder VB unterstützt.  
  
-   Sie müssen über ein SQL-Projekt verfügen, das SQL-Objekte enthält.  
  
-   Eine Instanz von SQL Server, auf der Sie ein Datenbankprojekt bereitstellen können.  
  
> [!NOTE]  
> Diese exemplarische Vorgehensweise ist für Benutzer gedacht, die bereits mit den SQL-Funktionen von SSDT vertraut sind. Außerdem wird von Ihnen erwartet, dass Sie mit den grundlegenden Visual Studio-Konzepten vertraut sind, wie etwa dem Erstellen einer Klassenbibliothek und dem Verwenden des Code-Editor zum Hinzufügen von Code zu einer Klasse.  
  
## <a name="CreateDeploymentContributor"></a>Erstellen eines Bereitstellungs-Contributors  
Zum Erstellen eines Bereitstellungs-Contributors führen Sie folgende Aufgaben aus:  
  
-   Erstellen Sie ein Klassenbibliotheksprojekt, und fügen Sie die erforderlichen Verweise hinzu.  
  
-   Definieren Sie eine Klasse mit der Bezeichnung „DeploymentUpdateReportContributor“, die von [DeploymentPlanExecutor](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplanexecutor.aspx) erbt.  
  
-   Überschreiben Sie die OnExecute-Methode.  
  
-   Fügen Sie eine private Hilfsklasse hinzu.  
  
-   Erstellen Sie die resultierende Assembly.  
  
#### <a name="to-create-a-class-library-project"></a>So erstellen Sie ein Klassenbibliotheksprojekt  
  
1.  Erstellen Sie ein Visual Basic- oder ein Visual C#-Klassenbibliotheksprojekt mit der Bezeichnung MyDeploymentContributor.  
  
2.  Benennen Sie die Datei „Class1.cs“ in „DeploymentUpdateReportContributor.cs“ um.  
  
3.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Projektknoten, und klicken Sie dann auf **Verweis hinzufügen**.  
  
4.  Wählen Sie auf der Registerkarte „Frameworks“ die Option **System.ComponentModel.Composition** aus.  
  
5.  Fügen Sie die erforderlichen SQL-Verweise hinzu: Klicken Sie mit der rechten Maustaste auf den Projektknoten, und klicken Sie dann auf **Verweis hinzufügen**. Klicken Sie auf **Durchsuchen**, und navigieren Sie zum Ordner **C:\Programme (x86)\Microsoft SQL Server\110\DAC\Bin**. Wählen Sie die Einträge **Microsoft.SqlServer.Dac.dll**, **Microsoft.SqlServer.Dac.Extensions.dll** und **Microsoft.Data.Tools.Schema.Sql.dll** aus, klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **OK**.  
  
    Beginnen Sie als Nächstes, der Klasse Code hinzuzufügen.  
  
#### <a name="to-define-the-deploymentupdatereportcontributor-class"></a>So definieren Sie die DeploymentUpdateReportContributor-Klasse  
  
1.  Aktualisieren Sie im Code-Editor die Datei „DeploymentUpdateReportContributor.cs“, damit sie folgenden **using**-Anweisungen entspricht:  
  
    ```csharp  
    using System;  
    using System.IO;  
    using System.Text;  
    using System.Xml;  
    using Microsoft.SqlServer.Dac.Deployment;  
    using Microsoft.SqlServer.Dac.Extensibility;  
    using Microsoft.SqlServer.Dac.Model;  
  
    ```  
  
2.  Aktualisieren Sie die Klassendefinition, damit sie folgendem Objekt entspricht:  
  
    ```csharp  
    /// <summary>  
        /// An executor that generates a report detailing the steps in the deployment plan. Will only run  
        /// if a "GenerateUpdateReport=true" contributor argument is set in the project file, in a targets file or  
        /// passed as an additional argument to the DacServices API. To set in a project file, add the following:  
        ///   
        /// <PropertyGroup>  
        ///     <ContributorArguments Condition="'$(Configuration)' == 'Debug'">  
        /// $(ContributorArguments);DeploymentUpdateReportContributor.GenerateUpdateReport=true;  
        ///     </ContributorArguments>  
        /// <PropertyGroup>  
        ///   
        /// </summary>  
        [ExportDeploymentPlanExecutor("MyDeploymentContributor.DeploymentUpdateReportContributor", "1.0.0.0")]  
        public class DeploymentUpdateReportContributor : DeploymentPlanExecutor  
        {  
        }  
  
    ```  
  
    Sie haben jetzt Ihren Bereitstellungs-Contributor definiert, der von DeploymentPlanExecutor erbt. Während des Erstellungs- und Bereitstellungsprozesses werden benutzerdefinierte Contributors aus dem Standarderweiterungsverzeichnis geladen. Den Bereitstellungsplan ausführende Contributors werden anhand eines [ExportDeploymentPlanExecutor](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.exportdeploymentplanexecutorattribute.aspx)-Attributs identifiziert.  
  
    Dieses Attribut muss angegeben werden, damit die Contributors ermittelt werden können. Es sollte ungefähr wie folgt aussehen:  
  
    ```csharp  
    [ExportDeploymentPlanExecutor("MyDeploymentContributor.DeploymentUpdateReportContributor", "1.0.0.0")]  
  
    ```  
  
    In diesem Fall muss der erste Parameter des Attributs ein eindeutiger Bezeichner sein. Dieser wird verwendet, um den Contributor in Projektdateien zu kennzeichnen. Eine bewährte Methode besteht darin, den Namespace Ihrer Bibliothek – „MyDeploymentContributor“ im Rahmen dieser exemplarischen Vorgehensweise – mit dem Klassennamen – das ist hier „DeploymentUpdateReportContributor“ – zu kombinieren, um den Bezeichner zu erstellen.  
  
3.  Fügen Sie als Nächstes den folgenden Member hinzu, den Sie verwenden, um diesem Anbieter das Akzeptieren eines Befehlszeilenparameters zu ermöglichen:  
  
    ```csharp  
    public const string GenerateUpdateReport = "DeploymentUpdateReportContributor.GenerateUpdateReport";  
    ```  
  
    Dieser Member ermöglicht dem Benutzer mithilfe der Option GenerateUpdateReport das Angeben, ob der Bericht generiert werden soll.  
  
    Als Nächstes überschreiben Sie die OnExecute-Methode und fügen den Code hinzu, den Sie bei der Bereitstellung eines Datenbankprojekts ausführen.  
  
#### <a name="to-override-onexecute"></a>So überschreiben Sie OnExecute  
  
-   Fügen Sie die folgende Methode der DeploymentUpdateReportContributor-Klasse hinzu:  
  
    ```csharp  
    /// <summary>  
            /// Override the OnExecute method to perform actions when you execute the deployment plan for  
            /// a database project.  
            /// </summary>  
            protected override void OnExecute(DeploymentPlanContributorContext context)  
            {  
                // determine whether the user specified a report is to be generated  
                bool generateReport = false;  
                string generateReportValue;  
                if (context.Arguments.TryGetValue(GenerateUpdateReport, out generateReportValue) == false)  
                {  
                    // couldn't find the GenerateUpdateReport argument, so do not generate  
                    generateReport = false;  
                }  
                else  
                {  
                    // GenerateUpdateReport argument was specified, try to parse the value  
                    if (bool.TryParse(generateReportValue, out generateReport))  
                    {  
                        // if we end up here, the value for the argument was not valid.  
                        // default is false, so do nothing.  
                    }  
                }  
  
                if (generateReport == false)  
                {  
                    // if user does not want to generate a report, we are done  
                    return;  
                }  
  
                // We will output to the same directory where the deployment script  
                // is output or to the current directory  
                string reportPrefix = context.Options.TargetDatabaseName;  
                string reportPath;  
                if (string.IsNullOrEmpty(context.DeploymentScriptPath))  
                {  
                    reportPath = Environment.CurrentDirectory;  
                }  
                else  
                {  
                    reportPath = Path.GetDirectoryName(context.DeploymentScriptPath);  
                }  
                FileInfo summaryReportFile = new FileInfo(Path.Combine(reportPath, reportPrefix + ".summary.xml"));  
                FileInfo detailsReportFile = new FileInfo(Path.Combine(reportPath, reportPrefix + ".details.xml"));  
  
                // Generate the reports by using the helper class DeploymentReportWriter  
                DeploymentReportWriter writer = new DeploymentReportWriter(context);  
                writer.WriteReport(summaryReportFile);  
                writer.IncludeScripts = true;  
                writer.WriteReport(detailsReportFile);  
  
                string msg = "Deployment reports ->"  
                    + Environment.NewLine + summaryReportFile.FullName  
                    + Environment.NewLine + detailsReportFile.FullName;  
  
                ExtensibilityError reportMsg = new ExtensibilityError(msg, Severity.Message);  
                base.PublishMessage(reportMsg);  
            }  
        /// <summary>  
        /// Override the OnExecute method to perform actions when you execute the deployment plan for  
        /// a database project.  
        /// </summary>  
            protected override void OnExecute(DeploymentPlanContributorContext context)  
            {  
                // determine whether the user specified a report is to be generated  
                bool generateReport = false;  
                string generateReportValue;  
                if (context.Arguments.TryGetValue(GenerateUpdateReport, out generateReportValue) == false)  
                {  
                    // couldn't find the GenerateUpdateReport argument, so do not generate  
                    generateReport = false;  
                }  
                else  
                {  
                    // GenerateUpdateReport argument was specified, try to parse the value  
                    if (bool.TryParse(generateReportValue, out generateReport))  
                    {  
                        // if we end up here, the value for the argument was not valid.  
                        // default is false, so do nothing.  
                    }  
                }  
  
                if (generateReport == false)  
                {  
                    // if user does not want to generate a report, we are done  
                    return;  
                }  
  
                // We will output to the same directory where the deployment script  
                // is output or to the current directory  
                string reportPrefix = context.Options.TargetDatabaseName;  
                string reportPath;  
                if (string.IsNullOrEmpty(context.DeploymentScriptPath))  
                {  
                    reportPath = Environment.CurrentDirectory;  
                }  
                else  
                {  
                    reportPath = Path.GetDirectoryName(context.DeploymentScriptPath);  
                }  
                FileInfo summaryReportFile = new FileInfo(Path.Combine(reportPath, reportPrefix + ".summary.xml"));  
                FileInfo detailsReportFile = new FileInfo(Path.Combine(reportPath, reportPrefix + ".details.xml"));  
  
                // Generate the reports by using the helper class DeploymentReportWriter  
                DeploymentReportWriter writer = new DeploymentReportWriter(context);  
                writer.WriteReport(summaryReportFile);  
                writer.IncludeScripts = true;  
                writer.WriteReport(detailsReportFile);  
  
                string msg = "Deployment reports ->"  
                    + Environment.NewLine + summaryReportFile.FullName  
                    + Environment.NewLine + detailsReportFile.FullName;  
  
                DataSchemaError reportMsg = new DataSchemaError(msg, ErrorSeverity.Message);  
                base.PublishMessage(reportMsg);  
            }  
    ```  
  
    An die OnExecute-Methode wird ein [DeploymentPlanContributorContext](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplancontributorcontext.aspx)-Objekt übergeben, das Zugriff auf alle angegebenen Argumente, das Quell- und Zieldatenbankmodell, die Erstellungseigenschaften und die Erweiterungsdateien bietet. In diesem Beispiel rufen wir das Modell ab und anschließend Hilfefunktionen auf, mit denen Informationen über das Modell ausgegeben werden. Wir verwenden die PublishMessage-Hilfemethode in der Basisklasse, um sämtliche auftretenden Fehler zu melden.  
  
    Weitere interessante Typen und Methoden: [TSqlModel](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.model.tsqlmodel.aspx), [ModelComparisonResult](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.modelcomparisonresult.aspx), [DeploymentPlanHandle](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplanhandle.aspx) und [SqlDeploymentOptions](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.sqldeploymentoptions.aspx).  
  
    Als Nächstes definieren Sie die Hilfsklasse, die in die Details des Bereitstellungsplans eintaucht.  
  
#### <a name="to-add-the-helper-class-that-generates-the-report-body"></a>So fügen Sie die Hilfsklasse hinzu, die den Berichtshauptteil erstellt  
  
-   Fügen Sie die Hilfsklasse und ihre Methoden hinzu, indem Sie folgenden Code hinzufügen:  
  
    ```csharp  
    /// <summary>  
            /// This class is used to generate a deployment  
            /// report.   
            /// </summary>  
            private class DeploymentReportWriter  
            {  
                readonly TSqlModel _sourceModel;  
                readonly ModelComparisonResult _diff;  
                readonly DeploymentStep _planHead;  
  
                /// <summary>  
                /// The constructor accepts the same context info  
                /// that was passed to the OnExecute method of the  
                /// deployment contributor.  
                /// </summary>  
                public DeploymentReportWriter(DeploymentPlanContributorContext context)  
                {  
                    if (context == null)  
                    {  
                        throw new ArgumentNullException("context");  
                    }  
  
                    // save the source model, source/target differences,  
                    // and the beginning of the deployment plan.  
                    _sourceModel = context.Source;  
                    _diff = context.ComparisonResult;  
                    _planHead = context.PlanHandle.Head;  
                }  
                /// <summary>  
                /// Property indicating whether script bodies  
                /// should be included in the report.  
                /// </summary>  
                public bool IncludeScripts { get; set; }  
  
                /// <summary>  
                /// Drives the report generation, opening files,   
                /// writing the beginning and ending report elements,  
                /// and calling helper methods to report on the  
                /// plan operations.  
                /// </summary>  
                internal void WriteReport(FileInfo reportFile)  
                {// Assumes that we have a valid report file  
                    if (reportFile == null)  
                    {  
                        throw new ArgumentNullException("reportFile");  
                    }  
  
                    // set up the XML writer  
                    XmlWriterSettings xmlws = new XmlWriterSettings();  
                    // Indentation makes it a bit more readable  
                    xmlws.Indent = true;  
                    FileStream fs = new FileStream(reportFile.FullName, FileMode.Create, FileAccess.Write, FileShare.ReadWrite);  
                    XmlWriter xmlw = XmlWriter.Create(fs, xmlws);  
  
                    try  
                    {  
                        xmlw.WriteStartDocument(true);  
                        xmlw.WriteStartElement("DeploymentReport");  
  
                        // Summary report of the operations that  
                        // are contained in the plan.  
                        ReportPlanOperations(xmlw);  
  
                        // You could add a method call here  
                        // to produce a detailed listing of the   
                        // differences between the source and  
                        // target model.  
                        xmlw.WriteEndElement();  
                        xmlw.WriteEndDocument();  
                        xmlw.Flush();  
                        fs.Flush();  
                    }  
                    finally  
                    {  
                        xmlw.Close();  
                        fs.Dispose();  
                    }  
                }  
  
                /// <summary>  
                /// Writes details for the various operation types  
                /// that could be contained in the deployment plan.  
                /// Optionally writes script bodies, depending on  
                /// the value of the IncludeScripts property.  
                /// </summary>  
                private void ReportPlanOperations(XmlWriter xmlw)  
                {// write the node to indicate the start  
                    // of the list of operations.  
                    xmlw.WriteStartElement("Operations");  
  
                    // Loop through the steps in the plan,  
                    // starting at the beginning.  
                    DeploymentStep currentStep = _planHead;  
                    while (currentStep != null)  
                    {  
                        // Report the type of step  
                        xmlw.WriteStartElement(currentStep.GetType().Name);  
  
                        // based on the type of step, report  
                        // the relevant information.  
                        // Note that this procedure only handles   
                        // a subset of all step types.  
                        if (currentStep is SqlRenameStep)  
                        {  
                            SqlRenameStep renameStep = (SqlRenameStep)currentStep;  
                            xmlw.WriteAttributeString("OriginalName", renameStep.OldName);  
                            xmlw.WriteAttributeString("NewName", renameStep.NewName);  
                            xmlw.WriteAttributeString("Category", GetElementCategory(renameStep.RenamedElement));  
                        }  
                        else if (currentStep is SqlMoveSchemaStep)  
                        {  
                            SqlMoveSchemaStep moveStep = (SqlMoveSchemaStep)currentStep;  
                            xmlw.WriteAttributeString("OrignalName", moveStep.PreviousName);  
                            xmlw.WriteAttributeString("NewSchema", moveStep.NewSchema);  
                            xmlw.WriteAttributeString("Category", GetElementCategory(moveStep.MovedElement));  
                        }  
                        else if (currentStep is SqlTableMigrationStep)  
                        {  
                            SqlTableMigrationStep dmStep = (SqlTableMigrationStep)currentStep;  
                            xmlw.WriteAttributeString("Name", GetElementName(dmStep.SourceTable));  
                            xmlw.WriteAttributeString("Category", GetElementCategory(dmStep.SourceElement));  
                        }  
                        else if (currentStep is CreateElementStep)  
                        {  
                            CreateElementStep createStep = (CreateElementStep)currentStep;  
                            xmlw.WriteAttributeString("Name", GetElementName(createStep.SourceElement));  
                            xmlw.WriteAttributeString("Category", GetElementCategory(createStep.SourceElement));  
                        }  
                        else if (currentStep is AlterElementStep)  
                        {  
                            AlterElementStep alterStep = (AlterElementStep)currentStep;  
                            xmlw.WriteAttributeString("Name", GetElementName(alterStep.SourceElement));  
                            xmlw.WriteAttributeString("Category", GetElementCategory(alterStep.SourceElement));  
                        }  
                        else if (currentStep is DropElementStep)  
                        {  
                            DropElementStep dropStep = (DropElementStep)currentStep;  
                            xmlw.WriteAttributeString("Name", GetElementName(dropStep.TargetElement));  
                            xmlw.WriteAttributeString("Category", GetElementCategory(dropStep.TargetElement));  
                        }  
  
                        // If the script bodies are to be included,  
                        // add them to the report.  
                        if (this.IncludeScripts)  
                        {  
                            using (StringWriter sw = new StringWriter())  
                            {  
                                currentStep.GenerateBatchScript(sw);  
                                string tsqlBody = sw.ToString();  
                                if (string.IsNullOrEmpty(tsqlBody) == false)  
                                {  
                                    xmlw.WriteCData(tsqlBody);  
                                }  
                            }  
                        }  
  
                        // close off the current step  
                        xmlw.WriteEndElement();  
                        currentStep = currentStep.Next;  
                    }  
                    xmlw.WriteEndElement();  
                }  
  
                /// <summary>  
                /// Returns the category of the specified element  
                /// in the source model  
                /// </summary>  
                private string GetElementCategory(TSqlObject element)  
                {  
                    return element.ObjectType.Name;  
                }  
  
                /// <summary>  
                /// Returns the name of the specified element  
                /// in the source model  
                /// </summary>  
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
            }        /// <summary>  
            /// This class is used to generate a deployment  
            /// report.   
            /// </summary>  
            private class DeploymentReportWriter  
            {  
                /// <summary>  
                /// The constructor accepts the same context info  
                /// that was passed to the OnExecute method of the  
                /// deployment contributor.  
                /// </summary>  
                public DeploymentReportWriter(DeploymentPlanContributorContext context)  
                {  
               }  
                /// <summary>  
                /// Property indicating whether script bodies  
                /// should be included in the report.  
                /// </summary>  
                public bool IncludeScripts { get; set; }  
  
                /// <summary>  
                /// Drives the report generation, opening files,   
                /// writing the beginning and ending report elements,  
                /// and calling helper methods to report on the  
                /// plan operations.  
                /// </summary>  
                internal void WriteReport(FileInfo reportFile)  
                {  
                }  
  
                /// <summary>  
                /// Writes details for the various operation types  
                /// that could be contained in the deployment plan.  
                /// Optionally writes script bodies, depending on  
                /// the value of the IncludeScripts property.  
                /// </summary>  
                private void ReportPlanOperations(XmlWriter xmlw)  
                {  
                }  
  
                /// <summary>  
                /// Returns the category of the specified element  
                /// in the source model  
                /// </summary>  
                private string GetElementCategory(IModelElement element)  
                {  
                }  
  
                /// <summary>  
                /// Returns the name of the specified element  
                /// in the source model  
                /// </summary>  
                private string GetElementName(IModelElement element)  
                {  
                }  
            }  
    ```  
  
-   Speichern Sie die Änderungen in der Klassendatei. In der Hilfsklasse wird auf eine Reihe hilfreicher Typen verwiesen:  
  
    |**Codebereich**|**Hilfreiche Typen**|  
    |-----------------|--------------------|  
    |Klassenmember|[TSqlModel](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.model.tsqlmodel.aspx), [ModelComparisonResult](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.modelcomparisonresult.aspx), [DeploymentStep](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentstep.aspx)|  
    |WriteReport-Methode|XmlWriter und XmlWriterSettings|  
    |ReportPlanOperations-Methode|Wichtige Typen enthalten Folgendes: [DeploymentStep](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentstep.aspx), [SqlRenameStep](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.sqlrenamestep.aspx), [SqlMoveSchemaStep](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.sqlmoveschemastep.aspx), [SqlTableMigrationStep](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.sqltablemigrationstep.aspx), [CreateElementStep](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.createelementstep.aspx), [AlterElementStep](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.alterelementstep.aspx), [DropElementStep](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.dropelementstep.aspx).<br /><br />Es gibt zahlreiche andere Schritte. Eine vollständige Liste der Schritte finden Sie in der API-Dokumentation.|  
    |GetElementCategory|[TSqlObject](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.model.tsqlobject.aspx)|  
    |GetElementName|[TSqlObject](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.model.tsqlobject.aspx)|  
  
    Als Nächstes erstellen Sie die Klassenbibliothek.  
  
#### <a name="to-sign-and-build-the-assembly"></a>So signieren und erstellen Sie die Assembly  
  
1.  Klicken Sie im Menü **Projekt** auf **Eigenschaften von MyDeploymentContributor**.  
  
2.  Klicken Sie auf die Registerkarte **Signierung** .  
  
3.  Klicken Sie auf **Assembly signieren**.  
  
4.  Klicken Sie unter **Schlüsseldatei mit starkem Namen auswählen:** auf **<New>** .  
  
5.  Geben Sie im Dialogfeld **Schlüssel für einen starken Namen erstellen** unter **Schlüsseldateiname** **MyRefKey**ein.  
  
6.  (optional) Sie können ein Kennwort für Ihre Schlüsseldatei mit starkem Namen angeben.  
  
7.  Klicken Sie auf **OK**.  
  
8.  Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
9. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
Als Nächstes müssen Sie die Assembly installieren, damit sie geladen wird, wenn Sie SQL-Projekte erstellen und bereitstellen.  
  
## <a name="InstallDeploymentContributor"></a>Installieren eines Bereitstellungs-Contributors  
Zum Installieren eines Bereitstellungs-Contributors müssen Sie die Assembly und die zugehörige PDB-Datei in den Erweiterungsordner kopieren.  
  
#### <a name="to-install-the-mydeploymentcontributor-assembly"></a>So installieren Sie die MyDeploymentContributor-Assembly  
  
-   Im nächsten Schritt kopieren Sie die Assemblyinformationen in das Verzeichnis „Extensions“. Beim Start von Visual Studio werden alle Erweiterungen im Ordner %Programme%\Microsoft SQL Server\110\DAC\Bin\Extensions und dessen Unterverzeichnissen identifiziert und für die Verwendung zur Verfügung gestellt:  
  
-   Kopieren Sie die Assemblydatei **MyDeploymentContributor.dll** aus dem Ausgabeverzeichnis in das Verzeichnis „%Programme%\Microsoft SQL Server\110\DAC\Bin\Extensions“. Der Pfad Ihrer kompilierten DLL-Datei lautet standardmäßig IhrProjektmappenpfad\IhrProjektpfad\bin\Debug oder IhrProjektmappenpfad\IhrProjektpfad\bin\Release.  
  
## <a name="TestDeploymentContributor"></a>Testen eines Bereitstellungs-Contributors  
Zum Testen eines Bereitstellungs-Contributors führen Sie folgende Aufgaben aus:  
  
-   Fügen Sie der SQLPROJ-Datei, die Sie bereitzustellen planen, Eigenschaften hinzu.  
  
-   Stellen Sie das Projekt mithilfe von MSBuild und durch Angeben des entsprechenden Parameters bereit.  
  
### <a name="add-properties-to-the-sql-project-sqlproj-file"></a>So fügen Sie der SQL Project (.sqlproj)-Datei Eigenschaften hinzu  
Sie müssen die SQL-Projektdatei immer aktualisieren, um die ID der Contributor festzulegen, die Sie ausführen möchten. Da von diesem Contributor zudem ein „GenerateUpdateReport“-Argument erwartet wird, muss dieses als Contributor-Argument angegeben werden.  
  
Dazu haben Sie zwei Möglichkeiten: Sie können die SQLPROJ-Datei manuell bearbeiten, um die erforderlichen Argumente hinzuzufügen. Sie können sich dafür entscheiden, falls Ihr Contributor über keine Contributor-Argumente verfügt, die zur Konfiguration erforderlich sind, oder falls Sie den Contributor nicht für eine große Anzahl von Projekten wiederverwenden möchten. Falls Sie diese Option wählen, fügen Sie der SQLPROJ-Datei nach dem ersten Importknoten in der Datei die folgenden Anweisungen hinzu:  
  
```  
<PropertyGroup>  
    <DeploymentContributors>$(DeploymentContributors); MyDeploymentContributor.DeploymentUpdateReportContributor</DeploymentContributors>  
<ContributorArguments Condition="'$(Configuration)' == 'Debug'">$(ContributorArguments);DeploymentUpdateReportContributor.GenerateUpdateReport=true;</ContributorArguments>  
  </PropertyGroup>  
```  
  
Die zweite Methode ist das Erstellen einer Zieledatei, die die erforderlichen Contributorargumente enthält. Diese ist hilfreich, falls Sie denselben Contributor für mehrere Projekte verwenden und Contributorargumente erforderlich sind, da sie die Standardwerte enthält. Erstellen Sie in diesem Fall eine Zieledatei im MSBuild-Erweiterungspfad.  
  
1.  Navigieren Sie zu %Programme%\MSBuild.  
  
2.  Erstellen Sie einen neuen Ordner namens „MyContributors“, in dem Ihre Zieldateien gespeichert werden.  
  
3.  Erstellen Sie in diesem Verzeichnis eine neue Datei namens „MyContributors.targets“, fügen Sie den folgenden Text hinzu, und speichern Sie die Datei:  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
  
    <Project xmlns="https://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
    <DeploymentContributors>$(DeploymentContributors);MyDeploymentContributor.DeploymentUpdateReportContributor</DeploymentContributors>  
    <ContributorArguments Condition="'$(Configuration)' == 'Debug'">$(ContributorArguments); DeploymentUpdateReportContributor.GenerateUpdateReport=true;</ContributorArguments>  
      </PropertyGroup>  
    </Project>  
    ```  
  
4.  Importieren Sie in die SQLPROJ-Datei für jedes Projekt, in dem Sie Contributors ausführen möchten, die Zieldatei durch Hinzufügen folgender Anweisung zur SQLPROJ-Datei nach dem Knoten \<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v$(VisualStudioVersion)\SSDT\Microsoft.Data.Tools.Schema.SqlTasks.targets" \/> in der Datei:  
  
    ```  
    <Import Project="$(MSBuildExtensionsPath)\MyContributors\MyContributors.targets " />  
    ```  
  
Nach dem Durchführen einer dieser Vorgehensweisen können Sie MSBuild verwenden, um die Parameter für Befehlszeilenbuilds zu übertragen.  
  
> [!NOTE]  
> Sie müssen die Eigenschaft „DeploymentContributors“ stets aktualisieren, damit Ihre Contributor-ID angegeben wird. Dies ist dieselbe ID, wie im Attribut „ExportDeploymentPlanExecutor“ in der Contributorquelldatei verwendet wird. Ohne diese wird Ihr Contributor nicht ausgeführt, wenn Sie das Projekt erstellen. Die Eigenschaft „ContributorArguments“ muss nur aktualisiert werden, wenn Argumente erforderlich sind, damit Ihr Contributor ausgeführt werden kann.  
  
### <a name="deploy-the-database-project"></a>Das Datenbankprojekt bereitstellen  
Ihr Projekt kann in Visual Studio normal veröffentlicht oder bereitgestellt werden. Öffnen Sie einfach eine Projektmappe, die Ihr SQL-Projekt enthält, und wählen Sie im Kontextmenü des Projekts die Option „Veröffentlichen...“, oder verwenden Sie F5 für eine Debug-Bereitstellung in LocalDB. In diesem Beispiel wird das Dialogfeld „Veröffentlichen...“ verwendet, um ein Bereitstellungsskript zu generieren.  
  
##### <a name="to-deploy-your-sql-project-and-generate-a-deployment-report"></a>So stellen Sie Ihr SQL-Projekt bereit und generieren einen Bereitstellungsbericht  
  
1.  Öffnen Sie Visual Studio und die Projektmappe, die Ihr SQL-Projekt enthält.  
  
2.  Wählen Sie Ihr Projekt aus, und drücken Sie F5, um eine Debug-Bereitstellung durchzuführen. Hinweis: Da das ContributorArguments-Element so festgelegt ist, dass es nur enthalten ist, falls die Konfiguration „Debuggen“ lautet, wird der Bereitstellungsbericht zurzeit nur für Debugbereitstellungen generiert. Um dies zu ändern, entfernen Sie die Anweisung „Condition="'$(Configuration)' == 'Debug'"“ aus der Definition „ContributorArguments“.  
  
3.  Eine Ausgabe wie folgende sollte im Ausgabefenster zu sehen sein:  
  
    ```  
    ------ Deploy started: Project: Database1, Configuration: Debug Any CPU ------  
    Finished verifying cached model in 00:00:00  
    Deployment reports ->  
  
      C:\Users\UserName\Documents\Visual Studio 2012\Projects\MyDatabaseProject\MyDatabaseProject\sql\debug\MyTargetDatabase.summary.xml  
      C:\Users\UserName\Documents\Visual Studio 2012\Projects\MyDatabaseProject\MyDatabaseProject\sql\debug\MyTargetDatabase.details.xml  
  
      Deployment script generated to:  
      C:\Users\UserName\Documents\Visual Studio 2012\Projects\MyDatabaseProject\MyDatabaseProject\sql\debug\MyDatabaseProject.sql  
  
    ```  
  
4.  Öffnen Sie MyTargetDatabase.summary.xml, und untersuchen Sie den Inhalt. Die Datei ähnelt folgendem Beispiel, das eine neue Datenbankbereitstellung zeigt:  
  
    ```  
    <?xml version="1.0" encoding="utf-8" standalone="yes"?>  
    <DeploymentReport>  
      <Operations>  
        <DeploymentScriptStep />  
        <DeploymentScriptDomStep />  
        <DeploymentScriptStep />  
        <DeploymentScriptDomStep />  
        <DeploymentScriptStep />  
        <DeploymentScriptStep />  
        <DeploymentScriptStep />  
        <DeploymentScriptStep />  
        <DeploymentScriptDomStep />  
        <DeploymentScriptDomStep />  
        <DeploymentScriptDomStep />  
        <DeploymentScriptDomStep />  
        <DeploymentScriptStep />  
        <DeploymentScriptDomStep />  
        <BeginPreDeploymentScriptStep />  
        <DeploymentScriptStep />  
        <EndPreDeploymentScriptStep />  
        <SqlBeginPreservationStep />  
        <SqlEndPreservationStep />  
        <SqlBeginDropsStep />  
        <SqlEndDropsStep />  
        <SqlBeginAltersStep />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales" Category="Schema" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.Customer" Category="Table" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.PK_Customer_CustID" Category="Primary Key" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.Orders" Category="Table" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.PK_Orders_OrderID" Category="Primary Key" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.Def_Customer_YTDOrders" Category="Default Constraint" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.Def_Customer_YTDSales" Category="Default Constraint" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.Def_Orders_OrderDate" Category="Default Constraint" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.Def_Orders_Status" Category="Default Constraint" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.FK_Orders_Customer_CustID" Category="Foreign Key" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.CK_Orders_FilledDate" Category="Check Constraint" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.CK_Orders_OrderDate" Category="Check Constraint" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.uspCancelOrder" Category="Procedure" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.uspFillOrder" Category="Procedure" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.uspNewCustomer" Category="Procedure" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.uspPlaceNewOrder" Category="Procedure" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.uspShowOrderDetails" Category="Procedure" />  
        <SqlEndAltersStep />  
        <DeploymentScriptStep />  
        <BeginPostDeploymentScriptStep />  
        <DeploymentScriptStep />  
        <EndPostDeploymentScriptStep />  
        <DeploymentScriptDomStep />  
        <DeploymentScriptDomStep />  
        <DeploymentScriptDomStep />  
      </Operations>  
    </DeploymentReport>  
  
    ```  
  
    > [!NOTE]  
    > Falls Sie ein Datenbankprojekt bereitstellen, das mit der Zieldatenbank identisch ist, ist der daraus resultierende Bericht nicht sehr aussagekräftig. Weitere aussagekräftige Ergebnisse erhalten Sie, wenn Sie Änderungen an einer Datenbank bereitstellen oder eine neue Datenbank bereitstellen.  
  
5.  Öffnen Sie MyTargetDatabase.details.xml, und untersuchen Sie den Inhalt. Ein kleiner Abschnitt der Detaildatei zeigt die Einträge und das Skript, die das Sales-Schema erstellen, eine Nachricht über das Erstellen einer Tabelle drucken und die Tabelle erstellen:  
  
    ```  
    <CreateElementStep Name="Sales" Category="Schema"><![CDATA[CREATE SCHEMA [Sales]  
        AUTHORIZATION [dbo];  
  
    ]]></CreateElementStep>  
        <SqlPrintStep><![CDATA[PRINT N'Creating [Sales].[Customer]...';  
  
    ]]></SqlPrintStep>  
        <CreateElementStep Name="Sales.Customer" Category="Table"><![CDATA[CREATE TABLE [Sales].[Customer] (  
        [CustomerID]   INT           IDENTITY (1, 1) NOT NULL,  
        [CustomerName] NVARCHAR (40) NOT NULL,  
        [YTDOrders]    INT           NOT NULL,  
        [YTDSales]     INT           NOT NULL  
    );  
  
    ]]></CreateElementStep>  
  
    ```  
  
    Durch Analysieren des Bereitstellungsplans während der Ausführung können Sie sämtliche Informationen melden, die in der Bereitstellung enthalten sind, und weitere Maßnahmen auf Grundlage der Schritte in diesem Plan ergreifen.  
  
## <a name="next-steps"></a>Next Steps  
Sie können weitere Tools erstellen, um die Verarbeitung der Ausgabe-XML-Dateien durchzuführen. Dies ist nur ein Beispiel für einen [DeploymentPlanExecutor](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplanexecutor.aspx). Sie können auch einen [DeploymentPlanModifier](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplanmodifier.aspx) erstellen, um einen Bereitstellungsplan zu ändern, bevor er ausgeführt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
[Exemplarische Vorgehensweise: Erweitern von Datenbankprojekten zum Generieren von Modellstatistiken](https://msdn.microsoft.com/library/ee461508(v=vs.100).aspx)  
[Exemplarische Vorgehensweise: Erweitern der Bereitstellung von Datenbankprojekten zum Ändern des Bereitstellungsplans](https://msdn.microsoft.com/library/ee461507(v=vs.100).aspx)  
[Anpassen der Datenbankerstellung und -bereitstellung durch Erstellungs- und Bereitstellungs-Contributors](https://msdn.microsoft.com/library/ee461505(v=vs.100).aspx)  
  
