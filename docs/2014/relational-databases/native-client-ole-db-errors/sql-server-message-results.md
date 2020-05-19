---
title: SQL Server-Meldungsergebnisse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
ms.assetid: 6663c6f9-def1-4d9e-845b-2085e5efc401
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 19c0c3b044943e51c6d791e962fa830f0b6d0144
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82704935"
---
# <a name="sql-server-message-results"></a>SQL Server-Meldungsergebnisse
  Die folgenden- [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisungen generieren keine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-anbietedatasets oder die Anzahl betroffener Zeilen, wenn Sie ausgeführt werden:  
  
-   PRINT  
  
-   RAISERROR mit einem Schweregrad von 10 oder niedriger  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 Diese Anweisungen geben entweder eine oder mehrere Informationsmeldungen zurück oder veranlassen, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Informationsmeldungen anstelle von Rowset- oder Anzahlergebnissen zurückgibt. Bei erfolgreicher Ausführung gibt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-OLE DB Anbieter S_OK zurück, und die Nachrichten sind für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Consumer des Native Client-OLE DB Anbieters verfügbar.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt S_OK zurück und verfügt über eine oder mehrere Informationsmeldungen, die nach der Ausführung vieler- [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisungen oder der Consumer-Ausführung einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider-Member-Funktion verfügbar sind.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Consumer des Native Client OLE DB-Anbieters, der die dynamische Angabe von Abfragetext zulässt, sollte Fehler Schnittstellen nach jeder Ausführung der Element Funktion unabhängig vom Wert des Rückgabecodes, dem vorhanden sein oder Fehlen eines zurückgegebenen **IRowset** -oder **IMultipleResults** -Schnittstellen Verweises oder der Anzahl betroffener Zeilen überprüfen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler](errors.md)  
  
  
