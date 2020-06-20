---
title: Erstellen eines Visual c# SMO-Projekts in Visual Studio .net | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- Visual C# [SMO]
ms.assetid: 1e7abb16-23a0-4a18-91ad-253261e6bf84
author: stevestein
ms.author: sstein
ms.openlocfilehash: bfc8e5cf35a7f03f485bc3ff9e94ee70eab2cea2
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "84997080"
---
# <a name="create-a-visual-c-smo-project-in-visual-studio-net"></a>Erstellen eines Visual C# SMO-Projekts in Visual Studio.NET
  In diesem Abschnitt wird beschrieben, wie eine einfache SMO-Konsolenanwendung erstellt wird.  
  
 In diesem Beispiel werden Namespaces importiert. Hierdurch kann das Programm auf SMO-Typen verweisen. Der Import des `Agent`-Namespaces ist optional. Verwenden Sie es, wenn Sie ein Programm schreiben, das den- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent verwendet. Der `Common`-Namespace ist erforderlich, um eine sichere Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herzustellen. Der `SqlClient`-Namespace wird verwendet, um SQL-Ausnahmefehler zu verarbeiten.  
  
### <a name="creating-a-visual-c-smo-project-in-visual-studionet"></a>Erstellen eines Visual c# SMO-Projekts in Visual Studio.net  
  
1.  Starten Sie [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] (oder [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)]).  
  
2.  Klicken Sie im Menü **Datei** auf **Neues Projekt**. Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
3.  Wählen Sie im Dialogfeld **Projekttypen** die Option **Visual c#** aus, und wählen Sie dann **Windows**aus. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Wählen Sie im Bereich installierte Vorlagen die Option Windows- **Anwendung**aus.  
  
4.  Optionale Geben Sie im Feld **Name** den Namen der neuen Anwendung ein.  
  
5.  Wählen Sie den Visual C#-Anwendungstyp aus. Wählen Sie in den folgenden Beispielen **Konsolenanwendung**aus.  
  
6.  Wählen Sie im Menü **Projekt** die Option **Verweis hinzufügen** aus. Das Dialogfeld **Verweis hinzufügen** wird angezeigt.  
  
7.  Klicken Sie auf **Durchsuchen**, suchen Sie die SMO-Assemblys im [!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)] Ordner, und wählen Sie die folgenden Dateien aus. Dabei handelt es sich um die mindestens zum Erstellen einer SMO-Anwendung erforderlichen Dateien:  
  
     Microsoft.SqlServer.ConnectionInfo.dll  
  
     Microsoft.SqlServer.Smo.dll  
  
     Microsoft.SqlServer.Management.Sdk.Sfc.dll  
  
     Microsoft.SqlServer.SqlEnum.dll  
  
    > [!NOTE]  
    >  Mit gedrückter `Ctrl`-TASTE können Sie mehrere Dateien gleichzeitig auswählen.  
  
8.  Fügen Sie alle zusätzlich erforderlichen SMO-Assemblys hinzu. Wenn Sie speziell für [!INCLUDE[ssSB](../../includes/sssb-md.md)] programmieren, fügen Sie beispielsweise die folgenden Assemblys hinzu:  
  
     Microsoft.SqlServer.ServiceBrokerEmum.dll  
  
9. Klicken Sie auf **Öffnen**.  
  
10. Klicken Sie im Menü **Ansicht** auf **Code**.-oder wählen Sie Program1.cs [Design] Windows aus, und doppelklicken Sie auf das Windows Form, um das Code Fenster anzuzeigen.  
  
11. Geben Sie im Code vor der namespace-Anweisung die folgenden `using`-Anweisungen ein, um die Typen im SMO-Namespace zu qualifizieren:  
  
    ```  
    using Microsoft.SqlServer.Management.Smo;  
    using Microsoft.SqlServer.Management.Common;  
    ```  
  
12. SMO verfügt über verschiedene Namespaces unter Microsoft.SqlServer.Management.Smo, z. B. Microsoft.SqlServer.Management.Smo.Agent. Fügen Sie diese Namespaces nach Bedarf hinzu.  
  
13. Sie können jetzt den SMO-Code hinzufügen.  
  
  
