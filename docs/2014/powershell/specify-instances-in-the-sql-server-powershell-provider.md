---
title: Angeben von Instanzen im SQL Server PowerShell-Anbieter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 9373de68-fd43-45f2-b9a6-149c96610aeb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 414d9135989c39ea183d14d2d6f5dfa6e84e6fe6
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72797764"
---
# <a name="specify-instances-in-the-sql-server-powershell-provider"></a>Angeben von Instanzen im SQL Server PowerShell-Anbieter
  Die für den SQL Server PowerShell-Anbieter angegebenen Pfade müssen die Instanz von [!INCLUDE[ssDE](../includes/ssde-md.md)] und den Computer, auf dem sie ausgeführt wird, angeben. Die Syntax zum Angeben des Computers und der Instanz muss sowohl den Regeln für die SQL Server-Bezeichner als auch für die Windows PowerShell-Pfade entsprechen.  
  
1.  **Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions)  
  
2.  **To specify an instance:**  [Examples](#Examples)  
  
## <a name="before-you-begin"></a>Vorbereitungsmaßnahmen  
 Der erste Knoten, der auf SQLSERVER:\SQL in einem SQL Server-Anbieterpfad folgt, ist der Name des Computers, auf dem die Instanz von [!INCLUDE[ssDE](../includes/ssde-md.md)]ausgeführt wird, z. B.:  
  
```  
SQLSERVER:\SQL\MyComputer  
```  
  
 Wenn Sie Windows PowerShell auf demselben Computer ausführen wie die Instanz von [!INCLUDE[ssDE](../includes/ssde-md.md)], können Sie anstelle des Computernamens entweder "localhost" oder "(local)" verwenden. Skripts, die "localhost" oder "(local)" verwenden, können auf jedem Computer ausgeführt werden, ohne entsprechend dem jeweiligen Computernamen geändert werden zu müssen.  
  
 Sie können mehrere Instanzen des ausführbaren Programms [!INCLUDE[ssDE](../includes/ssde-md.md)] auf demselben Computer ausführen. Der Knoten, der dem Computernamen in einem SQL Server-Anbieterpfad folgt, gibt die Instanz an, z. B.:  
  
```  
SQLSERVER:\SQL\MyComputer\MyInstance  
```  
  
 Jeder Computer kann eine Standardinstanz von [!INCLUDE[ssDE](../includes/ssde-md.md)]aufweisen. Sie geben bei der Installation keinen Namen für die Standardinstanz an. Wenn Sie in einer Verbindungszeichenfolge nur einen Computernamen angeben, werden Sie mit der Standardinstanz auf diesem Computer verbunden. Alle anderen Instanzen auf dem Computer müssen benannte Instanzen sein. Sie geben den Instanznamen während des Setups ein, und die Verbindungszeichenfolgen müssen sowohl den Computernamen als auch den Instanznamen angeben.  
  
###  <a name="LimitationsRestrictions"></a> Einschränkungen  
 Sie können keinen Punkt (.) verwenden, um den lokalen Computer in PowerShell-Skripts anzugeben. Der Punkt wird nicht unterstützt, da der Punkt von PowerShell als Befehl interpretiert wird.  
  
 Die Klammerzeichen in "(local)" werden von Windows PowerShell normalerweise als Befehle behandelt. Sie müssen sie entweder codieren, sie zur Verwendung in einem Pfad mit Escapezeichen versehen oder den Pfad in doppelte Anführungszeichen setzen. Weitere Informationen finden Sie unter "Codierung und Decodierung von SQL Server-Bezeichnern".  
  
 Für den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anbieter ist immer die Angabe eines Instanznamens erforderlich. Für Standardinstanzen müssen Sie den Instanznamen DEFAULT angeben.  
  
##  <a name="Examples"></a> Beispiele; Computer- und Instanznamen  
 Bei diesem Beispiel wird die Standardinstanz auf dem lokalen Computer mithilfe von "localhost" und DEFAULT angegeben:  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT
```  
  
 Die Klammerzeichen in "(local)" werden von Windows PowerShell normalerweise als Befehle behandelt. Daher müssen Sie entweder:  
  
-   die Pfadzeichenfolge in Anführungszeichen setzen:  
  
    ```powershell
    Set-Location "SQLSERVER:\SQL\(local)\DEFAULT"  
    ```  
  
-   die Klammer mit dem Graviszeichen (`) versehen:  
  
    ```powershell
    Set-Location SQLSERVER:\SQL\`(local`)\DEFAULT  
    ```  
  
-   die Klammer in ihrer hexadezimalen Darstellung codieren:  
  
    ```powershell
    Set-Location SQLSERVER:\SQL\%28local%29\DEFAULT  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Bezeichnern in PowerShell](sql-server-identifiers-in-powershell.md)   
 [SQL Server PowerShell-Anbieter](sql-server-powershell-provider.md)   
 [SQL Server-PowerShell](sql-server-powershell.md)  
