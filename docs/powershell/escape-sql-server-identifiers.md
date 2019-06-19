---
title: Escape-Bezeichner für SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 8a73e945-daa6-4e5d-93da-10f000f1f3a2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 40897ed67ca661a763a2c654dc2c5fb223956264
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62672586"
---
# <a name="escape-sql-server-identifiers"></a>Escape-Bezeichner für SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Sie können Zeichen, die zwar in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Begrenzungsbezeichnern zulässig sind, in Windows PowerShell-Pfadnamen jedoch nicht, oftmals mit dem Escapezeichen (`) umwandeln. Einige Zeichen können jedoch nicht mit Escapezeichen versehen werden. Zum Beispiel können Sie das Doppelpunktzeichen (:) in Windows PowerShell nicht mit Escapezeichen versehen. Bezeichner mit diesem Zeichen müssen codiert werden. Codierung ist zuverlässiger als das Umwandeln mit Escapezeichen, da das Codieren für alle Zeichen funktioniert.  

> [!NOTE]
> Es gibt zwei SQL Server PowerShell-Module: **SqlServer** und **SQLPS**. Das **SQLPS**-Modul ist zwar in der SQL Server-Installation (für die Abwärtskompatibilität) enthalten, wird jedoch nicht mehr aktualisiert. Das **SqlServer**-Modul ist das aktuellste PowerShell-Modul. Das **SqlServer**-Modul enthält aktualisierte Versionen der Cmdlets in **SQLPS** sowie neue Cmdlets zur Unterstützung der neuesten SQL-Funktionen.
> Vorherige Versionen des **SqlServer**-Moduls *waren* in SQL Server Management Studio (SSMS) enthalten, allerdings nur in den Versionen 16.x. Das **SqlServer**-Modul muss über den PowerShell-Katalog installiert werden, damit PowerShell mit SSMS 17.0 und höher verwendet werden kann.
> Informationen zur Installation des **SqlServer**-Moduls finden Sie unter [Installieren von SQL Server PowerShell](download-sql-server-ps-module.md).

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
  
  
