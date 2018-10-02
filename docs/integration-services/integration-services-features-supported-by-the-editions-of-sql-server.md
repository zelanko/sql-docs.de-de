---
title: Von den SQL Server-Editionen unterstützte Integration Services-Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e5018225-68bb-4f34-ae4a-ead79d8ad13a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 35c0b050c760540988ff366f91a7884b7b5fd56b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47819778"
---
# <a name="integration-services-features-supported-by-the-editions-of-sql-server"></a>Von den SQL Server-Editionen unterstützte Integration Services-Funktionen
 Dieses Thema bietet detaillierte Informationen zu den von den verschiedenen [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)]-Editionen unterstützten SQL Server Integration Services-Funktionen (SSIS).  

Von Evaluation und Developer Edition unterstützte Funktionen finden Sie in den Funktionen der Enterprise Edition in den folgenden Tabellen.
  
Die neuesten Anmerkungen zu dieser Version und Informationen zu Neuigkeiten finden Sie in folgenden Artikeln:
-   [Versionsanmerkungen zu SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
-   [Neuigkeiten in Integration Services in SQL Server 2016](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md)
-   [Neues in Integration Services in SQL Server 2017](../integration-services/what-s-new-in-integration-services-in-sql-server-2017.md)
    
**SQL Server 2016 R2 ausprobieren!**    

Die SQL Server Evaluation Edition steht für einen Testzeitraum von 180 Tagen zur Verfügung.  
    
> [![Download aus dem Evaluation Center](../analysis-services/media/download.png)](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) **[Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016)**    
    
## <a name="ISNew"></a> Neue Integration Services-Funktionen in SQL Server 2017
  
|Funktion|Enterprise|Standard|Web|Express mit Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Scale Out-Master|Benutzerkontensteuerung|||||
|Scale Out-Worker|Benutzerkontensteuerung|Ja <sup>1</sup>|TBD|TBD|TBD|
|Unterstützung für Microsoft Dynamics AX und Microsoft Dynamics CRM in OData-Komponenten <sup>2</sup>|Benutzerkontensteuerung|Benutzerkontensteuerung||||

<sup>1</sup> Wenn Sie Pakete ausführen, für die nur Enterprise-Funktionen in Scale Out erforderlich ist, müssen die Scale Out-Worker ebenfalls auf Instanzen von SQL Server Enterprise ausgeführt werden.

<sup>2</sup> Diese Funktion wird auch in SQL Server 2016 mit Service Pack 1 unterstützt.

## <a name="IEWiz"></a> SQL Server-Import/Export-Assistent

|Funktion|Enterprise|Standard|Web|Express mit Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|SQL Server-Import/Export-Assistent|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  

## <a name="IS"></a> Integration Services  
  
|Funktion|Enterprise|Standard|Web|Express mit Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Integrierte Datenquellenkonnektoren|Benutzerkontensteuerung|Benutzerkontensteuerung|||| 
|Integrierte Tasks und Transformationen|Benutzerkontensteuerung|Benutzerkontensteuerung||||  
|ODBC-Quelle und -Ziel |Benutzerkontensteuerung|Benutzerkontensteuerung|||| 
|Azure-Datenquellenkonnektoren und Tasks|Benutzerkontensteuerung|Benutzerkontensteuerung||||  
|Hadoop-/HDFS-Connectors und -Tasks|Benutzerkontensteuerung|Benutzerkontensteuerung||||  
|Grundlegende Datenprofilerstellungs-Tools|Benutzerkontensteuerung|Benutzerkontensteuerung|||| 

## <a name="ISAA"></a>Integration Services – Erweiterte Quellen und Ziele  
  
|Funktion|Enterprise|Standard|Web|Express mit Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Oracle-Quelle und -Ziel für eine leistungsstarke Ausführung von Attunity|Benutzerkontensteuerung|||||  
|Teradata-Quelle und -Ziel für eine leistungsstarke Ausführung von Attunity|Benutzerkontensteuerung|||||  
|SAP BW-Quelle und -Ziel|Benutzerkontensteuerung|||||  
|Ziel für Data Mining-Modelltraining|Benutzerkontensteuerung|||||  
|Ziel für Dimensionsverarbeitung|Benutzerkontensteuerung|||||  
|Ziel für Partitionsverarbeitung|Benutzerkontensteuerung|||||  
  
## <a name="ISAT"></a> Integration Services – Erweiterte Tasks und Transformationen  
  
|Funktion|Enterprise|Standard|Web|Express mit Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Change Data Capture-Komponenten von Attunity <sup>1</sup>|Benutzerkontensteuerung|||||  
|Transformation für Data Mining-Abfragen|Benutzerkontensteuerung|||||  
|Transformationen für Fuzzygruppierung und Fuzzysuche|Benutzerkontensteuerung|||||  
|Transformationen für Ausdrucksextrahierung und Ausdruckssuche|Benutzerkontensteuerung|||||  

<sup>1</sup> Für die Change Data Capture-Komponenten von Attunity ist Enterprise Edition erforderlich. Die Enterprise Edition ist jedoch nicht für den Change Data Capture Service und Change Data Capture-Designer notwendig. Sie können den Designer und den Dienst auf einem Computer verwenden, auf dem SSIS nicht installiert ist.
