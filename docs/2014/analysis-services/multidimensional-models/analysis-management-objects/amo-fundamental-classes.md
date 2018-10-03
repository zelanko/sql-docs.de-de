---
title: Grundlegende AMO-Klassen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- data sources [AMO]
- AMO, database objects
- AMO, server objects
- Analysis Management Objects, server objects
- database objects [AMO]
- Analysis Management Objects, database objects
- AMO, data sources
- Analysis Management Objects, data sources
ms.assetid: 440e9287-53a2-4db3-9481-1d2ceb6e5b5a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0235bfcba38e803933fdbf2eb67802df506c0130
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48067132"
---
# <a name="amo-fundamental-classes"></a>Grundlegende AMO-Klassen
  Grundlegende Klassen sind der Ausgangspunkt für die Verwendung von Analysis Management Objects (AMO). Mithilfe dieser Klassen erstellen Sie Ihre Umgebung für die übrigen Objekte, die in Ihrer Anwendung verwendet werden. Grundlegende Klassen beinhalten die folgenden Objekte: <xref:Microsoft.AnalysisServices.Server>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.DataSource> und <xref:Microsoft.AnalysisServices.DataSourceView>.  
  
 Die folgende Abbildung zeigt die Beziehung der in diesem Thema erläuterten Klassen.  
  
 ![Grundlegende AMO-Klassen](../../../analysis-services/dev-guide/media/amo-fundamentalclasses.gif "grundlegende AMO-Klassen")  
  
  
  
##  <a name="ServerObjects"></a> Server-Objekte  
 Darüber hinaus haben Sie Zugriff auf die folgenden Methoden:  
  
-   Verbindungsverwaltung: Connect, Disconnect, Reconnect und GetConnectionState.  
  
-   Transaktionsverwaltung: BeginTransaction, CommitTransaction und RollbackTransaction.  
  
-   Backup und Restore.  
  
-   DDL-Ausführung: Execute, CancelCommand, SendXmlaRequest, StartXmlaRequest.  
  
-   Metadaten-Verwaltung: UpdateObjects und Validate.  
  
 Um eine Verbindung mit einem Server herzustellen, benötigen Sie eine Standardverbindungszeichenfolge, wie sie in ADOMD.NET und OLEDB verwendet wird. Weitere Informationen finden Sie unter <xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A>. Der Name des Servers kann als Verbindungszeichenfolge angegeben werden, ohne dass ein Format für Verbindungszeichenfolgen verwendet werden muss.  
  
 Weitere Informationen zu den Methoden und Eigenschaften zur Verfügung stehen, finden Sie unter <xref:Microsoft.AnalysisServices.Server> in die <xref:Microsoft.AnalysisServices>.  
  
##  <a name="DatabaseObjects"></a> Datenbankobjekte  
 Wenn Sie in Ihrer Anwendung mit einem <xref:Microsoft.AnalysisServices.Database>-Objekt arbeiten möchten, müssen Sie eine Instanz der Datenbank von der übergeordneten Serverdatenbankauflistung abrufen. Zum Erstellen einer Datenbank fügen Sie einer Serverdatenbankauflistung ein <xref:Microsoft.AnalysisServices.Database>-Objekt hinzu und aktualisieren die neue Instanz auf dem Server. Zum Löschen einer Datenbank löschen Sie das <xref:Microsoft.AnalysisServices.Database>-Objekt mithilfe seiner eigenen Drop-Methode.  
  
 Datenbanken können mithilfe der BackUp-Methode (über das <xref:Microsoft.AnalysisServices.Database>- oder <xref:Microsoft.AnalysisServices.Server>-Objekt) gesichert werden. Sie können jedoch nur über das <xref:Microsoft.AnalysisServices.Server>-Objekt mithilfe der Restore-Methode wiederhergestellt werden.  
  
 Weitere Informationen zu den Methoden und Eigenschaften zur Verfügung stehen, finden Sie unter <xref:Microsoft.AnalysisServices.Database> in die <xref:Microsoft.AnalysisServices>.  
  
##  <a name="DSandDSV"></a> DataSource und DataSourceView-Objekte  
 Datenquellen werden mithilfe der <xref:Microsoft.AnalysisServices.DataSourceCollection> über die Datenbankklasse verwaltet. Eine Instanz von <xref:Microsoft.AnalysisServices.DataSource> kann mithilfe der Add-Methode über ein <xref:Microsoft.AnalysisServices.DataSourceCollection>-Objekt erstellt werden. Eine Instanz von <xref:Microsoft.AnalysisServices.DataSource> kann mithilfe der Remove-Methode über ein <xref:Microsoft.AnalysisServices.DataSourceCollection>-Objekt gelöscht werden.  
  
 <xref:Microsoft.AnalysisServices.DataSourceView>-Objekte werden über das <xref:Microsoft.AnalysisServices.DataSourceViewCollection>-Objekt in der Datenbankklasse verwaltet.  
  
 Weitere Informationen zu den verfügbaren Methoden und Eigenschaften finden Sie unter <xref:Microsoft.AnalysisServices.DataSource> und <xref:Microsoft.AnalysisServices.DataSourceView> in <xref:Microsoft.AnalysisServices>.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.AnalysisServices>   
 [Einführung in AMO-Klassen](amo-classes-introduction.md)   
 [Programmieren von grundlegenden AMO-Objekten](programming-amo-fundamental-objects.md)  
  
  
