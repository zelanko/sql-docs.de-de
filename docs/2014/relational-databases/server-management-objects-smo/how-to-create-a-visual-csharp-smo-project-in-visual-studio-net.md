---
title: Erstellen ein Visual c# SMO-Projekts in Visual Studio .NET | Microsoft Docs
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
helpviewer_keywords:
- Visual C# [SMO]
ms.assetid: 1e7abb16-23a0-4a18-91ad-253261e6bf84
caps.latest.revision: 42
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b96b2f52b1d993c02536b70e39ba7d1868643a04
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058458"
---
# <a name="create-a-visual-c-smo-project-in-visual-studio-net"></a>Erstellen eines Visual C# SMO-Projekts in Visual Studio.NET
  In diesem Abschnitt wird beschrieben, wie eine einfache SMO-Konsolenanwendung erstellt wird.  
  
 In diesem Beispiel werden Namespaces importiert. Hierdurch kann das Programm auf SMO-Typen verweisen. Der Import des `Agent`-Namespaces ist optional. Verwenden sie beim Schreiben eines Programms von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Der `Common`-Namespace ist erforderlich, um eine sichere Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herzustellen. Der `SqlClient`-Namespace wird verwendet, um SQL-Ausnahmefehler zu verarbeiten.  
  
### <a name="creating-a-visual-c-smo-project-in-visual-studionet"></a>Erstellen eines Visual c# SMO-Projekts in Visual Studio.NET  
  
1.  Starten Sie [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] (oder [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)]).  
  
2.  Klicken Sie im Menü **Datei** auf **Neues Projekt**. Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
3.  In **Projekttypen** wählen Sie im Dialogfeld **Visual C#-**, und wählen Sie dann **Windows**. In der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] installierte Vorlagen Bereich **Windows-Anwendung**.  
  
4.  (Optional) In der **Namen** Feld, geben Sie den Namen der neuen Anwendung.  
  
5.  Wählen Sie den Visual C#-Anwendungstyp aus. Für die Beispiele, die darauf folgen, wählen Sie **Konsolenanwendung**.  
  
6.  Wählen Sie im Menü **Projekt** die Option **Verweis hinzufügen** aus. Das Dialogfeld **Verweis hinzufügen** wird angezeigt.  
  
7.  Klicken Sie auf **Durchsuchen**, suchen Sie die SMO-Assemblys in der [!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)] Ordner, und wählen Sie dann die folgenden Dateien. Dabei handelt es sich um die mindestens zum Erstellen einer SMO-Anwendung erforderlichen Dateien:  
  
     Microsoft.SqlServer.ConnectionInfo.dll  
  
     Microsoft.SqlServer.Smo.dll  
  
     Microsoft.SqlServer.Management.Sdk.Sfc.dll  
  
     Microsoft.SqlServer.SqlEnum.dll  
  
    > [!NOTE]  
    >  Mit gedrückter `Ctrl`-TASTE können Sie mehrere Dateien gleichzeitig auswählen.  
  
8.  Fügen Sie alle zusätzlich erforderlichen SMO-Assemblys hinzu. Wenn Sie speziell für [!INCLUDE[ssSB](../../includes/sssb-md.md)] programmieren, fügen Sie beispielsweise die folgenden Assemblys hinzu:  
  
     Microsoft.SqlServer.ServiceBrokerEmum.dll  
  
9. Klicken Sie auf **Öffnen**.  
  
10. Auf der **Ansicht** Menü klicken Sie auf **Code**. – oder – wählen Sie Program1.cs [Entwurf] Windows, und doppelklicken Sie auf das WindowsFormular, um das Codefenster anzuzeigen.  
  
11. Geben Sie im Code vor der namespace-Anweisung die folgenden `using`-Anweisungen ein, um die Typen im SMO-Namespace zu qualifizieren:  
  
    ```  
    using Microsoft.SqlServer.Management.Smo;  
    using Microsoft.SqlServer.Management.Common;  
    ```  
  
12. SMO verfügt über verschiedene Namespaces unter Microsoft.SqlServer.Management.Smo, z. B. Microsoft.SqlServer.Management.Smo.Agent. Fügen Sie diese Namespaces an, wie sie benötigt werden.  
  
13. Sie können jetzt den SMO-Code hinzufügen.  
  
  