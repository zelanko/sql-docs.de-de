---
title: Befehle, die mehrere Rowsetergebnisse erzeugen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- SQL Server Native Client OLE DB provider, commands
- SQL Server Native Client OLE DB provider, multiple rowsets
- commands [OLE DB]
- multiple-rowset results
ms.assetid: 4567668d-35fd-4162-b61f-f7536862cdcb
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 29ce1e2c701db485d8251bc9c017a9b192576a7c
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82707831"
---
# <a name="commands-generating-multiple-rowset-results"></a>Mehrere Rowsetergebnisse generierende Befehle
  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter kann mehrere Rowsets von-Anweisungen zurückgeben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anweisungen geben unter folgenden Bedingungen mehrere Rowsetergebnisse zurück:  
  
-   SQL-Anweisungen im Batchmodus werden als einzelner Befehl gesendet.  
  
-   Gespeicherte Prozeduren implementieren einen Batch SQL-Anweisungen.  
  
## <a name="batches"></a>Batches  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter erkennt das Semikolon als Batch Trennzeichen für SQL-Anweisungen:  
  
```  
WCHAR*       wSQLString = L"SELECT * FROM Categories; "  
                          L"SELECT * FROM Products";  
```  
  
 Mehrere SQL-Anweisungen in einem Batch zu senden ist effizienter, als jede SQL-Anweisung einzeln auszuführen. Durch Senden eines Batches werden die Netzwerkroundtrips vom Client auf den Server reduziert.  
  
## <a name="stored-procedures"></a>Gespeicherte Prozeduren  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt ein Resultset für jede Anweisung in einer gespeicherten Prozedur zurück, sodass die meisten gespeicherten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Prozeduren mehrere Resultsets zurückgeben.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Verwenden von 'IMultipleResults' zur Verarbeitung mehrerer Resultsets](using-imultipleresults-to-process-multiple-result-sets.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Befehle](commands.md)  
  
  
