---
title: Verbinden mit Quelldaten (Datamining-Client für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- connections
ms.assetid: 548672ce-e403-4aca-b67a-c2c797f053dd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 78c60832ea6111b0682e8a6d2b5ab3540a19cfb1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48159740"
---
# <a name="connect-to-source-data-data-mining-client-for-excel"></a>Herstellen von Verbindungen mit Quelldaten (Data Mining-Client für Excel)
  In diesem Thema wird beschrieben, wie Sie Verbindungen, die zum Speichern von Data Mining-Modellen und für den Zugriff auf die in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] gespeicherten externen Daten verwendet werden, erstellen und verwenden.  
  
 **Datamining-Verbindungen.** Die beim Starten des Add-Ins erstellte Verbindung wird für den Zugriff auf Algorithmen, das Analysieren von Daten und das Speichern von Miningstrukturen und -modellen verwendet.  
  
 Eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ist erforderlich, um die Modellierungs- und Visualisierungstools in den Add-Ins zu verwenden. Der Grund dafür ist, dass die Add-Ins von den Algorithmen und Datenstrukturen abhängen, die von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] bereitgestellt werden.  
  
 **Verbindungen mit externen Datenquellen.** Sie können Verbindungen mit externen Daten auch herstellen, während Sie Modelle erstellen oder Ergebnisse speichern. So können Sie beispielsweise ein Data Mining-Modell auf einem Server erstellen und anschließend mit diesem Data Mining-Modell eine Vorhersage auf der Grundlage von Daten ausführen, die in einer anderen Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], in einer Excel-Datentabelle oder einer externen Datenquelle wie [!INCLUDE[msCoName](../includes/msconame-md.md)] Access gespeichert sind. Bei jedem Zugriff auf eine neue Datenquelle werden Sie in einem Dialogfeld aufgefordert, eine Verbindung zu erstellen.  
  
##  <a name="bkmk_prereq2"></a> Erforderliche Komponenten  
 Bei dieser Version des Add-Ins muss die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Instanz die Version SQL Server 2012 aufweisen. Eine separate Version der Add-Ins ist verfügbar, wenn Sie eine Verbindung mit einer früheren Version von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] herstellen möchten. Es gibt Add-In-Versionen, die SQL Server 2005, SQL Server 2008 und SQL Server 2008 R2 unterstützen.  
  
 Um eine Verbindung mit einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenbank herzustellen, benötigen Sie Zugriffsrechte für den Datenbankserver. Außerdem müssen Data Mining-Sitzungen aktiviert sein, und Sie benötigen Lese- oder Lese-/Schreibberechtigungen für die Datenbankobjekte, die auf dem Server gespeichert sind.  
  
