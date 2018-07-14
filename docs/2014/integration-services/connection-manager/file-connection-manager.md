---
title: Dateiverbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- folders [Integration Services], connections
- files [Integration Services], connections
- files [Integration Services]
- connection managers [Integration Services], File
- connections [Integration Services], files
- File connection manager
ms.assetid: 019078bc-44ee-4975-9169-0f9a89e3f3be
caps.latest.revision: 50
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 33e9bb0dbb4030d09be6db95dda2a33245cd7288
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37252692"
---
# <a name="file-connection-manager"></a>Dateiverbindungs-Manager
  Mit einem Dateiverbindungs-Manager kann ein Paket auf eine vorhandene Datei oder einen vorhandenen Ordner verweisen bzw. eine Datei oder einen Ordner zur Laufzeit erstellen. Beispielsweise können Sie auf eine Excel-Datei verweisen. Zur Ausführung bestimmter Komponenten in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] werden in Dateien enthaltene Informationen verwendet. Beispielsweise kann ein Task SQL ausführen auf eine Datei verweisen, die die SQL-Anweisungen enthält, die vom Task ausgeführt werden. Mit anderen Komponenten werden Vorgänge für Dateien ausgeführt. Mit dem Task Dateisystem kann beispielsweise auf eine Datei verwiesen werden, die an einen neuen Ort kopiert werden soll.  
  
## <a name="usage-types-of-the-file-connection-manager"></a>Verwendungstypen des Dateiverbindungs-Managers  
 Die `FileUsageType` -Eigenschaft von Dateiverbindungs-Manager gibt an, wie die dateiverbindung verwendet wird. Der Dateiverbindungs-Manager kann eine Datei bzw. einen Ordner erstellen und eine vorhandene Datei bzw. einen vorhandenen Ordner verwenden.  
  
 Die folgende Tabelle enthält die Werte der `FileUsageType`.  
  
|value|Description|  
|-----------|-----------------|  
|`0`|Der Dateiverbindungs-Manager verwendet eine vorhandene Datei.|  
|`1`|Der Dateiverbindungs-Manager erstellt eine Datei.|  
|`2`|Der Dateiverbindungs-Manager verwendet einen vorhandenen Ordner.|  
|`3`|Der Dateiverbindungs-Manager erstellt einen Ordner.|  
  
## <a name="multiple-file-or-folder-connections"></a>Mehrere Datei- oder Ordnerverbindungen  
 Der Dateiverbindungs-Manager kann nur auf eine einzige Datei oder einen einzigen Ordner verweisen. Wenn Sie auf mehrere Dateien oder Ordner verweisen möchten, verwenden Sie anstelle eines Dateiverbindungs-Managers einen Verbindungs-Manager für mehrere Dateien. Weitere Informationen finden Sie unter [Multiple Files Connection Manager](multiple-files-connection-manager.md).  
  
## <a name="configuration-of-the-file-connection-manager"></a>Konfiguration des Verbindungs-Managers für Dateien  
 Wenn Sie einem Paket einen Dateiverbindungs-Manager hinzufügen [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] einen Verbindungs-Manager, der in eine dateiverbindung zur Laufzeit aufgelöst wird, Eigenschaften der dateiverbindung festlegt und die dateiverbindung hinzufügt erstellt die `Connections` -Sammlung des Pakets.  
  
 Die `ConnectionManagerType` Eigenschaft des Verbindungs-Managers nastaven NA hodnotu `FILE`.  
  
 Es gibt folgende Möglichkeiten, um einen Dateiverbindungs-Manager zu konfigurieren:  
  
-   Geben Sie den Verwendungstyp an.  
  
-   Geben Sie eine Datei oder einen Ordner an.  
  
 Sie können die ConnectionString-Eigenschaft für den Dateiverbindungs-Manager festlegen, indem Sie einen Ausdruck im Eigenschaftenfenster von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]angeben. Fügen Sie jedoch im **Dateiverbindungs-Manager-Editor**für **Datei/Ordner**einen Pfad für eine Datei oder einen Ordner hinzu, um Überprüfungsfehler zu vermeiden, wenn Sie die Datei oder den Ordner mit einem Ausdruck angeben.  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Weitere Informationen zu den Eigenschaften, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können, finden Sie unter [Dateiverbindungs-Manager-Editor](../file-connection-manager-editor.md).  
  
 Informationen zum programmgesteuerten Konfigurieren eines Verbindungs-Managers finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> und [Programmgesteuertes Hinzufügen von Verbindungen](../building-packages-programmatically/adding-connections-programmatically.md).  
  
  
