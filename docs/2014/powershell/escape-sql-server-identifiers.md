---
title: Escape-Bezeichner für SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 8a73e945-daa6-4e5d-93da-10f000f1f3a2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 17196f4e9a6deaadca09e77e94e2cf393f4af237
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62922894"
---
# <a name="escape-sql-server-identifiers"></a>Escape-Bezeichner für SQL Server
  Sie können Zeichen, die zwar in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Begrenzungsbezeichnern zulässig sind, nicht jedoch in Windows PowerShell-Pfadnamen, oftmals mit dem Windows PowerShell-Escapezeichen (`) umwandeln. Einige Zeichen können jedoch nicht mit Escapezeichen versehen werden. Zum Beispiel können Sie das Doppelpunktzeichen (:) in Windows PowerShell nicht mit Escapezeichen versehen. Bezeichner mit diesem Zeichen müssen codiert werden. Codierung ist zuverlässiger als das Umwandeln mit Escapezeichen, da das Codieren für alle Zeichen funktioniert.  
  
## <a name="before-you-begin"></a>Vorbereitungen  
 Das Graviszeichen (`) befindet sich i. d. R. oben rechts auf der Tastatur, links von der RÜCKTASTE.  
  
## <a name="examples"></a>Beispiele  
 Dies ist ein Beispiel für das Umwandeln eines #-Zeichens mittels Escapezeichen:  
  
```  
cd SQLSERVER:\SQL\MyComputer\MyInstance\MyDatabase\MySchema\`#MyTempTable  
```  
  
 Dies ist ein Beispiel für das Maskieren der Klammer mit dem Escapezeichen beim Angeben von "(lokal)" als Computername:  
  
```  
Set-Location SQLSERVER:\SQL\`(local`)\DEFAULT  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Bezeichnern in PowerShell](sql-server-identifiers-in-powershell.md)   
 [SQL Server PowerShell-Anbieter](sql-server-powershell-provider.md)   
 [SQL Server-PowerShell](sql-server-powershell.md)  
  
  
