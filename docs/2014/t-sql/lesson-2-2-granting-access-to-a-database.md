---
title: Gewähren von Zugriff auf eine Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- database access
ms.assetid: 686edfe2-3650-48a6-a2da-9d46fa211ad8
caps.latest.revision: 11
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 7971df050304f242e79abcc7e26bdb5d31e5fb09
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43037091"
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
  
  
