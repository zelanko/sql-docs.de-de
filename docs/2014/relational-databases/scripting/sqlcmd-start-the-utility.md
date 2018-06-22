---
title: Starten des Hilfsprogramms „sqlcmd“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00d57437-7a29-4da1-b639-ee990db055fb
caps.latest.revision: 39
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: eb2234b466a41b58cc1dd137950514de4b7aa458
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148334"
---
# <a name="start-the-sqlcmd-utility"></a>Starten des Hilfsprogramms "sqlcmd"
  Damit Sie mit der Verwendung von `sqlcmd` beginnen können, müssen Sie zunächst das Hilfsprogramm starten und eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen. Sie können die Verbindung mit einer Standardinstanz oder mit einer benannten Instanz herstellen. Der erste Schritt besteht darin, das Hilfsprogramm `sqlcmd` zu starten.  
  
> [!NOTE]  
>  Die Windows-Authentifizierung ist der Standardauthentifizierungsmodus für `sqlcmd`. Wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung verwenden möchten, müssen Sie einen Benutzernamen und ein Kennwort angeben. Verwenden Sie hierzu die Optionen **-U** und **-P** .  
  
> [!NOTE]  
>  Standardmäßig wird [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] als die benannte Instanz **sqlexpress**installiert.  
  
 Wenn Sie bisher noch keine Verbindung mit dieser Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] hergestellt haben, müssen Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] möglicherweise so konfigurieren, dass Verbindungen akzeptiert werden.  
  
### <a name="to-start-the-sqlcmd-utility-and-connect-to-a-default-instance-of-sql-server"></a>So starten Sie das Hilfsprogramm "sqlcmd" und stellen Sie eine Verbindung mit einer Standardinstanz von SQL Server her  
  
1.  Klicken Sie im **Startmenü** auf **Ausführen**. Geben Sie im Feld **Öffnen** den Befehl **cmd**ein, und klicken Sie auf **OK** , um ein Eingabeaufforderungsfenster zu öffnen.  
  
2.  Geben Sie an der Eingabeaufforderung `sqlcmd`.  
  
3.  Drücken Sie die EINGABETASTE.  
  
     Sie verfügen jetzt über eine vertrauenswürdige Verbindung mit der Standardinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die auf dem Computer ausgeführt wird.  
  
     **1 >** ist die `sqlcmd` Aufforderung, die gibt die Zeilennummer an. Bei jedem Drücken der EINGABETASTE wird die Nummer um eins erhöht.  
  
4.  Zum Beenden der `sqlcmd` Geben Sie die Sitzung `EXIT` an die `sqlcmd` Eingabeaufforderung.  
  
### <a name="to-start-the-sqlcmd-utility-and-connect-to-a-named-instance-of-sql-server"></a>So starten Sie das Hilfsprogramm "sqlcmd" und stellen eine Verbindung mit einer benannten Instanz von SQL Server her  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster, und geben `sqlcmd -S` *MyServer\instanceName*. Ersetzen Sie *myServer\Instanzname* durch den Namen des Computers und der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, mit der Sie eine Verbindung herstellen möchten.  
  
2.  Drücken Sie die EINGABETASTE.  
  
     Die Eingabeaufforderung `sqlcmd` (1>) zeigt an, dass Sie mit der angegebenen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verbunden sind.  
  
    > [!NOTE]  
    >  Eingegebene [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen werden in einem Puffer gespeichert. Sie werden als Batch ausgeführt, wenn der Befehl "GO" erkannt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Transact-SQL-Skriptdateien mithilfe von sqlcmd](sqlcmd-run-transact-sql-script-files.md)  
  
  