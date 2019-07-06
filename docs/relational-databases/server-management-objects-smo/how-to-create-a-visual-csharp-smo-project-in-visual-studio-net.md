---
title: Erstellen Sie eine Visual c# SMO-Projekts in Visual Studio .NET | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- Visual C# [SMO]
ms.assetid: 1e7abb16-23a0-4a18-91ad-253261e6bf84
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7e67f69a6e1ce5ce18eb265fdc86eba8e8fcd0bc
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/05/2019
ms.locfileid: "67585087"
---
# <a name="how-to-create-a-visual-c-smo-project-in-visual-studio-net"></a>Erstellen eines Visual C#-SMO-Projekts in Visual Studio .NET
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  In diesem Abschnitt wird beschrieben, wie eine einfache SMO-Konsolenanwendung erstellt wird.  
  
 In diesem Beispiel werden Namespaces importiert. Hierdurch kann das Programm auf SMO-Typen verweisen. Importiert die **Agent** Namespaces ist optional. Verwenden, wenn Sie ein Programm schreiben, das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Die **allgemeine** Namespace ist erforderlich, um eine sichere Verbindung mit der Instanz von herstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Die **SqlClient** Namespace wird verwendet, um die SQL-Ausnahmefehler zu verarbeiten.  
  
### <a name="creating-a-visual-c-smo-project-in-visual-studionet"></a>Erstellen eines Visual c# SMO-Projekts in Visual Studio.NET  
  
1. Starten Sie Visual Studio
  
2. Auf der **Datei** Menü klicken Sie auf **neu** und dann **Projekt**.  Das Dialogfeld **Neues Projekt** wird angezeigt.   
  
3. In der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **installiert** Bereich, navigieren Sie zu **Vorlagen**\\**Visual C#-** \\**Windows** und wählen Sie **Konsolenanwendung**.  
  
4. (Optional) In der **Namen** Text geben den Namen der neuen Anwendung.  

5. Klicken Sie auf **OK** beim Laden der Vorlage für die Konsolenanwendung.  

6. Befolgen Sie die Anweisungen auf [Installieren von SMO](installing-smo.md) zum Installieren des Pakets für Ihr Projekt zu verweisen.
  
7. Klicken Sie im Menü **Ansicht** auf **Code**.
    
8. Geben Sie im Code vor der Namespace-Anweisung die folgenden **mit** Anweisungen, die die Typen im SMO-Namespace zu qualifizieren:
  
    ```  
    using Microsoft.SqlServer.Management.Smo;  
    using Microsoft.SqlServer.Management.Common;  
    ```  
  
15. SMO verfügt über verschiedene Namespaces unter Microsoft.SqlServer.Management.Smo, z. B. Microsoft.SqlServer.Management.Smo.Agent. Fügen Sie diese Namespaces, wie sie benötigt werden.  
  
16. Sie können jetzt den SMO-Code hinzufügen.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

