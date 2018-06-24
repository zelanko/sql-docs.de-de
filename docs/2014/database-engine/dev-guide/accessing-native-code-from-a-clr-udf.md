---
title: Zugreifen auf systemeigenen Code aus einem CLR-UDF | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 161afa9d-74a1-40f5-af17-162e355e7a46
caps.latest.revision: 4
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 82c2444f0d90876058bb7f062dd441f632741d0e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047904"
---
# <a name="accessing-native-code-from-a-clr-udf"></a>Zugreifen auf systemeigenen Code von einer CLR-UDF
  Dieses Beispiel zeigt, wie eine Funktion in systemeigenem (nicht verwaltetem) C++-Code in der Datenbank von einer benutzerdefinierten Funktion in einer Assembly aufgerufen wird.  
  
 In diesem Beispiel muss das Arbeitsverzeichnis `c:\test`.  
  
 Kompilieren Sie zuerst den C++-Code:  
  
```  
// Win32Sleep.cpp  
// compile with: /LD /link /noentry kernel32.lib  
#include <windows.h>  
  
extern "C"  
__declspec( dllexport ) void _cdecl SleepyLoop(DWORD sleep_interval) {  
   Sleep(sleep_interval);  
}  
```  
  
 Kompilieren Sie danach den C#-Code in eine Assembly:  
  
```  
// proc.cs  
// compile with: /target:library  
using System;  
using System.Threading;  
using System.Data.Sql;  
using System.Runtime.InteropServices;  
  
public class StoreProcedures {  
  
   public static readonly uint SLEEP_LOOP_TIMES = 10;  
   public static readonly uint SLEEP_DURATION = 1000;  
  
   [DllImport(@"c:\test\Win32Sleep.dll")]  
   internal static extern void SleepyLoop(uint sleepInterval);  
  
   public static void SleepInProcedure(int loopTimes) {  
      for ( int i = 0 ; i < loopTimes ; i++ ) {  
         // invoke the unmanaged routine  
         SleepyLoop(SLEEP_DURATION);  
      }  
   }  
}  
```  
  
 Führen Sie schließlich den folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)]-Befehl aus:  
  
```  
USE MASTER  
GO  
  
IF DB_ID('testdb') IS NOT NULL  
DROP DATABASE testdb  
GO  
  
CREATE DATABASE testdb  
GO  
  
USE testdb  
GO  
  
ALTER DATABASE testdb SET TRUSTWORTHY ON   
GO  
  
sp_configure 'show advanced options', 1  
GO  
RECONFIGURE  
GO  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
  
CREATE ASSEMBLY myasm FROM 'c:\test\proc.dll' WITH PERMISSION_SET=UNSAFE   
go  
  
CREATE PROCEDURE SleepProc(@loopTimes INT)  
AS EXTERNAL NAME myasm.[StoreProcedures].[SleepInProcedure]  
go  
  
-- sleep 5 seconds  
EXEC SleepProc 5  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Verwendungsszenarios und Beispiele für Common Language Runtime-Integration &#40;CLR&#41;](../../../2014/database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
  
  