##  <a name="bkmk_connect"></a> Erstellen von Data Mining-Serververbindungen  
 Die **Verbindungen** "Gruppieren" im Data Mining-Client für Excel und die Tabellenanalysetools für Excel Tools zum Verwalten von Verbindungen mit einer Instanz von bieten [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
-   Sie können die Verbindung beim Installieren des Add-Ins erstellen oder später hinzufügen.  
  
-   Sie können mehrere Verbindungen erstellen und Verbindungen jederzeit ändern, es sei denn, Sie erstellen gerade ein Modell oder führen eine Abfrage für ein Modell aus.  
  
     Ändern oder schließen Sie keine Verbindung, wenn ein Data Mining-Modell gerade verarbeitet wird. Im Data Mining-Modell können Daten verloren gehen, oder das Modell wird möglicherweise unbrauchbar.  
  
-   Es kann jeweils nur eine Verbindung aktiv sein.  
  
### <a name="connections-in-the-excel-add-ins"></a>Verbindungen in den Excel-Add-Ins  
 Die **Verbindungen** "Gruppieren" im Data Mining-Client für Excel und die Tabellenanalysetools für Excel ist, in dem für das Verwalten von Verbindungen mit einer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
##### <a name="create-a-new-server-connection-in-the-excel-add-ins"></a>Erstellen einer neuen Serververbindung in den Excel-Add-Ins  
  
1.  Klicken Sie auf die **Verbindung** Schaltfläche der **analysieren** oder **Data Mining** Menüband.  
  
    > [!NOTE]  
    >  Der Text auf der Schaltfläche gibt an, ob eine Verbindung vorhanden ist. Wenn im Arbeitsblatt keine Verbindung hergestellt wurde, wird die Schaltfläche "enthält den Text"\<keine Verbindung >. " Wenn auf dem Arbeitsblatt zuvor eine Verbindung hergestellt wurde, wird der Name dieser Verbindung auf der Schaltfläche angezeigt.  
  
2.  In der **Analysis Services-Verbindungen** Dialogfeld klicken Sie auf **neu**.  
  
3.  In der **neue Analysis Services-Verbindung** Dialogfeld geben den Namen des Servers.  
  
4.  Geben Sie die Authentifizierungsmethode an.  
  
5.  Wählen Sie eine Datenbank aus der **Katalogname** Dropdown-Liste. Wenn keine Datenbank auf der Instanz vorhanden ist, wählen Sie **(Standard)**.  
  
6.  Geben Sie einen Anzeigenamen für die Verbindung ein.  
  
7.  Klicken Sie auf **Testverbindung** , stellen Sie sicher, dass der Server und Datenbank verfügbar sind.  
  
8.  Klicken Sie auf **OK**und dann auf **Schließen**.  
  
### <a name="connections-using-a-web-service"></a>Konfigurieren von Verbindungen mithilfe eines Webdiensts  
 Wenn Sie eine Thin-Client-Architektur verwenden, um das Durchsuchen von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Cubes und -Daten zu ermöglichen, können Sie eine [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Serververbindung auch über Webdienste konfigurieren. Informationen zum Definieren eines webbasierten Clients finden Sie in der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
 Wenn Sie über Zugriff auf einen Server verfügen, der für Webdienste konfiguriert wurde, können Sie beim Erstellen der Verbindung den Verbindungstyp angeben.  
  
##### <a name="create-an-http-connection-to-analysis-services"></a>Herstellen einer HTTP-Verbindung mit Analysis Services  
  
1.  Öffnen der **neue Analysis Services-Verbindung** Dialogfeld.  
  
2.  Geben Sie als Servernamen http:// und die URL für den entsprechenden [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server ein.  
  
3.  Geben Sie den Benutzernamen und das Kennwort für den Zugriff auf den Webdienst ein.  
  
### <a name="connections-in-the-visio-add-in"></a>Verbindungen im Visio-Add-In  
 Im Gegensatz zu Excel wird in Visio kein Menüband bereitgestellt, und es stehen keine speziellen Schaltflächen für die Erstellung und Überwachung von Verbindungen zur Verfügung. Stattdessen wird die Datenverbindung hergestellt, wenn Sie zum ersten Mal ein Data Mining-Shape auswählen und auf einer Visio-Seite ablegen. Ein Assistent fordert Sie auf, das Modell für das Shape auszuwählen und weitere Optionen festzulegen.  
  
 Wenn Sie eine Verbindung mit zuvor verwendet haben eine [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenquellen in Excel ist, werden diese Verbindungen als mögliche Datenquellen zur Auswahl aufgeführt.  
  
##### <a name="create-a-connection-for-a-visio-shape"></a>Herstellen einer Verbindung für ein Visio-Shape  
  
1.  Öffnen Sie die Data Mining-Vorlage, und wählen Sie eines der Data Mining-Shapes aus.  
  
2.  Ziehen Sie das Shape, und legen Sie es auf einer leeren Seite ab.  
  
3.  In der **Vybrat zdroj DAT** (Dialogfeld), wählen Sie eine Datenquelle aus der Liste aus, oder klicken Sie auf **neu**.  
  
4.  Bei Auswahl von **neu**, führen Sie die Schritte, die weiter oben beschrieben wird, geben Sie einen Server und der Name des Katalogs oder über einen Webdienst zu verbinden.  
  
##  <a name="bkmk_change"></a> Ändern von Verbindungen  
 Sie können mehrere Verbindungen in einem Arbeitsblatt erstellen, aber es kann jeweils nur eine Verbindung aktiv sein. Der Name der aktuellen Verbindung wird angezeigt, der **Verbindung** Schaltfläche.  
  
 In Data Mining-Client für Excel, können Sie auch die Verbindungszeichenfolge und den Status für die aktuelle Verbindung überprüfen, indem Sie auf **Ablaufverfolgung** , und klicken Sie dann auf **aktuelle Verbindung**.  
  
#### <a name="use-a-different-server-connection"></a>Verwenden einer anderen Serververbindung  
  
1.  Klicken Sie auf **Verbindung**.  
  
2.  In der **Analysis Services-Verbindungen** Bereich, wählen Sie eine Verbindung zwischen dem **andere Verbindungen** aus, und klicken Sie auf **als aktuell**.  
  
3.  Klicken Sie auf **Testverbindung** um sicherzustellen, dass die Verbindung verfügbar ist.  
  
 Nachdem ein Miningmodell fertig verarbeitet wurde, werden die Ergebnisse lokal gespeichert. Wenn Sie zu diesem Zeitpunkt die Verbindung mit einem Server schließen und eine Verbindung mit einem anderen Server herstellen, hat dies keine Auswirkungen auf die Daten. Sie sollten die Verbindung jedoch nicht während der Verarbeitung des Data Mining-Modells ändern oder trennen, da dadurch die Daten beschädigt werden können.  
  
#### <a name="modify-an-existing-server-connection"></a>Ändern einer vorhandenen Serververbindung  
  
1.  Bestehende Verbindungen können nicht geändert werden. Wenn Sie eine Verbindung mit einer anderen Datenbank oder einem anderen Server herstellen möchten, sollten Sie eine neue Verbindung erstellen.  
  
2.  Wenn Sie die Verbindungszeichenfolge ändern müssen, um das Abfragetimeout zu erhöhen oder der Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] weitere Parameter hinzuzufügen, besteht eine Möglichkeit darin, die DMC-Datei mit der gespeicherten Verbindungszeichenfolge zu bearbeiten.  
  
     \<Laufwerk: > \Users\\< Myusername\>\AppData\Local\Microsoft\Data Mining-Add-in  
  
##  <a name="bkmk_extconnections"></a> Herstellen einer Verbindung mit externen Datenquellen  
 Während die Tools in der **analysieren** arbeiten ausschließlich mit Daten in Excel, die Tools im Menüband der **Data Mining** Menüband können Sie die direkte Verbindung mit externen Datenquellen, die als Eingaben verwendet werden sollen, für das Modell oder für Erstellen von Stichproben.  
  
 Die Add-Ins enthalten folgende Tools, die die Verwendung externer Daten für das Data Mining unterstützen:  
  
-   [Beispieldaten &#40;SQL Server Data Mining-Add-ins&#41;](sample-data-sql-server-data-mining-add-ins.md)  
  
-   [Assistent zum Klassifizieren &#40;Data Mining-Add-ins für Excel&#41;](classify-wizard-data-mining-add-ins-for-excel.md)  
  
-   [Assistent zum Schätzen von &#40;Data Mining-Add-ins für Excel&#41;](estimate-wizard-data-mining-add-ins-for-excel.md)  
  
-   [Cluster-Assistent &#40;Data Mining-Add-ins für Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md)  
  
-   [Planungs-Assistent &#40;Data Mining-Add-ins für Excel&#41;](forecast-wizard-data-mining-add-ins-for-excel.md)  
  
-   [Erstellen der Miningstruktur &#40;SQL Server Data Mining-Add-ins&#41;](create-mining-structure-sql-server-data-mining-add-ins.md)  
  
-   [Genauigkeitsdiagramm &#40;SQL Server Data Mining-Add-ins&#41;](accuracy-chart-sql-server-data-mining-add-ins.md)  
  
-   [Gewinndiagramm &#40;SQL Server Data Mining-Add-ins&#41;](profit-chart-sql-server-data-mining-add-ins.md)  
  
-   [Klassifikationsmatrix &#40;SQL Server Data Mining-Add-ins&#41;](classification-matrix-sql-server-data-mining-add-ins.md)  
  
### <a name="using-analysis-services-as-a-data-source"></a>Verwenden von Analysis Services als Datenquelle  
 Sie haben keinen direkten Zugriff auf Daten, die in einem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Cube oder einem tabellarischen Modell gespeichert sind. Stellen Sie stattdessen in Excel eine Verbindung mit dem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server her, und erstellen Sie auf Grundlage der Daten ein Modell.  
  
### <a name="relational-data-sources"></a>Relationale Datenquellen  
 Wenn Sie Daten aus einer relationalen Quelle als Eingabedaten für Ihr Modell verwenden möchten, können Sie eine Verbindung mit den folgenden SQL Server-Versionen herstellen:  
  
-   SQL Server 2008  
  
-   SQL Server 2008 R2  
  
-   SQL Server 2012  
  
 Sie können Daten auch aus einer beliebigen relationalen Datenquelle abrufen, die von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] als Datenquelle unterstützt wird. Weitere Informationen zu unterstützten Datenquellen finden Sie unter [Datenquellen in mehrdimensionalen Modellen](multidimensional-models/data-sources-in-multidimensional-models.md)  
  
 Beachten Sie, dass die folgenden Datentypen nicht für das Data Mining verwendet werden können und einen Fehler verursachen, wenn sie beim Erstellen eines Modells eingefügt werden:  
  
-   ntext  
  
-   BINARY  
  
## <a name="see-also"></a>Siehe auch  
 [Ablaufverfolgung &#40;Datamining-Client für Excel&#41;](trace-data-mining-client-for-excel.md)  
  
  
