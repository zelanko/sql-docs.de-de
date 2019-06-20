---
title: Starten des Hilfsprogramms „sqlcmd“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 00d57437-7a29-4da1-b639-ee990db055fb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ec1ec91705dfb9194f42c079cb7b3d5100c9d396
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66090109"
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
  
2.  Geben Sie an der Eingabeaufforderung `sqlcmd` ein:  
  
3.  Drücken Sie die EINGABETASTE.  
  
     Sie verfügen jetzt über eine vertrauenswürdige Verbindung mit der Standardinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die auf dem Computer ausgeführt wird.  
  
     **1 >** ist die `sqlcmd` Eingabeaufforderung, die die Nummer der Zeile angibt. Bei jedem Drücken der EINGABETASTE wird die Nummer um eins erhöht.  
  
4.  Zum Beenden der `sqlcmd` "Sitzung", Typ `EXIT` an die `sqlcmd` Eingabeaufforderung.  
  
### <a name="to-start-the-sqlcmd-utility-and-connect-to-a-named-instance-of-sql-server"></a>So starten Sie das Hilfsprogramm "sqlcmd" und stellen eine Verbindung mit einer benannten Instanz von SQL Server her  
  
1.  Öffnen Sie eine Eingabeaufforderung, und geben `sqlcmd -S` *MyServer\instanceName*. Ersetzen Sie *myServer\Instanzname* durch den Namen des Computers und der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, mit der Sie eine Verbindung herstellen möchten.  
  
2.  Drücken Sie die EINGABETASTE.  
  
     Die `sqlcmd` Eingabeaufforderung (1 >) gibt an, dass Sie mit der angegebenen Instanz verbunden sind [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    > [!NOTE]  
    >  Eingegebene [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen werden in einem Puffer gespeichert. Sie werden als Batch ausgeführt, wenn der Befehl "GO" erkannt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Transact-SQL-Skriptdateien mithilfe von sqlcmd](sqlcmd-run-transact-sql-script-files.md)  
  
  
