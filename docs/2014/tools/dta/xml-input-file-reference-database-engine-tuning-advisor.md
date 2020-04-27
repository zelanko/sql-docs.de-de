---
title: XML-Eingabedateireferenz (Datenbankoptimierungsratgeber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database Engine Tuning Advisor [SQL Server], XML input files
- input file reference [Database Engine Tuning Advisor]
- XML input files [Database Engine Tuning Advisor]
ms.assetid: 05e5e5f0-d6df-4336-b18e-e9bc2835a766
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b560b36eb98ec73723a4ce25cb3c647f4962b634
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62509982"
---
# <a name="xml-input-file-reference-database-engine-tuning-advisor"></a>XML-Eingabedateireferenz (Datenbankoptimierungsratgeber)
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Optimierungsratgeber kann mithilfe einer XML-Eingabedatei eine Datenbank optimieren. Anhand dieser XML-Datei wird festgelegt, welche Datenbanken, Tabellen, Arbeitsauslastungsdateien oder -tabellen und Optimierungsoptionen für die Optimierungssitzung verwendet werden sollen. Außerdem können Sie mit dieser Datei eine vom Benutzer angegebene Konfiguration zum Ausführen von Was-wäre-wenn-Analysen festlegen.  
  
 In XML-Eingabedateien des [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Optimierungsratgebers befinden sich hierarchisch angeordnete XML-Elemente mit Text oder anderen Elementen, die die Einstellungen der Optimierungssitzung angeben. Die XML-Eingabedatei des [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Optimierungsratgebers muss den Standards für wohlgeformte XML-Dokumente entsprechen, d. h., dass bei allen Elementnamen die Groß-/Kleinschreibung beachtet wird. Die Groß-/Kleinschreibung der Elemente ist wie in Pascal. Das bedeutet, dass das erste Zeichen ein Großbuchstabe und der erste Buchstabe eines nachfolgenden verketteten Worts ein Großbuchstabe ist.  
  
 Alle Elementwerte müssen den XML-Benennungskonventionen entsprechen. Weitere Informationen zu diesen Konventionen finden Sie unter [XML-Textinhalt](https://go.microsoft.com/fwlink/?LinkId=7614) in der MSDN Library.  
  
 Beachten Sie, dass dies keine vollständige Referenz ist. Informationen zu allen Elementen, die Sie zum Definieren von XML-Eingabedateien verwenden können, finden Sie im XML-Schema DTASchema.xsd des [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Optimierungsratgebers.  
  
## <a name="xml-declaration"></a>XML-Deklaration  
  
-   [XML-Daten &#40;SQL Server&#41;](../../relational-databases/xml/xml-data-sql-server.md)  
  
## <a name="dtaxml-root-element"></a>DTAXML-Stammelement  
  
-   [DTAXML-Element &#40;DTA&#41;](dtaxml-element-dta.md)  
  
## <a name="dtainput-elements"></a>DTAInput-Elemente  
  
-   [DTAInput-Element &#40;DTA&#41;](dtainput-element-dta.md)  
  
-   [Server-Element &#40;DTA&#41;](server-element-dta.md)  
  
-   [Workload-Element &#40;DTA&#41;](workload-element-dta.md)  
  
-   [TuningOptions-Element &#40;DTA&#41;](tuningoptions-element-dta.md)  
  
-   [Configuration-Element &#40;DTA&#41;](configuration-element-dta.md)  
  
## <a name="server-elements"></a>Serverelemente  
  
-   [Name-Element für Server &#40;DTA&#41;](name-element-for-server-dta.md)  
  
-   [Database-Element für Server &#40;DTA&#41;](database-element-for-server-dta.md)  
  
## <a name="workload-elements"></a>Arbeitsauslastungselemente  
  
-   [File-Element &#40;DTA&#41;](file-element-dta.md)  
  
-   [Database-Element zur Arbeitsauslastung &#40;DTA&#41;](database-element-for-workload-dta.md)  
  
-   [EventString-Element &#40;DTA&#41;](eventstring-element-dta.md)  
  
## <a name="tuning-options-elements"></a>Optimierungsoptionselemente  
  
-   [TuningTimeInMin-Element &#40;DTA&#41;](tuningtimeinmin-element-dta.md)  
  
-   [StorageBoundInMB-Element &#40;DTA&#41;](storageboundinmb-element-dta.md)  
  
-   [TestServer-Element &#40;DTA&#41;](testserver-element-dta.md)  
  
-   [FeatureSet-Element &#40;DTA&#41;](featureset-element-dta.md)  
  
-   [Partitioning-Element &#40;DTA&#41;](partitioning-element-dta.md)  
  
-   [DropOnlyMode-Element &#40;DTA&#41;](droponlymode-element-dta.md)  
  
-   [KeepExisting-Element &#40;DTA&#41;](keepexisting-element-dta.md)  
  
-   [OnlineIndexOperation-Element &#40;DTA&#41;](onlineindexoperation-element-dta.md)  
  
-   [DatabaseToConnect-Element &#40;DTA&#41;](databasetoconnect-element-dta.md)  
  
## <a name="configuration-elements"></a>Konfigurationselemente  
  
-   [Server-Element für Konfiguration &#40;DTA&#41;](server-element-for-configuration-dta.md)  
  
-   [Database-Element für Konfiguration &#40;DTA&#41;](database-element-for-configuration-dta.md)  
  
-   [Recommendation-Element &#40;DTA&#41;](recommendation-element-dta.md)  
  
-   [Create Element &#40;DTA&#41;](create-element-dta.md)  
  
-   [Index-Element &#40;DTA&#41;](index-element-dta.md)  
  
-   [Name-Element für Index &#40;DTA&#41;](name-element-for-index-dta.md)  
  
-   [Column-Element für Index &#40;DTA&#41;](column-element-for-index-dta.md)  
  
-   [Name-Element für Spalte &#40;DTA&#41;](name-element-for-column-dta.md)  
  
-   [Filegroup-Element für Index &#40;DTA&#41;](filegroup-element-for-index-dta.md)  
  
## <a name="database-elements"></a>Datenbankelemente  
  
-   [Name-Element für Datenbank &#40;DTA&#41;](name-element-for-database-dta.md)  
  
-   [Schema-Element für Datenbank &#40;DTA&#41;](schema-element-for-database-dta.md)  
  
-   [Name-Element für Schema &#40;DTA&#41;](name-element-for-schema-dta.md)  
  
-   [Table-Element für Schema &#40;DTA&#41;](table-element-for-schema-dta.md)  
  
-   [Name-Element für Tabelle &#40;DTA&#41;](name-element-for-table-dta.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbankoptimierungsratgeber](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
