---
title: Verbindungs-Manager für mehrere Dateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- folders [Integration Services], connections
- files [Integration Services], connections
- Multiple Files connection manager
- connection managers [Integration Services], Multiple Files
- connections [Integration Services], files
- multiple file connections
ms.assetid: 10bdc56e-c5cd-4ddb-b2f7-375fe57fe8b2
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 22fe47c60aadc0f5014b7aef2171399f8ea0d22a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060091"
---
# <a name="multiple-files-connection-manager"></a>Verbindungs-Manager für mehrere Dateien
  Mit einem Verbindungs-Manager für mehrere Dateien kann ein Paket auf vorhandene Dateien und Ordner verweisen oder Dateien und Ordner zur Laufzeit erstellen.  
  
> [!NOTE]  
>  Die integrierten Tasks und Datenflusskomponenten in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] verwenden keinen Verbindungs-Manager für mehrere Dateien. Sie können den Verbindungs-Manager jedoch im Skripttask oder in der Skriptkomponente verwenden. Informationen zum Verwenden von Verbindungs-Managern in der Skripttask finden Sie unter [Herstellen einer Verbindung zu Datenquellen im Skripttask ](../extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md). Informationen zur Verwendung von Verbindungs-Manager in der Skriptkomponente finden Sie unter [Connecting to Data Sources in the Script Component] (.. / extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md.  
  
## <a name="usage-types-of-the-multiple-files-connection-manager"></a>Verwendungstypen des Verbindungs-Managers für mehrere Dateien  
 Mit der `FileUsageType`-Eigenschaft des Verbindungs-Managers für mehrere Dateien wird angegeben, wie die Verbindung verwendet wird. Der Verbindungs-Manager für mehrere Dateien kann Dateien bzw. Ordner erstellen und vorhandene Dateien bzw. Ordner verwenden.  
  
 Die folgende Tabelle enthält die Werte der `FileUsageType`.  
  
|value|Description|  
|-----------|-----------------|  
|**0**|Der Verbindungs-Manager für mehrere Dateien verwendet eine vorhandene Datei.|  
|**1**|Der Verbindungs-Manager für mehrere Dateien erstellt eine Datei.|  
|**2**|Der Verbindungs-Manager für mehrere Dateien verwendet einen vorhandenen Ordner.|  
|**3**|Der Verbindungs-Manager für mehrere Dateien erstellt einen Ordner.|  
  
## <a name="configuration-of-the-multiple-files-connection-manager"></a>Konfiguration des Verbindungs-Managers für mehrere Dateien  
 Wenn Sie einem Paket einen Verbindungs-Manager für mehrere Dateien hinzufügen, erstellt [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] einen Verbindungs-Manager, der zur Laufzeit in eine Verbindung für mehrere Dateien aufgelöst wird, die Eigenschaften der Verbindung für mehrere Dateien festlegt und der `Connections`-Auflistung des Pakets die Verbindung für mehrere Dateien hinzufügt.  
  
 Die `ConnectionManagerType` des Verbindungs-Managers ist-Eigenschaftensatz auf `MULTIFILE`.  
  
 Es gibt folgende Möglichkeiten, um einen Verbindungs-Manager für mehrere Dateien zu konfigurieren:  
  
-   Geben Sie den Verwendungstyp von Dateien und Ordnern an.  
  
-   Geben Sie Dateien und Ordner an.  
  
-   Falls Sie mehrere Dateien oder Ordner verwenden, geben Sie die Reihenfolge an, in der auf die Dateien und Ordner zugegriffen wird.  
  
 Wenn der Verbindungs-Manager für mehrere Dateien auf mehrere Dateien und Ordner verweist, werden die Pfade der Dateien und Ordner durch einen senkrechten Strich (|) getrennt. Die `ConnectionString`-Eigenschaft des Verbindungs-Managers hat folgendes Format:  
  
 \<*Pfad*>|\<*Pfad*>  
  
 Mehrere Dateien oder Ordner können Sie auch mithilfe von Platzhalterzeichen angeben. Um z. B. auf alle Textdateien auf dem C-Laufwerk, den Wert der Verweis der `ConnectionString` Eigenschaft kann festgelegt werden, um "c:"\\*.txt.  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Weitere Informationen zu den Eigenschaften, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können, finden Sie unter [Referenz zur Benutzeroberfläche des Dialogfelds Dateiverbindungs-Manager hinzufügen](add-file-connection-manager-dialog-box-ui-reference.md).  
  
 Informationen zum programmgesteuerten Konfigurieren eines Verbindungs-Managers finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> und [Verbindungen programmgesteuert hinzufügen](../building-packages-programmatically/adding-connections-programmatically.md).  
  
  