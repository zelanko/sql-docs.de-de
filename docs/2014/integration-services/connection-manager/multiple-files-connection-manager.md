---
title: Verbindungs-Manager für mehrere Dateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- folders [Integration Services], connections
- files [Integration Services], connections
- Multiple Files connection manager
- connection managers [Integration Services], Multiple Files
- connections [Integration Services], files
- multiple file connections
ms.assetid: 10bdc56e-c5cd-4ddb-b2f7-375fe57fe8b2
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 20be558522d0f5df2aa4f5bcd0557626cff0e64c
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84920611"
---
# <a name="multiple-files-connection-manager"></a>Verbindungs-Manager für mehrere Dateien
  Mit einem Verbindungs-Manager für mehrere Dateien kann ein Paket auf vorhandene Dateien und Ordner verweisen oder Dateien und Ordner zur Laufzeit erstellen.  
  
> [!NOTE]  
>  Die integrierten Tasks und Datenflusskomponenten in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] verwenden keinen Verbindungs-Manager für mehrere Dateien. Sie können den Verbindungs-Manager jedoch im Skripttask oder in der Skriptkomponente verwenden. Informationen zum Verwenden von Verbindungs-Managern in der Skripttask finden Sie unter [Herstellen einer Verbindung zu Datenquellen im Skripttask ](../extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md). Weitere Informationen zur Verwendung von Verbindungs-Managern in der Skript Komponente finden Sie unter [Herstellen einer Verbindung mit Datenquellen in der Skript Komponente] (.). /extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md.  
  
## <a name="usage-types-of-the-multiple-files-connection-manager"></a>Verwendungstypen des Verbindungs-Managers für mehrere Dateien  
 Mit der `FileUsageType`-Eigenschaft des Verbindungs-Managers für mehrere Dateien wird angegeben, wie die Verbindung verwendet wird. Der Verbindungs-Manager für mehrere Dateien kann Dateien bzw. Ordner erstellen und vorhandene Dateien bzw. Ordner verwenden.  
  
 In der folgenden Tabelle sind die Werte von `FileUsageType` aufgeführt.  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**0**|Der Verbindungs-Manager für mehrere Dateien verwendet eine vorhandene Datei.|  
|**1**|Der Verbindungs-Manager für mehrere Dateien erstellt eine Datei.|  
|**2**|Der Verbindungs-Manager für mehrere Dateien verwendet einen vorhandenen Ordner.|  
|**3**|Der Verbindungs-Manager für mehrere Dateien erstellt einen Ordner.|  
  
## <a name="configuration-of-the-multiple-files-connection-manager"></a>Konfiguration des Verbindungs-Managers für mehrere Dateien  
 Wenn Sie einem Paket einen Verbindungs-Manager für mehrere Dateien hinzufügen, erstellt [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] einen Verbindungs-Manager, der zur Laufzeit in eine Verbindung für mehrere Dateien aufgelöst wird, die Eigenschaften der Verbindung für mehrere Dateien festlegt und der `Connections`-Auflistung des Pakets die Verbindung für mehrere Dateien hinzufügt.  
  
 Die `ConnectionManagerType`-Eigenschaft des Verbindungs-Managers ist auf `MULTIFILE` festgelegt.  
  
 Es gibt folgende Möglichkeiten, um einen Verbindungs-Manager für mehrere Dateien zu konfigurieren:  
  
-   Geben Sie den Verwendungstyp von Dateien und Ordnern an.  
  
-   Geben Sie Dateien und Ordner an.  
  
-   Falls Sie mehrere Dateien oder Ordner verwenden, geben Sie die Reihenfolge an, in der auf die Dateien und Ordner zugegriffen wird.  
  
 Wenn der Verbindungs-Manager für mehrere Dateien auf mehrere Dateien und Ordner verweist, werden die Pfade der Dateien und Ordner durch einen senkrechten Strich (|) getrennt. Die `ConnectionString`-Eigenschaft des Verbindungs-Managers hat folgendes Format:  
  
 \<*path*>|\<*path*>  
  
 Mehrere Dateien oder Ordner können Sie auch mithilfe von Platzhalterzeichen angeben. Um beispielsweise auf alle Textdateien auf dem Laufwerk C zu verweisen, kann der Wert der `ConnectionString` Eigenschaft auf c: \\ *. txt festgelegt werden.  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Weitere Informationen zu den Eigenschaften, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können, finden Sie unter [Referenz zur Benutzeroberfläche des Dialogfelds Dateiverbindungs-Manager hinzufügen](add-file-connection-manager-dialog-box-ui-reference.md).  
  
 Weitere Informationen zum programmgesteuerten Konfigurieren eines Verbindungs-Managers finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> und [Programmgesteuertes Hinzufügen von Verbindungen](../building-packages-programmatically/adding-connections-programmatically.md)festgelegt.  
  
  
