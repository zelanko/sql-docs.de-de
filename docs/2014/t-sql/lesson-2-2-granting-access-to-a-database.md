---
title: Gewähren von Zugriff auf eine Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- database access
ms.assetid: 686edfe2-3650-48a6-a2da-9d46fa211ad8
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 12e678b8cd5210ba6db0cd326c0cd803ed210735
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63460046"
---
# <a name="granting-access-to-a-database"></a>Gewähren von Zugriff auf eine Datenbank
  Mary hat nun Zugriff auf diese Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], verfügt jedoch nicht über die Berechtigung zum Zugriff auf die Datenbanken. Selbst auf die Standarddatenbank **TestData** kann sie erst zugreifen, wenn Sie sie als Datenbankbenutzerin autorisieren.  
  
 Wenn Sie Mary Zugriff gewähren möchten, wechseln Sie zur **TestData** -Datenbank, und ordnen Sie ihren Anmeldenamen mithilfe der CREATE USER-Anweisung einer Benutzerin namens Mary zu.  
  
### <a name="to-create-a-user-in-a-database"></a>So erstellen Sie einen Benutzer in einer Datenbank  
  
1.  Geben Sie die folgenden Anweisungen ein (wobei Sie `computer_name` durch den Namen Ihres Computers ersetzen), und führen Sie sie aus, um `Mary` Zugriff auf die `TestData` -Datenbank zu gewähren.  
  
    ```  
    USE [TestData];  
    GO  
  
    CREATE USER [Mary] FOR LOGIN [computer_name\Mary];  
    GO  
  
    ```  
  
     Mary hat nun sowohl auf [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] als auch auf die `TestData` -Datenbank Zugriff.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Erstellen von Sichten und gespeicherten Prozeduren](lesson-2-3-creating-views-and-stored-procedures.md)  
  
  
