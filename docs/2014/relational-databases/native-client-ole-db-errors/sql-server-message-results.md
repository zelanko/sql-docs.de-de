---
title: SQL Server-Meldungsergebnisse | Microsoft Docs
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
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
ms.assetid: 6663c6f9-def1-4d9e-845b-2085e5efc401
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7d1f6519c927bc8050590c1cc13821a7b7895f8a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056925"
---
# <a name="sql-server-message-results"></a>SQL Server-Meldungsergebnisse
  Die folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen generieren keine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter-Rowsets und Anzahl der betroffenen Zeilen zurück, wenn ausgeführt:  
  
-   PRINT  
  
-   RAISERROR mit einem Schweregrad von 10 oder niedriger  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 Diese Anweisungen geben entweder eine oder mehrere Informationsmeldungen zurück oder veranlassen, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Informationsmeldungen anstelle von Rowset- oder Anzahlergebnissen zurückgibt. Bei einer erfolgreichen Ausführung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter S_OK zurück, und die Nachrichten stehen die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Consumer der Native Client OLE DB-Anbieter.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt S_OK zurück und hat eine oder mehrere informationsmeldungen jeweils nach der Ausführung zahlreicher [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisungen oder Ausführung der Consumer eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter-Element Funktion.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter-Consumer ermöglicht die dynamische Angabe von Abfragetext prüfen Schnittstellen für Error nach jeder Ausführung der Elementfunktion unabhängig vom Wert von den Rückgabecode, das Vorhandensein oder fehlen von einem zurückgegebenen **IRowset** oder **IMultipleResults** -Schnittstellenverweises oder die Anzahl der betroffenen Zeilen.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler](errors.md)  
  
  