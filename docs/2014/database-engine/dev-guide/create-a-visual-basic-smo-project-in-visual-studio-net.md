---
title: Erstellen eines Visual Basic SMO-Projekts in Visual Studio .net | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic [SMO]
ms.assetid: d7a3892c-0f1c-4c4d-8480-b58dce3720bc
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 49eb94833d10b2e901c008092aea29eab8e4ad48
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84933681"
---
# <a name="create-a-visual-basic-smo-project-in-visual-studio-net"></a>Erstellen eines Visual Basic-SMO-Projekts in Visual Studio .NET
  In diesem Abschnitt wird beschrieben, wie eine einfache SMO-Konsolenanwendung erstellt wird.  
  
 In diesem Beispiel werden Namespaces importiert. Hierdurch kann das Programm auf SMO-Typen verweisen. Der Import des `Agent`-Namespaces ist optional. Verwenden Sie es, wenn Sie ein Programm schreiben, das den- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent verwendet. Der `Common`-Namespace ist erforderlich, um eine sichere Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herzustellen. Der `SqlClient`-Namespace wird verwendet, um SQL-Ausnahmefehler zu verarbeiten.  
  
### <a name="creating-a-visual-basic-smo-project-in-visual-studionet"></a>Erstellen eines Visual Basic-SMO-Projekts in Visual Studio.NET  
  
1.  Starten Sie [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] (oder [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)]).  
  
2.  Klicken Sie im Menü **Datei** auf **Neues Projekt**. Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
3.  Wählen Sie im Dialogfeld **Projekttypen** die Option **Visual Basic**aus, und wählen Sie dann **Windows**aus. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Wählen Sie im Bereich installierte Vorlagen die Option **Konsolenanwendung aus.**  
  
4.  Optionale Geben Sie im Feld **Name** den Namen der neuen Anwendung ein.  
  
5.  Klicken Sie auf **OK** , um die [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Vorlage Konsolenanwendung zu laden.  
  
6.  Wählen Sie im Menü **Projekt** die Option **Verweis hinzufügen** aus. Das Dialogfeld **Verweis hinzufügen** wird angezeigt.  
  
7.  Klicken Sie auf **Durchsuchen**, suchen Sie die SMO-Assemblys im Ordner c:\Programme\Microsoft SQL server\120\sdk\assemblys, und wählen Sie dann die folgenden Dateien aus. Dabei handelt es sich um die mindestens zum Erstellen einer SMO-Anwendung erforderlichen Dateien:  
  
     Microsoft.SqlServer.ConnectionInfo.dll  
  
     Microsoft.SqlServer.SqlEnum.dll  
  
     Microsoft.SqlServer.Smo.dll  
  
     Microsoft.SqlServer.Management.Sdk.Sfc  
  
    > [!NOTE]  
    >  Mit gedrückter `Ctrl`-TASTE können Sie mehrere Dateien gleichzeitig auswählen.  
  
8.  Fügen Sie alle zusätzlich erforderlichen SMO-Assemblys hinzu. Wenn Sie speziell für [!INCLUDE[ssSB](../../includes/sssb-md.md)] programmieren, fügen Sie beispielsweise die folgenden Assemblys hinzu:  
  
     Microsoft.SqlServer.ServiceBrokerEmum.dll  
  
9. Klicken Sie auf **Öffnen**.  
  
10. Klicken Sie im Menü **Ansicht** auf **Code**.-oder-wählen Sie das Fenster Module1. vb aus, um das Code Fenster anzuzeigen.  
  
11. Geben Sie im Code vor allen Deklarationen die folgenden **Imports** -Anweisungen ein, um die Typen im SMO-Namespace zu qualifizieren.  
  
    ```  
    Imports Microsoft.SqlServer.Management.Smo  
    Imports Microsoft.SqlServer.Management.Common  
    ```  
  
12. SMO verfügt über verschiedene Namespaces unter Microsoft.SqlServer.Management.Smo, z. B. Microsoft.SqlServer.Management.Smo.Agent. Fügen Sie diese Namespaces nach Bedarf hinzu.  
  
13. Sie können jetzt den SMO-Code hinzufügen.  
  
  
