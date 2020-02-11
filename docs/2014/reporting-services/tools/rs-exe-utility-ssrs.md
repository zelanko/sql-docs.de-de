---
title: Hilfsprogramm „RS.exe“ (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- automatic report server tasks
- rs utility
- command prompt utilities [Reporting Services]
- report servers [Reporting Services], automating tasks
- command prompt utilities [SQL Server], rs
- scripts [Reporting Services], command prompt
- deploying reports [Reporting Services]
ms.assetid: bd6f958f-cce6-4e79-8a0f-9475da2919ce
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a6c4bf8f67f787214d38148db40ea8122a064a42
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66099827"
---
# <a name="rsexe-utility-ssrs"></a>Hilfsprogramm 'RS.exe' (SSRS)
  Das Dienstprogramm rs.exe verarbeitet Skripts, die von Ihnen in einer Eingabedatei bereitgestellt werden. Verwenden Sie dieses Hilfsprogramm, um die Berichtsserverbereitstellung und Verwaltungsaufgaben zu automatisieren.  
  
> [!NOTE]  
>  In [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]und höheren Versionen wird die Verwendung des **rs** -Hilfsprogramms für Berichtsserver unterstützt, die für den integrierten SharePoint-Modus konfiguriert wurden, sowie für Server, die im einheitlichen Modus konfiguriert wurden. In früheren Versionen wurden nur Konfigurationen im einheitlichen Modus unterstützt.  
  
 **In diesem Thema:**  
  
-   [Datei Speicherort](#bkmk_filelocation)  
  
-   [Argumente](#bkmk_arguments)  
  
-   [Berechtigungen](#bkmk_permissions)  
  
-   [Beispiele](#bkmk_examples)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      rs {-?}  
{-i input_file=}  
{-s serverURL}  
{-u username}  
{-p password}  
{-e endpoint}  
{-l time_out}  
{-b batchmode}  
{-v globalvars=}  
{-t trace}  
```  
  
##  <a name="bkmk_filelocation"></a>Datei Speicherort  
 " **Rs. exe** " befindet sich unter " **\Programme\Microsoft SQL server\110\tools\binn**". Sie können das Hilfsprogramm von einem beliebigen Ordner im Dateisystem ausführen.  
  
##  <a name="bkmk_arguments"></a>Argumente  
 **-?**  
 (Optional) Zeigt die Syntax der **rs** -Argumente an.  
  
 `-i`*input_file*  
 (Erforderlich) Gibt die auszuführende RSS-Datei an. Dieser Wert kann einen relativen oder einen vollqualifizierten Pfad zur RSS-Datei enthalten.  
  
 `-s`*ServerURL*  
 (Erforderlich) Gibt den Namen des Webservers und den Namen des virtuellen Verzeichnisses auf dem Berichtsserver an, in dem die Datei ausgeführt werden soll. Ein Beispiel für eine Berichtsserver-URL ist `http://examplewebserver/reportserver`. Das Präfix http:// oder https:// zu Beginn des Servernamens ist optional. Wenn Sie kein Präfix angeben, verwendet der Berichtsserver-Skripthost zunächst https:// und dann http://, falls https:// nicht verfügbar ist.  
  
 `-u`[*Domäne*\\] *Benutzername*  
 (Optional) Gibt ein Benutzerkonto an, das für die Herstellung einer Verbindung mit dem Berichtsserver verwendet wird. Wenn `-u` und `-p` nicht angegeben werden, wird das aktuelle Windows-Benutzerkonto verwendet.  
  
 `-p`*Kennwort*  
 (Erforderlich, wenn `-u` angegeben ist.) Gibt das Kennwort an, das mit dem `-u`-Argument verwendet wird. Bei diesem Wert wird die Groß-/Kleinschreibung beachtet.  
  
 `-e`  
 (Optional) Gibt den SOAP-Endpunkt für die Ausführung des Skripts an. Folgende Werte sind gültig:  
  
-   Mgmt2010  
  
-   Mgmt2006  
  
-   Mgmt2005  
  
-   Exec2005  
  
 Wird kein Wert angegeben, wird der Endpunkt Mgmt2005 verwendet. Weitere Informationen zu den SOAP-Endpunkten finden Sie unter [Report Server Web Service Endpoints](../report-server-web-service/methods/report-server-web-service-endpoints.md).  
  
 `-l`*time_out*  
 Optionale Gibt die Anzahl der Sekunden an, die Verläufen, bevor die Verbindung mit dem Server über einen Timeout eintritt. Der Standardwert ist 60 Sekunden. Wenn Sie keinen Timeoutwert angeben, wird der Standardwert verwendet. Ein Wert von `0` gibt an, dass sich für die Verbindung kein Timeout ergibt.  
  
 **-b**  
 (Optional) Gibt an, dass die Befehle in der Skriptdatei als Batch ausgeführt werden. Falls ein Befehl fehlschlägt, wird ein Rollback für den Batch ausgeführt. Einige Befehle können nicht als Batch ausgeführt werden. Diese Befehle werden wie gewohnt ausgeführt. Nur Ausnahmen, die ausgegeben werden und nicht innerhalb des Skripts behandelt werden, führen zu einem Rollback. Wenn das Skript eine Ausnahme behandelt und normalerweise von `Main` zurückgegeben wird, wird ein Commit für den Batch ausgeführt. Wenn Sie diesen Parameter nicht angeben, werden die Befehle ausgeführt, ohne dass ein Batch erstellt wird. Weitere Informationen finden Sie unter [Batching Methods](../report-server-web-service-net-framework-soap-headers/batching-methods.md).  
  
 `-v`*globalvar*  
 (Optional) Gibt globale Variablen an, die in dem Skript verwendet werden. Wenn das Skript globale Variablen verwendet, müssen Sie dieses Argument angeben. Der angegebene Wert muss für die in der RSS-Datei definierten globalen Variablen gültig sein. Sie müssen eine globale Variable für jedes **-v**-Argument angeben.  
  
 Das Argument `-v` wird in der Befehlszeile angegeben und verwendet, um zur Laufzeit einen Wert für eine globale Variable festzulegen, die in Ihrem Skript definiert ist. Wenn Ihr Skript beispielsweise eine Variable namens *parentFolder*, enthält, können Sie in der Befehlszeile einen Namen für diesen Ordner angeben:  
  
 `rs.exe -i myScriptFile.rss -s http://myServer/reportserver -v parentFolder="Financial Reports"`  
  
 Globale Variablen werden mit den vorliegenden Namen erstellt und auf die bereitgestellten Werte festgelegt. Beispielsweise führt **-v a =**"`1`" **-v b =**"`2`" zu einer Variablen mit dem `a` Namen mit dem Wert "`1`" und einer Variablen **b** mit dem Wert "`2`".  
  
 Globale Variablen stehen für alle Funktionen im Skript zur Verfügung. Ein umgekehrter Schrägstrich und ein Anführungszeichen (**\\"**) werden als doppeltes Anführungszeichen interpretiert. Anführungszeichen sind nur erforderlich, wenn die Zeichenfolge ein Leerzeichen enthält. Variablennamen müssen für [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]gültig sein. Sie müssen mit einem Buchstaben oder Unterstrich beginnen und Buchstaben, Ziffern oder Unterstriche enthalten. Reservierte Wörter können nicht als Variablennamen verwendet werden. Weitere Informationen zur Verwendung globaler Variablen finden Sie unter [Integrierte Sammlungen in Ausdrücken &#40;Berichts-Generator und SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).  
  
 **-t**  
 (Optional) Schreibt Fehlermeldungen in das Ablaufverfolgungsprotokoll. Dieses Argument enthält keinen Wert. Weitere Informationen finden Sie unter [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md).  
  
##  <a name="bkmk_permissions"></a> Berechtigungen  
 Um das Tool ausführen zu können, müssen Sie die Berechtigung besitzen, eine Verbindung mit der Berichtsserverinstanz herzustellen, für die das Skript ausgeführt wird. Durch das Ausführen von Skripts können Sie Änderungen am lokalen Computer oder an einem Remotecomputer durchführen. Sollen Änderungen an einem Berichtsserver durchgeführt werden, der auf einem Remotecomputer installiert ist, geben Sie den Remotecomputer im `-s`-Argument an.  
  
##  <a name="bkmk_examples"></a>Beispiele  
 Das folgende Beispiel zeigt, wie die Skriptdatei angegeben wird, die das [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET-Skript und die auszuführenden Webdienstmethoden enthält.  
  
```  
rs -i c:\scriptfiles\script_copycontent.rss -s http://localhost/reportserver  
```  
  
 Ein ausführliches Beispiel finden Sie unter [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).  
  
 Weitere Beispiele finden Sie unter [Ausführen einer Reporting Services-Skriptdatei](run-a-reporting-services-script-file.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Sie können Skripts so definieren, dass sie Systemeigenschaften festlegen, Berichte veröffentlichen usw. Die Skripts, die Sie erstellen, können jede Methode der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -API einschließen. Weitere Informationen zu den verfügbaren Methoden und Eigenschaften finden Sie unter [Report Server Web Service](../report-server-web-service/report-server-web-service.md).  
  
 Das Skript muss in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET-Code geschrieben und in einer Unicode- oder UTF-8-Textdatei mit der Dateinamenerweiterung „.rss“ gespeichert sein. Das Hilfsprogramm **rs** kann nicht zum Debuggen von Skripts verwendet werden. Führen Sie den Code in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]aus, um ein Skript zu debuggen.  
  
> [!TIP]  
>  Ein ausführliches Beispiel finden Sie unter [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen einer Reporting Services Skriptdatei](run-a-reporting-services-script-file.md)   
 [Skript Bereitstellungs-und Verwaltungsaufgaben](script-deployment-and-administrative-tasks.md)   
 [Skripterstellung mit dem Hilfsprogramm Rs. exe und dem Webdienst](script-with-the-rs-exe-utility-and-the-web-service.md)   
 [Eingabeaufforderungs-Hilfsprogramme für Berichts Server &#40;SSRS&#41;](report-server-command-prompt-utilities-ssrs.md)  
  
  
