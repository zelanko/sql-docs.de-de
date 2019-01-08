---
title: Integration Services-Parameter (SSIS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9ed9ca8e-8b1e-48d9-907d-285516d6562b
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9358d3d7d014f7dc69dad00605ebdaaa2ef70707
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53352247"
---
# <a name="integration-services-ssis-parameters"></a>Integration Services (SSIS)-Parameter
  Mit[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -(SSIS-)Parametern können Sie Eigenschaften in Paketen zur Zeit der Paketausführung Werte zuweisen. Sie können *Projektparameter* auf Projektebene und *Paketparameter* auf Paketebene erstellen. Projektparameter werden verwendet, um jegliche externen Eingaben bereitzustellen, die das Projekt für ein oder mehrere Pakete im Projekt empfängt. Mit Paketparametern können Sie die Paketausführung ändern, ohne das Paket bearbeiten und erneut bereitstellen zu müssen.  
  
 In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] können Sie im Fenster **Project.params** Projektparameter erstellen, ändern oder löschen. Sie erstellen, ändern und löschen Paketparameter mit der Registerkarte **Parameter** im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer. Im Dialogfeld **Parametrisieren** können Sie einen neuen oder vorhandenen Parameter einer Taskeigenschaft zuordnen. Weitere Informationen zum Verwenden des Fensters **Project.params** und der Registerkarte **Parameter** finden Sie unter [Create Parameters](create-parameters.md). Weitere Informationen zum Dialogfeld **Parametrisieren** finden Sie unter [Parameterize Dialog Box](parameterize-dialog-box.md).  
  
## <a name="parameters-and-package-deployment-model"></a>Parameter und Paketbereitstellungsmodell  
 Im Allgemeinen sollten Sie beim Bereitstellen eines Pakets mit dem Paketbereitstellungsmodell Konfigurationen anstelle von Parametern verwenden.  
  
 Wenn Sie mithilfe des Paketbereitstellungsmodells ein Paket bereitstellen, das Parameter enthält, und dann das Paket ausführen, werden die Parameter während der Ausführung nicht aufgerufen. Wenn das Paket Paketparameter und Ausdrücke innerhalb des Pakets enthält, verwenden Sie die Parameter, die resultierenden Werte werden zur Laufzeit übernommen. Wenn das Paket Projektparameter enthält, tritt bei der Paketausführung möglicherweise ein Fehler auf.  
  
## <a name="parameters-and-project-deployment-model"></a>Parameter und Projektbereitstellungsmodell  
 Wenn Sie ein Projekt auf dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Server bereitstellen, verwenden Sie Sichten, gespeicherte Prozeduren und die [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] -Benutzeroberfläche zum Verwalten von Projekt- und Paketparametern. Weitere Informationen finden Sie in den nachfolgenden Themen.  
  
-   [Sichten &#40;Integration Services-Katalog&#41;](/sql/integration-services/system-views/views-integration-services-catalog)  
  
-   [Gespeicherte Prozeduren &#40;Integration Services-Katalog&#41;](/sql/integration-services/system-stored-procedures/stored-procedures-integration-services-catalog)  
  
-   [Konfigurieren (Dialogfeld)](catalog/configure-dialog-box.md)  
  
-   [Paket ausführen (Dialogfeld)](../../2014/integration-services/execute-package-dialog-box.md)  
  
### <a name="parameter-values"></a>Parameterwerte  
 Sie können einem Parameter bis zu drei verschiedene Werttypen zuweisen. Wenn eine Paketausführung gestartet wird, wird ein einzelner Wert für den Parameter verwendet, und der Parameter wird in seinen abschließenden Literalwert aufgelöst.  
  
 In der folgenden Tabelle sind die Werttypen aufgeführt.  
  
|Wertname|Description|Werttyp|  
|----------------|-----------------|-------------------|  
|Ausführungswert|Der Wert, der einer bestimmten Instanz der Paketausführung zugewiesen wird. Diese Zuweisung überschreibt alle anderen Werte, gilt aber nur für eine einzelne Instanz der Paketausführung.|Literal|  
|Serverwert|Der Wert, der dem Parameter innerhalb des Projektbereichs zugewiesen wird, nachdem das Projekt auf dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Server bereitgestellt wurde. Dieser Wert überschreibt den Entwurfsstandard.|Literaler oder Umgebungsvariablenverweis|  
|Entwurfswert|Der Wert, der dem Parameter zugewiesen wird, wenn das Projekt in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]erstellt oder bearbeitet wird. Dieser Wert bleibt im Projekt erhalten.|Literal|  
  
 Sie können mehreren Paketeigenschaften mithilfe eines einzelnen Parameters einen Wert zuweisen. Einer einzelnen Paketeigenschaft kann nur ein Wert aus einem einzelnen Parameter zugewiesen werden.  
  
###  <a name="executions"></a> Ausführungen und Parameterwerte  
 Die *Ausführung* ist ein Objekt, das eine einzelne Instanz der Paketausführung darstellt. Wenn Sie eine Ausführung erstellen, geben Sie alle Details an, die zum Ausführen eines Pakets erforderlich sind, z. B. Ausführungsparameterwerte. Sie können die Parameterwerte vorhandener Ausführungen auch ändern.  
  
 Wenn Sie einen Ausführungsparameterwert explizit festlegen, ist dieser Wert nur auf diese spezielle Instanz der Ausführung anwendbar. Der Ausführungswert wird anstelle eines Serverwerts oder eines Entwurfswerts verwendet. Wenn Sie keinen Ausführungswert explizit festlegen und ein Serverwert angegeben wurde, wird der Serverwert verwendet.  
  
 Wenn ein Parameter entsprechend markiert ist, muss für diesen Parameter ein Serverwert oder ein Ausführungswert angegeben werden. Andernfalls wird das entsprechende Paket nicht ausgeführt. Obwohl der Parameter zur Entwurfszeit über einen Standardwert verfügt, wird er nie verwendet, nachdem das Projekt bereitgestellt wurde.  
  
#### <a name="environment-variables"></a>Umgebungsvariablen  
 Wenn ein Parameter auf eine Umgebungsvariable verweist, wird der Literalwert dieser Variable durch den angegebenen Umgebungsverweis aufgelöst und auf den Parameter angewendet. Der finale Literalparameterwert, der für die Paketausführung verwendet wird, wird als Ausführungsparameterwert bezeichnet. Sie geben den Umgebungsverweis für eine Ausführung im Dialogfeld **Ausführen** an.  
  
 Wenn ein Projektparameter auf eine Umgebungsvariable verweist und der Literalwert in der Variablen bei der Ausführung nicht aufgelöst werden kann, wird der Entwurfswert verwendet. Der Serverwert wird nicht verwendet.  
  
 Um die Umgebungsvariablen anzuzeigen, die Parameterwerten zugewiesen werden, fragen Sie die catalog.object_parameters-Sicht ab. Weitere Informationen finden Sie unter [catalog.object_parameters &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database).  
  
#### <a name="determining-execution-parameter-values"></a>Bestimmen von Ausführungsparameterwerten  
 Die folgenden Transact-SQL-Sichten und die gespeicherte Prozedur können verwendet werden, um Parameterwerte anzuzeigen und festzulegen.  
  
 [catalog.execution_parameter_values &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-execution-parameter-values-ssisdb-database) (Sicht)  
 Zeigt die tatsächlichen Parameterwerte an, die von einer bestimmten Ausführung verwendet werden.  
  
 [catalog.get_parameter_values &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-get-parameter-values-ssisdb-database) (gespeicherte Prozedur)  
 Löst die tatsächlichen Werte für das angegebene Paket und den Umgebungsverweis auf und zeigt diese an.  
  
 [catalog.object_parameters &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database) (Sicht)  
 Zeigt die Parameter und Eigenschaften für alle Pakete und Projekte im [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Katalog an, einschließlich der Entwurfsstandard- und Serverstandardwerte.  
  
 [catalog.set_execution_parameter_value &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database)  
 Legt den Wert eines Parameters für eine Instanz der Ausführung im [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Katalog fest.  
  
 Sie können den Parameterwert auch im Dialogfeld **Paket ausführen** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ändern. Weitere Informationen finden Sie unter [Execute Package Dialog Box](../../2014/integration-services/execute-package-dialog-box.md).  
  
 Sie können einen Parameterwert auch mit der dtexec-Option `/Parameter` ändern. Weitere Informationen finden Sie unter [dtexec Utility](packages/dtexec-utility.md).  
  
### <a name="parameter-validation"></a>Parameterüberprüfung  
 Wenn Parameterwerte nicht aufgelöst werden können, schlägt die entsprechende Paketausführung fehl. Zur Fehlervermeidung können Sie Projekte und Pakete im Dialogfeld **Überprüfen** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]überprüfen. Mit der Überprüfung stellen Sie sicher, dass alle Parameter über die notwendigen Werte verfügen oder die notwendigen Werte mit bestimmten Umgebungsverweisen auflösen können. Mit der Überprüfung können auch andere häufig auftretende Paketprobleme überprüft werden.  
  
 Weitere Informationen finden Sie unter [Validate Dialog Box](catalog/validate-dialog-box.md).  
  
### <a name="parameter-example"></a>Parameterbeispiel  
 In diesem Beispiel wird ein Parameter mit dem Namen **pkgOptions** beschrieben, der für die Angabe von Optionen für das Paket verwendet wird, in dem er sich befindet.  
  
 Während der Entwurfszeit, als der Parameter in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]erstellt wurde, wurde dem Parameter der Standardwert 1 zugewiesen. Dieser Standardwert wird als Entwurfsstandard bezeichnet. Wenn das Projekt im SSISDB-Katalog bereitgestellt wurde und diesem Parameter keine anderen Werte zugewiesen wurden, würde der Paketeigenschaft, die dem **pkgOptions** -Parameter entspricht, während der Paketausführung der Wert 1 zugewiesen werden. Der Entwurfsstandard bleibt während des gesamten Lebenszyklus des Projekts erhalten.  
  
 Während der Vorbereitung einer bestimmten Instanz der Paketausführung wird dem **pkgOptions** -Parameter der Wert 5 zugewiesen. Dieser Wert wird als Ausführungswert bezeichnet, da es für den Parameter nur für diese spezifische Instanz der Ausführung gilt. Wenn die Ausführung startet, wird der dem **pkgOptions** -Parameter entsprechenden Paketeigenschaft der Wert 5 zugewiesen.  
  
## <a name="related-tasks"></a>Related Tasks  
 [Erstellen von Parametern](create-parameters.md)  
  
 [Festlegen von Parameterwerten nach der Bereitstellung des Projekts](../../2014/integration-services/set-parameter-values-after-the-project-is-deployed.md)  
  
## <a name="related-content"></a>Verwandte Inhalte  
 Blogeintrag, [SSIS-Quicktipp: Erforderliche Parameter](https://go.microsoft.com/fwlink/?LinkId=239781), auf mattmasson.com.  
  
  
