---
title: Ändern der SQL Server-Dienst erweiterten Eigenschaften mithilfe von VBScript | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- VBScript [WMI]
- modifying SQL Server Service properties
- WMI Provider for Configuration Management, VBScript
ms.assetid: f3c5d981-eaa3-4d34-9b91-37e42636aa81
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: f3a380f80b4ecc7540e29605543722edd55e226d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62705066"
---
# <a name="modify-sql-server-service-advanced-properties-using-vbscript"></a>Ändern der erweiterten Eigenschaften des SQL Server-Diensts mit VBScript
  In diesem Abschnitt wird beschrieben, wie ein VBScript-Programm erstellen, die die Version der installierten Instanzen von auflistet [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die auf einem Computer ausgeführt werden.  
  
 Mit dem Codebeispiel werden die Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die auf dem Computer ausgeführt werden, und deren Version aufgeführt.  
  
### <a name="listing-name-and-version-of-installed-instances-of-sql-server"></a>Auflisten der Namen und der Version von installierten Instanzen von SQL Server  
  
1.  Öffnen Sie ein neues Dokument in einem Texteditor wie [!INCLUDE[msCoName](../../includes/msconame-md.md)] Editor. Kopieren Sie den Code, den Sie im Anschluss an diese Prozedur finden, und speichern Sie die Datei mit der Erweiterung .vbs. Dieses Beispiel hat den Namen test.vbs.  
  
2.  Stellen Sie eine Verbindung zu einer Instanz des WMI-Anbieters für die Computerverwaltung mit der VBScript `GetObject`-Funktion her. In diesem Beispiel wird eine Verbindung zu einem Remotecomputer mit dem Namen mpc hergestellt, allerdings wird der Computername zur Verbindung zum lokalen Computer ausgelassen: winmgmts:root\Microsoft\SqlServer\ComputerManagement. Weitere Informationen zur `GetObject`-Funktion finden Sie in der VBScript-Referenz.  
  
3.  Verwenden Sie die `InstancesOf`-Methode, um eine Liste der Dienste aufzuzählen. Die Dienste können auch mit einer einfachen WQL-Abfrage und einer `ExecQuery`-Methode anstelle der `InstancesOf`-Methode aufgezählt werden.  
  
4.  Verwenden Sie die `ExecQuery`-Methode und eine WQL-Abfrage, um den Namen und die Version der installierten Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abzurufen.  
  
5.  Speichern Sie die Datei.  
  
6.  Führen Sie das Skript durch Eingabe `cscript test.vbs` an der Eingabeaufforderung.  
  
## <a name="example"></a>Beispiel  
  
```  
set wmi = GetObject("WINMGMTS:\\.\root\Microsoft\SqlServer\ComputerManagement12")  
for each prop in wmi.ExecQuery("select * from SqlServiceAdvancedProperty where SQLServiceType = 1 AND PropertyName = 'VERSION'")  
WScript.Echo prop.ServiceName & " " & prop.PropertyName & ": " & prop.PropertyStrValue  
next  
```  
  
  
