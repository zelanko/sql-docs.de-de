---
title: Erstellen Sie eine Visual Basic-SMO-Projekts in Visual Studio .NET | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic [SMO]
ms.assetid: d7a3892c-0f1c-4c4d-8480-b58dce3720bc
caps.latest.revision: 43
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0a3cacc04d8ce4afd863c7ef3cc8d21e1446c319
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37213790"
---
# <a name="create-a-visual-basic-smo-project-in-visual-studio-net"></a>Erstellen Sie eine Visual Basic-SMO-Projekts in Visual Studio .NET
  In diesem Abschnitt wird beschrieben, wie eine einfache SMO-Konsolenanwendung erstellt wird.  
  
 In diesem Beispiel werden Namespaces importiert. Hierdurch kann das Programm auf SMO-Typen verweisen. Der Import des `Agent`-Namespaces ist optional. Verwenden, wenn Sie ein Programm schreiben, das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Der `Common`-Namespace ist erforderlich, um eine sichere Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herzustellen. Der `SqlClient`-Namespace wird verwendet, um SQL-Ausnahmefehler zu verarbeiten.  
  
### <a name="creating-a-visual-basic-smo-project-in-visual-studionet"></a>Erstellen eines Visual Basic-SMO-Projekts in Visual Studio.NET  
  
1.  Starten Sie [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] (oder [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)]).  
  
2.  Klicken Sie im Menü **Datei** auf **Neues Projekt**. Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
3.  In **Projekttypen** wählen Sie im Dialogfeld **Visual Basic**, und wählen Sie dann **Windows**. In der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] installierte Vorlagen wählen Sie im Bereich **-Konsolenanwendung.**  
  
4.  (Optional) In der **Namen** Feld, geben Sie den Namen der neuen Anwendung.  
  
5.  Klicken Sie auf **OK** beim Laden der [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Vorlage für eine Konsolenanwendung.  
  
6.  Wählen Sie im Menü **Projekt** die Option **Verweis hinzufügen** aus. Das Dialogfeld **Verweis hinzufügen** wird angezeigt.  
  
7.  Klicken Sie auf **Durchsuchen**, suchen Sie die SMO-Assemblys im Ordner C:\Program Files\Microsoft SQL Server\120\SDK\Assemblies, und wählen Sie die folgenden Dateien. Dabei handelt es sich um die mindestens zum Erstellen einer SMO-Anwendung erforderlichen Dateien:  
  
     Microsoft.SqlServer.ConnectionInfo.dll  
  
     Microsoft.SqlServer.SqlEnum.dll  
  
     Microsoft.SqlServer.Smo.dll  
  
     Microsoft.SqlServer.Management.Sdk.Sfc  
  
    > [!NOTE]  
    >  Mit gedrückter `Ctrl`-TASTE können Sie mehrere Dateien gleichzeitig auswählen.  
  
8.  Fügen Sie alle zusätzlich erforderlichen SMO-Assemblys hinzu. Wenn Sie speziell für [!INCLUDE[ssSB](../../includes/sssb-md.md)] programmieren, fügen Sie beispielsweise die folgenden Assemblys hinzu:  
  
     Microsoft.SqlServer.ServiceBrokerEmum.dll  
  
9. Klicken Sie auf **Öffnen**.  
  
10. Auf der **Ansicht** Menü klicken Sie auf **Code**. oder wählen Sie im Fenster "Module1.vb", um das Codefenster anzuzeigen.  
  
11. Geben Sie im Code vor möglichen Deklarationen die folgenden **Importe** Anweisungen, die die Typen im SMO-Namespace zu qualifizieren.  
  
    ```  
    Imports Microsoft.SqlServer.Management.Smo  
    Imports Microsoft.SqlServer.Management.Common  
    ```  
  
12. SMO verfügt über verschiedene Namespaces unter Microsoft.SqlServer.Management.Smo, z. B. Microsoft.SqlServer.Management.Smo.Agent. Fügen Sie diese Namespaces, wie sie benötigt werden.  
  
13. Sie können jetzt den SMO-Code hinzufügen.  
  
  
